---
title: Registrar dispositivos Android automaticamente usando o registro móvel Knox da Samsung
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Android através do Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: enrollment
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 30df0f9e-6e9e-4d75-a722-3819e33d480d
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5f290370dd6ec05677a7073d9ca3edd854c9aa5e
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72505581"
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


Uma lista de identificadores de dispositivo (números de série e IMEIs) é adicionada automaticamente ao portal do Knox ao comprar dispositivos de revendedores autorizados que participam do programa de implantação do Knox.


## <a name="prerequisites"></a>Pré-requisitos

Para se inscrever no Intune através do KME, primeiro tem de registar a sua empresa no portal do Samsung Knox ao seguir estes passos:
1. [Verifique se o KME está disponível em seu país/região](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries): KME está disponível em mais de 55 países/regiões. Verifique se há suporte para seu país/região de implantação.

2. [Dispositivos suportados](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): o KME está disponível em todos os dispositivos Samsung com o Knox 2.4 ou superior para inscrição do Android e com o Knox 2.8 ou superior para inscrição do Android Enterprise.

3. [Requisitos de rede](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): certifique-se de que as regras de acesso de rede e firewall necessárias são permitidas na sua rede.

4. [Registo de uma conta Samsung](https://www2.samsungknox.com/en/user/register): é necessária uma conta Samsung para registar e ativar o KME e gerir todas as elegibilidades da Knox Enterprise num único local.

5. Revisão do registro: depois que seu perfil for concluído e enviado, o Samsung revisará seu aplicativo e o aprovará imediatamente ou o colocará em um status de revisão pendente para acompanhamento posterior. Depois que sua conta for aprovada, você poderá continuar em etapas adicionais.

## <a name="create-mdm-profile"></a>Criar um perfil MDM

Quando a sua empresa for registada com êxito, pode criar o seu perfil MDM para o Microsoft Intune no portal do Knox através das informações abaixo. Pode criar perfis MDM para Android e Android Enterprise no portal do Knox. 

### <a name="for-android-enterprise"></a>Para Android Enterprise

| Campos do Perfil MDM| Obrigatório? | Os | 
|-------------------|-----------|-------| 
|MDM Server URI (URI do Servidor MDM)     | Não        |Deixe este campo em branco. 
|Profile Name (Nome do Perfil)       | Sim       |Introduza um nome de perfil à sua escolha. 
|Description        | Não        |Introduza texto que descreva o perfil. 
|MDM Agent APK (APK do Agente MDM)      | Sim       |https://aka.ms/intune_kme_deviceowner 
|Enable this app as a Google Device Owner (Ativar esta aplicação como Proprietário do Dispositivo da Google) | Sim | Selecione esta opção para inscrever-se no Android Enterprise. 
|Supported MDM (Suporte de MDM)      | Sim       |Microsoft Intune 
|Leave all system apps enabled (Manter todas as aplicações de sistema ativadas) | Não | Selecione esta opção para garantir que todas as aplicações são ativadas e estão disponíveis no perfil. Se essa opção não estiver selecionada, apenas um conjunto limitado de aplicativos do sistema será exibido na bandeja de aplicativos do dispositivo. As aplicações como a aplicação de E-mail permanecem ocultas. 
|Custom JSON (JSON Personalizado)        | Não        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "Introduzir cadeia do token de inscrição do Intune"}. Saiba [como criar um perfil de inscrição](android-kiosk-enroll.md). 
| Add legal agreements (Adicionar contratos legais) | Não | Deixe este campo em branco. 

### <a name="for-android"></a>Para Android

Para obter orientações passo a passo, consulte as instruções do [Assistente de configuração de perfil do Samsung Knox](https://docs.samsungknox.com/KME-Getting-Started/Content/getting-started-wizard.htm) .

| Campos do Perfil MDM| Obrigatório? | Os |
|-------------------|-----------|-------|
|MDM Server URI (URI do Servidor MDM)     | Não        |Deixe este campo em branco.
|Profile Name (Nome do Perfil)       | Sim       |Introduza um nome de perfil à sua escolha.
|descrição        | Não        |Introduza texto que descreva o perfil.
|MDM Agent APK (APK do Agente MDM)      | Sim       |https://aka.ms/intune_kme
|Enable this app as a Google Device Owner (Ativar esta aplicação como Proprietário do Dispositivo da Google) | Não | Deixe esta opção desselecionada para Android. Essa opção se aplica somente ao Android Enterprise.
|Skip Setup wizard (Ignorar o Assistente de Configuração)  | Não        |Escolha esta opção para ignorar os prompts de instalação do dispositivo padrão para o usuário final.
|Allow End User to Cancel Enrollment (Permitir que o Utilizador Final Cancele a Inscrição) | Não | Selecione esta opção para permitir que os utilizadores cancelem o KME.
|Custom JSON (JSON Personalizado)        | Não        |Deixe este campo em branco.
| Add legal agreements (Adicionar contratos legais) | Não | Deixe este campo em branco.
Associate a Knox license with this profile (Associar uma licença do Knox a este perfil) | Não | Não selecione esta opção. O registro no Intune usando o KME não requer uma licença do Knox.

## <a name="add-devices"></a>Adicionar dispositivos

Para atribuir Perfis MDM a dispositivos, os dispositivos Samsung Knox suportados têm de ser adicionados ao Portal do Knox através de um dos seguintes métodos:
- **Usando revendedores (s) aprovados pelo Samsung:** Use esse método se você estiver comprando dispositivos de um dos revendedores aprovados pela Samsung. Os revendedores podem carregar automaticamente os dispositivos quando forem aprovados. [Para saber como adicionar revendedores, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Utilizar a Aplicação Knox Deployment (KDA):** utilize este método se tiver dispositivos existentes que precisam de ser inscritos através do KME. Pode utilizar Bluetooth ou NFC para adicionar dispositivos ao Portal do Knox através deste método. [Para saber como utilizar a KDA, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Atribuir um perfil MDM aos dispositivos
Antes de poder inscrever os dispositivos adicionados ao Portal do Knox, tem de lhes atribuir um perfil MDM. [Para saber mais sobre a configuração de dispositivos, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>Configurar o início de sessão dos utilizadores finais

Para os dispositivos inscritos no Intune com o KME para Android, pode configurar o início de sessão de um utilizador final da seguinte forma:

- **Sem a associação do nome de utilizador:** no Portal do Knox, em **Device details** (Detalhes do dispositivo), deixe os campos **User ID** (ID do Utilizador) e **Password** (Palavra-passe) em branco para os dispositivos adicionados. Essa opção requer que o usuário final Insira o nome de usuário e a senha ao registrar no Intune.

- **Com a associação do nome de utilizador:** no Portal do Knox, em **Device details** (Detalhes do dispositivo), forneça um **User ID** (ID do Utilizador), como um nome de utilizador para o utilizador atribuído ou uma conta do [Gestor de Inscrição de Dispositivos](device-enrollment-manager-enroll.md), para os dispositivos adicionados. Esta opção popula o nome de usuário e exige que o usuário final Insira uma senha ao registrar no Intune.

> [!NOTE]
>
>A associação de usuário só se aplica ao registro de administrador do dispositivo Android. Se a associação do utilizador estiver definida, apenas o utilizador associado poderá inscrever o dispositivo através do KME. Isto acontece mesmo após uma reposição de fábrica do dispositivo. Se não estiver definida nenhuma associação do utilizador no portal do Knox, todos os utilizadores com uma licença válida do Intune poderão inscrever o dispositivo com o KME.
>Para dispositivos Android Enterprise totalmente gerenciados, mesmo que a associação de usuário seja definida, ela não será passada para o dispositivo nem vinculará o dispositivo ao usuário.
>

## <a name="distribute-devices"></a>Distribuir dispositivos

Após criar e atribuir um perfil MDM, associar um nome de utilizador e identificar os dispositivos como pertencentes à empresa no Intune, poderá distribuir os dispositivos pelos utilizadores.

Ainda precisa de ajuda? Confira o [Guia do usuário do KME](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm)completo.

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

- **Suporte ao proprietário do dispositivo:** **suporte ao proprietário do dispositivo**  - : o Intune dá suporte ao registro de dispositivos dedicados e totalmente gerenciados usando o portal do KME. Outros modos de proprietário de dispositivos Android Enterprise serão suportados à medida que forem disponibilizados no Intune.

- **Nenhum suporte de perfil de trabalho:** O KME é um método de registro de dispositivo corporativo e os dispositivos registrados no perfil de trabalho do Android garantem que os dados pessoais e de trabalho sejam separados em dispositivos pessoais. Portanto, o registro de dispositivo para o perfil de trabalho usando KME não é um cenário com suporte no Intune.

- **Reposição de fábrica para inscrição no Android Enterprise:** se reutilizar dispositivos que já foram configurados, tem de efetuar a reposição de fábrica dos mesmos ao inscrever-se no Android Enterprise.

- **Atualizações usando a conta de Google Play:** Google Play conta não é necessária para registrar o dispositivo no Microsoft Intune. Mas, para registros de administrador do dispositivo Android, atualizações futuras para o aplicativo Portal da Empresa do Intune podem exigir uma conta de Google Play no dispositivo. Google Play conta não é necessária ao registrar-se no proprietário do dispositivo Google.

- O **campo "senha" é ignorado:** Se o campo de **senha** for preenchido nos **detalhes do dispositivo** no portal do Knox, ele será ignorado pelo aplicativo portal da empresa do Intune durante o registro do Android. O utilizador final tem de introduzir uma palavra-passe no dispositivo para concluir a inscrição do dispositivo.


## <a name="getting-support"></a>Obter suporte
Saiba mais sobre [como obter suporte para o Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).

