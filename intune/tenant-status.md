---
title: Página de status do Microsoft Intune locatário
titleSuffix: Microsoft Intune
description: Use a página status do locatário do Intune para exibir detalhes importantes do locatário sem sair do portal do Intune
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 946d46baf17a5ffdd4b567adca32b651cacb72bb
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67882229"
---
# <a name="intune-tenant-status-page"></a>Página status do locatário do Intune
A página de status do locatário é um hub centralizado no qual você pode exibir os detalhes atuais e importantes sobre seu locatário. Os detalhes incluem disponibilidade e uso da licença, status do conector e comunicações importantes sobre o serviço do Intune.  

Para exibir o painel, na portal do Azure acesse o **Intune > status do locatário**.  O status do locatário aparece no **grupo ajuda e suporte**.  

A página é dividida em quatro áreas:

## <a name="tenant-details"></a>Detalhes do locatário
Os detalhes do locatário fornecem informações rápidas sobre seu locatário. Exiba detalhes como o nome do locatário e o local, sua autoridade de MDM e o número de versão do serviço de locatários. O número de versão do serviço é um link que abre o artigo *novidades no Intune* no Microsoft docs. Nas novidades, você pode ler sobre os recursos e as atualizações mais recentes para o serviço do Intune.  

Esta seção também fornece informações básicas sobre suas licenças disponíveis e quantos são atribuídos aos usuários. As licenças para dispositivos não são mostradas.

## <a name="connector-status"></a>Status do conector
Status do conector é um local de uma única parada para examinar o status de todos os conectores disponíveis para o Intune.  

Os conectores são:
- **Conexões que você configura para serviços externos**. Por exemplo, o serviço de *Apple Volume Purchase Program* ou o serviço de *piloto automático do Windows* .  O status desse tipo de conector é baseado na última hora de sincronização bem-sucedida.
- **Certificados ou credenciais que são necessários para se conectar a um serviço externo não gerenciado**, como certificados de APNS ( *Apple Push Notification Services* ). O status desse tipo de conector é baseado no carimbo de data/hora de expiração do certificado ou da credencial.  

Por padrão, a exibição mostra até cinco conectores. Você pode selecionar **Ver todos os conectores** para expandir esta lista para exibir todos os conectores disponíveis, incluindo conectores que você não configurou para uso.  

Os conectores não íntegros sempre são exibidos na parte superior da lista. Em seguida, há conectores com avisos e, em seguida, a lista de conectores íntegros. Os conectores que você ainda não configurou aparecem por último.

Quando há mais de um único conector de um tipo, o status é um resumo para todos os mesmos conectores. O status menos íntegro de qualquer conector único é usado como a integridade do grupo.  

**Status do conector:**
- **Não íntegro**
  - O certificado ou a credencial expirou
  - A última sincronização ocorreu há três ou mais dias
- **Alerta**
  - O certificado ou a credencial expirará dentro de sete dias
  - A última sincronização ocorreu há mais de um dia
- **Íntegro**
  - O certificado ou a credencial não expirará nos próximos sete dias
  - A última sincronização foi menor que um dia atrás  

Quando você seleciona um conector na lista, o portal apresenta a página do portal que é relevante para criar ou configurar esse conector.  Por exemplo, quando você seleciona o conector de data de expiração do **VPP** , a página tokens do **programa adquiridos por volume do IOS** é aberta, na qual você pode exibir mais detalhes sobre esse conector. Você pode criar uma nova configuração ou editar e corrigir problemas com um existente.  

## <a name="intune-service-health"></a>Estado de funcionamento do serviço do Intune  
Você pode exibir detalhes de incidentes e avisos ativos sem precisar navegar até o painel de integridade do serviço Microsoft 365 ou o centro de mensagens, ambos localizados no [centro de administração do Microsoft 365](https://admin.microsoft.com). Somente incidentes em que o impacto foi observado para afetar seu locatário são mostrados.  

Quando você seleciona um incidente, os detalhes do incidente são apresentados diretamente na página status do locatário. Para exibir as consultas e os incidentes anteriores, selecione **Ver incidentes/avisos anteriores**. O centro de administração do Microsoft 365 é aberto e você pode exibir avisos e incidentes dos últimos 30 dias para seu locatário.  

Para exibir informações sobre a *integridade do serviço do Intune*, sua conta deve ter a função **administrador global** ou **administrador de serviços** no Azure Active Directory ou no centro de administração Microsoft 365. Para atribuir essas permissões, entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com) com permissões de administrador global. Selecione **usuários > usuários ativos**e, em seguida, selecione a conta que requer acesso. Selecione **Editar** para funções, selecione *administrador de serviços* ou *administrador global*e, em seguida, **salve** a edição para atribuir as permissões.  

Você só pode configurar suas preferências de comunicação para a integridade do serviço do Intune por meio do centro de administração Microsoft 365.

## <a name="intune-news"></a>Notícias do Intune  
Exiba comunicações informativas da equipe de serviço do Intune sem precisar navegar até o centro de mensagens do Office. As comunicações incluem mensagens sobre alterações que ocorreram recentemente no serviço do Intune ou que estão no caminho do seu locatário.  

Por padrão, as últimas 10 mensagens ativas são exibidas. Para exibir mensagens mais antigas, selecione **Ver mensagens anteriores** para abrir o *centro de mensagens* no centro de administração Microsoft 365.  

Para exibir informações de notícias do Intune, sua conta deve ter a função **administrador global** ou **administrador de serviços** no Azure Active Directory ou a função **leitor do centro de mensagens** no centro de administração do Microsoft 365.  Para atribuir essa permissão, entre no centro de [Administração do Microsoft 365](https://admin.microsoft.com) com permissões de administrador. Selecione **usuários > usuários ativos**e, em seguida, selecione a conta que requer acesso. Selecione **Editar** para *funções*, selecione *administrador de comunicações de equipes*e **salve** a edição para atribuir as permissões.  

Você só pode configurar suas preferências de comunicação para as notícias do Intune por meio do centro de administração Microsoft 365.
