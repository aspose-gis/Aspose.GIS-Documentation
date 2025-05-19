---
title: "ライセンス"
second_title: Aspose.GIS for .NET
type: docs
url: /ja/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: C# .NET GIS ライブラリまたは API をいくつかの制限付きで評価します。ファイルまたはストリームオブジェクト、または組み込みリソースとしてライセンスを適用します。
---

## **Aspose.GIS for .NET の評価**
Aspose.GIS for .NET は無料でダウンロードできます。ライセンスを適用する前に、コンポーネントは評価モードで動作します。ライセンスを購入し、ライセンスを適用するためのいくつかのコード行を追加すると、評価の制限が解除されます。

{{% alert color="primary" %}} 評価モードの制限なしで Aspose.GIS をテストしたい場合は、30 日間の仮ライセンスをリクエストできます。[仮ライセンスを取得](https://purchase.aspose.com/temporary-license)を参照してください。 {{% /alert %}}
### **評価モードの制限**
ライセンスが適用されていない状態で評価モードで実行すると、Aspose.GIS はいくつかの評価制限を除いて、完全な製品機能を提供します。

1. 1 時間あたりに開いたり作成したりできるドキュメントは **15 件** までです。
1. 各ドキュメント (読み取りまたは書き込み) でアクセスできるフィーチャは **100 件** までです。
1. 各ドキュメント (読み取りまたは書き込み) でアクセスできるラスターデータは **10,000** までです。
1. 変換操作のドキュメントで許可される最大フィーチャ数は **50** です。

ライセンスモードで実行すると、無制限の数のドキュメントとフィーチャを処理できます。
## **ライセンスの適用**
ライセンスは、製品名、ライセンス対象の開発者数、サブスクリプションの有効期限などの詳細を含むプレーンテキスト XML ファイルです。ファイルにはデジタル署名されているため、ファイルを変更しないでください。誤ってファイルに改行を追加すると、無効になります。

Aspose.GIS の評価制限を回避したい場合は、利用する前にライセンスを設定する必要があります。ライセンスはアプリケーション (またはプロセス) ごとに 1 回設定するだけで済みます。
### **Aspose.GIS for .NET でのライセンスの設定**
Aspose.GIS では、ライセンスをファイル、ストリーム、または組み込みリソースからロードできます。Aspose.GIS は次の場所でライセンスを探します。

- 明示的なパス
- Aspose.GIS.dll が含まれるフォルダー
- Aspose.GIS.dll を呼び出したアセンブリが含まれるフォルダー
- エントリアセンブリ (実行可能ファイル .exe) が含まれるフォルダー
- Aspose.GIS.dll を呼び出したアセンブリに組み込まれたリソース。Aspose.GIS には、ライセンスを設定する 2 つの一般的な方法があり、以下で説明します。
### **ファイルまたはストリームオブジェクトを使用してライセンスを適用**
ライセンスを設定する最も簡単な方法は、ライセンスファイルを Aspose.GIS.dll と同じフォルダーに配置し、パスなしでファイル名を指定することです。

{{< highlight java >}}

 // ライセンスのインスタンスを作成し、そのパスを通じてライセンスファイルを設定します。

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // ライセンスのインスタンスを作成し、ストリームを通じてライセンスを設定します。

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

SetLicense メソッドを呼び出すと、ライセンス名はライセンスファイル名と同じである必要があります。たとえば、ライセンスファイル名を "Aspose.GIS.lic.xml" に変更できます。次に、コードで SetLicense メソッドに修正されたライセンス名 (つまり Aspose.GIS.lic.xml) を使用する必要があります。

## **組み込みリソースとしてライセンスファイルを組み込む**
アプリケーションと一緒にライセンスをパッケージ化し、紛失しないようにするためのもう 1 つの優れた方法は、コンポーネントの DLL に含まれるアセンブリを呼び出すいずれかのものに組み込みリソースとして含めることです。ライセンスファイルを組み込みリソースとして含めるには、次の手順を実行します。

- Visual Studio で、ファイル | 既存のアイテムを追加... メニューを使用して、ライセンス (.lic) ファイルをプロジェクトに含めます。
- ソリューションエクスプローラーでファイルを選択し、プロパティウィンドウでビルドアクションを組み込みリソースに設定します。
- アセンブリ (Microsoft .NET Framework の System.Reflection.Assembly クラス) に埋め込まれたライセンスにアクセスするには、GetExecutingAssembly と GetManifestResourceStream メソッドを呼び出す必要はありません。必要なのは、ライセンスファイルをプロジェクトの組み込みリソースとして追加し、License.SetLicense メソッドにライセンスファイル名を渡すだけです。ライセンスクラスは自動的に組み込みリソース内のライセンスファイルを見つけます。

アプリケーションでこの方法 (埋め込み) でライセンスを設定する方法を理解するには、以下に示す例を確認してください。

{{< highlight java >}}

 // ライセンスクラスのインスタンス化

Aspose.Gis.License license = new Aspose.Gis.License();

// アセンブリに組み込まれたライセンスファイルの名前のみを渡します。

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **メーターキーの適用**
[Aspose.GIS for .NET API](/gis/net/) を使用すると、開発者はメーターキーを適用できます。これは新しいライセンスメカニズムです。新しいライセンスメカニズムは既存のライセンス方法と一緒に使用されます。API の機能の使用量に基づいて課金したい顧客は、メーターライセンスを使用できます。[メーターライセンス FAQ](https://purchase.aspose.com/faqs/licensing/metered) セクションを参照してください。

新しいクラス **Metered** が導入され、メーターキーを適用します。以下に、メーター公開キーと非公開キーを設定する方法を示すサンプルコードを示します。

**[C#]**

{{< highlight csharp >}}

 // メーター公開キーと非公開キーを設定します。

Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();

// setMeteredKey プロパティにアクセスし、公開キーと非公開キーをパラメーターとして渡します。

metered.SetMeteredKey("*****", "*****");

// 処理を実行します。

// 消費量を取得します。

decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();

// 表示情報

Console.WriteLine("消費量 : " + amount.ToString());

{{< /highlight >}}
