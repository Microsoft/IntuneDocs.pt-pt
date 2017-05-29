---
title: "Vantagens do SDK da Aplicação Intune | Documentos da Microsoft"
description: "O SDK da Aplicação Intune está disponível para as plataformas iOS e Android e permite funcionalidades de gestão de aplicações móveis com o Microsoft Intune."
keywords: 
author: mtillman
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: cd9f05e7-26e6-45e0-8d38-67d8232b1cae
ms.reviewer: jeffgilb
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 7944b6e16e72b781bb2f9101623deb1ce484fa46
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="intune-app-sdk-overview"></a>Descrição geral do SDK da Aplicação Intune
O SDK da Aplicação Intune, disponível para iOS e Android, permite à sua aplicação ter políticas de proteção de aplicações do Intune. Esforça-se para reduzir a quantidade de alterações de código necessárias do programador de aplicações. Irá descobrir que pode ativar a maioria das funcionalidades SDK sem alterar o comportamento da sua aplicação. Para uma melhor experiência de utilizador final e administrador de TI, pode utilizar as nossas APIs para personalizar o comportamento da sua aplicação para funcionalidades que requerem a participação na aplicação.

Após ativar as políticas de proteção de aplicações na sua aplicação, os administradores de TI podem implementar estas políticas de forma a proteger os respetivos dados empresariais dentro da aplicação.

## <a name="app-protection-features"></a>Funcionalidades de proteção de aplicações

Seguem-se exemplos de funcionalidades de proteção de aplicações do Intune que podem ser ativadas com o SDK.

### <a name="control-users-ability-to-move-corporate-files"></a>Controlar a capacidade dos utilizadores de mover ficheiros empresariais
Os administradores de TI podem controlar para onde podem ser movidos os dados escolares ou profissionais na aplicação. Por exemplo, podem implementar uma política que não permita à aplicação criar cópias de segurança de dados empresariais na cloud.

### <a name="configure-clipboard-restrictions"></a>Configurar restrições da área de transferência
Os administradores de TI podem configurar o comportamento da área de transferência nas aplicações geridas pelo Intune. Por exemplo, podem implementar uma política que impeça os utilizadores de cortar ou copiar dados da aplicação e colá-los numa aplicação pessoal não gerida.

### <a name="enforce-encryption-on-saved-data"></a>Impor encriptação nos dados guardados
Os administradores de TI podem impor uma política que assegure que os dados guardados no dispositivo pela aplicação são encriptados.

### <a name="remotely-wipe-corporate-data"></a>Apagar dados empresariais remotamente
Os administradores de TI podem apagar remotamente dados empresariais a partir de uma aplicação gerida pelo Intune. Esta funcionalidade é baseada na identidade e só irá eliminar os ficheiros associados à identidade empresarial do utilizador final. Para tal, a funcionalidade requer a participação da aplicação. A aplicação pode especificar a identidade na qual deve ocorrer a eliminação com segundo as definições de utilizador. Na ausência destas definições de utilizador específicas da aplicação, o comportamento predefinido é apagar o diretório da aplicação e notificar o utilizador final que o acesso foi removido.

### <a name="enforce-the-use-of-a-managed-browser"></a>Impor a utilização de um browser gerido
Os administradores de TI podem forçar as ligações Web na aplicação a serem abertas com a aplicação [Browser Gerido do Intune](../deploy-use/manage-internet-access-using-managed-browser-policies.md). Isto garante que as ligações apresentadas num ambiente empresarial são mantidas no domínio das aplicações geridas pelo Intune.

### <a name="enforce-a-pin-policy"></a>Impor uma política de PIN
Os administradores de TI podem exigir que o utilizador final introduza um PIN antes de aceder a dados empresariais na aplicação. Isto garante que a pessoa a utilizar a aplicação é a mesma pessoa que iniciou sessão com uma conta escolar ou profissional. Quando os utilizadores finais configuram o PIN, o SDK da Aplicação Intune utiliza o Azure Active Directory para verificar as credenciais dos utilizadores finais em relação à conta do Intune inscrita.

### <a name="require-users-to-sign-in-with-work-or-school-account-for-app-access"></a>Exigir que os utilizadores iniciem sessão com contas escolares ou profissionais para aceder à aplicação
Os administradores de TI podem exigir que os utilizadores iniciem sessão com a respetiva conta escolar ou profissional para aceder à aplicação. O SDK da Aplicação Intune utiliza o Azure Active Directory para fornecer uma experiência de início de sessão único, em que as credenciais, uma vez introduzidas, são reutilizadas para inícios de sessão subsequentes. Também é suportada a autenticação de soluções de gestão de identidades federadas com o Azure Active Directory.

### <a name="check-device-health-and-compliance"></a>Verificar o estado de funcionamento e a conformidade do dispositivo
Os administradores de TI podem verificar o estado de funcionamento e a conformidade do dispositivo com políticas do Intune antes de os utilizadores finais acederem à aplicação. No iOS, esta política verifica se o dispositivo foi desbloqueado por jailbreak. No Android, esta política verifica se o dispositivo foi desbloqueado por root.

### <a name="multi-identity-support"></a>Suporte de identidades múltiplas
O suporte de identidades múltiplas é uma funcionalidade do SDK que permite a coexistência de contas geridas por políticas (empresariais) e não geridas (pessoais) numa única aplicação.

Por exemplo, muitos utilizadores configuram as contas de e-mail empresariais e pessoais nas aplicações móveis do Office para iOS e Android. Quando um utilizador acede aos dados com a respetiva conta empresarial, o administrador de TI tem de ter a certeza de que a política de proteção de aplicações será aplicada. No entanto, quando um utilizador está a aceder a uma conta de e-mail pessoal, esses dados devem estar fora do controlo do administrador de TI. O SDK da Aplicação Intune cumpre este processo ao filtrar a política de proteção de aplicações para **apenas** a identidade empresarial na aplicação.

A funcionalidade de identidades múltiplas ajuda a resolver o problema de proteção de dados que as organizações enfrentam com aplicações de loja que suportam contas pessoais e profissionais.


### <a name="app-protection-without-device-enrollment"></a>Proteção de aplicações sem inscrição de dispositivos

>[!IMPORTANT]
>A proteção de aplicações do Intune sem inscrição de dispositivos ainda não está disponível com o SDK da Aplicação Intune para Android. Está disponível com as Ferramentas de Encapsulamento de Aplicações do Intune, o SDK para iOS, o Componente Xamarin do SDK e o Plug-in Cordova do SDK.


Muitos utilizadores com dispositivos pessoais querem aceder a dados empresariais sem inscrever o respetivo dispositivo pessoal num fornecedor de Gestão de Dispositivos Móveis (MDM). Uma vez que a inscrição MDM requer controlo global do dispositivo, os utilizadores costumam hesitar em ceder esse controlo do seu dispositivo pessoal à empresa.

A proteção de aplicações sem inscrição de dispositivos permite ao serviço Microsoft Intune implementar a política de proteção de aplicações diretamente numa aplicação, sem depender de um canal de gestão de dispositivos para implementar a política.

