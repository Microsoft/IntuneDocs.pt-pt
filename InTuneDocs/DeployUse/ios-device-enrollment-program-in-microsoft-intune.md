---
title: "Gestão do Apple DEP para dispositivos iOS | Microsoft Intune"
description: "Implemente um perfil de inscrição que inscreva dispositivos iOS comprados com o Programa de Inscrição de Dispositivos iOS (DEP) por ondas eletromagnéticas em dispositivos Apple geridos."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8ff9d9e7-eed8-416c-8508-efc20fca8578
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e2daff5dae435df55c866adbf602f554500d50e0
ms.openlocfilehash: e898d070eb61583ff379821c9bf24f3997ae177e


---

# Inscrever dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos
O Microsoft Intune pode implementar um perfil de inscrição que inscreve os dispositivos iOS comprados através do Programa de Inscrição de Dispositivos (DEP) por ondas eletromagnéticas. O pacote de inscrição pode incluir opções do assistente de configuração do dispositivo. Os utilizadores não podem anular a inscrição de dispositivos inscritos através do DEP.

## Gestão do Apple DEP para dispositivos iOS com o Microsoft Intune
Para gerir dispositivos iOS propriedade da empresa com o Programa de Inscrição de Dispositivos da Apple (DEP), a sua empresa tem de se associar ao DEP da Apple e de adquirir dispositivos através desse programa. Os detalhes desse processo estão disponíveis em:  [https://deploy.apple.com](https://deploy.apple.com) Entre as vantagens do programa incluem-se a configuração automatizada de dispositivos sem ligar por USB cada dispositivo a um computador.

Antes de poder inscrever dispositivos iOS pertencentes à empresa no DEP, precisa de um Token do DEP da Apple. Este token permite ao Intune sincronizar informações sobre os dispositivos pertencentes à empresa participantes no DEP. Também permite ao Intune efetuar carregamentos do Perfil de Inscrição para a Apple e atribuir dispositivos a esses perfis.

1.  **Começar a gerir dispositivos iOS com o Microsoft Intune** Antes de poder inscrever dispositivos iOS no Programa de Inscrição de Dispositivos (DEP), tem de concluir a ativação da gestão iOS para o Intune.

2.  **Obter uma Chave de Encriptação** Na qualidade de utilizador administrativo, abra a [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Admin** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS** &gt; **Programa de Inscrição de Dispositivos** e clique em **Transferir Chave de Encriptação**. Guarde o ficheiro da chave de encriptação (.pem) localmente. O ficheiro .pem é utilizado para pedir um certificado de relação de confiança a partir do portal do Programa de Inscrição de Dispositivos da Apple.

      ![Atualizar um token do programa de inscrição de dispositivos](../media/dev-sa-ios-dep.png)

3.  **Obter um token do Programa de Inscrição de Dispositivos** Aceda ao [Portal do Programa de Inscrição de Dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sessão com o ID Apple da sua empresa. Este ID Apple tem de ser utilizado no futuro para renovar o seu token do DEP.

    1.  No [Portal do Programa de Inscrição de Dispositivos](https://deploy.apple.com), aceda a **Programa de Inscrição de Dispositivos** &gt; **Gerir Servidores** e, em seguida, clique em **Adicionar Servidor MDM**.

    2.  Introduza o **Nome do Servidor MDM** e, em seguida, clique em **Seguinte**. O nome do servidor é uma referência para identificar o servidor MDM. Não é o nome nem o URL do servidor Microsoft Intune.

    3.  É aberta a caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;**. Clique em **Escolher Ficheiro…** para carregar o ficheiro .pem e, em seguida, clique em **Seguinte**.

    4.  A caixa de diálogo **Adicionar &lt;NomeDoServidor&gt;** apresenta uma ligação para o **Token do Seu Servidor**. Transfira o ficheiro do token do servidor (.p7m) para o seu computador e, em seguida, clique em **Concluído**.

    Este ficheiro do certificado (.p7m) é utilizado para estabelecer uma relação de confiança entre os servidores do Intune e do Programa de Inscrição de Dispositivos da Apple.

4.  **Adicionar o token do DEP ao Intune** Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Admin** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS** &gt; **Programa de Inscrição de Dispositivos** e clique em **Carregar o Token do DEP**. **Procure** o ficheiro do certificado (.p7m), introduza o seu **ID Apple**e, em seguida, clique em **Carregar**.

5.  **Adicionar a Política de Inscrição de Dispositivos da Empresa** Na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Política** &gt; **Inscrição de Dispositivos da Empresa** e, em seguida, clique em **Adicionar**.

    Forneça detalhes **Gerais** , incluindo o **Nome** e a **Descrição**, especifique se os dispositivos atribuídos ao perfil têm afinidade com o utilizador ou se pertencem a um grupo.
      - **Pedido de afinidade de utilizadores**: o dispositivo tem de ser afiliado a um utilizador durante a configuração inicial e, em seguida, receber permissões para aceder ao e-mail e aos dados da empresa em nome do utilizador.  A **afinidade de utilizador** deve ser configurada para dispositivos geridos por DEP que pertencem aos utilizadores e que precisam de utilizar o portal da empresa (por exemplo, para instalar aplicações). **Nota:** os dispositivos DEP com afinidade de utilizador não podem suportar a autenticação multifator.
      - **Sem afinidade de utilizador**: o dispositivo não está afiliado a um utilizador. Utilize esta afiliação em dispositivos que efetuem tarefas sem aceder aos dados de utilizador locais. As aplicações que requerem afiliação de utilizadores, incluindo a aplicação Portal da Empresa utilizada para instalar aplicações de linha de negócio, não irão funcionar.

    Também pode **Atribuir dispositivos ao seguinte grupo**. Clique em **Selecionar…** para escolher um grupo.

    [!INCLUDE[groups deprecated](../includes/group-deprecation.md)]

    Em seguida, ative **Configurar definições do Programa de Inscrição de Dispositivos para esta política** para suportar DEP.

      ![Painel do assistente de configuração](../media/pol-sa-corp-enroll.png)

     Estão disponíveis as seguintes definições para dispositivos geridos por DEP:

     - **Departamento** - É apresentado quando os utilizadores tocam em "Sobre a Configuração de" durante a ativação
     - **Número de telefone de suporte** - Apresentado quando o utilizador clica no botão **Preciso de ajuda** durante a ativação
     - **Modo de preparação** - Este estado é definido durante a ativação e não pode ser alterado sem a reposição de fábrica do dispositivo:
        - **Não supervisionado** - Capacidades de gestão limitadas
        - **Supervisionado** - Ativa mais opções de gestão e desativa o Bloqueio de Ativação por predefinição
     - **Bloquear perfil de inscrição para o dispositivo** - Este estado é definido durante a ativação e não pode ser alterado sem uma reposição de fábrica
        - **Desativar** - Permite que o perfil de gestão seja removido do menu **Definições**
        - **Ativar** - (requer **Modo de Preparação** = **Supervisionado**) desativa as definições de iOS que poderiam permitir a remoção do perfil de gestão
     - **Opções do Assistente de Configuração** - Estas definições são opcionais e podem ser configuradas mais tarde no menu **Definições** de iOS
        - **Código de Acesso** - Pedido de código de acesso durante a ativação. Solicite sempre um código de acesso, a menos que o dispositivo esteja protegido ou tenha o acesso controlado de outra forma (ou seja, modo de local público que restringe o dispositivo a uma aplicação).
        - **Serviços de Localização** - Se ativado, o Assistente de Configuração solicita o serviço durante a ativação
        - **Restaurar** - Se estiver ativado, o Assistente de Configuração solicita a cópia de segurança de iCloud durante a ativação
        - **ID Apple** - É necessário um ID Apple para transferir aplicações iOS da loja de aplicações, incluindo as instaladas pelo Intune. Se estiver ativado, o iOS irá pedir aos utilizadores um ID Apple quando o Intune tenta instalar uma aplicação sem um ID.
        - **Termos e Condições** - se ativado, o Assistente de Configuração solicita aos utilizadores que aceitem os termos e condições da Apple durante a ativação
        - **Touch ID** - se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Apple Pay** - se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Zoom** - se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Siri** - se ativado, o Assistente de Configuração solicita este serviço durante a ativação
        - **Enviar dados de diagnóstico para a Apple** - se ativado, o Assistente de Configuração solicita este serviço durante a ativação
     -  **Ativar a gestão adicional do Apple Configurator** - defina como **Não Permitir** para impedir a sincronização de ficheiros com o iTunes ou a gestão através do Apple Configurator. A Microsoft recomenda que defina para **Não Permitir**, exporte qualquer configuração adicional do Apple Configurator e, em seguida, implemente como um perfil de configuração iOS Personalizada através do Intune, em vez de utilizar esta definição para permitir a implementação manual com ou sem um certificado.
        - **Não Permitir** - impede o dispositivo de comunicar através de USB (desativa o emparelhamento)
        - **Permitir** - permite ao dispositivo comunicar através de ligação USB para qualquer PC ou Mac
        - **Requer certificado** - permite o emparelhamento com um Mac, com um certificado importado para o perfil de inscrição

6.  **Atribuir Dispositivos DEP para Gestão** Aceda ao [Portal do Programa de Inscrição de Dispositivos](https://deploy.apple.com) (https://deploy.apple.com) e inicie sessão com o ID Apple da sua empresa. Aceda a **Programa de Implementação** &gt; **Programa de Inscrição de Dispositivos** &gt; **Gerir Dispositivos**. Especifique como irá **Escolher Dispositivos**, fornecer informações sobre o dispositivo e especificar detalhes pelo **Número de Série**e **Número da Encomenda**do dispositivo, ou como **Carregar Ficheiro CSV**. Em seguida, selecione **Atribuir ao Servidor**, selecione o &lt;NomeDoServidor&gt; especificado para o Microsoft Intune e, em seguida, clique em **OK**.

7.  **Sincronizar Dispositivos Geridos por DEP** Na qualidade de utilizador administrativo, abra a [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Admin** &gt; **Gestão de Dispositivos Móveis** &gt; **iOS** &gt; ** Programa de Inscrição de Dispositivos** e clique em **Sincronizar agora**. É enviado um pedido de sincronização para a Apple. Para ver dispositivos geridos por DEP após a sincronização, na [consola de administração do Microsoft Intune](http://manage.microsoft.com), aceda a **Grupos** &gt; **Todos os Dispositivos** &gt; **Dispositivos Pré-inscritos Empresariais** &gt; **Por Número de Série do iOS**. Na área de trabalho **Por Número de Série do iOS**, o **Estado** dos dispositivos geridos indica "Não contactado" até o dispositivo ser ligado e executar o Assistente de Configuração para inscrever o dispositivo.

    Para estar em conformidade com os termos da Apple para o tráfego DEP aceitável, o Intune impõe as seguintes restrições:
     -  Uma sincronização completa do DEP não pode ser executada mais do que uma vez a cada 7 dias. Durante uma sincronização completa, o Intune atualiza cada número de série que a Apple tenha atribuído ao Intune, quer o número tenha sido ou não sincronizado anteriormente. Se for tentada uma sincronização completa no prazo de 7 dias após a sincronização completa anterior, o Intune apenas atualiza os números de série que ainda não estejam listados no Intune.
     -  São atribuídos 10 minutos a qualquer pedido de sincronização para ser concluído. Durante este tempo ou até o pedido ser concluído com êxito, o botão Sincronizar está desativado.

8.  **Distribuir dispositivos pelos utilizadores** Os dispositivos pertencentes à empresa podem agora ser distribuídos pelos utilizadores. Quando um dispositivo iOS é ativado, será inscrito para gestão pelo Intune.

## Alterações às atribuições de grupo do Intune

A partir de novembro, a gestão de grupos de dispositivos irá mudar para o Azure Active Directory. Após a transição para grupos do Azure Active Directory, a atribuição de grupo não será apresentada nas opções do **Perfil de Inscrição Empresarial**. Uma vez que esta alteração vai ser implementada durante alguns meses, poderá não estar disponível de imediato. Depois de mudar para o novo portal, as atribuições de grupos de dispositivos dinâmicas podem ser definidas com base nos nomes de Perfil de Inscrição Empresarial. Este processo garante que os dispositivos previamente atribuídos a um grupo de dispositivos serão inscritos de forma automática no grupo com a política e as aplicações implementadas. [Saiba mais sobre os grupos do Azure Active Directory](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-manage-groups/)

### Consulte também
[Prepare-se para inscrever dispositivos](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Sep16_HO2-->


