---
title: "Лицензиране"
second_title: Aspose.GIS за .NET
type: docs
url: /bg/net/licensing/
weight: 50
keywords: c# gis библиотека, .net gis библиотека
description: Оценете C# .NET GIS библиотеката или API с някои ограничения. Приложете лиценз чрез обект File или Stream или като вграден ресурс.
---

## **Оценка на Aspose.GIS за .NET**
Можете да изтеглите Aspose.GIS за .NET безплатно. Преди да приложите лиценз, компонентът работи в режим на оценка. Когато закупите лиценз и добавите няколко реда код, за да го приложите, ограниченията за оценка се премахват.

{{% alert color="primary" %}} Ако искате да тествате Aspose.GIS без ограничения в режим на оценка, можете да поискате 30-дневен временен лиценз. Моля, вижте [Получаване на временен лиценз](https://purchase.aspose.com/temporary-license). {{% /alert %}}
### **Ограничения в режим на оценка**
Когато работите в режим на оценка (без приложен лиценз), Aspose.GIS предоставя пълна функционалност на продукта, с изключение на някои ограничения за оценка.

1. Не повече от **15 документа** могат да бъдат отворени и/или създадени **на час**.
1. Не повече от **100 обекта** могат да бъдат достъпни във всеки документ (четене или запис).
1. Не повече от **10 000 растерни данни** могат да бъдат достъпни във всеки документ (четене или запис).
1. Максималният брой разрешени обекти в документ за операции по преобразуване е **50**.

Когато работите в лицензиран режим, можете да обработвате неограничен брой документи и обекти.
## **Прилагане на лиценз**
Лицензът е обикновен текстов XML файл, който съдържа подробности като името на продукта, броя на разработчиците, за които е лицензиран, дата на изтичане на абонамента и т.н. Файлът е дигитално подписан, така че не го променяйте. Дори непреднамереното добавяне на допълнителен пренос на ред във файла ще го направи невалиден.

Трябва да зададете лиценз преди да използвате Aspose.GIS, ако искате да избегнете ограниченията му за оценка. Необходимо е да зададете лиценз само веднъж на приложение (или процес).
### **Задаване на лиценз в Aspose.GIS за .NET**
В Aspose.GIS лицензът може да бъде зареден от файл, поток или вграден ресурс. Aspose.GIS се опитва да намери лиценза на следните места:

- Ясен път
- Папката, която съдържа Aspose.GIS.dll
- Папката, която съдържа асемблирането, което е извикало Aspose.GIS.dll
- Папката, която съдържа входното асемблиране (вашия .exe)
- Вграден ресурс в асемблирането, което е извикало Aspose.GIS.dll. Има два често срещани метода за задаване на лиценза, които са обсъдени по-долу:
### **Прилагане на лиценз с помощта на обект File или Stream**
Най-лесният начин да зададете лиценз е да поставите лицензионния файл в същата папка като Aspose.GIS.dll и да посочите само името на файла без пътя му.

{{< highlight java >}}

 // Създайте инстанция на лиценза и задайте лицензионния файл чрез неговия път

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

{{< highlight java >}}

 // Създайте инстанция на лиценза и задайте лиценза чрез поток

Aspose.Gis.License license = new Aspose.Gis.License();

license.SetLicense(myStream);

{{< /highlight >}}

Когато извиквате метода SetLicense, името на лиценза трябва да е същото като името на вашия лицензионен файл. Например, можете да промените името на лицензионния файл на "Aspose.GIS.lic.xml". След това в кода си трябва да използвате модифицираното име на лиценза (т.е. Aspose.GIS.lic.xml) за метода SetLicense.

## **Включване на лицензионния файл като вграден ресурс**
Друг елегантен начин за пакетиране на лиценза с вашето приложение и гарантиране, че няма да бъде загубен, е да го включите като вграден ресурс в едно от асемблиранията, което извиква dll на компонента (включен в Aspose.GIS). За да включите лицензионния файл като вграден ресурс, изпълнете следните стъпки:

- В Visual Studio включете лицензионния (.lic) файл в проекта, използвайки менюто File | Add Existing Item...
- Изберете файла в Solution Explorer и задайте Build Action на Embedded Resource в прозореца Properties
- За да получите достъп до лиценза, вграден в асемблирането (като вграден ресурс), не е необходимо да извиквате методите GetExecutingAssembly и GetManifestResourceStream на класа System.Reflection.Assembly на Microsoft .NET Framework. Всичко, което трябва да направите, е просто да добавите лицензионния файл като вграден ресурс към вашия проект и да предадете името на лицензионния файл в метода License.SetLicense. Класът License автоматично ще намери лицензионния файл във вградените ресурси.

Моля, прегледайте примера, даден по-долу, за да разберете този метод за задаване на лиценз (вграден) във вашите приложения.

{{< highlight java >}}

 // Създайте класа License

Aspose.Gis.License license = new Aspose.Gis.License();

// Предайте само името на лицензионния файл, вграден в асемблирането

license.SetLicense("Aspose.GIS.lic");

{{< /highlight >}}

## **Прилагане на Metered Key**
[Aspose.Gis for .NET API](/gis/net/) позволява на разработчиците да прилагат измерван ключ. Това е нов механизъм за лицензиране. Новият механизъм за лицензиране ще се използва заедно със съществуващия метод за лицензиране. Тези клиенти, които искат да бъдат таксувани въз основа на използването на функциите на API, могат да използват измерваното лицензиране. За повече подробности вижте раздела [Често задавани въпроси за измервано лицензиране](https://purchase.aspose.com/faqs/licensing/metered).

Въведен е нов клас **Metered**, за да се приложи измерван ключ. Следва примерният код, демонстриращ как да настроите измервания публичен и частен ключ.

**[C#]**

{{< highlight csharp >}}

 // задайте измервани публични и частни ключове
 
Aspose.Gid.Metered metered = new Aspose.BarCode.Metered();
 
// Достъп до свойството setMeteredKey и предайте публичните и частните ключове като параметри
 
metered.SetMeteredKey("*****", "*****");
 
// ИЗПЪЛНЕТЕ ОБРАБОТКАТА
 
// вземете количеството изразходвани данни
 
decimal amount = Aspose.BarCode.Metered.GetConsumptionQuantity();
 
// Показване на информацията
 
Console.WriteLine("Изразходвана сума: " + amount.ToString());

{{< /highlight >}}
