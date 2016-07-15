---
title: "Adicionar aplicações | Microsoft Intune"
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
ms.reviewer: mghadial
ms.suite: ems
ms.sourcegitcommit: f85e91b985d9d30c71dff9e0d910293354fc40b7
ms.openlocfilehash: 119a795697feb0cdbc2b93293cd66df7e77147cf


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
- Para implementar aplicações, precisará de um certificado de assinatura de código de dispositivos móveis empresariais. Para obter detalhes, consulte [Configurar a gestão do Windows Phone com o Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md).

Este tipo de aplicação é carregado para o seu espaço de armazenamento na nuvem.

Consulte abaixo para obter informações sobre a instalação de aplicações da Plataforma Universal do Windows (UWP) de linha de negócio com o Intune.

### **Pacote de aplicações do Windows (.appx, .appxbundle)**
- Para implementar aplicações, precisará de um certificado de assinatura de código de dispositivos móveis empresariais. Para obter detalhes, consulte [Configurar a gestão de dispositivos Windows com o Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).

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
> [!TIP]As opções para dispositivos móveis só estão disponíveis quando [definir a Autoridade de Gestão de Dispositivos Móveis](get-ready-to-enroll-devices-in-microsoft-intune.md) para o Intune.

## Intune Software Publisher
O **Microsoft Intune Software Publisher** é iniciado quando adiciona ou modifica aplicações a partir da consola do administrador do Microsoft Intune. A partir do publicador, pode selecionar e configurar um tipo de instalador de software que irá carregar aplicações (programas para computadores ou aplicações para dispositivos móveis) a armazenar no armazenamento na nuvem do Intune ou ligar a uma loja online ou aplicação Web.

### Requisitos
Antes de começar a utilizar o Microsoft Intune Software Publisher, tem de instalar a versão completa do [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Após a instalação, poderá ser necessário reiniciar o computador para que o Software Publisher abra corretamente.

## Espaço de armazenamento na nuvem
Todas as aplicações que criar com o tipo de instalação do instalador de software (por exemplo, uma aplicação de linha de negócio) são embaladas e carregadas para o armazenamento na nuvem do Microsoft Intune. Uma subscrição de avaliação do Intune inclui 2 gigabytes (GB) de armazenamento baseado na nuvem, o qual é utilizado para armazenar aplicações e atualizações geridas. Uma subscrição paga inclui 20 GB, com a opção de adquirir armazenamento adicional.

Pode ver quanto espaço está a utilizar e adquirir mais armazenamento no nó **Utilização do Armazenamento** da área de trabalho **Admin**.

Estas regras aplicam-se à aquisição de armazenamento adicional baseado na nuvem para o Intune:

-   Precisa de ter uma subscrição paga ativa para adquirir armazenamento adicional.

-   Apenas os administradores de faturação ou administradores globais do seu Microsoft Online Service podem adquirir armazenamento adicional através do Portal de Gestão do Office 365. Para adicionar, eliminar ou gerir estes administradores, tem de ser um administrador global e iniciar sessão no Portal de Gestão do Office 365.

-   Se for um cliente de licenciamento em volume que adquiriu o Intune ou o Suplemento Microsoft Intune através do Contrato Enterprise, contacte o seu Gestor de Conta Microsoft ou o Parceiro Microsoft para obter informações sobre os preços e adquirir armazenamento adicional.

#### Requisitos de espaço de armazenamento na nuvem

-   Certifique-se de que todos os ficheiros de instalação de aplicação estão na mesma pasta.

-   O tamanho máximo para qualquer ficheiro que carregar é de 2 GB.


## Suporte para aplicações da Plataforma Universal do Windows (UWP)
Os PC com Windows 10 não requerem uma chave de sideload para instalar aplicações de linha de negócio. No entanto, a chave de registo **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** tem de ter o valor **1** para permitir o sideload.

Se esta chave de registo não estiver configurada, o Intune irá definir automaticamente este valor como **1** quando implementar uma aplicação no dispositivo pela primeira vez. Se tiver definido este valor como **0**, o Intune não pode alterar automaticamente o valor e a implementação de aplicações de linha de negócio irá falhar.

As aplicações de linha de negócio da Plataforma Universal do Windows têm de ser assinadas com um certificado de assinatura de código considerado fidedigno em cada dispositivo em que a aplicação é implementada. Pode utilizar certificados a partir de uma infraestrutura PKI interna ou um certificado a partir de um certificado de raiz público de terceiros instalado no dispositivo.

Em dispositivos Windows 10 Mobile, pode utilizar um certificado de assinatura de código não Symantec para assinar aplicações **.appx** universais. Para aplicações **.xap** e pacotes **.appx** incorporados para o Windows Phone 8.1 que pretende instalar em dispositivos Windows 10 Mobile, tem de utilizar um certificado de assinatura de código da Symantec.

## Passos seguintes 

Em seguida, terá de adicionar as aplicações na consola do Intune antes de poder implementá-las. Pode adicionar aplicações a [dispositivos inscritos](add-apps-for-mobile-devices-in-microsoft-intune.md) ou [PC com Windows que pode gerir através do software de cliente do Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).



<!--HONumber=Jun16_HO3-->


