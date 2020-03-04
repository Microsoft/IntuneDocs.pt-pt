---
title: Inscrever automaticamente dispositivos Android com a inscrição de Mobile do Samsung Knox
titleSuffix: Microsoft Intune
description: Saiba como inscrever dispositivos Android através do Samsung KME
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: ''
ms.date: 03/03/2020
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
ms.openlocfilehash: ae445597cfd1afc4650c7a900ee335c939adedce
ms.sourcegitcommit: 6608dc70d01376e0cd90aa620a2fe01337f6a2f1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78260185"
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


Uma lista de identificadores de dispositivos (números de série e IMEIs) é adicionada automaticamente ao Portal Knox ao adquirir dispositivos de revendedores autorizados que participam no Programa de Implementação knox.


## <a name="prerequisites"></a>Pré-requisitos

Para se inscrever no Intune através do KME, primeiro tem de registar a sua empresa no portal do Samsung Knox ao seguir estes passos:
1. [Certifique-se de que o KME está disponível no seu país/região:](https://www.samsungknox.com/en/solutions/it-solutions/knox-configure/available-countries)O KME está disponível em mais de 55 países/regiões. Certifique-se de que o seu país/região de implantação é apoiado.

2. [Dispositivos suportados](https://www.samsungknox.com/en/knox-platform/supported-devices/2.4+): o KME está disponível em todos os dispositivos Samsung com o Knox 2.4 ou superior para inscrição do Android e com o Knox 2.8 ou superior para inscrição do Android Enterprise.

3. [Requisitos de rede](https://docs.samsungknox.com/KME-Getting-Started/Content/firewall_exceptions.htm): certifique-se de que as regras de acesso de rede e firewall necessárias são permitidas na sua rede.

4. [Registo de uma conta Samsung](https://www2.samsungknox.com/en/user/register): é necessária uma conta Samsung para registar e ativar o KME e gerir todas as elegibilidades da Knox Enterprise num único local.

5. Revisão de Registos: Depois de o seu perfil estar concluído e submetido, a Samsung revê a sua aplicação e aprova-a imediatamente ou coloca-a num estado de revisão pendente para posterior acompanhamento. Depois de a sua conta ser aprovada, pode continuar a dar mais passos.

## <a name="create-mdm-profile"></a>Criar um perfil MDM

Quando a sua empresa for registada com êxito, pode criar o seu perfil MDM para o Microsoft Intune no portal do Knox através das informações abaixo. Pode criar perfis MDM para Android e Android Enterprise no portal do Knox.
- Para criar um perfil Android MDM, selecione **Device Admin** como o tipo de perfil no Portal Knox. 
- Para criar um perfil Android Enterprise MDM, selecione **Device Owner** como o tipo de perfil no Portal Knox.  

### <a name="for-android"></a>Para Android

| Campos do Perfil MDM| Obrigatório? | Valores | 
|-------------------|-----------|-------| 
|Profile Name (Nome do Perfil)       | Sim       |Introduza um nome de perfil à sua escolha. |
|Description        | Não        |Introduza texto que descreva o perfil. |
|Informação do MDM     | Sim        |Escolha **o Server URI não necessário para o meu MDM**.| 
|MDM Agent APK (APK do Agente MDM)      | Sim       |https://aka.ms/intune_kme_deviceowner| 
|Custom JSON (JSON Personalizado)        | Sim*        |{"com.google.android.apps.work.clouddpc.EXTRA_ENROLLMENT_TOKEN": "Introduzir cadeia do token de inscrição do Intune"}. Aprenda a criar um símbolo de inscrição para [dispositivos dedicados](android-kiosk-enroll.md) e [dispositivos totalmente geridos.](android-fully-managed-enroll.md) |
|Skip Setup wizard (Ignorar o Assistente de Configuração)  | Não        |Escolha esta opção para ignorar as indicações padrão de configuração do dispositivo para o utilizador final.|
|Allow End User to Cancel Enrollment (Permitir que o Utilizador Final Cancele a Inscrição) | Não | Selecione esta opção para permitir que os utilizadores cancelem o KME.|
| Política de Privacidade, EULAs e Termos de Serviço | Não | Deixe este campo em branco. |
| Apoiar detalhes de contato | Sim | Escolha editar para atualizar os seus dados de contacto |
|Associate a Knox license with this profile (Associar uma licença do Knox a este perfil) | Não | Não selecione esta opção. Inscrever-se em Intune usando KME não requer uma licença Knox.|

\* Este campo não é necessário para completar a criação de perfis no portal Knox. No entanto, intune requer que este campo seja preenchido para que o perfil possa matricular o dispositivo com sucesso em Intune.

### <a name="for-android-enterprise"></a>Para Android Enterprise

Para obter orientações passo a passo, consulte as instruções [de Criar perfil da Samsung.](https://docs.samsungknox.com/KME-Getting-Started/Content/create-profiles.htm)

| Campos do Perfil MDM| Obrigatório? | Valores |
|-------------------|-----------|-------|
|Profile Name (Nome do Perfil)       | Sim       |Introduza um nome de perfil à sua escolha.|
|Description        | Não        |Introduza texto que descreva o perfil.|
|Escolha o seu MDM | Sim | Escolha o Microsoft Intune. |
|MDM Agent APK (APK do Agente MDM)      | Sim       |https://aka.ms/intune_kme|
|MDM Server URI (URI do Servidor MDM)     | Não        |Deixe este campo em branco.|
|Dados JSON personalizados        | Não        |Deixe este campo em branco.|
|Duplo DAR | Não | Deixe este campo em branco.|
|Código QR para inscrição | Não | Pode adicionar um código QR à velocidade da inscrição.|
|Aplicações do sistema | Sim | Escolha a opção **de deixar todas as aplicações do sistema habilitadas** para garantir que todas as aplicações estão ativadas e disponíveis para o perfil. Se esta opção não for selecionada, apenas um conjunto limitado de aplicações do sistema exibe na bandeja de aplicações do dispositivo. As aplicações como a aplicação de E-mail permanecem ocultas. |
|Política de Privacidade, EULAs e Termos de Serviço | Não | Deixe este campo em branco.|
|Nome da Empresa | Sim | Este nome será exibido durante a inscrição do dispositivo. |

## <a name="add-devices"></a>Adicionar dispositivos

Para atribuir Perfis MDM a dispositivos, os dispositivos Samsung Knox suportados têm de ser adicionados ao Portal do Knox através de um dos seguintes métodos:
- **Utilização de revendedores aprovados pela Samsung):** Utilize este método se estiver a adquirir dispositivos a um dos revendedores aprovados pela Samsung. Os revendedores podem carregar automaticamente os dispositivos quando forem aprovados. [Para saber como adicionar revendedores, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/Register_resellers.htm).

- **Utilizar a Aplicação Knox Deployment (KDA):** utilize este método se tiver dispositivos existentes que precisam de ser inscritos através do KME. Pode utilizar Bluetooth ou NFC para adicionar dispositivos ao Portal do Knox através deste método. [Para saber como utilizar a KDA, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/add-device-info.htm).

## <a name="assign-an-mdm-profile-to-devices"></a>Atribuir um perfil MDM aos dispositivos
Antes de poder inscrever os dispositivos adicionados ao Portal do Knox, tem de lhes atribuir um perfil MDM. [Para saber mais sobre a configuração de dispositivos, aceda ao Guia do Utilizador do Samsung Knox Enrollment](https://docs.samsungknox.com/KME-Getting-Started/Content/configure-devices.htm).

## <a name="configure-how-end-users-sign-in"></a>Configurar o início de sessão dos utilizadores finais

Para os dispositivos inscritos no Intune com o KME para Android, pode configurar o início de sessão de um utilizador final da seguinte forma:

- **Sem a associação do nome de utilizador:** no Portal do Knox, em **Device details** (Detalhes do dispositivo), deixe os campos **User ID** (ID do Utilizador) e **Password** (Palavra-passe) em branco para os dispositivos adicionados. Esta opção requer que o utilizador final introduza o nome do utilizador e a palavra-passe ao inscrever-se no Intune.

- **Com a associação do nome de utilizador:** no Portal do Knox, em **Device details** (Detalhes do dispositivo), forneça um **User ID** (ID do Utilizador), como um nome de utilizador para o utilizador atribuído ou uma conta do [Gestor de Inscrição de Dispositivos](device-enrollment-manager-enroll.md), para os dispositivos adicionados. Esta opção prepovoa o nome do utilizador e exige que o utilizador final introduza uma palavra-passe ao inscrever-se no Intune.

> [!NOTE]
>
>A associação de utilizadores aplica-se apenas à inscrição de administrador de dispositivos Android. Se a associação do utilizador estiver definida, apenas o utilizador associado poderá inscrever o dispositivo através do KME. Isto acontece mesmo após uma reposição de fábrica do dispositivo. Se não estiver definida nenhuma associação do utilizador no portal do Knox, todos os utilizadores com uma licença válida do Intune poderão inscrever o dispositivo com o KME.
>Para dispositivos geridos totalmente pelo Android Enterprise, mesmo que a associação de utilizadores esteja definida, este não será passado para o dispositivo ou ligará o dispositivo ao utilizador.
>

## <a name="distribute-devices"></a>Distribuir dispositivos

Após criar e atribuir um perfil MDM, associar um nome de utilizador e identificar os dispositivos como pertencentes à empresa no Intune, poderá distribuir os dispositivos pelos utilizadores.

Ainda precisa de ajuda? Consulte o guia completo do [utilizador KME](https://docs.samsungknox.com/KME-Getting-Started/Content/get-started.htm).

## <a name="frequently-asked-questions"></a>Perguntas mais frequentes

- **Suporte do Proprietário** do Dispositivo: suporte do Proprietário do **dispositivo - :** Intune suporta a inscrição de dispositivos dedicados e totalmente geridos utilizando o portal KME. Outros modos de proprietário de dispositivos Android Enterprise serão suportados à medida que forem disponibilizados no Intune.

- **Sem suporte ao perfil de trabalho:** O KME é um método de inscrição de dispositivos corporativos e os dispositivos matriculados no perfil de trabalho android garantem que o trabalho e os dados pessoais são separados em dispositivos pessoais. Assim, a inscrição do dispositivo para o perfil de trabalho usando kmE não é um cenário suportado em Intune.

- **Reposição de fábrica para inscrição no Android Enterprise:** se reutilizar dispositivos que já foram configurados, tem de efetuar a reposição de fábrica dos mesmos ao inscrever-se no Android Enterprise.

- **Atualizações utilizando a conta do Google Play:** A conta Google Play não é necessária para inscrever o dispositivo no Microsoft Intune. No então, para as inscrições de administrador de dispositivos Android, futuras atualizações para a aplicação Intune Company Portal podem necessitar de uma conta Google Play no dispositivo. A conta Google Play não é necessária quando se matricula no Google Device Owner.

- **O campo "Password" é ignorado:** Se o campo **de palavra-passe** for povoado em detalhes do **Dispositivo** no Portal Knox, é ignorado pela aplicação Intune Company Portal durante a inscrição no Android. O utilizador final tem de introduzir uma palavra-passe no dispositivo para concluir a inscrição do dispositivo.


## <a name="getting-support"></a>Obter suporte
Saiba mais sobre [como obter suporte para o Samsung KME](https://docs.samsungknox.com/KME-Getting-Started/Content/to-get-kme-support.htm).


