---
# required metadata

title: Configurar e implementar políticas de gestão de aplicações móveis na consola do Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: b4fb33a8-a2fa-4353-bd89-5bda48b68e83

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Configure and deploy mobile application management policies in the Microsoft Intune console
As políticas de gestão de aplicações móveis no Microsoft Intune permitem modificar a funcionalidade das aplicações que implementa para o ajudar a fazê-las cumprir com as políticas de conformidade e segurança da sua empresa. Por exemplo, pode restringir operações de corte, cópia e colagem numa aplicação gerida ou configurar uma aplicação para abrir todas as ligações num browser gerido.

As políticas de gestão de aplicações móveis suportam:

-   Dispositivos com Android 4 ou posterior.

-   Dispositivos com iOS 7 ou posterior.

> As políticas de gestão de aplicações móveis suportam dispositivos que estão inscritos no Intune.
> 
> Se estiver à procura de informações sobre como criar políticas de gestão de aplicações para dispositivos que não são geridos pelo Intune, consulte [Proteger os dados da aplicação através de políticas de gestão de aplicações móveis com o Microsoft Intune](protect-app-data-using-mobile-app-management-policies-with-microsoft-intune.md).

Ao contrário de outras políticas do Intune, o utilizador não implementa diretamente uma política de gestão de aplicações móveis. Em vez disso, associa a política à aplicação que pretende restringir. Quando a aplicação é implementada e instalada em dispositivos, as definições que especifica entrarão em vigor.

Para aplicar restrições a uma aplicação, esta tem de incorporar o Software Development Kit (SDK) da Aplicação Microsoft. Existem dois métodos para obter este tipo de aplicação:

-   **Utilizar uma aplicação gerida por política** – tem o SDK da Aplicação incorporado. Para adicionar este tipo de aplicação, especifique uma ligação para a aplicação a partir de uma loja de aplicações, como o iTunes ou o Google Play. Não é necessário processamento adicional para este tipo de aplicação. Consulte uma lista de [aplicações que pode utilizar com políticas de gestão de aplicações móveis do Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx)

-   **Utilizar uma aplicação "encapsulada"** - aplicações que são empacotadas novamente para incluir o SDK da Aplicação através da **Ferramenta de Encapsulamento de Aplicações do Microsoft Intune**. Normalmente esta ferramenta é utilizada para processar aplicações da empresa que foram criadas internamente. Não pode ser utilizada para processar aplicações que foram transferidas a partir da loja de aplicações. Consulte [Preparar as aplicações iOS para a gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e [Preparar as aplicações Android para a gestão de aplicações móveis com a ferramenta de Encapsulamento de Aplicações do Microsoft Intune](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md)

Algumas aplicações geridas, como a aplicação Outlook para iOS e Android, suportam **várias identidades**. Isto significa que o Intune apenas aplica definições de gestão a contas empresariais ou dados na aplicação.

Por exemplo, ao utilizar a aplicação do Outlook:

-   Se o utilizador configurar uma conta de e-mail empresarial e pessoal, o Intune só aplica definições de gestão à conta empresarial, mas não gere a conta pessoal.

-   Se o dispositivo for desativado ou a inscrição do mesmo anulada, apenas os dados empresariais do Outlook são removidos do dispositivo.

-   A conta empresarial utilizada tem de ser a mesma conta utilizada para inscrever o dispositivo no Intune.

> Se estiver a utilizar o Intune com o Configuration Manager, consulte [Controlar Aplicações ao Utilizar Políticas de Gestão de Aplicações Móveis no Configuration Manager](https://technet.microsoft.com/library/mt131414.aspx)

## Criar e implementar uma aplicação com uma política de gestão de aplicações móveis

-   **Passo 1:** Obter a ligação para uma aplicação gerida por política ou criar uma aplicação encapsulada.

-   **Passo 2:** Publicar a aplicação no seu espaço de armazenamento na nuvem.

-   **Passo 3:** Criar uma política de gestão de aplicações móveis.

-   **Passo 4:** Implementar a aplicação, selecionando a opção para associar a aplicação a uma política de gestão de aplicações móveis.

-   **Passo 5:** Monitorizar a implementação da aplicação.

## **Passo 1:** Obter a ligação para uma aplicação gerida por política ou criar uma aplicação encapsulada

-   **Para obter uma ligação para uma aplicação gerida por política** - na loja de aplicações, encontre e anote o URL da aplicação gerida por política que pretende implementar.

    Por exemplo, o URL da aplicação Microsoft Word para iPad é **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**

-   **Para criar uma aplicação encapsulada** - Para criar uma aplicação encapsulada, utilize as informações dos tópicos [Preparar as aplicações iOS para a gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune](prepare-ios-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md) e [Preparar as aplicações Android para a gestão de aplicações móveis com a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune](prepare-android-apps-for-mobile-application-management-with-the-microsoft-intune-app-wrapping-tool.md).

    A ferramenta cria uma aplicação processada que irá utilizar quando publicar a aplicação no seu espaço de armazenamento na nuvem.

## **Passo 2:** Publicar a aplicação no seu espaço de armazenamento na nuvem
Quando publica uma aplicação gerida, os procedimentos diferem dependendo de estar a publicar uma aplicação gerida por política ou uma aplicação que foi processada ao utilizar a Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para iOS.

#### Para publicar uma aplicação gerida por política

1.  Quando estiver pronto para carregar a aplicação para o seu espaço de armazenamento na nuvem, siga as instruções em [Adicionar aplicações para dispositivos móveis no Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)

2.  Para aplicações iOS, selecione **Aplicação iOS gerida a partir da App Store**, em **Selecionar como este software é disponibilizado para os dispositivos**

    Para aplicações Android, selecione **Ligação externa**

3.  Em **Especificar um URL**, introduza o URL para a aplicação gerida por política que anotou anteriormente.

Após a conclusão do carregamento, verá **Sim** para **Políticas de Gestão de Aplicações** na página **Propriedades de Software** da aplicação carregada.

Assim que tiver verificado que a aplicação é carregada com êxito, continue para o Passo 3.

#### Para publicar uma aplicação que foi processada através da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune

1.  Quando estiver pronto para carregar a aplicação para o seu espaço de armazenamento na nuvem, siga as instruções em [Adicionar aplicações para dispositivos móveis no Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md)

2.  Selecione **Instalador de Software**, em **Selecionar como este software é disponibilizado para os dispositivos**

3.  Selecione **Pacote de aplicação para iOS (&#42;ficheiro .ipa)**, em **Tipo de ficheiro do instalador de software**

Após a conclusão do carregamento, verá **Sim** para **Políticas de Gestão de Aplicações** na página **Propriedades de Software** da aplicação carregada.

Assim que tiver verificado que a aplicação é carregada com êxito, continue para o Passo 3.

## **Passo 3:** Criar uma política de gestão de aplicações móveis

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** &gt; **Descrição Geral** &gt; **Adicionar Política**

2.  Configure e implemente uma das seguintes políticas de **Software** , dependendo do tipo de dispositivo para o qual pretende configurar aplicações:

    -   **Política de Gestão de Aplicações Móveis (Android 4 e posterior)**

    -   **Política de Gestão de Aplicações Móveis (iOS 7 e posterior)**

    Pode utilizar definições recomendadas ou personalizar as mesmas. Para obter detalhes, consulte [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

3.  Configure as definições seguintes conforme necessário. As opções podem variar dependendo do tipo de dispositivo para o qual está a configurar a política.

|Nome da definição|Detalhes|
    |---------|--------------------|
    |**Nome**|Especifique um nome para esta política.|
    |**Descrição**|Opcionalmente, especifique uma descrição para esta política.|
    |**Restringir o conteúdo Web a apresentar num browser gerido pela empresa**|Quando esta definição é ativada, as ligações na aplicação serão abertas no Browser Gerido. Para esta opção funcionar, esta aplicação tem de estar implementada em dispositivos.|
    |**Impedir cópias de segurança do Android** ou **Impedir cópias de segurança do iTunes e iCloud**|Desativa a cópia de segurança de informações da aplicação.|
    |**Permitir que a aplicação transfira dados para outras aplicações**|Especifica as aplicações para as quais esta aplicação pode enviar dados. Pode optar por não permitir a transferência de dados para qualquer aplicação, permitir a transferência apenas para outras aplicações geridas ou permitir a transferência para qualquer aplicação. Esta definição não controla a utilização da funcionalidade **Abrir Em** nos dispositivos móveis.<br /><br />Por exemplo, quando não permite a transferência de dados, restringe a transferência de dados para serviços como mensagens SMS, atribuição de imagens a contactos e publicação no Facebook e Twitter.<br /><br />Para dispositivos iOS, de forma a impedir a transferência de documentos entre aplicações geridas e não geridas, tem também de configurar e implementar uma política de segurança de dispositivos móveis que desative a definição **Permitir documentos geridos noutras aplicações não geridas** Se selecionar a opção para permitir apenas a transferência para outras aplicações geridas, os visualizadores de imagens e de PDF do Intune (se estiverem implementados) serão utilizados para abrir conteúdos dos respetivos tipos.<br /><br />Além disso, se definir esta opção como **Aplicações Geridas por Políticas** ou **Nenhuma**, a funcionalidade do iOS 9 que permite que o Spotlight Search procure dados dentro de aplicações será bloqueada.|
    |**Permitir que a aplicação receba dados de outras aplicações**|Especifica de que aplicações esta aplicação pode receber dados. Pode optar por não permitir a transferência de dados de qualquer aplicação, permitir a transferência apenas de outras aplicações geridas ou permitir a transferência de qualquer aplicação<br /><br />Para aplicações iOS que suportem várias identidades (onde o Intune aplica apenas definições de gestão a contas empresariais ou a dados na aplicação), para um dispositivo inscrito com a política de gestão de aplicações móveis aplicada, quando um utilizador acede a dados a partir de uma aplicação que não é gerida por uma política de gestão de aplicações móveis, os dados serão tratados como dados empresariais e protegidos pela política.|
    |**Impedir "Guardar Como"**|Desativa a utilização da opção **Guardar Como** para guardar dados em localizações de armazenamento na nuvem pessoal (tais como OneDrive Pessoal ou Dropbox) em qualquer aplicação que utiliza esta política.|
    |**Restringir as operações de corte, cópia e colagem com outras aplicações**|Especifica como as operações de corte, cópia e colagem podem ser utilizadas com a aplicação. Escolha entre:<br /><br />**Bloqueado** – não permitir operações de corte, cópia e colagem entre esta aplicação e outras aplicações.<br /><br />**Aplicações Geridas por Política** – permitir apenas operações de corte, cópia e colagem entre esta aplicação e outras aplicações geridas.<br /><br />**Aplicações Geridas por Política com Colar Em** – permitir que os dados cortados ou copiados desta aplicação sejam colados apenas noutras aplicações geridas. Permitir que os dados cortados ou copiados de qualquer aplicação sejam colados nesta aplicação.<br /><br />**Qualquer Aplicação** - sem restrições para operações de corte, cópia e colagem desta ou para esta aplicação.<br /><br />Para copiar e colar dados entre aplicações geridas, ambas as aplicações têm de ter configuradas as definições **Aplicações Geridas por Política** ou **Aplicações Geridas por Política com Colar Em**.|
    |**Exigir PIN simples para acesso**|Exige que o utilizador introduza um número PIN que especifica para utilizar esta aplicação. Será pedido ao utilizador para configurar isto da primeira vez que executar a aplicação.|
    |**Número de tentativas antes de redefinição do PIN**|Especifique o número de tentativas de introdução do PIN que podem ser efetuadas antes do utilizador ter de redefinir o PIN.|
    |**Exigir credenciais da empresa para obter acesso**|Exige que o utilizador introduza as informações de início de sessão empresarial antes de poder aceder à aplicação.|
    |**Exigir a conformidade do dispositivo com a política empresarial para acesso**|Apenas permite que a aplicação seja utilizada quando o dispositivo não é desbloqueado através de jailbreak ou rooting.|
    |**Verificar novamente os requisitos de acesso após (minutos)**|No campo **Tempo limite** , especifique o período de tempo antes dos requisitos de acesso da aplicação serem novamente verificados após a aplicação ser iniciada.|
    |**Período de tolerância offline**|Se o dispositivo estiver offline, especifique o período de tempo antes dos requisitos de acesso da aplicação serem novamente verificados.|
    |**Encriptar dados da aplicação**|Especifica que todos os dados associados a esta aplicação serão encriptados, incluindo os dados armazenados externamente, como cartões SD.<br /><br />**Encriptação para iOS**<br /><br />Para aplicações associadas à política de gestão de aplicações móveis do Intune, os dados são encriptados em descanso ao utilizar a encriptação no nível do dispositivo fornecida pelo sistema operativo. Isto é ativado através da política de PIN de dispositivo que tem de ser definida pelo administrador de TI. Quando for necessário um PIN, os dados serão encriptados de acordo com as definições na política de gestão de aplicações móveis. Conforme indicado na documentação da Apple, [os módulos utilizados pelo iOS 7 têm a certificação FIPS 140-2](http://support.apple.com/en-us/HT202739)<br /><br />**Encriptação para Android**<br /><br />Para as aplicações associadas a uma política de gestão de aplicações móveis do Intune, a encriptação é fornecida pela Microsoft. Os dados são encriptados em sincronia durante operações de E/S de ficheiros, de acordo com a definição na política de gestão de aplicações móveis. As aplicações geridas no Android utilizam encriptação AES-128 no modo CBC ao utilizar as bibliotecas de criptografia da plataforma. O método de encriptação não tem certificação FIPS 140-2. O conteúdo no armazenamento do dispositivo será sempre encriptado.|
    |**Bloquear captura de ecrã** (apenas dispositivos Android)|Especifica que as funcionalidades de captura de ecrã do dispositivo estão bloqueadas durante a utilização desta aplicação.|

4.  Quando terminar, clique em **Guardar Política**

A nova política é apresentada no nó **Políticas de Configuração** da área de trabalho **Política** .

## **Passo 4:** Associar a aplicação a uma política de gestão de dispositivos móveis e, em seguida, implementá-la.
Implementar a aplicação, garantindo que seleciona a política de gestão de aplicações móveis na página **Gestão de Aplicações Móveis** para associar a política à aplicação.

Para obter detalhes, consulte [Implementar aplicações no Microsoft Intune](deploy-apps.md)

> Para dispositivos com sistemas operativos anteriores ao iOS 7.1, as políticas associadas não serão removidas quando a aplicação é desinstalada.
> 
> Se o registo do dispositivo no Intune for anulado, as políticas não serão removidas das aplicações. Todas as aplicações com políticas aplicadas manterão as definições de política, mesmo depois da aplicação ser desinstalada e instalada novamente.

### O que fazer quando uma aplicação já está implementada nos dispositivos
Poderão existir situações em que implementa uma aplicação e em que um dos utilizadores ou dispositivos visados já tem instalada uma versão não gerida da aplicação, por exemplo, o Microsoft Word instalado pelo utilizador a partir da Loja de Aplicações.

Neste caso, tem de pedir ao utilizador para desinstalar manualmente a versão não gerida para que a versão gerida que configurou possa ser instalada.

No entanto, para dispositivos que executem o iOS 9 e posteriores, o Intune pedirá automaticamente permissão ao utilizador para assumir o controlo de gestão da aplicação existente. Se estes concordarem, então, a aplicação passará a ser gerida pelo Intune e quaisquer políticas de gestão de aplicações móveis que tenha associado às aplicações serão igualmente aplicadas.

> Se o dispositivo estiver no modo supervisionado, o Intune irá assumir a gestão das aplicações existentes sem pedir autorização aos utilizadores.

## **Passo 5:** Monitorizar a implementação da aplicação.
Assim que criar e implementar uma aplicação associada a uma política de gestão de aplicações móveis, utilize os seguintes procedimentos para monitorizar a aplicação e resolver os conflitos de política.

#### Para ver o estado da implementação

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Grupos** &gt; **Descrição Geral**

2.  Efetue um dos seguintes passos:

    -   Clique em **Todos os Utilizadores** e, em seguida, faça duplo clique no utilizador cujos dispositivos pretende examinar. Na página **Propriedades do Utilizador**, clique em **Dispositivos** e, em seguida, faça duplo clique no dispositivo que pretende examinar.

    -   Clique em **Todos os Dispositivos** &gt; **Todos os Dispositivos Móveis**. Na página **Propriedades do Grupo de Dispositivos**, clique em **Dispositivos** e, em seguida, faça duplo clique no dispositivo que pretende examinar.

3.  Na página **Propriedades dos Dispositivos Móveis** , clique em **Política** para ver uma lista das políticas de gestão de aplicações móveis que foram implementadas no dispositivo.

4.  Selecione a política de gestão de aplicações móveis cujo estado pretende ver. Pode ver os detalhes da política no painel inferior e expandir o nó para apresentar as definições.

5.  Na coluna **Estado** de cada uma das políticas de gestão de aplicações móveis, será apresentada a caixa **Está em conformidade**, **Está em conformidade (Pendente)**ou **Erro** . Se a política selecionada tiver uma ou mais definições em conflito, a caixa **Erro** será apresentada neste campo.

6.  Assim que identificar um conflito, pode rever as definições de política em conflito para utilizar a mesma definição ou implementar apenas uma política para a aplicação e utilizador.

### Como são resolvidos os conflitos de políticas
Quando existe um conflito de política de gestão de aplicações móveis na primeira implementação para o utilizador ou dispositivo, o valor de definição específico em conflito será removido da política implementada na aplicação e a aplicação utilizará um valor de conflito incorporado.

Quando existe um conflito de política de gestão de aplicações móveis em implementações posteriores na aplicação ou utilizador, o valor de definição específico em conflito não será atualizado na política de gestão de aplicações móveis implementada na aplicação e a aplicação utilizará o valor existente para essa definição.

Nos casos em que o dispositivo ou o utilizador recebe duas políticas em conflito, aplica-se o comportamento seguinte:

-   Se uma política já tiver sido implementada no dispositivo, as definições da política existente não são substituídas.

-   Se ainda não tiver sido implementada uma política no dispositivo e forem implementadas duas definições em conflito, a predefinição incorporada no dispositivo é utilizada.





<!--HONumber=May16_HO2-->


