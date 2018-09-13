---
title: Políticas, perfis e perguntas e respostas sobre dispositivos com o Intune – Azure | Microsoft Docs
description: Leia sobre as diferentes políticas e perfis que pode utilizar no Microsoft Intune, incluindo políticas para configurar dispositivos, obter acesso aos recursos da empresa, ativar o acesso condicional e inscrever dispositivos da empresa. Obtenha também respostas a perguntas frequentes.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 6/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ROBOTS: ''
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: e8a7a7405fe40d3568e736c244d9fcb308350709
ms.sourcegitcommit: 4d314df59747800169090b3a870ffbacfab1f5ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/30/2018
ms.locfileid: "43317912"
---
# <a name="manage-settings-and-features-on-your-devices-with-intune-policies"></a>Gerir definições e funcionalidades no seu dispositivo com as políticas do Intune

As *políticas* do Microsoft Intune são grupos de definições que controlam funcionalidades em dispositivos móveis e computadores. Para criar políticas, é necessário utilizar modelos que incluam definições recomendadas ou personalizadas. Em seguida, é necessário implementá-las em grupos de dispositivos ou utilizadores.

## <a name="types-of-policies"></a>Tipos de políticas

As políticas do Intune inserem-se nas categorias seguintes. A categoria que utilizar afeta a forma como cria e implementa a política.

- **Políticas de configuração**: frequentemente utilizadas para gerir as funcionalidades e as definições de segurança nos seus dispositivos, incluindo o acesso aos recursos da empresa. Comece a utilizar [perfis de dispositivo do Intune](device-profiles.md).
- **Políticas de conformidade de dispositivos**: definem as regras e as definições que um dispositivo tem de cumprir para ser considerado conforme com as políticas de acesso condicional. Também pode utilizar as políticas de conformidade para monitorizar e resolver a conformidade dos dispositivos independentemente do acesso condicional. Comece a utilizar [políticas de conformidade de dispositivos](device-compliance-get-started.md).
- **Políticas de acesso condicional**: ajudam-no a proteger o e-mail e outros serviços, dependendo das condições que introduzir. [O que é o acesso condicional?](conditional-access.md) e [Formas comuns de utilizar o acesso condicional](conditional-access-intune-common-ways-use.md) são bons recursos para começar.
- **Políticas de inscrição de dispositivos da empresa**: para obter informações sobre as políticas de inscrição de dispositivos da empresa, veja [Inscrever dispositivos iOS](ios-enroll.md).

## <a name="frequently-asked-questions-about-intune-policies"></a>Perguntas mais frequentes sobre as políticas do Intune

### <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-being-deployed"></a>Quanto tempo é necessário para que os dispositivos móveis obtenham a política ou as aplicações após a implementação?
Quando uma política ou aplicação é implementada, o Intune começa imediatamente a notificar o dispositivo para dar entrada no serviço do Intune. Geralmente, este passo demora menos de cinco minutos.

Se um dispositivo não der entrada para obter uma política após o envio da primeira notificação, o Intune faz mais três tentativas.  Se o dispositivo estiver offline (por exemplo, se estiver desligado ou se não estiver ligado a uma rede), pode não receber as notificações. Neste caso, o dispositivo obtém a política na próxima entrada agendada com o serviço do Intune, da seguinte forma:

| Plataforma | Frequência de entrada |
| --- | --- |
| iOS | A cada 6 horas | 
| Mac OS X | A cada 6 horas |
| Android | A cada 8 horas | 
| Windows Phone | A cada 8 horas | 
| Windows 8,1  | A cada 8 horas |  
| PCs com o Windows 10 inscritos como dispositivos | A cada 8 horas | 

Se o dispositivo foi inscrito recentemente, a frequência da entrada é maior, conforme se segue:

| Plataforma | Frequência |
| --- | --- |
| iOS | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas |  
| Mac OS X | A cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas | 
| Android | A cada 3 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| Windows Phone | A cada 5 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas | 
| Computadores com o Windows inscritos como dispositivos | A cada 3 minutos durante 30 minutos e, em seguida, a cada 8 horas | 

Os utilizadores também podem abrir a aplicação Portal da Empresa e sincronizar o dispositivo para verificar imediatamente a política a qualquer altura.

### <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Que ações fazem o Intune enviar de imediato uma notificação para um dispositivo?
Os dispositivos dão entrada no Intune quando recebem uma notificação a solicitar-lhes que deem entrada ou durante as entradas agendadas regulares.  Quando define um dispositivo ou utilizador como o visado de uma ação, tal como uma limpeza, um bloqueio, uma reposição de código de acesso, uma implementação de aplicação, implementação de perfil (Wi-Fi, VPN, e-mail) ou uma implementação de política, o Intune tenta imediatamente notificar o dispositivo para dar entrada no serviço do Intune.

Outras alterações como a revisão das informações de contacto no portal da empresa não dão origem ao envio de uma notificação imediata para os dispositivos.

### <a name="if-multiple-policies-are-deployed-to-the-same-user-or-device-how-do-i-know-which-settings-are-applied"></a>Se forem implementadas múltiplas políticas para o mesmo utilizador ou dispositivo, como posso saber que definições foram aplicadas?
Quando são implementadas duas ou mais políticas no mesmo utilizador ou dispositivo, a avaliação relativa à definição que foi aplicada é realizada ao nível das definições individuais:

- As definições de políticas de conformidade têm sempre precedência sobre as definições de políticas de configuração.

- A definição de políticas de conformidade mais restritivas aplica-se se for avaliada em comparação com a mesma definição numa política de conformidade diferente.

- Se uma definição de política de configuração entrar em conflito com uma definição de uma política de configuração diferente, este conflito é apresentado no Intune. Deve resolver estes conflitos manualmente.

### <a name="what-happens-when-mobile-application-management-policies-conflict-with-each-other-which-one-applies-to-the-app"></a>O que acontece quando as políticas de gestão de aplicações móveis entram em conflito entre si? Qual delas é que se aplica à aplicação?
Os valores em conflito são as definições mais restritivas disponíveis numa política de MAM, exceto no que respeita aos campos de entrada de números (como tentativas de PIN antes da reposição).  Os campos de entrada de números são definidos como os valores, como se tivesse criado uma política de MAM na consola através da opção de definições recomendadas.

Os conflitos ocorrem quando duas definições de políticas são iguais.  Por exemplo, se configurou duas políticas MAM idênticas, à exceção da definição de copiar/colar.  Neste cenário, a definição de copiar/colar está definida para o valor mais restritivo, mas as definições restantes são aplicadas conforme configuradas.

Se uma política for implementada na aplicação e entrar em vigor e, em seguida, for implementada uma segunda, a primeira aplicação terá precedência e manter-se-á aplicada. A segunda política será apresentada como estando em conflito. Se forem aplicadas ao mesmo tempo, o que significa que nenhuma tem precedência sobre a outra, estarão ambas em conflito. As definições em conflito são definidas para os valores mais restritivos.

### <a name="what-happens-when-ios-custom-policies-conflict"></a>O que acontece quando políticas personalizadas do iOS entram em conflito?
O Intune não avalia o payload dos ficheiros do Apple Configurator nem de políticas OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personalizadas. Serve apenas como o mecanismo de entrega.

Quando implementar uma política personalizada, confirme que as definições configuradas não entram em conflito com a política de conformidade ou de configuração nem com outras políticas personalizadas. Se uma política personalizada com definições entrar em conflito, a ordem pela qual as definições são aplicadas é aleatória.

### <a name="what-happens-when-a-policy-is-deleted-or-no-longer-applicable"></a>O que acontece quando uma política é eliminada ou deixa de ser aplicável?
Quando eliminar uma política ou remover um dispositivo de um grupo que tenha uma política implementada, a política e as definições serão removidas do dispositivo de acordo com as listas seguintes.

#### <a name="enrolled-devices"></a>Dispositivos inscritos

- Perfis de Wi-Fi, VPN, certificado e e-mail: estes perfis são removidos de todos os dispositivos inscritos suportados.
- Todos os outros tipos de políticas:
  - **Dispositivos Windows e Android**: as definições não são removidas do dispositivo.
  - **Dispositivos Windows Phone 8.1**: as definições seguintes são removidas:
    - Palavra-passe obrigatória para desbloquear os dispositivos móveis
    - Permitir palavras-passe simples
    - Comprimento mínimo da palavra-passe
    - Tipo obrigatório de palavra-passe
    - Expiração da Palavra-passe (dias)
    - Memorizar histórico de palavras-passe
    - Número de falhas de início de sessão consecutivas a permitir antes do dispositivo ser apagado
    - Minutos de inatividade antes da palavra-passe ser exigida
    - Tipo obrigatório de palavra-passe – número mínimo de conjuntos de carateres
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

### <a name="where-can-i-find-help-troubleshooting-policies"></a>Onde posso encontrar as políticas de resolução de problemas?

Veja [Troubleshoot policies](troubleshoot-policies-in-microsoft-intune.md) (Resolução de problemas relacionados com políticas).
