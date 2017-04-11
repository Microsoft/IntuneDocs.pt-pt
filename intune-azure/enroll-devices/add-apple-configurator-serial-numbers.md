---
title: "Adicionar números de série do Apple Configurator"
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como adicionar números de série em dispositivos iOS pertencentes à empresa com o Apple Configurator."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/15/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d408aa38-7d1e-40df-9067-246e53f6e26f
ms.reviewer: dagerrit
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: 153cce3809e24303b8f88a833e2fc7bdd9428a4a
ms.openlocfilehash: 26d253f013195cc18f9a97b8259c603d707d22bf
ms.lasthandoff: 02/18/2017


---

# <a name="add-apple-configurator-serial-numbers"></a>Adicionar números de série do Apple Configurator

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Utilize estes passos para adicionar números de série ao Intune quando pretende [inscrever dispositivos iOS da empresa ao utilizar o Apple Configurator com o Assistente de Configuração](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md). Pode adicionar números de série individualmente ou carregar um ficheiro de valores separados por vírgulas (CSV) de números de série. Depois de adicionar os números de série, pode atribuir-lhes um perfil. O perfil contém as definições de gestão específicas que quer aplicar aos dispositivos.

Para obter outros métodos para inscrever dispositivos iOS estão descritos em [Escolher como inscrever dispositivos iOS no Intune](choose-ios-enrollment-method.md).

**Para adicionar números de série do Apple Configurator ao Intune**

1. Crie uma lista de valores de duas colunas, separados por vírgulas (.csv) sem cabeçalho. Adicione o identificador IMEI na coluna da esquerda e os detalhes na coluna da direita. O máximo atual para a lista é de 500 linhas. Num editor de texto, a lista .csv tem um aspeto semelhante ao seguinte:

    F7TLWCLBX196,detalhes do serviço</br>
   DLXQPCWVGHMJ,detalhes do dispositivo

2. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

3.  No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Inscrição da Apple**.

4. Em **Gerir Definições de Inscrição do Apple Configurator**, selecione **Números de Série do Apple Configurator**.

5. No painel **Números de Série do Apple Configurator**, selecione **Adicionar**.

6. No painel **Adicionar Números de Série**, selecione um perfil para aplicar os números de série que está a importar. Se estiver a importar um ficheiro com novos detalhes que vão substituir os existentes, selecione Substituir detalhes para os identificadores existentes para que os novos detalhes substituam os detalhes existentes.

7. Navegue para o ficheiro .csv dos números de série e selecione **Adicionar**.

## <a name="assign-a-profile-to-specific-serial-numbers"></a>Atribuir um perfil a números de série específicos

O Intune permite-lhe atribuir perfis a partir de dois locais diferentes no portal do Azure. Pode utilizar os passos abaixo ou pode atribuir perfis a partir do painel Perfis de Inscrição do Apple Configurator, que é onde cria o perfil (veja [Inscrever dispositivos iOS com o Apple Configurator ao utilizar o Assistente de Configuração](enroll-ios-devices-with-apple-configurator-and-setup-assistant.md)). Poderá utilizar os passos abaixo para atribuir o perfil apenas se já tiver criado o perfil.

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.

2. No painel Intune, escolha **Inscrever dispositivos** e, em seguida, escolha **Inscrição da Apple**.

3. No painel **Números de Série do Apple Configurator**, selecione os números de série aos quais pretende atribuir um perfil e, em seguida, selecione **Atribuir Perfil**.

4. No painel **Atribuir Perfil**, selecione o perfil que pretende atribuir e, em seguida, selecione **Atribuir**.

## <a name="delete-serial-numbers"></a>Eliminar números de série
Pode eliminar os números de série que importou anteriormente. Para eliminar os números de série, primeiro tem de anular a inscrição do dispositivo. Depois de remover um número de série, não pode utilizar o Apple Configurator através do Assistente de Configuração, exceto se voltar a adicionar o número de série.

## <a name="view-the-state-of-a-device"></a>Ver o estado de um dispositivo
Os números de série do dispositivo podem ter um de dois estados:

- Inscrito – o dispositivo está inscrito e ligou-se ao serviço do Intune
- Não contactado – o dispositivo nunca se ligou ao serviço do Intune.
- Reposição Pendente – o dispositivo está inscrito, mas foi realizada uma alteração (por exemplo, as definições de inscrição ou o perfil DEP aplicado foram alterados). Se alterar o perfil DEP de um dispositivo, as alterações não serão aplicadas enquanto o dispositivo não tiver a inscrição anulada e, em seguida, voltar a ser inscrito.

**Para ver o estado de um número de série**

No painel **Números de Série do Apple Configurator**, selecione o número de série cujo estado quer ver e procure no item **Estado**.

