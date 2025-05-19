---
title: "라이선스"
second_title: Aspose.GIS for .NET
type: docs
url: /ko/net/licensing/
weight: 50
keywords: c# gis library, .net gis library
description: C# .NET GIS 라이브러리 또는 API를 제한 사항과 함께 평가합니다. 파일 또는 스트림 개체로 또는 임베디드 리소스로 라이선스를 적용합니다.
---

## **Aspose.GIS for .NET 평가**
Aspose.GIS for .NET을 무료로 다운로드할 수 있습니다. 라이선스를 적용하기 전까지 구성 요소는 평가 모드로 작동합니다. 라이선스를 구매하고 몇 줄의 코드를 추가하여 라이선스를 적용하면 평가 제한이 제거됩니다.

{{% alert color="primary" %}} Aspose.GIS를 평가 모드 제한 없이 테스트하려면 30일 임시 라이선스를 요청할 수 있습니다. [임시 라이선스 받기](https://purchase.aspose.com/temporary-license)를 참조하십시오. {{% /alert %}}
### **평가 모드 제한**
(라이선스가 적용되지 않은) 평가 모드로 실행하면 Aspose.GIS는 일부 평가 제한을 제외하고 전체 제품 기능을 제공합니다.

1. 시간당 **15개** 이하의 문서를 열거나 생성할 수 있습니다.
2. 각 문서에서 액세스할 수 있는 기능은 **100개** 이하입니다(읽기 또는 쓰기).
3. 각 문서에서 액세스할 수 있는 래스터 데이터는 **10,000개** 이하입니다(읽기 또는 쓰기).
4. 변환 작업에 대한 문서의 최대 허용 기능 수는 **50개**입니다.

라이선스가 적용된 모드로 실행하면 무제한의 문서 및 기능을 처리할 수 있습니다.
## **라이선스 적용**
라이선스는 제품 이름, 라이선스를 받은 개발자 수, 구독 만료일 등과 같은 세부 정보를 포함하는 일반 텍스트 XML 파일입니다. 이 파일은 디지털 서명되어 있으므로 파일을 수정하지 마십시오. 실수로도 파일에 줄 바꿈을 추가하면 무효화됩니다.

Aspose.GIS의 평가 제한을 피하려면 Aspose.GIS를 사용하기 전에 라이선스를 설정해야 합니다. 라이선스는 애플리케이션(또는 프로세스)당 한 번만 설정하면 됩니다.
### **Aspose.GIS for .NET에서 라이선스 설정**
Aspose.GIS에서는 파일, 스트림 또는 임베디드 리소스에서 라이선스를 로드할 수 있습니다. Aspose.GIS는 다음 위치에서 라이선스를 찾습니다.

- 명시적 경로
- Aspose.GIS.dll이 포함된 폴더
- Aspose.GIS.dll을 호출한 어셈블리가 포함된 폴더
- 엔트리 어셈블리(your .exe)가 포함된 폴더
- Aspose.GIS.dll을 호출한 어셈블리의 임베디드 리소스입니다. 라이선스를 설정하는 두 가지 일반적인 방법은 아래에서 설명합니다.
### **파일 또는 스트림 개체를 사용하여 라이선스 적용**
라이선스를 설정하는 가장 쉬운 방법은 라이선스 파일을 Aspose.GIS.dll과 동일한 폴더에 넣고 경로 없이 파일 이름만 지정하는 것입니다.

{{< highlight java >}}

 // 라이선스의 인스턴스를 생성하고 해당 경로를 통해 라이선스 파일을 설정합니다.

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // 라이선스의 인스턴스를 생성하고 스트림을 통해 라이선스를 설정합니다.

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

SetLicense 메서드를 호출할 때 라이선스 이름은 라이선스 파일 이름과 동일해야 합니다. 예를 들어, 라이선스 파일 이름을 "Aspose.GIS.lic.xml"로 변경할 수 있습니다. 그런 다음 코드에서 수정된 라이선스 이름(즉, Aspose.GIS.lic.xml)을 SetLicense 메서드에 사용해야 합니다.

## **라이선스 파일을 임베디드 리소스로 포함**
라이선스를 애플리케이션과 함께 패키징하고 분실되지 않도록 하는 또 다른 깔끔한 방법은 라이선스를 Aspose.GIS의 DLL을 포함하는 어셈블리를 호출하는 어셈블리의 임베디드 리소스에 포함하는 것입니다. 라이선스 파일을 임베디드 리소스로 포함하려면 다음 단계를 수행합니다.

- Visual Studio에서 파일 | 기존 항목 추가... 메뉴를 사용하여 라이선스(.lic) 파일을 프로젝트에 포함합니다.
- 솔루션 탐색기에서 파일을 선택하고 속성 창에서 빌드 작업으로 임베디드 리소스를 설정합니다.
- 어셈블리에 임베디드된 라이선스(임베디드 리소스)에 액세스하려면 Microsoft .NET Framework의 System.Reflection.Assembly 클래스의 GetExecutingAssembly 및 GetManifestResourceStream 메서드를 호출할 필요가 없습니다. 필요한 것은 라이선스 파일을 프로젝트의 임베디드 리소스로 추가하고 License.SetLicense 메서드에 라이선스 파일 이름을 전달하는 것입니다. 라이선스 클래스는 자동으로 임베디드 리소스에서 라이선스 파일을 찾습니다.

이러한 방법으로 애플리케이션에서 라이선스를 설정하는 방법을 이해하려면 아래 예제를 참조하십시오.

{{< highlight java >}}

 // License 클래스의 인스턴스를 생성합니다.

Aspose.Gis.License license = new Aspose.Gis.License();

// 어셈블리에 임베디드된 라이선스 파일 이름만 전달합니다.

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **미터링 키 적용**
[Aspose.GIS for .NET API](/gis/net/)를 사용하면 개발자가 미터링 키를 적용할 수 있습니다. 새로운 라이선스 메커니즘입니다. 새로운 라이선스 메커니즘은 기존 라이선스 방법과 함께 사용됩니다. API 기능의 사용량에 따라 청구하려는 고객은 미터링 라이선스를 사용할 수 있습니다. 자세한 내용은 [미터링 라이선스 FAQ](https://purchase.aspose.com/faqs/licensing/metered) 섹션을 참조하십시오.

새로운 클래스 **Metered**가 도입되어 미터링 키를 적용합니다. 다음은 미터링 공개 및 개인 키를 설정하는 방법을 보여주는 샘플 코드입니다.

**[C#]**

{{< highlight csharp >}}

 // 미터링 공개 및 개인 키 설정

Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();

// setMeteredKey 속성에 액세스하고 매개변수로 공개 및 개인 키를 전달합니다.

metered.SetMeteredKey("*****", "*****");

// 처리 수행

// 소비된 데이터 양을 가져옵니다.

decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();

// 정보 표시

Console.WriteLine("소비량 : " + amount.ToString());


{{< /highlight >}}
