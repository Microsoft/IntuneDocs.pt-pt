---
title: Como remover o seu dispositivo Android do Intune | Documentos da Microsoft
description: Remova seu dispositivo Android do Portal da Empresa do Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: be980a8cd2eb7f0cbe40002f73f9bc36a36d1193
ms.sourcegitcommit: caee3c3fa77586314aa8040b0caf32a0527b669e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75859071"
---
# <a name="unenroll-your-android-device-from-management"></a>Anular a inscrição do seu dispositivo Android na gestão  

Remova um dispositivo Android inscrito para que deixe de ser gerido pela sua organização. Este artigo descreve como remover o dispositivo da aplicação Portal da Empresa. Depois de remover o dispositivo:  

* O dispositivo perde o acesso aos dados e aos recursos protegidos da sua organização.
* O dispositivo deixa de ser apresentado no Portal da Empresa.
* Não pode instalar aplicações a partir do Portal da Empresa.
* As definições alteradas no seu dispositivo quando o adicionou (por exemplo, a desativação da câmara ou o comprimento necessário específico de uma palavra-passe) deixam de ser aplicáveis.  

> [!NOTE]
> Você não pode cancelar o registro ou remover seu dispositivo de propriedade corporativa do aplicativo Microsoft Intune. O dispositivo foi registrado durante a instalação inicial do dispositivo e deve ser registrado para acessar os recursos da sua organização.  

1. No Portal da Empresa, no canto superior direito, toque nos três pontos verticais. É aberto o menu de ação.

   ![Uma captura de tela do aplicativo Portal da Empresa do Android, com o menu Ação aberto no canto superior direito. A nova opção “Remover Portal da Empresa” está disponível como a terceira opção, abaixo de “O Meu Perfil” e “Definições” e acima de “Termos e Condições”, “Ajuda e Comentários” e “Acerca de”.](./media/android_remove_cp_menu_action_after_1705.png)

2. Toque em **Remover Portal da Empresa**.  

3. É apresentada uma mensagem com informações sobre o que acontece depois de anular a inscrição do seu dispositivo. Toque em **OK** para confirmar que quer remover o dispositivo do Portal da Empresa.

   ![Uma captura de tela da confirmação disponível após a seleção da nova opção "remover portal da empresa" no menu Ação.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="remove-data-collected-by-the-company-portal-app"></a>Remover dados coletados pelo aplicativo Portal da Empresa  

Para remover todos os dados que a aplicação Portal da Empresa para Android armazena no seu dispositivo:

- Limpe os dados do aplicativo tocando em **aplicativos** > **[*nome do aplicativo*]**  > **limpar dados**.
- Exclua a seguinte pasta: \storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal.

## <a name="uninstall-the-company-portal-app"></a>Desinstalar a aplicação Portal da Empresa

Portal da Empresa é um aplicativo de gerenciamento de dispositivo. Ele não poderá ser desinstalado até que você cancele o registro do seu dispositivo de seu gerenciamento. Depois de concluir esse procedimento, toque sem soltar no ícone da aplicação Portal da Empresa, até surgir **Desinstalar**. Toque em **Desinstalar** para remover a aplicação do seu dispositivo.  

Como alternativa, toque em **configurações** > **aplicativos** > **portal da empresa** > **desinstalar**.  

### <a name="remove-the-company-portal-app-as-a-device-administrator"></a>Remover o aplicativo Portal da Empresa como um administrador de dispositivo

Como último recurso, você pode desinstalar o aplicativo do seu dispositivo como um administrador de dispositivo.  

Se você tiver um dispositivo de propriedade da empresa, sua organização poderá exigir que Portal da Empresa esteja em seu dispositivo em todos os momentos. Se você desinstalá-lo, poderá perder o acesso a recursos protegidos da empresa, como email, aplicativos, Wi-Fi ou VPN, até que o aplicativo seja reinstalado. Para obter mais informações sobre como instalar, atualizar ou remover aplicativos necessários, consulte [adicionar aplicativos ao Microsoft Intune](/intune/apps/apps-add#apps-that-are-added-automatically-by-intune).

Veja como desabilitar Portal da Empresa como um administrador de dispositivo. Os nomes reais de cada configuração podem variar em seu dispositivo Android.  

**Opção 1**:  

1. Selecione **configurações** > **segurança** > **configurações de segurança adicionais** > **Administradores de dispositivo**.  
2. Desmarque a seleção de **portal da empresa** .  

**Opção 2**:

1. Selecione **configurações** > **tela de bloqueio e segurança** > **outras configurações de segurança** > **aplicativos de administração de dispositivos**.
2. Desmarque a seleção de **portal da empresa** .

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [Web site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
