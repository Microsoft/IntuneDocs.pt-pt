---
title: "Acesso condicional ao O365 com base na aplicação| Microsoft Intune"
description: "Compreenda os conceitos de como o acesso condicional para MAM pode ajudar a controlar as aplicações que têm acesso aos serviços do O365."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 10/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bd6bee60-5e39-42c8-a2e9-f5865ac3573f
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 64eaba6918c4a5c7ccc39fb8ccfeae729a34ff4c
ms.openlocfilehash: a03faa57f9bf1ec6784f0b1ec2d41d3f4cd88a12


---

# Criar uma política que apenas permita aplicações móveis que suportem políticas de MAM do Intune para aceder aos serviços do Office 365
[As políticas de gestão de aplicações móveis (MAM) do Intune](protect-apps-and-data-with-microsoft-intune.md) ajudam a proteger os dados da sua empresa em dispositivos que estão inscritos para gestão no Intune. Também pode utilizar políticas de MAM em **dispositivos que sejam propriedade de funcionários e não estejam inscritos para gestão no Intune**.  Neste caso, apesar de não gerir o dispositivo, ainda precisa de garantir que os recursos e os dados da sua empresa estão protegidos. Ao utilizar acesso condicional para MAM, pode criar uma política para permitir que apenas as aplicações móveis que suportam políticas de MAM do Intune acedam a serviços do O365, como o Exchange Online.

Por exemplo, ao permitir que apenas a **aplicação Microsoft Outlook** aceda ao Exchange Online, pode **bloquear as aplicações de correio incorporadas no iOS e Android**, que não têm a proteção de dados das políticas de MAM do Intune para obter e-mails do **Exchange Online**.

## Pré-requisitos
**Antes** de poder configurar a política de acesso condicional para MAM, tem de ter uma **subscrição do Enterprise Mobility + Security ou do Azure Active Directory Premium** e os utilizadores finais têm de ter uma licença do EMS ou do Azure AD. Para saber mais detalhes, consulte a [página de preços do Enterprise Mobility](https://www.microsoft.com/en-us/cloud-platform/enterprise-mobility-pricing) ou a [página de preços do Azure Active Directory](https://azure.microsoft.com/en-us/pricing/details/active-directory/).


## Aplicações suportadas
**Exchange Online**
* Microsoft Outlook para Android e iOS

## Sobrepor com outros métodos de autenticação e acesso condicional
### Acesso condicional para MAM com autenticação baseada no certificado do Azure Active Directory

O acesso condicional para MAM não pode ser utilizado com a autenticação baseada no certificado do Azure Active Directory (Azure AD). Só pode ter um destes configurado de cada vez.
### Acesso condicional para MAM baseado na conformidade do dispositivo  

Pode configurar o [Acesso condicional baseado na conformidade do dispositivo ](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)(**Acesso condicional de dispositivo**) na [consola de administração do Intune](https://manage.microsoft.com) ou na [consola de gestão do Azure AD Premium] (https://manage.windowsazure.com). O acesso condicional de dispositivo exige que os utilizadores estabeleçam ligação ao Exchange Online através de dispositivos geridos pelo Intune que sejam compatíveis com a política de conformidade de dispositivo do Intune ou PCs associados a um domínio.  Se um utilizador pertencer a um ou mais grupos de segurança que são direcionados para políticas de acesso condicional de dispositivo e acesso condicional para MAM, o utilizador tem de cumprir um dos dois requisitos:
* A aplicação utilizada para aceder ao serviço é uma aplicação móvel que é suportada pelo acesso condicional para MAM e o dispositivo em que a aplicação está em execução tem o **Autenticador para iOS (para dispositivos iOS)** ou a **aplicação Portal da Empresa (para dispositivos Android)** instalado.
* O dispositivo utilizado para aceder ao serviço é **gerido pelo Intune e é compatível** com a política de conformidade de dispositivo do Intune ou é um **PC associado a um domínio**.  Eis alguns exemplos para ajudar a ilustrar isto:
  * Se um utilizador tentar estabelecer ligação a partir da **aplicação de e-mail nativa no iOS**, o utilizador precisará de ter um **dispositivo compatível e gerido**, uma vez que a aplicação de e-mail nativa não é suportada pelo acesso condicional para MAM.
  * Se um utilizador tentar estabelecer ligação a partir de um **PC Windows Home**, a **política de acesso condicional de dispositivo** será aplicada, exigindo que o utilizador utilize um PC associado a um domínio.


## O que esperar ao utilizar uma aplicação com acesso condicional para MAM
O acesso condicional para MAM verifica a identidade da aplicação aprovada através de uma aplicação de mediação que tem de estar presente no dispositivo:
*  No **iOS**, a **aplicação Azure Authenticator** é a aplicação de mediação.
* No **Android**, a **aplicação Portal da Empresa do Intune** é a aplicação de mediação. 

É pedido aos utilizadores finais que iniciam sessão pela primeira vez numa aplicação que é suportada pelo acesso condicional para MAM, como o OneDrive ou o Outlook, que instalem a aplicação de mediação e registem o dispositivo com o Azure AD. O registo do dispositivo no Azure AD (anteriormente conhecido como Workplace Join) irá criar um certificado e um registo do dispositivo contra os quais são emitidos tokens.  **Não** é o mesmo que a **inscrição MDM**. Não existem políticas ou perfis de gestão aplicados e não existe um inventário das aplicações no dispositivo.  O processo de instalar a aplicação de mediação e registar o dispositivo só acontecerá na primeira utilização de uma aplicação gerida.


## Passos seguintes
[Criar uma Política do Exchange Online para aplicações de MAM](mam-ca-for-exchange-online.md)

[Bloquear aplicações que não possuem autenticação moderna](block-apps-with-no-modern-authentication.md)

### Consulte também

[Proteger dados de aplicações com políticas de MAM](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Oct16_HO2-->


