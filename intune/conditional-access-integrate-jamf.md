---
title: Integrar o Jamf Pro com o Microsoft Intune para conformidade | Microsoft Intune
description: Utilize as políticas de conformidade do Microsoft Intune com o acesso condicional do Azure Active Directory para ajudar a proteger os dispositivos geridos pelo Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/16/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 27f8f80aca1a8517864d375f75b6829d325740ce
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57399213"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrar o Jamf Pro com o Intune para conformidade

Aplica-se a: Intune no portal do Azure

Se a sua organização utiliza [Jamf Pro](https://www.jamf.com) para gerir os seus utilizadores finais Macs, pode utilizar as políticas de conformidade do Microsoft Intune com o acesso condicional do Azure Active Directory para garantir que os dispositivos na sua organização estão em conformidade.

## <a name="prerequisites"></a>Pré-requisitos

É preciso o seguinte para configurar o acesso condicional com o Jamf Pro:

- Jamf Pro 10.1.0 ou posterior
- [Aplicação Portal da Empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS com OS X 10.11 Yosemite ou posterior

## <a name="connecting-intune-to-jamf-pro"></a>Ligar o Intune ao Jamf Pro

Para ligar o Intune com o Jamf Pro:

1. Criar uma nova aplicação no Azure
2. Integrar o Intune com o Jamf Pro
3. Configurar o acesso condicional no Jamf Pro

## <a name="create-an-application-in-azure-active-directory"></a>Criar uma aplicação no Azure Active Directory

1. Na [portal do Azure](https://portal.azure.com), aceda à **Azure Active Directory** > **registos das aplicações**.
2. Selecione **+ novo registo de aplicação**.
3. Introduza um **nome a apresentar**, tal como **Acesso Condicional do Jamf**.
4. Selecione **aplicação Web / API**.
5. Especifique o **URL de Início de Sessão** com o seu URL de instância do Jamf Pro.
6. Selecione **Criar**. A aplicação é criada e o portal apresenta os detalhes da aplicação.
7. Guardar uma cópia da **ID da aplicação** para a nova aplicação. Especifique este ID num procedimento posterior. Em seguida, selecione **configurações** e aceda à **acesso à API** > **chaves**.
8. Na *chaves* painel, especifique um **Descrição**, o tempo de espera antes de ele **Expires**e, em seguida, selecione **guardar** para gerar a aplicação Chave (valor).

   > [!IMPORTANT]
   > A Chave da Aplicação só é apresentada uma vez durante este processo. Lembre-se de a guardar num local de fácil acesso.

8. Sobre o *definições* painel para a aplicação, navegue para **acesso à API** > **permissões obrigatórias**. Selecione quaisquer permissões existentes e, em seguida, clique em **eliminar** e elimine todas as permissões. A eliminar permissões existentes que é necessária, uma vez que adiciona uma nova permissão e o aplicativo só funciona se tiver a permissão única necessária.  
9. Para atribuir uma nova permissão, selecione **+ adicionar** > **selecionar uma API** > **API do Microsoft Intune**e, em seguida, clique em **selecione**.
10. Sobre o *ativar o acesso ao* painel, selecione **enviar atributos do dispositivo para o Microsoft Intune** e, em seguida, clique em **selecione**e, em seguida **feito**.
11. Sobre o *permissões obrigatórias* painel, selecione **conceder permissões** e, em seguida **Sim** para aplicar as permissões necessárias para a aplicação.

    > [!NOTE]
    > Se a Chave da Aplicação expirar, terá de criar uma nova Chave da Aplicação no Microsoft Azure e, em seguida, atualizar os dados do Acesso Condicional no Jamf Pro. O Azure permite-lhe ter a chave antiga e a nova chave ativas para evitar interrupções ao serviço.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Integrar o Intune com o Jamf Pro

1. Na [portal do Azure](https://portal.azure.com), aceda à **Microsoft Intune** > **conformidade do dispositivo** > **degestãodedispositivosdeparceiros**.
2. Ativar o conector de conformidade para Jamf ao colar o ID da aplicação guardada durante o procedimento anterior para o **ID de aplicação do Active Directory do Jamf Azure** campo.
3. Selecione **Guardar**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar a Integração do Microsoft Intune no Jamf Pro

1. No Jamf Pro, navegue para **Gestão Global** > **Acesso Condicional**. Clique no botão **Edit** (Editar) no separador **Microsoft Intune Integration** (Integração do Microsoft Intune).
2. Selecione a caixa de verificação **Enable Microsoft Intune Integration** (Ativar a Integração do Microsoft Intune).
3. Indique as informações necessárias sobre o seu inquilino do Azure, incluindo a **Localização**, o **Nome de domínio**, bem como o **ID da Aplicação** e a **Chave da Aplicação** que guardou dos passos anteriores.
4. Selecione **Guardar**. Jamf Pro testa as suas definições e verificar o seu êxito.

## <a name="set-up-compliance-policies-and-register-devices"></a>Definir as políticas de conformidade e registar dispositivos

Depois de configurar a integração entre o Intune e Jamf, precisa [aplicar políticas de conformidade para dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md).



## <a name="next-steps"></a>Passos Seguintes

- [Aplicar políticas de conformidade a dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md)
- [Dados Jamf envia para o Intune](data-jamf-sends-to-intune.md)
