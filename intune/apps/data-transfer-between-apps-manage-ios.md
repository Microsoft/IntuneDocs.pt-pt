---
title: Gerir as transferências de dados entre aplicações iOS
titleSuffix: Microsoft Intune
description: Saiba como utilizar políticas de gestão de aplicações móveis no Microsoft Intune para gerir as transferências de dados entre aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/09/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a1ba4a5e6096f77c87560554fd2c9cd601a33e4
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511723"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Como gerir a transferência de dados entre aplicações iOS no Microsoft Intune

Para ajudar a proteger os dados da empresa, restringir as transferências de ficheiros apenas para as aplicações que gere. Pode gerir aplicações iOS das seguintes formas:

- Proteja os dados org para contas de trabalho ou escola configurando uma política de proteção de aplicações para as aplicações. que chamamos *de aplicações geridas por políticas.*  Veja [todas as aplicações geridas pelo Intune que pode gerir com a política de proteção de aplicações](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Implementar e gerir as aplicações através da gestão de dispositivos iOS, que requer dispositivos para se inscreverem numa solução de Gestão de Dispositivos Móveis (MDM). As aplicações que implementa podem ser *aplicações geridas por políticas* ou outras aplicações geridas pelo iOS.

A funcionalidade **de gestão Open-in** para dispositivos iOS matriculados pode limitar as transferências de ficheiros entre aplicações geridas pelo iOS. Detete restrições *de gestão open-in* em configurações de configuração e, em seguida, implemente-as utilizando a sua solução MDM.  Quando um utilizador instala a aplicação implementada, as restrições que definiu são aplicadas.

## <a name="use-app-protection-with-ios-apps"></a>Utilize a proteção de aplicativos com aplicações iOS
Utilize as políticas de proteção de aplicações com a funcionalidade **de gestão open-in** do iOS para proteger os dados da empresa das seguintes formas:

- **Dispositivos não geridos por qualquer solução MDM:** Pode definir as definições da política de proteção de aplicações para controlar a partilha de dados com outras aplicações através de *extensões* *Open-in* ou Share .  Para tal, configure os **dados do Send Org para outras** aplicações para aplicações geridas pela Policy com valor de **filtragem Open-In/Share.**  O comportamento *Open-in/Share* na *aplicação gerida* pela política apresenta apenas outras *aplicações geridas* por políticas como opções de partilha. 

- **Dispositivos geridos por soluções MDM**: Para dispositivos matriculados em soluções de MDM intune ou de terceiros, a partilha de dados entre apps com políticas de proteção de aplicações e outras aplicações geridas para iOS implementadas através do MDM é controlada pelas políticas de APP Intune e o iOS Open na funcionalidade de **gestão.** Para garantir que as aplicações que implementa utilizando uma solução MDM também estão associadas às suas políticas de proteção de aplicações Intune, configure a configuração UPN do utilizador conforme descrito na seguinte secção, [configuração upN do utilizador Configure](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Para especificar como pretende permitir a transferência de dados para outras aplicações, ative os **dados do Send Org para outras aplicações** e, em seguida, escolha o seu nível de partilha preferido. Para especificar como pretende permitir que uma aplicação receba dados de outras apps, ative **o Receber dados de outras apps** e, em seguida, escolha o seu nível preferido de receber dados. Para obter mais informações sobre a receção e partilha de dados de aplicações, veja [Definições de reposicionamento de dados](app-protection-policy-settings-ios.md#data-protection).

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurar a definição de UPN do utilizador para o Microsoft Intune ou EMM de terceiros
Configurar a definição UPN do utilizador é **necessária** para dispositivos que são geridos pela Intune ou uma solução EMM de terceiros para identificar a conta de utilizador inscrita. A configuração UPN funciona com as políticas de proteção de aplicações que implementa a partir de Intune. O seguinte procedimento é um fluxo geral sobre como configurar a configuração da UPN e a experiência do utilizador resultante:

1. No [portal Azure, crie](https://portal.azure.com) [e atribua uma política](app-protection-policies.md) de proteção de aplicações para iOS/iPadOS. Configure definições de política em conformidade com os requisitos da sua empresa e selecione as aplicações iOS que devem ter esta política.

2. Implemente as aplicações e o perfil de e-mail que deseja gerido através do Intune ou da sua solução MDM de terceiros utilizando os seguintes passos generalizados. Esta experiência também é abrangida pelo *Exemplo 1*.

3. Implemente a aplicação com as seguintes definições de configuração da aplicação para o dispositivo gerido:

      **chave** = IntuneMAMUPN, **valor** = <username@company.com>

      Exemplo: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > Em Intune, o tipo de inscrição da política de configuração da aplicação deve ser definido para **Dispositivos Geridos**.
     > Além disso, a aplicação precisa de ser instalada a partir do Portal da Empresa Intune (se definida como disponível) ou empurrada conforme necessário para o dispositivo. 

4. Implemente a política **Gestão Open In** ao utilizar o Intune ou o seu fornecedor de MDM de terceiros nos dispositivos inscritos.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exemplo 1: experiência de administrador no Intune ou na consola de MDM de terceiros

1. Aceda à consola de administração do Intune ou do seu fornecedor de MDM de terceiros. Aceda à secção da consola na qual implementa as definições de configuração de aplicações para dispositivos iOS inscritos.

2. Na secção Configuração da Aplicação, introduza a definição seguinte:

   **chave** = IntuneMAMUPN, **valor** = <username@company.com>

   A sintaxe exata do par chave/valor pode diferir com base no seu fornecedor de MDM de terceiros. A tabela que se segue apresenta exemplos de fornecedores de MDM de terceiros e os valores exatos que deve introduzir para o par chave/valor.

   |Fornecedor de MDM de terceiros| Chave de Configuração | Tipo de Valor | Valor de Configuração|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Cadeia | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Cadeia | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Cadeia | ${userUPN} **ou** ${userEmailAddress} |
   |Gestão de Pontos Finais de Citrix | IntuneMAMUPN | Cadeia | ${user.userprincipalname} |
   |Gestor de Dispositivos Móveis ManageEngine | IntuneMAMUPN | Cadeia | %upn% |

> [!NOTE]  
> Para o Outlook para iOS/iPadOS, se implementar uma Política de Configuração de Aplicações gerida com a opção "Utilizar o designer de configuração" e permitir permitir apenas contas de **trabalho ou de escola,** a chave de configuração IntuneMAMUPN está configurada automaticamente nos bastidores da apólice. Mais detalhes podem ser encontrados na secção FAQ em [New Outlook para iOS e Android App Configuração De Política de Política de Configuração – Configuração Geral](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481)de Aplicações . 


### <a name="example-2-end-user-experience"></a>Exemplo 2: experiência de utilizador final

*Partilha de uma* app gerida por políticas *para outras aplicações com partilha de OS*

1. Um utilizador abre a aplicação Microsoft OneDrive num dispositivo iOS matriculado e inicia sintetizadorna na sua conta de trabalho.  A conta que o utilizador introduz deve corresponder à conta UPN especificada nas definições de configuração da aplicação para a aplicação Microsoft OneDrive.

2. Após o iniciar o sessão, as definições de APP configuradas pelo administrador aplicam-se à conta de utilizador no Microsoft OneDrive.  Isto inclui configurar os **dados do Send Org para outras aplicações** para as **aplicações geridas** pela Policy com valor de partilha de OS.

3. O utilizador pré-visualiza um ficheiro de trabalho e tenta partilhar através do Open-in para a aplicação gerida pelo iOS.  

4. A transferência de dados tem sucesso e os dados estão agora protegidos pela **gestão open-in** na aplicação gerida pelo iOS.  A INTune APP não se aplica a aplicações que não sejam *aplicações geridas por políticas.*

*Partilha de uma* aplicação gerida pelo iOS *para uma* aplicação gerida por políticas com dados org *de entrada*

1. Um utilizador abre o Correio nativo num dispositivo iOS matriculado com um perfil de e-mail gerido.  

1. O utilizador abre um anexo de documento de trabalho do Correio nativo para o Microsoft Word.

1. Quando a aplicação Word é lançada, uma de duas experiências ocorre:
   1. Os dados são protegidos pela Intune APP quando:
      - O utilizador está inscrito na sua conta de trabalho que corresponde à conta UPN especificada nas definições de configuração da aplicação para a aplicação Microsoft Word. 
      - As definições de APP configuradas pelo administrador aplicam-se à conta de utilizador no Microsoft Word.  Isto inclui configurar os **dados do Receive de outras aplicações** para as aplicações All com o valor de dados org de **entrada.**
      - A transferência de dados tem sucesso e o documento está marcado com a identidade de trabalho na aplicação.  A Intune APP protege as ações do utilizador para o documento.
   1. Os dados **não** são protegidos pela Intune APP quando:
      - O utilizador **não** está inscrito na sua conta de trabalho.
      - As definições configuradas pelo administrador **não** são aplicadas ao Microsoft Word porque o utilizador não está inscrito.
      - A transferência de dados tem sucesso e o documento **não** está marcado com a identidade de trabalho na aplicação.  A Intune APP **não** protege as ações do utilizador para o documento por não estar ativa.

    > [!NOTE]
    > O utilizador pode adicionar e utilizar as suas contas pessoais com o Word. As políticas de proteção de aplicações não se aplicam quando o utilizador utiliza o Word fora de um contexto de trabalho. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Validar a definição de UPN de utilizador para EMM de terceiros

Depois de configurar a definição UPN do utilizador, valide a capacidade da aplicação iOS de receber e cumprir a política de proteção de aplicações Intune.

Por exemplo, a definição da política PIN da **aplicação Require** é fácil de testar. Quando a definição de política é igual a **Exigir,** o utilizador deve consultar uma solicitação para definir ou introduzir um PIN antes de poder aceder aos dados da empresa.

Em primeiro lugar, [crie e atribua uma política de proteção de aplicações](app-protection-policies.md) à aplicação iOS. Para obter mais informações sobre como testar a política de proteção de aplicações, consulte as políticas de proteção de [aplicações .](app-protection-policies-validate.md)


## <a name="see-also"></a>Veja também
[O que é uma política de proteção de aplicações do Intune](app-protection-policy.md)
