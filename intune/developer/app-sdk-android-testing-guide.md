---
title: Guia de testes do SDK do Microsoft Intune app para Android
description: O guia de teste do SDK do Microsoft Intune app para Android ajuda você a testar seu aplicativo Android gerenciado pelo Intune.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: developer
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9eada01f2b1e876d6d3b47140c671e3ff7eeab02
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503504"
---
# <a name="microsoft-intune-app-sdk-for-android-testing-guide"></a>Guia de testes do SDK do Microsoft Intune app para Android

Este guia ajuda os desenvolvedores a testar seus aplicativos Android gerenciados pelo Intune.  

## <a name="prerequisite-test-accounts"></a>Contas de teste de pré-requisitos
Você pode criar novas contas com ou sem dados gerados previamente. Para criar uma nova conta:
1. Vá para o site de [demonstrações da Microsoft](https://demos.microsoft.com/environments/create/tenant) . 
2. [Configure o Intune](../fundamentals/setup-steps.md) para habilitar o MDM (gerenciamento de dispositivo móvel).
3. [Criar usuários](../fundamentals/users-add.md).
4. [Criar grupos](../fundamentals/groups-add.md).
5. [Atribua licenças](../fundamentals/licenses-assign.md) conforme apropriado para seu teste.


## <a name="azure-portal-policy-configuration"></a>Configuração de política de portal do Azure
[Criar e atribuir políticas de proteção de aplicativo](../apps/app-protection-policies.md) na [folha do Intune do portal do Azure](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). Você também pode criar e atribuir sua [política de configuração de aplicativo](../apps/app-configuration-policies-overview.md) na folha do Intune.

> [!NOTE]
> Se seu aplicativo não estiver listado no portal do Azure, você poderá direcioná-lo com uma política selecionando a opção **mais aplicativos** e fornecendo o nome do pacote na caixa de texto.

## <a name="test-cases"></a>Casos de teste

Os casos de teste a seguir fornecem etapas de configuração e confirmação. Use estas diretrizes para ajudar a solucionar problemas de aplicativos Android gerenciados pelo Intune.

### <a name="required-pin-and-corporate-credentials"></a>PIN necessário e credenciais corporativas

Você pode exigir um PIN para acessar recursos corporativos. Além disso, você pode impor a autenticação corporativa antes que os usuários possam usar aplicativos gerenciados. Eis como:

1. Defina **exigir PIN para acesso** e **exigir credenciais corporativas para acesso** a **Sim**. Para obter mais informações, consulte [configurações de política de proteção de aplicativo Android em Microsoft Intune](../apps/app-protection-policy-settings-android.md#access-requirements).
2. Confirme as seguintes condições:
    - A inicialização do aplicativo deve apresentar um prompt de entrada de PIN ou o usuário de produção que foi usado durante o registro com o Portal da Empresa.
    - A falha em apresentar uma solicitação de entrada válida pode ser devido a um manifesto do Android configurado incorretamente, especificamente os valores para a integração da ADAL (O skipbroker Authentication Library) (Azure Active Directory a autenticação, a ClientID e a autoridade).
    - Falha ao apresentar qualquer prompt pode ser devido a um valor de `MAMActivity` incorretamente integrado. Para obter mais informações sobre `MAMActivity`, consulte [Microsoft INTUNE SDK de aplicativo para o guia do desenvolvedor do Android](app-sdk-android.md).

> [!NOTE] 
> Se o teste anterior não estiver funcionando, os testes a seguir provavelmente também falharão. Examine a integração do [SDK](app-sdk-android.md##sdk-integration) e da [Adal](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) .

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Restringir a transferência e o recebimento de dados com outros aplicativos
Você pode controlar a transferência de dados entre aplicativos gerenciados corporativos, da seguinte maneira:

1. Defina **permitir que o aplicativo transfira dados para outros aplicativos** para **aplicativos gerenciados por política**.
2. Defina **permitir que o aplicativo receba dados de outros aplicativos** para **todos os aplicativos**. O uso de tentativas e provedores de conteúdo são afetados por essas políticas.
3. Confirme as seguintes condições:
    - A abertura de um aplicativo não gerenciado para seu aplicativo funciona corretamente.
    - O compartilhamento de conteúdo entre aplicativos gerenciados é permitido.
    - O compartilhamento de aplicativos gerenciados para aplicativos não gerenciados (por exemplo, Chrome) é bloqueado.

### <a name="restrict-cut-copy-and-paste"></a>Restringir recortar, copiar e colar
Você pode restringir a área de transferência do sistema a aplicativos gerenciados da seguinte maneira:

1. Defina **restringir recortar, copiar e colar com outros aplicativos** para **política gerenciada com colar em**.
2. Confirme as seguintes condições:
    - A cópia de texto do seu aplicativo para um aplicativo não gerenciado (por exemplo, mensagens) é bloqueada.

### <a name="prevent-save"></a>Impedir salvamento
Você pode controlar **salvar como** funcionalidade, da seguinte maneira:

1. Se seu aplicativo exigir [controles de salvar como integrados](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted), defina **impedir ' salvar como '** como **Sim**.
2. Confirme as seguintes condições:
    - Save é restrito a apenas locais gerenciados apropriados.

### <a name="file-encryption"></a>Criptografia de arquivo
Você pode criptografar dados no dispositivo, da seguinte maneira:

1. Defina **criptografar dados do aplicativo** como **Sim**.
2. Confirme as seguintes condições:
    - O comportamento normal do aplicativo não é afetado.

### <a name="prevent-android-backups"></a>Impedir cópias de segurança Android
Você pode controlar o backup do aplicativo, da seguinte maneira:

1. Se você tiver definido [restrições de backup integradas](app-sdk-android.md#protecting-backup-data), defina **impedir backups do Android** como **Sim**.
2. Confirme as seguintes condições:
    - Os backups são restritos.

### <a name="unenrollment"></a>Cancelamento
Você pode apagar remotamente aplicativos gerenciados de contendo emails e documentos corporativos, e os dados pessoais são descriptografados quando não são mais administrados. Eis como:

1. No portal do Azure, [emita um apagamento](../apps/apps-selective-wipe.md).
2. Se seu aplicativo não se registrar para nenhum manipulador de apagamento, confirme as seguintes condições:
    - Ocorre um apagamento completo do aplicativo.
3. Se seu aplicativo tiver se registrado para `WIPE_USER_DATA` ou `WIPE_USER_AUXILARY_DATA`, confirme as seguintes condições:
    - O conteúdo gerenciado é removido do aplicativo. Para obter mais informações, consulte [Guia do desenvolvedor do SDK de aplicativos do Intune para Android – apagamento seletivo](app-sdk-android.md#selective-wipe).

### <a name="multi-identity-support"></a>Suporte de identidades múltiplas
A integração de [suporte a várias identidades](app-sdk-android.md#multi-identity-optional) é uma alteração de alto risco que precisa ser exaustivamente testada. Os problemas mais comuns ocorrem devido à configuração inadequada da identidade (contexto versus nível de ameaça) e aos arquivos de rastreamento (`MAMFileProtectionManager`).

No mínimo, confirme que:

- A política **salvar como** está funcionando corretamente para identidades gerenciadas.
- As restrições de cópia e colagem são impostas corretamente de gerenciado para pessoal.
- Somente os dados pertencentes à identidade gerenciada são criptografados e os arquivos pessoais não são modificados.
- O apagamento seletivo durante o cancelamento do registro remove apenas os dados de identidade gerenciados.
- O usuário receberá uma solicitação para a inicialização condicional ao mudar de uma conta não gerenciada para a gerenciada (somente na primeira vez).

### <a name="app-configuration-optional"></a>Configuração do aplicativo (opcional)
Você pode configurar o comportamento de aplicativos gerenciados. Se seu aplicativo consumir quaisquer definições de configuração de aplicativo, você deverá testar se seu aplicativo manipula corretamente todos os valores que você (como o administrador) pode definir. Você pode criar e atribuir [políticas de configuração de aplicativo](../apps/app-configuration-policies-overview.md) no Intune.

## <a name="next-steps"></a>Próximos passos

- [Adicionar um aplicativo de linha de negócios Android ao Microsoft Intune](../apps/lob-apps-android.md)
