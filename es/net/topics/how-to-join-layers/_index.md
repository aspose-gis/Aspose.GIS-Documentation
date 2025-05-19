---
title: "Cómo unir capas usando geometría o atributos"
type: docs
url: /es/net/how-to-join-layers
weight: 70
---

## Resumen

En los SIG, las uniones son un mecanismo potente para combinar información de diferentes capas basándose en un atributo común o una relación espacial. Las uniones le permiten fusionar datos de atributos de una capa (la capa fuente) con otra capa (la capa destino) utilizando un campo común o una ubicación espacial. La primera es la unión de datos por clave (atributo en la tabla). Utilizando un campo común, como una clave única, puede vincular registros en una tabla con registros en otra tabla. El segundo enfoque es la unión de datos por ubicación (espacialmente). Admitimos ambos enfoques y le ofrecemos la oportunidad de utilizarlos según sus necesidades.

Supongamos que ha recibido datos que describen el cambio porcentual en la población para diferentes distritos, y desea generar varios mapas de crecimiento de la población basados ​​en esta información. Si bien sus datos de población se almacenan en una tabla en su base de datos y comparten un campo común con su capa, puede unir estos datos a sus objetos geográficos y utilizar campos adicionales para etiquetar, categorizar, consultar o analizar los objetos de la capa.

Normalmente, realiza uniones de datos basadas en un valor de campo que existe en ambas tablas. Los nombres de los campos no necesariamente tienen que coincidir, pero los tipos de datos deben ser iguales: números con números, cadenas con cadenas, y así sucesivamente. Puede ejecutar la unión de datos utilizando la herramienta de geoprocesamiento "Add Join". Al unir atributos, los campos unidos se agregan dinámicamente a la tabla existente. Las propiedades del campo como alias, visibilidad y formato numérico se conservan al agregar o eliminar la unión.

## Capacidades para unirse por campo clave

- Este enfoque le permite **vincular registros de diferentes tablas** basándose en un campo clave común. Puede especificar el campo clave que se utilizará para la comparación con el fin de establecer la relación entre los registros. Esto es particularmente útil cuando necesita fusionar datos basándose en un identificador u otro atributo único.

Especificando el método para comparar datos basándose en el campo clave:

- Puede definir **diferentes métodos de comparación** para el campo clave al fusionar datos. Por ejemplo, puede optar por tener una coincidencia exacta, comparar basándose en un patrón o dentro de un rango de valores. Esto permite una determinación más precisa de las relaciones entre los registros y le brinda control sobre el proceso de fusión de datos.

Especificando una lista de nombres de atributos que se van a fusionar:

- Al fusionar datos, puede especificar **atributos específicos** que deben fusionarse. Esto le permite elegir solo los atributos necesarios para la fusión y administrar la estructura de la tabla resultante.

## Capacidades para unirse usando geometría

- Este enfoque le permite vincular datos basándose en su **ubicación espacial**. Puede definir un radio de búsqueda dentro del cual se buscarán los objetos geométricos más cercanos para fusionarlos. Esto es útil cuando necesita unir datos basándose en su posición geográfica.

Controlando el radio de búsqueda para encontrar objetos geométricos más cercanos:

- Puede controlar **el radio de búsqueda** al fusionar datos basándose en la ubicación. Al especificar un valor de radio, determina la distancia dentro de la cual se buscarán los objetos más cercanos para fusionarlos. Esto le brinda control sobre qué objetos participarán en el proceso de fusión de datos según su relación espacial.

## Proyecto de demostración

Para comprender mejor la funcionalidad de nuestra biblioteca, consideremos [un ejemplo de su uso](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Apps/Geo.Layers.Join). Este código ilustra cómo unir capas vectoriales por atributos o geometría.

El código proporcionado consta de dos métodos, JoinByIndex() y JoinByCoords(), que demuestran operaciones de unión de datos utilizando una clase LayerConstructor.

En el método JoinByIndex():

- Se crean listas de geometrías con atributos asociados.

- Se inicializa un objeto LayerConstructor.

- El método crea una capa vectorial y una capa de geometría utilizando las geometrías proporcionadas.

- La capa de geometría se une basándose en un identificador único ("Id") utilizando el método JoinLayersById().

- La capa vectorial resultante unida se devuelve.

En el método JoinByCoords():

- Se crean listas de geometrías con atributos asociados.

- Se inicializa un objeto LayerConstructor.

- Se crean capas de geometría utilizando las geometrías proporcionadas.

- Las capas de geometría se unen basándose en coordenadas coincidentes utilizando el método JoinLayersByCoords().

- La capa vectorial resultante unida se devuelve.

En resumen, estos métodos muestran dos enfoques diferentes para unir datos: uno basado en un identificador único y el otro basado en coordenadas coincidentes. La clase LayerConstructor facilita estas operaciones de unión de datos.

## Opciones de unión para índice

La clase JoinOptions proporciona un conjunto de opciones para configurar la unión de capas. Profundicemos en cada opción:

- **JoinAttributeName**: Esta opción le permite especificar el nombre del atributo de la capa unida cuyo valor se utilizará en la comparación de la condición. Establece la conexión entre las dos capas basándose en este atributo.

- **TargetAttributeName**: Con esta opción, puede especificar el nombre del atributo de la capa principal que se comparará con el atributo de la capa unida. Ayuda a determinar las características coincidentes entre las capas.

- **JoinAttributeNames**: Esta opción le permite especificar una lista de nombres de atributos que desea unir. Si esta lista se deja vacía o se establece en nulo, todos los atributos de la capa unida se incluirán en la operación de unión. Sin embargo, al seleccionar nombres de atributos específicos, puede controlar los atributos que se unen, lo cual puede ser útil para optimizar el uso de la memoria y el tiempo de procesamiento.

- **ConditionComparer**: Esta opción le permite definir una lógica personalizada para comparar valores de atributos entre las características de las dos capas. Por defecto, utiliza el comparador EqualityComparer.Default, que comprueba si hay igualdad. Sin embargo, puede proporcionar su propio comparador personalizado que implemente IEqualityComparer para requisitos de comparación más especializados.

- **JoinedAttributesPrefix**: Esta opción le permite especificar un prefijo de cadena para los nombres de los atributos de la capa unida. El valor predeterminado es "joined_", lo que significa que los atributos unidos se prefijarán con "joined_" en la capa unida resultante. Este prefijo ayuda a diferenciar los atributos unidos de los atributos originales de la capa principal.

La clase JoinOptions proporciona flexibilidad y control sobre varios aspectos del proceso de unión de capas. Puede especificar los atributos para unir, personalizar la lógica de comparación y definir un prefijo para los atributos unidos resultantes. Estas opciones le permiten adaptar la operación de unión a sus necesidades específicas y obtener información significativa de las capas fusionadas.

## Opciones de unión para geometría

La clase **JoinByGeometryOptions** representa opciones para unir capas basándose en la geometría. Exploremos la funcionalidad de cada opción:

- **Radius**: Esta opción especifica el radio dentro del cual se buscará la geometría unida. Determina la proximidad dentro de la cual las características de la capa principal se harán coincidir con las características de la capa unida basándose en su relación espacial.

- **ConditionComparer**: Esta opción le permite definir una lógica personalizada para comparar valores de atributos de las características de las dos capas. Por defecto, utiliza EqualityComparer.Default, que comprueba si hay igualdad. Sin embargo, puede proporcionar su propio comparador personalizado que implemente IEqualityComparer para requisitos de comparación más específicos.

- **JoinedAttributesPrefix**: Esta opción le permite especificar un prefijo de cadena para los nombres de los atributos de la capa unida. El valor predeterminado es "joined_", lo que significa que los atributos unidos se prefijarán con "joined_" en la capa unida resultante. Este prefijo ayuda a diferenciar los atributos unidos de los atributos originales de la capa principal.

La clase JoinByGeometryOptions proporciona los medios para personalizar el proceso de unión de capas basándose en su relación espacial. Al especificar un radio de búsqueda, puede controlar la extensión dentro de la cual se harán coincidir las geometrías. Esto permite ajustar la operación de unión basándose en la proximidad deseada entre las características. La opción de proporcionar un comparador personalizado le brinda flexibilidad para comparar valores de atributos, y la opción de prefijar los atributos unidos ayuda a diferenciarlos en la capa unida resultante.

Utilizando estas opciones, puede realizar una fusión de datos con conocimiento espacial y obtener información de las capas unidas que se basa en su proximidad espacial y valores de atributos.

## Resumen

El mecanismo de unión de datos en los SIG permite combinar objetos geométricos con sus respectivos atributos de diferentes capas. Esto proporciona la capacidad de analizar y extraer información basándose en relaciones espaciales y de atributos dentro de los datos. Las opciones disponibles permiten personalizar el proceso de unión para satisfacer requisitos específicos y necesidades de análisis en los datos del SIG.

La unión de datos facilita varias tareas, que incluyen:

- Encontrar objetos que cumplan criterios espaciales específicos, como identificar todos los edificios dentro de un radio de 500 metros de un punto específico.

- Combinar datos geográficos para crear una visión general más completa e informativa de una situación.

- Analizar valores de atributos de objetos basándose en condiciones espaciales específicas para identificar tendencias y patrones.

Las opciones de unión de datos permiten una configuración precisa del proceso de coincidencia de objetos. Estas opciones incluyen la selección de los atributos a unir, la definición de una lógica personalizada para comparar valores de atributos y la adición de un prefijo a los nombres de los atributos de los datos unidos. Estas opciones brindan flexibilidad y adaptabilidad al proceso de unión, atendiendo a requisitos específicos y a los objetivos del análisis de datos en los SIG.

El mecanismo de unión de datos juega un papel importante en la integración y el análisis de datos geográficos, lo que produce una comprensión más completa de la naturaleza espacial y de atributos de los objetos bajo investigación.