---
title: "Gerir definições de dispositivos com políticas | Microsoft Intune"
description: "Utilize o Intune para criar e implementar políticas que controlam as definições e funcionalidades em dispositivos que gere."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 10/11/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2
ms.reviewer: heenamac
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e95db6d0ccbe350984f11ce08749b700c2f5ad01
ms.openlocfilehash: 058843a1cdd0ca4c32c7cc4d7a901e7547da633e


---

# Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune
As *políticas* do Microsoft Intune são grupos de definições que controlam funcionalidades em dispositivos móveis e computadores. As políticas são criadas com modelos que contêm definições recomendadas ou personalizadas e, depois, implementadas em grupos de dispositivos ou de utilizadores.

## Tipos de políticas

As políticas do Intune inserem-se nas categorias seguintes. A categoria que utilizar afeta a forma como cria e implementa a política.


- **Políticas de configuração**: estas políticas são frequentemente utilizadas para gerir as funcionalidades e as definições de segurança nos seus dispositivos. Utilize as informações deste tópico para saber como criar e implementar estas políticas e para explorar as definições disponíveis.
- **Políticas de conformidade do dispositivo**: estas políticas definem as regras e as definições que um dispositivos tem de cumprir para ser considerado conforme pelas políticas de acesso condicional. Também pode utilizar as políticas de conformidade para monitorizar e resolver a conformidade dos dispositivos independentemente do acesso condicional.
Para obter detalhes, consulte [Políticas de conformidade de dispositivos no Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- **Políticas de acesso condicional**: estas políticas ajudam-no a proteger o e-mail e outros serviços, dependendo das condições que especificar.
Para obter detalhes, consulte [Restringir o acesso ao e-mail e aos serviços do O365 com o Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).
- **Políticas de inscrição de dispositivos da empresa**: para obter informações sobre as políticas de inscrição de dispositivos da empresa, consulte [Configurar a gestão de iOS e Mac com o Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Políticas de acesso a recursos:** estas políticas funcionam em conjunto para ajudar os seus utilizadores a obterem acesso aos ficheiros e recursos de que precisam para trabalhar com êxito, onde quer que estejam.
Para obter detalhes, consulte [Ativar o acesso aos recursos da empresa com o Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md).


Para obter uma lista completa das políticas do Intune, consulte [Referência de políticas do Microsoft Intune](microsoft-intune-policy-reference.md).




## Criar uma política de configuração

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), selecione **Política** &gt; **Políticas de Configuração** &gt; **Adicionar**.

2.  Selecione a política que pretende, escolha utilizar as definições recomendadas para a política (quando disponível; pode alterar estas definições mais tarde) ou criar uma política personalizada com as suas próprias definições.

    > [!TIP]
    > Para o ajudar a escolher a política correta, consulte [Referência de políticas do Microsoft Intune](microsoft-intune-policy-reference.md).

3.  Quando estiver pronto, selecione **Criar Política**.

4.  Na página **Criar Política**, configure um nome e uma descrição opcional para a política.

5.  Configure as definições da política necessárias e, em seguida, escolha **Guardar Política**.

    Se precisar de ajuda em quaisquer definições de política, escolha o seu tipo de política na lista seguinte:

    - [Definições para dispositivos iOS](ios-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Android](android-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Android for Work](android-for-work-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Windows 8 e Windows 8.1](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Windows Phone 8.1](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos móveis e computadores Windows 10](windows-10-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Windows Team](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Definições para a atualização da edição Windows](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Mac OS X](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Definições para o Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Definições para a política de termos e condições](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Definições gerais para dispositivos móveis (legados)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  Na caixa de diálogo de confirmação selecione **Sim** para implementar a política de imediato ou selecione **Não** para criar uma política sem a implementar.

Pode navegar pelas secções de cada tipo de política na área de trabalho **Política** para ver e editar a política nova.

Quando cria uma política que utiliza as definições recomendadas, o nome da nova política é uma combinação do nome do modelo, data e hora. Ao editar a política, o nome é atualizado com a data e hora da edição.

Depois de criar uma política, normalmente, irá querer implementá-la num ou mais grupos de utilizadores ou dispositivos.

> [!TIP]
> Não implementa todos os tipos de política. Por exemplo, a política de gestão de aplicações móveis (MAM) não é implementada. Este tipo de política está associado a uma aplicação em relação à qual o implementará.

## Implementar uma política de configuração

1.  Na área de trabalho **Política**, selecione a que pretende implementar e escolha **Gerir a Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação**, para:

    -   Para implementar a política, selecione um ou mais grupos nos quais pretende implementá-la e, em seguida, escolha **Adicionar** &gt; **OK**.

    -   Para fechar a caixa de diálogo sem implementar a política, escolha **Cancelar**.

Ao selecionar uma política implementada, pode ver mais informações sobre a implementação na parte inferior da lista de políticas.

## Gerir políticas

1.  Na [Consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Política** e, em seguida, navegue até à política que pretende gerir e selecione-a.

2.  Selecione uma das seguintes ações:

- **Editar**: abra as propriedades da política selecionada para poder fazer alterações.
- **Eliminar** – elimine a política selecionada.<br>Quando elimina uma política, esta é removida de todos os grupos nos quais estava implementada.
- **Gerir a Implementação** – selecione o grupo no qual pretende implementar a política e escolha **Adicionar**.


## Perguntas mais frequentes sobre as políticas do Intune

### Quanto tempo é necessário para que os dispositivos móveis obtenham a política ou as aplicações após a implementação?
Quando uma política ou aplicação é implementada, o Intune começa imediatamente a tentar notificar o dispositivo de que deverá dar entrada no serviço do Intune. Geralmente, o processo demora menos de cinco minutos.

Se um dispositivo não der entrada para obter uma política após o envio da primeira notificação, o Intune faz mais três tentativas.  Se o dispositivo estiver offline (por exemplo, se estiver desligado ou se não estiver ligado a uma rede), pode não receber as notificações. Neste caso, o dispositivo irá obter a política na entrada seguinte agendada com o serviço do Intune, da seguinte forma:

- iOS e Mac OS X: a cada seis horas.
- Android: a cada oito horas.
- Windows Phone: a cada oito horas.
- PCs com Windows 8.1 e Windows 10 inscritos como dispositivos: a cada oito horas.

Se o dispositivo tiver acabado de se inscrever, a frequência de entrada será maior, conforme se segue:

- iOS e Mac OS X: a cada 15 minutos durante seis horas e, em seguida, a cada seis horas.
- Android: a cada três minutos durante 15 minutos, depois a cada 15 minutos durante duas horas e, em seguida, a cada oito horas.
- Windows Phone: a cada cinco minutos durante 15 minutos, depois a cada 15 minutos durante duas horas e, em seguida, a cada oito horas.
- PCs Windows inscritos como dispositivos: a cada três minutos durante 30 minutos e, em seguida, a cada oito horas.

Os utilizadores também podem abrir a aplicação Portal da Empresa e sincronizar o dispositivo para verificar imediatamente a política a qualquer altura.

### Que ações fazem o Intune enviar de imediato uma notificação para um dispositivo?
Os dispositivos dão entrada no Intune quando recebem uma notificação a solicitar-lhes que deem entrada ou durante as entradas agendada regulares.  Quando segmenta um dispositivo ou utilizador especificamente com uma ação, tal como uma eliminação, bloqueio, reposição de código de acesso, implementação de aplicação, implementação de perfil (Wi-Fi, VPN, e-mail, etc.) ou uma implementação de política, o Intune começará imediatamente a tentar notificar o dispositivo de que deve dar entrada no serviço do Intune para receber estas atualizações.

Outras alterações, como a revisão das informações de contacto no portal da empresa, não dão origem a uma notificação imediata para os dispositivos.

### Se forem implementadas várias políticas no mesmo utilizador ou dispositivo, como posso saber que definições irão ser aplicadas?
Quando são implementadas duas ou mais políticas no mesmo utilizador ou dispositivo, a avaliação relativa à definição que vai ser aplicada é realizada ao nível das definições individuais:

-   As definições de políticas de conformidade têm sempre precedência sobre as definições de políticas de configuração.

-   A definição de política de conformidade mais restritiva é aplicada se for avaliada em comparação com a mesma definição noutra política de conformidade.

-   Se uma definição de política de configuração entrar em conflito com uma definição de uma política de configuração diferente, este conflito será apresentado na consola do Intune. Tem de resolver manualmente esses conflitos.

### O que acontece quando as políticas de gestão de aplicações móveis entram em conflito entre si? Qual delas é aplicada à aplicação?
Os valores em conflito são as definições mais restritivas disponíveis numa política de MAM, exceto no que respeita aos campos de entrada de números (como tentativas de PIN antes da reposição).  Os campos de entrada de números serão definidos para os valores que teria uma política de MAM que criasse na consola através da opção de definições recomendadas.

Os conflitos ocorrem quando duas definições de políticas são iguais.  Por exemplo, se configurou duas políticas MAM idênticas, à exceção da definição de copiar/colar.  Neste cenário, a definição de copiar/colar será definida para o valor mais restritivo, mas as definições restantes serão aplicadas conforme configuradas.

Se uma política for implementada na aplicação e entrar em vigor e, em seguida, for implementada uma segunda, a primeira implementada terá precedência e manter-se-á aplicada, ao passo que a segunda estará em conflito. Se forem aplicadas ao mesmo tempo, o que significa que nenhuma tem precedência sobre a outra, estarão ambas em conflito. As definições em conflito serão definidas para os valores mais restritivos.

### O que acontece quando políticas personalizadas do iOS entram em conflito?
O Intune não avalia o payload dos ficheiros do Apple Configurator nem de políticas OMA-URI (Open Mobile Alliance Uniform Resource Identifier) personalizadas. Serve apenas como o mecanismo de entrega.

Quando implementar uma política personalizada, confirme que as definições configuradas não entram em conflito com a política de conformidade, de configuração ou outras políticas personalizadas. No caso de uma política personalizada com conflitos de definições, a ordem pela qual as definições são aplicadas é aleatória.

### O que acontece quando uma política é eliminada ou deixa de ser aplicável?
Quando elimina uma política ou remove um dispositivo de um grupo no qual a política foi implementada, a política e as definições serão removidos do dispositivo de acordo com as listas seguintes.

#### Dispositivos inscritos

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

#### PCs Windows com o software de cliente Intune

- **Definições do Endpoint Protection**: as definições são restauradas para os valores recomendados. A única exceção é a definição **Aderir ao Serviço de Proteção Ativa Microsoft**, na qual o valor predefinido é **Não**. Para obter detalhes, consulte [Ajude a proteger os PC Windows com o Endpoint Protection para o Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).
- **Definições de atualizações de software**: as definições são repostas para o estado predefinido do sistema operativo. Para obter detalhes, consulte [Manter os PC com Windows atualizados com atualizações de software no Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **Definições do Microsoft Intune Center**: todas as informações de contacto para suporte que foram configuradas pela política são eliminadas dos computadores.
- **Definições da Firewall do Windows**: as definições são repostas para o estado predefinido do sistema operativo do computador. Para obter detalhes, consulte [Ajude a proteger os PC Windows com o Endpoint Protection para o Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).


### Posso atualizar as políticas num dispositivo para garantir que estão atualizadas (aplica-se a PCs Windows que executem apenas o software de cliente do Intune)?

1.  Em qualquer grupo de dispositivos, selecione em que dispositivos pretende atualizar as políticas e selecione **Tarefas Remotas** &gt; **Atualizar Políticas**.
2.  Escolha **Tarefas Remotas**, no canto inferior direito da consola de administração do Intune, para verificar o estado das tarefas.

### Onde posso encontrar as políticas de resolução de problemas?

Consulte [Resolver problemas de políticas no Microsoft Intune](/intune/troubleshoot/troubleshoot-policies-in-microsoft-intune).



<!--HONumber=Oct16_HO2-->


