---
title: "Inscrever dispositivos – gestor de inscrição de dispositivos"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: utilize a conta do gestor de inscrição de dispositivos para inscrever dispositivos no Intune. "
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 7196b33e-d303-4415-ad0b-2ecdb14230fd
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: b4629d98f935ab2fac95144940e2a58a1b1e7c5c
ms.lasthandoff: 02/18/2017

---

# <a name="enroll-devices-using-device-enrollment-manager"></a>Inscrever dispositivos com o gestor de inscrição de dispositivos

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador. A conta do *gestor de inscrição de dispositivos* (DEM) é uma conta de utilizador especial que pode inscrever até 1000 dispositivos. Pode adicionar utilizadores existentes à conta DEM de forma a conceder-lhes capacidades especiais de DEM. Cada dispositivo inscrito utiliza uma única licença. Recomendamos que utilize os dispositivos inscritos através desta conta como dispositivos partilhados em vez de dispositivos pessoais (“BYOD”).  

Têm de existir utilizadores no portal do Azure para serem adicionados como gestores de inscrição de dispositivos. Para garantir a segurança, o utilizador DEM não deve ser também um administrador do Intune.

>[!NOTE]
>O método de inscrição DEM não pode ser utilizado com estes métodos de inscrição: [Apple Configurator com o Assistente de Configuração](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md), [Apple Configurator com inscrição direta](enroll-ios-devices-with-apple-configurator-and-direct-enrollment.md) ou [programa de registo de aparelho](enroll-ios-devices-using-device-enrollment-program.md). 

## <a name="example-of-a-device-enrollment-manager-scenario"></a>Exemplo de um cenário do gestor de inscrição de dispositivos

Um restaurante quer fornecer 50 tablets de ponto de venda aos seus empregados de mesa e monitores de apresentação de pedidos para os empregados da cozinha. Os funcionários não precisam nunca de aceder aos dados da empresa nem de iniciar sessão como utilizadores. O administrador do Intune cria uma conta de gestor de inscrição de dispositivos e adiciona um supervisor de restaurante à conta DEM, concedendo assim capacidades de DEM a esse supervisor. Agora, o supervisor pode inscrever os 50 tablets com as credenciais de DEM.

Apenas os utilizadores da consola do Intune podem ser gestores de inscrição de dispositivos. O utilizador do gestor de inscrição de dispositivos não pode ser um administrador do Intune.

O utilizador DEM pode:

-   Inscrever até 1000 dispositivos no Intune.
-   Iniciar sessão no Portal da Empresa para obter aplicações da empresa.
-   Configurar o acesso aos dados da empresa ao implementar aplicações específicas de funções nos tablets.

## <a name="limitations-of-devices-that-are-enrolled-with-a-dem-account"></a>Limitações dos dispositivos inscritos com uma conta DEM

Os dispositivos inscritos com uma conta de gestor de inscrição de dispositivos têm as seguintes limitações:

  - Não há nenhum "utilizador" de dispositivo específico. Por conseguinte, não existe acesso aos dados da empresa ou ao e-mail. No entanto, a VPN, por exemplo, poderá continuar a ser utilizada para fornecer aplicações de dispositivos com acesso a dados.

  - Não há acesso condicional, porque estes cenários são por utilizador.

  - O utilizador DEM não pode utilizar o Portal da Empresa para anular a inscrição de dispositivos inscritos para DEM no próprio dispositivo. O administrador do Intune tem esta capacidade, mas o utilizador DEM não a tem.

  - Apenas o dispositivo local é apresentado na aplicação Portal da Empresa ou do site.
 
  - Os utilizadores não podem utilizar aplicações Apple Volume Purchase Program (VPP) devido aos requisitos do Apple ID por utilizador para a gestão de aplicações.
 
  - (Apenas para iOS) Se utiliza DEM para inscrever dispositivos iOS, não pode utilizar o Apple Configurator nem o Programa de Inscrição de Dispositivos Apple (DEP) para inscrever dispositivos.


> [!NOTE]
> Para implementar aplicações da empresa em dispositivos geridos com o gestor de inscrição de dispositivos, implemente a aplicação Portal da Empresa como uma **Instalação Obrigatória** na conta de utilizador do gestor de inscrição de dispositivos.
> Para melhorar o desempenho, a aplicação Portal da Empresa num dispositivo DEM apresenta apenas os dispositivos locais. A gestão remota de outros dispositivos DEM só pode ser efetuada a partir da consola de administração do Intune.


## <a name="add-a-device-enrollment-manager"></a>Adicionar um gestor de inscrição de dispositivos

1.  No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2.  No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Gestores de Inscrição de Dispositivos**.

3.  Selecione **Adicionar**.

4.  No painel **Adicionar Utilizador**, introduza um nome principal para o utilizador DEM e selecione **Adicionar**. O utilizador DEM é adicionado à lista de utilizadores DEM.

## <a name="remove-a-device-enrollment-manager"></a>Remover um gestor de inscrição de dispositivos

A remoção de um gestor de inscrição de dispositivos não afeta os dispositivos inscritos. Quando um gestor de inscrição de dispositivos é removido:

-   Remover um utilizador da lista de utilizadores DEM não afeta os dispositivos inscritos e estes continuam a ser completamente geridos.

-   As credenciais da conta do gestor de inscrição de dispositivos removido permanecem válidas.

-   O gestor de inscrição de dispositivos removido continua sem poder apagar ou extinguir dispositivos.

-   O gestor de inscrição de dispositivos removido não pode inscrever mais dispositivos, a menos que o limite por dispositivo, configurado pelo administrador do Intune, não tenha sido atingido.

**Para remover um gestor de inscrição de dispositivos**

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Gestores de Inscrição de Dispositivos**.

3. No painel **Gestores de Inscrição de Dispositivos**, clique com o botão direito do rato no utilizador DEM e selecione **Remover**.

## <a name="view-the-properties-of-a-device-enrollment-manager"></a>Ver as propriedades de um gestor de inscrição de dispositivos

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Gestores de Inscrição de Dispositivos**.

3. No painel **Gestores de Inscrição de Dispositivos**, clique com o botão direito do rato no utilizador DEM e selecione **Propriedades**.

