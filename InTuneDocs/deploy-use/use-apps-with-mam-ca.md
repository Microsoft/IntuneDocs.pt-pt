---
title: "Utilizar aplicações com acesso condicional para MAM | Documentos da Microsoft"
description: "Compreenda os conceitos de como o acesso condicional para MAM pode ajudar a controlar as aplicações que têm acesso aos serviços do O365."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 10/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 71dcf9bc-bfd1-4e06-b7ad-14b33a2288d0
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 22746475bf50f8e4775c81e6833428c7f2ef9eba


---
# <a name="what-to-expect-when-using-an-app-with-mam-ca"></a>O que esperar ao utilizar uma aplicação com acesso condicional para MAM

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O acesso condicional para MAM verifica a identidade da aplicação aprovada através de uma aplicação de mediação que tem de estar presente no dispositivo:
*  No **iOS**, a **aplicação Azure Authenticator** é a aplicação de mediação.
* No **Android**, a **aplicação Portal da Empresa do Intune** é a aplicação de mediação. 

É pedido aos utilizadores finais que iniciam sessão pela primeira vez numa aplicação que é suportada pelo acesso condicional para MAM, como o OneDrive ou o Outlook, que instalem a aplicação de mediação e registem o dispositivo com o Azure AD. O registo do dispositivo no Azure AD (anteriormente conhecido como Workplace Join) irá criar um certificado e um registo do dispositivo contra os quais são emitidos tokens.  **Não** é o mesmo que a **inscrição MDM**. Não existem políticas ou perfis de gestão aplicados e não existe um inventário das aplicações no dispositivo.  O processo de instalar a aplicação de mediação e registar o dispositivo só acontecerá na primeira utilização de uma aplicação gerida.

Segue-se uma lista de propriedades diretamente derivadas do dispositivo:

* alternativeSecurityIds (Thumbprint do certificado do Azure Active Directory e hash de chave pública)
* tipoDeSODoDispositivo
* versãoDeSODoDispositivo
* nomeaApresentar

## <a name="to-remove-a-device-from-azure-ad-registration"></a>Para remover um dispositivo do registo do Azure AD
Pode remover o registo do dispositivo através da consola de administração do Azure AD, o que, normalmente, é algo a cargo do administrador de TI.  Também pode ser o utilizador final a fazê-lo no próprio dispositivo.

* **Consola de administração do Azure AD**: na consola de administração do Azure AD**, elimine o dispositivo que pretende remover.
* **Dispositivo iOS**: abra a aplicação Azure Authenticator, percorra para a esquerda na conta e selecione anular o registo.  
* **Dispositivo Android**: desinstale a aplicação Portal da Empresa ou remova a conta nas **Definições do sistema**.



## <a name="mam-ca-with-conditional-access-based-on-device-compliance"></a>Acesso condicional para MAM baseado na conformidade do dispositivo  

Pode configurar o [Acesso condicional baseado na conformidade do dispositivo ](restrict-access-to-email-and-o365-services-with-microsoft-intune.md)(**Acesso condicional de dispositivo**) na [consola de administração do Intune](https://manage.microsoft.com) ou na [consola de gestão do Azure AD Premium] (https://manage.windowsazure.com). O acesso condicional de dispositivo exige que os utilizadores estabeleçam ligação ao Exchange Online através de dispositivos geridos pelo Intune que sejam compatíveis com a política de conformidade de dispositivo do Intune ou PCs associados a um domínio.  Se um utilizador pertencer a um ou mais grupos de segurança que são visados por políticas de acesso condicional de dispositivo e acesso condicional para MAM, o utilizador tem de cumprir um dos dois requisitos:
* A aplicação utilizada para aceder ao serviço é uma aplicação móvel que é suportada pelo acesso condicional para MAM e o dispositivo em que a aplicação está em execução tem o **Autenticador para iOS (para dispositivos iOS)** ou a **aplicação Portal da Empresa (para dispositivos Android)** instalado.
* O dispositivo utilizado para aceder ao serviço é **gerido pelo Intune e é compatível** com a política de conformidade de dispositivo do Intune ou é um **PC associado a um domínio**.  Eis alguns exemplos para ajudar a ilustrar isto:
  * Se um utilizador tentar estabelecer ligação a partir da **aplicação de e-mail nativa no iOS**, o utilizador precisará de ter um **dispositivo compatível e gerido**, uma vez que a aplicação de e-mail nativa não é suportada pelo acesso condicional para MAM.
  * Se um utilizador tentar estabelecer ligação a partir de um **PC Windows Home**, a **política de acesso condicional de dispositivo** será aplicada, exigindo que o utilizador utilize um PC associado a um domínio.




## <a name="next-steps"></a>Passos seguintes
[Criar uma Política do Exchange Online para aplicações de MAM](mam-ca-for-exchange-online.md)

[Bloquear aplicações que não tenham autenticação moderna](block-apps-with-no-modern-authentication.md)

### <a name="see-also"></a>Consulte também

[Proteger dados de aplicações com políticas de MAM](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


