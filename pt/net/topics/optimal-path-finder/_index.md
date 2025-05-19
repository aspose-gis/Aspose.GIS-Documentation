---
title: "Localizador de Caminho Ótimo"
type: docs
url: /pt/net/optimal-path-finder
weight: 70
---

## Resumo

A busca pelo caminho mais curto em uma rede rodoviária é um processo de análise destinado a determinar a maneira mais eficiente de viajar entre pontos em um mapa. Esta ferramenta pode ser útil para criar rotas ideais com várias paradas ou medir a distância e o tempo de viagem entre diferentes locais. Com cada chamada, nossa tecnologia pode encontrar rotas ótimas para um ou vários veículos. Por exemplo, ela pode ajudar os motoristas a encontrar as rotas ideais para entregar mercadorias ou determinar a distância ideal de deslocamento de casa para o trabalho para diferentes passageiros.

## Capacidades do Algoritmo

Nossa biblioteca fornece a capacidade de construir a rota mais **ótima entre dois pontos** em um mapa. Possui os seguintes recursos principais:

1. Busca pelo caminho ótimo no mapa, considerando trilhas e obstáculos: Levamos em consideração não apenas estradas, mas também caminhos off-road, como trilhas, calçadas e obstáculos que podem afetar a escolha do caminho ideal.

2. Busca pelo caminho ótimo somente em estradas: Se você precisar encontrar uma rota exclusivamente em estradas, fornecemos esse recurso. Isso é útil, por exemplo, para veículos restritos a viajar apenas em estradas.

3. Definição de diferentes velocidades para estradas: Temos a capacidade de atribuir diferentes velocidades a diferentes estradas. Por exemplo, velocidades mais altas podem ser definidas para rodovias principais e velocidades mais baixas para faixas estreitas.

4. Definição de obstáculos retangulares: Você pode definir obstáculos retangulares no mapa que precisam ser levados em consideração ao construir o caminho ideal. Isso é útil quando existem obstáculos conhecidos, como edifícios ou lagos (sua aproximação).

5. Limitação do raio de busca para estradas: Você pode restringir o raio de busca para estradas a fim de reduzir o tempo de busca e se concentrar apenas em uma área específica.

6. Controle de desempenho e precisão: Fornecemos a capacidade de controlar o desempenho e a precisão do algoritmo. Você pode ajustá-lo para alcançar o equilíbrio desejado entre velocidade de pesquisa e precisão da construção da rota.

Em seguida, forneceremos uma descrição mais detalhada de cada um desses recursos e examinaremos exemplos de suas aplicações.

## Abordagem à Solução

Embora a busca de caminhos seja uma tarefa não trivial, existem vários algoritmos bons e confiáveis que são reconhecidos na comunidade de desenvolvimento.

Em nossa implementação, usamos um algoritmo de Lee modificado. Temos uma grade de células no plano. A partir do ponto inicial, uma onda se propaga em 8 direções (incluindo diagonais) para as células vizinhas, calculando o tempo necessário para alcançá-las. Uma célula vizinha pode conter um obstáculo ou uma estrada. As estradas podem ter diferentes coeficientes de velocidade. Assim, "marcamos" nossa grade com o tempo que leva para alcançar cada célula a partir da célula inicial dentro de um determinado raio ou até atingir o ponto de destino. Se alcançarmos o ponto de destino, construiremos um caminho reverso usando nossa grade.

Para determinar a rota ideal na rede rodoviária, várias etapas precisam ser tomadas. Primeiro, você precisa definir as estradas e especificar a velocidade de movimento em cada uma delas. Você também deve considerar a presença de obstáculos artificiais e naturais que podem afetar o percurso do caminho. Depois disso, você precisa especificar os pontos inicial e final da busca. Uma vez que essas etapas preliminares sejam concluídas, você pode prosseguir com a busca real do caminho. O resultado será um caminho representado, por exemplo, como uma lista de coordenadas de pontos.

É importante observar que o caminho ideal pode depender do modo de transporte escolhido, pois a velocidade de movimento e o conjunto de obstáculos podem variar. Portanto, diferentes conjuntos de estradas e obstáculos devem ser usados para cada tipo de transporte ao procurar o caminho ideal.

## Projeto de Demonstração no GitHub

Para entender melhor a funcionalidade da nossa biblioteca, vamos considerar [um exemplo de seu uso](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Este código ilustra como configurar estradas e obstáculos no algoritmo de busca de caminhos e encontrar a rota ideal.

O exemplo consiste nas seguintes etapas:

1. Criando uma lista de informações sobre estradas (RoadInfo), que inclui informações sobre o segmento da estrada (Segment) e a velocidade de movimento (Velocity).
2. Adicionando estradas rápidas à lista.
3. Adicionando anéis lentos à lista.
4. Criando um gerador de camadas de vias (WayLayerGenerator) e adicionando estradas ao gerador.
5. Buscando vários caminhos do ponto inicial (startPoint) para os pontos finais (goalPoint01, goalPoint02, goalPoint03) usando o raio especificado (radius).
6. Preparando uma camada de estradas (roadsLayer) para exibição no mapa e adicionando objetos de estrada.
7. Preparando uma camada de vias (wayLayer) para exibição no mapa e criando objetos geométricos para cada caminho encontrado.
8. [Exibindo o mapa](https://docs.aspose.com/gis/net/how-to-draw-geometry/) usando a função ShowMap, salvando o mapa no caminho especificado.

Este código constrói e exibe caminhos de estrada no mapa para pontos especificados usando informações sobre estradas e o gerador de camadas de vias.

## Opções de Busca

A busca de caminhos é realizada usando a classe **WayLayerGenerator** localizada no namespace Aspose.Gis.GeoTools.WayAnalyzer.

A classe WayLayerGenerator possui o método **FindTheWay** para encontrar o caminho do ponto inicial ao alvo. Para criar uma instância da classe WayLayerGenerator, passamos os WayOptions como parâmetros (todos os parâmetros são opcionais):

- StartPoint: O ponto inicial

- GoalPoint: O ponto de destino

- Radius: O raio de busca

- Scale: A escala da grade

- IsMoveOnlyRoad: Se deve buscar o caminho apenas em estradas

O recurso notável aqui é o parâmetro Scale. Se ele for especificado no construtor, fixamos uma escala constante para buscas subsequentes. Se o parâmetro Scale não estiver definido, mas StartPoint e GoalPoint estiverem definidos, calculamos a escala como a distância entre os pontos inicial e final dividida por 100. Em todos os outros casos, o valor padrão de Scale é 1. Para usuários experientes, é melhor definir Scale ou definir StartPoint e GoalPoint diretamente para representar estradas e obstáculos na grade com mais eficiência (especialmente se houver muitos deles).

Para usar o método FindTheWay, precisamos especificar os pontos inicial e final. Também podemos definir o raio de busca (a distância até a qual a onda se propaga). Por padrão, o raio é calculado como a distância entre os pontos inicial e final multiplicada por 3. Os pontos inicial e final podem estar próximos ou muito distantes um do outro, então, com base na distância entre eles, calculamos a escala de nossa grade. Se a escala atual não corresponder à anterior, recalculamos a grade. A escala pode ser fixada usando o parâmetro Scale. Nesse caso, ela não é computada e a grade não é recalculada.

Antes de iniciar a busca, precisamos definir o mapa de estradas e obstáculos usando os métodos AddRoad e AddBlock correspondentes da classe WayLayerGenerator.

Para o método **AddRoad**, precisamos especificar:

- startPoint: O ponto inicial da estrada

- endPoint: O ponto final da estrada

- velocity: A velocidade de movimento na estrada

Para o método **AddBlock**, precisamos especificar:

- x: A coordenada x do canto superior esquerdo do bloco

- y: A coordenada y do canto superior esquerdo do bloco

- sizeX: O tamanho no eixo x

- sizeY: O tamanho no eixo y

Esses métodos nos permitem definir o mapa de estradas e obstáculos antes de iniciar o processo de busca de caminhos.

## Exemplos de Código

Aqui estão alguns exemplos de código que ilustram como configurar estradas e obstáculos no algoritmo de busca de caminhos e encontrar a rota ideal.

Exemplo 1: Encontrando um caminho entre os pontos inicial e final.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Exemplo 2**: Definindo o parâmetro Scale e tendo coordenadas negativas para o ponto.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Exemplo 3**: Definindo o parâmetro IsMoveOnlyRoad e o raio de busca.

```
WayOptions mapGeneratorOptions = new WayOptions();
mapGeneratorOptions.IsMoveOnlyRoad = true;
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddRoad(new Point(100, 100), new Point(140, 150), 10);
generator.AddRoad(new Point(140, 150), new Point(190, 100), 10);
Point startPoint = new Point(100, 100);
Point goalPoint = new Point(190, 100);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 100);
```

**Exemplo 4**: Definindo o parâmetro Scale para uma busca mais rápida.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Exemplo 5**: Exemplo de busca múltipla.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
generator.AddBlock(200, 1700, 1500, 100, 0);
generator.AddBlock(1700, 200, 100, 1600, 0);
generator.AddBlock(200, 200, 1500, 100, 0);
generator.AddRoad(new Point(1000, 1150), new Point(200, 600), 10);
generator.AddRoad(new Point(50, 450), new Point(150, 1850), 10);

Point startPoint = new Point(1000, 1000);
Point goalPoint = new Point(1900, 1000);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 3500);

Point startPoint = new Point(50, 50);
Point goalPoint = new Point(70, 70);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

Esses exemplos de código constroem e exibem caminhos de estrada no mapa para pontos especificados, usando informações sobre estradas e o gerador de camadas de vias.

**Em resumo**, o localizador de caminho ótimo é uma ferramenta poderosa para analisar redes rodoviárias e determinar as rotas mais eficientes entre pontos em um mapa. Ele leva em consideração vários fatores, como tipos de estradas, obstáculos e diferentes velocidades, para calcular o caminho ideal. Com a capacidade de buscar caminhos tanto em estradas quanto em trilhas off-road, bem como controlar o raio de busca e ajustar o desempenho e a precisão, este algoritmo fornece uma solução versátil para otimização de rotas. Ao considerar diferentes modos de transporte e ajustar conjuntos de estradas e obstáculos de acordo, ele pode ser usado em vários cenários, como planejamento de entrega ou otimização de deslocamento. Os exemplos de código e explicações fornecidas demonstram as capacidades do algoritmo e as etapas envolvidas na sua utilização. Em última análise, o localizador de caminho ótimo oferece uma maneira robusta de encontrar as rotas mais eficientes e melhorar a navegação em uma rede rodoviária.