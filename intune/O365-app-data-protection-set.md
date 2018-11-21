---
title: Gestão de dados das aplicações do Office 365 no Microsoft Intune
titlesuffix: ''
description: Saiba mais sobre a gestão de dados das aplicações do Office 365 no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 10/04/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 852612ac-f146-4372-a900-3f6fdebd05ad
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: ayesham
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a3eed03deb3f619f75502e8a9d1d66fefc38a081
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180076"
---
# <a name="how-your-users-will-experience-basic-protection-on-managed-office-365-apps-in-microsoft-intune"></a>Como a proteção básica em aplicações geridas do Office 365 se vai refletir nos seus utilizadores no Microsoft Intune

O assistente **Gerir aplicações do Office 365** cria uma política de proteção de aplicações para cada plataforma de dispositivo.

O assistente ativa as seguintes políticas:

**iOS**
* Encriptar dados da aplicação

**Android**
* Encriptar dados da aplicação
* Exigir PIN simples para acesso

Estas políticas garantem que pode gerir as aplicações do Office 365 e, ao mesmo, permitem-lhe eliminar os dados de trabalho das aplicações do Office quando precisar. Também garantem proteção básica no caso de um dispositivo se perder ou ser roubado, ao garantir que os seus dados de trabalho são encriptados e que é preciso introduzir um PIN para ver os dados nas aplicações do Office 365.


Este artigo utiliza o OneDrive para Empresas como exemplo para demonstrar a experiência do utilizador numa aplicação gerida pelo Intune.


>[!NOTE]
>Normalmente, num dispositivo pessoal, o utilizador final teria de transferir a aplicação. Se o dispositivo for gerido por uma solução de gestão de dispositivos móveis (MDM), pode implementar a aplicação no dispositivo.

## <a name="user-experience-on-an-ios-device"></a>Experiência do utilizador num dispositivo iOS

1. Inicie a aplicação OneDrive para Empresas para abrir a página de início de sessão.  
2. Escreva o nome de utilizador da sua conta profissional. Será redirecionado para a página de autenticação do Office 365 para introduzir as suas credenciais de trabalho. 
3. Depois de as suas credenciais serem autenticadas com êxito pelo Azure Active Directory, as políticas de proteção de aplicações serão aplicadas e ser-lhe-á pedido que reinicie a aplicação OneDrive para Empresas. 

   > [!NOTE]
   > A mensagem de reinício necessário é apresentada apenas nos dispositivos que não estão inscritos no Intune.

4. Reinicie a aplicação OneDrive para Empresas. A aplicação é iniciada com as políticas de proteção de aplicações ativadas e é-lhe pedido para definir um PIN para o dispositivo (se ainda não tiver um configurado para o dispositivo).  

   > [!NOTE]
   > A maior parte dos utilizadores não vê este pedido. Este pedido será apresentado apenas aos utilizadores que ainda não ativaram um PIN no dispositivo iOS.

5. Depois de definir o PIN e o confirmar, volte à aplicação OneDrive para Empresas. Verá um aviso único a indicar que o administrador de TI está agora a proteger os dados de trabalho no OneDrive. 
6. Clique para dispensar este aviso de modo a aceder aos ficheiros no OneDrive para Empresas. 

>[!NOTE]
>Quando altera uma política implementada, as alterações serão aplicadas na próxima vez que abrir a aplicação.

## <a name="user-experience-on-an-android-device"></a>Experiência do utilizador num dispositivo Android

1. Inicie a aplicação OneDrive para Empresas para abrir a página de início de sessão.  <br/> ![Imagem do ecrã de boas-vindas da aplicação OneDrive](./media/onedrive-android-welcome.png)
2. Escreva o nome de utilizador da sua conta profissional. Será redirecionado para a página de autenticação do Office 365 para introduzir as suas credenciais de trabalho. <br/> ![Imagem do início de sessão no O365 no Android](./media/o365-sign-in-android.png)
3. Após as suas credenciais serem autenticadas com êxito pelo Azure Active Directory, verá uma mensagem com instruções para instalar a aplicação Portal da Empresa, caso ainda não esteja instalada no dispositivo. Toque em **Ir para loja** para continuar. <br/> ![Imagem da mensagem para obter a aplicação Portal da Empresa](./media/get-company-portal-android.png) <br/>Se já tiver a aplicação Portal da Empresa instalada no telemóvel, a aplicação OneDrive para Empresas será automaticamente iniciada e poderá avançar para a nota final.   

   > [!IMPORTANT]
   > No Android, depois de configurar as aplicações do Office para serem geridas por uma política de proteção de aplicações, o utilizador do dispositivo **tem** de instalar a aplicação Portal da Empresa para aceder aos e-mails e aos documentos do trabalho, embora o utilizador final não precise de abrir ou iniciar sessão na aplicação para ler os e-mails ou os documentos.

4. Entrou na Google Play Store, onde pode transferir e instalar a aplicação Portal da Empresa. A aplicação ajuda a manter os dados em segurança. <br/> ![Imagem da aplicação na Google Play Store](./media/google-play-get-app-android.png)
5. Depois de concluir a instalação da aplicação, selecione **Aceitar** para aceitar os termos. A aplicação OneDrive para Empresas é iniciada automaticamente.


>[!NOTE]
>Da próxima vez que abrir o OneDrive para Empresas, poderá ser-lhe pedido para definir um PIN se o departamento de TI o exigir. Depois de definir e confirmar o PIN, pode continuar no OneDrive para Empresas.

![Imagem do pedido de PIN](./media/pin-prompt-android.png)


<!--- Original steps: 6. The next time you open OneDrive for Business, you may be asked to set a PIN, if your IT requires one to use the OneDrive for Business app. ART 7. After you set and confirm the PIN, you can continue on to OneDrive for Business. -->

## <a name="what-policies-does-this-wizard-set"></a>Que políticas define este assistente?

|     |       | |
|----|--------|-|
|**Nome**|Gerir aplicações do Office 365| |
| **Descrição**|Criadas pelo assistente Gerir aplicações do Office 365| |
| |  | |
| **Nome da definição** |**Valor da política para iOS** | **Valor da política para Android** |
|Impedir cópias de segurança do iTunes e do iCloud| Não | N/D |
|Impedir cópias de segurança Android |N/D | Não|
|Permitir que a aplicação transfira dados para outras aplicações | Todas as aplicações | Todas as aplicações|
|Permitir que a aplicação receba dados de outras aplicações| Todas as aplicações | Todas as aplicações|
|Impedir "Guardar como" | Não | Não|
|Restringir cortar, copiar e colar com outras aplicações | Qualquer aplicação | Qualquer aplicação |
|Restringir o conteúdo Web a apresentar num browser gerido pela empresa | Não| Não|
|Encriptar dados da aplicação | Quando o dispositivo está bloqueado | Sim|
|Desativar a sincronização de contactos | Não| Não|
|Desativar a impressão | Não | Não|
|Exigir PIN para acesso | Não | Sim|
|Número de tentativas antes de redefinição do PIN | N/D |5|
|Permitir PIN simples | N/D |Sim|
|Comprimento do PIN | N/D | 4|
|Permitir impressões digitais em vez do PIN | N/D | Sim |
|Exigir credenciais da empresa para obter acesso | Não | Não|
|Bloquear a execução de aplicações geridas em dispositivos com jailbreak ou root | Não | Não|
|Verificar novamente os requisitos de acesso após (minutos) – Tempo limite | 30 | 30|
|Verificar novamente os requisitos de acesso após (minutos) – Período de tolerância offline | 720 |720|
|Intervalo offline (dias) antes de os dados da aplicação serem eliminados | 90 | 90|
|Bloquear captura de ecrã (apenas dispositivos Android) | N/D | Não |

### <a name="why-is-an-app-pin-policy-only-configured-for-android-devices"></a>Por que motivo a política de PIN da aplicação é apenas configurada para dispositivos Android?
A encriptação funciona de forma diferente no iOS e no Android.

No iOS, para aplicações associadas a uma política de proteção de aplicações do Intune, os dados são encriptados em descanso através da encriptação no nível do dispositivo fornecida pelo sistema operativo. Por isso, quando ativa a política de encriptação de aplicações, também está automaticamente a exigir que o utilizador tenha e introduza um PIN de dispositivo para aceder aos dados de trabalho. Os utilizadores que ainda não tenham um PIN de dispositivo configurado recebem um pedido para criar um PIN de dispositivo.

No Android, para as aplicações que estão associadas a uma política de proteção de aplicações do Intune, os dados são encriptados de forma síncrona durante tarefas de E/S de ficheiros. Os conteúdos no armazenamento do dispositivo são sempre encriptados. Nos dispositivos que não são geridos por MDM, a política de proteção de aplicações não pode exigir um PIN de dispositivo. Para garantir que os utilizadores são obrigados a utilizar um PIN para acederem aos dados de trabalho, o assistente ativa a política de PIN da aplicação.

Pode sempre editar estas definições da política para satisfazer os requisitos da sua organização.

### <a name="how-can-i-view-and-edit-the-policies-created-by-the-wizard"></a>Como posso ver e editar as políticas criadas pelo assistente?
Para ver ou atualizar estas políticas, ou todas as políticas que criar no Intune no portal do Azure, no dashboard, selecione **Gerir aplicações** > **Políticas de Proteção de Aplicações**. A lista de políticas é apresentada do lado direito. Escolha a política que quer visualizar para ver e editar as definições. <br/>
![Imagem do caminho da interface de utilizador para ver as políticas](./media/image-for-faq.png)

## <a name="next-steps"></a>Passos Seguintes
- Saiba mais sobre as [políticas de proteção de aplicações](app-protection-policy.md).
