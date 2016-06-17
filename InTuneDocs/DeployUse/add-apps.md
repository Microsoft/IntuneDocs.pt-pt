---
# required metadata

title: Adicionar aplicações | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Adicionar aplicações com o Microsoft Intune
Antes de iniciar a implementação de aplicações com o Microsoft Intune, familiarize-se com os conceitos apresentados neste tópico. Estes irão ajudá-lo a compreender as aplicações que pode implementar em que plataforma e a compreender os pré-requisitos que devem ser cumpridos antes de fazê-lo.

## Tipos de aplicações que pode implementar com o Intune
Pode implementar aplicações em todos os tipos de dispositivos suportados pelo Intune. Consoante o tipo de aplicação que pretende implementar, o processo e os dispositivos suportados irão variar. Utilize as informações seguintes para ajudá-lo a compreender o que pode e não pode implementar:


### **Windows Installer (&#42;.exe, &#42;.msi)**
- Este tipo de aplicação tem de suportar a instalação automática sem intervenção do utilizador. A documentação da aplicação deve incluir as opções relevantes da linha de comandos para instalar automaticamente a aplicação (por exemplo, **/q**). Pode encontrar uma lista de opções da linha de comandos comuns [aqui](https://support.microsoft.com/en-us/kb/227091).
- Quaisquer ficheiros e pastas adicionais que sejam exigidos pelo programa de configuração da aplicação têm de estar disponíveis na localização que especificar para os ficheiros de configuração da aplicação.
- Na maior parte dos casos, os ficheiros Windows Installer (.msi) e Windows Installer Patch (.msp) não requerem a instalação de argumentos de linha de comandos pelo Intune. Consulte a documentação da sua aplicação. Se forem necessários argumentos de linha de comandos, os mesmos têm de ser introduzidos como pares Nome=Valor (como TRANSFORMS=custom_transform.mst).

Este tipo de aplicação é carregado para o seu espaço de armazenamento na nuvem.
### **Pacote de Aplicações para Android (ficheiro &#42;.apk)**
Este tipo de aplicação é carregado para o seu espaço de armazenamento na nuvem.
### **Pacote de Aplicações para iOS (ficheiro &#42;.ipa)**
- Para implementar aplicações iOS, precisa de um pacote .ipa válido.
- O pacote .ipa tem de estar assinado pela Apple e a data de expiração indicada no perfil de aprovisionamento tem de ser válida. O Intune pode distribuir as aplicações iOS de certificados de empresa. Nem todas as aplicações com certificação de programador da Apple são suportadas.
- A sua empresa tem de estar registada no iOS Developer Enterprise Program.
- Certifique-se de que a firewall da sua organização permite o acesso aos sites de aprovisionamento e certificação de iOS.
- Não é necessário implementar um ficheiro de manifesto (.plist) com a aplicação.

Este tipo de aplicação é carregado para o seu espaço de armazenamento na nuvem.

Atualmente, os utilizadores finais não podem instalar aplicações empresariais diretamente a partir da aplicação Portal da Empresa do Intune para iOS. Isto deve-se a restrições colocadas nas aplicações que são publicadas na iOS App Store (consulte as [Diretrizes de Revisão da App Store](https://developer.apple.com/app-store/review/guidelines/)). Os utilizadores podem aceder a aplicações empresariais (incluindo aplicações geridas da App Store e pacotes de aplicações de linha de negócio) ao iniciar a aplicação Portal da Empresa nos respetivos dispositivos e ao tocar no mosaico Aplicações da Empresa, que irá abrir o browser e redirecioná-los para o Portal Web do Intune.

### **Pacote de aplicações do Windows Phone (&#42;.xap, .appx, .appxbundle)**
- Para implementar aplicações, precisará de um certificado de assinatura de código de dispositivos móveis empresariais. Para detalhes, consulte [Configurar a gestão do Windows Phone com o Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md).

Este tipo de aplicação é carregado para o seu espaço de armazenamento na nuvem.

Consulte abaixo para obter informações sobre a instalação de aplicações da Plataforma Universal do Windows (UWP) de linha de negócio com o Intune.

### **Pacote de aplicações do Windows (.appx, .appxbundle)**
- Para implementar aplicações, precisará de um certificado de assinatura de código de dispositivos móveis empresariais. Para detalhes, consulte [Configurar a gestão de dispositivos Windows com o Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).

Este tipo de aplicação é carregado para o seu espaço de armazenamento na nuvem.
### **Windows Installer através de MDM (&#42;.msi)**
Este tipo de instalador permite-lhe criar e implementar aplicações baseadas no Windows Installer em PCs inscritos que estejam a executar o Windows 10.<br /><br />As considerações seguintes são aplicáveis quando utiliza este tipo de instalador:
- Só pode carregar um único ficheiro com a extensão .msi.
- O código de produto do ficheiro e a versão do produto são utilizados para deteção da aplicação.
- Será utilizado o comportamento de reinício predefinido da aplicação. O Intune não controla este procedimento.
- Serão instalados pacotes MSI por utilizador para um único utilizador.
- Serão instalados pacotes MSI por máquina para todos os utilizadores do dispositivo.
- Atualmente, os pacotes MSI de modo duplo são instalados apenas para todos os utilizadores do dispositivo.
- As atualizações de aplicações são suportadas quando o código de produto MSI de cada versão for igual.

Este tipo de aplicação é carregado para o seu espaço de armazenamento na nuvem.
### **Ligação Externa**
Utilizada quando tiver:
- Um **URL** que permita aos utilizadores transferir uma aplicação a partir de uma loja de aplicações.
- Uma **ligação** para uma aplicação baseada na Web executada a partir do browser.

As aplicações baseadas em ligações externas não são armazenadas no seu espaço de armazenamento na nuvem do Intune.
### **Aplicação iOS gerida da loja de aplicações**
Permite gerir e implementar aplicações iOS gratuitas a partir da loja de aplicações. Também permite associar [políticas de gestão de aplicações móveis](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) a [aplicações compatíveis](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) e rever o respetivo estado na consola de administrador.<br /><br />As aplicações iOS geridas não são armazenadas no seu espaço de armazenamento na nuvem do Intune.
> [!TIP]As opções para dispositivos móveis só estão disponíveis quando definir a [Autoridade de Gestão de Dispositivos Móveis](get-ready-to-enroll-devices-in-microsoft-intune.md) para o Intune.

## Suporte para aplicações da Plataforma Universal do Windows (UWP)
Os dispositivos Windows 10 não requerem uma chave de sideload para instalar aplicações de linha de negócio. No entanto, a chave de registo **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** tem de ter o valor **1** para permitir o sideload.

Se esta chave de registo não estiver configurada, o Intune irá definir automaticamente este valor como **1** quando implementar uma aplicação no dispositivo pela primeira vez. Se tiver definido este valor como **0**, o Intune não pode alterar automaticamente o valor e a implementação de aplicações de linha de negócio irá falhar.

As aplicações de linha de negócio da Plataforma Universal do Windows têm de ser assinadas com um certificado de assinatura de código considerado fidedigno em cada dispositivo em que a aplicação é implementada. Pode utilizar certificados a partir de uma infraestrutura PKI interna ou um certificado a partir de um certificado de raiz público de terceiros instalado no dispositivo.

Em dispositivos Windows 10 Mobile, pode utilizar um certificado de assinatura de código não Symantec para assinar aplicações **.appx** universais. Para aplicações **.xap** e pacotes **.appx** incorporados para o Windows Phone 8.1 que pretende instalar em dispositivos Windows 10 Mobile, tem de utilizar um certificado de assinatura de código da Symantec.

## Passos seguintes 

Em seguida, terá de adicionar as aplicações na consola do Intune antes de poder implementá-las. Pode adicionar aplicações para [dispositivos inscritos](add-apps-for-mobile-devices-in-microsoft-intune.md) ou [PCs Windows que gere com o software de cliente do Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).

<!--HONumber=May16_HO4-->


