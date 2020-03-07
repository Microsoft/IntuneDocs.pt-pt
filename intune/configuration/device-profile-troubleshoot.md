---
title: Resolução de problemas de perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Perguntas e respostas comuns com políticas e perfis de dispositivos, incluindo alterações de perfil não aplicadas a utilizadores ou dispositivos, quanto tempo leva para que novas políticas sejam empurradas para dispositivos, que configurações são aplicadas quando existem múltiplas políticas, o que acontece quando a o perfil é eliminado ou removido, e muito mais com o Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
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
ms.openlocfilehash: 21497716f17ced83bdcc1952cb952151f993bb7b
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78368378"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Questões comuns, questões e resoluções com políticas e perfis de dispositivos no Microsoft Intune

Obtenha respostas a perguntas comuns ao trabalhar com perfis e políticas de dispositivos no Intune. Este artigo também enumera os intervalos de tempo de check-in, fornece mais detenções em conflitos, e muito mais.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Por que razão um utilizador não obtém um novo perfil quando altera uma palavra-passe ou frase de acesso num perfil de Wi-Fi existente?

Suponhamos que cria um perfil de Wi-Fi empresarial, implementa o perfil num grupo, altera a palavra-passe e guarda o perfil. Quando o perfil é alterado, alguns utilizadores podem não receber o novo perfil.

Para mitigar este problema, configure o Wi-Fi de convidado. Se o Wi-Fi empresarial falhar, os utilizadores podem ligar-se ao Wi-Fi de convidado. Certifique-se de que ativa todas as definições de ligação automática. Implemente o perfil de Wi-Fi convidado para todos os utilizadores.

Algumas recomendações adicionais:  

- Se a rede Wi-Fi que estiver a ligar utilizar uma palavra-passe ou uma palavra-passe, certifique-se de que pode ligar-se diretamente ao router Wi-Fi. Pode testar com um dispositivo iOS/iPadOS.
- Depois de se ligar com êxito ao ponto final do Wi-Fi (router do Wi-Fi), tenha em atenção o SSID e a credencial utilizados (este valor será a palavra-passe ou a frase de acesso).
- Introduza o SSID e a credencial (palavra-passe ou frase de acesso) no campo Chave Pré-partilhada. 
- Implemente num grupo de teste com um número de utilizadores limitado, preferencialmente apenas a equipa de TI. 
- Sincronize o seu dispositivo iOS/iPadOS para Intune. Inscreva-o caso ainda não o tenha feito. 
- Tente ligar-se novamente ao mesmo ponto final do Wi-Fi (como mencionado no primeiro passo).
- Implemente em grupos maiores e, por fim, em todos os utilizadores esperados na sua organização. 

## <a name="how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned"></a>Quanto tempo leva os dispositivos para obter uma política, perfil ou app depois de serem atribuídos?

Instone notifica o dispositivo para fazer o check-in com o serviço Intune. Os tempos de notificação variam, incluindo imediatamente até algumas horas. Estes tempos de notificação também variam entre plataformas.

Se um dispositivo não fizer o check-in para obter a apólice ou perfil após a primeira notificação, Intune faz mais três tentativas. Um dispositivo offline, como desligado ou não ligado a uma rede, não pode receber as notificações. Neste caso, o dispositivo obtém a política ou perfil no seu próximo check-in agendado com o serviço Intune. O mesmo se aplica aos controlos de incumprimento, incluindo dispositivos que passam de um estado conforme a um estado não conforme.

**Frequências estimadas:**

| Plataforma | Ciclo de atualização|
| --- | --- |
| iOS/iPadOS | Cerca de 8 horas |
| macOS | Cerca de 8 horas |
| Android | Cerca de 8 horas |
| PCs com o Windows 10 inscritos como dispositivos | Cerca de 8 horas |
| Windows Phone | Cerca de 8 horas |
| Windows 8.1 | Cerca de 8 horas |

Se o dispositivo recentemente matriculado, o cumprimento, o incumprimento e o check-in de configuração são mais frequentemente executados, o que é **estimado** em:

| Plataforma | Frequência |
| --- | --- |
| iOS/iPadOS | A cada 15 minutos por 1 hora, e em volta de 8 horas |  
| macOS | A cada 15 minutos por 1 hora, e em volta de 8 horas | 
| Android | A cada 3 minutos por 15 minutos, a cada 15 minutos por 2 horas, e em volta de 8 horas | 
| PCs com o Windows 10 inscritos como dispositivos | A cada 3 minutos por 15 minutos, a cada 15 minutos por 2 horas, e em volta de 8 horas | 
| Windows Phone | A cada 5 minutos por 15 minutos, a cada 15 minutos por 2 horas, e em volta de 8 horas | 
| Windows 8.1 | A cada 5 minutos por 15 minutos, a cada 15 minutos por 2 horas, e em volta de 8 horas | 

A qualquer momento, os utilizadores podem abrir a aplicação Portal da Empresa, **Definições** > **Sync** para verificar imediatamente as atualizações de política ou de perfil.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Que ações fazem o Intune enviar de imediato uma notificação para um dispositivo?

Existem diferentes ações que desencadeiam uma notificação, como quando uma política, perfil ou app é atribuída (ou não atribuída), atualizada, eliminada, e assim por diante. Estes tempos de ação variam entre plataformas.

Os dispositivos fazem o check-in com o Intune quando recebem uma notificação para fazer o check-in ou durante o check-in agendado. Quando se direciona um dispositivo ou utilizador com uma ação, como bloqueio, reset de código de acesso, app, perfil ou atribuição de políticas, em seguida, Intune notifica imediatamente o dispositivo para fazer o check-in para receber estas atualizações.

Outras alterações, como a revisão das informações de contacto na aplicação Portal da Empresa, não provocam uma notificação imediata aos dispositivos.

As definições na política ou perfil são aplicadas em cada check-in. O post de blog de atualização da [política do Windows 10 MDM](https://www.petervanderwoude.nl/post/windows-10-mdm-policy-refresh/) pode ser um bom recurso.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Se forem atribuídas várias políticas ao mesmo utilizador ou dispositivo, como posso saber que definições serão aplicadas?

Quando duas ou mais políticas são atribuídas ao mesmo utilizador ou dispositivo, então a definição que se aplica acontece ao nível de definição individual:

- As definições de política de conformidade têm sempre precedência sobre as definições de perfil de configuração.

- Se uma política de conformidade avaliar a mesma definição noutra política de conformidade, então aplica-se a definição de política de conformidade mais restritiva.

- Se uma política de configuração que estabelece conflitos com uma definição noutra política de configuração, este conflito é mostrado em Intune. Deve resolver estes conflitos manualmente.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>O que acontece quando as políticas de proteção de aplicações estão em conflito entre si? Qual delas é aplicada na aplicação?

Os valores de conflito são as definições mais restritivas disponíveis numa política de proteção de aplicações, *com exceção* dos campos de entrada de números, tais como tentativas pin antes de reset. Os campos de entrada de números são definidos da mesma forma que os valores, como se tivesse criado uma política MAM utilizando a opção de definições recomendada.

Os conflitos acontecem quando duas definições de perfil são as mesmas. Por exemplo, se configurou duas políticas MAM idênticas, à exceção da definição de copiar/colar. Neste cenário, a definição de copiar/colar está definida para o valor mais restritivo, mas as definições restantes são aplicadas conforme configuradas.

Uma política é implementada para a app e faz efeito. Uma segunda política está implementada. Neste cenário, a primeira política tem precedência e mantém-se aplicada. A segunda política mostra um conflito. Se ambos forem aplicados ao mesmo tempo, o que significa que não há política anterior, então ambos estão em conflito. As definições em conflito são definidas para os valores mais restritivos.

## <a name="what-happens-when-iosipados-custom-policies-conflict"></a>O que acontece quando as políticas personalizadas iOS/iPadOS entram em conflito?

O Intune não avalia o payload dos ficheiros do Apple Configurator nem de políticas OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personalizadas. Serve apenas como o mecanismo de entrega.

Ao atribuir uma política personalizada, confirme que as configurações configuradas não entram em conflito com a conformidade, configuração ou outras políticas personalizadas. Se uma política personalizada e as suas configurações entram em conflito, as definições são aplicadas aleatoriamente.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>O que acontece quando um perfil é eliminado ou deixa de ser aplicável?

Quando elimina um perfil, ou remove um dispositivo de um grupo que tem o perfil, então o perfil e as definições são removidos do dispositivo conforme descrito:

- Perfis de Wi-Fi, VPN, certificado e e-mail: estes perfis são removidos de todos os dispositivos inscritos suportados.
- Todos os outros tipos de perfil:  

  - **Dispositivos Windows e Android**: As definições não são removidas do dispositivo
  - **Dispositivos Windows Phone 8.1**: as definições seguintes são removidas:  
  
    - Palavra-passe obrigatória para desbloquear os dispositivos móveis
    - Permitir palavras-passe simples
    - Comprimento mínimo da palavra-passe
    - Tipo obrigatório de palavra-passe
    - Expiração da Palavra-passe (dias)
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
    - Permitir tethering Wi-Fi
    - Permitir ligação automática a hotspots Wi-Fi
    - Permitir relatórios de hotspots Wi-Fi
    - Permitir a limpeza
    - Permitir Bluetooth
    - Permitir NFC
    - Permitir Wi-Fi

  - **iOS/iPadOS**: Todas as definições são removidas, exceto:
  
    - Permitir chamadas em roaming
    - Permitir roaming de dados
    - Permitir sincronização automática em roaming

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Alterei um perfil de restrição de dispositivos, mas as alterações ainda não foram aplicadas

Uma vez definidos, os dispositivos Windows Phone não permitem que as políticas de segurança definidas utilizando MDM ou EAS sejam reduzidas em segurança. Por exemplo, define um **número mínimo de senha de caracteres** para 8. Tenta reduzi-lo a 4. O perfil mais restritivo já é aplicado ao dispositivo.

Para mudar o perfil para um valor menos seguro, então redefinir as políticas de segurança. Por exemplo, no Windows 8.1, no ambiente de trabalho, passe para a direita > selecione **Definições** > **Painel de Controlo**. Selecione a miniaplicação **Contas de Utilizador** . No menu de navegação à esquerda, existe uma ligação de Políticas de **Segurança redefinida** (em direção ao fundo). Selecione-a e, em seguida, selecione **Repor Políticas**.

Outros dispositivos MDM, como Android, Windows Phone 8.1 e posteriormente, iOS/iPadOS e Windows 10 podem ter de ser retirados, e reinscritos em Intune para aplicar um perfil menos restritivo.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Algumas definições numa devolução de perfil do Windows 10 "Não Aplicável"

Algumas definições nos dispositivos do Windows 10 podem apresentar como "Não Aplicável". Quando isso acontece, essa definição específica não é suportada na versão ou edição do Windows em execução no dispositivo. Esta mensagem pode ocorrer pelas seguintes razões:

- A definição está apenas disponível para versões mais recentes do Windows, e não para a versão atual do sistema operativo (OS) no dispositivo.
- A definição só está disponível para edições específicas do Windows ou SKUs específicas, tais como Home, Professional, Enterprise e Education.

Para saber mais sobre a versão e os requisitos sKU para as diferentes definições, consulte a referência do Fornecedor de Serviços de [Configuração (CSP).](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference)

## <a name="next-steps"></a>Passos Seguintes

Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).
