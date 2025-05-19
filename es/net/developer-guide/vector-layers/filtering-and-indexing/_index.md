---
title: Filtrado e Indexación de Capas Vectoriales GIS en C#
linktitle: Filtrado e Indexación
second_title: Aspose.GIS para .NET
type: docs
url: /es/filtering-and-indexing/
weight: 30
description: Con la Biblioteca o API de GIS C# .NET, puede filtrar capas vectoriales GIS por valores de atributo o límites espaciales. También puede usar índices para acelerar el filtrado y las consultas espaciales.
---

Con Aspose.GIS para .NET puede filtrar capas por valores de atributo o límites espaciales. También puede usar índices para acelerar el filtrado y las consultas espaciales.
## **Índice de atributos**
### **Filtrar Sin Índice**
Así es como se filtra una capa por los valores de un atributo:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filtrar Con Índice**
El código anterior está bien siempre que la capa se filtre solo una vez. Pero, si es probable que la capa se consulte varias veces, podemos beneficiarnos de los índices de atributos. Toma algo de tiempo construir un índice de atributos, pero se puede reutilizar varias veces para acelerar el filtrado.

El siguiente ejemplo utiliza un archivo de índice de atributos para acelerar el filtrado de capas por valores del atributo:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Guardar Características Filtradas**
Las características filtradas se pueden guardar en capas:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Renderizar Características Filtradas**
También es posible renderizar características filtradas. El siguiente ejemplo utiliza un índice de atributos para seleccionar rápidamente todas las características con una población superior a 2000 y agregarlas al mapa:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Índice Espacial**
Los índices espaciales se utilizan para acelerar las consultas espaciales. Al igual que los índices de atributos, los índices espaciales se reutilizan después de su creación.
### **Encontrar Características Más Cercanas a un Punto**
Así es como se utiliza un índice espacial para acelerar la búsqueda de la característica más cercana a algún punto:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Seleccionar Características que Intersecan con una Geometría**
El siguiente ejemplo utiliza un índice espacial para acelerar la selección de características que intersecan con una geometría:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
