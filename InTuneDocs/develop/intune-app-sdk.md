---
title: "Vantagens do SDK da Aplicação do Intune | Documentos da Microsoft"
description: 
keywords: 
author: mtillman
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 613e293d9bd853d6de7cdc0d753cc8473afc180b
ms.openlocfilehash: e8f96499f006af590b6e7da295503696110dad4e


---

# <a name="intune-app-sdk-overview"></a>Descrição Geral do SDK da Aplicação do Intune
O SDK da Aplicação do Intune está disponível para as plataformas iOS e Android e permite funcionalidades de gestão de aplicações móveis com o Microsoft Intune. Esforça-se para reduzir a quantidade de alterações de código necessárias do programador de aplicações. Irá descobrir que pode ativar a maioria das funcionalidades SDK sem alterar o comportamento da sua aplicação. Para uma melhor experiência de utilizador final e administrador de TI, pode utilizar as nossas APIs para personalizar o comportamento da sua aplicação para funcionalidades que requerem a participação na aplicação. 

Assim que tiver a aplicação ativada, os administradores de TI podem implementar políticas em aplicações geridas pelo Intune e tirar partido destas funcionalidades para proteger os dados empresariais.

## <a name="regular-features"></a>Funcionalidades Normais

### <a name="control-users-ability-to-move-corporate-documents"></a>Controlar a capacidade dos utilizadores moverem documentos empresariais
Os administradores de TI podem controlar o reposicionamento de ficheiros dos documentos empresariais em aplicações geridas pelo Intune. Por exemplo, podem implementar uma política que desative as aplicações de cópia de segurança de ficheiros de efetuarem uma cópia de segurança dos dados empresariais para a nuvem.

### <a name="configure-clipboard-restrictions"></a>Configurar restrições da área de transferência
Os administradores de TI podem configurar o comportamento da área de transferência nas aplicações geridas pelo Intune. Por exemplo, podem implementar uma política para que os utilizadores finais não possam utilizar a área de transferência para cortar/copiar de uma aplicação gerida pelo Intune e colar numa aplicação pessoal e não gerida.

### <a name="enforce-encryption-on-saved-data"></a>Impor encriptação nos dados guardados
Os administradores de TI podem impor uma política que assegure que os dados guardados no dispositivo pela aplicação são encriptados.

### <a name="remotely-wipe-corporate-data"></a>Apagar dados empresariais remotamente
Os administradores de TI podem apagar remotamente dados empresariais a partir de uma aplicação gerida pelo Intune. Esta funcionalidade é baseada na identidade e só irá eliminar os ficheiros associados à identidade empresarial do utilizador final. Para tal, a funcionalidade requer a participação da aplicação. A aplicação pode especificar a identidade na qual deve ocorrer a eliminação com segundo as definições de utilizador. Na ausência destas definições de utilizador específicas da aplicação, o comportamento predefinido é apagar o diretório da aplicação e notificar o utilizador final que o acesso foi removido.

### <a name="enforce-the-use-of-a-managed-browser"></a>Impor a utilização de um browser gerido
Os administradores de TI podem impor a utilização da aplicação Browser Gerido do Intune ao abrir ligações a partir de aplicações geridas pelo Intune. Isto garante que as ligações apresentadas num ambiente empresarial são mantidas no domínio das aplicações geridas pelo Intune.

### <a name="enforce-a-pin-policy"></a>Impor uma política de PIN
Os administradores de TI podem impor uma política de PIN quando uma aplicação gerida pelo Intune é iniciada. Isto garante que o utilizador a iniciar a aplicação é o mesmo utilizador que iniciou sessão com uma conta escolar ou profissional inscrita. Quando os utilizadores finais configuram o PIN, o SDK da Aplicação do Intune utiliza o Azure Active Directory para verificar as credenciais dos utilizadores finais em relação à conta do Intune inscrita.

### <a name="require-users-to-enter-credentials-before-they-can-start-apps"></a>Exigir que os utilizadores introduzam credenciais antes de poderem iniciar a aplicações
Os administradores de TI podem exigir que os utilizadores introduzam as credenciais antes dos utilizadores poderem iniciar uma aplicação gerida  O SDK da Aplicação do Intune utiliza o Azure Active Directory para fornecer uma experiência de início de sessão único, em que as credenciais, uma vez introduzidas, são reutilizadas para inícios de sessão subsequentes. Também é suportada a autenticação de soluções de gestão de identidades [federadas com o Azure Active Directory](https://msdn.microsoft.com/library/azure/jj679342.aspx).

### <a name="check-device-health-and-compliance"></a>Verificar o estado de funcionamento e a conformidade do dispositivo
Os administradores de TI podem verificar o estado de funcionamento e a conformidade do dispositivo com políticas empresariais antes de os utilizadores finais acederem a aplicações geridas pelo Intune. Na plataforma iOS, esta política verifica se o dispositivo tem jailbreak. Na plataforma Android, esta política verifica se o dispositivo tem root.

### <a name="sdk-multi-identity-support"></a>Suporte de identidades múltiplas do SDK
O suporte de identidades múltiplas é uma funcionalidade que permite a coexistência de contas geridas por políticas (empresariais) e não geridas (pessoais) numa única aplicação.

Por exemplo, muitos utilizadores configuram as contas de e-mail empresariais e pessoais na aplicação Outlook para iOS e Android. Quando um utilizador acede aos dados na respetiva conta empresarial, o administrador de TI tem de ter a certeza de que a gestão de políticas de MAM será aplicada. No entanto, quando um utilizador está a aceder a uma conta de e-mail pessoal, esses dados devem estar fora do controlo do administrador de TI. O Microsoft Intune permite isto ao direcionar a política de gestão para a conta empresarial apenas na aplicação. Esta funcionalidade de identidades múltiplas ajuda a resolver o problema de proteção de dados que as organizações estão a enfrentar com dispositivos e aplicações que suportam contas pessoais e profissionais.

* **Como suportar identidades múltiplas**: as APIs do SDK da Aplicação Microsoft Intune permitem-lhe especificar um Nome Principal de Utilizador (UPN) com operações de dados específicas, tais como operações de área de transferência e operações de ficheiros. O SDK utiliza o UPN para corresponder a chamada efetuada ao UPN utilizado para inscrever o dispositivo no serviço Microsoft Intune. Se os UPNs corresponderem, a chamada é tratada como uma chamada de "dados empresariais" e os dados estão protegidos; se os UPNs não corresponderem, a chamada é tratada como uma chamada de "dados pessoais" e os dados não estão protegidos.

### <a name="app-management-without-device-enrollment"></a>Gestão de aplicações sem inscrição de dispositivos

>[!IMPORTANT]
>Atualmente, a gestão de aplicações móveis do Intune sem inscrição de dispositivos só está disponível com o SDK da Aplicação do Intune para iOS. 


Muitos utilizadores com dispositivos pessoais pretendem ver e utilizar os dados empresariais sem inscrever o respetivo dispositivo pessoal num produto de Gestão de Dispositivos Móveis (MDM). Uma vez que a inscrição MDM requer controlo global do dispositivo, os utilizadores hesitam em fornecer esse controlo global do seu próprio dispositivo pessoal à empresa.

A gestão de aplicações sem inscrição de dispositivos permite ao serviço Microsoft Intune implementar a política de MAM diretamente numa aplicação, sem depender de um canal de MDM para implementar a política. Uma vez que não é preciso nenhum canal MDM, a inscrição MDM não é necessária.



<!--HONumber=Dec16_HO2-->


