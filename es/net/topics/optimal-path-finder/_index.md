---
title: "Optimizador de Ruta Óptima"
type: docs
url: /es/net/optimal-path-finder
weight: 70
---

## Resumen

La búsqueda del camino más corto en una red vial es un proceso de análisis destinado a determinar la forma más eficiente de viajar entre puntos en un mapa. Esta herramienta puede ser útil para crear rutas óptimas con múltiples paradas o medir la distancia y el tiempo de viaje entre diferentes ubicaciones. Con cada llamada, nuestra tecnología puede encontrar rutas óptimas para uno o varios vehículos. Por ejemplo, puede ayudar a los conductores a encontrar las rutas óptimas para entregar mercancías o determinar la distancia de desplazamiento óptima desde casa al trabajo para diferentes pasajeros.

## Capacidades del Algoritmo

Nuestra biblioteca proporciona la capacidad de construir la ruta más **óptima entre dos puntos** en un mapa. Tiene las siguientes características principales:

1. Búsqueda del camino óptimo en el mapa, considerando senderos y obstáculos: Tenemos en cuenta no solo las carreteras sino también caminos fuera de carretera como senderos, pasarelas peatonales y obstáculos que pueden afectar la elección del camino óptimo.

2. Búsqueda del camino óptimo solo en carreteras: Si necesita encontrar una ruta exclusivamente en carreteras, proporcionamos esta capacidad. Esto es útil, por ejemplo, para vehículos restringidos a viajar solo por carretera.

3. Establecimiento de diferentes velocidades para las carreteras: Tenemos la capacidad de asignar diferentes velocidades a diferentes carreteras. Por ejemplo, se pueden establecer velocidades más altas para las principales autopistas y velocidades más bajas para los carriles estrechos.

4. Establecimiento de obstáculos rectangulares: Puede definir obstáculos rectangulares en el mapa que deben tenerse en cuenta al construir el camino óptimo. Esto es útil cuando hay obstáculos conocidos como edificios o lagos (su aproximación).

5. Limitación del radio de búsqueda para carreteras: Puede restringir el radio de búsqueda para carreteras con el fin de reducir el tiempo de búsqueda y centrarse solo en un área específica.

6. Control del rendimiento y la precisión: Proporcionamos la capacidad de controlar el rendimiento y la precisión del algoritmo. Puede ajustarlo para lograr el equilibrio deseado entre la velocidad de búsqueda y la precisión de la construcción de la ruta.

A continuación, proporcionaremos una descripción más detallada de cada una de estas características y examinaremos ejemplos de sus aplicaciones.

## Enfoque a la Solución

Aunque encontrar el camino es una tarea no trivial, existen varios algoritmos buenos y confiables que son reconocidos en la comunidad de desarrollo.

En nuestra implementación, utilizamos un algoritmo de Lee modificado. Tenemos una cuadrícula de celdas en el plano. Desde el punto de partida, una onda se propaga en 8 direcciones (incluidas las diagonales) a las celdas vecinas, calculando el tiempo requerido para llegar a cada una de ellas. Una celda vecina puede contener un obstáculo o una carretera. Las carreteras pueden tener diferentes coeficientes de velocidad. Por lo tanto, "marcamos" nuestra cuadrícula con el tiempo que se tarda en alcanzar cada celda desde la celda inicial dentro de un cierto radio o hasta llegar al punto objetivo. Si llegamos al punto objetivo, construimos un camino inverso utilizando nuestra cuadrícula.

Para determinar la ruta óptima en la red vial, es necesario seguir varios pasos. Primero, debe definir las carreteras y especificar la velocidad de movimiento en cada una de ellas. También debe considerar la presencia de obstáculos artificiales y naturales que puedan afectar el recorrido del camino. Después de eso, debe especificar los puntos de inicio y destino de la búsqueda. Una vez completados estos pasos preliminares, puede proceder a la búsqueda real del camino. El resultado será un camino representado, por ejemplo, como una lista de coordenadas de puntos.

Es importante tener en cuenta que el camino óptimo puede depender del modo de transporte elegido, ya que la velocidad de movimiento y el conjunto de obstáculos pueden variar. Por lo tanto, se deben utilizar diferentes conjuntos de carreteras y obstáculos al buscar el camino óptimo para cada tipo de transporte.

## Proyecto de Demostración en GitHub

Para comprender mejor la funcionalidad de nuestra biblioteca, consideremos [un ejemplo de su uso](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Tools.Paths). Este código ilustra cómo configurar carreteras y obstáculos en el algoritmo de búsqueda del camino y encontrar la ruta óptima.

El ejemplo consta de los siguientes pasos:

1. Creación de una lista de información de carreteras (RoadInfo), que incluye información sobre el segmento de carretera (Segment) y la velocidad de movimiento (Velocity).
2. Adición de carreteras rápidas a la lista.
3. Adición de anillos lentos a la lista.
4. Creación de un generador de capas de vías (WayLayerGenerator) y adición de carreteras al generador.
5. Búsqueda de múltiples caminos desde el punto de partida (startPoint) hasta los puntos objetivo (goalPoint01, goalPoint02, goalPoint03) utilizando el radio especificado (radius).
6. Preparación de una capa de carreteras (roadsLayer) para mostrar en el mapa y adición de objetos de carretera.
7. Preparación de una capa de vías (wayLayer) para mostrar en el mapa y creación de objetos geométricos para cada camino encontrado.
8. [Mostrar el mapa](https://docs.aspose.com/gis/net/how-to-draw-geometry/) utilizando la función ShowMap, guardando el mapa en la ruta especificada.

Este código construye y muestra caminos de carretera en el mapa para puntos especificados utilizando información de carreteras y el generador de capas de vías.

## Opciones de Búsqueda

La búsqueda del camino se realiza utilizando la clase **WayLayerGenerator** ubicada en el espacio de nombres Aspose.Gis.GeoTools.WayAnalyzer.

La clase WayLayerGenerator tiene el método **FindTheWay** para encontrar el camino desde el punto de partida hasta el objetivo. Para crear una instancia de la clase WayLayerGenerator, pasamos los WayOptions como parámetros (todos los parámetros son opcionales):

- StartPoint: El punto de partida

- GoalPoint: El punto objetivo

- Radius: El radio de búsqueda

- Scale: La escala de la cuadrícula

- IsMoveOnlyRoad: Si se debe buscar el camino solo en carreteras

La característica notable aquí es el parámetro Scale. Si se especifica en el constructor, fijamos una escala constante para búsquedas posteriores. Si el parámetro Scale no está establecido pero StartPoint y GoalPoint están establecidos, calculamos la escala como la distancia entre los puntos de inicio y destino dividida por 100. En todos los demás casos, el valor predeterminado de Scale es 1. Para usuarios experimentados, es mejor establecer Scale o establecer directamente StartPoint y GoalPoint para representar más eficientemente las carreteras y los obstáculos en la cuadrícula (especialmente si hay muchos de ellos).

Para utilizar el método FindTheWay, necesitamos especificar los puntos de inicio y destino. También podemos establecer el radio de búsqueda (la distancia a la que se propaga la onda). Por defecto, el radio se calcula como la distancia entre los puntos de inicio y destino multiplicada por 3. Los puntos de inicio y destino pueden estar cerca o muy lejos uno del otro, por lo que en función de la distancia entre ellos, calculamos la escala de nuestra cuadrícula. Si la escala actual no coincide con la anterior, recalculamos la cuadrícula. La escala se puede fijar utilizando el parámetro Scale. En este caso, no se calcula y la cuadrícula no se recalcula.

Antes de comenzar la búsqueda, necesitamos definir el mapa de carreteras y obstáculos utilizando los métodos correspondientes AddRoad y AddBlock de la clase WayLayerGenerator.

Para el método **AddRoad**, necesitamos especificar:

- startPoint: El punto de partida de la carretera

- endPoint: El punto final de la carretera

- velocity: La velocidad de movimiento en la carretera

Para el método **AddBlock**, necesitamos especificar:

- x: La coordenada x de la esquina superior izquierda del bloque

- y: La coordenada y de la esquina superior izquierda del bloque

- sizeX: El tamaño en el eje x

- sizeY: El tamaño en el eje y

Estos métodos nos permiten definir el mapa de carreteras y obstáculos antes de comenzar el proceso de búsqueda del camino.

## Ejemplos de Código

Aquí hay algunos ejemplos de código que ilustran cómo configurar carreteras y obstáculos en el algoritmo de búsqueda del camino y encontrar la ruta óptima.

Ejemplo 1: Encontrar un camino entre los puntos de inicio y destino.

```
WayOptions mapGeneratorOptions = new WayOptions();
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(5, 7);
Point goalPoint = new Point(15, 13);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Ejemplo 2**: Establecimiento del parámetro de escala y teniendo coordenadas negativas para el punto.

```
WayOptions mapGeneratorOptions = new WayOptions(1);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(-50, -70);
Point goalPoint = new Point(150, 130);
var resultWay = generator.FindTheWay(startPoint, goalPoint);
```

**Ejemplo 3**: Establecimiento del parámetro IsMoveOnlyRoad y radio de búsqueda.

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

**Ejemplo 4**: Establecimiento del parámetro de escala para una búsqueda más rápida.

```
WayOptions mapGeneratorOptions = new WayOptions(10);
var generator = new WayLayerGenerator(mapGeneratorOptions);
Point startPoint = new Point(50, 70);
Point goalPoint = new Point(1650, 1300);
var resultWay = generator.FindTheWay(startPoint, goalPoint, 2500);
```

**Ejemplo 5**: Ejemplo de búsqueda múltiple.

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

Estos ejemplos de código construyen y muestran caminos de carretera en el mapa para puntos especificados, utilizando información de carreteras y un generador de capas de vías.

**En resumen**, el optimizador de ruta óptima es una herramienta poderosa para analizar redes viales y determinar las rutas más eficientes entre puntos en un mapa. Tiene en cuenta varios factores como los tipos de carreteras, los obstáculos y diferentes velocidades para calcular el camino óptimo. Con la capacidad de buscar caminos tanto en carreteras como fuera de ellas, así como controlar el radio de búsqueda y ajustar el rendimiento y la precisión, este algoritmo proporciona una solución versátil para la optimización de rutas. Al considerar diferentes modos de transporte y ajustar los conjuntos de carreteras y obstáculos en consecuencia, se puede utilizar en varios escenarios como la planificación de entregas o la optimización del desplazamiento diario. Los ejemplos de código y las explicaciones proporcionadas demuestran las capacidades del algoritmo y los pasos involucrados en su utilización. En última instancia, el optimizador de ruta óptima ofrece una forma sólida de encontrar las rutas más eficientes y mejorar la navegación en una red vial.