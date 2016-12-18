---
title: "Adicionar utilizadores e conceder permissões | Microsoft Intune"
description: "Sincronizar utilizadores no local com o Azure AD e conceder permissões de administrador para a sua subscrição do Intune"
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 6e9ec662-465b-4ed4-94c1-cff0fe18f126
ms.reviewer: angrobe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 18d31a306549bae6dd44ab78d1dd08649ee71158


---

# <a name="add-users-and-give-administrative-permission-to-intune"></a>Adicionar utilizadores e conceder permissões administrativas no Intune

Como administrador, pode adicionar utilizadores diretamente ou sincronizar utilizadores do Active Directory no local. Depois de adicionados, os utilizadores podem inscrever dispositivos e aceder a recursos da empresa. Também pode dar aos utilizadores permissões adicionais, incluindo *administrador inquilino*, *administrador de serviços* e *permissões de gestor de inscrição de dispositivo*.

Este tópico ajuda-o a:

- [Adicionar utilizadores ao Intune](#add-users-to-intune)
- [Conceder permissões adicionais do Intune](#grant-intune-permissions) incluindo:
  - [Administrador inquilino](#tenant-administrator)
  - [Administrador de serviços](#service-administrator)
  - [Gestores de inscrição de dispositivos](#device-enrollment-managers)

## <a name="add-users-to-intune"></a>Adicionar utilizadores ao Intune
Pode adicionar manualmente os utilizadores na sua subscrição do Intune através do [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), uma vez que não são atribuídos automaticamente a uma licença do Intune. Em vez disso, posteriormente, um administrador inquilino do Intune tem de editar a conta de utilizador para atribuir uma licença ao utilizador a partir do portal do Office 365. Para obter orientação, veja [Adicionar utilizadores individualmente ou em volume ao Office 365](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec).

### <a name="sync-active-directory-and-add-users-to-intune"></a>Sincronizar o Active Directory e adicionar utilizadores ao Intune
Pode configurar a sincronização de diretórios para importar contas de utilizador do Active Directory no local para o Microsoft Azure Active Directory (Azure AD) que inclui utilizadores do Intune. Ligar o serviço do Active Directory no local a todos os serviços baseados no Azure Active Directory simplifica bastante a gestão da identidade de utilizadores. Também pode configurar funcionalidades de início de sessão único para tornar a experiência de autenticação dos utilizadores familiar e fácil. Ao ligar o mesmo [inquilino do Azure AD](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) com múltiplos serviços, as contas de utilizador que anteriormente foram sincronizados estão disponíveis para todos os serviços baseados na cloud.

### <a name="how-to-sync-on-premises-users-with-azure-ad"></a>Como sincronizar os utilizadores no local com o Azure AD
A única ferramenta de que precisa para sincronizar as contas de utilizador com o Azure AD é o [Assistente do Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). O Assistente do Azure AD Connect proporciona uma experiência orientada e simplificada para ligar a sua infraestrutura de identidade no local à nuvem.  Escolha a sua topologia e as suas necessidades (um ou vários diretórios, sincronização de palavras-passe ou federação) e o assistente implementará e configurará todos os componentes necessários para ter a sua ligação pronta, incluindo serviços de sincronização, Serviços de Federação do Active Directory (AD FS) e o módulo Azure AD PowerShell.

> [!TIP]
> O Azure AD Connect engloba capacidades que foram anteriormente lançadas como Dirsync e Azure AD Sync. Saiba mais sobre a [integração de diretórios](http://technet.microsoft.com/library/jj573653.aspx). Para saber quais são as vantagens de sincronizar as contas de utilizador do diretório no local com o Azure AD, veja [Semelhanças entre o Active Directory e o Azure AD](http://technet.microsoft.com/library/dn518177.aspx).

## <a name="grant-intune-permissions"></a>Conceder permissões ao Intune

Depois de acrescentar utilizadores à sua subscrição do Intune, recomendamos que conceda permissões administrativas a algumas contas de utilizador. Para administrar o Intune, pode dar aos utilizadores três tipos de permissão do Intune
-   **Administrador inquilino**: utilize o portal Office 365 para atribuir este tipo de administrador para gerir a sua subscrição, incluindo faturação, armazenamento na cloud e para gestão dos utilizadores que podem utilizar o Intune.
-   **Administrador do serviços**: utilize a consola do administrador do Microsoft Intune para atribuir este tipo de administrador a tarefas quotidianas, incluindo gestão de dispositivos móveis e de computadores, implementação de políticas ou de aplicações e execução de relatórios.
-   **Gestor de inscrição de dispositivos**: utilize a consola do administrador do Microsoft Intune para atribuir este tipo de administrador a tarefas quotidianas, incluindo gestão de dispositivos móveis e de computadores, implementação de políticas ou de aplicações e execução de relatórios.


### <a name="tenant-administrator"></a>Administrador inquilino


Aos administradores inquilinos é atribuída uma função de administrador que define o âmbito de administração desse utilizador e as tarefas que o mesmo pode gerir. As funções de administrador são comuns entre os diferentes serviços em nuvem da Microsoft, embora alguns serviços não suportem determinadas funções. O Intune utiliza as seguintes funções:
- **Administrador global** – acede a todas as funcionalidades administrativas do Intune. Por predefinição, a pessoa que se inscreve no Intune torna-se um Administrador global. Os administradores globais são os únicos que podem atribuir outras funções de administrador. Pode ter mais do que um administrador global na sua organização. Como melhor prática, recomendamos que apenas algumas pessoas na sua empresa tenham esta função para reduzir o risco para o seu negócio.
- **Administrador de faturação** – faz compras, gere subscrições, gere pedidos de suporte e monitoriza o estado de funcionamento do serviço.
- **Administrador de palavras-passe** – repõe palavras-passe, gere pedidos de serviço e monitoriza o estado de funcionamento do serviço. Os administradores de palavras-passe estão limitados à reposição de palavras-passe para os utilizadores.
- **Administrador de suporte do serviço** – abre pedidos de suporte na Microsoft e visualiza o dashboard de serviço e o centro de mensagens. Tem permissões de "visualizar apenas" exceto para a abertura e leitura de pedidos de suporte.
- **Administrador de gestão de utilizadores** – repõe palavras-passe, monitoriza o estado de funcionamento do serviço, adiciona e elimina as contas de utilizador e gere pedidos de serviço. O administrador de gestão de utilizadores não pode eliminar um administrador global, criar outras funções de administrador ou repor palavras-passe para os administradores de faturação, globais e de serviço.

Por predefinição, a conta que utilizar para criar a sua subscrição do Microsoft Intune será um administrador inquilino com a função de administrador global. Enquanto administrador inquilino, utiliza a consola de administrador do Intune para gerir a sua subscrição do Intune e atribuir administradores inquilinos a partir do [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854). Utilize um administrador inquilino com função de administrador global para aceder ao portal e designar o seu primeiro administrador de serviços. Como melhor prática, não utilize um administrador inquilino em tarefas de gestão diárias. Um administrador inquilino não precisa de uma licença do Intune para aceder à consola de administrador do Intune. O administrador inquilino é um conceito comum nos serviços em nuvem da Microsoft. Quando subscreve o Intune, o seu serviço é um inquilino do Azure AD. Veja a secção de inquilino do Azure AD em [O que é um diretório do Azure AD?](http://technet.microsoft.com/library/jj573650.aspx) para obter mais informações.

Enquanto administrador inquilino, utilize o [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854) para gerir a sua subscrição, incluindo as seguintes tarefas, se a sua função de administrador o permitir:

- Gerir as contas de utilizador e configurar a sincronização de diretórios a partir do seu Active Directory no local
- Gerir grupos de utilizadores denominados grupos de segurança
- Atribuir licenças de utilizadores do Intune
- Configurar o nome de domínio para a sua subscrição utilizada quando os utilizadores iniciam sessão (por exemplo, contoso.com)
- Gerir faturação e compras incluindo licenças e espaço de armazenamento na cloud
- Localizar ligações para ver o estado de funcionamento do serviço do Intune

Para aceder ao portal do Office 365, a sua conta tem de ter o estado de início de sessão definido como **Permitido**. Este estado é diferente de ter uma licença para a subscrição. Por predefinição, todas as contas de utilizador têm o estado **Permitido**. Os utilizadores sem permissões de administrador podem utilizar o portal do Office 365 para repor palavras-passe do Intune.

### <a name="service-administrator"></a>Administrador de serviços

Por predefinição, o Intune não designa um administrador de serviços. Em vez disso, tem de utilizar um administrador inquilino com a função de administrador global para designar o primeiro administrador de serviços da sua subscrição. Enquanto administrador de serviços, utiliza a [consola de administrador do Intune](https://manage.microsoft.com/) para gerir as tarefas diárias do Intune. Pode designar administradores de serviços a partir da consola do administrador. Um administrador de serviços precisa de uma licença do Intune para poder aceder à consola de administração.

Aos administradores de serviços é atribuída uma das seguintes permissões:
- **Acesso total**: acesso sem restrições para todas as áreas da consola do administrador do Intune, adicionar e gerir outros administradores de serviços
- **Acesso só de leitura**: permissão de leitura para todas as áreas da consola do administrador do Intune, não pode modificar dados, mas pode executar relatórios
- **Suporte técnico – Nó de Grupos**: permite ao administrador de serviços executar apenas as tarefas associadas a cenários de suporte técnico, veja [Personalizar vistas da consola do Intune de acordo com funções de administrador](/intune/deploy-use/control-what-admins-can-see-in-the-microsoft-intune-admin-console)

Enquanto administrador de serviços, utilize este portal para gerir operações diárias, incluindo:

- Criar e gerir políticas para computadores e dispositivos móveis
- Carregar e implementar atualizações de software e aplicações
- Gerir o Endpoint Protection nos computadores
- Ver o estado dos dispositivos e executar relatórios

### <a name="device-enrollment-managers"></a>Gestores de inscrição de dispositivos

Os gestores de inscrição de dispositivos são contas de utilizador padrão com uma permissão adicional para inscrever mais dispositivos sem utilizador. Por predefinição, cada utilizador do Intune pode inscrever até quinze dispositivos. Como administrador, pode atribuir a uma conta de utilizador a permissão de gestor de inscrição de dispositivos. Essa conta pode inscrever um grande número de dispositivos pertencentes à empresa. Esta funcionalidade é útil se os dispositivos forem atribuídos aos utilizadores de forma temporária ou se forem utilizados no modo de local público, em que não é necessária a associação dos utilizadores aos dispositivos. Para obter mais informações, veja [Gestor de inscrição de dispositivos](https://docs.microsoft.com/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).

>[!div class="step-by-step"]

>[&larr; **Definições de domínio**](.\start-with-a-paid-subscription-to-microsoft-intune-step-2.md)     [**Gerir licenças do Intune** &rarr;](.\start-with-a-paid-subscription-to-microsoft-intune-step-4.md)  



<!--HONumber=Dec16_HO2-->


