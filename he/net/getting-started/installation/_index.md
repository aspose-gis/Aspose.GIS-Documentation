---
title: "התקנה"
second_title: Aspose.GIS for .NET
type: docs
url: /he/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: התקן ספריית GIS C#.NET או API מ- NuGet באמצעות ממשק המשתמש של Package Manager או Console, מארכיון ZIP. ניתן להשתמש בו גם ב-.NET Core ובמערכת הפעלה Linux.
---

## **התקנת Aspose.GIS**
### **מ-NuGet**
כדי להתקין את Aspose.GIS, השתמש בממשק המשתמש של Package Manager או ב-Package Manager Console. כאשר אתה מתקין חבילה, NuGet רושם את התלות בקובץ הפרויקט שלך או בקובץ packages.config.
#### **ממשק המשתמש של Package Manager**
1. בסייר הפתרונות, לחץ לחיצה ימנית על **References** ובחר **Manage NuGet Packages**.

![todo:image_alt_text](installation_1.png)

1. ודא שמקור החבילות **Package Source** מוגדר כ-"nuget.org", בחר את הכרטיסייה Browse, חפש Aspose.GIS, בחר את החבילה ברשימה ולחץ על Install:

![todo:image_alt_text](installation_2.png)

1. הכר את [הסכם רישיון משתמש קצה של Aspose](https://about.aspose.com/legal/eula).
1. אם תתבקש לסקור שינויים, בחר **OK**.
#### **Package Manager Console**
1. בחר את הפקודה **Tools** > **NuGet Package Manager** > **Package Manager Console**.
2. לאחר פתיחת המסוף, ודא שרשימת הנפתחת **Default project** מציגה את הפרויקט שאליו ברצונך להתקין את החבילה. אם יש לך פרויקט אחד בלבד בפתרון, הוא כבר נבחר.

![todo:image_alt_text](installation_3.png)

1. הזן את הפקודה Install-Package Aspose.GIS. חלון המסוף יציג פלט עבור הפקודה.
### **עם מתקין MSI או מארכיון ZIP**
כחלופה להתקנת NuGet, תוכל להוריד את Aspose.GIS מ[סעיף ההורדות](https://downloads.aspose.com/gis/net) כמתקין MSI או ארכיון ZIP.
## **הוראות ספציפיות לפלטפורמה**
### **Linux**
בעת שימוש בפונקציונליות עיבוד המפות של Aspose.GIS תחת Linux, ודא שספריית System.Drawing.Common מוגדרת כראוי. אם אתה מקבל הודעת שגיאה דומה ל

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

זה אומר שהתלויות של System.Drawing.Common חסרות מהמערכת. כדי לתקן זאת, הפעל:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **דרישות מערכת עבור Aspose.GIS for .NET**
כל רכיבי .NET של Aspose דורשים סט הרשאות Full Trust.

Aspose.GIS כולל שני וריאנטים של ההרכבה שנבנו עבור

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 ומעלה**
מערכות הפעלה:

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `גם גרסאות 32 ו-64 סיביות נתמכות.
### **.NET Core v2.0 ומעלה**
` `מערכות הפעלה:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (גרסה 1607) או גרסאות מאוחרות יותר
- Microsoft Windows Server 2008 R2 SP1 (Full Server או Server Core), 2012 SP1 (Full Server או Server Core), 2012 R2 (Full Server או Server Core), 2016 או גרסאות מאוחרות יותר (Full Server, Server Core או Nano Server)
- macOS 10.12 "Sierra" וגרסאות מאוחרות יותר
- Linux (64 סיביות, x86_64 או amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64 סיביות, arm32), 8.7 או גרסאות מאוחרות יותר
  - Ubuntu 18.04 (64 סיביות, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 או גרסאות מאוחרות יותר
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 או גרסאות מאוחרות יותר
  - Alpine Linux 3.7 או גרסאות מאוחרות יותר

פרטים נוספים זמינים במדריך .NET Core: [דרישות מוקדמות של Windows](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [דרישות מוקדמות של macOS](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [דרישות מוקדמות של Linux](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **תמיכה ניסיונית**
- Mono 5.4 ומעלה
- Xamarin:
  - Xamarin.iOS: גרסה 10.14 או מאוחרת יותר
  - Xamarin.Android: גרסה 8.0 או מאוחרת יותר
  - Xamarin.Mac: גרסה 3.8 או מאוחרת יותר
