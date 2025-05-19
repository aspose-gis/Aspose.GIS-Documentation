---
title: "Aplicación de Consola Generador de Capas"
type: docs
url: /es/net/layer-generator-console
weight: 50
---

## Resumen

Esta aplicación de consola está diseñada para generar objetos geométricos de varios tipos y guardarlos en el formato elegido. Le permite crear puntos, polígonos y polilíneas, especificar la cantidad de objetos a generar y elegir el formato de salida para guardar.

## Uso

Sintaxis del comando:

```
app.exe -t <geometry_type> -c <count> -f <file_name> -o <output_format>
```

Argumentos:

```
-t, --type: Tipo de geometría. Uno de los siguientes: Punto, Polígono, Polilínea.

-c, --count: Requerido. Número de objetos a generar. Por ejemplo: 15.

-f, --fileName: Requerido. Nombre del archivo para guardar. Especifique el nombre del archivo y la extensión. Por ejemplo: test.json.

-o, --outputFormat: Formato de salida. Consulte los formatos de archivo compatibles aquí.

--help: Mostrar información de ayuda para el comando.

--version: Mostrar la información de la versión de la aplicación.
```

Un ejemplo de comando para crear 15 puntos aleatorios y guardarlos en un archivo con el formato "test.json":

```
app.exe -t Point -c 15 -f test.json -o json
```

## Instalación y Licencias

Si desea utilizar la aplicación, debe descargar el archivo y extraerlo. Siga el enlace a continuación.

```
https://releases.aspose.com/gis/net/new-releases/aspose.gis-layer-generator-application/
```

Aunque la Aplicación de Consola Generador de Capas Aspose.GIS es gratuita, Aspose.GIS .NET está licenciado como de costumbre, por lo que puede reutilizar su licencia a través de la aplicación o evaluar la aplicación utilizando Aspose.GIS .NET en modo de prueba o solicitar una licencia temporal.

## Conclusión

El Generador de Objetos Geométricos es una conveniente aplicación de consola que le ayuda a crear muestras de geometría de varios tipos y guardarlas en el formato deseado. Es una herramienta útil para trabajar con datos geoespaciales y desarrollar sistemas de información geográfica.
