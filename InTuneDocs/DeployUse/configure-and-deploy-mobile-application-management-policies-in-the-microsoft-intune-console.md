---
title: "Configurar políticas de MAM na consola do Intune | Microsoft Intune"
description: "As políticas de gestão de aplicações móveis no Microsoft Intune permitem modificar a funcionalidade das aplicações que implementa para o ajudar a fazê-las cumprir as políticas de conformidade e segurança da sua empresa."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83
ms.reviewer: joglocke
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9a442d9472159757333a9ebe081d86eac9907cdc
ms.openlocfilehash: d7978e558c68ad3209f1503619a9113dba126028


---

# Configurar e implementar as políticas de gestão de aplicações móveis na consola do Microsoft Intune
As políticas de gestão de aplicações móveis (MAM) no Microsoft Intune permitem modificar a funcionalidade das aplicações que implementa para o ajudar a fazê-las cumprir as políticas de conformidade e segurança da sua empresa. Por exemplo, pode restringir operações de corte, cópia e colagem numa aplicação gerida ou configurar uma aplicação para abrir todas as ligações num browser gerido.

As políticas de gestão de aplicações móveis suportam:

-   Dispositivos com Android 4 ou posterior.

-   Dispositivos com iOS 8.0 ou posterior.

> [!TIP]
> As políticas de gestão de aplicações móveis suportam dispositivos que estão inscritos no Intune.
>
> Se estiver à procura de informações sobre como criar políticas de gestão de aplicações para dispositivos que não são geridos pelo Intune, veja [Proteger os dados da aplicação através de políticas de gestão de aplicações móveis com o Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

Ao contrário de outras políticas do Intune, o utilizador não implementa diretamente uma política de gestão de aplicações móveis. Em vez disso, associa a política à aplicação que pretende restringir. Quando a aplicação é implementada e instalada em dispositivos, as definições que especifica entrarão em vigor.

Para aplicar restrições a uma aplicação, esta tem de incorporar o SDK da Aplicação do Microsoft Intune. Existem três métodos para obter este tipo de aplicação:

-   **Utilizar uma aplicação gerida por política**. Uma aplicação gerida por política tem o SDK da Aplicação incorporado. Para adicionar este tipo de aplicação, especifique uma ligação para a aplicação a partir de uma loja de aplicações, como o iTunes ou o Google Play. Não é necessário processamento adicional para este tipo de aplicação. Para obter mais informações, veja a [lista de aplicações que pode utilizar com políticas de gestão de aplicações móveis do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-apps).

-   **Utilizar uma aplicação encapsulada**. Uma aplicação encapsulada é uma aplicação que empacota novamente para incluir o SDK da Aplicação através da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune. Normalmente, esta ferramenta é utilizada para processar aplicações da empresa que foram criadas internamente. Não pode ser utilizada para processar aplicações que foram transferidas a partir da loja de aplicações. Para obter mais informações, veja [Preparar as aplicações iOS para a gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e [Preparar as aplicações Android para a gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

- **Escrever a sua própria aplicação que incorpora o SDK da Aplicação do Intune**. O SDK da Aplicação do Intune permite-lhe incorporar funcionalidades de gestão de aplicação numa aplicação enquanto estiver a escrevê-la. Para obter mais informações, veja [Descrição Geral do SDK da Aplicação do Intune](/intune/develop/intune-app-sdk).

Para obter ajuda na escolha entre a Ferramenta de Encapsulamento de Aplicações e o SDK da Aplicação do Intune, veja [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune.md).

Algumas aplicações geridas, como a aplicação Outlook para iOS e Android, suportam *várias identidades*. Isto significa que o Intune apenas aplica definições de gestão a contas empresariais ou dados na aplicação.

Por exemplo, ao utilizar a aplicação do Outlook:

-   Se o utilizador configurar uma conta de e-mail empresarial e pessoal, o Intune só aplica definições de gestão à conta empresarial e não gere a conta pessoal.

-   Se o dispositivo for desativado ou a inscrição do mesmo anulada, apenas os dados empresariais do Outlook são removidos do dispositivo.

-   A conta empresarial utilizada tem de ser a mesma conta utilizada para inscrever o dispositivo no Intune.

> [!TIP]
> Se estiver a utilizar o Intune com o Configuration Manager, consulte [Como Controlar Aplicações ao Utilizar Políticas de Gestão de Aplicações Móveis no Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx).

## Criar e implementar uma aplicação com uma política de gestão de aplicações móveis

-   **Passo 1:** Obter a ligação para uma aplicação gerida por política, criar uma aplicação encapsulada, ou utilizar o SDK da Aplicação do Intune para escrever uma aplicação com MAM.

-   **Passo 2:** Publicar a aplicação no seu espaço de armazenamento na nuvem.

-   **Passo 3:** Criar uma política de gestão de aplicações móveis.

-   **Passo 4:** Associar a aplicação a uma política de gestão de aplicações móveis e, em seguida, implementá-la.

-   **Passo 5:** Monitorizar a implementação da aplicação.

## Passo 1: Obter a ligação para uma aplicação gerida por política, criar uma aplicação encapsulada ou utilizar o SDK da Aplicação do Intune para escrever uma aplicação com MAM

Na loja de aplicações, encontre e anote o URL da aplicação gerida por política que pretende implementar. Por exemplo, o URL da aplicação Microsoft Word para iPad é **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.


## Passo 2: Publicar a aplicação no seu espaço de armazenamento na nuvem
Quando publica uma aplicação gerida, os procedimentos diferem dependendo de estar a publicar uma aplicação gerida por política ou uma aplicação que foi processada ao utilizar a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS.

#### Para publicar uma aplicação gerida por política

1.  Quando estiver pronto para carregar a aplicação para o seu espaço de armazenamento na nuvem, siga as instruções em [Adicionar aplicações a dispositivos móveis no Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Para aplicações iOS, selecione **Aplicação iOS gerida a partir da App Store**, em **Selecionar como este software é disponibilizado para os dispositivos**.

    Para aplicações Android, selecione **Ligação externa**.

3.  Em **Especificar um URL**, introduza o URL para a aplicação gerida por política que anotou anteriormente.

Após a conclusão do carregamento, verá **Sim** para **Políticas de Gestão de Aplicações** na página **Propriedades de Software** da aplicação carregada.

Depois de ter verificado que a aplicação foi carregada com êxito, continue para o passo 3.

#### Para publicar uma aplicação que foi processada através da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune

1.  Quando estiver pronto para carregar a aplicação para o seu espaço de armazenamento na nuvem, siga as instruções em [Adicionar aplicações a dispositivos móveis no Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

2.  Selecione **Instalador de Software**, em **Selecionar como este software é disponibilizado para os dispositivos**.

3.  Selecione **Pacote de aplicação para iOS (&#42;ficheiro .ipa)**, em **Tipo de ficheiro do instalador de software**.

Após a conclusão do carregamento, verá **Sim** para **Políticas de Gestão de Aplicações** na página **Propriedades de Software** da aplicação carregada.

Depois de ter verificado que a aplicação foi carregada com êxito, continue para o passo 3.

## Passo 3: criar uma política de gestão de aplicações móveis

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), selecione **Política** &gt; **Descrição Geral** &gt; **Adicionar Política**.

2.  Configure e implemente uma das seguintes políticas de **Software**, dependendo do tipo de dispositivo para o qual pretende configurar aplicações:

    -   **Política de Gestão de Aplicações Móveis (Android 4 e posterior)**

    -   **Política de Gestão de Aplicações Móveis (iOS 8.0 e posterior)**

    Pode utilizar definições recomendadas ou personalizar as mesmas. Para obter informações, consulte [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Configure as definições seguintes conforme necessário. As opções podem variar dependendo do tipo de dispositivo para o qual está a configurar a política.

|Nome da definição|Detalhes|
    |---------|--------------------|
    |**Nome**|Especifique um nome para esta política.|
    |**Descrição**|Opcionalmente, especifique uma descrição para esta política.|
    |**Restringir o conteúdo Web a apresentar num browser gerido pela empresa**|Quando esta definição está ativada, as ligações na aplicação serão abertas no browser gerido. Para esta opção funcionar, esta aplicação tem de estar implementada em dispositivos.|
    |**Impedir cópias de segurança do Android** ou **Impedir cópias de segurança do iTunes e iCloud**|Esta definição desativa a cópia de segurança de informações da aplicação.|
    |**Permitir que a aplicação transfira dados para outras aplicações**|Esta definição especifica as aplicações para as quais esta aplicação pode enviar dados. Pode optar por não permitir a transferência de dados para qualquer aplicação, permitir a transferência apenas para outras aplicações geridas ou permitir a transferência para qualquer aplicação. <br /><br />Por exemplo, quando não permite a transferência de dados, restringe a transferência de dados para serviços como mensagens SMS, atribuição de imagens a contactos e publicação no Facebook e Twitter.<br /><br />Para dispositivos iOS, para impedir a transferência de documentos entre aplicações geridas e não geridas, também tem de configurar e implementar uma política de segurança de dispositivos móveis que desativa a definição **Permitir documentos geridos noutras aplicações não geridas**. Se optar por permitir a transferência apenas para outras aplicações geridas, os visualizadores de PDF e imagem do Intune (se estiverem implementados) serão utilizados para abrir conteúdos dos respetivos tipos.<br /><br />Além disso, se definir esta opção como **Aplicações Geridas por Políticas** ou **Nenhuma**, a funcionalidade do iOS 9 que permite que o Spotlight Search procure dados dentro de aplicações será bloqueada.<br><br>Esta definição não controla a utilização da funcionalidade Abrir Em nos dispositivos móveis. Para gerir a funcionalidade Abrir Em, veja [Gerir a transferência de dados entre aplicações iOS com o Microsoft Intune](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).|
    |**Permitir que a aplicação receba dados de outras aplicações**|Esta definição especifica de que aplicações esta aplicação pode receber dados. Pode optar por não permitir a transferência de dados de qualquer aplicação, permitir a transferência apenas de outras aplicações geridas ou permitir a transferência de qualquer aplicação.<br /><br />Quando um utilizador acede a dados a partir de uma aplicação que não seja gerida por uma política de gestão de aplicações móveis, os dados serão tratados como dados empresariais e protegidos pela política. Isto aplica-se às aplicações iOS que suportem várias identidades (em que o Intune aplica definições de gestão apenas a contas empresariais ou dados na aplicação). Em alternativa, isto aplica-se a um dispositivo inscrito com uma política de gestão de aplicações móveis aplicada.|
    |**Impedir "Guardar Como"**|Esta definição desativa a utilização da opção **Guardar Como** para guardar dados em localizações de armazenamento na nuvem pessoal (tais como OneDrive ou Dropbox) em qualquer aplicação que utiliza esta política.|
    |**Restringir as operações de corte, cópia e colagem com outras aplicações**|Esta definição especifica como as operações de corte, cópia e colagem podem ser utilizadas com a aplicação. Escolha entre:<br /><br />**Bloqueado**. Não permitir operações de corte, cópia e colagem entre esta aplicação e outras aplicações.<br /><br />**Aplicações Geridas por Políticas**. Permitir apenas operações de corte, cópia e colagem entre esta aplicação e outras aplicações geridas.<br /><br />**Aplicações Geridas por Políticas com Colar Em**. Permitir que os dados cortados ou copiados desta aplicação sejam colados apenas noutras aplicações geridas. Permitir que os dados cortados ou copiados de qualquer aplicação sejam colados nesta aplicação.<br /><br />**Qualquer Aplicação**. Sem restrições nas operações de corte, cópia e colagem para ou desta aplicação.<br /><br />Para copiar e colar dados entre aplicações geridas, ambas as aplicações têm de ter configuradas as definições **Aplicações Geridas por Políticas** ou **Aplicações Geridas por Políticas com Colar Em**.|
    |**Exigir PIN simples para acesso**|Esta definição exige que o utilizador introduza um PIN que especifica para utilizar esta aplicação. Será pedido ao utilizador para configurar isto da primeira vez que executar a aplicação.|
    |**Número de tentativas antes de redefinição do PIN**|Especifique o número de tentativas de introdução do PIN que podem ser efetuadas antes de o utilizador ter de redefinir o PIN.|
    |**Exigir credenciais da empresa para obter acesso**|Esta definição exige que o utilizador introduza as informações de início de sessão empresariais antes de poder aceder à aplicação.|
    |**Exigir a conformidade do dispositivo com a política empresarial para acesso**|Esta definição apenas permite que a aplicação seja utilizada quando o dispositivo não tem jailbreak nem root.|
    |**Verificar novamente os requisitos de acesso após (minutos)**|No campo **Tempo limite**, especifique o período de tempo antes de os requisitos de acesso da aplicação serem novamente verificados após a aplicação ser aberta.|
    |**Período de tolerância offline**|Se o dispositivo estiver offline, especifique o período de tempo antes dos requisitos de acesso da aplicação serem novamente verificados.|
    |**Encriptar dados da aplicação**|Esta definição especifica que todos os dados associados a esta aplicação serão encriptados. Isto inclui os dados armazenados externamente, como em cartões SD.<br /><br />**Encriptação para iOS**<br /><br />Para aplicações associadas à política de gestão de aplicações móveis do Intune, os dados são encriptados em descanso através da encriptação ao nível do dispositivo fornecida pelo sistema operativo. Isto é ativado através da política de PIN de dispositivo definida pelo administrador de TI. Quando for necessário um PIN, os dados serão encriptados de acordo com as definições na política de gestão de aplicações móveis. Conforme indicado na documentação da Apple, [os módulos utilizados pelo iOS têm a certificação FIPS 140-2](http://support.apple.com/en-us/HT202739).<br /><br />**Encriptação para Android**<br /><br />Para as aplicações associadas a uma política de gestão de aplicações móveis do Intune, a encriptação é fornecida pela Microsoft. Os dados são encriptados de modo síncrono durante as operações de E/S de ficheiros.  O conteúdo no armazenamento do dispositivo será sempre encriptado. O método de encriptação não tem certificação FIPS 140-2.|
    |**Bloquear captura de ecrã** (apenas dispositivos Android)|Esta definição especifica que as funções de captura de ecrã do dispositivo estão bloqueadas durante a utilização desta aplicação.|

4. Quando terminar, selecione **Guardar Política**.

A nova política é apresentada no nó **Políticas de Configuração** da área de trabalho **Política**.

## Passo 4: Associar a aplicação a uma política de gestão de aplicações móveis e, em seguida, implementá-la
Certifique-se de que seleciona a política de gestão de aplicações móveis na página **Gestão de Aplicações Móveis** da caixa de diálogo **Gerir Implementação** para associar a política à aplicação.

Para obter detalhes, consulte [Implementar aplicações no Microsoft Intune](deploy-apps.md).

> [!IMPORTANT]
> Se o dispositivo não estiver inscrito no Intune, as políticas não são removidas das aplicações. As aplicações que tinham as políticas aplicadas irão manter as definições de política depois de a aplicação ser desinstalada e reinstalada.

### O que fazer quando uma aplicação já está implementada nos dispositivos
Poderão existir situações em que implementa uma aplicação e em que um dos utilizadores ou dispositivos visados já tem instalada uma versão não gerida da aplicação. Por exemplo, o utilizador pode ter instalado o Microsoft Word a partir da loja de aplicações.

Neste caso, tem de pedir ao utilizador para desinstalar manualmente a versão não gerida para que a versão gerida que configurou possa ser instalada.

No entanto, para dispositivos que executem o iOS 9 e posteriores, o Intune pedirá automaticamente permissão ao utilizador para assumir o controlo de gestão da aplicação existente. Se este concordar, a aplicação passará a ser gerida pelo Intune e quaisquer políticas de gestão de aplicações móveis que tenha associado às aplicações serão igualmente aplicadas.

> [!TIP]
> Se o dispositivo estiver no modo supervisionado, o Intune irá assumir a gestão das aplicações existentes sem pedir autorização aos utilizadores.

## Passo 5: Monitorizar a implementação da aplicação
Depois de criar e implementar uma aplicação associada a uma política de gestão de aplicações móveis, utilize o seguinte procedimento para monitorizar a aplicação e resolver os conflitos de política.

#### Para ver o estado da implementação

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Grupos** &gt; **Descrição Geral**.

2.  Efetue um dos seguintes passos:

    -   Escolha **Todos os Utilizadores** e, em seguida, faça duplo clique no utilizador cujo dispositivo pretende examinar. Na página **Propriedades do Utilizador**, escolha **Dispositivos** e, em seguida, faça duplo clique no dispositivo que pretende examinar.

    -   Clique em **Todos os Dispositivos** &gt; **Todos os Dispositivos Móveis**. Na página **Propriedades do Grupo de Dispositivos**, escolha **Dispositivos** e, em seguida, faça duplo clique no dispositivo que pretende examinar.

3.  Na página **Propriedades dos Dispositivos Móveis** , selecione **Política** para ver uma lista das políticas de gestão de aplicações móveis que foram implementadas no dispositivo.

4.  Selecione a política de gestão de aplicações móveis cujo estado pretende ver. Pode ver os detalhes da política no painel inferior e expandir o nó para apresentar as definições.

5.  Na coluna **Estado** de cada uma das políticas de gestão de aplicações móveis, será apresentado **Está em Conformidade**, **Está em Conformidade (Pendente)** ou **Erro**. Se a política selecionada tiver uma ou mais definições em conflito, será apresentado **Erro** neste campo.

6.  Depois de identificar um conflito, pode rever as definições de política em conflito para utilizar a mesma definição ou pode implementar apenas uma política à aplicação e ao utilizador.

### Como são resolvidos os conflitos de políticas
Quando existe um conflito de política de gestão de aplicações móveis na primeira implementação para o utilizador ou dispositivo, o valor de definição específico em conflito será removido da política implementada na aplicação. A aplicação utilizará um valor de conflito incorporado.

Quando existe um conflito de política de gestão de aplicações móveis em implementações posteriores na aplicação ou utilizador, o valor de definição específico em conflito não será atualizado na política de gestão de aplicações móveis implementada na aplicação. A aplicação utilizará o valor existente para essa definição.

Nos casos em que o dispositivo ou o utilizador recebe duas políticas em conflito, aplica-se o comportamento seguinte:

-   Se uma política já tiver sido implementada no dispositivo, as definições da política existente não são substituídas.

-   Se ainda não tiver sido implementada uma política no dispositivo e forem implementadas duas definições em conflito, a predefinição incorporada no dispositivo é utilizada.



<!--HONumber=Oct16_HO3-->


