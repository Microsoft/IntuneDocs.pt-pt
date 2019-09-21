---
title: Guia de testes do SDK do Microsoft Intune app para desenvolvedores do Android
description: O guia de teste do SDK do Microsoft Intune app para Android ajuda você a testar seu aplicativo Android gerenciado pelo Intune.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 07/09/2019
ms.topic: reference
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 4ef8f421-9610-4d34-a464-cc02eb1578a9
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: ''
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91b7fc7414c3a6d6517cd4b704cb5e99ddcf96d0
ms.sourcegitcommit: 1494ff4b33c13a87f20e0f3315da79a3567db96e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71167181"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Guia de testes do SDK do Microsoft Intune app para desenvolvedores Android

O guia de teste do SDK do Microsoft Intune app para Android foi projetado para ajudá-lo a testar seu aplicativo Android gerenciado pelo Intune.  

## <a name="prerequisite-test-accounts"></a>Contas de teste de pré-requisitos
Novas contas podem ser criadas com e sem dados gerados previamente. Para criar uma nova conta:
1. Navegue até o site de [demonstrações da Microsoft](https://demos.microsoft.com/environments/create/tenant) . 
2. [Configure o Intune](setup-steps.md) para habilitar o MDM (gerenciamento de dispositivo móvel).
3. [Criar usuários](users-add.md).
4. [Criar grupos](groups-add.md).
5. [Atribua licenças](licenses-assign.md) conforme apropriado para seu teste.


## <a name="azure-portal-policy-configuration"></a>Configuração de política de portal do Azure
[Criar e atribuir políticas de proteção de aplicativo](app-protection-policies.md) na [folha do Intune do portal do Azure](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). Sua [política de configuração de aplicativo](app-configuration-policies-overview.md) também pode ser criada e atribuída na folha do Intune.

> [!NOTE]
> Se seu aplicativo não estiver listado no portal do Azure, você poderá direcioná-lo com uma política selecionando a opção **mais aplicativos** e fornecendo o nome do pacote na caixa de texto.

> [!IMPORTANT]
> Para que uma política de configuração de aplicativo seja aplicada, o usuário de registro deve ser direcionado por uma [política de proteção de aplicativo do Intune](app-protection-policy.md).

## <a name="test-cases"></a>Casos de teste

Os casos de teste a seguir fornecem etapas de configuração e confirmação. Use estas diretrizes para ajudar a solucionar problemas de aplicativos Android gerenciados pelo Intune.

### <a name="required-pin-and-corporate-credentials"></a>PIN necessário e credenciais corporativas

Você pode exigir um PIN para acessar recursos corporativos. Além disso, você pode impor a autenticação corporativa antes que os usuários possam usar aplicativos gerenciados. Use as etapas a seguir para definir esses requisitos:

1. Configure **exigir PIN para acesso** e **exigir credenciais corporativas para acesso** a **Sim**. Para obter mais informações, consulte [configurações de política de proteção de aplicativo Android em Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Confirme as seguintes condições:
    - A inicialização do aplicativo deve apresentar um prompt de PIN de entrada/configuração e/ou o usuário de produção que foi usado durante o registro com o Portal da Empresa.
    - A falha em apresentar uma solicitação de entrada válida pode ser devido a um manifesto do Android configurado incorretamente, especificamente os valores para integração de ADAL (O skipbroker, ClientID e autoridade).
    - Falha ao apresentar qualquer prompt pode ser devido a um valor incorretamente integrado `MAMActivity` . Para obter mais informações `MAMActivity`sobre o, consulte [Microsoft Intune app SDK for Android Developer Guide](app-sdk-android.md).

> [!NOTE] 
> Se o teste acima não estiver funcionando, os testes a seguir provavelmente também falharão. Examine a integração do [SDK](app-sdk-android.md##sdk-integration) e da [Adal](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) .

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Restringir a transferência e o recebimento de dados com outros aplicativos
Você pode controlar a transferência de dados entre aplicativos gerenciados corporativos da seguinte maneira:

1. Defina **permitir que o aplicativo transfira dados para outros aplicativos** para **aplicativos gerenciados por política**.
2. Defina **permitir que o aplicativo receba dados de outros aplicativos** para **todos os aplicativos**. O uso de tentativas e provedores de conteúdo será afetado por essas políticas.
3. Confirme as seguintes condições:
    - A abertura de um aplicativo não gerenciado para seu aplicativo funciona corretamente.
    - O compartilhamento de conteúdo entre aplicativos gerenciados é permitido.
    - O compartilhamento de aplicativos gerenciados para aplicativos não gerenciados (por exemplo, Chrome) é bloqueado.

### <a name="restrict-cut-copy-and-paste"></a>Restringir recortar, copiar e colar
Você pode restringir a área de transferência do sistema a aplicativos gerenciados da seguinte maneira:

1. Defina **restringir recortar, copiar e colar com outros aplicativos** para **política gerenciada com colar em**.
2. Confirme as seguintes condições:
    - A cópia de texto do seu aplicativo para um aplicativo não gerenciado (por exemplo, mensagens) é bloqueada.

### <a name="prevent-save-as"></a>Impedir **salvar como**
Você pode controlar **salvar como** funcionalidade da seguinte maneira:

1. Se seu aplicativo exigir [controles ' salvar como ' integrados](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted), defina **evitar ' salvar como '** como **Sim**.
2. Confirme as seguintes condições:
    - Save é restrito a apenas locais gerenciados apropriados.

### <a name="file-encryption"></a>Criptografia de arquivo
Você pode criptografar dados no dispositivo da seguinte maneira:

1. Defina **criptografar dados do aplicativo** como **Sim**.
2. Confirme as seguintes condições:
    - O comportamento normal do aplicativo não é afetado.

### <a name="prevent-android-backups"></a>Impedir backups do Android
Você pode controlar o backup do aplicativo da seguinte maneira:

1. Se você tiver definido [restrições de backup integradas](app-sdk-android.md#protecting-backup-data), configure **impedir backups do Android** como **Sim**.
2. Confirme as seguintes condições:
    - Os backups são restritos.

### <a name="unenrollment"></a>Cancelamento
Você pode apagar remotamente os aplicativos gerenciados de contendo emails e documentos corporativos, e os dados pessoais são descriptografados quando não são mais administrados da seguinte maneira:

1. No portal do Azure, [emita um apagamento](apps-selective-wipe.md).
2. Se seu aplicativo não se registrar para nenhum manipulador de apagamento, confirme as seguintes condições:
    - Ocorre um apagamento completo do aplicativo.
3. Se seu aplicativo tiver se registrado `WIPE_USER_DATA` para `WIPE_USER_AUXILARY_DATA`o ou, confirme as seguintes condições:
    - O conteúdo gerenciado é removido do aplicativo. Para obter mais informações, consulte [Guia do desenvolvedor do SDK de aplicativos do Intune para Android – apagamento seletivo](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Identidades Múltiplas
A integração de [suporte a várias identidades](app-sdk-android.md#multi-identity-optional) é uma alteração de alto risco que precisa ser exaustivamente testada. Os problemas mais comuns serão devido à configuração inadequada da identidade (contexto versus nível de ameaça) e também ao controle de arquivos`MAMFileProtectionManager`().

O mínimo dos cenários a seguir para várias identidades deve ser revalidado:

- A política **salvar como** está funcionando corretamente para identidades gerenciadas.
- As restrições de colagem de cópia são impostas corretamente de gerenciado para pessoal.
- Somente os dados pertencentes à identidade gerenciada são criptografados e os arquivos pessoais não são modificados.
- O apagamento seletivo durante o cancelamento do registro remove apenas os dados de identidade gerenciados.
- O usuário final será solicitado a fornecer uma inicialização condicional ao mudar da conta não gerenciada para a gerenciada (somente na primeira vez).

### <a name="app-configuration-optional"></a>Configuração do aplicativo (opcional)
Você pode configurar o comportamento de aplicativos gerenciados da seguinte maneira:

1. Se seu aplicativo consumir quaisquer definições de configuração de aplicativo, você deverá testar se seu aplicativo manipula corretamente todos os valores que você (como o administrador) pode definir. [As políticas de configuração de aplicativo](app-configuration-policies-overview.md) podem ser criadas e atribuídas usando o Intune.

## <a name="next-steps"></a>Passos seguintes

- [Adicione um aplicativo de linha de negócios Android a Microsoft Intune](lob-apps-android.md).
