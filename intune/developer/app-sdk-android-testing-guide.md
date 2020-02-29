---
title: Microsoft Intune App SDK para guia de testes Android
description: O Microsoft Intune App SDK para o guia de testes Android ajuda-o a testar a sua aplicação Android gerida por Intune.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/02/2020
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
ms.openlocfilehash: 699665f93d04801223f2fc6e6536d9b675e75242
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181947"
---
# <a name="microsoft-intune-app-sdk-for-android-testing-guide"></a>Microsoft Intune App SDK para guia de testes Android

Este guia ajuda os desenvolvedores a testar as suas aplicações Android geridas por Intune.  

## <a name="prerequisite-test-accounts"></a>Contas de teste pré-requisitos
Pode criar novas contas com ou sem dados pré-gerados. Para criar uma nova conta:
1. Vá ao site da [Microsoft Demos.](https://demos.microsoft.com/environments/create/tenant) 
2. [Configurar intune](../fundamentals/setup-steps.md) para permitir a gestão de dispositivos móveis (MDM).
3. [Criar utilizadores](../fundamentals/users-add.md).
4. [Criar grupos](../fundamentals/groups-add.md).
5. [Atribua licenças](../fundamentals/licenses-assign.md) conforme apropriado para os seus testes.


## <a name="azure-portal-policy-configuration"></a>Configuração da política do portal Azure
[Crie e atribua políticas](../apps/app-protection-policies.md) de proteção de aplicações na [lâmina Intune do portal Azure](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). Também pode criar e atribuir a sua política de configuração de [aplicações](../apps/app-configuration-policies-overview.md) na lâmina Intune.

> [!NOTE]
> Se a sua aplicação não estiver listada no portal Azure, pode direcioná-la com uma política selecionando a opção **mais apps** e fornecendo o nome do pacote na caixa de texto.

## <a name="test-cases"></a>Casos de teste

Os seguintes casos de teste fornecem etapas de configuração e confirmação. Use esta orientação para ajudar a resolver problemas com problemas de aplicativos Android geridos pela Intune.

### <a name="required-pin-and-corporate-credentials"></a>PIN exigido e credenciais corporativas

Pode exigir um PIN para aceder aos recursos corporativos. Além disso, pode impor a autenticação corporativa antes que os utilizadores possam utilizar aplicações geridas. Eis como:

1. Definir **Exigir PIN para acesso** e exigir **credenciais corporativas para acesso** a **Sim**. Para mais informações, consulte as definições de política de proteção de [aplicações Android no Microsoft Intune](../apps/app-protection-policy-settings-android.md#access-requirements).
2. Confirme as seguintes condições:
    - O lançamento da aplicação deve apresentar um aviso para a entrada de PIN, ou para o utilizador de produção que foi utilizado durante a inscrição no Portal da Empresa.
    - A não apresentação de um pedido de entrada válido pode dever-se a um manifesto Android configurado incorretamente, especificamente os valores para a integração da Azure Ative Directory Authentication Library (ADAL) (SkipBroker, ClientID e Authority).
    - A não apresentação de qualquer pedido pode dever-se a um valor `MAMActivity` incorretamente integrado. Para mais informações sobre `MAMActivity`, consulte [microsoft Intune App SDK para guia](app-sdk-android.md)de desenvolvedores Android .

> [!NOTE] 
> Se o teste anterior não estiver a funcionar, os seguintes testes provavelmente também falharão. Rever a integração [de SDK](app-sdk-android.md#sdk-integration) e [ADAL.](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal)

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Restringir a transferência e receção de dados com outras aplicações
Pode controlar a transferência de dados entre aplicações geridas por empresas, da seguinte forma:

1. Definir **Permitir que a aplicação transfira dados para outras aplicações** para **aplicações geridas por políticas.**
2. Definir **Permitir que a aplicação receba dados de outras aplicações** para todas as **aplicações.** A utilização de intençãos e fornecedores de conteúdos é afetada por estas políticas.
3. Confirme as seguintes condições:
    - Abrindo de uma aplicação não gerida para as suas funções de aplicação corretamente.
    - É permitida a partilha de conteúdos entre aplicações geridas.
    - A partilha de aplicações geridas para aplicações não geridas (por exemplo, o Chrome) está bloqueada.

### <a name="restrict-cut-copy-and-paste"></a>Restringir corte, cópia e pasta
Pode restringir a área de recortão do sistema a aplicações geridas, da seguinte forma:

1. Definir **Restringir corte, cópia e colar com outras aplicações** para **Política gerida com pasta em**.
2. Confirme as seguintes condições:
    - A cópia do texto da sua aplicação para uma aplicação não gerida (por exemplo, Mensagens) está bloqueada.

### <a name="prevent-save"></a>Evitar a salvação
Pode controlar a funcionalidade **Save As,** da seguinte forma:

1. Se a sua aplicação necessitar de [controlos integrados Save As](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted), demodote **'Save As'** to **Yes**.
2. Confirme as seguintes condições:
    - A poupança limita-se apenas a locais geridos apropriados.

### <a name="file-encryption"></a>Encriptação de ficheiros
Pode encriptar dados no dispositivo da seguinte forma:

1. **Detete os dados da aplicação para** **Sim**.
2. Confirme as seguintes condições:
    - O comportamento normal da aplicação não é afetado.

### <a name="prevent-android-backups"></a>Impedir cópias de segurança Android
Pode controlar a cópia de segurança da aplicação, da seguinte forma:

1. Se tiver definido [restrições de backup integradas,](app-sdk-android.md#protecting-backup-data)delicie-se **com as cópias** de segurança do Android para **Sim**.
2. Confirme as seguintes condições:
    - Os reforços são restritos.

### <a name="unenrollment"></a>Não inscrição
Pode limpar remotamente as aplicações geridas de conter e-mails e documentos corporativos, e os dados pessoais são desencriptados quando já não são administrados. Eis como:

1. Do portal Azure, [emita uma limpeza.](../apps/apps-selective-wipe.md)
2. Se a sua aplicação não se registar para quaisquer manipuladores de limpeza, confirme as seguintes condições:
    - Ocorre uma limpeza completa da aplicação.
3. Se a sua aplicação tiver registado para `WIPE_USER_DATA` ou `WIPE_USER_AUXILARY_DATA`, confirme as seguintes condições:
    - O conteúdo gerido é removido da aplicação. Para mais informações, consulte [Intune App SDK para guia](app-sdk-android.md#selective-wipe)de desenvolvedores Android - limpeza seletiva .

### <a name="multi-identity-support"></a>Suporte de identidades múltiplas
Integrar o [apoio multi-identidade](app-sdk-android.md#multi-identity-optional) é uma mudança de alto risco que precisa de ser testada de forma completa. As questões mais comuns ocorrem devido à definição indevida da identidade (contexto vs. nível de ameaça) e de ficheiros de rastreio (`MAMFileProtectionManager`).

Minimamente, confirme que:

- **Save As** a política está a funcionar corretamente para identidades geridas.
- As restrições de cópia e pasta são corretamente aplicadas de geridas para pessoais.
- Apenas os dados pertencentes à identidade gerida são encriptados e os ficheiros pessoais não são modificados.
- A limpeza seletiva durante a não inscrição remove apenas os dados de identidade geridos.
- O utilizador é solicitado para o lançamento condicional ao mudar de uma conta não gerida para uma conta gerida (apenas pela primeira vez).

### <a name="app-configuration-optional"></a>Configuração de aplicativos (opcional)
Pode configurar o comportamento de aplicações geridas. Se a sua aplicação consumir quaisquer configurações de configuração da aplicação, deve testar que a sua aplicação lida corretamente com todos os valores que você (como administrador) pode definir. Pode criar e atribuir políticas de configuração de [aplicações](../apps/app-configuration-policies-overview.md) no Intune.

## <a name="next-steps"></a>Próximos passos

- [Adicione uma aplicação de linha de negócios Android ao Microsoft Intune](../apps/lob-apps-android.md)
