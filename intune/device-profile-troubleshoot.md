---
title: Resolução de problemas de perfis de dispositivo no Microsoft Intune – Azure | Microsoft Docs
description: Problemas comuns com perfis de dispositivos, incluindo alterações de perfis que não foram aplicadas a alguns utilizadores ou dispositivos, o tempo que uma política demora a ser imposta aos dispositivos, as definições que são aplicadas quando existem múltiplas políticas, o que acontece quando um perfil é eliminado ou removido e mais no Microsoft Intune no portal do Azure
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 1/10/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: heenamac
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 32281ae37b7b36dfbf49503275a8a1e6c35d8f6d
ms.sourcegitcommit: 513c59a23ca5dfa80a3ba6fc84068503a4158757
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/11/2019
ms.locfileid: "54210793"
---
# <a name="common-issues-and-resolutions-with-device-profiles-in-microsoft-intune"></a>Problemas comuns com perfis de dispositivos e respetivas soluções no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Resolva problemas comuns ao utilizar perfis de dispositivos do Intune.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Por que razão um utilizador não obtém um novo perfil quando altera uma palavra-passe ou frase de acesso num perfil de Wi-Fi existente? 
Suponhamos que cria um perfil de Wi-Fi empresarial, implementa o perfil num grupo, altera a palavra-passe e guarda o perfil. Quando o perfil é alterado, alguns utilizadores podem não receber o novo perfil.

Para mitigar este problema, configure o Wi-Fi de convidado. Se o Wi-Fi empresarial falhar, os utilizadores podem ligar-se ao Wi-Fi de convidado. Certifique-se de que ativa todas as definições de ligação automática. Implemente o perfil de Wi-Fi convidado para todos os utilizadores.

Algumas recomendações adicionais:  

- Uma vez que a rede Wi-Fi a que se está a ligar utiliza uma palavra-passe ou frase de acesso, certifique-se de que pode ligar diretamente ao router do Wi-Fi. Pode testar com um dispositivo iOS.
- Depois de se ligar com êxito ao ponto final do Wi-Fi (router do Wi-Fi), tenha em atenção o SSID e a credencial utilizados (este valor será a palavra-passe ou a frase de acesso).
- Introduza o SSID e a credencial (palavra-passe ou frase de acesso) no campo Chave Pré-partilhada. 
- Implemente num grupo de teste com um número de utilizadores limitado, preferencialmente apenas a equipa de TI. 
- Sincronize o seu dispositivo iOS com o Intune. Inscreva-o caso ainda não o tenha feito. 
- Tente ligar-se novamente ao mesmo ponto final do Wi-Fi (como mencionado no primeiro passo).
- Implemente em grupos maiores e, por fim, em todos os utilizadores esperados na sua organização. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>Quanto tempo é necessário para que os dispositivos móveis obtenham a política ou as aplicações após a atribuição?
Quando uma política ou aplicação é atribuída, o Intune começa imediatamente a notificar o dispositivo para dar entrada no serviço do Intune. Geralmente, a notificação demora menos de cinco minutos.

Se um dispositivo não der entrada para obter uma política após o envio da primeira notificação, o Intune faz mais três tentativas. Se o dispositivo estiver offline (por exemplo, se estiver desligado ou se não estiver ligado a uma rede), pode não receber as notificações. Neste caso, o dispositivo obtém a política na próxima entrada agendada com o serviço do Intune, da seguinte forma:

- iOS e macOS: Cada seis horas
- Android: Cada oito horas
- Windows Phone: Cada oito horas
- Windows 8.1 e Windows 10 PCs inscritos como dispositivos: Cada oito horas

Se o dispositivo foi inscrito recentemente, a frequência da entrada é maior, conforme se segue:

- iOS e macOS: Cada 15 minutos durante seis horas e, em seguida, a cada seis horas
- Android: Cada três minutos durante 15 minutos, depois a cada 15 minutos durante duas horas e, em seguida, a cada oito horas
- Windows Phone: Cada cinco minutos durante 15 minutos, depois a cada 15 minutos durante duas horas e, em seguida, a cada oito horas
- PCs com Windows inscritos como dispositivos: Cada três minutos durante 30 minutos e, em seguida, a cada oito horas

Para verificarem imediatamente a política a qualquer altura, os utilizadores podem abrir a aplicação Portal da Empresa e sincronizar o dispositivo.

Para os dispositivos sem afinidade do utilizador, a frequência de sincronização imediatamente a seguir à inscrição pode variar de horas para um dia ou mais. O Intune envia pedidos em vários intervalos para um dispositivo dar entrada no serviço. No entanto, é o dispositivo que tem de dar entrada. Após a inscrição inicial, consoante o tipo de inscrição do dispositivo e as políticas e perfis atribuídos a um dispositivo, não é possível prever o tempo que um dispositivo demora a concluir a entrada. Contudo, assim que o dispositivo estiver inscrito e todas as políticas iniciais forem aplicadas, o dispositivo geralmente procura novas políticas a cada seis horas.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Que ações fazem o Intune enviar de imediato uma notificação para um dispositivo?
Os dispositivos dão entrada no Intune quando recebem uma notificação para darem entrada ou durante as entradas agendadas regulares. Quando direciona uma ação para um dispositivo ou utilizador, tal como uma eliminação, um bloqueio, uma reposição de código de acesso, uma atribuição de aplicações, uma atribuição de perfis ou uma atribuição de políticas, o Intune notifica imediatamente o dispositivo para dar entrada no serviço do Intune para receber estas atualizações.

Outras alterações, como a revisão das informações de contacto no portal da empresa, não dão origem a uma notificação imediata para os dispositivos.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Se forem atribuídas várias políticas ao mesmo utilizador ou dispositivo, como posso saber que definições serão aplicadas?
Se forem atribuídas duas ou mais políticas ao mesmo utilizador ou dispositivo, as definições a aplicar vão ocorrer ao nível das definições individuais:

- As definições de políticas de conformidade têm sempre precedência sobre as definições de políticas de configuração

- Se uma política de conformidade for avaliada em comparação com a mesma definição noutra política de conformidade, será aplicada a política de conformidade mais restritiva.

- Se uma definição de política de configuração entrar em conflito com uma definição de uma política de configuração diferente, este conflito é apresentado no portal do Azure. Neste cenário, resolva estes conflitos manualmente.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>O que acontece quando as políticas de proteção de aplicações estão em conflito entre si? Qual delas é aplicada na aplicação?
Os valores em conflito são as definições mais restritivas disponíveis numa política de proteção de aplicação, exceto no que respeita aos campos de entrada de números (como tentativas de PIN antes da reposição). Os campos de entrada de números são definidos como os valores, como se tivesse criado uma política de MAM na consola através da opção de definições recomendadas.

Os conflitos ocorrem quando duas definições de perfil são iguais. Por exemplo, se configurou duas políticas MAM idênticas, à exceção da definição de copiar/colar. Neste cenário, a definição de copiar/colar está definida para o valor mais restritivo, mas as definições restantes são aplicadas conforme configuradas.

Se for atribuído um perfil à aplicação e entrar em vigor e, em seguida, for atribuído um segundo, o primeiro atribuído tem precedência e manter-se-á aplicado, ao passo que o segundo estará em conflito. Se forem aplicados ao mesmo tempo, o que significa que nenhum perfil tem precedência sobre o outro, estarão ambos em conflito. As definições em conflito são definidas para os valores mais restritivos.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>O que acontece quando políticas personalizadas do iOS entram em conflito?
O Intune não avalia o payload dos ficheiros Apple Configuration nem dos perfis OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personalizados. Serve apenas como o mecanismo de entrega.

Quando atribuir um perfil personalizado, confirme que as definições configuradas não entram em conflito com a política de conformidade, de configuração ou outras políticas personalizadas. Se um perfil personalizado e as respetivas definições entrarem em conflito, as definições são aplicadas aleatoriamente.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>O que acontece quando um perfil é eliminado ou deixa de ser aplicável?
Quando elimina um perfil ou remove um dispositivo de um grupo que contém o perfil, este último e as definições são removidos do dispositivo de acordo com as seguintes listas:

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
Os dispositivos Windows Phone não permitem que as políticas de segurança definidas através de MDM ou EAS sejam reduzidas em termos de segurança depois de serem configuradas. Por exemplo, defina um **Número mínimo de carateres de palavra-passe** para 8 e, em seguida, tente reduzir para 4. O perfil mais restritivo já foi aplicado ao dispositivo.

Se quiser alterar o perfil para um valor menos seguro, reponha as políticas de segurança. Por exemplo, no ambiente de trabalho do Windows 8.1, percorra a partir da direita e selecione **Definições** > **Painel de Controlo**. Selecione a miniaplicação **Contas de Utilizador** . No menu de navegação esquerdo, existe uma ligação denominada **Repor Políticas de Segurança** (na parte inferior). Selecione-a e, em seguida, selecione **Repor Políticas**.

Outros dispositivos MDM, como Android, Windows Phone 8.1 e posterior, iOS e Windows 10, poderão ter de ser extintos e reinscritos no serviço para aplicar um perfil menos restritivo.

## <a name="some-settings-in-a-windows-10-profile-return-not-applicable"></a>Algumas definições no perfil do Windows 10 retornam "Não aplicável"
Algumas definições em dispositivos Windows 10 podem mostrar como "Não aplicável". Quando isto acontecer, essa definição específica não é suportada na versão ou edição do Windows em execução no dispositivo. Esta mensagem pode ocorrer pelos seguintes motivos:

- A definição só está disponível para versões mais recentes do Windows e não a atual versão de sistema operativo (SO) no dispositivo.
- A definição só está disponível para edições específicas do Windows ou SKUs específicos, tais como Home, Professional, Enterprise e Education.

Para saber mais sobre a versão e os requisitos de SKU para as diferentes configurações, consulte a [referência de fornecedor de serviços de configuração (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference).

## <a name="next-steps"></a>Passos Seguintes
Precisa de ajuda adicional? Veja [Como obter suporte para o Microsoft Intune](get-support.md).
