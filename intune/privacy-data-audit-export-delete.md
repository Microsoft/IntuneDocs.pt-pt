---
title: Auditar, exportar ou eliminar dados pessoais
description: Saiba como auditar, exportar ou eliminar dados pessoais.
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 05/18/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 96990be0-eb1e-43a4-a0e4-09c7dbdc2bf4
ms.reviewer: angerobe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 76e0c411afe1fb4e32b26c6ad669cb91b6cd3336
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57232799"
---
# <a name="audit-export-or-delete-personal-data-in-intune"></a>Auditar, exportar ou eliminar dados pessoais no Intune

Os administradores do Intune podem utilizar os registos de auditoria para controlar atividades relacionadas com os dados pessoais. Também podem exportar e eliminar dados pessoais.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]

## <a name="audit-personal-data"></a>Auditar dados pessoais

Os registos de auditoria proporcionam aos administradores de inquilinos um registo das atividades que geram uma alteração no Microsoft Intune. Os registos de auditoria estão disponíveis para muitas atividades de gestão e, normalmente, criam, atualizam (editam), eliminam e atribuem ações. Também podem ser revistas tarefas remotas que geram eventos de auditoria. Estes registos de auditoria poderão conter dados pessoais de utilizadores cujos dispositivos estão inscritos no Intune.  

Por motivos de segurança, o Intune poderá manter os registos de auditoria das ações do utilizador e do dispositivo durante um ano. Estes registos são eliminados automaticamente após o período de retenção de um ano.

Para rever os registos de auditoria, veja [Registos de auditoria das atividades do Intune](monitor-audit-logs.md). 

Os administradores não podem eliminar os registos de auditoria.

Estes eventos de auditoria são retidos durante um ano. Os administradores de inquilinos podem solicitar os registos de auditoria através [deste formulário de pedido de suporte](https://privacy.microsoft.com/en-US/privacy-questions?).

## <a name="export-personal-data"></a>Exportar dados pessoais

Os administradores podem exportar dados pessoais do utilizador final, incluindo contas, dados do serviço e registos associados, para cumprir as exigências associadas aos Direitos do Titular dos Dados. A decisão de fornecer ou não uma cópia dos dados pessoais ao titular dos dados é sua e da sua organização ou se tiver um motivo profissional legítimo para reter os dados. Se optar por fornecê-los, pode disponibilizar uma cópia do documento, uma versão não confidencial adequada ou uma captura de ecrã das partes que considera adequadas para partilhar.

Para exportar os dados pessoais de um utilizador, pode utilizar: 
- o painel Dispositivo de MDM do Intune para exportar uma lista de dispositivos. Também pode copiar diretamente dados do dispositivo.
- o [Export-IntuneData.ps1 script](https://aka.ms/intunedataexport).

## <a name="delete-end-user-personal-data"></a>Eliminar dados pessoais do utilizador final

Existem três formas de remover os dados pessoais da gestão do Intune:
- Eliminar o utilizador do Azure Active Directory
- Repor as predefinições de fábrica do dispositivo
- Remoção automática por parte do utilizador

### <a name="delete-a-user-from-intune"></a>Eliminar um utilizador do Intune

Para eliminar os dados pessoais de um utilizador final do Intune, o administrador tem de [eliminar o utilizador do Azure Active Directory (AAD)](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory.md#delete-users-from-azure-ad). Quando o utilizador é eliminado do AAD (eliminado definitivamente), o Intune recebe o sinal de eliminação do AAD e, em seguida, inicia automaticamente a remoção de todos os dados pessoais desse utilizador do serviço do Intune. As informações do utilizador serão eliminadas do serviço do Intune no prazo de 30 dias após a ação de remoção.

### <a name="reset-device-to-factory-settings"></a>Repor as predefinições de fábrica do dispositivo
A reposição das predefinições de fábrica restaura todas as definições e dados pessoais empresariais para as predefinições de fábrica. Isto é útil quando se fornece um dispositivo a outro colaborador. São removidos ficheiros do utilizador, aplicações instaladas pelo utilizador e definições não predefinidas. Estes dados são eliminados do serviço do Intune no prazo de 30 dias após a ação de remoção.

### <a name="user-self-removal-from-intune-management"></a>Remoção automática da gestão do Intune por parte do utilizador
Os utilizadores podem remover os respetivos dispositivos pessoais [Android, Apple ou Windows](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android.md) da gestão do Intune sem assistência administrativa.   

### <a name="retire"></a>Extinguir
A ação **Extinguir** remove dados aprovisionados do Intune, tais como aplicações da empresa, dados sobre aplicações geridas pelo Intune, definições de política e perfis de e-mail aprovisionados através do Intune. Esta ação mantém os dados pessoais do utilizador no dispositivo.

### <a name="delete-a-tenant-from-microsoft-intune"></a>Eliminar um inquilino do Microsoft Intune

Se um cliente inquilino do Intune cancelar a respetiva conta do Intune, todos os dados do inquilino são eliminados no prazo de 180 dias após o cliente fechar a conta do Intune. Se o inquilino do AAD estiver associado a outras subscrições do Microsoft Enterprise (Azure, Office 365), são eliminados apenas os Dados de Cliente do Intune. Mantém-se o recurso de inquilino do AAD para ser utilizado pelas outras subscrições. Se a conta do Intune for a única subscrição associada ao inquilino do AAD, o inquilino será eliminado, bem como todos os recursos e Dados do Cliente.

### <a name="delete-a-user-in-a-hybrid-mobile-device-management-mdm-environment"></a>Eliminar um utilizador num ambiente híbrido de Gestão de Dispositivos Móveis (MDM)
Quando tiver um ambiente híbrido de MDM (Intune integrado com o Configuration Manager), tem de concluir as seguintes ações (por ordem) para eliminar totalmente um utilizador e removê-lo completamente do seu Active Directory local, do Configuration Manager e do Intune.

1. Elimine o utilizador do seu Active Directory (AD) local. Isto impedirá a sincronização do utilizador com o Azure Active Directory e a deteção deste pelo Configuration Manager. 
2. Elimine o utilizador da consola do Configuration Manager para remover o utilizador e os dados associados do Configuration Manager. Na consola, aceda a **Ativos e Conformidade** > **Utilizadores**, clique com o botão direito no utilizador a eliminar e clique em **Eliminar**.
3. [Eliminar o utilizador do AAD](https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory.md#delete-users-from-azure-ad) remove o utilizador e os dados associados do Azure Active Directory e do Intune ao mesmo tempo. Quando o utilizador é eliminado do AAD (eliminado definitivamente), o Intune recebe o sinal de eliminação do AAD e, em seguida, inicia automaticamente a remoção de todos os dados pessoais desse utilizador do serviço do Intune. As informações do utilizador serão eliminadas do serviço do Intune no prazo de 30 dias após a ação de remoção.

## <a name="next-steps"></a>Passos Seguintes

Saiba como [auditar, exportar ou eliminar](privacy-data-audit-export-delete.md) dados pessoais no Intune.
