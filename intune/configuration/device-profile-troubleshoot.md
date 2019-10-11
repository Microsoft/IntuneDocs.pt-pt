---
title: Solucionar problemas de perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Perguntas e respostas comuns com perfis e políticas de dispositivo, incluindo alterações de perfil não aplicadas a usuários ou dispositivos, quanto tempo leva para que novas políticas sejam enviadas para os dispositivos, quais configurações são aplicadas quando há várias políticas, o que acontece quando um o perfil é excluído ou removido e mais com Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 05/29/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8fa8e1940a5b5b9c6938abfdd0813a2b8c537f8
ms.sourcegitcommit: f1bd3b866f3ba62a562d88fdae07eef64ac11cbb
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/11/2019
ms.locfileid: "72262507"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Perguntas comuns, problemas e resoluções com perfis e políticas de dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Obtenha respostas para perguntas comuns ao trabalhar com perfis de dispositivo e políticas no Intune. Este artigo também lista os intervalos de tempo de check-in, fornece mais Detains em conflitos e muito mais.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Por que um usuário não recebe um novo perfil ao alterar uma senha ou frase secreta em um perfil de Wi-Fi existente?

Você cria um perfil de Wi-Fi corporativo, implanta o perfil em um grupo, altera a senha e salva o perfil. Quando o perfil é alterado, alguns usuários não podem obter o novo perfil.

Para atenuar esse problema, configure o Wi-Fi convidado. Se o Wi-Fi corporativo falhar, os usuários poderão se conectar ao Wi-Fi convidado. Certifique-se de habilitar as configurações de conexão automaticamente. Implante o perfil Wi-Fi convidado para todos os usuários.

Algumas recomendações adicionais:  

- Se a rede Wi-Fi à qual você está se conectando usar uma senha ou frase secreta, verifique se você pode se conectar ao roteador Wi-Fi diretamente. Você pode testar com um dispositivo iOS.
- Depois de se conectar com êxito ao ponto de extremidade Wi-Fi (Roteador Wi-Fi), observe o SSID e a credencial usada (esse valor é a senha ou frase secreta).
- Insira o SSID e a credencial (senha ou frase secreta) no campo chave pré-compartilhada. 
- Implante em um grupo de teste que tenha um número limitado de usuários, preferivelmente apenas a equipe de ti. 
- Sincronize seu dispositivo iOS para o Intune. Registre-se se você ainda não tiver se inscrito. 
- Teste a conexão com o mesmo ponto de extremidade Wi-Fi (conforme mencionado na primeira etapa) novamente.
- Distribua para grupos maiores e, eventualmente, para todos os usuários esperados em sua organização. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Quanto tempo leva para os dispositivos obterem uma política, um perfil ou um aplicativo depois de serem atribuídos?

O Intune notifica o dispositivo para fazer check-in no serviço do Intune. Os tempos de notificação variam, incluindo imediatamente até algumas horas. Esses tempos de notificação também variam entre as plataformas.

Se um dispositivo não fizer check-in para obter a política ou o perfil após a primeira notificação, o Intune fará mais três tentativas. Um dispositivo offline, como desativado ou não conectado a uma rede, pode não receber as notificações. Nesse caso, o dispositivo Obtém a política ou o perfil em seu próximo check-in agendado com o serviço do Intune, que é **estimado** em:

| Plataforma | Ciclo de atualização|
| --- | --- |
| iOS | Aproximadamente a cada 8 horas |
| macOS | Aproximadamente a cada 8 horas |
| Android | Aproximadamente a cada 8 horas |
| Computadores Windows 10 registrados como dispositivos | Aproximadamente a cada 8 horas |
| Windows Phone | Aproximadamente a cada 8 horas |
| Windows 8.1 | Aproximadamente a cada 8 horas |

Se o dispositivo tiver sido registrado recentemente, o check-in de conformidade e configuração será executado com mais frequência, o que é **estimado** em:

| Plataforma | Frequência |
| --- | --- |
| iOS | A cada 15 minutos por 1 hora e, em seguida, a cada 8 horas |  
| macOS | A cada 15 minutos por 1 hora e, em seguida, a cada 8 horas | 
| Android | A cada 3 minutos por 15 minutos, então a cada 15 minutos por 2 horas e, em seguida, a cada 8 horas | 
| Computadores Windows 10 registrados como dispositivos | A cada 3 minutos por 15 minutos, então a cada 15 minutos por 2 horas e, em seguida, a cada 8 horas | 
| Windows Phone | A cada 5 minutos por 15 minutos, então a cada 15 minutos por 2 horas e, em seguida, a cada 8 horas | 
| Windows 8.1 | A cada 5 minutos por 15 minutos, então a cada 15 minutos por 2 horas e, em seguida, a cada 8 horas | 

A qualquer momento, os usuários podem abrir o aplicativo Portal da Empresa e sincronizar o dispositivo para verificar imediatamente se há atualizações de política ou perfil.

Para dispositivos sem afinidade de usuário, a frequência de sincronização imediatamente após o registro pode variar de horas para um dia ou mais. O Intune envia solicitações em vários intervalos para que um dispositivo faça check-in no Intune. No entanto, ainda é até o dispositivo fazer check-in. Após o registro inicial, o tempo que leva um dispositivo para concluir o check-in é imprevisível. Ele também depende do tipo de registro de dispositivo e das políticas e perfis atribuídos a um dispositivo. Depois que o dispositivo for registrado e todas as políticas e perfis iniciais forem aplicadas, o dispositivo verificará se há novas políticas e perfis a cada 6-8 horas, com base no tempo que o dispositivo registra no Intune.

Como prática recomendada, verifique se os dispositivos estão online por pelo menos oito horas consecutivas para obter os melhores resultados.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Quais ações fazem com que o Intune envie imediatamente uma notificação para um dispositivo?

Há diferentes ações que disparam uma notificação, como quando uma política, um perfil ou um aplicativo é atribuído (ou não atribuído), atualizado, excluído e assim por diante. Esses tempos de ação variam entre as plataformas.

Os dispositivos fazem check-in no Intune quando recebem uma notificação para fazer check-in ou durante o check-in agendado. Quando você direciona um dispositivo ou usuário com uma ação, como bloqueio, redefinição de senha, aplicativo, perfil ou atribuição de política, o Intune notifica imediatamente o dispositivo para fazer check-in para receber essas atualizações.

Outras alterações, como a revisão das informações de contato no aplicativo Portal da Empresa, não causam uma notificação imediata para os dispositivos.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Se várias políticas forem atribuídas ao mesmo usuário ou dispositivo, como saber quais configurações são aplicadas?

Quando duas ou mais políticas são atribuídas ao mesmo usuário ou dispositivo, a configuração que se aplica ocorre no nível de configuração individual:

- As configurações de política de conformidade sempre têm precedência sobre as configurações do perfil de configuração.

- Se uma política de conformidade for avaliada em relação à mesma configuração em outra política de conformidade, a configuração de política de conformidade mais restritiva será aplicada.

- Se uma definição de política de configuração estiver em conflito com uma configuração em outra política de configuração, esse conflito será mostrado no Intune. Resolva esses conflitos manualmente.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>O que acontece quando as políticas de proteção de aplicativo entram em conflito entre si? Qual deles é aplicado ao aplicativo?

Os valores de conflito são as configurações mais restritivas disponíveis em uma política de proteção de aplicativo, *exceto* pelos campos de entrada de número, como tentativas de PIN antes da redefinição. Os campos de entrada de número são definidos da mesma forma que os valores, como se você criasse uma política de MAM usando a opção de configurações recomendadas.

Os conflitos ocorrem quando duas configurações de perfil são iguais. Por exemplo, você configurou duas políticas de MAM que são idênticas, exceto para a configuração copiar/colar. Nesse cenário, a configuração copiar/colar é definida como o valor mais restritivo, mas o restante das configurações é aplicado como configurado.

Uma política é implantada no aplicativo e entra em vigor. Uma segunda política é implantada. Nesse cenário, a primeira política tem precedência e permanece aplicada. A segunda política mostra um conflito. Se ambos forem aplicados ao mesmo tempo, o que significa que não há política anterior, ambos estarão em conflito. Todas as configurações conflitantes são definidas para os valores mais restritivos.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>O que acontece quando as políticas personalizadas do iOS entram em conflito?

O Intune não avalia a carga de arquivos de configuração da Apple ou uma política de OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personalizada. Ele simplesmente serve como mecanismo de entrega.

Ao atribuir uma política personalizada, confirme se as configurações definidas não entram em conflito com a conformidade, configuração ou outras políticas personalizadas. Se uma política personalizada e suas configurações entrarem em conflito, as configurações serão aplicadas aleatoriamente.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>O que acontece quando um perfil é excluído ou não é mais aplicável?

Quando você exclui um perfil ou remove um dispositivo de um grupo que tem o perfil, o perfil e as configurações são removidos do dispositivo conforme descrito:

- Wi-Fi, VPN, certificado e perfis de email: esses perfis são removidos de todos os dispositivos registrados com suporte.
- Todos os outros tipos de perfil:  

  - **Dispositivos Windows e Android**: as configurações não são removidas do dispositivo
  - **Dispositivos Windows Phone 8,1**: as seguintes configurações foram removidas:  
  
    - Exigir uma senha para desbloquear dispositivos móveis
    - Permitir senhas simples
    - Comprimento mínimo da senha
    - Tipo de senha necessária
    - Expiração da senha (dias)
    - Lembrar histórico de senha
    - Número de falhas de entrada repetidas permitidas antes que o dispositivo seja apagado
    - Minutos de inatividade antes que a senha seja exigida
    - Tipo de senha necessária – número mínimo de conjuntos de caracteres
    - Permitir câmera
    - Exigir criptografia no dispositivo móvel
    - Permitir armazenamento removível
    - Permitir navegador da Web
    - Permitir repositório de aplicativos
    - Permitir captura de tela
    - Permitir geolocalização
    - Permitir conta Microsoft
    - Permitir copiar e colar
    - Permitir compartilhamento de Internet por Wi-Fi
    - Permitir conexão automática para pontos de acesso Wi-Fi gratuitos
    - Permitir relatório de hotspot Wi-Fi
    - Permitir apagamento
    - Permitir Bluetooth
    - Permitir NFC
    - Permitir Wi-Fi

  - **Ios**: todas as configurações são removidas, exceto:
  
    - Permitir roaming de voz
    - Permitir roaming de dados
    - Permitir sincronização automática durante o roaming

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Alterei um perfil de restrição de dispositivo, mas as alterações não entraram em vigor

Uma vez definido, os dispositivos Windows Phone não permitem que as políticas de segurança definidas usando MDM ou EAS sejam reduzidas em segurança. Por exemplo, você define um **número mínimo de caracteres de senha** como 8. Você tenta reduzi-lo para 4. O perfil mais restritivo já está aplicado ao dispositivo.

Para alterar o perfil para um valor menos seguro, redefina as políticas de segurança. Por exemplo, em Windows 8.1, na área de trabalho, passe o dedo da direita > selecione **configurações** > **painel de controle**. Selecione o miniaplicativo **contas de usuário** . No menu de navegação à esquerda, há um link **Redefinir políticas de segurança** (em direção à parte inferior). Selecione-o e escolha **Redefinir políticas**.

Outros dispositivos MDM, como Android, Windows Phone 8,1 e posterior, iOS e Windows 10 podem precisar ser desativados e registrados novamente no Intune para aplicar um perfil menos restritivo.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Algumas configurações em um perfil do Windows 10 retornam "não aplicável"

Algumas configurações em dispositivos Windows 10 podem ser mostradas como "não aplicável". Quando isso acontece, essa configuração específica não tem suporte na versão ou edição do Windows em execução no dispositivo. Essa mensagem pode ocorrer pelos seguintes motivos:

- A configuração só está disponível para versões mais recentes do Windows e não a versão atual do sistema operacional (SO) no dispositivo.
- A configuração só está disponível para edições específicas do Windows ou SKUs específicos, como Home, Professional, Enterprise e Education.

Para saber mais sobre os requisitos de versão e SKU para as diferentes configurações, consulte a [referência do provedor de serviços de configuração (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Passos seguintes

Precisa de ajuda adicional? Consulte [como obter suporte para Microsoft Intune](../fundamentals/get-support.md).
