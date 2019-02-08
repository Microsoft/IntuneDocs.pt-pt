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
ms.collection: M365-identity-device-management
ms.openlocfilehash: fafd9c92a51c8ef258d151a3c19c271fdc45f4c2
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55835865"
---
# <a name="unenroll-your-android-device-from-management"></a>Anular a inscrição do seu dispositivo Android na gestão  

Remova um dispositivo Android inscrito para que deixe de ser gerido pela sua organização. Este artigo descreve como remover o dispositivo da aplicação Portal da Empresa. Depois de remover o dispositivo:  

* O dispositivo perde o acesso aos dados e aos recursos protegidos da sua organização.
* O dispositivo deixa de ser apresentado no Portal da Empresa.
* Não pode instalar aplicações a partir do Portal da Empresa.
* As definições alteradas no seu dispositivo quando o adicionou (por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe) deixam de ser aplicáveis.  

1. No Portal da Empresa, no canto superior direito, toque nos três pontos verticais. É aberto o menu de ação.

   ![Uma captura de ecrã da aplicação Portal da empresa para Android, com o menu de ação aberto no canto superior direito. A nova opção “Remover Portal da Empresa” está disponível como a terceira opção, abaixo de “O Meu Perfil” e “Definições” e acima de “Termos e Condições”, “Ajuda e Comentários” e “Acerca de”.](./media/android_remove_cp_menu_action_after_1705.png)

2. Toque em **Remover Portal da Empresa**.  

3. É apresentada uma mensagem com informações sobre o que acontece depois de anular a inscrição do seu dispositivo. Toque em **OK** para confirmar que quer remover o dispositivo do Portal da Empresa.

   ![Uma captura de ecrã de confirmação disponível depois de selecionar a nova opção "Remover portal da empresa" no menu de ação.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>Remover dados recolhidos pela aplicação Portal da empresa  

Para remover todos os dados que a aplicação Portal da Empresa para Android armazena no seu dispositivo:

-   Limpar dados de aplicação ao tocar em **aplicativos** > **[*nome da aplicação*]** > **limpar dados**.
-   Elimine a pasta seguinte: \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal.

## <a name="uninstall-the-company-portal-app"></a>Desinstalar a aplicação Portal da Empresa  
Portal da empresa é uma aplicação de gestão de dispositivos. Ele não pode ser desinstalado até que anula a inscrição do dispositivo no seu gerenciamento. Depois de concluir esse procedimento, toque sem soltar no ícone da aplicação Portal da Empresa, até surgir **Desinstalar**. Toque em **Desinstalar** para remover a aplicação do seu dispositivo.  

Em alternativa, toque em **configurações** > **aplicações** > **Portal da empresa** > **desinstalação**.  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>Remover a aplicação Portal da empresa como um administrador do dispositivo  
Como último recurso, pode desinstalar a aplicação a partir do seu dispositivo como um administrador do dispositivo.  

Se tiver um dispositivo da empresa, a sua organização pode exigir que o Portal da empresa ser no seu dispositivo durante todo o tempo. Se desinstalá-lo, poderá perder o acesso a recursos protegidos da empresa como e-mail, aplicações, Wi-Fi ou VPN, até que a aplicação é reinstalada. Para obter mais informações sobre como instalar, atualizar ou remover as aplicações necessárias, consulte [adicionar aplicações ao Microsoft Intune](https://docs.microsoft.com/intune/apps-add#apps-that-are-added-automatically-by-intune).  

Eis como desativar o Portal da empresa como um administrador do dispositivo. Os nomes reais de cada configuração podem variar no seu dispositivo Android.  

**Opção 1**:  
1. Selecione **configurações** > **segurança** > **configurações de segurança adicionais** > **administradores de dispositivos** .  
2. Limpar o **Portal da empresa** seleção.  

**Opção 2**:  
1. Selecione **configurações** > **bloqueio de ecrã e segurança** > **outras definições de segurança** > **administração de dispositivos aplicações**.  
2. Limpar o **Portal da empresa** seleção.    

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
