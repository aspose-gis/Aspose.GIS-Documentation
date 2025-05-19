---
title: "Instalación"
second_title: Aspose.GIS for .NET
type: docs
url: /es/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Instale la biblioteca o API de GIS C#.NET desde NuGet utilizando la interfaz de usuario o la consola del Administrador de paquetes, desde un archivo ZIP. También se puede utilizar en .NET Core y SO Linux.
---

## **Instalar Aspose.GIS**
### **Desde NuGet**
Para instalar Aspose.GIS, utilice la interfaz de usuario del Administrador de paquetes o la Consola del Administrador de paquetes. Cuando instala un paquete, NuGet registra la dependencia en su archivo de proyecto o en un archivo packages.config.
#### **Interfaz de usuario del Administrador de paquetes**
1. En el Explorador de soluciones, haga clic derecho en **Referencias** y elija **Administrar paquetes de NuGet**.

![todo:image_alt_text](installation_1.png)

1. Compruebe que "nuget.org" esté seleccionado como **Origen del paquete**, seleccione la pestaña Examinar, busque Aspose.GIS, seleccione ese paquete en la lista y haga clic en Instalar:

![todo:image_alt_text](installation_2.png)

1. Familiarícese con el [Acuerdo de licencia de usuario final de Aspose](https://about.aspose.com/legal/eula).
1. Si se le solicita que revise los cambios, seleccione **Aceptar**.
#### **Consola del Administrador de paquetes**
1. Seleccione el comando de menú **Herramientas** > **Administrador de paquetes de NuGet** > **Consola del administrador de paquetes**.
1. Después de que se abra la consola, asegúrese de que la lista desplegable **Proyecto predeterminado** muestre el proyecto en el que desea instalar el paquete. Si tiene un solo proyecto en la solución, ya está seleccionado.

![todo:image_alt_text](installation_3.png)

1. Introduzca el comando Install-Package Aspose.GIS. La ventana de la consola mostrará la salida del comando.
### **Con MSI Installer o Desde ZIP Archive**
Como alternativa a la instalación de NuGet, puede descargar Aspose.GIS desde la [sección Descargas](https://downloads.aspose.com/gis/net) empaquetado como instalador MSI o archivo ZIP.
## **Instrucciones específicas de la plataforma**
### **Linux**
Al utilizar la funcionalidad de renderizado de mapas de Aspose.GIS en Linux, asegúrese de que la biblioteca System.Drawing.Common esté configurada correctamente. Si obtiene un mensaje de error similar a 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

significa que faltan las dependencias de System.Drawing.Common en el sistema. Para solucionar eso, ejecute:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Requisitos del sistema para Aspose.GIS for .NET**
Todos los componentes de Aspose .NET requieren un conjunto de permisos Full Trust.

Aspose.GIS incluye dos variantes del ensamblado construido para

- .NET Framework 4.7,
- .NET Standard 2.0.

---
### **.NET Framework v4.7 o posterior**
Sistemas operativos: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Tanto las versiones de 32 como de 64 bits son compatibles.
### **.NET Core v2.0 o posterior**
` `Sistemas operativos:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (versión 1607) o versiones posteriores
- Microsoft Windows Server 2008 R2 SP1 (Full Server or Server Core), 2012 SP1 (Full Server or Server Core), 2012 R2 (Full Server or Server Core), 2016 o versiones posteriores (Full Server, Server Core, or Nano Server)
- macOS 10.12 "Sierra" y versiones posteriores
- Linux (64 bits, x86_64 o amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64 bits, arm32), 8.7 o versiones posteriores
  - Ubuntu 18.04 (64 bits, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 o versiones posteriores
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 o versiones posteriores
  - Alpine Linux 3.7 o versiones posteriores

Más detalles disponibles en la guía de .NET Core: [Requisitos previos de Windows](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [Requisitos previos de macOS](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Requisitos previos de Linux](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Soporte experimental**
- Mono 5.4 o posterior
- Xamarin:
  - Xamarin.iOS: versión 10.14 o posterior
  - Xamarin.Android: versión 8.0 o posterior
  - Xamarin.Mac: versión 3.8 o posterior
