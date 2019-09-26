---
title: Portal de resolução de problemas de suporte técnico
titleSuffix: Microsoft Intune
description: O pessoal de suporte técnico utiliza o portal de resolução de problemas para resolver problemas técnicos dos utilizadores.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 03/11/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a4e6cbf2d9edcff83ae756c2dbcf098cae0ae54
ms.sourcegitcommit: 73fbecf7cee4fdfc37d3c30ea2007d2a9a6d2d12
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/03/2019
ms.locfileid: "71301863"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O portal de resolução de problemas permite que os operadores de suporte técnico e os administradores do Intune vejam as informações de utilizador para resolverem pedidos de ajuda dos utilizadores. As organizações que incluem um suporte técnico podem atribuir o **Operador de suporte técnico** a um grupo de utilizadores. A função de operador de suporte técnico pode utilizar o painel **Resolução de problemas**.

O painel **Resolução de Problemas** também apresenta problemas de inscrição de utilizadores. Os detalhes acerca do problema e os passos de remediação sugeridos podem ajudar os administradores e os operadores de suporte técnico a resolver problemas. Existem determinados problemas de inscrição que não são detetados e é possível que não existam sugestões de remediação para alguns erros.

Para obter passos sobre como adicionar uma função de operador de suporte técnico, veja [Controlo de administração baseada em funções (RBAC) com o Intune](/intune/role-based-access-control)

Quando um utilizador contacta o suporte acerca de um problema técnico com o Intune, o operador de suporte técnico introduz o nome do utilizador. O Intune mostra dados úteis que podem ajudar a resolver vários problemas de nível 1, incluindo:

- Estado de utilizador
- Atribuições
- Resolver problemas de compatibilidade
- O dispositivo não responde
- O dispositivo não consegue aceder às definições de VPN ou Wi-Fi
- Falha na instalação da aplicação

## <a name="to-review-troubleshooting-details"></a>Para rever os detalhes da resolução de problemas

No painel Resolução de Problemas, selecione **Utilizador selecionado** para ver as informações do utilizador. As informações dos utilizadores podem ajudá-lo a compreender o estado atual dos utilizadores e dos dispositivos deles.  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
3. No painel **Intune**, selecione **Resolução de problemas**.
4. Clique em **Selecionar** para selecionar um utilizador para o qual pretende executar a resolução de problemas.
5. Selecione um utilizador ao escrever o nome ou endereço de e-mail. Clique em **Selecionar**. As informações de resolução de problemas do utilizador são apresentadas no painel Resolução de problemas. A seguinte tabela explica as informações.

> [!Note]  
> Também pode aceder ao painel **Resolução de problemas** ao apontar o seu browser para: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Áreas do dashboard de resolução de problemas

Pode utilizar o painel **Resolução de problemas** para analisar as informações de utilizador.

![Painel de solução de problemas, com áreas numeradas descritas na tabela a seguir](/intune/media/troubleshooting-dash.png)

| Área | Name | Descrição |
| ---  | ---  | ---         |
| 1.   | Estado da conta  | Mostra o estado do inquilino do Intune atual como **Ativo** ou **Inativo**.       |
| 2.   | Seleção do utilizador  | O nome do utilizador atualmente selecionado. Clique em **Alterar utilizador** para selecionar um novo utilizador.       |
| 3.   | Estado de utilizador  | Apresenta o estado da licença do Intune do utilizador, número de dispositivos, conformidade de cada dispositivo, número de aplicações e conformidade das aplicações.       |
| 4.   | Informações do utilizador  | Utilize a lista para selecionar os detalhes a consultar no painel. <br>Pode selecionar: <ul><li>Aplicações do cliente<li>Políticas de conformidade<li> Políticas de configuração<li>Políticas de proteção de aplicações <li>Restrições de inscrição</ul>      |
| 5.   | Associação a grupos  | Mostra os grupos atuais dos quais o utilizador selecionado é membro.       |

<!-- this section needs to be updated

## Client apps reference

The apps that are running devices
- managed by Intune and Azure Active Directory (AD) 
- owned by users managed by Intune and Azure Active Directory (AD).

### Properties

The properties of client apps.

| Property      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name          | The name of the application.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| OS            | The operating system installed on the device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Type          | You can choose an assignment type for each app.  <br> **Available** - Users install the app from the Company Portal app or website.  <br> **Not Applicable** - The app is not installed or shown in the Company Portal. <br> **Uninstall** - The app is uninstalled from devices in the selected groups.  <br> **Available with or without enrollment** - Assign this app to groups of users whose devices are not enrolled with Intune. |
| Last Modified | The name of the type of device.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| App install | Denotes whether an app install failure or success has occurred on the individual device. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection status

An app protection policy is available to mobile apps that integrate with Enterprise Mobility Solution (EMS) technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## App protection policies reference

An app protection policy is available to mobile apps that integrate with EMS technologies.These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

### Properties

The table summarizes app protection policies status for devices managed by Intune.

| Property    | Description                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Name        | The name of the application.                                                                                                        |
| Deployed    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Platform    | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Enrollment  | The name of the type of device.                                                                                                     |
| Last Update | The timestamp the policy was modified.                                                                                              |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Text                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device Name        | The name of the type of device.                                                                                                     |
| Managed By         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last Check in      | The name of the type of device.                                                                                                     |

## Compliance policies reference

Makes sure that the devices used to access company apps and data, comply with certain rules like using a PIN to access the device, and encryption of data stored on the device.

### Properties

The properties of the compliance policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, and **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |

### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

## Configuration policies reference

An app configuration policy is available to mobile apps with vendor-specific configuration. 

### Properties

The properties of the configuration policies.

| Property      | Description                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Assignment    | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Name          | The name of the application.                                                                                                        |
| OS            | The operating system installed on the device.                                                                                       |
| Policy Type   | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Last Modified | The name of the type of device.                                                                                                     |

### Devices

Devices managed by Intune or by users managed by Intune or Azure AD.

| Property           | Description                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Device name        | The name of the type of device.                                                                                                     |
| Managed by         | The timestamp the policy was modified.                                                                                              |
| Azure AD join type | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| Ownership          | The type of device ownership (**Company**, **Personal**, or **Unknown**).                                               |
| Intune compliant   | The name of the type of device.                                                                                                     |
| Azure AD compliant | The status of each of the users' app protection apps. The possible statuses for the apps are **Checked in** and **Not checked in**. |
| OS                 | The operating system installed on the device.                                                                                       |
| OS version         | The Operating System version number of the device.                                                                                  |
| Last check-in      | The name of the type of device.                                                                                                     |


### App protection policies

An app protection policy is available to mobile apps that integrate with EMS technologies. These policies give a baseline of protection for your corporate data when it is downloaded to mobile apps, including the Office mobile apps. 

| Property    | Description                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Status      | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| App name    | The name of the application                                                           |
| Device name | The name of the type of device.                                                       |
| Device type | The name of the type of device.                                                       |
| Policies    | The type of device ownership (**Company**, **Personal**, or **Unknown**). |
| Last sync   | The timestamp of the last time the device synchronized with Intune.                   |

-->

## <a name="enrollment-failure-reference"></a>Referência de falha de inscrição

A tabela Falhas de Inscrição lista as tentativas de inscrição que falharam. Um dispositivo listado na tabela abaixo pode ter sido inscrito posteriormente com êxito durante outra tentativa. É possível que algumas tentativas falhadas não sejam listadas. As informações de mitigação não estão disponíveis para todas as falhas.

| Coluna de tabela | Descrição |
|-------------|----------|
| Início da inscrição | A hora de início em que o utilizador começou a inscrição. |
| OS | O sistema operativo do dispositivo. |
| Versão do SO | A versão do sistema operativo do dispositivo. |
| Falha | O motivo da falha. |

### <a name="failure-details"></a>Detalhes da falha

Ao selecionar uma linha de falha, são fornecidos mais detalhes.

| Section | Descrição |
|-------------|----------|
| Detalhes da falha | Uma explicação em maior detalhe sobre a falha. |
| Potenciais remediações | Passos sugeridos para resolver o erro. Poderão não existir remediações para determinadas falhas. |
| Recursos (Opcional) | Ligações para leituras adicionais ou para determinada área no portal para efetuar uma ação. |

### <a name="enrollment-errors"></a>Erros de inscrição

| Erro | Detalhes |
|-------------|----------|
| Tempo limite ou Falha de dispositivos iOS | Exceder do tempo limite entre o dispositivo e o Intune devido ao utilizador demorar demasiado tempo a concluir a inscrição. |
| Utilizador não encontrado ou licenciado | O utilizador não possui uma licença ou foi removido do serviço. |
| O dispositivo já está inscrito | Uma pessoa tentou inscrever um dispositivo ao utilizar o Portal da Empresa num dispositivo que ainda está inscrito por outro utilizador. |
| Não incluído no Intune | Houve uma tentativa de inscrição enquanto a autoridade de gestão de dispositivos móveis (MDM) do Intune ainda não estava configurada. |
| Falha na autorização da inscrição | Houve uma tentativa de inscrição através de uma versão antiga do portal da empresa. |
| Dispositivo não suportado | O dispositivo não cumpre os requisitos mínimos de inscrição no Intune. |
| As restrições de inscrição não correspondem | A inscrição foi bloqueada devido a uma restrição de inscrição configurada pelo administrador. |
| Versão do dispositivo demasiado baixa | O administrador configurou uma restrição de inscrição que requer uma versão superior do dispositivo. |
| Versão do dispositivo demasiado alta | O administrador configurou uma restrição de inscrição que requer uma versão inferior do dispositivo. |
| O dispositivo não pode ser inscrito como pessoal | O administrador configurou uma restrição de inscrição para bloquear inscrições pessoais e o dispositivo com falha não estava predefinido como empresarial. |
| Plataforma do dispositivo bloqueada | O administrador configurou uma restrição de inscrição que bloqueia a plataforma deste dispositivo. |
| Token em massa expirado | O token em massa no pacote de aprovisionamento expirou. |
| Não foram encontrados os detalhes ou o dispositivo Autopilot | O dispositivo Autopilot não foi encontrado ao tentar inscrever-se. |
| O perfil do Autopilot não foi encontrado ou não foi atribuído | O dispositivo não tem um perfil do Autopilot ativo. |
| Método de inscrição do Autopilot inesperado | O dispositivo tentou inscrever-se através de um método não permitido. |
| Dispositivo do Autopilot removido | O dispositivo que tentou inscrever-se foi removido do Autopilot para esta conta. |
| Máximo de dispositivos atingido | A inscrição foi bloqueada devido a uma restrição de limite de dispositivos configurada pelo administrador. |
| Inclusão da Apple | A inscrição de todos os dispositivos iOS foi bloqueada até ao momento devido a um certificado push de MDM da Apple expirado ou em falta no Intune. |
| O dispositivo não foi pré-registado | O dispositivo não foi pré-registado como dispositivo empresarial e todas as inscrições pessoais foram bloqueadas por um administrador. |
| Funcionalidade não suportada | O utilizador procedeu a uma provável tentativa de inscrição através de um método incompatível com a sua configuração do Intune. |

## <a name="collect-available-data-from-mobile-device"></a>Recolher dados disponíveis de dispositivos móveis

Utilize os seguintes recursos para ajudar a recolher dados de dispositivos ao resolver problemas de dispositivos:
- [Enviar erros de inscrição de dispositivos iOS para o seu administrador de TI](/intune-user-help/send-errors-to-your-it-admin-ios)
- [Help your company support fix device issues with verbose logging](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) (Ajudar o suporte da empresa a corrigir problemas de dispositivos com o registo verboso)
- [Enviar registos Android ao suporte da empresa por cabo USB](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
- [Enviar registos de dados de diagnóstico para o seu administrador de TI através de e-mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
- [Enviar erros de inscrição de dispositivos Android para o seu administrador de TI](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>Passos seguintes

Pode saber mais sobre o Controlo de administração baseada em funções (RBAC) para definir funções no seu dispositivo organizacional, gestão de aplicações móveis e tarefas de proteção de dados. Para obter mais informações, veja [Controlo de administração baseada em funções (RBAC) com o Intune](/intune/role-based-access-control).

Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para obter mais informações, veja [Problemas conhecidos no Microsoft Intune](/intune/known-issues).

Saiba como criar um pedido de suporte e obter ajuda quando precisar. [Obter suporte](/intune/get-support).
