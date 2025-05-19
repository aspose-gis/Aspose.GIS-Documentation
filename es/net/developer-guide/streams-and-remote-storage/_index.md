---
title: "Flujos y Almacenamiento Remoto"
type: docs
url: /es/net/streams-and-remote-storage/
weight: 70
---

## **Trabajando con Formatos Multi-Archivo**
Algunos formatos de datos SIG dividen el contenido en varios archivos. Por ejemplo, un shapefile debe tener al menos tres archivos: *.shp, *.shx y *.dbf. Estos formatos requieren que todos los archivos se almacenen en una estructura de directorio particular con un patrón predefinido para los nombres de archivo.

Al mismo tiempo, los archivos pueden almacenarse en un servidor remoto o en otra ubicación accesible solo a través de flujos. Los flujos carecen de información sobre los nombres de archivo y la estructura del directorio, lo que hace imposible que los controladores de formato de archivo determinen cómo procesar los datos. Aspose.GIS resuelve esto proporcionando el mecanismo de rutas abstractas.

Una ruta abstracta representa una ruta a un archivo (o un directorio) en algún almacenamiento similar a un sistema de archivos. El almacenamiento puede ser cualquier cosa que tenga un concepto del archivo y el directorio, desde un archivo hasta un servidor FTP. Define cómo ejecutar operaciones típicas de archivos, como abrir un archivo o enumerar un directorio.

Puede especificar cómo realizar operaciones de archivo para su almacenamiento implementando una clase que herede de [AbstractPath](https://reference.aspose.com/gis/net/aspose.gis/abstractpath) y proporcionando implementaciones para sus métodos abstractos.
## **Demostración: Azure Blob Storage**
El repositorio de ejemplos de Aspose.GIS contiene un ejemplo de una implementación totalmente funcional de una ruta abstracta personalizada para Azure Blob Storage. Esta demostración muestra cómo leer un shapefile directamente desde Azure Blob Storage. Puede encontrarlo aquí: [https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET](https://github.com/aspose-gis/Aspose.GIS-for-.NET/tree/master/Showcases/Azure_Blob_Integration_by_Aspose_Gis_for_NET).
## **Formatos de un solo archivo (GeoJSON, KML)**
Los formatos de datos SIG como GeoJSON y KML pueden almacenar todos los datos para una capa en un solo archivo. Si puede obtener un flujo para el archivo, puede omitir la implementación de una ruta abstracta personalizada y usar el método [AbstractPath.FromStream()](https://reference.aspose.com/gis/net/aspose.gis/abstractpath/methods/fromstream) para instanciar una ruta abstracta para el flujo.
### **Leer un archivo desde un flujo**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-ReadGeoJsonFromStream-ReadGeoJsonFromStream.cs" >}}
### **Escribir un archivo en un flujo**
{{< gist "aspose-com-gists" "10f3783b9581d10bc69dbada42705d2c" "Examples-CSharp-Layers-WriteGeoJsonToStream-WriteGeoJsonToStream.cs" >}}
