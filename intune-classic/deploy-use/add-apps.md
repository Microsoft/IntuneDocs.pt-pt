---
title: Adicionar aplicações
description: Antes de começar a implementar aplicações com o Intune, familiarize-se com os conceitos apresentados neste tópico.
keywords: ''
author: mattbriggs
ms.author: mabrigg
manager: dougeby
ms.date: 07/13/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 2b770f4f-6d36-41e4-b535-514b46e29aaa
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 4c455d590c693893edc5e82c01095b9751a8e357
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="add-apps-with-microsoft-intune"></a>Adicionar aplicações com o Microsoft Intune

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Antes de iniciar a implementação de aplicações com o Microsoft Intune, familiarize-se com os conceitos apresentados neste tópico. Estes conceitos ajudam-no a compreender que aplicações pode implementar em que plataforma. Também podem ajudá-lo a compreender os pré-requisitos que têm de ser cumpridos antes de implementar as aplicações.

## <a name="app-types-that-you-can-deploy"></a>Tipos de aplicações que pode implementar

### <a name="software-installer"></a>Instalador de software

|                                  Tipo de aplicação                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Detalhes                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         <strong>Windows Installer (&#42;.exe, &#42;.msi)</strong>          | Este tipo de aplicação tem de suportar a instalação automática sem intervenção do utilizador. A documentação da aplicação deve incluir as opções relevantes da linha de comandos para instalar automaticamente a aplicação (por exemplo, <strong>/q</strong>). Pode encontrar uma lista das opções comuns da linha de comandos em [Parâmetros da Linha de Comandos para a Ferramenta Microsoft Windows Installer](https://support.microsoft.com/kb/227091).<br><br>Quaisquer ficheiros e pastas adicionais que sejam exigidos pelo programa de configuração da aplicação têm de estar disponíveis na localização que especificar para os ficheiros de configuração da aplicação.<br><br>Na maior parte dos casos, os ficheiros do Windows Installer (.msi) e Windows Installer Patch (.msp) não requerem a instalação de argumentos de linha de comandos pelo Intune. Consulte a documentação da sua aplicação.<br><br>Se forem necessários argumentos de linha de comandos, os mesmos têm de ser introduzidos como pares Nome=Valor (como TRANSFORMS=custom_transform.mst).<br><br>Este tipo de aplicação aplica-se apenas a PCs com o software de cliente do Intune. |
|            <strong>Pacote de Aplicações para Android (&#42;.apk)</strong>            |                                                                                                                                                                                                                                                                                                                                                                                                                                          Para implementar aplicações Android, tem de ter um pacote .apk válido.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|              <strong>Pacote de Aplicações para iOS (&#42;.ipa)</strong>              |                                                                                                                                                                            Para implementar aplicações iOS, precisa de um pacote .ipa válido.<br><br>O pacote .ipa tem de estar assinado pela Apple e a data de expiração indicada no perfil de aprovisionamento tem de ser válida. O Intune pode distribuir as aplicações iOS de certificados de empresa.<br><br>Nem todas as aplicações com certificação de programador da Apple são suportadas.<br><br>A sua empresa tem de estar registada no iOS Developer Enterprise Program.<br><br>Certifique-se de que a firewall da sua organização permite o acesso aos sites de aprovisionamento e certificação de iOS.<br><br>Não precisa de implementar um ficheiro de manifesto (. plist) com a aplicação.                                                                                                                                                                             |
| <strong>Pacote de aplicações do Windows Phone (&#42;.xap, .appx, .appxbundle)</strong> |                                                                                                                                                                                                                                                                                                                                                                  Para implementar aplicações, precisa de um certificado de assinatura de código de dispositivos móveis empresariais. Para obter detalhes, consulte [Configurar a gestão do Windows Phone com o Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).                                                                                                                                                                                                                                                                                                                                                                  |
|         <strong>Pacote de aplicações do Windows (.appx, .appxbundle)</strong>          |                                                                                                                                                                                                                                                                                                                                                                 Para implementar aplicações, precisa de um certificado de assinatura de código de dispositivos móveis empresariais. Para obter detalhes, consulte [Configurar a gestão de dispositivos Windows com o Microsoft Intune](set-up-windows-device-management-with-microsoft-intune.md).                                                                                                                                                                                                                                                                                                                                                                  |
|         <strong>Windows Installer através de MDM (&#42;.msi)</strong>         |                                                                                             Utiliza esta aplicação para criar e implementar aplicações baseadas no Windows Installer em PCs inscritos com o Windows 10. Estes PCs são geridos através da gestão de dispositivos móveis (MDM).<br /><br />Só pode carregar um único ficheiro com a extensão .msi.<br><br>O código de produto do ficheiro e a versão do produto são utilizados para deteção da aplicação.<br><br>É utilizado o comportamento de reinício predefinido da aplicação. O Intune não controla este comportamento.<br><br>São instalados pacotes MSI por utilizador para um único utilizador.<br><br>São instalados pacotes MSI por máquina para todos os utilizadores do dispositivo.<br><br>Atualmente, os pacotes MSI de modo duplo são instalados apenas para todos os utilizadores do dispositivo.<br><br>As atualizações de aplicações são suportadas quando o código de produto MSI de cada versão for igual.<br>                                                                                             |

Todos os tipos de aplicações de instalador de software são carregados para o seu espaço de armazenamento na cloud.

### <a name="external-link"></a>**Ligação Externa**
Utilizar uma ligação externa quando tiver:
- Um URL que permita aos utilizadores transferir uma aplicação a partir de uma loja de aplicações.
- Uma ligação para uma aplicação baseada na Web executada a partir do browser.

As aplicações baseadas em ligações externas não são armazenadas no seu espaço de armazenamento na cloud do Intune.
### <a name="managed-ios-app-from-the-app-store"></a>**Aplicação iOS gerida da loja de aplicações**
Pode utilizar aplicações iOS geridas para gerir e implementar aplicações iOS gratuitas a partir da loja de aplicações. Também pode utilizar aplicações iOS geridas para associar [políticas de gestão de aplicações móveis](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md) a [aplicações compatíveis](https://www.microsoft.com/server-cloud/products/microsoft-intune/partners.aspx) e rever o respetivo estado na consola do administrador.<br /><br />As aplicações iOS geridas não são armazenadas no seu espaço de armazenamento na cloud do Intune.

> [!TIP]
> As opções para dispositivos móveis só estão disponíveis quando [definir a autoridade MDM](prerequisites-for-enrollment.md) para o Intune.

## <a name="intune-software-publisher"></a>Intune Software Publisher
O Microsoft Intune Software Publisher é iniciado quando adiciona ou modifica aplicações a partir da consola do administrador do Intune. A partir do publicador, pode selecionar e configurar um tipo de instalador de software que irá permitir:

- Carregar aplicações (programas para computadores ou aplicações para dispositivos móveis) a guardar no armazenamento na cloud do Intune.
- Ligar a uma loja online ou aplicação Web.

Antes de começar a utilizar o Software Publisher, tem de instalar a versão completa do [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Após a instalação, poderá ser necessário reiniciar o computador para que o Software Publisher seja aberto corretamente.

## <a name="cloud-storage-space"></a>Espaço de armazenamento na cloud
Todas as aplicações que criar com o tipo de instalação do instalador de software são carregadas para o armazenamento na cloud do Microsoft Intune. Uma subscrição de avaliação do Intune inclui 2 gigabytes (GB) de armazenamento baseado na cloud, o qual é utilizado para armazenar aplicações e atualizações geridas. A subscrição completa inclui 20 GB de espaço de armazenamento.

Pode ver quanto espaço está a utilizar no nó **Utilização do Armazenamento** da área de trabalho **Administração**. Pode comprar armazenamento adicional para o Intune com o seu método de compra original.  Se tiver pago através de fatura ou cartão de crédito, visite o [Portal de Gestão de Subscrições](https://portal.office.com/adminportal/home?switchtomodern=true#/subscriptions).  Caso contrário, contacte o seu parceiro ou representante de vendas.

Requisitos de espaço de armazenamento na cloud:

-   Todos os ficheiros de instalação da aplicação têm de estar na mesma pasta.
-   O tamanho máximo para qualquer ficheiro que carregar é de 2 GB.


## <a name="support-for-universal-windows-platform-uwp-apps"></a>Suporte para aplicações da Plataforma Universal do Windows (UWP)
Os PCs com Windows 10 não requerem uma chave de sideload para instalar aplicações de linha de negócio. No entanto, a chave de registo **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps** tem de ter o valor **1** para permitir o sideload.

Se esta chave de registo não estiver configurada, o Intune define automaticamente este valor como **1** quando implementar uma aplicação no dispositivo pela primeira vez. Se tiver definido este valor como **0**, o Intune não pode alterar automaticamente o valor e a implementação de aplicações de linha de negócio falha.

As aplicações de linha de negócio da Plataforma Universal do Windows têm de ser assinadas com um certificado de assinatura de código considerado fidedigno em cada dispositivo em que a aplicação é implementada. Pode utilizar certificados a partir de uma infraestrutura de chaves públicas (PKI) interna ou um certificado a partir de um certificado de raiz público de terceiros instalado no dispositivo.

Em dispositivos Windows 10 Mobile, pode utilizar um certificado de assinatura de código não Symantec para assinar aplicações **.appx** universais. Para aplicações **.xap** e pacotes **.appx** incorporados para o Windows Phone 8.1 que pretende instalar em dispositivos Windows 10 Mobile, tem de utilizar um certificado de assinatura de código da Symantec.

### <a name="dependencies-for-uwp-apps"></a>Dependências de aplicações UWP

Quando adiciona um pacote de appxbundle Universal do Windows 10 ao Intune, também tem de garantir que são carregadas quaisquer dependências da aplicação.
Para carregar dependências, confirme que a pasta **Dependências** que se criou quando foi criada a aplicação está na mesma pasta que o próprio ficheiro .appxbundle.
Dessa forma, ao carregar a aplicação para o Intune, todos os ficheiros na pasta **Dependências** também são carregados. A seguinte captura de ecrã ilustra este processo:


![como selecionar dependências do appxbundle UWP Windows 10](./media/w10-dependencies.png)


## <a name="next-steps"></a>Próximos passos

Tem de adicionar as aplicações na consola do Intune antes de poder implementá-las. Pode adicionar aplicações a [dispositivos inscritos](add-apps-for-mobile-devices-in-microsoft-intune.md) ou [PCs com Windows que gere através do software de cliente do Intune](add-apps-for-windows-pcs-in-microsoft-intune.md).
