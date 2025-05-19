---
title: "Atualizações do Aspose.GIS: Edição de Features e Geometrias e salvando as alterações no banco de dados."
type: docs
url: /pt/net/showcases/saving-changes-to-database/
description: "Este artigo explora os aprimoramentos recentes na biblioteca Aspose.GIS, focando nas novas capacidades para detectar e salvar alterações de geometria em um aplicativo de mapeamento."
weight: 80
---
# Atualizações do Aspose.GIS: Edição de Features e Geometrias e salvando as alterações no banco de dados.

## Introdução

À luz das recentes mudanças na biblioteca [Aspose.GIS](https://www.nuget.org/packages/Aspose.gis), é importante destacar algumas delas para que não passem despercebidas. Neste artigo, discutiremos a nova capacidade de detectar e salvar alterações em geometrias e features no banco de dados.

Como exemplo para demonstração, continuaremos trabalhando no aplicativo descrito no artigo ["Desenhe um mapa. Um mapa deslizante com tiles"](https://docs.aspose.com/gis/net/showcases/sliding-map-with-tiles/) e o expandiremos ligeiramente adicionando funcionalidades de edição de objetos no mapa. O conjunto de dados permanece o mesmo do artigo anterior.

## Front-end

Para a demonstração das capacidades de modificação da geometria, escolhemos uma extensão popular de código aberto para [leaflet](https://leafletjs.com/) — [leaflet-geoman](https://geoman.io/).

Adicionamos esta biblioteca através do arquivo libman.json:
![Libman](libman.png)

Em seguida, conectamos os estilos e scripts à página:
```razor
@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.js"></script>
    <script src="~/lib/contagt/leaflet-geoman-free/dist/leaflet-geoman.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

Para fins de demonstração, limitaremos as capacidades de edição apenas a edifícios. O usuário clica no botão esquerdo do mouse no mapa e, se houver um edifício naquele local, ele é destacado e fica disponível para edição. Isso é alcançado sobrepondo uma camada adicional sobre os tiles.

Quando o usuário clica no mapa, a biblioteca Leaflet calcula as coordenadas geoespaciais do clique. Enviamos essas coordenadas para o back-end e pesquisamos no banco de dados por geometrias que intersectam com o ponto clicado. Se houver edifícios entre essas geometrias, os retornaremos.

Os edifícios são retornados do back-end no formato `GeoJSON` e adicionados ao mapa como uma camada separada para edição. É assim que lidamos com o clique:
```javascript
var featuresLayer = L.featureGroup().addTo(map);

map.on('click', function (e) {
    var latlng = e.latlng;
    var featureFound = false;

    console.log(latlng.lat + ' ' + latlng.lng);

    featuresLayer.eachLayer(function (layer) {
        if (layer.getBounds && layer.getBounds().contains(latlng)) {
            featureFound = true;
            return;
        }
    });

    if (!featureFound) {
        loadGeoJSON(latlng.lat, latlng.lng)
            .then((addedFeatureLayer) => {
                if (addedFeatureLayer) {
                    addedFeatureLayer.addTo(featuresLayer);
                    addedFeatureLayer.pm.enable();
                    console.log('Feature added.');
                } else {
                    console.log('No feature to add.');
                }
            });
    }

    featureFound = false;
});
```

Temos um grupo de camadas persistente para geometrias editáveis, `featuresLayer`, que foi adicionado ao mapa. Verificamos se o clique foi feito em uma geometria já carregada e, caso contrário, fazemos uma solicitação ao back-end para carregar os polígonos representando edifícios. As camadas de features carregadas são adicionadas a featuresLayer e o modo de edição é ativado.

Aqui está como fica a função para carregar features e converter do `GeoJSON`:
```javascript
function loadGeoJSON(lat, lng) {
    return fetch(`/features?lat=${lat}&lng=${lng}`)
        .then(response => response.json())
        .then(data => {
            if (data && data.features && data.features.length > 0) {
                return L.geoJSON(data);

            } else {
                return null;
            }
        })
        .catch(error => console.error('Error loading a feature:', error));
}
```

Após a sessão de edição, o usuário clica em um botão `Salvar` personalizado:

![Save](save-btn.png)

Atualize a página e veja as alterações:

![Changes](changes.png)

Infelizmente, a função `tiles.redraw()` não funciona corretamente, pois os tiles carregados anteriormente são armazenados em cache, exigindo um refresh forçado do mapa via `Ctrl + F5`.

Aqui está o handler para pressionar o botão salvar:
```javascript
function saveResult() {
    if (featuresLayer.getLayers().length === 0) {
        console.log('There are no layers to send to the server.');
        return;
    }
    sendGeoJSONToServer()
        .then(() => {
            console.log('clear and update map');
            featuresLayer.clearLayers();
            tiles.redraw();
        });
}

function sendGeoJSONToServer() {
    var geojsonData = featuresLayer.toGeoJSON();

    return fetch('/features', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/geo+json'
        },
        body: JSON.stringify(geojsonData)
    })
        .then(data => {
            console.log('The data has been successfully sent to the server.');
        })
        .catch(error => {
            console.error('Error when sending GeoJSON:', error);
        });
}
```

## Back-end

Aqui adicionamos um novo controlador, `FeaturesController`, onde criamos um handler para extrair casas/features de acordo com as coordenadas enviadas.

A solicitação SQL é a seguinte:

```csharp
            var latitude = lat.ToString(CultureInfo.InvariantCulture);
            var longitude = lng.ToString(CultureInfo.InvariantCulture);
            var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
                        FROM public.planet_osm_polygon
                        WHERE ST_Intersects(way, ST_Transform(ST_SetSRID(ST_MakePoint({longitude}, {latitude}), 4326), 3857)) AND building IS NOT NULL";
```

As coordenadas são transformadas em um ponto, indicando o sistema de coordenadas da solicitação original do cliente (WGS 84) e, em seguida, traduzidas para o sistema no qual os dados do banco de dados são apresentados (Web Mercator). Procuramos interseções com este ponto para geometrias marcadas como edifícios.

A execução da solicitação e envio de dados ao cliente ocorre de forma semelhante ao que discutimos no artigo anterior:
```csharp
VectorLayer inputLayer;

using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
    var dataSource = Drivers.PostGis
        .FromQuery(query)
        .GeometryField("way")
        .AddAttribute("osm_id", AttributeDataType.Long)
        .AddAttribute("name", AttributeDataType.String)
        .AddAttribute("building", AttributeDataType.String)
        .Build();

    conn.Open();

    inputLayer = await dataSource.ReadAsync(conn);
}

var jsonStream = new MemoryStream();

inputLayer.SaveTo(AbstractPath.FromStream(jsonStream), Drivers.GeoJson);

var result = Encoding.UTF8.GetString(jsonStream.ToArray());

return new ContentResult()
{
    Content = result,
    ContentType = "application/geo+json"
};
```
Com uma pequena diferença: salvamos nossa camada InMemory como GeoJSON na memória como um stream, então a convertemos em uma string e enviamos para o cliente.

Agora chegamos à essência das atualizações no Aspose.GIS — salvar alterações no banco de dados. O método `Edit()` lida com isso. Lemos o corpo da solicitação para carregá-lo completamente na memória e o lemos como um stream:
```csharp
Request.EnableBuffering();
using var reader = new StreamReader(Request.Body, Encoding.UTF8);

// just buffer the body.
await reader.ReadToEndAsync();
Request.Body.Position = 0;
```
Em seguida, lemos as features editadas no formato GeoJSON:
```csharp
using (var inputLayer = VectorLayer.Open(AbstractPath.FromStream(Request.Body), Drivers.GeoJson))
```
O próximo passo, do conjunto de features enviadas, extraímos os atributos que representam os identificadores exclusivos das features correspondentes no banco de dados. Formamos uma solicitação para popular um layer especial para edição e construímos a fonte de dados correspondente:
```csharp
var ids = string.Join(", ", inputLayer.Select(x => x.GetValue<long>("osm_id")));

var query = $@"SELECT osm_id, building, name, ST_AsEWKB(way) as way
               FROM public.planet_osm_polygon
               WHERE osm_id IN ({ids});";

var dataSource = Drivers.PostGis
    .FromQuery(query)
    .GeometryField("way")
    .AddAttribute("osm_id", AttributeDataType.Integer, System.Data.DbType.Int64)
    .AddAttribute("name", AttributeDataType.String)
    .AddAttribute("building", AttributeDataType.String)
    .AsTrackableForChanges("public.planet_osm_polygon", "osm_id", true)
    .Build();
```
Observe o método de configuração `AsTrackableForChanges`. Este é um método especial que indica a necessidade de criar uma fonte de dados específica capaz de rastrear alterações. O primeiro parâmetro especifica a tabela para a qual as solicitações de alteração devem ser enviadas. O segundo indica qual atributo será considerado o identificador para fazer alterações no banco de dados. A parte mais interessante é o terceiro parâmetro. Quando definido como True, ele indica que a camada rastreará o aparecimento de duplicatas de acordo com o segundo parâmetro e "sobrescreverá" features carregadas anteriormente com novas. No entanto, no caso de resultados de edição, ou seja, adicionar um novo feature com o mesmo identificador, um comando `UPDATE` será gerado de acordo com as alterações em comparação com o valor antigo. Se duplicatas aparecerem durante a inicialização da camada do banco de dados, a camada sobrescreverá silenciosamente elas com o último valor. Se o terceiro parâmetro for definido como falso, uma exceção será lançada ao aparecimento de duplicatas, seja durante a inicialização ou edição.

Os nomes dos atributos serão usados como nomes de campos na tabela editável. É importante observar um ponto crucial em relação à detecção de alterações. É essencial especificar o tipo de dados exato do atributo que será armazenado na camada para rastrear alterações, ele deve ser preciso em relação aos tipos recém-adicionados ou modificados. Por exemplo, se adicionarmos um novo feature com um `osm_id` do tipo `Int32`, enquanto o tipo de atributo especificado na camada é `Int64`, isso será tratado como dois valores diferentes, pois não há sobrecarga do método `Equal`s que pareça `Int64.Equals(Int32)`. Nas versões futuras, este comportamento será revisado e corrigido se possível. O tipo de parâmetro terceiro será aplicado durante o salvamento dos dados como o tipo de dado alvo da tabela do banco de dados.

Em seguida, conectamos ao banco de dados e lemos os dados da tabela:
```csharp
using var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary");
await conn.OpenAsync();
using var transaction = await conn.BeginTransactionAsync();
var editLayer = await dataSource.ReadAsync(conn, transaction);
```
Um ponto importante é que para a transação funcionar corretamente no nível do banco de dados, é necessário passar a transação atual como o segundo parâmetro durante a operação de leitura.

Em seguida, precisamos executar uma série de transformações antes de enviar as alterações ao banco de dados:
```csharp
var transformer = SpatialReferenceSystem.Wgs84.CreateTransformationTo(SpatialReferenceSystem.WebMercator);

foreach (var feature in inputLayer)
{
    feature.Geometry = transformer.Transform(feature.Geometry);
    ((Geometry)feature.Geometry).HasZ = false;
}

foreach (var feature in inputLayer)
{
    var replacingId = feature.GetValue<long>("osm_id");
    var toReplaceIndex = editLayer.TakeWhile(x => x.GetValue<long>("osm_id") != replacingId).Count();
    editLayer.ReplaceAt(toReplaceIndex, feature);
}

await dataSource.SubmitChangesAsync(editLayer, conn, transaction);

transaction.Commit();
```
Leaflet gera geometrias no sistema de coordenadas WGS 84, no entanto, o esquema do banco de dados requer armazenamento em Web Mercator. Para transformar para o sistema Web Mercator, criamos um objeto `transformer` especial e o usamos para a conversão.

Além disso, leaflet preenche o terceiro parâmetro das coordenadas da geometria Z com um valor de 0. No entanto, este parâmetro não é contabilizado no nosso esquema do banco de dados, então removemos sua presença definindo o valor de `HasZ` como falso.

O ponto final é aplicar alterações substituindo a feature existente pela que foi recebida do cliente que tem o mesmo osm_id. Esta operação levará à detecção de alterações em relação às instâncias mais antigas da feature. No momento de chamar `SubmitChangesAsync`, o processo de detecção de alteração ocorrerá e os comandos INSERT, DELETE e UPDATE serão enviados ao banco de dados de acordo com suas alterações.

Obrigado por ler até o fim. Todo o código estará disponível no seguinte repositório: [Aspose.GIS.TilesTest](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest)
---