---
title: Implementar a aplicação Lookout for Work
description: Configure e implemente a aplicação Lookout for Work para Android.
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 03/21/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 524c4209-ad57-4d35-955e-a00d796bf858
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: sandera
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1b08ac6049bc7bbbf5c2203f156a6c03b6fc7a51
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="configure-and-deploy-lookout-for-work-app"></a>Configurar e implementar a aplicação Lookout for Work

[!INCLUDE [classic-portal](../includes/classic-portal.md)]

Este artigo explica-lhe como configurar e implementar a aplicação Lookout for Work em dispositivos Android e iOS.

## <a name="android-google-play-store-app"></a>Android (aplicação da Google Play Store)

1. Na [consola do administrador do Microsoft Intune](https://manage.microsoft.com), aceda a **Aplicações** e selecione **Adicionar Aplicações**.
2. Na página **Configuração do Software** do publicador, selecione **Ligação externa** e especifique o URL seguinte: https://play.google.com/store/apps/details?id=com.lookout.enterprise
   >[!NOTE]
   >Não clique na caixa para exigir um browser gerido.

3. Na página **Descrição do software**, preencha as seguintes informações:
   * **Editor:** Lookout Mobile Security
   * **Nome:** Lookout for Work
   * **Descrição:** o Lookout oferece a melhor proteção contra ameaças para dispositivos móveis para manter o seu dispositivo seguro. Quando a aplicação Lookout está instalada no dispositivo, a aplicação protege o seu dispositivo de ameaças e irá alertá-lo a si e ao administrador da sua empresa, se forem detetadas algumas.
   * **Categoria:** Gestão de Computadores

4. Após a conclusão com êxito, verá uma mensagem **Carregamento de dados para o Microsoft Intune concluído com êxito**.

   Na Consola do Intune, quando clicar em **Aplicações**, verá a aplicação **Lookout for Work** na lista ![captura de ecrã da página de aplicações da consola de administração do Intune a mostrar as aplicações Lookout for Work na lista](../media/mtp/lookout-app-listed-intune-console.png)

5. Implemente a aplicação para os utilizadores ao selecionar a aplicação Lookout for Work e **Gerir Implementação**.

   Tem de selecionar os mesmos utilizadores adicionados na opção Gestão de Inscrições na consola do Lookout MTP.  Consulte o Passo 3 na [secção Configurar a sua subscrição com o Lookout MTP](configure-deploy-lookout-for-work-app.md) para obter informações sobre adicionar grupos de utilizadores ao Lookout MTP.

   >[!IMPORTANT]
   > O assistente de implementação de aplicações do Intune não tem conhecimento dos grupos de utilizadores do Azure AD e em alternativa utiliza os grupos de utilizadores do Intune. Por isso, tem de criar um grupo de utilizadores do Intune com base no grupo de utilizadores do Azure AD que está inscrito na consola do Lookout MTP, conforme descrito [neste](plan-your-user-and-device-groups.md) tópico.

6. Selecione a opção **Instalação Necessária** para exigir que a aplicação Lookout seja instalada no dispositivo do utilizador.

## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (versão Enterprise da aplicação Lookout)

1. Certifique-se de que a **gestão de iOS** está configurada no seu dispositivo. Para obter instruções sobre como configurar o dispositivo para a gestão de iOS, veja [Configurar a gestão de dispositivos iOS e Mac](set-up-ios-and-mac-management-with-microsoft-intune.md).

2. **Volte a assinar** a aplicação Lookout for Work para iOS. A Lookout faz a distribuição da respetiva aplicação Lookout for Work para iOS fora da iOS App Store. **Antes de distribuir a aplicação**,tem de voltar a assinar a aplicação com o seu iOS Enterprise Developer Certificate. Para obter instruções detalhadas para voltar a assinar a aplicação Lookout for Work para iOS, consulte [Lookout for Work iOS app re-signing process (Processo de reassinatura da aplicação Lookout for Work para iOS – em inglês)](https://personal.support.lookout.com/hc/articles/114094038714) no site da Lookout.

3. Ative a autenticação do Azure Active Directory para utilizadores iOS do seguinte modo:
   1.  Inicie sessão no portal de gestão do [Azure Active Directory](https://manage.windowsazure.com) e navegue para a página da aplicação.
   2.  Adicione a **aplicação Lookout for Work para iOS** como uma **aplicação de cliente nativo**.
   ![captura de ecrã da caixa de diálogo Adicionar aplicações a mostrar a opção Aplicação de cliente nativo](../media/mtp/aad-add-app.png)
   3. Substitua o valor **com.lookout.enterprise.onomedasuaempresa** pelo ID de pacote de cliente que selecionou quando assinou o IPA.
   4.  Adicione o URI de redirecionamento adicional: **&lt;companyportal://code/>** seguido de uma versão com codificação URL do seu URI de redirecionamento original.
   5.  Adicione **Permissões Delegadas** à sua aplicação.

   Para mais detalhes, consulte [Configure a native client application (Configurar uma aplicação de cliente nativo – em inglês)](https://azure.microsoft.com/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).

4. Carregue o ficheiro .ipa assinado novamente tal como descrito no tópico [Adicionar aplicações para dispositivos móveis no Microsoft Intune](/intune-classic/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune). Defina a versão de SO mínima para iOS 8.0 ou posterior.

   ![captura de ecrã da página de aplicações na consola de administração do Intune com a aplicação Lookout for Work apresentada na lista de aplicações](../media/mtp/ios-app-uploaded-intune.png)

5. Crie a política de configuração de aplicações geridas tal como descrito no tópico [Configurar aplicações iOS com políticas de configuração de aplicações móveis no Microsoft Intune](/intune-classic/deploy-use/configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune).

   ![captura de ecrã do assistente criar nova política com a política de configuração de aplicações para iOS 8.0 ou posterior realçada](../media/mtp/ios-app-config.png)

6. **Para implementar a aplicação para os utilizadores**, selecione a aplicação Lookout for Work e **Gerir Implementação**.

   Tem de selecionar os mesmos utilizadores que foram adicionados à opção Gestão de Inscrições na consola do Lookout.  Veja o Passo 3 na secção [configurar a subscrição do Lookout](https://docs.microsoft.com/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps) para obter informações sobre como adicionar grupos de utilizadores ao Lookout MTP.

   >[!IMPORTANT]
   > O assistente de implementação da aplicação Intune não se apercebe dos grupos de utilizadores do Azure AD e utiliza os grupos de utilizadores do Intune, pelo que tem de criar um grupo de utilizadores do Intune com base no grupo de utilizadores do Azure AD inscrito na consola do Lookout, conforme descrito [neste](plan-your-user-and-device-groups.md) tópico.

   Selecione a opção **Instalação Necessária** para exigir que a aplicação Lookout seja instalada no dispositivo do utilizador.

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>O que acontece quando a aplicação implementada é aberta no dispositivo
https://github.com/Microsoft/Docs/blob/master/ContributorGuide/index.md Quando o utilizador abre o Lookout for Work no dispositivo, é-lhe pedido para ativar a aplicação e selecionar a opção Iniciar sessão com o Azure Active Directory. Pode encontrar instruções detalhadas sobre o fluxo do utilizador final nos tópicos seguintes:

* [É-lhe pedido que instale o Lookout for Work no seu dispositivo Android](https://docs.microsoft.com/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)

* [Tem de resolver uma ameaça que o Lookout for Work encontrou no seu dispositivo Android](https://docs.microsoft.com/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>Próximos passos
* [Criar política de conformidade do dispositivo Lookout no Intune](https://docs.microsoft.com/sccm/protect/deploy-use/enable-device-threat-protection-rule-compliance-policy)
