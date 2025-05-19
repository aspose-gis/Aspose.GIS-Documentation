---
title: "Licencias"
second_title: Aspose.GIS para .NET
type: docs
url: /es/net/licensing/
weight: 50
keywords: biblioteca gis c#, biblioteca gis .net
description: Evalúe la biblioteca GIS de C# .NET o API con algunas limitaciones. Aplique una Licencia utilizando un Objeto de Archivo o Flujo o como un Recurso Incrustado.
---

## **Evaluar Aspose.GIS para .NET**
Puede descargar Aspose.GIS para .NET de forma gratuita. Antes de aplicar una licencia, el componente funciona en modo de evaluación. Cuando compre una licencia y agregue algunas líneas de código para aplicar la licencia, las limitaciones de evaluación se eliminan.

{{% alert color="primary" %}} Si desea probar Aspose.GIS sin limitaciones del modo de evaluación, puede solicitar una Licencia Temporal de 30 días. Consulte [Obtener una Licencia Temporal](https://purchase.aspose.com/temporary-license). {{% /alert %}}
### **Limitaciones del Modo de Evaluación**
Al ejecutarse en modo de evaluación (sin una licencia aplicada), Aspose.GIS proporciona funcionalidad completa del producto, excepto algunas limitaciones de evaluación.

1. No se pueden abrir y/o crear más de **15 documentos** **por hora**.
1. No se pueden acceder a más de **100 características** en cada documento (lectura o escritura).
1. No se pueden acceder a más de **10 000 datos ráster** en cada documento (lectura o escritura).
1. El número máximo permitido de características en un documento para las operaciones de conversión es de **50**.

Cuando se ejecuta en modo con licencia, puede procesar un número ilimitado de documentos y características.
## **Aplicando una Licencia**
La licencia es un archivo XML de texto plano que contiene detalles como el nombre del producto, el número de desarrolladores a los que está licenciada, la fecha de vencimiento de la suscripción y así sucesivamente. El archivo está firmado digitalmente, por lo que no lo modifique. Incluso la adición inadvertida de un salto de línea adicional al archivo lo invalidará.

Debe establecer una licencia antes de utilizar Aspose.GIS si desea evitar sus limitaciones de evaluación. Solo es necesario establecer una licencia una vez por aplicación (o proceso).
### **Estableciendo una Licencia en Aspose.GIS para .NET**
En Aspose.GIS, la licencia se puede cargar desde un archivo, flujo o un recurso incrustado. Aspose.GIS intenta encontrar la licencia en las siguientes ubicaciones:

- Ruta explícita
- La carpeta que contiene Aspose.GIS.dll
- La carpeta que contiene el ensamblado que llamó a Aspose.GIS.dll
- La carpeta que contiene el ensamblado de entrada (su .exe)
- Un recurso incrustado en el ensamblado que llamó a Aspose.GIS.dll. Existen dos métodos comunes para establecer la licencia, que se analizan a continuación:
### **Aplicar Licencia utilizando un Objeto de Archivo o Flujo**
La forma más fácil de establecer una licencia es colocar el archivo de licencia en la misma carpeta que Aspose.GIS.dll y especificar solo el nombre del archivo sin su ruta.

{{< highlight java >}}

 // Instancie una instancia de licencia y establezca el archivo de licencia a través de su ruta

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Instancie una instancia de licencia y establezca la licencia a través de un flujo

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

Cuando llama al método SetLicense, el nombre de la licencia debe ser el mismo que el nombre del archivo de su licencia. Por ejemplo, puede cambiar el nombre del archivo de licencia a "Aspose.GIS.lic.xml". Luego, en su código, debe utilizar el nombre de licencia modificado (es decir, Aspose.GIS.lic.xml) para el método SetLicense.

## **Incluyendo el Archivo de Licencia como un Recurso Incrustado**
Otra forma práctica de empaquetar la licencia con su aplicación y asegurarse de que no se pierda es incluirla como un recurso incrustado en uno de los ensamblados que llama a la dll del componente (incluido en Aspose.GIS). Para incluir el archivo de licencia como un recurso incrustado, siga estos pasos:

- En Visual Studio, incluya el archivo de licencia (.lic) en el proyecto utilizando el menú Archivo | Agregar Elemento Existente...
- Seleccione el archivo en el Explorador de soluciones y establezca Acción de compilación en Recurso incrustado en la ventana Propiedades.
- Para acceder a la licencia incrustada en el ensamblado (como recurso incrustado), no es necesario llamar a los métodos GetExecutingAssembly y GetManifestResourceStream de la clase System.Reflection.Assembly de Microsoft .NET Framework. Todo lo que necesita hacer es agregar el archivo de licencia como un recurso incrustado a su proyecto y pasar el nombre del archivo de licencia al método License.SetLicense. La clase License encontrará automáticamente el archivo de licencia en los recursos incrustados.

Consulte el ejemplo siguiente para comprender este método de establecimiento de la licencia (incrustada) en sus aplicaciones.

{{< highlight java >}}

 // Instancie la clase License

Aspose.Gis.License license = new Aspose.Gis.License();

// Pase solo el nombre del archivo de licencia incrustado en el ensamblado

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Aplicando Clave Medida**
[La API de Aspose.GIS para .NET](/gis/net/) permite a los desarrolladores aplicar una clave medida. Es un nuevo mecanismo de licencia. El nuevo mecanismo de licencia se utilizará junto con el método de licencia existente. Aquellos clientes que deseen ser facturados en función del uso de las características de la API pueden utilizar la licencia medida. Para obtener más detalles, consulte la sección [Preguntas frecuentes sobre licencias medidas](https://purchase.aspose.com/faqs/licensing/metered).

Se ha introducido una nueva clase **Metered** para aplicar la clave medida. A continuación se muestra el código de ejemplo que demuestra cómo establecer la clave pública y privada medida.

**[C#]**

{{< highlight csharp >}}

 // establezca las claves públicas y privadas medidas
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Acceda a la propiedad setMeteredKey y pase las claves pública y privada como parámetros
 
metered.SetMeteredKey("*****", "*****");
 
// HACER PROCESAMIENTO
 
// obtener la cantidad de datos medidos
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Mostrar información
 
Console.WriteLine("Cantidad Consumida : " + amount.ToString());

{{< /highlight >}}
