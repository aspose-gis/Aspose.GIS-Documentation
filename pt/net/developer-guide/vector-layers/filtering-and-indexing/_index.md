---
title: Filtragem e Indexação de Camadas Vetoriais GIS em C#
linktitle: Filtragem e Indexação
second_title: Aspose.GIS for .NET
type: docs
url: /pt/filtering-and-indexing/
weight: 30
description: Com a Biblioteca ou API GIS C# .NET, você pode filtrar camadas vetoriais GIS por valores de atributo ou limites espaciais. Você também pode usar índices para acelerar a filtragem e consultas espaciais.
---

Com Aspose.GIS for .NET você pode filtrar camadas por valores de atributo ou limites espaciais. Você também pode usar índices para acelerar a filtragem e consultas espaciais.
## **Índice de Atributo**
### **Filtrar Sem Índice**
Aqui está como filtrar uma camada pelos valores de um atributo:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FilterLayerByAttributeValue.cs" >}}
### **Filtrar Com Índice**
O código acima é bom enquanto a camada for filtrada apenas uma vez. Mas, se a camada provavelmente for consultada várias vezes, podemos nos beneficiar de índices de atributo. Leva algum tempo para construir um índice de atributo, mas ele pode ser reutilizado várias vezes para acelerar a filtragem.

O exemplo a seguir usa um arquivo de índice de atributo para acelerar a filtragem da camada pelos valores do atributo:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-IterateFilteredFeatures.cs" >}}
### **Salvar Recursos Filtrados**
Os recursos filtrados podem ser salvos em camadas:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-SaveFilteredFeaturesToLayer.cs" >}}
### **Renderizar Recursos Filtrados**
Também é possível renderizar recursos filtrados. O exemplo a seguir usa um índice de atributo para selecionar rapidamente todos os recursos com população superior a 2000 e adicioná-los ao mapa:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-RenderFilteredFeatures.cs" >}}
## **Índice Espacial**
Os índices espaciais são usados para acelerar consultas espaciais. Assim como os índices de atributo, os índices espaciais são reutilizados após a criação.
### **Encontrar Recursos Mais Próximos ao Ponto**
Aqui está como usar um índice espacial para acelerar a busca pelo recurso mais próximo a algum ponto:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeatureNearestToPoint.cs" >}}
### **Selecionar Recursos que Intersectam com a Geometria**
O exemplo a seguir usa um índice espacial para acelerar a seleção de recursos que intersectam com a geometria:

{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-FilteringAndIndexing-FindFeaturesWithinExtent.cs" >}}
