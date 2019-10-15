---
title: Auditar, exportar ou excluir dados pessoais
titleSuffix: Microsoft Intune
description: Saiba como auditar, exportar ou excluir dados pessoais.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: kerimh
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 74428abf8141c648b5b81bba3177cc89a3cb01d2
ms.sourcegitcommit: dd6755383ba89824d1cc128698a65fde6bb2de55
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306812"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Auditar, exportar ou excluir dados pessoais no Intune

Os administradores do Intune podem usar logs de auditoria para controlar atividades em torno de dados pessoais. Os administradores também podem exportar e excluir dados pessoais.

[!INCLUDE [GDPR-related guidance](../includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>Auditar dados pessoais

Os logs de auditoria fornecem aos administradores de locatários um registro de atividades que geram uma alteração no Microsoft Intune. Os logs de auditoria estão disponíveis para muitas atividades de gerenciamento e normalmente criam, atualizam (editam), excluem e atribuem ações. Tarefas remotas que geram eventos de auditoria também podem ser revisadas. Esses logs de auditoria podem conter dados pessoais de usuários cujos dispositivos estão registrados no Intune.  

Para fins de segurança, o Intune pode manter logs de auditoria para ações de usuário e dispositivo por um período de um ano. Esses logs são excluídos automaticamente após o período de retenção de um ano.

Para examinar os logs de auditoria, consulte [logs de auditoria para atividades do Intune](../fundamentals/monitor-audit-logs.md). 

Os administradores não podem excluir os logs de auditoria.

Esses eventos de auditoria são mantidos por um ano. Os administradores de locatários podem solicitar logs de auditoria usando [esse formulário de solicitação de suporte](https://privacy.microsoft.com/en-US/privacy-questions?).

## <a name="export-personal-data"></a>Exportar dados pessoais

Os administradores podem exportar dados pessoais do usuário final, incluindo contas, dados de serviço e logs associados para atender a solicitações de direitos de entidade de dados. Cabe a você e à sua organização decidir se deseja ou não fornecer a entidade de dados com uma cópia dos dados pessoais ou se você tem um motivo comercial legítimo para retenções. Se você optar por fornecê-lo, poderá fornecê-los com uma cópia do documento real, uma versão corretamente redigida ou uma captura de tela das partes que você considerou que precisa compartilhar.

Para exportar dados pessoais de um usuário, você pode usar: 
- a folha do dispositivo MDM do Intune para exportar uma lista de dispositivos. Você também pode copiar os dados do dispositivo diretamente.
- o [script Export-IntuneData. ps1](https://aka.ms/intunedataexport).

## <a name="delete-end-user-personal-data"></a>Excluir dados pessoais do usuário final

Há três maneiras de remover dados pessoais do gerenciamento do Intune:
- Excluir o usuário do Azure Active Directory
- Redefinir o dispositivo para as configurações de fábrica
- Remoção automática do usuário

### <a name="delete-a-user-from-intune"></a>Excluir um usuário do Intune

Para excluir os dados pessoais de um usuário final do Intune, um administrador deve [excluir o usuário do Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user). Quando o usuário é excluído do AAD (com exclusão complexa), o Intune recebe o sinal de exclusão do AAD e, em seguida, começa automaticamente a limpar todos os dados pessoais do usuário do serviço do Intune. As informações do usuário serão excluídas do serviço do Intune dentro de 30 dias após a ação de remoção.

### <a name="reset-device-to-factory-settings"></a>Redefinir o dispositivo para as configurações de fábrica
Redefinir para as configurações de fábrica restaura todas as configurações e dados pessoais e da empresa para as configurações de fábrica originais. É útil para fornecer um dispositivo para o próximo funcionário. Os arquivos do usuário, os aplicativos instalados pelo usuário e as configurações não padrão são removidos e esses dados são excluídos do serviço do Intune dentro de 30 dias após a ação de remoção.

### <a name="user-self-removal-from-intune-management"></a>Remoção automática do usuário do gerenciamento do Intune
Os usuários podem remover seu dispositivo pessoal do [Android, Apple ou Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android) do gerenciamento do Intune sem assistência de administrador.   

### <a name="retire"></a>Desativar
A ação **desativar** remove dados provisionados pelo Intune, como aplicativos da empresa, dados sobre aplicativos que o Intune está gerenciando, configurações de política e perfis de email que são provisionados por meio do Intune. Essa ação deixa os dados pessoais do usuário no dispositivo.

### <a name="delete-a-tenant-from-microsoft-intune"></a>Excluir um locatário de Microsoft Intune

Se um cliente de locatário do Intune cancelar sua conta do Intune, todos os dados de locatário serão excluídos dentro de 180 dias depois que o cliente fechar a conta do Intune. Se o locatário do AAD estiver associado a outras assinaturas corporativas da Microsoft (Azure, Office 365), somente os dados do cliente do Intune serão excluídos. O recurso de locatário do AAD é mantido para ser usado pelas outras assinaturas. Se a conta do Intune for a única assinatura associada ao locatário do AAD, o locatário será excluído e todos os recursos e dados do cliente também serão excluídos.

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>Excluir um usuário em um ambiente de MDM (gerenciamento de dispositivo móvel) híbrido
Quando você tem um ambiente de MDM híbrido (o Intune integrado com o Configuration Manager), você deve concluir as seguintes ações (em ordem) para excluir completamente um usuário e removê-los completamente do seu Active Directory local, Configuration Manager e Intune.

1. Exclua o usuário do seu Active Directory local (AD). Isso impedirá que o usuário seja sincronizado com o Azure AD e também descoberto pela descoberta de Configuration Manager. 
2. Exclua o usuário do console de Configuration Manager para remover o usuário e os dados associados do Configuration Manager. No console do, acesse **ativo e conformidade** > **usuários**, clique com o botão direito do mouse no usuário a ser excluído e clique em **excluir**.
3. [Exclua o usuário do AAD](https://docs.microsoft.com/azure/active-directory/fundamentals/add-users-azure-active-directory#delete-a-user), que remove o usuário e os dados associados do Azure Active Directory e do Intune ao mesmo tempo. Quando o usuário é excluído do AAD (com exclusão complexa), o Intune recebe o sinal de exclusão do AAD e, em seguida, começa automaticamente a limpar todos os dados pessoais do usuário do serviço do Intune. As informações do usuário serão excluídas do serviço do Intune dentro de 30 dias após a ação de remoção.

> [!Important]
>A integração de novos clientes híbridos do MDM foi preterida. Para obter mais informações, consulte a postagem [do blog mover do gerenciamento de dispositivo móvel híbrido para o Intune no Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) .

## <a name="next-steps"></a>Passos seguintes

Descubra como [auditar, exportar ou excluir](privacy-data-audit-export-delete.md) dados pessoais no Intune.
