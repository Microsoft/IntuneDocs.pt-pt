---
title: Gerir a transferência de dados entre aplicações iOS | Microsoft Intune
description: Saiba como utilizar políticas de gestão de aplicações móveis no Microsoft Intune para gerir as transferências de dados entre aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/28/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0435a571ceb5fb4896fe36f01658e20fafd5c56f
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57233122"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Como gerir a transferência de dados entre aplicações iOS no Microsoft Intune

Para ajudar a proteger dados da empresa, restringir as transferências de ficheiros a apenas as aplicações que gere. Pode gerir aplicações iOS das seguintes formas:

-   Impedir a perda de dados da empresa ao configurar uma política de proteção de aplicações para as aplicações, o que chamamos **geridas por políticas** aplicações. Veja [todas as aplicações geridas pelo Intune que pode gerir com a política de proteção de aplicações](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

-   Implementar e gerir aplicações através da **canal MDM**, que requer dispositivos a inscrever-se numa solução de gestão de dispositivos móveis (MDM). As aplicações que implementar podem ser **geridas por políticas** ou outras aplicações geridas.

A funcionalidade **Gestão Open in** dos dispositivos iOS pode limitar as transferências de ficheiros entre as aplicações que são implementadas através do **canal MDM**. Definir *gestão Open in* restrições nas definições de configuração e, em seguida, implementá-las com a sua solução de MDM.  Quando um utilizador instala a aplicação implementada, são aplicadas as restrições definidas.

##  <a name="use-app-protection-with-ios-apps"></a>Utilizar a proteção de aplicações com aplicações iOS
Utilizar políticas de proteção de aplicações com o iOS **gestão Open in** para proteger os dados da empresa das seguintes formas:

-   **Dispositivos de funcionários não geridos por nenhuma solução MDM:** A proteção de aplicações pode configurar definições de política **permitir que a aplicação transfira dados apenas aplicações geridas por políticas**. O *Open-In* comportamento das aplicações geridas por políticas apresenta apenas outras aplicações geridas por políticas como opções para a partilha. Se um utilizador tentar enviar um ficheiro protegido por políticas como um anexo do OneDrive na aplicação de e-mail nativo, esse ficheiro é ilegível.

-   **Dispositivos geridos pelo Intune:** Para dispositivos inscritos no Intune, transferência de dados entre aplicações com políticas de proteção de aplicações e outras aplicações iOS geridas implementadas através do Intune é permitida automaticamente. Para especificar como pretende permitir a transferência de dados para outras aplicações, ative **permitir que a aplicação transfira dados para outras aplicações** e, em seguida, escolha o seu nível favorito de compartilhamento. Para especificar como pretende permitir que uma aplicação receba dados de outras aplicações, ative **permitir que a aplicação receba dados de outras aplicações** e, em seguida, escolha o seu nível favorito de receção de dados. Pode utilizar a funcionalidade **Gestão Open in** para controlar a transferência de dados entre as aplicações que são implementadas através do Intune. Para obter mais informações sobre a receção e partilha de dados de aplicações, veja [Definições de reposicionamento de dados](app-protection-policy-settings-ios.md#data-protection).   

-   **Dispositivos geridos por uma solução MDM de terceiros:** Pode restringir a transferência de dados apenas às aplicações geridas utilizando o iOS **gestão Open in** funcionalidade.
Para certificar-se de que as aplicações que implementar através de uma solução MDM de terceiros também estão associadas com as políticas de proteção de aplicações do Intune, configure a definição de UPN do utilizador, conforme descrito na seção a seguir, [configurar a definição de UPN do utilizador](#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Quando implementar aplicações com a definição de UPN do utilizador, aplicam as políticas de proteção de aplicações à aplicação quando o utilizador inicia sessão com a respetiva conta de trabalho.

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurar a definição de UPN do utilizador para o Microsoft Intune ou EMM de terceiros
A configuração da definição de UPN do utilizador é **obrigatória** para dispositivos geridos pelo Intune ou por uma solução de EMM de terceiros. A configuração de UPN funciona com as políticas de proteção de aplicações que implementar a partir do Intune. O procedimento seguinte é um fluxo geral sobre como configurar a definição de UPN e a experiência do usuário resultante:

1.  No [portal do Azure](https://portal.azure.com), [crie e atribua uma política de proteção de aplicações](app-protection-policies.md) para dispositivos iOS. Configure definições de política em conformidade com os requisitos da sua empresa e selecione as aplicações iOS que devem ter esta política.

2.  Implemente as aplicações e o perfil de e-mail que pretende que sejam geridos através do Intune ou a sua solução de MDM de terceiros através dos seguintes passos generalizados. Esta experiência também é abrangida pelo *exemplo 1*.

3.  Implemente a aplicação com as seguintes definições de configuração de aplicação no dispositivo gerido:

      **key** = IntuneMAMUPN, **value** = <username@company.com>

      Exemplo: [‘IntuneMAMUPN’, ‘jondoe@microsoft.com’]
      
       > [!NOTE]
       > No Intune, a política de configuração de aplicação tem de ser de tipo de inscrição "Dispositivos geridos pelo".
       > Addicionally, a aplicação tem de ser instalado a partir do Portal da empresa do Intune se definido como disponível ou enviada por push conforme necessário para o dispositivo. 

4.  Implemente a política **Gestão Open In** ao utilizar o Intune ou o seu fornecedor de MDM de terceiros nos dispositivos inscritos.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exemplo 1: Experiência de administrador no Intune ou a consola MDM de terceiros

1. Aceda à consola de administração do Intune ou do seu fornecedor de MDM de terceiros. Aceda à secção da consola na qual implementa as definições de configuração de aplicações para dispositivos iOS inscritos.

2. Na secção Configuração da Aplicação, introduza a definição seguinte:

   **key** = IntuneMAMUPN, **value** = <username@company.com>

   A sintaxe exata do par chave/valor pode diferir com base no seu fornecedor de MDM de terceiros. A tabela seguinte mostra exemplos de fornecedores MDM de terceiros e os valores exatos que deve introduzir para o par chave/valor.

   |Fornecedor de MDM de terceiros| Chave de Configuração | Tipo de Valor | Valor de Configuração|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Cadeia | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Cadeia | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Cadeia | ${userUPN} **ou** ${userEmailAddress} |
   |Gestor de Dispositivos Móveis ManageEngine | IntuneMAMUPN | Cadeia | %upn% |


### <a name="example-2-end-user-experience"></a>Exemplo 2: Experiência do utilizador final

1.  Um utilizador instala a aplicação Microsoft Word num dispositivo.

2.  O utilizador inicia a aplicação de e-mail nativa gerida para aceder ao e-mail.

3.  O utilizador tenta abrir um documento de e-mail nativa no Microsoft Word.

4.  Quando inicia a aplicação Word, é pedido ao utilizador iniciar sessão com a respetiva conta profissional. A conta que o usuário insere deve coincidir com a conta especificada nas definições de configuração da aplicação para a aplicação Microsoft Word.

    > [!NOTE]
    > O utilizador pode adicionar e utilizar as respetivas contas pessoais com o Word. Políticas de proteção de aplicações não se aplicam quando o utilizador utiliza o Word fora do contexto de trabalho. 

5.  Após o início de sessão, as definições de política de proteção de aplicações aplicam-se à aplicação Word.

6.  A transferência de dados será efetuada e o documento será etiquetado com uma identidade da empresa na aplicação.  Os dados são tratados num contexto de trabalho e definições de política aplicam-se. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Validar a definição de UPN de utilizador para EMM de terceiros

Depois de configurar a definição de UPN do utilizador, valide a capacidade da aplicação iOS para receber e estar em conformidade com a política de proteção de aplicações do Intune.

Por exemplo, o **exigir PIN da aplicação** definição de política é fácil de testar. Quando a definição de política é igual a **Sim**, o utilizador deverá ver um pedido para definir ou introduzir um PIN antes de poderem aceder os dados da empresa.

Em primeiro lugar, [crie e atribua uma política de proteção de aplicações](app-protection-policies.md) à aplicação iOS. Para obter mais informações sobre como testar a política de proteção de aplicações, consulte [validar as políticas de proteção de aplicações](app-protection-policies-validate.md).


### <a name="see-also"></a>Consulte também
[O que é uma política de proteção de aplicações do Intune](app-protection-policy.md)
