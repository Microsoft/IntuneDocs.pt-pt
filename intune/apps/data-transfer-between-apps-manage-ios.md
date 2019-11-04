---
title: Gerir as transferências de dados entre aplicações iOS
titleSuffix: Microsoft Intune
description: Saiba como utilizar políticas de gestão de aplicações móveis no Microsoft Intune para gerir as transferências de dados entre aplicações.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/03/2019
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
ms.openlocfilehash: cdc849405b7404203faa6e86d3fed1ea8e35ec43
ms.sourcegitcommit: 60f0ff6d2efbae0f2ce14b9a9f3f9267309e209b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/01/2019
ms.locfileid: "73414627"
---
# <a name="how-to-manage-data-transfer-between-ios-apps-in-microsoft-intune"></a>Como gerir a transferência de dados entre aplicações iOS no Microsoft Intune

Para ajudar a proteger os dados da empresa, restrinja as transferências de arquivos somente para os aplicativos que você gerencia. Pode gerir aplicações iOS das seguintes formas:

- Proteja os dados da organização para contas corporativas ou de estudante Configurando uma política de proteção de aplicativo para os aplicativos. que chamamos de *aplicativos gerenciados por política*.  Veja [todas as aplicações geridas pelo Intune que pode gerir com a política de proteção de aplicações](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

- Implante e gerencie os aplicativos por meio do gerenciamento de dispositivos iOS, o que exige que os dispositivos se registrem em uma solução de MDM (gerenciamento de dispositivo móvel). Os aplicativos que você implanta podem ser *aplicativos gerenciados por política* ou outros aplicativos gerenciados do Ios.

O recurso de **Gerenciamento do Open-in** para dispositivos IOS registrados pode limitar transferências de arquivos entre aplicativos gerenciados do Ios. Definir restrições de *Gerenciamento de abertura* em definições de configuração e implantá-las usando sua solução de MDM.  Quando um usuário instala o aplicativo implantado, as restrições que você define são aplicadas.

## <a name="use-app-protection-with-ios-apps"></a>Usar a proteção de aplicativo com aplicativos iOS
Use as políticas de proteção de aplicativo com o recurso de **gerenciamento aberto** do IOS para proteger os dados da empresa das seguintes maneiras:

- **Dispositivos não gerenciados por nenhuma solução de MDM:** Você pode definir as configurações de política de proteção de aplicativo para controlar o compartilhamento de dados com outros aplicativos por meio de *extensões de compartilhamento*ou *abertas* .  Para fazer isso, configure a configuração **enviar dados org para outro aplicativo** para **aplicativos gerenciados por política com o valor de filtragem de compartilhamento/entrada** .  O comportamento de *abrir/compartilhar* no *aplicativo gerenciado por política* apresenta apenas outros *aplicativos gerenciados por política* como opções para compartilhamento. 

- **Dispositivos gerenciados por soluções de MDM**: para dispositivos registrados no Intune ou soluções de MDM de terceiros, o compartilhamento de dados entre aplicativos com políticas de proteção de aplicativo e outros aplicativos Ios gerenciados implantados por meio do MDM é controlado pelas políticas de aplicativo do Intune e pelo Ios **aberto no recurso de gerenciamento** . Para garantir que os aplicativos implantados usando uma solução de MDM também estejam associados às políticas de proteção de aplicativo do Intune, defina a configuração de UPN do usuário, conforme descrito na seção a seguir, [defina configuração de UPN do usuário](data-transfer-between-apps-manage-ios.md#configure-user-upn-setting-for-microsoft-intune-or-third-party-emm). Para especificar como você deseja permitir a transferência de dados para outros aplicativos, habilite **enviar dados da organização para outros aplicativos** e, em seguida, escolha o nível de compartilhamento preferencial. Para especificar como você deseja permitir que um aplicativo receba dados de outros aplicativos, habilite **receber dados de outros aplicativos** e, em seguida, escolha o nível preferencial de recebimento de dados. Para obter mais informações sobre a receção e partilha de dados de aplicações, veja [Definições de reposicionamento de dados](app-protection-policy-settings-ios.md#data-protection).

## <a name="configure-user-upn-setting-for-microsoft-intune-or-third-party-emm"></a>Configurar a definição de UPN do utilizador para o Microsoft Intune ou EMM de terceiros
Definir a configuração de UPN do usuário é **necessário** para dispositivos que são gerenciados pelo Intune ou uma solução do EMM de terceiros para identificar a conta de usuário registrado. A configuração de UPN funciona com as políticas de proteção de aplicativo que você implanta do Intune. O procedimento a seguir é um fluxo geral sobre como definir a configuração de UPN e a experiência do usuário resultante:

1. No [portal do Azure](https://portal.azure.com), [crie e atribua uma política de proteção de aplicações](app-protection-policies.md) para dispositivos iOS. Configure definições de política em conformidade com os requisitos da sua empresa e selecione as aplicações iOS que devem ter esta política.

2. Implante os aplicativos e o perfil de email que você deseja gerenciar por meio do Intune ou sua solução de MDM de terceiros usando as seguintes etapas generalizadas. Essa experiência também é coberta pelo *exemplo 1*.

3. Implante o aplicativo com as seguintes definições de configuração de aplicativo para o dispositivo gerenciado:

      **chave** = IntuneMAMUPN, **valor** = <username@company.com>

      Exemplo: [‘IntuneMAMUPN’, ‘janellecraig@contoso.com’]
      
     > [!NOTE]
     > No Intune, o tipo de registro da política de configuração de aplicativo deve ser definido como **dispositivos gerenciados**.
     > Além disso, o aplicativo precisa ser instalado do Portal da Empresa do Intune (se definido como disponível) ou enviado por push conforme necessário para o dispositivo. 

4. Implemente a política **Gestão Open In** ao utilizar o Intune ou o seu fornecedor de MDM de terceiros nos dispositivos inscritos.


### <a name="example-1-admin-experience-in-intune-or-third-party-mdm-console"></a>Exemplo 1: experiência de administrador no Intune ou na consola de MDM de terceiros

1. Aceda à consola de administração do Intune ou do seu fornecedor de MDM de terceiros. Aceda à secção da consola na qual implementa as definições de configuração de aplicações para dispositivos iOS inscritos.

2. Na secção Configuração da Aplicação, introduza a definição seguinte:

   **chave** = IntuneMAMUPN, **valor** = <username@company.com>

   A sintaxe exata do par chave/valor pode diferir com base no seu fornecedor de MDM de terceiros. A tabela a seguir mostra exemplos de provedores de MDM de terceiros e os valores exatos que você deve inserir para o par chave/valor.

   |Fornecedor de MDM de terceiros| Chave de Configuração | Tipo de Valor | Valor de Configuração|
   | ------- | ---- | ---- | ---- |
   |Microsoft Intune| IntuneMAMUPN | Cadeia | {{UserPrincipalName}}|
   |VMware AirWatch| IntuneMAMUPN | Cadeia | {UserPrincipalName}|
   |MobileIron | IntuneMAMUPN | Cadeia | ${userUPN} **ou** ${userEmailAddress} |
   |Gerenciamento de ponto de extremidade Citrix | IntuneMAMUPN | Cadeia | $ {User. UserPrincipalName} |
   |Gestor de Dispositivos Móveis ManageEngine | IntuneMAMUPN | Cadeia | %upn% |

> [!NOTE]  
> Para o Outlook para iOS, se você implantar uma política de configuração de aplicativo de dispositivos gerenciados com a opção "usando o designer de configuração" e habilitar **Permitir somente contas corporativas ou de estudante**, a chave de configuração IntuneMAMUPN será configurada automaticamente em segundo plano para a política. Mais detalhes podem ser encontrados na seção de perguntas frequentes em [novo Outlook para IOS e experiência de política de configuração de aplicativo Android – configuração geral do aplicativo](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/New-Outlook-for-iOS-and-Android-App-Configuration-Policy/ba-p/370481). 


### <a name="example-2-end-user-experience"></a>Exemplo 2: experiência de utilizador final

*Compartilhamento de um* aplicativo gerenciado por política *para outros aplicativos com compartilhamento de so*

1. Um usuário abre o aplicativo Microsoft OneDrive em um dispositivo iOS registrado e entra em sua conta corporativa.  A conta que o usuário insere deve corresponder ao UPN da conta que você especificou nas definições de configuração do aplicativo Microsoft OneDrive.

2. Depois de entrar, suas configurações de aplicativo configuradas pelo administrador se aplicam à conta de usuário no Microsoft OneDrive.  Isso inclui a configuração de **enviar dados org para outros aplicativos** para os **aplicativos gerenciados por política com o valor de compartilhamento do sistema operacional** .

3. O usuário visualiza um arquivo de trabalho e tenta compartilhar por meio do Open-in para o aplicativo gerenciado do iOS.  

4. A transferência de dados é realizada com sucesso e os dados agora são protegidos pelo **Gerenciamento do Open-in** no aplicativo gerenciado do Ios.  O aplicativo do Intune não se aplica a aplicativos que não são *aplicativos gerenciados por política*.

*Compartilhamento de um* aplicativo gerenciado do IOS *para um* aplicativo gerenciado *por política com dados de entrada da organização*

1. Um usuário abre o email nativo em um dispositivo iOS registrado com um perfil de email gerenciado.  

1. O usuário abre um anexo de documento de trabalho do email nativo para o Microsoft Word.

1. Quando o aplicativo Word é iniciado, uma das duas experiências ocorre:
   1. Os dados são protegidos pelo aplicativo do Intune quando:
      - O usuário é conectado à sua conta corporativa que corresponde ao UPN da conta que você especificou nas definições de configuração do aplicativo Microsoft Word. 
      - As configurações do aplicativo configurado pelo administrador se aplicam à conta de usuário no Microsoft Word.  Isso inclui configurar a configuração **receber dados de outros aplicativos** para **todos os aplicativos com o valor de entrada de dados da organização** .
      - A transferência de dados é realizada com sucesso e o documento é marcado com a identidade de trabalho no aplicativo.  O aplicativo do Intune protege as ações do usuário para o documento.
   1. Os dados **não** são protegidos pelo aplicativo do Intune quando:
      - O usuário **não** está conectado à sua conta corporativa.
      - As configurações definidas pelo administrador **não** são aplicadas ao Microsoft Word porque o usuário não está conectado.
      - A transferência de dados é realizada com sucesso e o documento **não** é marcado com a identidade de trabalho no aplicativo.  O aplicativo do Intune **não** protege as ações do usuário para o documento porque ele não está ativo.

    > [!NOTE]
    > O usuário pode adicionar e usar suas contas pessoais com o Word. As políticas de proteção de aplicativo não se aplicam quando o usuário usa o Word fora de um contexto de trabalho. 

### <a name="validate-user-upn-setting-for-third-party-emm"></a>Validar a definição de UPN de utilizador para EMM de terceiros

Depois de definir a configuração de UPN do usuário, valide a capacidade do aplicativo iOS de receber e obedecer à política de proteção de aplicativo do Intune.

Por exemplo, a configuração exigir política de **PIN do aplicativo** é fácil de testar. Quando a configuração de política for igual a **exigir**, o usuário deverá ver um prompt para definir ou inserir um PIN antes que possa acessar os dados da empresa.

Em primeiro lugar, [crie e atribua uma política de proteção de aplicações](app-protection-policies.md) à aplicação iOS. Para obter mais informações sobre como testar a política de proteção do aplicativo, consulte [validar políticas de proteção do aplicativo](app-protection-policies-validate.md).


## <a name="see-also"></a>Consulte também
[O que é uma política de proteção de aplicações do Intune](app-protection-policy.md)
