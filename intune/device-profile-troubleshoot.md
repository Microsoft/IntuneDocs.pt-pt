---
title: Resolver problemas de perfis de dispositivos no Microsoft Intune
titlesuffix: Azure portal
description: "Se estiver com dificuldades, utilize este tópico para o ajudar a resolver problemas com perfis de dispositivos do Intune.\""
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 1/17/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 0bc5ad6e0467fe8a8c98c1ad2d71b967c18b8233
ms.sourcegitcommit: 967a7c23b863123398c40b812e2eb02c921a0afe
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/18/2018
---
# <a name="troubleshooting-device-profiles-in-microsoft-intune"></a>Resolver problemas de perfis de dispositivos no Microsoft Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

As informações neste tópico podem servir para o ajudar a resolver problemas comuns sobre perfis de dispositivos do Intune.

## <a name="why-doesnt-a-user-get-a-new-profile-when-changing-a-password-or-passphrase-on-an-existing-wi-fi-profile"></a>Por que razão um utilizador não obtém um novo perfil quando altera uma palavra-passe ou frase de acesso num perfil de Wi-Fi existente? 
Quando cria um perfil de Wi-Fi empresarial, implementa o perfil num grupo, altera a palavra-passe e guarda o perfil, é de esperar que o utilizador obtenha o novo perfil. No entanto, o utilizador poderá não receber o novo perfil. 

Para mitigar este problema, certifique-se de que tem um Wi-Fi convidado configurado de forma a que o utilizador regresse ao Wi-Fi convidado caso o Wi-Fi empresarial falhe. A definição de ligação automática tem de estar ativada. Este perfil de Wi-Fi convidado tem de ser implementado em todos os utilizadores.

Existem algumas melhores práticas adicionais que pode seguir:
- Uma vez que a rede Wi-Fi a que se está a ligar exige uma palavra-passe ou frase de acesso, certifique-se de que pode ligar diretamente ao router do Wi-Fi. Pode testar com um dispositivo iOS.
- Depois de se ligar com êxito ao ponto final do Wi-Fi (router do Wi-Fi), tenha em atenção o SSID e a credencial utilizados (a palavra-passe ou a frase de acesso.)
- Introduza o SSID e a credencial (palavra-passe ou frase de acesso) no campo Chave Pré-partilhada. 
- Implemente num grupo de teste com um número de utilizadores limitado, preferencialmente, apenas a equipa de TI. 
- Sincronize o seu dispositivo iOS com o Intune. Inscreva-o caso ainda não o tenha feito. 
- Tente ligar-se novamente ao mesmo ponto final do Wi-Fi (como mencionado no primeiro passo).
- Implemente em grupos maiores e, por fim, em todos os utilizadores esperados na sua organização. 

## <a name="how-long-does-it-take-for-mobile-devices-to-get-a-policy-or-apps-after-they-have-been-assigned"></a>Quanto tempo é necessário para que os dispositivos móveis obtenham a política ou as aplicações após a atribuição?
Quando uma política ou aplicação é atribuída, o Intune começa imediatamente a tentar notificar o dispositivo que deverá dar entrada no serviço do Intune. Geralmente, o processo demora menos de cinco minutos.

Se um dispositivo não der entrada para obter uma política após o envio da primeira notificação, o Intune faz mais três tentativas. Se o dispositivo estiver offline (por exemplo, se estiver desligado ou se não estiver ligado a uma rede), pode não receber as notificações. Neste caso, o dispositivo obtém a política na próxima entrada agendada com o serviço do Intune, da seguinte forma:

- iOS e macOS: a cada seis horas.
- Android: a cada oito horas.
- Windows Phone: a cada oito horas.
- PCs com Windows 8.1 e Windows 10 inscritos como dispositivos: a cada oito horas.

Se o dispositivo tiver acabado de ser inscrito, a frequência da entrada é maior, conforme se segue:

- iOS e macOS: a cada 15 minutos durante seis horas e, em seguida, a cada seis horas.
- Android: a cada três minutos durante 15 minutos, depois a cada 15 minutos durante duas horas e, em seguida, a cada oito horas.
- Windows Phone: a cada cinco minutos durante 15 minutos, depois a cada 15 minutos durante duas horas e, em seguida, a cada oito horas.
- PCs com Windows inscritos como dispositivos: a cada três minutos durante 30 minutos e, em seguida, a cada oito horas.

Os utilizadores também podem abrir a aplicação Portal da Empresa e sincronizar o dispositivo para verificar imediatamente a política a qualquer altura.

Para os dispositivos sem afinidade do utilizador, a frequência de sincronização imediatamente a seguir à inscrição pode variar de horas para um dia ou mais. O Intune envia pedidos em vários intervalos para um dispositivo dar entrada no serviço. No entanto, é o dispositivo que tem de dar entrada. Após a inscrição inicial, consoante o tipo de inscrição do dispositivo e as políticas e perfis atribuídos a um dispositivo, não é possível prever o tempo que um dispositivo demora a concluir a entrada. Contudo, assim que o dispositivo estiver inscrito e todas as políticas iniciais tiverem sido aplicadas, o dispositivo deve procurar novas políticas a cada seis horas, aproximadamente.

## <a name="what-actions-cause-intune-to-immediately-send-a-notification-to-a-device"></a>Que ações fazem o Intune enviar de imediato uma notificação para um dispositivo?
Os dispositivos dão entrada no Intune quando recebem uma notificação a solicitar-lhes que o façam ou durante as entradas agendadas regulares. Quando direciona uma ação para um dispositivo ou utilizador, tal como uma eliminação, um bloqueio, uma reposição de código de acesso, uma atribuição de aplicações, uma atribuição de perfil (Wi-Fi, VPN, e-mail, etc.) ou uma atribuição de políticas, o Intune começa imediatamente a tentar notificar o dispositivo de que deve dar entrada no serviço do Intune para receber estas atualizações.

Outras alterações, como a revisão das informações de contacto no portal da empresa, não dão origem a uma notificação imediata para os dispositivos.

## <a name="if-multiple-policies-are-assigned-to-the-same-user-or-device-how-do-i-know-which-settings-gets-applied"></a>Se forem atribuídas várias políticas ao mesmo utilizador ou dispositivo, como posso saber que definições serão aplicadas?
Quando são atribuídas duas ou mais políticas ao mesmo utilizador ou dispositivo, a avaliação relativa à definição que vai ser aplicada é realizada ao nível das definições individuais:

-   As definições de políticas de conformidade têm sempre precedência sobre as definições de políticas de configuração.

-   A definição de política de conformidade mais restritiva é aplicada se for avaliada em comparação com a mesma definição noutra política de conformidade.

-   Se uma definição de política de configuração entrar em conflito com uma definição de uma política de configuração diferente, este conflito é apresentado no portal do Azure. Tem de resolver manualmente esses conflitos.

## <a name="what-happens-when-app-protection-policies-conflict-with-each-other-which-one-is-applied-to-the-app"></a>O que acontece quando as políticas de proteção de aplicações estão em conflito entre si? Qual delas é aplicada na aplicação?
Os valores em conflito são as definições mais restritivas disponíveis numa política de proteção de aplicação, exceto no que respeita aos campos de entrada de números (como tentativas de PIN antes da reposição). Os campos de entrada de números são definidos como os valores, como se tivesse criado uma política de MAM na consola através da opção de definições recomendadas.

Os conflitos ocorrem quando duas definições de perfil são iguais. Por exemplo, se configurou duas políticas MAM idênticas, à exceção da definição de copiar/colar. Neste cenário, a definição de copiar/colar está definida para o valor mais restritivo, mas as definições restantes são aplicadas conforme configuradas.

Se for atribuído um perfil à aplicação e entrar em vigor e, em seguida, for atribuído um segundo, o primeiro atribuído tem precedência e manter-se-á aplicado, ao passo que o segundo estará em conflito. Se forem aplicados ao mesmo tempo, o que significa que nenhum perfil tem precedência sobre o outro, estarão ambos em conflito. As definições em conflito são definidas para os valores mais restritivos.

## <a name="what-happens-when-ios-custom-policies-conflict"></a>O que acontece quando políticas personalizadas do iOS entram em conflito?
O Intune não avalia o payload dos ficheiros Apple Configuration nem dos perfis OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personalizados. Serve apenas como o mecanismo de entrega.

Quando atribuir um perfil personalizado, confirme que as definições configuradas não entram em conflito com a política de conformidade, de configuração ou outras políticas personalizadas. No caso de um perfil personalizado com conflitos de definições, a ordem pela qual as definições são aplicadas é aleatória.

## <a name="what-happens-when-a-profile-is-deleted-or-no-longer-applicable"></a>O que acontece quando um perfil é eliminado ou deixa de ser aplicável?
Quando elimina um perfil ou remove um dispositivo de um grupo no qual a política foi atribuída, o perfil e as definições são removidos do dispositivo de acordo com as listas seguintes.

### <a name="enrolled-devices"></a>Dispositivos inscritos

- Perfis de Wi-Fi, VPN, certificado e e-mail: estes perfis são removidos de todos os dispositivos inscritos suportados.
- Todos os outros tipos de perfil:
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
        - Permitir a reposição de fábrica
        - Permitir Bluetooth
        - Permitir NFC
        - Permitir Wi-Fi

    - **iOS**: todas as definições são removidas, exceto:
        - Permitir chamadas em roaming
        - Permitir roaming de dados
        - Permitir sincronização automática em roaming

## <a name="i-changed-a-device-restriction-profile-but-the-changes-havent-taken-effect"></a>Alterei um perfil de restrição de dispositivos, mas as alterações ainda não foram aplicadas
Os dispositivos Windows Phone não permitem que as políticas de segurança definidas através de MDM ou EAS sejam reduzidas em termos de segurança depois de serem configuradas. Por exemplo, defina um **Número mínimo de carateres de palavra-passe** para 8 e, em seguida, tente reduzir para 4. O perfil mais restritivo já foi aplicado ao dispositivo.

Consoante a plataforma de dispositivo, se pretender alterar o perfil para um valor menos seguro, poderá ter de repor as políticas de segurança.
Por exemplo, no ambiente de trabalho do Windows, percorra a partir da direita para abrir a barra **Atalhos** e selecione **Definições** &gt; **Painel de Controlo**. Selecione a miniaplicação **Contas de Utilizador** .
No menu de navegação esquerdo, existe uma ligação **Repor Políticas de Segurança** na parte inferior. Escolha a mesma e, em seguida, escolha o botão **Repor Políticas**.
Outros dispositivos MDM, tal como Android, Windows Phone 8.1 e posterior e iOS, poderão ter de ser extintos e reinscritos no serviço para que possa aplicar um perfil menos restritivo.


### <a name="next-steps"></a>Próximos passos
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](get-support.md).