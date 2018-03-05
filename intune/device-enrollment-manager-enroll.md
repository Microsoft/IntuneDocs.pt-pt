---
title: "Inscrever dispositivos – gestor de inscrição de dispositivos"
titlesuffix: Azure portal
description: "Utilize a conta do gestor de inscrição de dispositivos para inscrever dispositivos no Intune. \""
keywords: 
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 01/03/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: damionw
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 4ae5060ca2ea884ddbcf0e21d7a6e95c56f973bc
ms.sourcegitcommit: a6fd6b3df8e96673bc2ea48a2b9bda0cf0a875ae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/03/2018
---
# <a name="enroll-devices-using-device-enrollment-manager"></a>Inscrever dispositivos com o gestor de inscrição de dispositivos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador. A conta do *gestor de inscrição de dispositivos* (DEM) é uma conta de utilizador especial que pode inscrever até 1000 dispositivos. Pode adicionar utilizadores existentes à conta DEM de forma a conceder-lhes capacidades especiais de DEM. Cada dispositivo inscrito utiliza uma única licença. Recomendamos que utilize os dispositivos inscritos através desta conta como dispositivos partilhados em vez de dispositivos pessoais (“BYOD”).  

Têm de existir utilizadores no portal do Azure para serem adicionados como gestores de inscrição de dispositivos. Para garantir a segurança, o utilizador DEM não deve ser também um administrador do Intune.

>[!NOTE]
>O método de inscrição DEM não pode ser utilizado com estes métodos de inscrição: [Apple Configurator com o Assistente de Configuração](apple-configurator-setup-assistant-enroll-ios.md), [Apple Configurator com inscrição direta](apple-configurator-direct-enroll-ios.md), [Gestor de Escola da Apple (ASM)](apple-school-manager-set-up-ios.md) ou [Programa de Inscrição de Dispositivos (DEP)](device-enrollment-program-enroll-ios.md). Também não pode servir para inscrever dispositivos macOS.

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Exemplo de um cenário do gestor de inscrição de dispositivos

Um restaurante quer fornecer 50 tablets de ponto de venda aos seus empregados de mesa e monitores de apresentação de pedidos para os empregados da cozinha. Os funcionários não precisam nunca de aceder aos dados da empresa nem de iniciar sessão como utilizadores. O administrador do Intune cria uma conta de gestor de inscrição de dispositivos e adiciona um supervisor de restaurante à conta DEM, concedendo assim capacidades de DEM a esse supervisor. Agora, o supervisor pode inscrever os 50 tablets com as credenciais de DEM.

Apenas os utilizadores do portal do Azure podem ser gestores de inscrição de dispositivos. O utilizador do gestor de inscrição de dispositivos não pode ser um administrador do Intune.

O utilizador DEM pode:

-   Inscrever até 1000 dispositivos no Intune
-   Iniciar sessão no Portal da Empresa para obter aplicações da empresa
-   Configurar o acesso aos dados da empresa ao implementar aplicações específicas de funções nos tablets

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitações dos dispositivos inscritos com uma conta DEM

Os dispositivos inscritos com uma conta de gestor de inscrição de dispositivos têm as seguintes limitações:

  - Nenhum acesso por utilizador. Uma vez que os dispositivos não têm um utilizador atribuído, o dispositivo não tem nenhum acesso a dados ou e-mails da empresa. As configurações VPN, por exemplo, poderão continuar a ser utilizadas para fornecer aplicações de dispositivos com acesso a dados.
  - Sem acesso condicional porque estes cenários são por utilizador.
  - O utilizador DEM não pode utilizar o Portal da Empresa para anular a inscrição de dispositivos inscritos para DEM no próprio dispositivo. O administrador do Intune pode fazer isto, mas o utilizador DEM não.
  - Apenas o dispositivo local é apresentado na aplicação Portal da Empresa ou do site.
  - Os utilizadores não podem utilizar aplicações Apple Volume Purchase Program (VPP) devido aos requisitos do Apple ID por utilizador para a gestão de aplicações.
  - (Apenas para iOS) Se utilizar o DEM para inscrever dispositivos iOS, não poderá utilizar o Apple Configurator, o Programa de Inscrição de Dispositivos Apple (DEP) ou o Gestor de Escola da Apple (ASM) para inscrever dispositivos.
  - (Apenas Android) Existe um limite para o número de dispositivos Android for Work que pode inscrever com uma única conta DEM. Pode inscrever um máximo de 10 dispositivos de perfil de trabalho Android por conta DEM. Esta limitação não se aplica à inscrição Android legada.
  - Cada dispositivo requer uma licença de dispositivo. Saiba mais sobre [licenças de utilizador e dispositivo](licenses-assign.md#how-user-and-device-licenses-affect-access-to-services).


> [!NOTE]
> Para implementar aplicações da empresa em dispositivos geridos com o gestor de inscrição de dispositivos, implemente a aplicação Portal da Empresa como uma **Instalação Obrigatória** na conta de utilizador do gestor de inscrição de dispositivos.
> Para melhorar o desempenho, a aplicação Portal da Empresa num dispositivo DEM apresenta apenas os dispositivos locais. A gestão remota de outros dispositivos DEM só pode ser efetuada a partir da consola de administração do Intune.


## <a name="add-a-device-enrollment-manager"></a>Adicionar um gestor de inscrição de dispositivos

1.  No [Intune no portal do Azure](https://aka.ms/intuneportal), selecione **Inscrição de dispositivos** > **Gestores de inscrições de dispositivos**.

2.  Selecione **Adicionar**.

3.  No painel **Adicionar Utilizador**, introduza um nome principal para o utilizador DEM e selecione **Adicionar**. O utilizador DEM é adicionado à lista de utilizadores DEM.

## <a name="permissions-for-dem"></a>Permissões para DEM

As funções de Administrador global ou Administrador de Serviço do Intune no Azure AD são necessárias para executar tarefas de inscrição do DEM. Essas funções são também necessárias para ver todos os utilizadores DEM apesar das permissões RBAC indicadas e disponíveis na função de Utilizador personalizada. Um utilizador sem uma função de Administrador global ou Administrador de serviço do Intune atribuída, mas com permissões de leitura para a função de Gestores de Inscrição de Dispositivos, pode ver apenas os utilizadores DEM que criaram. O suporte da função RBAC para estas funcionalidades será comunicado no futuro.

Se um utilizador não tiver uma função de Administrador global ou Administrador de serviço do Intune atribuída, mas tiver permissões de leitura ativadas para a função de Gestores de Inscrição de Dispositivos atribuída ao mesmo, poderá ver apenas os utilizadores DEM que criaram.

## <a name="remove-a-device-enrollment-manager"></a>Remover um gestor de inscrição de dispositivos

A remoção de um gestor de inscrição de dispositivos não afeta os dispositivos inscritos. Quando um gestor de inscrição de dispositivos é removido:

-   Os dispositivos inscritos não são afetados e continuam a ser completamente geridos.
-   As credenciais da conta do gestor de inscrição de dispositivos removido permanecem válidas.
-   O gestor de inscrição de dispositivos removido continua sem poder apagar ou extinguir dispositivos.
-   O gestor de inscrição de dispositivos removido pode apenas inscrever um número de dispositivos até o limite por utilizador configurado pelo administrador do Intune.

**Para remover um gestor de inscrição de dispositivos**

1. No portal do Azure, escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Gestores de Inscrição de Dispositivos**.
3. No painel **Gestores de Inscrição de Dispositivos**, clique com o botão direito do rato no utilizador DEM e selecione **Remover**.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>Ver as propriedades de um gestor de inscrição de dispositivos

1. No portal do Azure, escolha **Inscrição de dispositivos** e, em seguida, **Gestores de Inscrição de Dispositivos**.
2. No painel **Gestores de Inscrição de Dispositivos**, clique com o botão direito do rato no utilizador DEM e selecione **Propriedades**.
