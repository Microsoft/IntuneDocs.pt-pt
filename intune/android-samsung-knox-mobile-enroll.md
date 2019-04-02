---
title: Inscrever automaticamente dispositivos Android com a inscrição de Mobile do Samsung Knox
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Android através do Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: arnab
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3f753b959d7b2c64358abd92f4276a8e7f55c0f6
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58798905"
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
1.  [Certifique-se de KME está disponível na sua região](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME está disponível em mais 55 países. Certifique-se de que o seu país de implementação é suportado.

2.  [Dispositivos suportados](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): KME está disponível em todos os dispositivos Samsung com um mínimo de Knox 2.4 para inscrição de dispositivos Android e um mínimo de Knox 2.8 para inscrição do Android empresarial.

3.  [Requisitos de rede](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): Certifique-se de que a firewall necessárias e as regras de acesso de rede são permitidas na sua rede.

4.  [Registre-se para uma conta de Samsung](https://www2.samsungknox.com/en/user/register): É necessária uma conta de Samsung para se registrar e habilitar KME e gerenciar todas as elegibilidades do Knox Enterprise num único local.

5.  Revisão de registo: Depois que seu perfil é concluído e submetido, Samsung executa uma revisão da aplicação e aprova-o imediatamente ou coloca-o no estado pendente de revisão para acompanhamento adicional. Após a sua conta ser aprovada, pode avançar para os passos seguintes.

## <a name="create-mdm-profile"></a>Criar um perfil MDM

Quando a sua empresa for registada com êxito, pode criar o seu perfil MDM para o Microsoft Intune no portal do Knox através das informações abaixo. Pode criar perfis MDM para Android e Android Enterprise no portal do Knox. 

### <a name="for-android-enterprise"></a>Para Android Enterprise

| Campos do Perfil MDM| Obrigatório? | Valores | 
|-------------------|-----------|-------| 
|MDM Server URI (URI do Servidor MDM)     | Não        |Deixe este campo em branco. 
|Profile Name (Nome do Perfil)       | Sim       |Introduza um nome de perfil à sua escolha. 
|Descrição        | Não        |Introduza texto que descreva o perfil. 
|MDM Agent APK (APK do Agente MDM)      | Sim       |https://aka.ms/intune_kme_deviceowner 
|Enable this app as a Google Device Owner (Ativar esta aplicação como Proprietário do Dispositivo da Google) | Sim | Selecione esta opção para inscrever-se no Android Enterprise. 
|Supported MDM (Suporte de MDM)      | Sim       |Microsoft Intune 
|Leave all system apps enabled (Manter todas as aplicações de sistema ativadas) | Não | Selecione esta opção para garantir que todas as aplicações são ativadas e estão disponíveis no perfil. Se esta opção não for selecionada, será apresentado apenas um conjunto muito limitado de aplicações de sistema na grelha de aplicações do dispositivo. As aplicações como a aplicação de E-mail permanecem ocultas. 
|Custom JSON (JSON Personalizado)        | Não        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "Introduza cadeia de token de inscrição do Intune"}. Saiba [como criar um perfil de inscrição](android-kiosk-enroll.md). 
| Add legal agreements (Adicionar contratos legais) | Não | Deixe este campo em branco. 

### <a name="for-android"></a>Para Android

Para obter orientações passo a passo, veja as instruções do [Samsung Knox Profile Setup Wizard](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) (Assistente de Configuração do Perfil do Samsung Knox).

| Campos do Perfil MDM| Obrigatório? | Valores |
|-------------------|-----------|-------|
|MDM Server URI (URI do Servidor MDM)     | Não        |Deixe este campo em branco.
|Profile Name (Nome do Perfil)       | Sim       |Introduza um nome de perfil à sua escolha.
|descrição        | Não        |Introduza texto que descreva o perfil.
|MDM Agent APK (APK do Agente MDM)      | Sim       |https://aka.ms/intune_kme
|Enable this app as a Google Device Owner (Ativar esta aplicação como Proprietário do Dispositivo da Google) | Não | Deixe esta opção desselecionada para Android. Esta aplica-se apenas ao Android Enterprise.
|Skip Setup wizard (Ignorar o Assistente de Configuração)  | Não        |Selecione esta opção para ignorar os pedidos de configuração do dispositivo padrão em nome do utilizador final.
|Allow End User to Cancel Enrollment (Permitir que o Utilizador Final Cancele a Inscrição) | Não | Selecione esta opção para permitir que os utilizadores cancelem o KME.
|Custom JSON (JSON Personalizado)        | Não        |Deixe este campo em branco.
| Add legal agreements (Adicionar contratos legais) | Não | Deixe este campo em branco.
Associate a Knox license with this profile (Associar uma licença do Knox a este perfil) | Não | Não selecione esta opção. A inscrição no Intune através do KME não precisa de uma licença do Knox.

## <a name="add-devices"></a>Adicionar dispositivos

Para atribuir Perfis MDM a dispositivos, os dispositivos Samsung Knox suportados têm de ser adicionados ao Portal do Knox através de um dos seguintes métodos:
- **Usando Reseller(s) Samsung aprovados:** Utilize este método se de que está a comprar dispositivos de um dos revendedores do Samsung aprovado. Os revendedores podem carregar automaticamente os dispositivos quando forem aprovados. [Para saber como adicionar revendedores, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Utilizar a aplicação de implementação do Knox (KDA):** Utilize este método se tiver dispositivos existentes que têm de estar inscritos através do KME. Pode utilizar Bluetooth ou NFC para adicionar dispositivos ao Portal do Knox através deste método. [Para saber como utilizar a KDA, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Atribuir um perfil MDM aos dispositivos
Antes de poder inscrever os dispositivos adicionados ao Portal do Knox, tem de lhes atribuir um perfil MDM. [Para saber mais sobre a configuração de dispositivos, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>Configurar o início de sessão dos utilizadores finais

Para os dispositivos inscritos no Intune com o KME para Android, pode configurar o início de sessão de um utilizador final da seguinte forma:

- **Sem associação de nome de utilizador:** No Portal do Knox em **detalhes do dispositivo**, deixe a **ID de utilizador** e **palavra-passe** campos em branco para os dispositivos adicionados. Esta ação precisa que o utilizador final introduza o nome de utilizador e a palavra-passe na inscrição do Intune.

- **Com a associação de nome de utilizador:** No Portal do Knox em **detalhes do dispositivo**, forneça um **ID de utilizador** (como um nome de utilizador para o utilizador atribuído ou uma [Gestor de inscrição de dispositivos](https://docs.microsoft.com/intune/device-enrollment-manager-enroll) conta) para os dispositivos adicionados. Esta ação preenche previamente o nome de utilizador e exige que o utilizador final introduza uma palavra-passe na inscrição no Intune.

> [!NOTE]
>
>A associação do utilizador aplica-se apenas à inscrição do Android. Se a associação do utilizador estiver definida, apenas o utilizador associado poderá inscrever o dispositivo através do KME. Isto acontece mesmo após uma reposição de fábrica do dispositivo. Se não estiver definida nenhuma associação do utilizador no portal do Knox, todos os utilizadores com uma licença válida do Intune poderão inscrever o dispositivo com o KME.
>

## <a name="distribute-devices"></a>Distribuir dispositivos

Após criar e atribuir um perfil MDM, associar um nome de utilizador e identificar os dispositivos como pertencentes à empresa no Intune, poderá distribuir os dispositivos pelos utilizadores.

Ainda precisa de ajuda? Veja todo o [Knox Mobile Enrollment User Guide](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm) (Guia do Utilizador do Knox Mobile Enrollment).

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

- **Suporte de proprietário do dispositivo:** O Intune suporta a inscrição de dispositivos para o modo de local público apenas com o Android enterprise. Outros modos de proprietário de dispositivos Android Enterprise serão suportados à medida que forem disponibilizados no Intune.

- **Sem suporte de perfil de trabalho:** KME é um método de inscrição de dispositivos da empresa e dispositivos inscritos no perfil de trabalho Android Certifique-se de trabalho e dados pessoais são separados em dispositivos pessoais. Por isso, a inscrição de dispositivos ao utilizar KME de perfil de trabalho não é um cenário suportado no Intune.

- **Reposição de fábrica para se inscreverem no Android enterprise:** Se a dispositivos que já foram definidos de adaptação, dispositivos têm de ser ao inscrever-se ao Android enterprise de reposição de fábrica.

- **Atualizações com a conta do Google Play:** Conta do Google Play não é necessária para a inscrição do dispositivo para o Microsoft Intune. No entanto, as atualizações futuras da aplicação Portal da Empresa do Intune poderão precisar de uma conta do Google Play no dispositivo. A conta do Google Play não é necessária ao efetuar a inscrição no Proprietário do Dispositivo Google.

- **Campo de "Password" é ignorado:** Se o **palavra-passe** campo é preenchido no **detalhes do dispositivo** no Portal do Knox, ela é ignorada pela aplicação Portal da empresa do Intune durante a inscrição de dispositivos Android. O utilizador final tem de introduzir uma palavra-passe no dispositivo para concluir a inscrição do dispositivo.


## <a name="getting-support"></a>Obter suporte
Saiba mais sobre [como obter suporte para o Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


