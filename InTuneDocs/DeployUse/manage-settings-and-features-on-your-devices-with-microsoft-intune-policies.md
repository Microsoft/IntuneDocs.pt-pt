---
# required metadata

title: Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 09bae0b9-4f79-4658-8ca1-a71ab992c1b2

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune
As **políticas** do Microsoft Intune são grupos de definições que controlam funcionalidades em dispositivos móveis e computadores. Pode criar políticas através de modelos que contenham definições recomendadas ou personalizadas e depois implementá-las em dispositivos ou grupos de utilizadores.

## Que tipos de política pode utilizar?

As políticas do Intune inserem-se nas categorias seguintes. A categoria que utilizar afeta a forma como cria e implementa a política.


- **Políticas de configuração:** estas políticas são frequentemente utilizadas para gerir as funcionalidades e as definições de segurança nos seus dispositivos. Utilize as informações deste tópico para saber como criar e implementar estas políticas e para explorar as definições disponíveis.
- **Políticas de conformidade do dispositivo:** estas políticas definem as regras e as definições que um dispositivos tem de cumprir para ser considerado conforme pelas políticas de acesso condicional. Também pode utilizar as políticas de conformidade para monitorizar e resolver a conformidade dos dispositivos independentemente do acesso condicional.
Para obter detalhes, consulte [Políticas de conformidade de dispositivos no Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md).
- **Políticas de acesso condicional:** estas políticas ajudam a proteger o e-mail e outros serviços dependendo das condições que especificar.
Para obter detalhes, consulte [Restringir o acesso ao e-mail e aos serviços do Office 365 com o Microsoft Intune](restrict-access-to-email-and-o365-services-with-microsoft-intune.md).
- **Políticas de inscrição de dispositivos de empresa:** para obter informações sobre as políticas de inscrição de dispositivos de empresa, consulte [Configurar a gestão de iOS e Mac com o Microsoft Intune](set-up-ios-and-mac-management-with-microsoft-intune.md).
- **Políticas de acesso a recursos:** este grupo de políticas funciona em conjunto para ajudar os seus utilizadores a obterem acesso aos ficheiros e recursos de que precisam para trabalhar com êxito, onde quer que estejam.
Para obter detalhes, consulte [Permitir o acesso aos recursos da empresa com o Microsoft Intune](enable-access-to-company-resources-with-microsoft-intune.md).


Para obter uma lista completa das políticas do Intune, consulte o artigo [Referência de políticas do Microsoft Intune](microsoft-intune-policy-reference.md).




## Criar uma política de configuração

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), clique em **Política** &gt; **Políticas de Configuração** &gt; **Adicionar**.

2.  Selecione a política que pretende, escolha entre utilizar as definições recomendadas para a política (quando disponível; pode alterar estas definições mais tarde) ou criar uma política personalizada com as suas próprias definições.

    > [!TIP]
    > Para o ajudar a escolher a política certa, consulte [Referência de políticas do Microsoft Intune](microsoft-intune-policy-reference.md).

3.  Quando estiver pronto, clique em **Criar Política**.

4.  No ecrã **Criar Política** , configure um nome e uma descrição opcional para a política.

5.  Configure as definições de política necessárias e, em seguida, clique em **Guardar Política**.

    Se precisar de ajuda em quaisquer definições de política, escolha o seu tipo de política na lista seguinte:

    - [Definições para dispositivos iOS](ios-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Android](android-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Windows 8 e Windows 8.1](windows-configuration-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Windows Phone 8.1](windows-phone-8-1-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos móveis e computadores Windows 10](windows-10-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Windows Team](windows-team-configuration-policy-settings-in-microsoft-intune.md)
    - [Definições para a atualização da edição Windows](edition-upgrade-policy-settings-in-microsoft-intune.md)
    - [Definições para dispositivos Mac OS X](mac-os-x-policy-settings-in-microsoft-intune.md)
    - [Definições para o Exchange ActiveSync](exchange-activesync-policy-settings-in-microsoft-intune.md)
    - [Definições para a política de termos e condições](terms-and-condition-policy-settings-in-microsoft-intune.md)
    - [Definições gerais para dispositivos móveis (legados)](mobile-device-security-policy-settings-in-microsoft-intune.md)

4.  Na caixa de diálogo de confirmação clique em **Sim** para implementar a política de imediato ou clique em **Não** para criar uma política sem a implementar.

Pode visualizar e editar a nova política navegando pelas secções de cada tipo de política na área de trabalho **Política** .

Quando cria uma política que utiliza as definições recomendadas, o nome da nova política é uma combinação do nome do modelo, data e hora. Ao editar a política, o nome é atualizado com a data e hora da edição.

Agora que criou uma política, normalmente, irá querer implementá-la num ou mais grupos de utilizadores ou dispositivos.

> [!TIP]
> Não implementa todos os tipos de política. Por exemplo, a política de gestão de aplicações móveis não é implementada. Este tipo de política está associado a uma aplicação em relação à qual o implementará.

## Implementar uma política de configuração

1.  Na área de trabalho **Política**, selecione a política que pretende implementar e, em seguida, clique em **Gerir Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação** , para:

    -   **Para implementar a política** - selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, clique em **Adicionar** &gt; **OK**.

    -   **Para fechar a caixa de diálogo sem implementar a política** - Clique em **Cancelar**.

Ao selecionar uma política implementada, pode ver mais informações sobre a implementação na parte inferior da lista de políticas.

## Gerir políticas

1.  Na [Consola de administração do Microsoft Intune](https://manage.microsoft.com/), clique em **Política**e, em seguida, navegue até à política que pretende gerir e selecione-a.

2.  Selecione uma das seguintes ações:

- **Editar** - Abre as propriedades da política selecionada para poder efetuar alterações.
- **Eliminar** - Elimina a política selecionada.<br>Quando elimina uma política, esta é removida de todos os grupos nos quais estava implementada.
- **Gerir a Implementação** - Selecione o grupo no qual pretende implementar a política e clique em **Adicionar**.

## Tarefas para as políticas do Intune

### Para atualizar as políticas num dispositivo para garantir que estão atualizadas (aplica-se a PCs Windows que executem apenas o software de cliente Intune)

1.  Na [Consola do administrador do Microsoft Intune](https://manage.microsoft.com/), clique em **Grupos**e, em seguida, selecione um grupo de dispositivos.

2.  Selecione os dispositivos nos quais pretende atualizar as políticas e clique em **Tarefas Remotas** &gt; **Atualizar Políticas**.

3.  Clique em **Tarefas Remotas** no canto inferior direito da consola de administração do Intune para verificar o estado das tarefas.

## Informações de referência para as políticas do Intune

### Quanto tempo é necessário para que os dispositivos móveis obtenham a política ou as aplicações após a implementação?
Quando uma política ou aplicação é implementada, o Intune começa imediatamente a tentar notificar o dispositivo de que deverá dar entrada no serviço Intune. Geralmente, o processo demora menos de 5 minutos.

Se um dispositivo não der entrada para obter uma política após o envio da primeira notificação, são realizadas mais 3 tentativas.  Se o dispositivo estiver offline (por exemplo, se estiver desligado, ou se não estiver ligado a uma rede), pode não receber as notificações.

Neste caso, o dispositivo irá obter uma política na entrada seguinte agendada com o serviço Intune, da seguinte forma:

- iOS - a cada 6 horas
- Android - a cada 8 horas
- Windows Phone - a cada 8 horas
- PCs Windows inscritos como dispositivos - a cada 24 horas

Se o dispositivo tiver acabado de se inscrever, a frequência de entrada será maior, conforme se segue:

- iOS - a cada 15 minutos durante 6 horas e, em seguida, a cada 6 horas
- Android - a cada 3 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas
- Windows Phone - a cada 5 minutos durante 15 minutos, depois a cada 15 minutos durante 2 horas e, em seguida, a cada 8 horas
- PCs Windows inscritos como dispositivos - a cada 3 minutos durante 30 minutos e, em seguida, a cada 24 horas

Os utilizadores também podem iniciar a aplicação do Portal da Empresa e sincronizar o dispositivo para verificar imediatamente uma política a qualquer altura.

### Que ações fazem o Intune enviar de imediato uma notificação para um dispositivo?
Os dispositivos dão entrada no Intune quando recebem uma notificação a solicitar-lhes que deem entrada ou durante as entradas agendadas, conforme indicado nas tabelas acima.  Quando define um dispositivo ou utilizador como o visado específico de uma ação, tal como uma eliminação, bloqueio, reposição de código de acesso, implementação de aplicação, implementação de perfil (Wi-Fi, VPN, e-mail, etc.) ou uma implementação de política, o Intune começará imediatamente a tentar notificar o dispositivo de que deve dar entrada no serviço Intune para receber estas atualizações.

Outras alterações como a revisão das informações de contacto no portal da empresa não dão origem a uma notificação imediata para os dispositivos.

> [!TIP]
> Quando for implementada uma política com definições num dispositivo Android, é pedido ao utilizador que efetue uma ação para estar em conformidade com a política. Até que os utilizadores efetuem esta ação ou o dispositivo seja reiniciado, as novas definições de política não entrarão em vigor.

### Se forem implementadas várias políticas para o mesmo utilizador ou dispositivo, como posso saber que definições irão ser aplicadas?
É importante ter presente que ao serem implementadas  duas ou mais políticas para o mesmo utilizador ou dispositivo, a avaliação relativa à definição aplicada é realizada ao nível da definição individual.

-   As definições de políticas de conformidade têm sempre precedência sobre as definições de políticas de configuração

-   A definição de políticas de conformidade mais restritivas é aplicada se for avaliada em comparação com a mesma definição numa política de conformidade diferente

-   A definição de políticas de configuração mais restritivas é aplicada se avaliada em comparação com a mesma definição numa política de configuração diferente

### O que acontece quando as políticas de gestão de aplicações móveis (MAM) entram em conflito entre si? Qual delas é aplicada à aplicação?
Os valores em conflito são as definições mais restritivas disponíveis numa política de gestão de aplicações móveis, exceto no que respeita aos campos de entrada de números (como tentativas de PIN antes da reposição).  Os campos de intrada de números serão definidos para os valores que teria uma política MAM que criasse na consola através da opção de definições recomendadas.

Os conflitos ocorrem quando duas definições de políticas são iguais.  Por exemplo, se configurou duas políticas MAM idênticas, à exceção da definição de copiar/colar.  Neste cenário, a definição de copiar/colar será definida para o valor mais restritivo, mas as definições restantes serão aplicadas conforme configuradas.

Se uma política for implementada para a aplicação e entrar em vigor e, em seguida, for implementada uma segunda, a primeira implementada terá precedência e manter-se-á aplicada, e a segunda estará em conflito. Todavia, se forem aplicadas em simultâneo, não existindo portanto nenhuma política precedente, ficam ambas em conflito e quaisquer definições em conflito serão definidas para os valores mais restritivos.

### O que acontece quando políticas personalizadas do iOS entram em conflito?
O Intune não avalia o payload de ficheiros de configuração da Apple ou a política OMA-URI personalizada, serve meramente como mecanismo de entrega.

Por conseguinte, quando implementar uma política personalizada, certifique-se de que as definições configuradas não entram em conflito com a política de conformidade, de configuração ou outras políticas personalizadas. No caso de uma política personalizada com conflitos de definições, a ordem pela qual as definições são aplicadas é aleatória.

### O que acontece quando uma política é eliminada ou já não é aplicável
Quando elimina uma política ou remove um dispositivo de um grupo no qual a política foi implementada, a política e as definições serão removidos do dispositivo de acordo com as seguintes tabelas:

#### Dispositivos inscritos

- Perfis de Wi-Fi, VPN, certificado e e-mail - estes perfis são removidos de todos os dispositivos inscritos suportados.
- Todos os outros tipos de política
    - **Dispositivos Windows e Android** - as definições não são removidas do dispositivo.
    - **Dispositivos Windows Phone 8.1** - as seguintes definições são removidas:
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
        - Permitir Conta Microsoft
        - Permitir copiar e colar
        - Permitir partilha de Wi-Fi
        - Permitir ligação automática a hotspots Wi-Fi
        - Permitir relatórios de hotspots Wi-Fi
        - Permitir a reposição de fábrica
        - Permitir Bluetooth
        - Permitir NFC
        - Permitir Wi-Fi
    
    - **iOS** - todas as definições são removidas, exceto:
        - Permitir chamadas em roaming
        - Permitir roaming de dados
        - Permitir sincronização automática em roaming

#### PCs Windows com o software de cliente Intune

- **Definições do Endpoint Protection** - As definições são restauradas para os valores recomendados. A única exceção é a definição **Aderir ao Serviço de Proteção Ativa Microsoft** para a qual o valor predefinido é **Não**. Para obter detalhes, consulte [Ajude a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).
- **Definições de atualizações de software** - As definições são repostas para o estado predefinido do sistema operativo. Para obter detalhes, consulte [Manter os computadores com Windows atualizados com atualizações de software no Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md).
- **Definições do Microsoft Intune Center** - Todas as informações de contacto para suporte que foram configuradas pela política são eliminadas dos computadores.
- **Definições da Firewall do Windows** - As definições são repostas para o estado predefinido do sistema operativo do computador. Para obter detalhes, consulte [Ajude a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md).





<!--HONumber=May16_HO1-->

