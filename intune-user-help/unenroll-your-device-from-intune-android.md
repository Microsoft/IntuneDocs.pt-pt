---
title: Como remover o seu dispositivo Android do Intune | Documentos da Microsoft
description: Descreve como anular a inscrição de dispositivos Android no Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 10/23/2018
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
ms.openlocfilehash: d932005c955afed7f16e9766b559b77b2cd43182
ms.sourcegitcommit: 604b29c480b24270b5debc3e5f3141c8149ee6ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/24/2018
ms.locfileid: "49959490"
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
O Portal da Empresa é uma aplicação de gestão de dispositivos, pelo que apenas pode ser desinstalado se [anular a inscrição do seu dispositivo na respetiva gestão](unenroll-your-device-from-intune-android.md#unenroll-your-android-device-from-management). Depois de concluir esse procedimento, toque sem soltar no ícone da aplicação Portal da Empresa, até surgir **Desinstalar**. Toque em **Desinstalar** para remover a aplicação do seu dispositivo.  

Em alternativa, toque em **Definições** > **Aplicações** > **Portal da Empresa** > **Desinstalar**.  

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
