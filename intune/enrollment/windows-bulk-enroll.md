---
title: Inscrição em massa para o Windows 10
titleSuffix: Microsoft Intune
description: Criar um pacote de inscrição em massa para o Microsoft Intune
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 5/21/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: spshumwa
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b2ce91cea1fdef211a8e6a9dc1c19086f355385
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72585281"
---
# <a name="bulk-enrollment-for-windows-devices"></a>Inscrição em massa para dispositivos Windows

Como administrador, pode associar inúmeros dispositivos Windows novos ao Azure Active Directory e ao Intune. Para inscrever em massa dispositivos para o seu inquilino do Azure AD, crie um pacote de aprovisionamento com a aplicação Windows Configuration Designer (WCD). Ao aplicar o pacote de aprovisionamento aos dispositivos pertencentes à empresa, associa os dispositivos ao inquilino do Azure AD e inscreve-os na gestão do Intune. Depois que o pacote for aplicado, ele estará pronto para os usuários do Azure AD entrarem.

Os utilizadores do Azure AD são utilizadores padrão nestes dispositivos e obtêm as aplicações necessárias e as políticas do Intune atribuídas. Os dispositivos Windows que são inscritos no Intune através da inscrição em massa do Windows podem utilizar a aplicação do Portal da Empresa para instalar as aplicações disponíveis. 

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Pré-requisitos para a inscrição em massa de dispositivos Windows

- Dispositivos que executem a atualização de Criativos do Windows 10 (compilação 1703) ou posterior
- [Inscrição automática no Windows](windows-enroll.md#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>Criar um pacote de aprovisionamento

1. Transfira o [Windows Configuration Designer (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22) na Loja Microsoft.
   ![Captura de ecrã da aplicação Windows Configuration Designer na loja](./media/windows-bulk-enroll/bulk-enroll-store.png)

2. Abra a aplicação **Windows Configuration Designer** e selecione **Aprovisionar computadores**.
   ![Captura de ecrã após selecionar Aprovisionar computadores na aplicação Windows Configuration Designer](./media/windows-bulk-enroll/bulk-enroll-select.png)

3. É apresentada a janela **Novo projeto**, onde pode especificar as seguintes informações:
   - **Nome** – um nome para o projeto
   - **Pasta do projeto** – guardar a localização do projeto
   - **Descrição** – uma descrição opcional do projeto ![Captura de ecrã após especificar o nome, a pasta do projeto e a descrição na aplicação Windows Configuration Designer](./media/windows-bulk-enroll/bulk-enroll-name.png)

4. Introduza um nome exclusivo para os seus dispositivos. Os nomes podem incluir um número de série (%SERIAL%) ou um conjunto de carateres aleatório. Opcionalmente, também poderá introduzir uma chave de produto se estiver a atualizar a edição do Windows, a configurar o dispositivo para a utilização partilhada e a remover software pré-instalado.
   
   ![Captura de ecrã após especificar o nome e a chave de produto na aplicação Windows Configuration Designer](./media/windows-bulk-enroll/bulk-enroll-device.png)

5. Opcionalmente, pode configurar a rede Wi-Fi à qual os dispositivos se ligam quando são iniciados pela primeira vez.  Se os dispositivos de rede não estiverem configurados, precisará de uma ligação de rede com fios quando o dispositivo for iniciado pela primeira vez.
   ![Captura de ecrã após ativar a rede Wi-Fi, incluindo as opções de Tipo de rede e SSID de rede, na aplicação Windows Configuration Designer](./media/windows-bulk-enroll/bulk-enroll-network.png)

6. Selecione **Inscrever no Azure AD**, introduza uma data de **Expiração do Token em Massa** e, em seguida, selecione **Obter Token em Massa**.
   ![Captura de ecrã da gestão de conta na aplicação Windows Configuration Designer](./media/windows-bulk-enroll/bulk-enroll-account.png)

7. Indique as suas credenciais do Azure AD para obter um token em massa.
   ![Captura do início de sessão na aplicação Windows Configuration Designer](./media/windows-bulk-enroll/bulk-enroll-cred.png)

8. Clique em **Seguinte** quando **Token em Massa** for obtido com êxito.

9. Opcionalmente, pode **Adicionar aplicações** e **Adicionar certificados**. Estas aplicações e certificados são aprovisionados no dispositivo.

10. Opcionalmente, pode proteger o seu pacote de aprovisionamento por palavra-passe.  Clique em **Criar**.
    ![Captura da proteção do pacote na aplicação Windows Configuration Designer](./media/windows-bulk-enroll/bulk-enroll-create.png)

## <a name="provision-devices"></a>Aprovisionar dispositivos

1. Aceda ao pacote de aprovisionamento na localização especificada na **Pasta do projeto** especificada na aplicação.

2. Escolha como vai aplicar o pacote de aprovisionamento ao dispositivo.  Um pacote de aprovisionamento pode ser aplicado a um dispositivo de uma das seguintes formas:
   - Colocar o pacote de aprovisionamento numa unidade USB, inserir a unidade USB no dispositivo que pretende inscrever em massa e aplicá-lo durante a configuração inicial
   - Coloque o pacote de provisionamento em uma pasta de rede e aplique-o após a instalação inicial

   Para obter instruções passo a passo sobre a aplicação de um pacote de aprovisionamento, veja [Apply a provisioning package (Aplicar um pacote de aprovisionamento)](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package).

3. Depois de aplicar o pacote, o dispositivo será reiniciado automaticamente dentro de um minuto.
   ![Captura de ecrã após especificar o nome, a pasta do projeto e a descrição na aplicação Windows Configuration Designer](./media/windows-bulk-enroll/bulk-enroll-add.png)

4. Quando o dispositivo for reiniciado, estabelecerá ligação ao Azure Active Directory e será inscrito no Microsoft Intune.

## <a name="troubleshooting-windows-bulk-enrollment"></a>Resolução de problemas de inscrição em massa no Windows

### <a name="provisioning-issues"></a>Problemas de aprovisionamento
O aprovisionamento destina-se a ser utilizado em dispositivos Windows novos. As falhas de aprovisionamento podem exigir que o dispositivo seja apagado ou recuperado a partir de uma imagem de arranque. Estes exemplos descrevem alguns motivos para o aprovisionamento de falhas:

- Um pacote de aprovisionamento que tenta associar um domínio do Active Directory ou um inquilino do Azure Active Directory que não crie uma conta local pode tornar o dispositivo inacessível se o processo de associação ao domínio falhar devido à falta de conetividade de rede.
- Os scripts executados pelo pacote de aprovisionamento são executados no contexto do sistema. Os scripts conseguem realizar alterações arbitrárias às configurações e ao sistema de ficheiros do dispositivo. Um script malicioso ou incorreto pode colocar o dispositivo num estado que só pode ser recuperado ao recriar a imagem ou limpar o dispositivo.

Você pode verificar o êxito/falha das configurações em seu pacote no log do administrador de **provisionamento-Diagnostics-Provider** no Visualizador de eventos.

### <a name="bulk-enrollment-with-wi-fi"></a>Inscrição em massa por Wi-Fi 

Os dispositivos inscritos em massa não podem utilizar certificados direcionados ao utilizador e a implementação por Wi-Fi. Terá de utilizar [certificados ao nível do dispositivo](../protect/certificates-configure.md) para gerir estas ligações. 

### <a name="conditional-access"></a>Conditional Access
O acesso condicional não está disponível para dispositivos Windows registrados usando o registro em massa.
