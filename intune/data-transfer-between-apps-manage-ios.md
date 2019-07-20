---
title: Gerir as transferências de dados entre aplicações iOS
titleSuffix: Microsoft Intune
description: Saiba como utilizar políticas de gestão de aplicações móveis no Microsoft Intune para gerir as transferências de dados entre aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/08/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: d10b2d64-8c72-4e9b-bd06-ab9d9486ba5e
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a1e370b65d8bfd7e61562347323bf1455dfe55b
ms.sourcegitcommit: bd09decb754a832574d7f7375bad0186a22a15ab
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/19/2019
ms.locfileid: "68354308"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Como gerir a transferência de dados entre aplicações iOS no Microsoft Intune

Para ajudar a proteger os dados da empresa, restrinja as transferências de arquivos somente para os aplicativos que você gerencia. Pode gerir aplicações iOS das seguintes formas:

- Evitar a perda de dados da empresa Configurando uma política de proteção de aplicativo para os aplicativos, que chamamos de aplicativos **gerenciados por política** . Veja [todas as aplicações geridas pelo Intune que pode gerir com a política de proteção de aplicações](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Implante e gerencie aplicativos por meio do **canal MDM**, que exige que os dispositivos se registrem em uma solução de MDM (gerenciamento de dispositivo móvel). Os aplicativos que você implanta podem ser aplicativos **gerenciados por política** ou outros aplicativos gerenciados.

A funcionalidade **Gestão Open in** dos dispositivos iOS pode limitar as transferências de ficheiros entre as aplicações que são implementadas através do **canal MDM**. Defina as restrições de *Gerenciamento em aberto* nas definições de configuração e implante-as usando sua solução de MDM.  Quando um usuário instala o aplicativo implantado, as restrições que você define são aplicadas.

## <a name="use-app-protection-with-ios-apps"></a>Usar a proteção de aplicativo com aplicativos iOS
Use as políticas de proteção de aplicativo com o recurso iOS **Open in Management** para proteger os dados da empresa das seguintes maneiras:

- **Dispositivos de Propriedade do funcionário não gerenciados por nenhuma solução de MDM:** Você pode definir as configurações de política de proteção de aplicativo para **permitir que o aplicativo transfira dados somente para aplicativos gerenciados por política**. O comportamento de *abertura* em um aplicativo gerenciado por política apresenta apenas outros aplicativos gerenciados por política como opções para compartilhamento. Se um usuário tentar enviar um arquivo protegido por política como um anexo do OneDrive no aplicativo de email nativo, esse arquivo ficará ilegível.

- **Dispositivos gerenciados por soluções de MDM**: Para dispositivos registrados no Intune ou soluções de MDM de terceiros, o compartilhamento de dados entre aplicativos com políticas de proteção de aplicativo e outros aplicativos iOS gerenciados implantados por meio do MDM é controlado pelas políticas de aplicativo do Intune e pelo recurso de **gerenciamento aberto do** Ios. Para garantir que os aplicativos implantados usando uma solução de MDM também estejam associados às políticas de proteção de aplicativo do Intune, defina a configuração de UPN do usuário, conforme descrito na seção a seguir, [defina configuração de UPN do usuário](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Para especificar como você deseja permitir a transferência de dados para outros aplicativos, habilite **enviar dados da organização para outros aplicativos** e, em seguida, escolha o nível de compartilhamento preferencial. Para especificar como você deseja permitir que um aplicativo receba dados de outros aplicativos, habilite **receber dados de outros aplicativos** e, em seguida, escolha o nível preferencial de recebimento de dados. Para obter mais informações sobre a receção e partilha de dados de aplicações, veja [Definições de reposicionamento de dados](app-protection-policy-settings-ios.md#data-protection).

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurar a definição de UPN do utilizador para o Microsoft Intune ou EMM de terceiros
A configuração da definição de UPN do utilizador é **obrigatória** para dispositivos geridos pelo Intune ou por uma solução de EMM de terceiros. A configuração de UPN funciona com as políticas de proteção de aplicativo que você implanta do Intune. O procedimento a seguir é um fluxo geral sobre como definir a configuração de UPN e a experiência do usuário resultante:

1. No [portal do Azure](https://portal.azure.com), [crie e atribua uma política de proteção de aplicações](app-protection-policies.md) para dispositivos iOS. Configure definições de política em conformidade com os requisitos da sua empresa e selecione as aplicações iOS que devem ter esta política.

2. Implante os aplicativos e o perfil de email que você deseja gerenciar por meio do Intune ou sua solução de MDM de terceiros usando as seguintes etapas generalizadas. Essa experiência também é coberta pelo *exemplo 1*.

3. Implante o aplicativo com as seguintes definições de configuração de aplicativo para o dispositivo gerenciado:

      **key** = IntuneMAMUPN, **value** = <username@company.com>

      Exemplo: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > No Intune, o tipo de registro da política de configuração de aplicativo deve ser definido como **dispositivos gerenciados**.
     > Além disso, o aplicativo precisa ser instalado do Portal da Empresa do Intune (se definido como disponível) ou enviado por push conforme necessário para o dispositivo. 

4. Implemente a política **Gestão Open In** ao utilizar o Intune ou o seu fornecedor de MDM de terceiros nos dispositivos inscritos.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exemplo 1: Experiência de administração no Intune ou no console de MDM de terceiros

1. Aceda à consola de administração do Intune ou do seu fornecedor de MDM de terceiros. Aceda à secção da consola na qual implementa as definições de configuração de aplicações para dispositivos iOS inscritos.

2. Na secção Configuração da Aplicação, introduza a definição seguinte:

   **key** = IntuneMAMUPN, **value** = <username@company.com>

   A sintaxe exata do par chave/valor pode diferir com base no seu fornecedor de MDM de terceiros. A tabela a seguir mostra exemplos de provedores de MDM de terceiros e os valores exatos que você deve inserir para o par chave/valor.

   |Fornecedor de MDM de terceiros| Chave de Configuração | Tipo de Valor | Valor de Configuração|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Cadeia | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Cadeia | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Cadeia | ${userUPN} **ou** ${userEmailAddress} |
   |Gerenciamento de ponto de extremidade Citrix | IntuneMAMUPN | Cadeia | ${user.userprincipalname} |
   |Gestor de Dispositivos Móveis ManageEngine | IntuneMAMUPN | Cadeia | %upn% |

> [!NOTE]  
> Para o aplicativo do Outlook no iOS se você implantar uma política de configuração de aplicativo com a opção "usando o designer de configuração", a chave de configuração IntuneMAMUPN será configurada automaticamente nos bastidores da política. Mais detalhes sobre Veja a seção de perguntas frequentes em [novo Outlook para IOS e experiência de política de configuração de aplicativo Android – configuração geral do aplicativo](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481). 


### <a name="example-2-end-user-experience"></a>Exemplo 2: Experiência do utilizador final

1. Um usuário instala o aplicativo Microsoft Word em um dispositivo.

2. O usuário inicia o aplicativo de email nativo gerenciado para acessar seus emails.

3. O usuário tenta abrir um documento do email nativo no Microsoft Word.

4. Quando o aplicativo do Word é iniciado, o usuário é solicitado a entrar com sua conta corporativa. A conta que o usuário insere deve corresponder à conta especificada nas definições de configuração de aplicativo do aplicativo Microsoft Word.

    > [!NOTE]
    > O usuário pode adicionar e usar suas contas pessoais com o Word. As políticas de proteção de aplicativo não se aplicam quando o usuário usa o Word fora de um contexto de trabalho. 

5. Após a entrada, as configurações de política de proteção de aplicativo se aplicam ao aplicativo Word.

6. A transferência de dados será efetuada e o documento será etiquetado com uma identidade da empresa na aplicação.  Os dados são tratados em um contexto de trabalho e as configurações de política se aplicam. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Validar a definição de UPN de utilizador para EMM de terceiros

Depois de definir a configuração de UPN do usuário, valide a capacidade do aplicativo iOS de receber e obedecer à política de proteção de aplicativo do Intune.

Por exemplo, a configuração exigir política de **PIN do aplicativo** é fácil de testar. Quando a configuração de política for igual a **Sim**, o usuário deverá ver um prompt para definir ou inserir um PIN antes que possa acessar os dados da empresa.

Em primeiro lugar, [crie e atribua uma política de proteção de aplicações](app-protection-policies.md) à aplicação iOS. Para obter mais informações sobre como testar a política de proteção do aplicativo, consulte [validar políticas de proteção do aplicativo](app-protection-policies-validate.md).


## <a name="see-also"></a>Consulte também
[O que é uma política de proteção de aplicações do Intune](app-protection-policy.md)
