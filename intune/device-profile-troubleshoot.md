---
title: Resolução de problemas de perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Comuns perguntas e respostas com políticas de dispositivos e perfis, incluindo alterações do perfil não é aplicadas a utilizadores ou dispositivos, o tempo que demora para novas políticas a ser imposta aos dispositivos, quais configurações são aplicadas quando existem múltiplas políticas, o que acontece quando um perfil é eliminado ou removido e mais com o Microsoft Intune.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8c95ed6f865795c2e9638e4975b51bee4678013d
ms.sourcegitcommit: cb93613bef7f6015a4c4095e875cb12dd76f002e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57231541"
---
# <a name="common-questions-issues-and-resolutions-with-device-policies-and-profiles-in-microsoft-intune"></a>Perguntas comuns, problemas e resoluções com as políticas de dispositivos e perfis no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Obtenha respostas a perguntas comuns ao trabalhar com perfis de dispositivo e as políticas no Intune. Este artigo também listas que os intervalos de tempo de entrada, fornece mais detalhes da em conflitos e muito mais.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Por que razão um utilizador não obtém um novo perfil quando altera uma palavra-passe ou frase de acesso num perfil de Wi-Fi existente?

Suponhamos que cria um perfil de Wi-Fi empresarial, implementa o perfil num grupo, altera a palavra-passe e guarda o perfil. Quando o perfil é alterado, alguns utilizadores podem não receber o novo perfil.

Para mitigar este problema, configure o Wi-Fi de convidado. Se o Wi-Fi empresarial falhar, os utilizadores podem ligar-se ao Wi-Fi de convidado. Certifique-se de que ativa todas as definições de ligação automática. Implemente o perfil de Wi-Fi convidado para todos os utilizadores.

Algumas recomendações adicionais:  

- Se a rede Wi-Fi que está a ligar a utilizar uma palavra-passe ou frase de acesso, certifique-se de que pode ligar diretamente ao router do Wi-Fi. Pode testar com um dispositivo iOS.
- Depois de se ligar com êxito ao ponto final do Wi-Fi (router do Wi-Fi), tenha em atenção o SSID e a credencial utilizados (este valor será a palavra-passe ou a frase de acesso).
- Introduza o SSID e a credencial (palavra-passe ou frase de acesso) no campo Chave Pré-partilhada. 
- Implemente num grupo de teste com um número de utilizadores limitado, preferencialmente apenas a equipa de TI. 
- Sincronize o seu dispositivo iOS com o Intune. Inscreva-o caso ainda não o tenha feito. 
- Tente ligar-se novamente ao mesmo ponto final do Wi-Fi (como mencionado no primeiro passo).
- Implemente em grupos maiores e, por fim, em todos os utilizadores esperados na sua organização. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>Quanto tempo é necessário para que os dispositivos móveis obtenham a política ou as aplicações após a atribuição?

Quando uma política ou aplicação é atribuída, o Intune começa imediatamente a notificar o dispositivo para dar entrada no serviço do Intune. Geralmente, a notificação demora menos de cinco minutos.

Se um dispositivo não der entrada para obter a política após a primeira notificação, o Intune faz mais três tentativas. Um dispositivo offline, tal como desativada ou não ligado a uma rede, poderá não receber as notificações. Neste caso, o dispositivo obtém a política na entrada seguinte agendada verificação com o serviço do Intune, o que é:

| Plataforma | Ciclo de atualização|
| --- | --- |
| iOS | A cada 6 horas |
| macOS | A cada 6 horas |
| Android | A cada 8 horas |
| PCs com o Windows 10 inscritos como dispositivos | A cada 8 horas |
| Windows Phone | A cada 8 horas |
| Windows 8.1 | A cada 8 horas |

Se o dispositivo inscrito recentemente, o check-in é executado com mais frequência:

| Plataforma | Frequência |
| --- | --- |
| iOS | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas |  
| Mac OS X | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas | 
| Android | A cada 3 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| Windows Phone | A cada 5 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| Computadores com o Windows inscritos como dispositivos | A cada 3 minutos durante 30 minutos e, em seguida, a cada 8 horas | 

Em qualquer altura, os utilizadores podem abrir a aplicação Portal da empresa e sincronizar o dispositivo para verificar imediatamente a existência de atualizações de perfil.

Para dispositivos sem afinidade do utilizador, a frequência de sincronização imediatamente a seguir à inscrição pode variar de horas para um dia ou mais. O Intune envia pedidos em vários intervalos para um dispositivo para dar entrada no Intune. No entanto, é o dispositivo para check-in. Após a inscrição inicial, o tempo que demora um dispositivo para concluir o check-in é imprevisível. Também depende do tipo de inscrição de dispositivos e as políticas e perfis atribuídos a um dispositivo. Depois do dispositivo é inscrito e todas as políticas iniciais forem aplicadas, o dispositivo geralmente procura novas políticas a cada 6 a 8 horas.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Que ações fazem o Intune enviar de imediato uma notificação para um dispositivo?

Dispositivos dar entrada no Intune quando recebem uma notificação para entrada ou durante o check-in agendado. Quando segmenta um dispositivo ou utilizador com uma ação, tal como o bloqueio, reposição de código de acesso, atribuição de aplicações, atribuição de política de perfil ou, em seguida, o Intune notifica imediatamente o dispositivo para check-in para receber estas atualizações.

Outras alterações como a revisão das informações de contacto no portal da empresa não dão origem ao envio de uma notificação imediata para os dispositivos.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Se forem atribuídas várias políticas ao mesmo utilizador ou dispositivo, como posso saber que definições serão aplicadas?

Quando duas ou mais políticas são atribuídas ao mesmo utilizador ou dispositivo, em seguida, a definição que se aplica ocorre ao nível das definições individuais:

- Definições de política de conformidade têm sempre precedência sobre as definições de perfil de configuração.

- Se uma política de conformidade for avaliada em relação a mesma definição noutra política de conformidade, aplica-se a definição de política de conformidade mais restritiva.

- Se uma política de configuração, definição está em conflito com uma definição de política de configuração de outro, este conflito é apresentado no Intune. Deve resolver estes conflitos manualmente.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>O que acontece quando as políticas de proteção de aplicações estão em conflito entre si? Qual delas é aplicada na aplicação?

Os valores em conflito são as definições mais restritivas disponíveis numa política de proteção de *exceto* para os campos de entrada de números, como tentativas PIN antes da reposição. Os campos de entrada de números são definidos como os valores, como se tivesse criado uma política de MAM utilizando a opção de definições recomendadas.

Conflitos ocorrem quando duas definições de perfil são iguais. Por exemplo, se configurou duas políticas MAM idênticas, à exceção da definição de copiar/colar. Neste cenário, a definição de copiar/colar está definida para o valor mais restritivo, mas as definições restantes são aplicadas conforme configuradas.

Uma política é implementada na aplicação e entrar em vigor. Uma segunda política é implementada. Neste cenário, a primeira diretiva tem precedência e permanece aplicada. A segunda política mostra um conflito. Se ambos forem aplicadas ao mesmo tempo, o que significa que não existe política precedente, em seguida, ambos estão em conflito. As definições em conflito são definidas para os valores mais restritivos.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>O que acontece quando políticas personalizadas do iOS entram em conflito?

O Intune não avalia o payload dos ficheiros do Apple Configurator nem de políticas OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personalizadas. Serve apenas como o mecanismo de entrega.

Quando atribui uma política personalizada, certifique-se que as definições configuradas não entram em conflito com a conformidade, configuração ou outras políticas personalizadas. Se uma política personalizada e as respetivas definições entrarem em conflito, as definições são aplicadas aleatoriamente.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>O que acontece quando um perfil é eliminado ou deixa de ser aplicável?

Quando elimina um perfil ou remove um dispositivo de um grupo que tenha o perfil, o perfil e as definições são removidas do dispositivo, tal como descrito:

- Wi-Fi, VPN, certificado e perfis de e-mail: Estes perfis são removidos de todos os dispositivos inscritos suportados.
- Todos os outros tipos de perfil:  

  - **Windows e dispositivos Android**: As definições não são removidas do dispositivo
  - **Dispositivos Windows Phone 8.1**: As seguintes definições são removidas:  
  
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

  - **iOS**: Todas as definições são removidas, exceto:
  
    - Permitir chamadas em roaming
    - Permitir roaming de dados
    - Permitir sincronização automática em roaming

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Alterei um perfil de restrição de dispositivos, mas as alterações ainda não foram aplicadas

Uma vez definida, os dispositivos Windows Phone não permitem políticas de segurança definidas através de MDM ou EAS sejam reduzidas em termos de segurança. Por exemplo, define um **número mínimo de palavra-passe de caráter** para 8. Tente reduzir para 4. O perfil mais restritivo já está a ser aplicado ao dispositivo.

Para alterar o perfil para um valor menos seguro, em seguida, repor as políticas de segurança. Por exemplo, no Windows 8.1, na área de trabalho, percorra a partir da direita > selecione **configurações** > **painel de controlo**. Selecione a miniaplicação **Contas de Utilizador** . No menu de navegação esquerdo, existe uma **repor políticas de segurança** link (na direção da parte inferior). Selecione-a e, em seguida, selecione **Repor Políticas**.

Outros dispositivos MDM, tal como Android, Windows Phone 8.1 e posterior, iOS e Windows 10 poderão ter de ser extintos e reinscritos no Intune para aplicar um perfil menos restritivo.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Algumas definições no perfil do Windows 10 retornam "Não aplicável"

Algumas definições em dispositivos Windows 10 podem mostrar como "Não aplicável". Quando isto acontecer, essa definição específica não é suportada na versão ou edição do Windows em execução no dispositivo. Esta mensagem pode ocorrer pelos seguintes motivos:

- A definição só está disponível para versões mais recentes do Windows e não a atual versão de sistema operativo (SO) no dispositivo.
- A definição só está disponível para edições específicas do Windows ou SKUs específicos, tais como Home, Professional, Enterprise e Education.

Para saber mais sobre a versão e os requisitos de SKU para as diferentes configurações, consulte a [referência de fornecedor de serviços de configuração (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Passos Seguintes

Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](get-support.md).
