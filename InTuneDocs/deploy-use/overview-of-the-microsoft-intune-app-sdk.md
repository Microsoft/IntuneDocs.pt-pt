---
title: "Descrição Geral do SDK da Aplicação Microsoft Intune | Documentos da Microsoft"
description: "O SDK da Aplicação Intune está disponível para as plataformas iOS e Android e permite funcionalidades de gestão de aplicações móveis com o Microsoft Intune."
keywords: 
author: mtillman
manager: angrobe
ms.author: mtillman
ms.date: 12/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ef1751bb-3a2f-4662-a922-38c076869eb3
ms.reviewer: oydang
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: f46f13e9dbf03fa2b3e2ec7339cad927ea0b38e0
ms.openlocfilehash: 99f3aa3c8640dd41133584b3e1cb056dfd493efa


---

# <a name="overview-of-the-microsoft-intune-app-sdk"></a>Descrição Geral do SDK da Aplicação Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

O SDK da Aplicação Intune está disponível para as plataformas iOS e Android e permite funcionalidades de gestão de aplicações móveis com o Microsoft Intune. Além disso, tenta reduzir a quantidade de alterações de código realizadas pelo programador.

Vai descobrir que pode ativar maioria das funcionalidades SDK sem alterar o comportamento da sua aplicação. Para uma melhor experiência de utilizador final e administrador de TI, pode utilizar as nossas APIs para personalizar o comportamento da sua aplicação para funcionalidades que requerem a participação na aplicação.

Assim que tiver a aplicação ativada, os administradores de TI podem implementar políticas em aplicações geridas pelo Intune e tirar partido destas funcionalidades para proteger os dados empresariais.

## <a name="features"></a>Funcionalidades
### <a name="control-users-ability-to-move-corporate-documents"></a>Controlar a capacidade dos utilizadores moverem documentos empresariais
Os administradores de TI podem controlar o reposicionamento de ficheiros dos documentos empresariais em aplicações geridas pelo Intune. Por exemplo, podem implementar uma política que desative as aplicações de cópia de segurança de ficheiros de efetuarem uma cópia de segurança dos dados empresariais para a cloud.  

### <a name="configure-clipboard-restrictions"></a>Configurar restrições da área de transferência
Os administradores de TI podem configurar o comportamento da área de transferência nas aplicações geridas pelo Intune. Por exemplo, podem implementar uma política para que os utilizadores finais não possam utilizar a área de transferência para cortar ou copiar de uma aplicação gerida pelo Intune e colar numa aplicação não gerida.

### <a name="enforce-encryption-on-saved-data"></a>Impor encriptação nos dados guardados
Os administradores de TI podem impor uma política que assegure que os dados guardados no dispositivo pela aplicação são encriptados.

### <a name="remotely-wipe-corporate-data"></a>Apagar dados empresariais remotamente
Os administradores de TI podem apagar dados empresariais remotamente a partir de uma aplicação gerida pelo Intune quando a inscrição do dispositivo for anulada no Microsoft Intune. Esta funcionalidade baseia-se na identidade e elimina apenas os ficheiros relacionados com a identidade empresarial do utilizador final. Para tal, a funcionalidade requer a participação da aplicação. A aplicação pode especificar a identidade na qual deve ocorrer a eliminação com segundo as definições de utilizador. Na ausência destas definições de utilizador especificadas da aplicação, o comportamento predefinido é apagar o diretório da aplicação e notificar o utilizador final que o acesso aos recursos empresariais foi removido.

### <a name="enforce-the-use-of-a-managed-browser"></a>Impor a utilização de um browser gerido
Os administradores de TI podem impor a utilização de um browser gerido quando os utilizadores abrem ligações a partir de aplicações geridas pelo Intune. Quando os utilizadores finais utilizam o browser gerido pelo Microsoft Intune, este ajuda a garantir que as ligações que aparecem nos e-mails num cliente de correio gerido pelo Intune são mantidas dentro do domínio das aplicações geridas pelo Intune.

### <a name="enforce-a-pin-policy"></a>Impor uma política de PIN
Os administradores de TI podem impor uma política de PIN quando uma aplicação gerida pelo Intune é iniciada. Esta política ajuda a garantir que os utilizadores finais que inscreveram os dispositivos no Microsoft Intune são os mesmos utilizadores que estão a iniciar as aplicações. Quando os utilizadores finais configuram o PIN, o SDK da Aplicação Intune utiliza o Azure Active Directory para verificar as credenciais em relação às credenciais de inscrição de dispositivos.

### <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>Exigir que os utilizadores introduzam credenciais antes de poderem iniciar a aplicações
Os administradores de TI podem exigir que os utilizadores finais introduzam as credenciais antes destes poderem iniciar uma aplicação gerida. O SDK da Aplicação Intune utiliza o Azure Active Directory para fornecer uma experiência de início de sessão única. Tal significa que as credenciais, uma vez introduzidas, são reutilizadas para inícios de sessão subsequentes. O SDK também suporta a autenticação de soluções de gestão de identidades [federadas com o Azure Active Directory](/active-directory/active-directory-aadconnect-federation-compatibility).

### <a name="check-device-health-and-compliance"></a>Verificar o estado de funcionamento e a conformidade do dispositivo
Os administradores de TI podem verificar o estado de funcionamento e a conformidade do dispositivo com políticas empresariais antes de os utilizadores finais poderem aceder a aplicações geridas pelo Intune. Na plataforma iOS, esta política verifica se o dispositivo tem jailbreak. Na plataforma Android, esta política verifica se o dispositivo tem root.  



<!--HONumber=Dec16_HO3-->


