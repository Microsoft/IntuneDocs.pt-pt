---
title: No desenvolvimento – Microsoft Intune
titlesuffix: ''
description: Funcionalidades do Microsoft Intune em desenvolvimento
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 03/04/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: cacampbell
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 42200c474b964e6c6bc9610c3e90689c5811a2ee
ms.sourcegitcommit: 6da78a3c07e9ad9c72ff532867cde754e9deca00
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/07/2019
ms.locfileid: "57577834"
---
# <a name="in-development-for-microsoft-intune---march-2019"></a>No desenvolvimento do Microsoft Intune – Março de 2019

Para ajudar na preparação de sua e planejamento, esta página, listas de atualizações de interface do Usuário do Intune e recursos que estão em desenvolvimento, mas ainda não lançadas. Além disso:

- Se prevemos que precisará executar uma ação antes de uma alteração, vamos publicar uma mensagem de centro de mensagens do Office gratuita.
- Quando um recurso é iniciado na produção, como uma pré-visualização ou em disponibilidade geral, a descrição da funcionalidade irá mover esta página e para o [página Novidades](whats-new.md).
- Esta página e o [página Novidades](whats-new.md) são atualizados periodicamente. Volte a consultar posteriormente para obter mais atualizações.
- Consulte a [M365 Roteiro](https://www.microsoft.com/microsoft-365/roadmap?rtc=2&filters=EMS) para resultados estratégicos e as linhas do tempo.

> [!Note]
> Estes itens refletem as expectativas de atuais da Microsoft sobre as capacidades do Intune numa versão futura. Datas e funcionalidades individuais podem ser alteradas. Nem todos os itens no desenvolvimento de tem uma descrição da funcionalidade nesta página.


<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure


<!-- 1903 start-->

### <a name="encryption-report-----2351538---"></a>Relatório de encriptação  <!-- 2351538 -->
Será capaz de utilizar um novo relatório de encriptação para ver detalhes sobre o estado de encriptação dos seus dispositivos. Detalhes disponíveis incluirá uma versão do TPM de dispositivos, preparação de encriptação e o estado, o relatório de erros e mais.  

### <a name="access-bitlocker-recovery-keys-from-the-intune-portal-----2351547----"></a>Aceder a chaves de recuperação do BitLocker a partir do portal do Intune  <!-- 2351547  -->
Estamos a adicionar um novo ponto de entrada em dispositivos, onde pode ver os detalhes do Azure Active Directory (AAD) sobre o ID da chave do BitLocker e chaves de recuperação do BitLocker.

### <a name="scope-tags-for-app-configuration-policies---2371891---"></a>Etiquetas de âmbito para políticas de configuração de aplicações <!--2371891 -->
Poderá adicionar uma etiqueta de âmbito a uma política de configuração de aplicação para que apenas as pessoas com funções atribuídas também essa etiqueta de âmbito tenham acesso para a política de configuração de aplicação. A política de configuração de aplicação só pode ser direcionada para ou associada a aplicações atribuídas a mesma etiqueta de âmbito.

### <a name="assign-autopilot-profiles-to-the-all-devices-virtual-group---2715522---"></a>Atribuir perfis do Autopilot ao grupo virtual Todos os dispositivos <!--2715522 -->
Poderá atribuir perfis do Autopilot ao grupo virtual Todos os dispositivos. Para o fazer, selecione **Inscrição de dispositivos** > **Inscrição do Windows** > **Perfis de Implementação** > selecione um perfil >  **Atribuições** > em **Atribuir a**, selecione **Todos os dispositivos**. Para obter mais informações sobre perfis do Autopilot, veja [Inscrever dispositivos Windows com o Windows AutoPilot](enrollment-autopilot.md).

### <a name="install-available-apps-using-the-company-portal-app-after-windows-bulk-enrollment----2751523----"></a>Instalar as aplicações disponíveis com a aplicação Portal da empresa após a inscrição em massa do Windows <!-- 2751523  -->
Dispositivos Windows inscritos no Intune, utilizando [inscrição em massa de Windows](windows-bulk-enroll.md) (pacotes de aprovisionamento) será possível utilizar a aplicação do Portal da empresa para instalar as aplicações disponíveis. Para obter mais informações sobre a aplicação Portal da empresa, consulte [adicionar manualmente o Portal da empresa do Windows 10](store-apps-company-portal-app.md) e [como configurar a aplicação Portal da empresa do Microsoft Intune](company-portal-app.md).

### <a name="scope-tags-for-ios-app-provisioning-profiles---2934430---"></a>Etiquetas de âmbito para perfis de aprovisionamento de aplicações iOS <!--2934430 -->
Poderá adicionar uma etiqueta de âmbito para um perfil de aprovisionamento de aplicações iOS, para que apenas as pessoas com funções atribuídas também essa etiqueta de âmbito tenham acesso para o perfil de aprovisionamento de aplicações iOS. 

### <a name="office-deployment-tool-odt-xml-for-office-proplus-deployment----3192477----"></a>Ferramenta de implementação do Office (ODT) XML para a implementação do Office ProPlus <!-- 3192477  -->
Será capaz de fornecer a ferramenta de implementação do Office (ODT) XML ao criar uma instância do Office Pro Plus na consola de administração do Intune. Isso permitirá que a maior capacidade de personalização se as opções de interface do Usuário do Intune existentes não atenderem às suas necessidades. 

###  <a name="block-users-from-scanning-for-windows-updates-------3316758------"></a>Impedir que os utilizadores a analisar as atualizações do Windows    <!-- 3316758    -->
Estamos a adicionar uma novo Windows cadência de atualização que pode utilizar a definição que irá impedir que os utilizadores a analisar as atualizações do Windows. Esta definição não estará disponível a partir do portal, mas pode ser configurada utilizando a Graph API do Intune.

### <a name="windows-update-notifications-----3316782---"></a>Notificações de atualização do Windows  <!-- 3316782 -->
Estamos a adicionar suporte para as configurações de anel de atualização do Windows para que possa configurar as notificações de atualização do Windows que os seus utilizadores verão. Esta definição não estará disponível a partir do portal, mas pode ser configurada utilizando a Graph API do Intune.

### <a name="changes-to-company-portal-enrollment-for-ios-12-device-users---3448635---"></a>Alterações para a inscrição no Portal da empresa para os utilizadores de dispositivos iOS 12 <!--3448635 -->  
Portal da empresa para iOS irão atualizar ecrãs de inscrição da aplicação e os passos para se alinhar com as alterações de inscrição de MDM lançadas no Apple iOS 12.2. O fluxo de trabalho atualizado vai agora pedir aos utilizadores:

- Permita o Safari abrir o site do Portal da empresa (por meio do Safari) e transferir o perfil de gestão antes de retornar para a aplicação Portal da empresa. 
- Abra a aplicação de definições para instalar o perfil de gestão no respetivo dispositivo.
- Regressar à aplicação Portal da empresa que conclua a inscrição.  

Para obter mais informações sobre como pode preparar para estas alterações, consulte a [postagem de Comunidade tecnológica da Microsoft] (https://techcommunity.microsoft.com/]. Entretanto, para suportar as novas inscrições iOS no Portal da empresa, atualizámos os passos em [inscrever o dispositivo de iOS no Intune](https://docs.microsoft.com/en-us/intune/ios-enroll). Estas alterações docs estarão em direto após Apple versões iOS versão 12.2. 

### <a name="support-for-additional-connectors-on-the-tenant-status-page----3617202-------"></a>Suporte para conectores adicionais na página de estado do inquilino <!-- 3617202     -->
A página de estado do inquilino irá apresentar informações do Estado de conectores adicionais, incluindo *a proteção de ameaças avançada do Windows Defender* (ATP) e outros conectores de defesa contra ameaças móveis.

### <a name="granting-intune-read-only-access-to-some-azure-active-directory-roles----3637917---"></a>Intune a conceder acesso de leitura apenas ao algumas funções do Azure Active Directory <!-- 3637917 -->
Podemos irá conceder que acesso só para as seguintes funções do Azure AD de leitura do Intune. Permissões concedidas com funções do Azure AD substituem as permissões concedidas com controlo de acesso baseado em funções (RBAC) do Intune.

Ler apenas o acesso aos dados de auditoria do Intune:

- Administrador de conformidade
- Administrador de dados de conformidade

Acesso só de leitura a todos os dados do Intune:

- Administrador de Segurança
- Operador de segurança
- Leitor de segurança
- Leitor global

### <a name="easier-access-to-diagnostic-settings------3804627-----"></a>Facilitar o acesso às definições de diagnóstico   <!-- 3804627   -->
Estamos a adicionar uma nova opção para o **registos de auditoria** painel em cada em cada carga de trabalho do Log de auditoria na consola do Intune que pode utilizar para abrir diretamente a *das definições de diagnóstico* página.

### <a name="create-and-use-device-configuration-profiles-on-android-zebra-devices-in-intune----3895244----"></a>Criar e utilizar perfis de configuração do dispositivo em dispositivos das riscas das Android no Intune <!-- 3895244  -->
O Intune suportará a configuração de dispositivos das riscas das Android. Especificamente, poderá: 

- Criar um perfil de configuração do dispositivo e aplicar as definições para dispositivos Android Enterprise as riscas das usando OEMConfig (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > **Android enterprise** para a plataforma).
- Criar um perfil de configuração do dispositivo e aplicar as definições para dispositivos as riscas das Android através de perfis de extensões de mobilidade (MX) gerados pelo StageNow (**configuração do dispositivo** > **perfis**  >  **Criar perfil** > **Android** para a plataforma).

Aplica-se a:  
- Android
- Android enterprise

<!-- 1901 start -->

### <a name="deployment-of-online-licensed-microsoft-store-for-business-apps----1672660----"></a>Implementação de online licenciado Microsoft Store para aplicações de negócio <!-- 1672660  -->
Será capaz de atribuir necessário online licenciada Microsoft Store para aplicações de negócio no contexto do dispositivo. Implementar um Microsoft Store para a aplicação de negócios desta forma permitirá que a aplicação ser instalada para todos os utilizadores no dispositivo. Isto só é aplicável no Windows 10 RS4 + dispositivos de ambiente de trabalho. A opção para instalar no contexto do dispositivo está disponível na página de atribuição de aplicações de cliente para aplicações licenciadas Online do MSFB.

## <a name="notices"></a>Avisos

[!INCLUDE [Intune notices](./includes/intune-notices.md)]

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
