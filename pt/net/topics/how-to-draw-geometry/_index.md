---
title: "Como Desenhar Geometria em um Mapa"
type: docs
url: /pt/net/how-to-draw-geometry
weight: 70
---

Para criar e exibir objetos geométricos em um mapa, você precisa começar por **criar um objeto de geometria**. Existem dois métodos que você pode usar:

- **Construtor para Cada Tipo de Feature de Geometria**
Este método envolve o uso de um construtor personalizado para cada tipo de feature de geometria. Por exemplo, para criar um ponto, você usaria o seguinte código:

```
Point point = new Point(40.7128, -74.006);
```

No entanto, este método pode se tornar desafiador e complicado de gerenciar ao criar objetos complexos como polilinhas ou coleções. Como resultado, o desenvolvedor pode precisar adicionar muitas linhas de código, causando uma queda na legibilidade do código. Garantir a integridade dos dados durante a inicialização também pode ser difícil. Por exemplo, considere o seguinte exemplo que cria um polígono com um buraco dentro:

```
Polygon polygon = new Polygon();

LinearRing ring = new LinearRing();
ring.AddPoint(50.02, 36.22);
ring.AddPoint(49.99, 36.26);
ring.AddPoint(49.97, 36.23);
ring.AddPoint(49.98, 36.17);
ring.AddPoint(50.02, 36.22);

LinearRing hole = new LinearRing();
hole.AddPoint(50.00, 36.22);
hole.AddPoint(49.99, 36.20);
hole.AddPoint(49.98, 36.23);
hole.AddPoint(50.00, 36.24);
hole.AddPoint(50.00, 36.22);

polygon.ExteriorRing = ring;
polygon.AddInteriorRing(hole);
```

Outra desvantagem desta abordagem é a falta de uniformidade dos dados para inicialização. Você não pode criar um repositório de constantes ou arquivos dentro do seu projeto.

- **WKT (Well-Known Text)**
Este método envolve gerar geometria a partir de WKT (Well-Known Text), que oferece uma maneira padronizada de criar geometrias. O seguinte código demonstra como criar um ponto e uma linha:

```
var point = Geometry.FromText("POINT (23.5, 25.3)");
var line = Geometry.FromText("LINESTRING Z (0.1 0.2 0.3, 1 2 1, 12 23 2)");
```

Embora esta abordagem possa reduzir ligeiramente o desempenho devido à necessidade de analisar a string, ela simplifica a criação de objetos mais complexos.

Você pode encontrar mais detalhes sobre WKT no seguinte artigo: "Exportando e Importando Dados de/para WKT e WKB."

Exibindo Objetos Geométricos no Mapa
Depois de ter criado um objeto geométrico, o próximo passo é exibi-lo no mapa. Embora o mapa possa exibir camadas carregadas de várias fontes e formatos, a InMemoryLayer é uma camada que não requer uma fonte.

**Para exibir seu objeto geométrico**, você pode criar uma InMemoryLayer e adicionar o objeto a ela:

```
using (var layer = Drivers.InMemory.CreateLayer())
{
     Feature feature = layer.ConstructFeature();
     feature.Geometry = Geometry.FromText("POINT (23.5, 25.3)");
     layer.Add(feature);
}
```

Agora você pode **exibir esta camada no mapa e criar um arquivo em um dos formatos suportados**, como SVG, com o seguinte código:

```
using (var map = new Map(500, 500))
{
     map.Add(layer);
     map.Render(filesPath, Renderers.Svg);
}
```

Depois de ter adicionado a camada e exibido-a no mapa, você pode salvá-la em qualquer um dos formatos suportados. Neste exemplo, o formato SVG é escolhido para evitar problemas potenciais com suporte ao Bitmap. É importante observar que Net 6.0 tem suporte limitado ao Bitmap, o que pode resultar em restrições como a incapacidade de renderizar imagens Bitmap usando Blazor WebAsm no lado do cliente. Portanto, ao escolher um formato para salvar seu mapa, é importante considerar as limitações da plataforma de destino e selecionar um formato compatível com ela.

O artigo explica como criar e exibir objetos geométricos em um mapa com um estilo padrão e simples. No entanto, a biblioteca Aspose oferece uma ampla gama de opções de estilo que podem ser personalizadas para atender às suas necessidades. Para explorar essas opções, recomendamos consultar a [documentação do Aspose.MapRendering]( https://docs.aspose.com/gis/net/map-rendering/), que fornece informações detalhadas sobre como usar diferentes técnicas de estilo para melhorar o apelo visual do seu mapa.

**Em resumo**, para criar objetos geométricos em um mapa, você pode usar um construtor para cada tipo de feature de geometria ou gerar geometria a partir de WKT. Para exibir o objeto, coloque-o em uma camada e exiba a camada em um mapa com estilo padrão do mapa. Salve o mapa em um formato suportado, como SVG, e use nossa biblioteca para explorar opções de estilo. Além disso, nossa biblioteca oferece uma oportunidade de ver um exemplo finalizado clicando no [link]( https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Geo.Geometry.Viewer) fornecido na documentação, o que pode ajudá-lo a entender como implementar essas técnicas em seus próprios projetos.
