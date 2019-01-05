---
title: Como remover o seu dispositivo Android do Intune | Documentos da Microsoft
description: Remover o seu dispositivo Android a partir do Portal da empresa do Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 01/04/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 75b26e178badbaa7905199eb91490134d2b72ba9
ms.sourcegitcommit: 61ed365f7f8826451c41bcab5e19bef97b5a3c72
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/05/2019
ms.locfileid: "54057343"
---
# <a name="unenroll-your-android-device-from-management"></a>Anular a inscrição do seu dispositivo Android na gestão  

Remova um dispositivo Android inscrito para que deixe de ser gerido pela sua organização. Este artigo descreve como remover o dispositivo da aplicação Portal da Empresa. Depois de remover o dispositivo:  

* O dispositivo perde o acesso aos dados e aos recursos protegidos da sua organização.
* O dispositivo deixa de ser apresentado no Portal da Empresa.
* Não pode instalar aplicações a partir do Portal da Empresa.
* As definições alteradas no seu dispositivo quando o adicionou (por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe) deixam de ser aplicáveis.  

1. No Portal da Empresa, no canto superior direito, toque nos três pontos verticais. É aberto o menu de ação.

   ![Uma imagem da aplicação Portal da Empresa para Android, com o menu de ação aberto no canto superior direito. A nova opção “Remover Portal da Empresa” está disponível como a terceira opção, abaixo de “O Meu Perfil” e “Definições” e acima de “Termos e Condições”, “Ajuda e Comentários” e “Acerca de”.](./media/android_remove_cp_menu_action_after_1705.png)

2. Toque em **Remover Portal da Empresa**.  

3. É apresentada uma mensagem com informações sobre o que acontece depois de anular a inscrição do seu dispositivo. Toque em **OK** para confirmar que quer remover o dispositivo do Portal da Empresa.

   ![Uma imagem da caixa de diálogo de confirmação, que está disponível depois de selecionar a nova opção “Remover Portal da Empresa” no menu de ação. A caixa de diálogo informa o utilizador que "ao remover o portal da empresa, o dispositivo já não será gerido pelo suporte da empresa e que poderá remover o acesso aos dados da empresa, às aplicações da empresa e ao e-mail da empresa". Em seguida, pede ao utilizador para confirmar se quer remover a aplicação Portal da Empresa ao selecionar “Sim”.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>Remover dados recolhidos pela aplicação Portal da Empresa  

Para remover todos os dados que a aplicação Portal da Empresa para Android armazena no seu dispositivo:

-   Limpe os dados da aplicação em Aplicações, clique na aplicação e, em seguida, no botão "Limpar dados"
-   Elimine a pasta "\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal"

## <a name="uninstall-the-company-portal-app"></a>Desinstalar a aplicação Portal da Empresa  
Portal da empresa é uma aplicação de gestão de dispositivos. Não pode ser desinstalado até [anular a inscrição do dispositivo no seu gerenciamento](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management). Depois de concluir esse procedimento, toque sem soltar no ícone da aplicação Portal da Empresa, até surgir **Desinstalar**. Toque em **Desinstalar** para remover a aplicação do seu dispositivo.  

Em alternativa, toque em **configurações** > **aplicações** > **Portal da empresa** > **desinstalação**.  

### <a name="remove-company-portal-app-as-device-administrator"></a>Remover a aplicação Portal da empresa como administrador do dispositivo  
Como último recurso, pode desinstalar a aplicação do seu dispositivo, removendo-lo como um administrador do dispositivo.  

Se tiver um dispositivo da empresa, a sua organização pode exigir que o Portal da empresa ser no seu dispositivo durante todo o tempo. Se desinstalá-lo, poderia perder o acesso a recursos protegidos da empresa como e-mail, aplicações, Wi-Fi ou VPN, até que a aplicação é reinstalada. Para obter mais informações sobre como instalar, atualizar ou remover as aplicações necessárias, consulte [adicionar aplicações ao Microsoft Intune](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune).  

Conclua os passos abaixo para desativar o Portal da empresa como um administrador do dispositivo. Os nomes reais de cada configuração podem variar no seu dispositivo Android.  

**Passos de Android, opção 1**:  
1. Selecione **configurações** > **segurança** > **configurações de segurança adicionais** > **administradores de dispositivos** .  
2. Limpar o **Portal da empresa** seleção.  

**Passos de Android, opção 2**:  
1. Selecione **configurações** > **bloqueio de ecrã e segurança** > **outras definições de segurança** > **administração de dispositivos aplicações**.  
2. Limpar o **Portal da empresa** seleção.    

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
