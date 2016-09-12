---
title: "Adicionar aplicações | Microsoft Intune"
description: "Antes de começar a implementar aplicações com o Intune, familiarize-se com os conceitos apresentados neste tópico."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 727d28cff074124b5401f6c2931f87df3a9d2d23
ms.openlocfilehash: 93c05ecd0154bb637f421dcc5d7ee56ff8d3ab2d


---

# Adicionar aplicações com o Microsoft Intune
Antes de iniciar a implementação de aplicações com o Microsoft Intune, familiarize-se com os conceitos apresentados neste tópico. Estes conceitos irão ajudá-lo a compreender que aplicações pode implementar em que plataforma. Também podem ajudá-lo a compreender os pré-requisitos que devem ser cumpridos antes de implementar as aplicações.

## Tipos de aplicações que pode implementar

### Instalador de software

|Tipo de aplicação|Detalhes|
|----------------|-------|
|**Windows Installer (&#42;.exe, &#42;.msi)**|Este tipo de aplicação tem de suportar a instalação automática sem intervenção do utilizador. A documentação da aplicação deve incluir as opções relevantes da linha de comandos para instalar automaticamente a aplicação (por exemplo, **/q**). Pode encontrar uma lista das opções comuns da linha de comandos em [Parâmetros da Linha de Comandos para a Ferramenta Microsoft Windows Installer](https://support.microsoft.com/en-us/kb/227091).<br><br>Quaisquer ficheiros e pastas adicionais que sejam exigidos pelo programa de configuração da aplicação têm de estar disponíveis na localização que especificar para os ficheiros de configuração da aplicação.<br><br>Na maior parte dos casos, os ficheiros do Windows Installer (.msi) e Windows Installer Patch (.msp) não requerem a instalação de argumentos de linha de comandos pelo Intune. Consulte a documentação da sua aplicação.<br><br>Se forem necessários argumentos de linha de comandos, os mesmos têm de ser introduzidos como pares Nome=Valor (como TRANSFORMS=custom_transform.mst).|
|**Pacote de Aplicações para Android (&#42;.apk)**|Para implementar aplicações Android, tem de ter um pacote .apk válido.|
|**Pacote de Aplicações para iOS (&#42;.ipa)**|Para implementar aplicações iOS, precisa de um pacote .ipa válido.<br><br>O pacote .ipa tem de estar assinado pela Apple e a data de expiração indicada no perfil de aprovisionamento tem de ser válida. O Intune pode distribuir as aplicações iOS de certificados de empresa.<br><br>Nem todas as aplicações com certificação de programador da Apple são suportadas.<br><br>A sua empresa tem de estar registada no iOS Developer Enterprise Program.<br><br>Certifique-se de que a firewall da sua organização permite o acesso aos sites de aprovisionamento e certificação de iOS.<br><br>Não precisa de implementar um ficheiro de manifesto (. plist) com a aplicação.|
|**Pacote de aplicações do Windows Phone (&#42;.xap, .appx, .appxbundle)**|Para implementar aplicações, precisará de um certificado de assinatura de código de dispositivos móveis empresariais. Para obter detalhes, consulte [Configurar a gestão do Windows Phone com o Microsoft Intune](set-up-windows-phone-management-with-microsoft-intune.md).|
|**Pacote de aplicações do Windows (.appx, .appxbundle)**|Para implementar aplicações, precisará de um certificado de assinatura de código de dispositivos móveis empresariais. Para obter detalhes, consulte [Configurar a gestão de dispositivos Windows com o Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).|
|**Windows Installer através de MDM (&#42;.msi)**|Utiliza esta aplicação para criar e implementar aplicações baseadas no Windows Installer em PCs inscritos com o Windows 10. Estes PCs são geridos através da gestão de dispositivos móveis (MDM).<br /><br />Só pode carregar um único ficheiro com a extensão .msi.<br><br>O código de produto do ficheiro e a versão do produto são utilizados para deteção da aplicação.<br><br>Será utilizado o comportamento de reinício predefinido da aplicação. O Intune não controla este procedimento.<br><br>Serão instalados pacotes MSI por utilizador para um único utilizador.<br><br>Serão instalados pacotes MSI por máquina para todos os utilizadores do dispositivo.<br><br>Atualmente, os pacotes MSI de modo duplo são instalados apenas para todos os utilizadores do dispositivo.<br><br>As atualizações de aplicações são suportadas quando o código de produto MSI de cada versão for igual.<br>
Todos os tipos de aplicações de instalador de software são carregados para o seu espaço de armazenamento na nuvem.

### **Ligação Externa**
Utilizar uma ligação externa quando tiver:
- Um URL que permita aos utilizadores transferir uma aplicação a partir de uma loja de aplicações.
- Uma ligação para uma aplicação baseada na Web executada a partir do browser.

As aplicações baseadas em ligações externas não são armazenadas no seu espaço de armazenamento na nuvem do Intune.
### **Aplicação iOS gerida da loja de aplicações**
Pode utilizar aplicações iOS geridas para gerir e implementar aplicações iOS gratuitas a partir da loja de aplicações. Também pode utilizar aplicações iOS geridas para associar [políticas de gestão de aplicações móveis](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) a [aplicações compatíveis](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) e rever o respetivo estado na consola do administrador.<br /><br />As aplicações iOS geridas não são armazenadas no seu espaço de armazenamento na nuvem do Intune.

> [!TIP]
> As opções para dispositivos móveis só estão disponíveis quando [definir a autoridade MDM](get-ready-to-enroll-devices-in-microsoft-intune.md) para o Intune.

## Intune Software Publisher
O Microsoft Intune Software Publisher é iniciado quando adiciona ou modifica aplicações a partir da consola do administrador do Intune. A partir do publicador, pode selecionar e configurar um tipo de instalador de software que irá permitir:

- Carregar aplicações (programas para computadores ou aplicações para dispositivos móveis) a guardar no armazenamento na nuvem do Intune.
- Ligar a uma loja online ou aplicação Web.

Antes de começar a utilizar o Software Publisher, tem de instalar a versão completa do [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Após a instalação, poderá ser necessário reiniciar o computador para que o Software Publisher seja aberto corretamente.

## Espaço de armazenamento na nuvem
Todas as aplicações que criar com o tipo de instalação do instalador de software (por exemplo, uma aplicação de linha de negócio) são empacotadas e carregadas para o armazenamento na nuvem do Microsoft Intune. Uma subscrição de avaliação do Intune inclui 2 gigabytes (GB) de armazenamento baseado na nuvem, o qual é utilizado para armazenar aplicações e atualizações geridas. A subscrição completa inclui 20 GB de espaço de armazenamento.

Pode ver quanto espaço está a utilizar no nó **Utilização do Armazenamento** da área de trabalho **Administração**.

Requisitos de espaço de armazenamento na nuvem:

-   Todos os ficheiros de instalação da aplicação têm de estar na mesma pasta.
-   O tamanho máximo para qualquer ficheiro que carregar é de 2 GB.


## Suporte para aplicações da Plataforma Universal do Windows (UWP)
Os PCs com Windows 10 não requerem uma chave de sideload para instalar aplicações de linha de negócio. No entanto, a chave de registo **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** tem de ter o valor **1** para permitir o sideload.

Se esta chave de registo não estiver configurada, o Intune irá definir automaticamente este valor como **1** quando implementar uma aplicação no dispositivo pela primeira vez. Se tiver definido este valor como **0**, o Intune não pode alterar automaticamente o valor e a implementação de aplicações de linha de negócio irá falhar.

As aplicações de linha de negócio da Plataforma Universal do Windows têm de ser assinadas com um certificado de assinatura de código considerado fidedigno em cada dispositivo em que a aplicação é implementada. Pode utilizar certificados a partir de uma infraestrutura de chaves públicas (PKI) interna ou um certificado a partir de um certificado de raiz público de terceiros instalado no dispositivo.

Em dispositivos Windows 10 Mobile, pode utilizar um certificado de assinatura de código não Symantec para assinar aplicações **.appx** universais. Para aplicações **.xap** e pacotes **.appx** incorporados para o Windows Phone 8.1 que pretende instalar em dispositivos Windows 10 Mobile, tem de utilizar um certificado de assinatura de código da Symantec.

## Passos seguintes

Terá de adicionar as aplicações na consola do Intune antes de poder implementá-las. Pode adicionar aplicações a [dispositivos inscritos](add-apps-for-mobile-devices-in-microsoft-intune.md) ou [PCs com Windows que gere através do software de cliente do Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).



<!--HONumber=Aug16_HO5-->


