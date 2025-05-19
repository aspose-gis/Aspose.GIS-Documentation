---
title: "Licenciamento"
second_title: Aspose.GIS for .NET
type: docs
url: /pt/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: Avalie a biblioteca C# .NET GIS ou API com algumas limitações. Aplique Licença usando Objeto Arquivo ou Stream ou como um Recurso Incorporado.
---

## **Avalie Aspose.GIS for .NET**
Você pode baixar o Aspose.GIS for .NET gratuitamente. Antes de aplicar uma licença, o componente funciona no modo de avaliação. Quando você compra uma licença e adiciona algumas linhas de código para aplicar a licença, as limitações de avaliação são removidas.

{{% alert color="primary" %}} Se você quiser testar o Aspose.GIS sem limitações do modo de avaliação, pode solicitar uma Licença Temporária de 30 dias. Consulte [Obter uma Licença Temporária](https://purchase.aspose.com/temporary-license). {{% /alert %}}
### **Limitações do Modo de Avaliação**
Ao executar no modo de avaliação (sem uma licença aplicada), o Aspose.GIS fornece funcionalidade completa do produto, exceto algumas limitações de avaliação.

1. Não mais que **15 documentos** podem ser abertos e/ou criados **por hora**.
1. Não mais que **100 recursos** podem ser acessados em cada documento (leitura ou gravação).
1. Não mais que **10 000 dados raster** podem ser acessados em cada documento (leitura ou gravação).
1. O número máximo permitido de recursos em um documento para operações de conversão é **50**.

Ao executar no modo licenciado, você pode processar um número ilimitado de documentos e recursos.
## **Aplicando uma Licença**
A licença é um arquivo XML de texto simples que contém detalhes como o nome do produto, o número de desenvolvedores para os quais ele é licenciado, a data de validade da assinatura e assim por diante. O arquivo é assinado digitalmente, portanto, não o modifique. Mesmo a adição inadvertida de uma quebra de linha extra ao arquivo o invalidará.

Você precisa definir uma licença antes de utilizar o Aspose.GIS se quiser evitar suas limitações de avaliação. É necessário definir uma licença apenas uma vez por aplicativo (ou processo).
### **Definindo uma Licença no Aspose.GIS for .NET**
No Aspose.GIS, a licença pode ser carregada de um arquivo, stream ou recurso incorporado. O Aspose.GIS tenta encontrar a licença nos seguintes locais:

- Caminho explícito
- A pasta que contém o Aspose.GIS.dll
- A pasta que contém o assembly que chamou o Aspose.GIS.dll
- A pasta que contém o assembly de entrada (seu .exe)
- Um recurso incorporado no assembly que chamou o Aspose.GIS.dll. Existem dois métodos comuns para definir a licença, que são discutidos abaixo:
### **Aplicar Licença usando Arquivo ou Objeto Stream**
A maneira mais fácil de definir uma licença é colocar o arquivo de licença na mesma pasta do Aspose.GIS.dll e especificar apenas o nome do arquivo sem seu caminho.

{{< highlight java >}}

 // Instancie uma instância de licença e defina o arquivo de licença por meio de seu caminho

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Instancie uma instância de licença e defina a licença por meio de um stream

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

Quando você chama o método SetLicense, o nome da licença deve ser o mesmo do seu arquivo de licença. Por exemplo, você pode alterar o nome do arquivo de licença para "Aspose.GIS.lic.xml". Em seguida, no seu código, você deve usar o nome da licença modificado (ou seja, Aspose.GIS.lic.xml) para o método SetLicense.

## **Incluindo o Arquivo de Licença como um Recurso Incorporado**
Outra maneira organizada de empacotar a licença com seu aplicativo e garantir que ela não será perdida é incluí-la como um recurso incorporado em um dos assemblies que chama o dll do componente (incluído no Aspose.GIS). Para incluir o arquivo de licença como um recurso incorporado, siga as etapas abaixo:

- No Visual Studio, inclua o arquivo de licença (.lic) no projeto usando o menu Arquivo | Adicionar Item Existente...
- Selecione o arquivo no Solution Explorer e defina Ação da Compilação como Recurso Incorporado na janela Propriedades
- Para acessar a licença incorporada no assembly (como recurso incorporado), não é necessário chamar os métodos GetExecutingAssembly e GetManifestResourceStream da classe System.Reflection.Assembly do Microsoft .NET Framework. Tudo o que você precisa fazer é adicionar o arquivo de licença como um recurso incorporado ao seu projeto e passar o nome do arquivo de licença para o método License.SetLicense. A classe License encontrará automaticamente o arquivo de licença nos recursos incorporados.

Consulte o exemplo abaixo para entender este método de definição de licença (incorporada) em seus aplicativos.

{{< highlight java >}}

 // Instancie a classe License

Aspose.Gis.License license = new Aspose.Gis.License();

// Passe apenas o nome do arquivo de licença incorporado no assembly

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Aplicando Chave Medida**
[API Aspose.Gis for .NET](/gis/net/) permite que os desenvolvedores apliquem chave medida. É um novo mecanismo de licenciamento. O novo mecanismo de licenciamento será usado junto com o método de licenciamento existente. Aqueles clientes que desejam ser cobrados com base no uso dos recursos da API podem usar o licenciamento medido. Para obter mais detalhes, consulte a seção [FAQ sobre Licenciamento Medido](https://purchase.aspose.com/faqs/licensing/metered).

Uma nova classe **Metered** foi introduzida para aplicar chave medida. O seguinte é o código de exemplo demonstrando como definir chave pública e privada medida.

**[C#]**

{{< highlight csharp >}}

 // defina chaves públicas e privadas medidas
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Acesse a propriedade setMeteredKey e passe as chaves pública e privada como parâmetros
 
metered.SetMeteredKey("*****", "*****");
 
// FAÇA O PROCESSAMENTO
 
// obtenha a quantidade de dados consumida
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Exiba as informações
 
Console.WriteLine("Quantidade Consumida : " + amount.ToString());

{{< /highlight >}}
