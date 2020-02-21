---
title: Problemas de resolução de problemas de problemas de matrícula de dispositivos iOS/iPadOS no Microsoft Intune
titleSuffix: Microsoft Intune
description: Sugestões para resolver problemas quando se matriculam dispositivos iOS/iPadOS no Intune.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 11/18/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.reviewer: mghadial
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: a29fab4be6e2046b2c6757505001a7ba3455b8d6
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514324"
---
# <a name="troubleshoot-iosipados-device-enrollment-problems-in-microsoft-intune"></a>Problemas de resolução de problemas iOS/iPadOS problemas de inscrição no microsoft Intune

Este artigo ajuda os administradores intune a compreender e a resolver problemas ao inscrever dispositivos iOS/iPadOS no Intune.

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar a resolver problemas, é importante recolher algumainformação básica. Esta informação pode ajudá-lo a entender melhor o problema e reduzir o tempo para encontrar uma resolução.

Recolher as seguintes informações sobre o problema:

- Qual é a mensagem exata de erro?
- Onde vê a mensagem de erro?
- Quando começou o problema? A inscrição já funcionou?
- Que plataforma (Android, iOS/iPadOS, Windows) tem o problema?
- Quantos utilizadores são afetados? Todos os utilizadores são afetados ou apenas alguns?
- Quantos dispositivos são afetados? Todos os dispositivos são afetados ou apenas alguns?
- O que é a autoridade do MDM?
- Como é que as inscrições estão a ser realizadas? É "Bring your own device" (BYOD) ou Apple Device Registration Program (DEP) com perfis de inscrição?

## <a name="error-messages"></a>Mensagens de erro

### <a name="profile-installation-failed-a-network-error-has-occurred"></a>Instalação de perfil falhou. Ocorreu um erro de rede.

**Causa:** Há um problema não especificado com o iOS/iPadOS no dispositivo.

#### <a name="resolution"></a>Resolução

1. Para evitar a perda de dados nos seguintes passos (restaurar o iOS/iPadOS elimina todos os dados do dispositivo), certifique-se de que faz o backback dos seus dados.
2. Coloque o dispositivo em modo de recuperação e, em seguida, restaure-o. Certifique-se de que o configura como um novo dispositivo. Para obter mais informações sobre como restaurar os dispositivos iOS/iPadOS, consulte [https://support.apple.com/HT201263](https://support.apple.com/HT201263).
3. Reinscreva o dispositivo.

### <a name="profile-installation-failed-connection-to-the-server-could-not-be-established"></a>Instalação de perfil falhou. A ligação ao servidor não pôde ser estabelecida.

**Causa:** O seu inquilino Intune está configurado para permitir apenas dispositivos corporativos. 

#### <a name="resolution"></a>Resolução
1. Inicie sessão no portal do Azure.
2. Selecione **Mais Serviços,** procure Intune e, em seguida, selecione **Intune**.
3. Selecione **Inscrição de dispositivos** > **Restrições de inscrição**.
4. Sob restrições de **tipo de dispositivo,** selecione a restrição que pretende definir > **Propriedades** > **Selecione plataformas** > selecione **Permitir** **iOS,** e depois clique **EM OK**.
5. **Selecione plataformas De Configuração,** selecione **Permitir** dispositivos iOS/iPadOS de propriedade pessoal e, em seguida, clique em **OK**.
6. Reinscreva o dispositivo.

**Causa:** Os registos CNAME necessários no DNS não existem.

#### <a name="resolution"></a>Resolução
Crie registos de recursos DNS CNAME para o domínio da sua empresa. Por exemplo, se o domínio da sua empresa for contoso.com, crie um CNAME em DNS que redirecione EnterpriseEnrollment.contoso.com para EnterpriseEnrollment-s.manage.microsoft.com.

Apesar de a criação de entradas DNS CNAME ser opcional, os registos CNAME facilitam a inscrição para os utilizadores. Se não for encontrado nenhum registo CNAME de inscrição, os utilizadores receberão um pedido para introduzir manualmente o nome do servidor MDM, enrollment.manage.microsoft.com.

Se houver mais de um domínio verificado, crie um registo CNAME para cada domínio. Os registos de recursos CNAME têm de conter as seguintes informações:

|TIPO|Nome do anfitrião|Aponta para|TTL|
|------|------|------|------|
|CNAME|EnterpriseEnrollment.dominio_empresa.com|EnterpriseEnrollment-s.manage.microsoft.com|1 Hr|
|CNAME|EnterpriseRegistration.dominio_empresa.com|EnterpriseRegistration.windows.net|1 Hr|

Se a sua empresa utilizar vários domínios para as credenciais do utilizador, crie os registos CNAME para cada domínio.

> [!NOTE]
> As alterações aos registos DNS podem demorar até 72 horas a serem propagadas. Não é possível verificar a alteração de DNS no Intune até o registo DNS ser propagado.

**Causa:** Inscreveu um dispositivo que estava previamente matriculado numa conta de utilizador diferente, e o utilizador anterior não foi devidamente removido de Intune.

#### <a name="resolution"></a>Resolução
1. Cancele qualquer instalação de perfil atual.
2. Abra [https://portal.manage.microsoft.com](https://portal.manage.microsoft.com) em Safari.
3. Reinscreva o dispositivo.

> [!NOTE]
> Se a inscrição ainda falhar, remova os cookies no Safari (não bloqueie cookies), em seguida, reinscreva o dispositivo.

**Causa:** O dispositivo já está matriculado com outro fornecedor de MDM.

#### <a name="resolution"></a>Resolução
1. Abra **as Definições** no dispositivo iOS/iPadOS, vá para **a General > Gestão de Dispositivos**.
2. Remova qualquer perfil de gestão existente.
3. Reinscreva o dispositivo.

**Causa:** O utilizador que está a tentar inscrever o dispositivo não tem uma licença Microsoft Intune.

#### <a name="resolution"></a>Resolução
1. Vá ao [Office 365 Admin Center,](https://portal.office.com/adminportal/home#/homepage)e depois escolha **Utilizadores > Utilizadores Ativos**.
2. Selecione a conta de utilizador a que pretende atribuir uma licença de utilizador Intune e, em seguida, escolha as licenças do **Produto > Edit**.
3. Mude o alternância para a posição **On** para a licença que pretende atribuir a este utilizador e, em seguida, escolha **Guardar**.
4. Reinscreva o dispositivo.

### <a name="this-service-is-not-supported-no-enrollment-policy"></a>Este Serviço não é suportado. Sem política de inscrição.

**Causa**: Um certificado de push Apple MDM não está configurado no Intune, ou o certificado é inválido. 

#### <a name="resolution"></a>Resolução

- Se o certificado de push MDM não estiver configurado, siga os passos em Obter um certificado de [push Apple MDM](apple-mdm-push-certificate-get.md#steps-to-get-your-certificate).
- Se o certificado de push MDM for inválido, siga os passos no certificado de [push Apple MDM renovado](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).

### <a name="company-portal-temporarily-unavailable-the-company-portal-app-encountered-a-problem-if-the-problem-persists-contact-your-system-administrator"></a>Portal da Empresa temporariamente indisponível. A aplicação Portal da Empresa encontrou um problema. Se o problema persistir, contacte o administrador do sistema.

**Causa:** A aplicação Portal da Empresa está desatualizada ou corrompida.

#### <a name="resolution"></a>Resolução
1. Retire a aplicação Portal da Empresa do dispositivo.
2. Descarregue e instale a aplicação **Microsoft Intune Company Portal** a partir da App **Store.**
3. Reinscreva o dispositivo.
 > [!NOTE]
    > Este erro também pode ocorrer se o utilizador estiver a tentar inscrever mais dispositivos do que a inscrição do dispositivo está configurada para permitir. Siga as medidas de resolução para a Tampa do **Dispositivo Alcançada** abaixo se estes passos não resolverem o problema.

### <a name="device-cap-reached"></a>Tampa do dispositivo alcançada

**Causa:** O utilizador tenta inscrever mais dispositivos do que o limite de inscrição do dispositivo.

#### <a name="resolution"></a>Resolução
1. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **dispositivos** > **Todos os Dispositivos**, e verifique o número de dispositivos que o utilizador inscreveu.
    > [!NOTE]
    > Deve também ter o logon do utilizador afetado no portal do [utilizador Intune](https://portal.manage.microsoft.com/) e verificar os dispositivos que se inscreveram. Podem existir dispositivos que aparecem no portal do [utilizador intune,](https://portal.manage.microsoft.com/) mas não no [portal de administração Intune,](https://portal.azure.com/?Microsoft_Intune=1&Microsoft_Intune_DeviceSettings=true&Microsoft_Intune_Enrollment=true&Microsoft_Intune_Apps=true&Microsoft_Intune_Devices=true#blade/Microsoft_Intune_DeviceSettings/ExtensionLandingBlade/overview)estes dispositivos também contam para o limite de inscrição do dispositivo.
2. No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Dispositivos** > Restrições de **Inscrição** > verifique o limite de inscrição do dispositivo. Por predefinição, o limite é fixado para 15. 
3. Se o número de dispositivos matriculados atingir o limite, remova dispositivos desnecessários ou aumente o limite de inscrição do dispositivo. Como cada dispositivo matriculado consome uma licença Intune, recomendamos que remova sempre os dispositivos desnecessários primeiro.
4. Reinscreva o dispositivo.

### <a name="workplace-join-failed"></a>A join no local de trabalho falhou

**Causa:** A aplicação Portal da Empresa está desatualizada ou corrompida.  

#### <a name="resolution"></a>Resolução
1. Retire a aplicação Portal da Empresa do dispositivo.
2. Descarregue e instale a aplicação **Microsoft Intune Company Portal** a partir da App **Store.**
3. Reinscreva o dispositivo.

### <a name="user-license-type-invalid"></a>Tipo de licença de utilizador inválido

**Causa:** O utilizador que está a tentar inscrever o dispositivo não tem uma licença Intune válida.

#### <a name="resolution"></a>Resolução
1. Vá ao centro de administração da [Microsoft 365](https://portal.office.com/adminportal/home#/homepage)e, em seguida, escolha **utilizadores** > **Utilizadores Ativos**.
2. Selecione a conta de utilizador afetada > **Licenças** de produto > **Editar**.
3. Verifique se uma licença Intune válida é atribuída a este utilizador.
4. Reinscreva o dispositivo.

### <a name="user-name-not-recognized-this-user-account-is-not-authorized-to-use-microsoft-intune-contact-your-system-administrator-if-you-think-you-have-received-this-message-in-error"></a>Nome do utilizador não reconhecido. Esta conta de utilizador não está autorizada a utilizar o Microsoft Intune. Contacte o administrador do seu sistema caso considere que recebeu esta mensagem por engano.

**Causa:** O utilizador que está a tentar inscrever o dispositivo não tem uma licença Intune válida.

1. Vá ao centro de administração da [Microsoft 365](https://portal.office.com/adminportal/home#/homepage)e, em seguida, escolha **utilizadores** > **Utilizadores Ativos**.
2. Selecione a conta de utilizador afetada e, em seguida, escolha **as licenças** do Produto > **Editar**.
3. Verifique se uma licença Intune válida é atribuída a este utilizador.
4. Reinscreva o dispositivo.

### <a name="profile-installation-failed-the-new-mdm-payload-does-not-match-the-old-payload"></a>Instalação de perfil falhou. A nova carga útil do MDM não corresponde à carga antiga.

**Causa:** Um perfil de gestão já está instalado no dispositivo.

#### <a name="resolution"></a>Resolução

1. Abra **as Definições** no dispositivo iOS/iPadOS > **General** > Gestão de **Dispositivos**.
2. Toque no perfil de gestão existente e toque em **Remover Gestão.**
3. Reinscreva o dispositivo.

### <a name="noenrollmentpolicy"></a>NoEnrollmentPolicy

**Causa:** O certificado do Apple Push Notification Service (APNs) está em falta, inválido ou caducado.

#### <a name="resolution"></a>Resolução
Verifique se um certificado APNs válido é adicionado ao Intune. Para mais informações, consulte Configurar a [inscrição iOS/iPadOS](ios-enroll.md).

### <a name="accountnotonboarded"></a>AccountNotOnboarded

**Causa:** Há um problema com o certificado do serviço apple push notification (APNs) configurado em Intune.

#### <a name="resolution"></a>Resolução
Renovar o certificado APNs e, em seguida, reinscrever o dispositivo.

> [!IMPORTANT]
> Certifique-se de que renova o certificado APNs. Não substitua o certificado DE APNs. Se substituir o certificado, terá de reinscrever todos os dispositivos iOS/iPadOS em Intune. 

- Para renovar o certificado APNs em Intune autónomo, consulte Renovar o certificado de [push Apple MDM](apple-mdm-push-certificate-get.md#renew-apple-mdm-push-certificate).
- Para renovar o certificado APNs no Office 365, consulte [Criar um Certificado APNs para dispositivos iOS/iPadOS](https://support.office.com/article/Create-an-APNs-Certificate-for-iOS-devices-522b43f4-a2ff-46f6-962a-dd4f47e546a7).

### <a name="xpc_type_error-connection-invalid"></a>ligação XPC_TYPE_ERROR inválida

Quando liga um dispositivo gerido pelo DEP que lhe é atribuído um perfil de inscrição, a inscrição falha e recebe a seguinte mensagem de erro:

```
asciidoc
mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" } }
iPhone mobileassetd[83] <Notice>: Client connection invalid (Connection invalid); terminating connection
iPhone com.apple.accessibility.AccessibilityUIServer(MobileAsset)[288] <Notice>: [MobileAssetError:29] Unable to copy asset information from https://mesu.apple.com/assets/ for asset type com.apple.MobileAsset.VoiceServices.CombinedVocalizerVoices
iPhone mobileassetd[83] <Notice>: 0x1a49aebc0 Client connection: XPC_TYPE_ERROR Connection invalid <error: 0x1a49aebc0> { count = 1, transaction: 0, voucher = 0x0, contents = "XPCErrorDescription" => <string: 0x1a49aee18> { length = 18, contents = "Connection invalid" }
```

**Causa:** Há um problema de ligação entre o dispositivo e o serviço Apple DEP.

#### <a name="resolution"></a>Resolução
Corrija o problema de ligação ou utilize uma ligação de rede diferente para inscrever o dispositivo. Poderá também ter de contactar a Apple se o problema persistir.


## <a name="other-issues"></a>Outras questões

### <a name="dep-enrollment-doesnt-start"></a>A inscrição do DEP não começa
Quando liga um dispositivo gerido pelo DEP que é atribuído a um perfil de inscrição, o processo de inscrição intune não é iniciado.

**Causa:** O perfil de inscrição é criado antes do token DEP ser enviado para Intune.

#### <a name="resolution"></a>Resolução

1. Editar o perfil de inscrição. Pode fazer qualquer alteração no perfil. O objetivo é atualizar o tempo de modificação do perfil.
2. Synchronize dispositivos geridos pelo DEP: No [Microsoft Endpoint Manager Admin Center,](https://go.microsoft.com/fwlink/?linkid=2109431)escolha **Dispositivos** > **iOS** > **iOS matricular** > programa de inscrição  **Inscrição;** escolha agora um token > **Sync.** É enviado um pedido de sincronização para a Apple.

### <a name="dep-enrollment-stuck-at-user-login"></a>Inscrição de DEP presa no login do utilizador
Quando liga um dispositivo gerido pelo DEP que lhe é atribuído um perfil de inscrição, a configuração inicial fica depois de introduzir credenciais.

**Causa:** A autenticação multi-Factor (MFA) está ativada. Atualmente, o MFA não funciona durante a inscrição em dispositivos DEP.

#### <a name="resolution"></a>Resolução
Desative o MFA e, em seguida, reinscreva o dispositivo.


## <a name="next-steps"></a>Próximos passos

- [Resolução de problemas de inscrição de dispositivos no Intune](../troubleshoot-device-enrollment-in-intune.md)
- [Faça uma pergunta sobre o fórum Intune](https://social.technet.microsoft.com/Forums/%7Blang-locale%7D/home?category=microsoftintune&filter=alltypes&sort=lastpostdesc)
- [Consulte o Blog da Equipa de Suporte Intune da Microsoft](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/bg-p/IntuneCustomerSuccess)
- [Consulte o Microsoft Enterprise Mobility and Security Blog](https://techcommunity.microsoft.com/t5/Azure-Active-Directory-Identity/Announcing-the-public-preview-of-Azure-AD-group-based-license/ba-p/245210)
