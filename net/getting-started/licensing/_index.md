---
title: "Licensing"
type: docs
url: /net/licensing/
weight: 50
---

## **Evaluate Aspose.GIS for .NET**
You can download Aspose.GIS for .NET for free. Before you apply a license, the component works in evaluation mode. When you purchase a license and add a few lines of code to apply the license, evaluation limitations are removed.

{{% alert color="primary" %}} If you want to test Aspose.GIS without evaluation mode limitations, you can request a 30-day Temporary License. Please refer to [Get a Temporary License](https://purchase.aspose.com/temporary-license). {{% /alert %}} 
### **Evaluation Mode Limitations**
When executing in evaluation mode (without a license applied), Aspose.GIS provides full product functionality except some evaluation limitations.

1. No more than **15 documents** can be opened and/or created **per hour**
1. No more than **100 features** can be accessed in each document (reading or writing)
1. No more than **10 000 raster data** can be accessed in each document (reading or writing).
1. Maximum allowed number of features in a document for conversion operations is **50**

When executing in licensed mode, you can process unlimited number of documents and features.
## **Applying a License**
The license is a plain text XML file that contains details such as the product name, number of developers it is licensed to, subscription expiry date and so on. The file is digitally signed, so don't modify the file. Even inadvertent addition of an extra line break into the file will invalidate it.

You need to set a license before utilising Aspose.GIS if you want to avoid its evaluation limitations. It is only required to set a license once per application (or process).
### **Setting a License in Aspose.GIS for .NET**
In Aspose.GIS, license can be loaded from a file, stream or an embedded resource. Aspose.GIS tries to find the license in the following locations:

- Explicit path
- The folder that contains Aspose.GIS.dll
- The folder that contains the assembly that called Aspose.GIS.dll
- The folder that contains the entry assembly (your .exe)
- An embedded resource in the assembly that called Aspose.GIS.dll. There are two common methods to set the license, which are discussed below:
### **Apply License using File or Stream Object**
The easiest way to set a license, is to put the license file in the same folder as that of Aspose.GIS.dll and specify just the file name without its path.



{{< highlight java >}}

 // Instantiate an instance of license and set the license file through its path

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Instantiate an instance of license and set the license through a stream

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}



When you call SetLicense method, the license name should be same as that of your license file name. For example, you may change the license file name to "Aspose.GIS.lic.xml". Then in your code, you should use the modified license name (that is Aspose.GIS.lic.xml) for the SetLicense method.



## **Including the License File as an Embedded Resource**
Another neat way of packaging the license with your application and making sure it will not be lost, is to include it as an embedded resource into one of the assemblies that calls the dll of the component (included in Aspose.GIS). To include the license file as an embedded resource, perform the following steps:

- In Visual Studio, include the license (.lic) file into the project using the File | Add Existing Item... menu
- Select the file in the Solution Explorer and set Build Action to Embedded Resource in the Properties window
- To access the license embedded in the assembly (as embedded resource), it is not needed to call GetExecutingAssembly and GetManifestResourceStream methods of System.Reflection.Assembly class of Microsoft .NET Framework. All is needed to do, is to just add the license file as an embedded resource to your project and pass the name of the license file into License.SetLicense method. The License class will automatically find the license file in the embedded resources.

Please review the example given below to understand this method of setting license (embedded) in your applications.

{{< highlight java >}}

 // Instantiate the License class

Aspose.Gis.License license = new Aspose.Gis.License();

// Pass only the name of the license file embedded in the assembly

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Applying Metered Key**
[Aspose.Gis for .NET API](/gis/net/) allow developers to apply metered key. It is a new licensing mechanism. The new licensing mechanism will be used along with existing licensing method. Those customers who want to be billed based on the usage of the API features can use the metered licensing. For more details, please refer to [Metered Licensing FAQ](https://purchase.aspose.com/faqs/licensing/metered) section.

A new class **Metered** has been introduced to apply metered key. Following is the sample code demonstrating how to set metered public and private key.

**[C#]**

{{< highlight csharp >}}

 // set metered public and private keys

Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();

// Access the setMeteredKey property and pass public and private keys as parameters

metered.SetMeteredKey("*****", "*****");

// DO PROCESSING

// get metered data amount

decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();

// Display information

Console.WriteLine("Amount Consumed : " + amount.ToString());


{{< /highlight >}}



