---
title: Integrar o Jamf Pro com o Microsoft Intune para conformidade
titleSuffix: Microsoft Intune
description: Utilize políticas de conformidade do Microsoft Intune com o Azure Active Directory condicional acesso para o ajudar a proteger os dispositivos geridos pelo Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: elocholi
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7b5d3754c7dd3ead9236e223fd568e58e96fe9a1
ms.sourcegitcommit: 4b83697de8add3b90675c576202ef2ecb49d80b2
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67045145"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrar o Jamf Pro com o Intune para conformidade

Aplica-se a: Intune no portal do Azure

Se a sua organização utiliza [Jamf Pro](https://www.jamf.com) para gerir os seus utilizadores finais Macs, pode utilizar as políticas de conformidade do Microsoft Intune com o Azure Active Directory condicional acesso para se certificar de que os dispositivos na sua organização estão em conformidade.

## <a name="prerequisites"></a>Pré-requisitos

É necessário o seguinte procedimento para configurar o acesso condicional com o Jamf Pro:

- Jamf Pro 10.1.0 ou posterior
- [Aplicação Portal da Empresa para macOS](https://aka.ms/macoscompanyportal)
- Dispositivos macOS com OS X 10.11 Yosemite ou posterior

## <a name="connecting-intune-to-jamf-pro"></a>Ligar o Intune ao Jamf Pro

Para ligar o Intune com o Jamf Pro:

1. Criar uma nova aplicação no Azure
2. Integrar o Intune com o Jamf Pro
3. Configurar o acesso condicional no Jamf Pro

## <a name="create-an-application-in-azure-active-directory"></a>Criar uma aplicação no Azure Active Directory

1. No [portal do Azure](https://portal.azure.com), aceda à **Azure Active Directory** > **registos das aplicações**e, em seguida, selecione **novo registo**. 

2. Sobre o **registar uma aplicação** , especifique os seguintes detalhes:
   - Na **Name** secção, introduza um nome significativo, por exemplo **acesso condicional do Jamf**.
   - Para o **tipos de conta suportados** secção, selecione **contas em qualquer diretório organizacional**. 
   - Para **URI de redirecionamento**, deixe a predefinição da Web e, em seguida, especifique o URL para a sua instância do Jamf Pro.  

3. Selecione **registar** para criar a aplicação e para abrir a página de descrição geral da nova aplicação.  

4. Na aplicação **descrição geral** página, copie a **ID de aplicação (cliente)** valor e registe-a para utilização posterior. Precisará desse valor em procedimentos posteriores.  

5. Selecione **certificados e segredos** sob **gerir**. Selecione o **novo segredo do cliente** botão. Introduza um valor na **Descrição**, selecione qualquer opção para **Expires** e escolha **Add**.

   > [!IMPORTANT]  
   > Antes de sair desta página, copie o valor para o segredo do cliente e registe-a para utilização posterior. Precisará esse valor em procedimentos posteriores. Este valor não está disponível novamente, sem recriar o registo de aplicações.  

6. Selecione **permissões API** em gerir.  Selecione as permissões existentes e, em seguida, selecione **remover permissão** para eliminar essas permissões. Remoção de todas as permissões existentes é necessária pois terá de adicionar uma nova permissão e o aplicativo só funciona se tiver a permissão única necessária.  

7. Para atribuir uma nova permissão, selecione **adicionar uma permissão**. Sobre o **permissões de pedido de API** página, selecione **Intune**e, em seguida, selecione **permissões de aplicação**. Selecione apenas a caixa de verificação **update_device_attributes**.  

   Selecione **adicionar permissão** para guardar esta configuração.  

8. Sobre o **permissões de API** página, selecione **conceder autorização de administrador para a Microsoft**e, em seguida, selecione Sim.  

   O processo de registo de aplicação no Azure AD foi concluído.


    > [!NOTE]
    > Se o segredo do cliente expirar, tem de criar um novo segredo de cliente no Azure e, em seguida, atualizar os dados de acesso condicional no Jamf Pro. Azure permite-lhe ter ambos os a antiga secreta e nova chave ativa para evitar interrupções ao serviço.

## <a name="enable-intune-to-integrate-with-jamf-pro"></a>Integrar o Intune com o Jamf Pro

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=20909)e aceda à **Microsoft Intune** > **conformidade de dispositivos** > **degestãodedispositivosdeparceiros**.

2. Ativar o conector de conformidade para Jamf ao colar o ID da aplicação guardada durante o procedimento anterior para o **ID de aplicação do Active Directory do Jamf Azure** campo.

3. Selecione **Guardar**.

## <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar a Integração do Microsoft Intune no Jamf Pro

1. No Jamf Pro, navegue para **Gestão Global** > **Acesso Condicional**. Clique no botão **Edit** (Editar) no separador **Microsoft Intune Integration** (Integração do Microsoft Intune).

2. Selecione a caixa de verificação **Enable Microsoft Intune Integration** (Ativar a Integração do Microsoft Intune).

3. Indique as informações necessárias sobre o seu inquilino do Azure, incluindo **localização**, **nome de domínio**, o **ID de aplicação**e o valor para o *cliente segredo* que guardou quando criou a aplicação no Azure AD.  

4. Selecione **Guardar**. O Jamf Pro testa as suas definições e verifica se o seu sucesso.

## <a name="set-up-compliance-policies-and-register-devices"></a>Definir as políticas de conformidade e registar dispositivos

Depois de configurar a integração entre o Intune e Jamf, precisa [aplicar políticas de conformidade para dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md).



## <a name="next-steps"></a>Passos Seguintes

- [Aplicar políticas de conformidade a dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md)
- [Dados Jamf envia para o Intune](data-jamf-sends-to-intune.md)
