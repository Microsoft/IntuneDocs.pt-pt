---
title: "Gerir o acesso à Internet com políticas de browser gerido| Microsoft Intune"
description: 
keywords: 
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: dc946303-e09b-4d73-8bf4-87742299bc54
ms.reviewer: jeffgilb
ms.suite: ems
ms.sourcegitcommit: 2df44199ecd904dcfb6774a942244338c1384186
ms.openlocfilehash: c4462af584d54225084159dfa35f5e1d07c36397


---

# Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune
O browser gerido é uma aplicação de navegação na Web que pode implementar na sua organização com o Microsoft Intune. Uma política de browser gerido configura uma lista de permissões ou uma lista de bloqueios que restringe os sites que os utilizadores do browser gerido podem visitar.

Como esta aplicação é uma aplicação gerida, também pode aplicar políticas de gestão de aplicações móveis à aplicação, como controlar a utilização de operações de corte, cópia e colagem, impedir capturas de ecrã e ainda garantir que as ligações para conteúdo em que os utilizadores clicam abrem apenas noutras aplicações geridas. Para obter detalhes, consulte [Configurar e implementar políticas de gestão de aplicações móveis na consola do Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md).

> [!IMPORTANT]
>Se os utilizadores instalarem o browser gerido a partir da loja de aplicações e não é for gerido pelo Intune, o seguinte comportamento aplica-se: iOS – a aplicação de browser gerido pode ser utilizada como um browser básico, mas algumas funcionalidades não estarão disponíveis e não será possível aceder a dados de outras aplicações geridas pelo Intune.
Android – a aplicação de browser gerido não pode ser utilizada.
Se os utilizadores instalarem o browser gerido sozinhos num dispositivo iOS com uma versão inferior ao iOS 9, este não será gerido pelas políticas que criar. Para garantir que o browser é gerido pelo Intune, os utilizadores têm de desinstalar a aplicação antes de poderem implementá-la como uma aplicação gerida. No iOS 9 e posteriores, se os utilizadores instalarem o browser gerido sozinhos, ser-lhes-á pedida permissão para que seja gerido pela política.

Pode criar políticas de browser gerido para os seguintes tipos de dispositivos:

-   Dispositivos a executar o Android 4 e posterior

-   Dispositivos com iOS 7.1 e posterior

O Browser Gerido do Intune suporta a abertura de conteúdos da Web de [Parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

## Criar uma política de browser gerido

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** &gt; ** Adicionar Política**.

2.  Configure um dos seguintes tipos de política de **Software** :

    -   **Política de Browser Gerido (Android 4 e posterior)**

    -   **Política de Browser Gerido (iOS 7.1 e posterior)**

    Para obter mais informações sobre como criar e implementar políticas, veja o tópico [Manage settings and features on your devices with Microsoft Intune Policies (Gerir definições e funcionalidades nos seus dispositivos com as Políticas do Microsoft Intune)](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)

3.  Utilize a seguinte tabela para o ajudar a configurar as definições de política de browser gerido:

|Nome da definição|Detalhes|
    |----------------|--------------------|
    |**Nome**|Introduza um nome exclusivo para a política de browser gerido para o ajudar a identificá-la na consola do Intune.|
    |**Descrição**|Forneça uma descrição geral da política de browser gerido e outras informações relevantes que o ajudem a localizá-la.|
    |**Ativar uma lista de permissões ou uma lista de bloqueios para restringir os URLs que o Browser Gerido pode abrir**|Selecione uma das seguintes opções:<br /><br />**Permitir que o browser gerido abra apenas os URLs indicados abaixo** - especificar uma lista dos URLs que o browser gerido pode abrir.<br /><br />**Impedir o browser gerido de abrir os URLs indicados abaixo** - especificar uma lista dos URLs que o browser gerido não poderá abrir. **Nota:** não pode incluir URLs permitidos e bloqueados na mesma política de browser gerido.<br />Para obter mais informações sobre os formatos de URL que pode especificar, veja **Formatos de URL para URLs permitidos e bloqueados**, neste tópico.|

4.  Quando terminar, clique em **Guardar Política**.

A nova política é apresentada no nó **Políticas de Configuração** da área de trabalho **Política** .

## Criar uma implementação para a aplicação de browser gerido
Após criar a política de browser gerido, pode criar uma implementação de software para a aplicação de browser gerido e associá-la à política de browser gerido que criou.

> [!IMPORTANT]
> As políticas de browser gerido não são implementadas da mesma forma que as outras políticas do Intune. Este tipo de política tem de ser associada ao pacote de software de browser gerido.

Implemente a aplicação, garantindo que seleciona a política de browser gerido na página **Gestão de Aplicações Móveis** para associar a política à aplicação.

Para obter mais informações sobre como implementar aplicações, veja [Implementar aplicações no Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## Segurança e privacidade do browser gerido

-   Em dispositivos iOS, os sites que os utilizadores visitam que têm um certificado expirado ou não fidedigno não podem ser abertos.

-   As definições que os utilizadores criam para o browser incorporado nos seus dispositivos não são utilizadas pelo browser gerido. Isto acontece porque o browser gerido não tem acesso a estas definições.

-   Se configurar as opções **Exigir PIN simples para obter acesso** ou **Exigir credenciais da empresa para obter acesso** numa política de gestão de aplicações móveis associada ao browser gerido e um utilizador clicar na ligação de ajuda na página de autenticação, em seguida, o utilizador pode procurar sites na Internet independentemente de terem sido adicionados a uma lista de bloqueios na política de browser gerido.

-   O browser gerido só pode bloquear o acesso a sites quando estes são acedidos diretamente. Não pode bloquear o acesso quando são utilizados serviços intermédios (como um serviço de tradução) para aceder ao site.

-   Para permitir a autenticação e garantir que é possível aceder à documentação do Intune, **&#42;.microsoft.com** está excluído das definições da lista de permissões ou de bloqueios – é sempre permitido.

### Desativar dados de utilização
A Microsoft recolhe automaticamente dados anónimos sobre o desempenho e a utilização do browser gerido para melhorar os produtos e serviços Microsoft, mas pode desativar a recolha de dados através da definição **Dados de Utilização** no seu dispositivo. OS utilizadores não têm controlo sobre a recolha destes dados.

## Informações de referência

### Formato do URL para URLs permitidos e bloqueados
Utilize as informações seguinte para saber mais sobre os formatos permitidos e os carateres universais que pode utilizar ao especificar os URLs na lista de permissões e bloqueios.

-   Pode utilizar o símbolo de caráter universal "**&#42;**" de acordo com as regras na lista de padrões permitidos abaixo.

-   Certifique-se de que adiciona o prefixo **http** ou **https** a todos os URLs quando os introduzir na lista.

-   Pode especificar os números da porta no endereço. Se não especificar um número da porta, os valores serão:

    -   Porta 80 para http

    -   Porta 443 para https

    A utilização de carateres universais para o número da porta não é suportada; por exemplo, **http&colon;//www&period;contoso&period;com:*;** e **http&colon;//www&period;contoso&period;com: /*;**

-   Utilize a tabela seguinte para saber mais sobre os padrões permitidos que pode utilizar ao especificar URLs:

|URL|Detalhes|Correspondências|Não corresponde|
    |-------|---------------|-----------|------------------|
    |http://www.contoso.com|Corresponde a uma única página|www.contoso.com|host.contoso.com<br /><br />www.contoso.com/images<br /><br />contoso.com/|
    |http://contoso.com|Corresponde a uma única página|contoso.com/|host.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com|
    |http://www.contoso.com/&#42;|Corresponde a todos os URLs a começar com www.contoso.com|www.contoso.com<br /><br />www.contoso.com/images<br /><br />www.contoso.com/videos/tvshows|host.contoso.com<br /><br />host.contoso.com/images|
    |http://&#42;.contoso.com/&#42;|Corresponde a todos os subdomínios em contoso.com|developer.contoso.com/resources<br /><br />news.contoso.com/images<br /><br />news.contoso.com/videos|contoso.host.com|
    |http://www.contoso.com/images|Corresponde a uma única pasta|www.contoso.com/images|www.contoso.com/images/dogs|
    |http://www.contoso.com:80|Corresponde a uma única página, ao utilizar um número de porta|http://www.contoso.com:80||
    |https://www.contoso.com|Corresponde a uma única página segura|https://www.contoso.com|http://www.contoso.com|
    |http://www.contoso.com/images/&#42;|Corresponde a uma única pasta e a todas as subpastas|www.contoso.com/images/dogs<br /><br />www.contoso.com/images/cats|www.contoso.com/videos|

-   Seguem-se exemplos de algumas entradas que não pode especificar:

    -   &#42;.com

    -   &#42;.contoso/&#42;

    -   www.contoso.com/&#42;images

    -   www.contoso.com/&#42;images&#42;pigs

    -   www.contoso.com/page&#42;

    -   Endereços IP

    -   https://&#42;

    -   http://&#42;

    -   http://www.contoso.com:&#42;

    -   http://www.contoso.com: /&#42;

### Como são resolvidos os conflitos entre a lista de permissões e de bloqueios
Se forem implementadas várias políticas de browser gerido num dispositivo e as definições entrarem em conflito, o modo (permitido ou bloqueado) e as listas de URLs são avaliados em relação a conflitos. No caso de existir um conflito, aplica-se o seguinte comportamento:

-   Se os modos em cada política forem os mesmos mas as listas de URLs forem diferentes, os URLs não serão impostos no dispositivo.

-   Se os modos em cada política forem diferentes mas as listas de URLs forem as mesmas, os URLs não serão impostos no dispositivo.

-   Se um dispositivo estiver a receber políticas de browser gerido pela primeira vez e duas políticas entrarem em conflito, os URLs não serão impostos no dispositivo. Utilize o nó **Conflitos de Política** da área de trabalho **Política** para ver os conflitos.

-   Se um dispositivo já tiver recebido uma política de browser gerido e for implementada uma segunda política com definições em conflito, as definições originais permanecem no dispositivo. Utilize o nó **Conflitos de Política** da área de trabalho **Política** para ver os conflitos.



<!--HONumber=Jun16_HO4-->


