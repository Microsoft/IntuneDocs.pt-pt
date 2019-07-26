---
title: Solucionando problemas de registro de dispositivo iOS no Microsoft Intune
titleSuffix: Microsoft Intune
description: Sugestões para solucionar alguns dos problemas mais comuns ao registrar dispositivos iOS no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/25/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c826d27079e365670ba47aa22d1dd8e5d42f4b21
ms.sourcegitcommit: 1d4aec7b79c70d35ec3fc29df6ff9c6a1403412e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/25/2019
ms.locfileid: "68496375"
---
# <a name="troubleshoot-ios-device-enrollment-problems-in-microsoft-intune"></a>Solucionar problemas de registro de dispositivo iOS no Microsoft Intune

Este artigo ajuda os administradores do Intune a entender e solucionar problemas ao registrar dispositivos iOS no Intune.

## <a name="prerequisites"></a>Pré-requisitos
Antes de iniciar a solução de problemas, é importante coletar algumas informações básicas. Essas informações podem ajudá-lo a entender melhor o problema e reduzir o tempo para encontrar uma resolução.

Colete as seguintes informações sobre o problema:
- Qual é a mensagem de erro exata?
- Onde você vê a mensagem de erro?
- Quando o problema foi iniciado? O registro já funcionou? 
- Qual plataforma (Android, iOS, Windows) tem o problema?
- Quantos usuários são afetados? Todos os usuários foram afetados ou apenas alguns?
- Quantos dispositivos são afetados? Todos os dispositivos foram afetados ou apenas alguns?
- O que é a autoridade de MDM? Se for System Center Configuration Manager, qual versão do Configuration Manager você está usando?
- Como o registro está sendo executado? Ele é "Traga seu próprio dispositivo" (BYOD) ou DEP (Programa de registro de dispositivos da Apple) com perfis de registro?

## <a name="error-messages"></a>Mensagens de erro

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Falha na instalação do perfil. Ocorreu um erro de rede.

**Faz** Há um problema não especificado com o iOS no dispositivo.

#### <a name="resolution"></a>Resolução
1. Para evitar a perda de dados nas etapas a seguir (a restauração do iOS exclui todos os dados no dispositivo), certifique-se de fazer backup dos dados.
2. Coloque o dispositivo no modo de recuperação e restaure-o. Certifique-se de configurá-lo como um novo dispositivo. Para obter mais informações sobre como restaurar dispositivos iOS, consulte [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Registre novamente o dispositivo.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Falha na instalação do perfil. Não foi possível estabelecer a conexão com o servidor.

**Faz** Seu locatário do Intune está configurado para permitir somente dispositivos de propriedade corporativa. 

#### <a name="resolution"></a>Resolução
1. Inicie sessão no Portal do Azure.
2. Selecione **mais serviços**, pesquise Intune e, em seguida, selecione **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. Em **restrições de tipo de dispositivo**, selecione a restrição que você deseja definir > **Propriedades** > **Selecionar plataformas** > selecione **permitir** para **Ios**e clique em **OK**.
5. Selecione **Configurar plataformas**, selecione **permitir** dispositivos IOS de propriedade pessoal e clique em **OK**.
6. Registre novamente o dispositivo.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Não há suporte para esse serviço. Nenhuma política de registro.

**Causa**: Um certificado de push do MDM da Apple não está configurado no Intune ou o certificado é inválido. 

#### <a name="resolution"></a>Resolução

- Se o MDM Push Certificate não estiver configurado, siga as etapas em [obter um Apple MDM Push Certificate](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate).
- Se o MDM Push Certificate for inválido, siga as etapas em [renovar Apple MDM Push Certificate](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Portal da Empresa temporariamente indisponível. O aplicativo Portal da Empresa encontrou um problema. Se o problema persistir, contate o administrador do sistema.

**Faz** O aplicativo Portal da Empresa está desatualizado ou corrompido.

#### <a name="resolution"></a>Resolução
1. Remova o aplicativo Portal da Empresa do dispositivo.
2. Baixe e instale o aplicativo **Microsoft Intune portal da empresa** da **loja de aplicativos**.
3. Registre novamente o dispositivo.

### <a name="device-cap-reached"></a>Limite do dispositivo atingido

**Faz** O usuário tenta registrar mais dispositivos do que o limite de registro do dispositivo.

#### <a name="resolution"></a>Resolução
1. Abra o [portal](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview) > deadministraçãodo Intune**todos os dispositivos**e verifique o número de dispositivos que o usuário registrou. > 
    > [!NOTE]
    > Você também deve ter o logon do usuário afetado no [portal do usuário do Intune](https://portal.manage.microsoft.com/) e verificar os dispositivos que foram registrados. Pode haver dispositivos que aparecem no portal do [usuário do Intune](https://portal.manage.microsoft.com/) , mas não no [portal de administração do Intune](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview), tais dispositivos também contam para o limite de registro do dispositivo.
2. Vá para **administrador** > **Gerenciamento** > de dispositivo móvel**regras de registro** > verificar o limite de registro do dispositivo. Por padrão, o limite é definido como 15. 
3. Se o número de dispositivos registrados tiver atingido o limite, remova os dispositivos desnecessários ou aumente o limite de registro do dispositivo. Como cada dispositivo registrado consome uma licença do Intune, recomendamos que você sempre remova dispositivos desnecessários primeiro.
4. Registre novamente o dispositivo.

### <a name="workplace-join-failed"></a>Falha na Workplace Join

**Faz** O aplicativo Portal da Empresa está desatualizado ou corrompido.  

#### <a name="resolution"></a>Resolução
1. Remova o aplicativo Portal da Empresa do dispositivo.
2. Baixe e instale o aplicativo **Microsoft Intune portal da empresa** da **loja de aplicativos**.
3. Registre novamente o dispositivo.

### <a name="user-license-type-invalid"></a>Tipo de licença de usuário inválido

**Faz** O usuário que está tentando registrar o dispositivo não tem uma licença do Intune válida.

#### <a name="resolution"></a>Resolução
1. Vá para o [centro de administração do Microsoft 365](https://portal.office.com/adminportal/home#/homepage)e, em seguida, escolha **usuários** > usuários**ativos**.
2. Selecione a conta de usuário afetada > **licenças** > de produto**Editar**.
3. Verifique se uma licença válida do Intune está atribuída a este usuário.
4. Registre novamente o dispositivo.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Nome de usuário não reconhecido. Esta conta de usuário não está autorizada a usar Microsoft Intune. Contate o administrador do sistema se você considerar que recebeu esta mensagem por erro.

**Faz** O usuário que está tentando registrar o dispositivo não tem uma licença do Intune válida.

1. Vá para o [centro de administração do Microsoft 365](https://portal.office.com/adminportal/home#/homepage)e, em seguida, escolha **usuários** > usuários**ativos**.
2. Selecione a conta de usuário afetada e escolha **licenças** > de produto**Editar**.
3. Verifique se uma licença válida do Intune está atribuída a este usuário.
4. Registre novamente o dispositivo.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Falha na instalação do perfil. A nova carga de MDM não corresponde à carga antiga.

**Faz** Um perfil de gerenciamento já está instalado no dispositivo.

#### <a name="resolution"></a>Resolução

1. Abra **as configurações** no dispositivo IOS >**Gerenciamento de dispositivo** **geral** > .
2. Toque no perfil de gerenciamento existente e toque em **remover gerenciamento**.
3. Registre novamente o dispositivo.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Faz** O certificado do Apple Push Notification Service (APNs) está ausente, inválido ou expirou.

#### <a name="resolution"></a>Resolução
Verifique se um certificado APNs válido foi adicionado ao Intune. Para obter mais informações, consulte [Configurar o gerenciamento de dispositivos IOS e Mac](https://docs.microsoft.com/intune-classic/deploy-use/set-up-ios-and-mac-management-with-microsoft-intune). 

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Faz** Há um problema com o certificado APNs (Apple Push Notification Service) configurado no Intune.

#### <a name="resolution"></a>Resolução
Renove o certificado APNs e registre novamente o dispositivo.

> [!IMPORTANT]
> Certifique-se de renovar o certificado APNs. Não substitua o certificado APNs. Se você substituir o certificado, será necessário registrar novamente todos os dispositivos iOS no Intune. 

- Para renovar o certificado APNs no Intune autônomo, consulte renovar [Apple MDM Push Certificate](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Para renovar o certificado APNs no Intune híbrido com Configuration Manager, consulte [Configurar o gerenciamento de dispositivo híbrido do IOS com System Center Configuration Manager e Microsoft Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/enroll-hybrid-ios-mac).
- Para renovar o certificado APNs no Office 365, consulte [criar um certificado APNs para dispositivos IOS](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpctypeerror-connection-invalid"></a>Conexão XPC_TYPE_ERROR inválida

Quando você ativa um dispositivo gerenciado por DEP que recebe um perfil de registro, o registro falha e você recebe a seguinte mensagem de erro:

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Faz** Há um problema de conexão entre o dispositivo e o serviço de DEP da Apple.

#### <a name="resolution"></a>Resolução
Corrija o problema de conexão ou use uma conexão de rede diferente para registrar o dispositivo. Talvez você também precise entrar em contato com a Apple se o problema persistir.


## <a name="other-issues"></a>Outros problemas

### <a name="dep-enrollment-doesnt-start"></a>O registro de DEP não é iniciado
Quando você ativa um dispositivo gerenciado por DEP que recebe um perfil de registro, o processo de registro do Intune não é iniciado.

**Faz** O perfil de registro é criado antes do token de DEP ser carregado no Intune.

#### <a name="resolution"></a>Resolução

1. Edite o perfil de registro. Você pode fazer qualquer alteração no perfil. A finalidade é atualizar a hora de modificação do perfil.
2. Sincronizar dispositivos gerenciados por DEP: Abra o portal do Intune **> admin** > **Gerenciamento** > de dispositivo móvel**Ios** > **programa de registro de dispositivos** > **sincronizar agora**. É enviado um pedido de sincronização para a Apple.

### <a name="dep-enrollment-stuck-at-user-login"></a>Registro de DEP travado no logon do usuário
Quando você ativa um dispositivo gerenciado por DEP que recebe um perfil de registro, a instalação inicial se une depois que você insere as credenciais.

**Faz** A autenticação multifator (MFA) está habilitada. Atualmente, o MFA não funciona durante o registro em dispositivos DEP.

#### <a name="resolution"></a>Resolução
Desabilite o MFA e registre novamente o dispositivo.

## <a name="next-steps"></a>Passos Seguintes

- [Resolução de problemas de inscrição de dispositivos no Intune](troubleshoot-device-enrollment-in-intune.md)
- [Faça uma pergunta no fórum do Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consulte o blog da equipe de suporte do Microsoft Intune](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Confira o blog do Microsoft Enterprise Mobility e segurança](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
