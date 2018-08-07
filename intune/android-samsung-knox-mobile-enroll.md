---
title: Inscrever automaticamente dispositivos Android através do Samsung Knox Mobile Enrollment
titlesuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Android através do Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 05/08/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0ada3be91c3b2c15e33e51449678212286362dbf
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321191"
---
# <a name="automatically-enroll-android-devices-by-using-samsungs-knox-mobile-enrollment"></a>Inscrever automaticamente dispositivos Android através do Samsung Knox Mobile Enrollment

Este tópico ajuda-o a configurar o Intune para inscrever dispositivos Android suportados através do Samsung Knox Mobile Enrollment (KME). Ao utilizar o Intune com o Samsung KME, pode inscrever um grande número de dispositivos Android pertencentes à empresa quando os utilizadores finais ativarem os respetivos dispositivos pela primeira vez e se ligarem a uma rede móvel ou Wi-Fi. Além disso, os dispositivos podem ser inscritos com a Aplicação Knox Deployment através de Bluetooth ou NFC.

Para ativar a inscrição do Intune com o Samsung KME, utilize o portal do Intune e o portal do Samsung Knox por esta ordem:

1. No portal do Knox:
    1. [Crie um perfil MDM](#create-mdm-profile)
    2. [Adicione dispositivos](#add-devices)
    3. [Atribua um perfil MDM aos dispositivos](#assign-an-mdm-profile-to-devices)
2. No portal do Knox, [configure o início de sessão de utilizador final](#configure-how-end-users-sign-in).
3. [Distribua os dispositivos](#distribute-devices).


Será adicionada automaticamente uma lista de identificadores de dispositivos (números de série e IMEIs) ao portal do Knox quando comprar os dispositivos a revendedores autorizados que participem no Knox Deployment Program.


## <a name="prerequisites"></a>Pré-requisitos

Para se inscrever no Intune através do KME, primeiro tem de registar a sua empresa no portal do Samsung Knox ao seguir estes passos:
1.  [Certifique-se de que o KME está disponível na sua região](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): o KME está disponível em mais de 55 países. Certifique-se de que o seu país de implementação é suportado.

2.  [Dispositivos suportados](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): o KME está disponível em todos os dispositivos Samsung com o Knox 2.4 ou superior.

3.  [Requisitos de rede](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): certifique-se de que as regras de acesso de rede e firewall necessárias são permitidas na sua rede.

4.  [Registo de uma conta Samsung](https://www2.samsungknox.com/en/user/register): é necessária uma conta Samsung para registar e ativar o KME e gerir todas as elegibilidades da Knox Enterprise num único local.

5.  Revisão do Registo: após concluir e submeter o seu perfil, a Samsung irá rever a sua aplicação. A aplicação será aprovada automaticamente ou colocada num estado de revisão pendente para mais seguimento. Após a sua conta ser aprovada, pode avançar para os passos seguintes.

## <a name="create-mdm-profile"></a>Criar um perfil MDM

Quando a sua empresa for registada com êxito, pode criar o seu perfil MDM para o Microsoft Intune no Portal do Knox através das informações abaixo. Para obter orientações passo a passo, veja as instruções do [Samsung Knox Profile Setup Wizard](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) (Assistente de Configuração do Perfil do Samsung Knox).

| Campos do Perfil MDM| Obrigatório? | Valores |
|-------------------|-----------|-------|
|MDM Server URI (URI do Servidor MDM)     | Não        |Deixe este campo em branco.
|Profile Name (Nome do Perfil)       | Sim       |Introduza um nome de perfil à sua escolha.
|descrição        | Não        |Introduza texto que descreva o perfil.
|MDM Agent APK (APK do Agente MDM)      | Sim       |https://aka.ms/intune_kme
|Skip Setup wizard (Ignorar o Assistente de Configuração)  | Não        |Selecione esta opção para ignorar os pedidos de configuração do dispositivo padrão em nome do utilizador final.
|Allow End User to Cancel Enrollment (Permitir que o Utilizador Final Cancele a Inscrição) | Não | Selecione esta opção para permitir que os utilizadores cancelem o KME.
|Custom JSON (JSON Personalizado)        | Não        |Deixe este campo em branco.
| EULAs, Terms of Service & User Agreements (EULAs, Termos do Serviço e Contratos do Utilizador)| Não | Selecione esta opção para apresentar os contratos relacionados com o Knox para aceitação do utilizador.
Associate a Knox license with this profile (Associar uma licença do Knox a este perfil) | Não | Não selecione esta opção. A inscrição no Intune através do KME não precisa de uma licença do Knox.

## <a name="add-devices"></a>Adicionar dispositivos

Para atribuir Perfis MDM a dispositivos, os dispositivos Samsung Knox suportados têm de ser adicionados ao Portal do Knox através de um dos seguintes métodos:
- **Utilizar Revendedores Aprovados da Samsung:** utilize este método se estiver a comprar dispositivos a um dos revendedores aprovados da Samsung. Os revendedores podem carregar automaticamente os dispositivos quando forem aprovados. [Para saber como adicionar revendedores, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Utilizar a Aplicação Knox Deployment (KDA):** utilize este método se tiver dispositivos existentes que precisam de ser inscritos através do KME. Pode utilizar Bluetooth ou NFC para adicionar dispositivos ao Portal do Knox através deste método. [Para saber como utilizar a KDA, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Atribuir um perfil MDM aos dispositivos
Antes de poder inscrever os dispositivos adicionados ao Portal do Knox, tem de lhes atribuir um perfil MDM. [Para saber mais sobre a configuração de dispositivos, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>Configurar o início de sessão dos utilizadores finais

Para os dispositivos inscritos no Intune com o KME, pode configurar o início de sessão de um utilizador final da seguinte forma:

- **Sem a associação do nome de utilizador:** no Portal do Knox, em **Device details** (Detalhes do dispositivo), deixe os campos **User ID** (ID do Utilizador) e **Password** (Palavra-passe) em branco para os dispositivos adicionados. Esta ação precisa que o utilizador final introduza o nome de utilizador e a palavra-passe na inscrição do Intune.

- **Com a associação do nome de utilizador:** no Portal do Knox, em **Device details** (Detalhes do dispositivo), forneça um **User ID** (ID do Utilizador), como um nome de utilizador para o utilizador atribuído ou uma conta do [Gestor de Inscrição de Dispositivos](https://docs.microsoft.com/en-us/intune/device-enrollment-manager-enroll), para os dispositivos adicionados. Esta ação preenche previamente o nome de utilizador e exige que o utilizador final introduza uma palavra-passe na inscrição no Intune.

> [!NOTE]
>
>Se a associação do utilizador estiver definida, apenas o utilizador associado poderá inscrever o dispositivo através do KME. Isto acontece mesmo após uma reposição de fábrica do dispositivo. Se não estiver definida nenhuma associação do utilizador no Portal do Knox, todos os utilizadores com uma licença válida do Intune poderão inscrever o dispositivo com o KME.
>

## <a name="distribute-devices"></a>Distribuir dispositivos

Após criar e atribuir um perfil MDM, associar um nome de utilizador e identificar os dispositivos como pertencentes à empresa no Intune, poderá distribuir os dispositivos pelos utilizadores.

Ainda precisa de ajuda? Veja todo o [Knox Mobile Enrollment User Guide](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm) (Guia do Utilizador do Knox Mobile Enrollment).

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes
- **Conta do Google Play:** não é necessária uma conta do Google Play para inscrever o dispositivo no Microsoft Intune. No entanto, as atualizações futuras da aplicação Portal da Empresa do Intune poderão precisar de uma conta do Google Play no dispositivo.

- **Modo de Proprietário do Dispositivo da Google:** a inscrição no modo de Proprietário do Dispositivo da Google através do KME não é suportada nesta Pré-visualização. Este cenário está atualmente a ser investigado.

- **O campo "Password" (Palavra-passe) é ignorado:** se o campo **Password** (Palavra-passe) for preenchido em **Device details** (Detalhes do dispositivo) no Portal do Knox, será ignorado pela aplicação Portal da Empresa do Intune. O utilizador final tem de introduzir uma palavra-passe no dispositivo para concluir a inscrição do dispositivo.

- **Inscrição do Android Empresarial:** o KME não suporta a Inscrição do Android Empresarial.

## <a name="getting-support"></a>Obter suporte
Saiba mais sobre [como obter suporte para o Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


