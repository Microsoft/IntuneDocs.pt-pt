---
title: Microsoft Intune App SDK para o guia de teste de programação do Android
description: O Microsoft Intune App SDK para o guia de teste Android ajuda a testar seu aplicativo Android geridos pelo Intune.
keywords: SDK
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/14/2019
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
ms.openlocfilehash: 9f8fa8f361e886c8eac697bb585ccf15eb9152f1
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66043846"
---
# <a name="microsoft-intune-app-sdk-for-android-developers-testing-guide"></a>Microsoft Intune App SDK para programadores Android guia de teste

O Microsoft Intune App SDK para o guia de teste Android foi concebido para ajudar a testar a sua aplicação Android gerida pelo Intune.  

## <a name="prerequisite-test-accounts"></a>Contas de teste de pré-requisito
Podem ser criadas novas contas com e sem dados previamente gerados. Para criar uma nova conta:
1. Navegue para o [Microsoft Demos](https://demos.microsoft.com/environments/create/tenant) site. 
2. [Configurar o Intune](https://docs.microsoft.com/intune/setup-steps) para ativar a gestão de dispositivos móveis (MDM).
3. [Criar utilizadores](https://docs.microsoft.com/intune/users-add).
4. [Criar grupos](https://docs.microsoft.com/intune/groups-add).
5. [Atribuir licenças](https://docs.microsoft.com/intune/licenses-assign) conforme adequado para o seu teste.


## <a name="azure-portal-policy-configuration"></a>Configuração de política de portal do Azure
[Criar e atribuir políticas de proteção de aplicações](https://docs.microsoft.com/intune/app-protection-policies) no [painel do Intune do portal do Azure](https://portal.azure.com/?feature.customportal=false#blade/Microsoft_Intune_Apps/MainMenu/14/selectedMenuItem/Overview). Sua [política de configuração de aplicação](https://docs.microsoft.com/intune/app-configuration-policies-overview) também podem ser criados e atribuídos no painel do Intune.

> [!NOTE]
> Se a aplicação não estiver listada no portal do Azure, pode segmentá-la com uma política ao selecionar o **mais aplicações** opção e fornecer o nome do pacote na caixa de texto.

> [!IMPORTANT]
> Para uma política de configuração de aplicações aplicar, o utilizador de inscrição tem de ser visado por uma [política de proteção de aplicações do Intune](https://docs.microsoft.com/intune/app-protection-policy).

## <a name="test-cases"></a>Casos de teste

Os casos de teste seguintes fornecem passos de configuração e a confirmação. Use essa orientação para ajudar a resolver problemas de aplicação Android gerida pelo Intune.

### <a name="required-pin-and-corporate-credentials"></a>Exigir PIN e de credenciais da empresa

Pode exigir um pin para aceder a recursos da empresa. Além disso, pode impor autenticação empresarial antes dos utilizadores podem utilizar aplicações geridas. Utilize os seguintes passos para definir estes requisitos:

1. Configurar **exigir PIN para acesso** e **requerer credenciais empresariais de acesso** para **Sim**. Para obter mais informações, consulte [definições de política de proteção de aplicações Android no Microsoft Intune](app-protection-policy-settings-android.md#access-requirements).
2. Confirme as seguintes condições:
    - Iniciação da aplicação deve apresentar uma linha de comandos de entrada/configuração de PIN e/ou o utilizador de produção que foi utilizado durante a inscrição com o Portal da empresa.
    - Falha ao apresentar um pedido de início de sessão válido pode ser devido a um manifesto android configurado incorretamente, especificamente os valores para a integração da ADAL (SkipBroker, ID de cliente e autoridade).
    - Falha de apresentar qualquer linha de comandos pode ser devido a um incorretamente integrada `MAMActivity` valor. Para obter mais informações sobre `MAMActivity`, consulte [Microsoft Intune App SDK para o guia de programação do Android](app-sdk-android.md).

> [!NOTE] 
> Se o teste acima não está a funcionar, os testes abaixo provavelmente também falhará. Revisão [SDK](app-sdk-android.md##sdk-integration) e [ADAL](app-sdk-android.md#configure-azure-active-directory-authentication-library-adal) integração.

### <a name="restrict-transferring-and-receiving-data-with-other-apps"></a>Restringir a transferência e a receção de dados com outras aplicações
Pode controlar a transferência de dados entre aplicações geridas empresariais da seguinte forma:

1. Definir **permitir que a aplicação transfira dados para outras aplicações** ao **aplicações geridas por políticas**.
2. Definir **permitir que a aplicação receba dados de outras aplicações** ao **todas as aplicações**. Utilização de objetivos e provedores de conteúdo será afetada por estas políticas.
3. Confirme as seguintes condições:
    - Abrir a partir de uma aplicação não gerida para as suas funções de aplicação corretamente.
    - É permitida a partilha de conteúdo entre aplicações geridas.
    - É bloqueada a partilha de aplicações geridas para aplicações não geridos (por exemplo, o Chrome).

### <a name="restrict-cut-copy-and-paste"></a>Restringir cortar, copiar e colar
Pode restringir a área de transferência do sistema às aplicações geridas da seguinte forma:

1. Definir **restringir operações cortar, copiar e colar com outras aplicações** ao **geridas por políticas com colar em**.
2. Confirme as seguintes condições:
    - Copie o texto da sua aplicação para uma gerida está bloqueada a aplicação não gerida (por exemplo, mensagens).

### <a name="prevent-save-as"></a>Impedir **guardar como**
Pode controlar **guardar como** funcionalidade da seguinte forma:

1. Se a sua aplicação necessita [integrada "Guardar como" controles](app-sdk-android.md#example-determine-if-saving-to-device-or-cloud-storage-is-permitted), defina **impedir "Guardar como"** para **Sim**.
2. Confirme as seguintes condições:
    - Guardar está restringido a apenas as localizações gerenciadas apropriadas.

### <a name="file-encryption"></a>Encriptação de ficheiros
Pode criptografar dados no dispositivo da seguinte forma:

1. Definir **encriptar dados da aplicação** ao **Sim**.
2. Confirme as seguintes condições:
    - O comportamento do aplicativo normal não é afetado.

### <a name="prevent-android-backups"></a>Impedir cópias de segurança Android
Pode controlar a cópia de segurança de aplicação da seguinte forma:

1. Se tiver definido [integrado restrições de cópia de segurança](app-sdk-android.md#protecting-backup-data), configure **cópias de segurança Android impedir** para **Sim**.
2. Confirme as seguintes condições:
    - As cópias de segurança são restritas.

### <a name="unenrollment"></a>Anulação da inscrição
Pode apagar remotamente aplicações geridas do que contém os documentos e e-mails empresariais e dados pessoais são desencriptados quando já não é administrado da seguinte forma:

1. No portal do Azure, [emitir uma eliminação](https://docs.microsoft.com/intune/apps-selective-wipe).
2. Se a sua aplicação não os registra para qualquer manipuladores de eliminação confirme as seguintes condições:
    - Ocorre uma eliminação completa da aplicação.
3. Se seu aplicativo registrou `WIPE_USER_DATA` ou `WIPE_USER_AUXILARY_DATA`, confirme as seguintes condições:
    - O conteúdo gerido é removido da aplicação. Para obter mais informações, consulte [SDK da aplicação Intune para o guia de programação do Android – eliminação seletiva](app-sdk-android.md#selective-wipe).

### <a name="multi-identity"></a>Identidades Múltiplas
Integrando [suporte de identidades múltiplas](app-sdk-android.md#multi-identity-optional) é uma alteração de alto risco, que tem de ser totalmente testados. Os problemas mais comuns serão devidos à definição incorreta da identidade (contexto vs. o nível de ameaça) e também os arquivos de controle (`MAMFileProtectionManager`).

No mínimo, os seguintes cenários de várias identidades devem possível revalidar:

- **Guardar como** política está a funcionar corretamente para identidades geridas.
- Copie colar restrições são impostas corretamente a partir de gerido para o pessoal.
- Apenas os dados pertencentes à identidade gerida são encriptados e arquivos pessoais não são modificados.
- A eliminação seletiva durante a anulação da inscrição apenas remove os dados de identidade gerida.
- O utilizador final é solicitado iniciação condicional quando a alteração de não-gerenciado para a conta gerenciada (apenas na primeira vez).

### <a name="app-configuration-optional"></a>Configuração de aplicações (opcional)
Pode configurar o comportamento de aplicações geridas da seguinte forma:

1. Se seu aplicativo consome as definições de configuração de aplicação, deve testar que o seu aplicativo manipula corretamente todos os valores (como administrador) pode definir. [Políticas de configuração de aplicação](https://docs.microsoft.com/intune/app-configuration-policies-overview) podem ser criados e atribuídos com o Intune.

## <a name="next-steps"></a>Passos Seguintes

- [Adicionar uma aplicação de linha de negócio Android ao Microsoft Intune](lob-apps-android.md).
