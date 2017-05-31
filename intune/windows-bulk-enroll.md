---
title: "Inscrição em massa para o Windows 10 | Microsoft Docs"
titleSuffix: Intune Azure preview
description: "Criar um pacote de inscrição em massa para o Microsoft Intune"
keywords: 
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.date: 03/18/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: damionw
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: f8d1ff7a9a8bd804d4fe40f8aec7e7d0bf998e35
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017

---
# <a name="bulk-enrollment-for-windows-devices"></a>Inscrição em massa para dispositivos Windows

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Como administrador, pode associar inúmeros dispositivos Windows novos ao Azure Active Directory e ao Intune. Para inscrever em massa dispositivos para o seu inquilino do Azure AD, crie um pacote de aprovisionamento com a aplicação Windows Configuration Designer (WCD). Ao aplicar o pacote de aprovisionamento aos dispositivos pertencentes à empresa, associa os dispositivos ao inquilino do Azure AD e inscreve-os na gestão do Intune. Depois de o pacote ser aplicado, estará pronto para os utilizadores do Azure AD iniciarem sessão.

Os utilizadores do Azure AD são utilizadores padrão nestes dispositivos e obtêm as aplicações necessárias e as políticas do Intune atribuídas. De momento, os cenários self-service e Portal da Empresa não são suportados.

## <a name="prerequisites-for-windows-devices-bulk-enrollment"></a>Pré-requisitos para a inscrição em massa de dispositivos Windows

A inscrição em massa de dispositivos Windows precisa do seguinte:

- Dispositivos que executem a atualização de Criativos do Windows 10 ou posterior
- [Inscrição automática no Windows](https://docs.microsoft.com/intune-classic/deploy-use/set-up-windows-device-management-with-microsoft-intune#enable-windows-10-automatic-enrollment)

## <a name="create-a-provisioning-package"></a>Criar um pacote de aprovisionamento

1. Transfira o [Windows Configuration Designer (WCD)](https://www.microsoft.com/store/apps/9nblggh4tx22) da Loja Windows.
![Captura de ecrã das capturas de ecrã e da descrição da Loja da aplicação Windows Configuration Designer](media/bulk-enroll-store.png)

2. Abra a aplicação **Windows Configuration Designer** e selecione **Aprovisionar computadores**.
![Captura de ecrã após selecionar Aprovisionar computadores na aplicação Windows Configuration Designer](media/bulk-enroll-select.png)

3. É apresentada a janela **Novo projeto**, onde pode especificar o seguinte:
  - **Nome** – um nome para o projeto
  - **Pasta do projeto** – onde o projeto será guardado
  - **Descrição** – uma descrição opcional do projeto ![Captura de ecrã após especificar o nome, a pasta do projeto e a descrição na aplicação Windows Configuration Designer](media/bulk-enroll-name.png)

4.    Introduza um nome exclusivo para os seus dispositivos. Os nomes podem incluir um número de série (%%SERIAL%%) ou um conjunto de carateres aleatório. Opcionalmente, também poderá introduzir uma chave de produto se estiver a atualizar a edição do Windows, a configurar o dispositivo para a utilização partilhada e a remover software pré-instalado.
![Captura de ecrã após especificar o nome, a pasta do projeto e a descrição na aplicação Windows Configuration Designer](media/bulk-enroll-device.png)

5.    Opcionalmente, pode configurar a rede Wi-Fi à qual os dispositivos se ligam quando são iniciados pela primeira vez.  Se esta rede não estiver configurada, precisará de uma ligação de rede com fios quando o dispositivo for iniciado pela primeira vez.
![Captura de ecrã após ativar a rede Wi-Fi, incluindo as opções de Tipo de rede e SSID de rede, na aplicação Windows Configuration Designer](media/bulk-enroll-network.png)

6.    Selecione **Inscrever no Azure AD**, introduza uma data de **Expiração do Token em Massa** e, em seguida, selecione **Obter Token em Massa**.
![Captura de ecrã após especificar o nome, a pasta do projeto e a descrição na aplicação Windows Configuration Designer](media/bulk-enroll-account.png)

7. Indique as suas credenciais do Azure AD para obter um token em massa.
![Captura de ecrã após especificar o nome, a pasta do projeto e a descrição na aplicação Windows Configuration Designer](media/bulk-enroll-cred.png)

8.    Clique em **Seguinte** quando **Token em Massa** for obtido com êxito.

9. Opcionalmente, pode **Adicionar aplicações** e **Adicionar certificados**. Estas aplicações e certificados são aprovisionados no dispositivo.

10. Opcionalmente, pode proteger o seu pacote de aprovisionamento por palavra-passe.  Clique em **Criar**.
![Captura de ecrã após especificar o nome, a pasta do projeto e a descrição na aplicação Windows Configuration Designer](media/bulk-enroll-create.png)

## <a name="provision-devices"></a>Aprovisionar dispositivos

1. Aceda ao pacote de aprovisionamento na localização especificada na **Pasta do projeto** especificada na aplicação.

2. Escolha como vai aplicar o pacote de aprovisionamento ao dispositivo.  Um pacote de aprovisionamento pode ser aplicado a um dispositivo de uma das seguintes formas:
 - Colocar o pacote de aprovisionamento numa unidade USB, inserir a unidade USB no dispositivo que pretende inscrever em massa e aplicá-lo durante a configuração inicial
 - Colocar o pacote de aprovisionamento numa pasta de rede, aplicá-la e inserir no dispositivo que pretende inscrever em massa depois da configuração inicial

 Para obter instruções passo a passo sobre a aplicação de um pacote de aprovisionamento, veja [Apply a provisioning package (Aplicar um pacote de aprovisionamento)](https://technet.microsoft.com/itpro/windows/configure/provisioning-apply-package).

3. Depois de aplicar o pacote, o dispositivo será reiniciado automaticamente dentro de um minuto.
 ![Captura de ecrã após especificar o nome, a pasta do projeto e a descrição na aplicação Windows Configuration Designer](media/bulk-enroll-add.png)

4. Quando o dispositivo for reiniciado, estabelecerá ligação ao Azure Active Directory e será inscrito no Microsoft Intune.

## <a name="troubleshooting-windows-bulk-enrollment"></a>Resolução de problemas de inscrição em massa no Windows

O aprovisionamento destina-se a ser utilizado em dispositivos Windows novos. As falhas de aprovisionamento podem precisar de uma reposição de fábrica no dispositivo ou da recuperação do dispositivo a partir de uma imagem de arranque. Estes exemplos descrevem alguns motivos para o aprovisionamento de falhas:

- Um pacote de aprovisionamento que tenta associar um domínio do Active Directory ou um inquilino do Azure Active Directory que não crie uma conta local pode tornar o dispositivo inacessível se o processo de associação ao domínio falhar devido à falta de conetividade de rede.
- Os scripts executados pelo pacote de aprovisionamento são executados no contexto do sistema e conseguem realizar alterações arbitrárias às configurações e ao sistema de ficheiros do dispositivo. Um script malicioso ou incorreto pode colocar o dispositivo num estado que só pode ser recuperado ao recriar a imagem ou através de uma reposição de fábrica do dispositivo.

