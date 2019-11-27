---
title: Resolução de problemas de perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Perguntas e respostas comuns com perfis e políticas de dispositivo, incluindo alterações de perfil não aplicadas a usuários ou dispositivos, quanto tempo leva para que novas políticas sejam enviadas para os dispositivos, quais configurações são aplicadas quando há várias políticas, o que acontece quando um o perfil é excluído ou removido e mais com Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/15/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a1177a37ddbfa7f760339c4ad0cd7773d670540
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199195"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Perguntas comuns, problemas e resoluções com perfis e políticas de dispositivo no Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Obtenha respostas para perguntas comuns ao trabalhar com perfis de dispositivo e políticas no Intune. Este artigo também lista os intervalos de tempo de check-in, fornece mais Detains em conflitos e muito mais.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Por que razão um utilizador não obtém um novo perfil quando altera uma palavra-passe ou frase de acesso num perfil de Wi-Fi existente?

Suponhamos que cria um perfil de Wi-Fi empresarial, implementa o perfil num grupo, altera a palavra-passe e guarda o perfil. Quando o perfil é alterado, alguns utilizadores podem não receber o novo perfil.

Para mitigar este problema, configure o Wi-Fi de convidado. Se o Wi-Fi empresarial falhar, os utilizadores podem ligar-se ao Wi-Fi de convidado. Certifique-se de que ativa todas as definições de ligação automática. Implemente o perfil de Wi-Fi convidado para todos os utilizadores.

Algumas recomendações adicionais:  

- Se a rede Wi-Fi à qual você está se conectando usar uma senha ou frase secreta, verifique se você pode se conectar ao roteador Wi-Fi diretamente. Pode testar com um dispositivo iOS.
- Depois de se ligar com êxito ao ponto final do Wi-Fi (router do Wi-Fi), tenha em atenção o SSID e a credencial utilizados (este valor será a palavra-passe ou a frase de acesso).
- Introduza o SSID e a credencial (palavra-passe ou frase de acesso) no campo Chave Pré-partilhada. 
- Implemente num grupo de teste com um número de utilizadores limitado, preferencialmente apenas a equipa de TI. 
- Sincronize o seu dispositivo iOS com o Intune. Inscreva-o caso ainda não o tenha feito. 
- Tente ligar-se novamente ao mesmo ponto final do Wi-Fi (como mencionado no primeiro passo).
- Implemente em grupos maiores e, por fim, em todos os utilizadores esperados na sua organização. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Quanto tempo leva para os dispositivos obterem uma política, um perfil ou um aplicativo depois de serem atribuídos?

O Intune notifica o dispositivo para fazer check-in no serviço do Intune. Os tempos de notificação variam, incluindo imediatamente até algumas horas. Esses tempos de notificação também variam entre as plataformas.

Se um dispositivo não fizer check-in para obter a política ou o perfil após a primeira notificação, o Intune fará mais três tentativas. Um dispositivo offline, como desativado ou não conectado a uma rede, pode não receber as notificações. Nesse caso, o dispositivo Obtém a política ou o perfil em seu próximo check-in agendado com o serviço do Intune, que é **estimado** em:

| Plataforma | Ciclo de atualização|
| --- | --- |
| iOS | Aproximadamente a cada 8 horas |
| macOS | Aproximadamente a cada 8 horas |
| Android | Aproximadamente a cada 8 horas |
| PCs com o Windows 10 inscritos como dispositivos | Aproximadamente a cada 8 horas |
| Windows Phone | Aproximadamente a cada 8 horas |
| Windows 8.1 | Aproximadamente a cada 8 horas |

Se o dispositivo tiver sido registrado recentemente, o check-in de conformidade e configuração será executado com mais frequência, o que é **estimado** em:

| Plataforma | Frequência |
| --- | --- |
| iOS | A cada 15 minutos por 1 hora e, em seguida, a cada 8 horas |  
| macOS | A cada 15 minutos por 1 hora e, em seguida, a cada 8 horas | 
| Android | A cada 3 minutos por 15 minutos, então a cada 15 minutos por 2 horas e, em seguida, a cada 8 horas | 
| PCs com o Windows 10 inscritos como dispositivos | A cada 3 minutos por 15 minutos, então a cada 15 minutos por 2 horas e, em seguida, a cada 8 horas | 
| Windows Phone | A cada 5 minutos por 15 minutos, então a cada 15 minutos por 2 horas e, em seguida, a cada 8 horas | 
| Windows 8.1 | A cada 5 minutos por 15 minutos, então a cada 15 minutos por 2 horas e, em seguida, a cada 8 horas | 

A qualquer momento, os usuários podem abrir o aplicativo Portal da Empresa, **configurações** > **sincronização** para verificar imediatamente se há atualizações de política ou perfil.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Que ações fazem o Intune enviar de imediato uma notificação para um dispositivo?

Há diferentes ações que disparam uma notificação, como quando uma política, um perfil ou um aplicativo é atribuído (ou não atribuído), atualizado, excluído e assim por diante. Esses tempos de ação variam entre as plataformas.

Os dispositivos fazem check-in no Intune quando recebem uma notificação para fazer check-in ou durante o check-in agendado. Quando você direciona um dispositivo ou usuário com uma ação, como bloqueio, redefinição de senha, aplicativo, perfil ou atribuição de política, o Intune notifica imediatamente o dispositivo para fazer check-in para receber essas atualizações.

Outras alterações, como a revisão das informações de contato no aplicativo Portal da Empresa, não causam uma notificação imediata para os dispositivos.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Se forem atribuídas várias políticas ao mesmo utilizador ou dispositivo, como posso saber que definições serão aplicadas?

Quando duas ou mais políticas são atribuídas ao mesmo usuário ou dispositivo, a configuração que se aplica ocorre no nível de configuração individual:

- As configurações de política de conformidade sempre têm precedência sobre as configurações do perfil de configuração.

- Se uma política de conformidade for avaliada em relação à mesma configuração em outra política de conformidade, a configuração de política de conformidade mais restritiva será aplicada.

- Se uma definição de política de configuração estiver em conflito com uma configuração em outra política de configuração, esse conflito será mostrado no Intune. Deve resolver estes conflitos manualmente.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>O que acontece quando as políticas de proteção de aplicações estão em conflito entre si? Qual delas é aplicada na aplicação?

Os valores de conflito são as configurações mais restritivas disponíveis em uma política de proteção de aplicativo, *exceto* pelos campos de entrada de número, como tentativas de PIN antes da redefinição. Os campos de entrada de número são definidos da mesma forma que os valores, como se você criasse uma política de MAM usando a opção de configurações recomendadas.

Os conflitos ocorrem quando duas configurações de perfil são iguais. Por exemplo, se configurou duas políticas MAM idênticas, à exceção da definição de copiar/colar. Neste cenário, a definição de copiar/colar está definida para o valor mais restritivo, mas as definições restantes são aplicadas conforme configuradas.

Uma política é implantada no aplicativo e entra em vigor. Uma segunda política é implantada. Nesse cenário, a primeira política tem precedência e permanece aplicada. A segunda política mostra um conflito. Se ambos forem aplicados ao mesmo tempo, o que significa que não há política anterior, ambos estarão em conflito. As definições em conflito são definidas para os valores mais restritivos.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>O que acontece quando políticas personalizadas do iOS entram em conflito?

O Intune não avalia o payload dos ficheiros do Apple Configurator nem de políticas OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personalizadas. Serve apenas como o mecanismo de entrega.

Ao atribuir uma política personalizada, confirme se as configurações definidas não entram em conflito com a conformidade, configuração ou outras políticas personalizadas. Se uma política personalizada e suas configurações entrarem em conflito, as configurações serão aplicadas aleatoriamente.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>O que acontece quando um perfil é eliminado ou deixa de ser aplicável?

Quando você exclui um perfil ou remove um dispositivo de um grupo que tem o perfil, o perfil e as configurações são removidos do dispositivo conforme descrito:

- Perfis de Wi-Fi, VPN, certificado e e-mail: estes perfis são removidos de todos os dispositivos inscritos suportados.
- Todos os outros tipos de perfil:  

  - **Dispositivos Windows e Android**: as configurações não são removidas do dispositivo
  - **Dispositivos Windows Phone 8.1**: as definições seguintes são removidas:  
  
    - Palavra-passe obrigatória para desbloquear os dispositivos móveis
    - Permitir palavras-passe simples
    - Comprimento mínimo da palavra-passe
    - Tipo obrigatório de palavra-passe
    - Expiração da palavra-passe (dias)
    - Memorizar histórico de palavras-passe
    - Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado
    - Minutos de inatividade antes da palavra-passe ser exigida
    - Tipo de palavra-passe obrigatório – Número mínimo de conjuntos de carateres
    - Permitir câmara
    - Encriptação obrigatória no dispositivo móvel
    - Permitir armazenamento amovível
    - Permitir browser
    - Permitir loja de aplicações
    - Permitir captura de ecrã
    - Permitir geolocalização
    - Permitir conta Microsoft
    - Permitir copiar e colar
    - Permitir partilha de Wi-Fi
    - Permitir ligação automática a hotspots Wi-Fi
    - Permitir relatórios de hotspots Wi-Fi
    - Permitir a limpeza
    - Permitir Bluetooth
    - Permitir NFC
    - Permitir Wi-Fi

  - **iOS**: todas as definições são removidas, exceto:
  
    - Permitir chamadas em roaming
    - Permitir roaming de dados
    - Permitir sincronização automática em roaming

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Alterei um perfil de restrição de dispositivos, mas as alterações ainda não foram aplicadas

Uma vez definido, os dispositivos Windows Phone não permitem que as políticas de segurança definidas usando MDM ou EAS sejam reduzidas em segurança. Por exemplo, você define um **número mínimo de caracteres de senha** como 8. Você tenta reduzi-lo para 4. O perfil mais restritivo já está aplicado ao dispositivo.

Para alterar o perfil para um valor menos seguro, redefina as políticas de segurança. Por exemplo, em Windows 8.1, na área de trabalho, passe o dedo da direita > selecione **configurações** > **painel de controle**. Selecione a miniaplicação **Contas de Utilizador** . No menu de navegação à esquerda, há um link **Redefinir políticas de segurança** (em direção à parte inferior). Selecione-a e, em seguida, selecione **Repor Políticas**.

Outros dispositivos MDM, como Android, Windows Phone 8,1 e posterior, iOS e Windows 10 podem precisar ser desativados e registrados novamente no Intune para aplicar um perfil menos restritivo.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Algumas configurações em um perfil do Windows 10 retornam "não aplicável"

Algumas configurações em dispositivos Windows 10 podem ser mostradas como "não aplicável". Quando isso acontece, essa configuração específica não tem suporte na versão ou edição do Windows em execução no dispositivo. Essa mensagem pode ocorrer pelos seguintes motivos:

- A configuração só está disponível para versões mais recentes do Windows e não a versão atual do sistema operacional (SO) no dispositivo.
- A configuração só está disponível para edições específicas do Windows ou SKUs específicos, como Home, Professional, Enterprise e Education.

Para saber mais sobre os requisitos de versão e SKU para as diferentes configurações, consulte a [referência do provedor de serviços de configuração (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Passos Seguintes

Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).
