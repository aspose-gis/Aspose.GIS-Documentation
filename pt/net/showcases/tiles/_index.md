---
title: "Desenhe um mapa. Um mapa deslizante com blocos."
type: docs
url: /pt/net/showcases/sliding-map-with-tiles/
description: "Como desenhar blocos e construir um mapa deslizante a partir deles."
weight: 80
aliases:
 - /pt/net/showcases/tiles/
---
# Desenhe um mapa. Um mapa deslizante com blocos.
Neste artigo, queremos mostrar como, usando a biblioteca [Aspose.GIS](https://www.nuget.org/packages/Aspose.GIS/) e dados públicos, você pode construir um mapa deslizante que será gerado em tempo real. Graças ao novo recurso da biblioteca, agora podemos consultar dados GIS do banco de dados via consulta SQL. Aqui está o que devemos obter como resultado:

![Resultado](result.png)

Repositório do código fonte [aqui](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Aspose.GIS.TilesTest).

## Preparação de dados.

Primeiramente, precisaremos de informações geoespaciais que podemos carregar no banco de dados. Uma das fontes populares dessas informações é o `OpenStreetMap`, então vamos usá-lo. A maneira mais conveniente, na minha opinião, é extrair dados em formato pbf do recurso público https://download.geofabrik.de/ . Por exemplo, vamos baixar [Hungria](https://download.geofabrik.de/europe/hungary-latest.osm.pbf).

No próximo estágio, precisamos de uma instância funcional de `PostGIS`. É claro que você pode usar uma versão instalada localmente do `PostgreSQL`, mas acho muito conveniente usar contêineres Docker. Vamos instalar o PostGIS usando um arquivo docker compose:

```yaml
services:
  postgis:
    image: postgis/postgis
    environment:
      - POSTGRES_DB=gis
      - POSTGRES_USER=gis
      - POSTGRES_PASSWORD=password
    ports:
      - 5432:5432
    volumes:
      - d:\\local_folder:/usr/share/gisdata
```

O volume `d:\local_folder:/usr/share/gisdata` é necessário para carregar dados GIS da máquina local.

Em seguida, vamos executar nosso contêiner:

```bash
docker compose up
```

Conecte-se à instância do banco de dados usando o `pgAdmin` e crie o banco de dados Hungria lá:

![Criar DB](create_db.png)

ou através do comando SQL:

```sql
CREATE DATABASE Hungary;
```

Adicione as extensões necessárias a este banco de dados:

![Extensões](add_extention.png)

Estas serão as extensões `postgis` e `hstore`. hstore é uma extensão que permite usar o tipo de dado chave-valor. OpenStreetMap usa amplamente esse tipo para descrever atributos que não se enquadram na categoria dos principais, portanto, campos separados não são criados para eles, mas são armazenados no campo tags.

Há também uma versão semelhante a SQL dos comandos:

```sql
CREATE EXTENSION IF NOT EXISTS hstore;
CREATE EXTENSION IF NOT EXISTS postgis;
```

Agora vamos nos conectar ao contêiner, no meu caso é `local_folder-postgis-1`:

```bash
docker exec -it local_folder-postgis-1 sh
```

E instale o programa que importará dados do arquivo `pbf` para o banco de dados:

```bash
apt-get update && apt-get install -y osm2pgsql
```

Certifique-se de que o arquivo `hungary-latest.osm.pbf` esteja localizado na sua pasta `local_folder` e execute o comando de importação:

```bash
osm2pgsql --create --database=Hungary --user=gis --password --host=localhost --port=5432 --hstore /usr/share/gisdata/hungary-latest.osm.pbf
```

No caso da Hungria, levou um minuto e meio para completar este comando. A opção `--create` significa o modo de criação simples de um novo banco de dados. Aliás, além de tudo mais, também existe o modo `--append`, que permite atualizar os dados se eles tiverem mudado:

```bash
osm2pgsql --append --slim OSMFILE
```

A opção `--hstore` diz ao aplicativo para criar adicionalmente um campo `tags` do tipo hstore para armazenar informações adicionais sobre recursos e geometrias.

## Back-end

Então, nossos dados estão prontos para uso. O próximo passo no caminho para a criação de um mapa é a criação do back-end. O objetivo do nosso back-end é gerar `tiles` especiais, geralmente com tamanho `256*256`, dos quais, como um mosaico, o mapa será montado no navegador. Cada tile é identificado exclusivamente por uma combinação de parâmetros como Z, que é o grau de zoom in/out do mapa, X é a linha na matriz de tiles e Y é a coluna. Você pode ler mais sobre a natureza dos tiles [aqui](https://wiki.openstreetmap.org/wiki/Slippy_map_tilenames).

Nosso backend será em ASP.NET Core correspondentemente, então vamos começar com a criação do projeto. Então vamos criar um projeto baseado no modelo `ASP.NET Core MVC` pré-instalado no `Visual Studio`.

Em seguida, instale o pacote NuGet `Aspose.GIS` no projeto que gerará os tiles:

```cmd
dotnet add package Aspose.GIS --version 24.6.0
```

Limpe o projeto de arquivos desnecessários. Para que a estrutura se pareça aproximadamente com a mostrada abaixo:

![Explorador de soluções](project.png)

Em seguida, exclua o conteúdo da pasta wwwroot/lib, pois instalaremos nossas dependências através do `libman`. Abaixo está a estrutura do arquivo `libman.json`:
```json
{
  "version": "1.0",
  "defaultProvider": "cdnjs",
  "libraries": [
    {
      "library": "leaflet@1.9.4",
      "destination": "wwwroot/lib/leaflet/"
    },
    {
      "library": "bootstrap@5.3.3",
      "destination": "wwwroot/lib/bootstrap/",
      "files": [
        "css/bootstrap-reboot.min.css"
      ]
    }
  ]
}
```

Adicionadas as dependências do cliente no arquivo `_Layout.cshtml`:

```razor
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>@ViewData["Title"] - Aspose.GIS.TilesTest</title>
    <link href="~/lib/bootstrap/css/bootstrap-reboot.min.css" rel="stylesheet" />
    @await RenderSectionAsync("Styles", required: false)
</head>
<body>
    @RenderBody()
    @await RenderSectionAsync("Scripts", required: false)
</body>
</html>
```

E também edite `Index.cshtml`:

```razor
@{
    ViewData["Title"] = "Home Page";
}

<div id="map"></div>

@section Styles {
    <link href="~/lib/leaflet/leaflet.min.css" rel="stylesheet" />
    <link href="~/css/map.css" rel="stylesheet" asp-append-version="true"/>
}

@section Scripts {
    <script src="~/lib/leaflet/leaflet.min.js"></script>
    <script src="~/js/map.js" asp-append-version="true"></script>
}
```

Neste caso, `bootstrap-reboot.min.css` redefine as configurações de estilo padrão e `leaflet.min.js` é responsável por renderizar o mapa, ou seja, montar as peças dos tiles em um mapa.
Vamos definir a altura do bloco de mapa para a altura total da área visível no arquivo `map.css`:

```css
#map {
    min-height: 100vh;
}
```

O conteúdo do arquivo `map.js` também é bastante simples, mas um pouco mais interessante:

```javascript
var map = L.map('map').setView([47.59995, 19.36623], 13);
const tiles = L.tileLayer('/tiles/{z}/{x}/{y}.png', {
    maxZoom: 19,
    minZoom: 11
}).addTo(map);
```

Aqui usamos a API da biblioteca leaflet, onde especificamos o ID do bloco de mapa `'map'`, então no método `setView` definimos as coordenadas do local a partir do qual o carregamento inicial do mapa começará e também a escala, por exemplo, 13. Observe o método `tileLayer`, ele aceita uma string de padrão para o pedido de tile ao servidor. Este endereço pode ser absoluto para acessar servidores de tiles de terceiros ou relativo como em nosso caso.

Para implementar o manipulador de solicitação para gerar tiles, vamos primeiro definir uma rota separada no arquivo `Program.cs`:

```csharp
app.MapControllerRoute(name: "tiles",
  pattern: "tiles/{z}/{x}/{y}.png",
  defaults: new { controller = "Tiles", action = "Index" });

app.MapControllerRoute(
  name: "default",
  pattern: "{controller=Home}/{action=Index}/{id?}");
```

Aqui, duas rotas são definidas, a primeira para os tiles e a segunda é a padrão. No caso de `MapControllerRoute`, a ordem importa, então para evitar comportamento inesperado, vale a pena colocar a rota para os tiles antes da rota padrão.

Em seguida, vamos para o manipulador em si. Crie o controlador `TilesController.cs`:

```csharp
public async Task<ActionResult> Index(int z, int x, int y)
```

E então, agora temos todos os dados necessários para calcular a caixa delimitadora coberta pelo tile no sistema de coordenadas correspondente. Na implementação atual, nossos dados no banco de dados são armazenados no sistema de coordenadas Web Mercator. OpenStreetMap por padrão fornece dados neste sistema de coordenadas. Web Mercator é `projection`(forma do sistema de coordenadas) é mais frequentemente usado para mapeamento em vários serviços populares porque cobre quase todo o planeta e as distâncias são medidas em metros, o que simplifica os cálculos, ao contrário de, por exemplo, `WGS84`, onde as distâncias são medidas em graus.

```csharp
VectorLayer inputLayer;
using (var conn = new NpgsqlConnection("Host=127.0.0.1;Username=gis;Password=password;Database=Hungary"))
{
  var builder = new DatabaseDataSourceBuilder();

  builder
    .FromQuery(query)
    .GeometryField("way")
    .AddAttribute("osm_id", AttributeDataType.Long)
    .AddAttribute("addr:housenumber", AttributeDataType.String)
    .AddAttribute("building", AttributeDataType.String)
    .AddAttribute("name", AttributeDataType.String)
    .AddAttribute("source", AttributeDataType.String)
    .AddAttribute("admin_level", AttributeDataType.Integer)
    .AddAttribute("place", AttributeDataType.String)
    .AddAttribute("landuse", AttributeDataType.String)
    .AddAttribute("water", AttributeDataType.String);
  conn.Open();

  var inputLayer = await builder.Build().ReadAsync(conn);
}
```

Temos recebido uma camada que contém todas as geometrias que intersectam nosso tile.

Ok, agora podemos colorir o mapa um pouco, como cidades, corpos d'água ou florestas. Para fazer isso, precisamos dividir nossa única camada em camadas separadas e independentes que correspondam a critérios específicos, como florestas ou rios. Aqui está um exemplo:

```csharp
var cities = inputLayer.Where(x => x.GetValue<string>("place") == "city");
citiesLayer = CopyToNewLayer(cities, inputLayer);

var forest = inputLayer.Where(x => x.GetValue<string>("landuse") == "forest");
forestLayer = CopyToNewLayer(forest, inputLayer);

var water = inputLayer.Where(x => !x.IsValueNull("water"));
waterLayer = CopyToNewLayer(water, inputLayer);
```

Abaixo você verá como usaremos essas camadas. A função `CopyToNewLayer` é auxiliar, ela ajuda a criar novas camadas; para este artigo, não é de grande importância, você pode olhar sua implementação no repositório que eu referenciei no início do artigo.

E agora precisamos apenas renderizar tudo isso em um tile PNG e retorná-lo ao cliente. Este é um código de amostra:

```csharp
using var map = new Map(256, 256);
var pngStream = new MemoryStream();
var labeling = new RuleBasedLabeling
{
  { x => x.GetValue<string>("source") == "polygon",  new SimpleLabeling("addr:housenumber") },
  LabelingRule.CreateElseRule(new SimpleLabeling("name"))
};

map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);            
map.Add(citiesLayer, new SimpleFill { FillColor = Color.PeachPuff }, labeling);
map.Add(forestLayer, new SimpleFill { FillColor = Color.PaleGreen }, labeling);
map.Add(waterLayer, new SimpleFill { FillColor = Color.SkyBlue }, labeling);
map.Add(buildingsLayer, new SimpleFill { FillColor = Color.SandyBrown }, labeling);
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Aqui, um objeto `Map` é criado com o tamanho padrão do tile de 256x256. Essencialmente, um `Map` é uma tela para renderizar o tile. Em seguida, inicializamos um objeto especial para rotulagem, ao qual regras para renderizar texto em formas geométricas desenhadas são passadas, por exemplo, números de casas, nomes de ruas, etc. Neste caso, se não for um polígono e/ou o atributo `addr:housenumber` estiver vazio, os dados serão retirados do atributo `name`.

Um ponto importante é que o objeto Map precisa especificar explicitamente o sistema de coordenadas em que renderizará:

```csharp
map.SpatialReferenceSystem = SpatialReferenceSystem.WebMercator;
```

Em seguida, precisamos definir a área real do tile que deve ser renderizada, não a área expandida que solicitamos ao banco de dados. Para fazer isso, definimos explicitamente a área de renderização através da propriedade `Extent`:

```csharp
map.Extent = new Extent(min_x, min_y, max_x, max_y, SpatialReferenceSystem.WebMercator);
```

E então adicionamos sequencialmente camadas ao tile. A primeira é adicionada abaixo de todas e a última está no topo.

E finalmente precisamos apenas renderizar o tile como um fluxo de bytes na memória, então redefinir o fluxo para o início e passar o fluxo para a plataforma ASP.NET Core para transferência posterior ao cliente:

```csharp
map.Render(AbstractPath.FromStream(pngStream), Renderers.Png);

pngStream.Seek(0, SeekOrigin.Begin);

return File(pngStream, "image/png");
```

Esperamos ter conseguido transmitir as ideias e técnicas básicas de construção de mapas a você. Desejamos boa sorte em seus experimentos.