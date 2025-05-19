---
title: "Instalação"
second_title: Aspose.GIS for .NET
type: docs
url: /pt/net/installation/
weight: 40
keywords: c# gis library, .net gis library
description: Instale a biblioteca ou API GIS C#.NET do NuGet usando a Interface Gráfica do Gerenciador de Pacotes ou o Console, do Arquivo ZIP. Também pode ser usado no .NET Core e no sistema operacional Linux.
---

## **Instale Aspose.GIS**
### **Do NuGet**
Para instalar Aspose.GIS, você usa o Package Manager UI ou o Package Manager Console. Quando você instala um pacote, o NuGet registra a dependência em seu arquivo de projeto ou em um arquivo packages.config.
#### **Package Manager UI**
1. No Solution Explorer, clique com o botão direito do mouse em **Referências** e escolha **Gerenciar Pacotes NuGet**.

![todo:image_alt_text](installation_1.png)

1. Verifique se "nuget.org" está selecionado como a **Fonte do Pacote**, selecione a guia Navegar, procure por Aspose.GIS, selecione esse pacote na lista e clique em Instalar:

![todo:image_alt_text](installation_2.png)

1. Familiarize-se com o [Acordo de Licença de Usuário Final da Aspose](https://about.aspose.com/legal/eula).
1. Se solicitado a revisar as alterações, selecione **OK**.
#### **Package Manager Console**
1. Selecione o menu comando **Ferramentas** > **Gerenciador de Pacotes NuGet** > **Console do Gerenciador de Pacotes**.
1. Depois que o console for aberto, certifique-se de que a lista suspensa **Projeto Padrão** mostre o projeto no qual você deseja instalar o pacote. Se você tiver um único projeto na solução, ele já estará selecionado.

![todo:image_alt_text](installation_3.png)

1. Digite o comando Install-Package Aspose.GIS. A janela do console exibirá a saída para o comando.
### **Com MSI Installer ou Do Arquivo ZIP**
Como alternativa à instalação do NuGet, você pode baixar o Aspose.GIS da [seção de Downloads](https://downloads.aspose.com/gis/net) empacotado como instalador MSI ou arquivo ZIP.
## **Instruções Específicas da Plataforma**
### **Linux**
Ao usar a funcionalidade de renderização de mapa do Aspose.GIS no Linux, certifique-se de que a biblioteca System.Drawing.Common esteja configurada corretamente. Se você receber uma mensagem de erro semelhante a 

"The type initializer for 'Gdip' threw an exception. ---> System.DllNotFoundException: Unable to load shared library 'libdl' or one of its dependencies."

significa que as dependências do System.Drawing.Common estão faltando no sistema. Para corrigir isso, execute:

apt-get update && apt-get install -y libgdiplus libc6-dev libx11-dev
## **Requisitos de Sistema para Aspose.GIS for .NET**
Todos os componentes Aspose .NET exigem o conjunto de permissões Full Trust.

Aspose.GIS inclui duas variantes do assembly construído para

- .NET Framework 4.7,
- .NET Standard 2.0.

### **.NET Framework v4.7 ou posterior**
Sistemas operacionais: 

- Microsoft Windows 10, 8, 7 SP1
- Microsoft Windows Server 2016, 2012 R2, 2012, 2008 R2 SP1

` `Tanto as versões de 32 quanto 64 bits são suportadas.
### **.NET Core v2.0 ou posterior**
` `Sistemas operacionais:

- Microsoft Windows 7 SP1, 8.1, 10 Anniversary Update (versão 1607) ou versões posteriores
- Microsoft Windows Server 2008 R2 SP1 (Full Server ou Server Core), 2012 SP1 (Full Server ou Server Core), 2012 R2 (Full Server ou Server Core), 2016 ou versões posteriores (Full Server, Server Core ou Nano Server)
- macOS 10.12 "Sierra" e versões posteriores
- Linux (64 bits, x86_64 ou amd64):
  - Red Hat Enterprise Linux 7, 6
  - CentOS 7
  - Oracle Linux 7
  - Fedora 28, 27
  - Debian 9 (64 bits, arm32), 8.7 ou versões posteriores
  - Ubuntu 18.04 (64 bits, arm32), 16.04, 14.04
  - Linux Mint 18, 17
  - openSUSE 42.3 ou versões posteriores
  - SUSE Enterprise Linux (SLES) 12 Service Pack 2 ou posterior
  - Alpine Linux 3.7 ou versões posteriores

Mais detalhes disponíveis no Guia do .NET Core: [Pré-requisitos do Windows](https://docs.microsoft.com/en-us/dotnet/core/install/windows?tabs=netcore21#dependencies), [Pré-requisitos do macOS](https://docs.microsoft.com/en-us/dotnet/core/install/macos?tabs=netcore2x#dependencies), [Pré-requisitos do Linux](https://docs.microsoft.com/en-us/dotnet/core/install/linux?tabs=netcore2x).
### **Suporte Experimental**
- Mono 5.4 ou posterior
- Xamarin:
  - Xamarin.iOS: versão 10.14 ou posterior
  - Xamarin.Android: versão 8.0 ou posterior
  - Xamarin.Mac: versão 3.8 ou posterior
