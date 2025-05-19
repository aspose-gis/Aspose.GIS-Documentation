---
title: "Streams e Armazenamento Remoto"
type: docs
url: /pt/net/streams-and-remote-storage/
weight: 70
---

## **Trabalhando com Formatos Multi-Arquivo**
Alguns formatos de dados GIS dividem o conteúdo em vários arquivos. Por exemplo, um shapefile deve ter pelo menos três arquivos: *.shp, *.shx e *.dbf. Esses formatos exigem que todos os arquivos sejam armazenados em uma estrutura de diretório específica com um padrão predefinido para nomes de arquivo.

Ao mesmo tempo, os arquivos podem ser armazenados em um servidor remoto ou outro local acessível apenas por meio de streams. Streams não possuem informações sobre nomes de arquivo e estrutura de diretórios, tornando impossível para os drivers de formato de arquivo determinar como processar os dados. Aspose.GIS resolve isso fornecendo o mecanismo de caminhos abstratos.

Um caminho abstrato representa um caminho para um arquivo (ou um diretório) em algum armazenamento semelhante a um sistema de arquivos. O armazenamento pode ser qualquer coisa que tenha um conceito de arquivo e diretório, desde um arquivo até um servidor FTP. Ele define como executar operações típicas de arquivo, como abrir um arquivo ou listar um diretório.

Você pode especificar como realizar operações de arquivo para seu armazenamento implementando uma classe que herda [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) e fornecendo implementações para seus métodos abstratos.
## **Demonstração: Armazenamento de Blobs do Azure**
O repositório de exemplos Aspose.GIS contém um exemplo de uma implementação totalmente funcional de um caminho abstrato personalizado para o Armazenamento de Blobs do Azure. Esta demonstração mostra como ler um shapefile diretamente do Armazenamento de Blobs do Azure. Você pode encontrá-lo aqui: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Formatos de arquivo único (GeoJSON, KML)**
Formatos de dados GIS como GeoJSON e KML podem armazenar todos os dados para uma camada em um único arquivo. Se você puder obter um stream para o arquivo, poderá pular a implementação de um caminho abstrato personalizado e usar o método [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) para instanciar um caminho abstrato para o stream.
### **Leia um arquivo de um stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Escreva um arquivo em um stream**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
