---
# required metadata

title: Perguntas mais frequentes | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a8126cca-9ec4-454b-a20b-dc1bb6797327

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Perguntas mais frequentes sobre o Intune
Este artigo responde a algumas perguntas mais frequentes sobre o Intune. Se não vir uma resposta à sua pergunta aqui, [informe-nos](https://microsoftintune.uservoice.com/)

## Problemas gerais

-   **Quando o serviço do Intune tiver sido atualizado, como poderei sabê-lo?**

    Inicie sessão na sua conta em manage.microsoft.com. Em Descrição Geral da Administração, escolha **Ver Estado do Serviço**. A localização do seu inquilino e a agenda de manutenção estão listadas aqui. Leia mais sobre as atualizações do serviço no artigo [Novidades](/intune/deploy-use/whats-new-in-microsoft-intune).

-   **Se um utilizador mudar o nome de um dispositivo na aplicação Portal da Empresa, a alteração do nome também se reflete no Intune ou no Configuration Manager?**

    Não, essa alteração de nome é apenas para conveniência do utilizador.

-   **Existe alguma funcionalidade de assistência remota no Intune para dispositivos móveis?**

    Não, não existe. Certas aplicações de terceiros, como o [Bomgar](http://www.bomgar.com/) e o [TeamViewer](https://www.teamviewer.com/) podem ser úteis.

## Contas

-   **Se começar a avaliar o Intune e criar um novo inquilino para a avaliação, posso utilizar o mesmo inquilino para adicionar o Office 365 à avaliação?**

    Sim. Só tem de iniciar sessão com um administrador global da sua subscrição/inquilino do Intune existente, como, por exemplo, *globaladmin@&lt;company&gt;.onmicrosoft.com*

-   **A atribuição de autoridade de MDM ao Intune durante uma subscrição de avaliação limita qualquer mudança para o serviço de outra empresa caso eu mude de ideias relativamente ao Intune?**

    Embora seja difícil imaginar que não se mantenha com o Intune, a opção da autoridade de MDM não afeta a sua capacidade de mudar para outro serviço. Trata-se, especificamente, de escolher entre o Intune ou o Intune com o System Center Configuration Manager.

-   **Posso utilizar o meu nome de domínio do Office 365 existente para a posterior conta do Intune?**

    Sim, se iniciar sessão com o ID organizacional associado ao seu inquilino de Office 365 e domínio verificado existentes quando cria a respetiva avaliação do Intune ou ativa as suas licenças.

    Desta forma, o Intune utilizará o mesmo domínio/utilizadores/etc. da sua conta do Office 365. Tenha em atenção que cada utilizador do Office 365 teria de ser ativado como utilizador do Intune através de uma licença do Intune. Este procedimento teria de ser efetuado pelo administrador global que gere o inquilino.

## Inscrição

-   **Onde podem os meus utilizadores aprender a inscrever dispositivos?**

    Pode utilizar ou personalizar informações a partir das [Instruções de inscrição no Intune do utilizador final para administradores de TI](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)

-   **Como posso resolver problemas de inscrição de dispositivos?**

    Pode encontrar formas de resolver problemas comuns de inscrição em [Resolução de problemas de inscrição de dispositivos no Intune](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune)

-   **Como posso recolher registos de inscrição se um utilizador tiver um problema de inscrição?**

    Siga [estas instruções](http://www.microsoft.com/en-us/download/46391)

## Gestão de dispositivos móveis

-   **MDM Geral**

    -   **O Intune consegue detetar se um dispositivo tem jailbreak?**

        Sim, para alguns sistemas operativos. Para obter informações sobre como gerir dispositivos com jailbreak, consulte [Criar políticas de conformidade de dispositivos](/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune.md)

    -   **Posso eliminar dados empresariais de um dispositivo de forma seletiva?**

        Sim. Para mais informações sobre a eliminação seletiva, consulte [Ajudar a proteger os seus dados através de eliminação remota, bloqueio remoto ou reposição do código de acesso](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune.md)

    -   **Existe alguma forma de bloquear determinados sites no browser do dispositivo móvel através do Intune?**

        Isso não é possível no browser nativo de nenhuma plataforma. No entanto, pode permitir ou bloquear URLs quando tiver implementado o browser gerido do Intune em dispositivos iOS e Android. Para mais informações, consulte [Gerir o acesso à Internet através de políticas de browser gerido](/intune/Deploy-Use/Manage-Internet-access-using-managed-browser-policies-with-Microsoft-Intune.md)

    -   **É possível impedir um utilizador de desinstalar uma aplicação?**

        Geralmente, não. Contudo, num dispositivo iOS supervisionado, pode impedir um utilizador de desinstalar uma aplicação que tenha sido distribuída através do Apple Configurator. 

    -   **Existe alguma forma de gerir a utilização de dados móveis?**

        Não diretamente, mas pode certificar-se de que o Wi-Fi é o método preferencial de ligação ao enviar perfis Wi-Fi para os dispositivos, conforme descrito em [Ajudar utilizadores a estabelecerem uma ligação a redes empresariais através de perfis Wi-Fi](/intune/Deploy-Use/wi-fi-connections-in-microsoft-intune.md). Além disso, algumas plataformas (como, por exemplo, iOS e Android KNOX) permitem controlar definições, tais como o roaming de voz e dados.

    -   **Existe alguma forma de impedir um utilizador de anular a inscrição de um dispositivo? E se o dispositivo for propriedade da empresa?**

        Geralmente, não. No entanto, ao utilizar as definições personalizadas do Windows Phone, pode impedir a anulação de inscrições do utilizador no Windows Phone 8.1. Além disso, no caso dos dispositivos iOS supervisionados e inscritos no Programa de Inscrição de Dispositivos (DEP) da Apple, é possível impedir um utilizador de anular a inscrição de um dispositivo.

    -   **Posso mudar a autoridade de MDM que escolhi?**

        Pode mudar a autoridade de MDM nalgumas situações. Para tal, contacte o Suporte, conforme descrito em [Como obter suporte do Microsoft Intune](/intune/Troubleshoot/How-to-get-support-for-Microsoft-Intune.md). A tabela abaixo descreve as alterações que são possíveis. As alterações na autoridade de MDM exigem a reinscrição dos dispositivos.

        **Para:** Intune!**Para:** O365|**Para:** Configuration Manager com o Intune|
        
        **De:** Intune| |Sim&#42;|Sim|



-   ****De:** O365||Sim&#42;||Sim|**

    -   ****De:** Configuration Manager com o Intune|Sim|Sim| |**

        &#42;As autoridade de MDM do O365 e do Intune podem coexistir, pelo que não terá de reinscrever os dispositivos móveis. Windows Posso carregar uma aplicação da Loja Windows em sideload?

    -   **As aplicações disponíveis publicamente não podem ser carregadas em sideload.**

        Embora possa transferir o XAP, não pode carregá-lo para o Intune por se tratar de um XAP público, encriptado e assinado com um certificado de assinatura de código do programador. Só é possível carregar em sideload as aplicações desenvolvidas por si e assinadas com o seu próprio certificado de assinatura de código.

    -   **As aplicações da Loja do Windows Phone distribuídas através do Portal da Empresa necessitam que o utilizador final tenha uma Conta Microsoft?**

        Sim, o utilizador final não poderá obter as aplicações se não tiver uma Conta Microsoft. Com exceção das aplicações LOB privadas de sideload, que podem ser implementadas num dispositivo sem uma Conta Microsoft.

        **É necessária uma Conta Microsoft num Windows Phone 8.1 para o mesmo poder ser gerido pelo Intune?**
        Não. Contudo, é necessária para instalar a maioria das aplicações a partir do arquivo público. Por que é que o Windows Phone requer um certificado da Symantec para a gestão? O Windows Phone controla a forma como pode instalar aplicações. Qualquer utilizador com uma conta Microsoft pode instalar aplicações a partir da loja do Windows Phone ou as empresas podem instalar ou efetuar o sideload das respetivas aplicações de linha de negócio (Line of Business, LOB) programadas internamente através de um processo especial descrito na documentação do Windows Phone.

        Quando instala aplicações LOB, os Windows Phones apenas confiam num tipo de certificado especial emitido pela Symantec. Não pode utilizar outros certificados gerados de forma comercial ou privada. Este requisito aplica-se a todas as soluções de gestão de dispositivos móveis, não apenas ao Intune. O certificado da Symantec cria um token de inscrição de aplicações (AET). O AET pode ser instalado num dispositivo quando este é inscrito na gestão de dispositivos móveis ou pode ser instalado fora de banda a partir de um site seguro ou a partir de um anexo de e-mail. Os administradores têm de assinar todas as aplicações de LOB com o certificado da Symantec, com as ferramentas fornecidas no [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=268439). Quando os utilizadores tentam instalar aplicações de LOB, o sistema operativo do Windows Phone compara a assinatura no AET com a assinatura da aplicação.

        -   Se as assinaturas corresponderem, a instalação é autorizada a continuar.

        -   Se não for possível verificar o AET, a instalação falha.

        -   Existem diversos motivos pelos quais pode não ser possível verificar o AET:

        O AET nunca foi instalado no dispositivo

    **O AET expirou**
  O AET não foi criado com o mesmo certificado da Symantec utilizado para assinar a aplicação O Windows Phone não requer a presença do AET durante a inscrição na MDM mas, até à versão de novembro de 2014, o Intune exigia o AET e um ficheiro ssp.xap assinado porque não havia nenhuma outra forma de instalar o AET e o ficheiro ssp.xap exceto durante a inscrição.

      > Como é que o AET é criado para os utilizadores do Intune?

    **Quando os administradores carregam o ficheiro .pfx do certificado da Symantec, o Intune cria automaticamente o AET e implementa-o nos Windows Phones inscritos.**
       Os administradores do Intune não precisam de utilizar a ferramenta AET Generator no Windows Phone SDK.

       -   O Intune não suporta a criação manual do AET nem a implementação do mesmo fora de banda. Que alterações foram efetuadas para reduzir a necessidade de um certificado da Symantec?

        -   Na versão de novembro de 2014, o Intune efetuou alterações para permitir cenários em que as empresas não possuem um certificado da Symantec. O Portal da Empresa para Windows Phone 8.1 está disponível para instalação a partir da loja, pelo que não precisa de ser assinado com um certificado da Symantec nem validado com um AET. Em vez disso, a aplicação é validada durante o processo de publicação da loja.

        Os dispositivos Windows Phone 8.1 podem ser inscritos com ou sem um AET no telemóvel. Se existir um AET disponível, este será instalado quando o dispositivo sincronizar com o Intune pela primeira vez.

        **Se não existir um AET, o dispositivo ainda pode ser gerido pelo Intune e os utilizadores podem instalar o Portal da Empresa a partir da loja e utilizar a maioria das funcionalidades do Portal da Empresa sem um certificado da Symantec para assinar aplicações.**
        Não foram efetuadas alterações ao requisito da Symantec para os dispositivos Windows Phone 8.

        -   Os dispositivos Windows Phone 8 têm de ter o ficheiro ssp.xap assinado e o AET presentes durante a inscrição ou não a poderão a efetuar.

        -   Que funcionalidade é suportada se um dispositivo Windows Phone 8.1 for inscrito mas não existir um certificado da Symantec?

        -   Se um dispositivo Windows Phone 8.1 for inscrito mas não existir um certificado da Symantec, pode:

        -   Criar políticas e emiti-las para o dispositivo

        -   Configurar as informações de contacto do departamento de TI que serão apresentadas no Portal da Empresa

        Criar ligações avançadas para a loja e implementá-las no Portal da Empresa

        > [!IMPORTANT]
        > Criar ligações para páginas Web e implementá-las no Portal da Empresa Criar termos e condições que têm de ser aceites pelos utilizadores antes de poderem utilizar o Portal da Empresa

        **A única coisa que não pode fazer sem um certificado da Symantec é implementar aplicações de LOB.**
        O Intune Software Publisher não verifica se as aplicações estão assinadas quando o utilizador as carrega. Se implementar aplicações não assinadas, estas irão falhar quando os utilizadores as tentarem instalar. O que podem fazer os utilizadores se tiverem o Portal da Empresa mas não existir um certificado da Symantec?

        Os dispositivos Windows Phone 8.1 não têm de estar inscritos para que os utilizadores possam instalar o Portal da Empresa a partir da loja.

        -   Se o dispositivo não estiver inscrito, será pedido ao utilizador que o inscreva. Tocar no pedido do Portal da Empresa direciona os utilizadores diretamente para **Definições/Área de trabalho**, onde poderão inscrever os dispositivos.

        -   Mesmo sem inscrever o dispositivo, os utilizadores podem realizar as seguintes ações com o Portal da Empresa instalado a partir da loja:

        -   Aceitar ou recusar os termos e condições configurados pelo administrador.

        -   Se os utilizadores recusarem os termos e condições, o Portal da Empresa é fechado.

        -   Ver as informações de contacto do departamento de TI.

        Ver todos os dispositivos inscritos, incluindo dispositivos iOS, Android e Windows Utilizar ligações avançadas para aplicações na loja Utilizar ligações Web para abrir páginas Web Com o dispositivo inscrito, os utilizadores podem ver o dispositivo na lista **Os Meus Dispositivos** .

        Uma vez inscrito, o dispositivo está sujeito a todas as políticas do Intune implementadas.

        **Os dispositivos têm de estar inscritos para obter o AET e para instalar aplicações de LOB. Um dispositivo não inscrito que tente instalar uma aplicação de LOB será direcionado para a inscrição.**
        A única coisa que os utilizadores não podem fazer, caso a empresa não tenha um certificado da Symantec, é instalar aplicações de LOB implementadas pelo administrador. A nossa empresa já tem um certificado e tem feito a inscrição de dispositivos Windows Phone 8.1.

        **Tenho de fazer algo de forma diferente, agora que o Portal da Empresa está disponível na loja?**
        O ficheiro ssp.xap atual do Centro de Transferências ainda funciona nos dispositivos Windows Phone 8.1.

        -   Pode continuar a instruir os utilizadores para se inscreverem e obterem o portal da empresa durante a instalação.

        -   Quais são as vantagens e desvantagens para os utilizadores se obtiverem o Portal da Empresa a partir da loja?

        -   Vantagens:

        -   Os utilizadores obtêm ligações avançadas e ligações Web, mesmo que o dispositivo Windows Phone 8.1 não esteja inscrito

        Quando a Microsoft atualiza o Portal da Empresa, a aplicação da loja é atualizada automaticamente sem que o utilizador tenha de transferir, assinar e implementar novamente o ficheiro ssp.xap

        -   A documentação para os utilizadores do Windows Phone 8.1, iOS, Android e Windows é consistente: "Aceda à loja e instale o Portal da Empresa".

        -   Os utilizadores veem a aplicação à medida que é instalada e recebem instruções de inscrição quando é aberta

        Desvantagens:

        -   Os utilizadores veem uma caixa de verificação para instalar um “**hub da empresa**”, mas não são direcionados para o Portal da Empresa na lista de aplicações do dispositivo

        -   Os utilizadores não têm de aceitar termos e condições personalizados até abrirem o Portal da Empresa

        -   Nas seguintes circunstâncias, pode continuar a instruir os utilizadores para se inscreverem e para instalarem o ficheiro ssp.xap durante a inscrição:

        **Se a empresa bloquear o acesso dos Windows Phones à loja, os utilizadores têm de instalar o ficheiro ssp.xap durante a inscrição.**

        -   Se os utilizadores não tiverem contas Microsoft configuradas nos respetivos Windows Phones, não poderão instalar o Portal da Empresa a partir da loja.

        -   Se a documentação existente para a inscrição do Windows Phone lhes indicar para acederem primeiro a Definições, Área de Trabalho, poderá demorar algum tempo para atualizar os documentos e direcionar os utilizadores para a loja.

        -   Qual é a diferença entre o ficheiro ssp.xap no Centro de Transferências e a aplicação na loja?

        **O Portal da Empresa na loja não tem de ser assinado por um certificado da Symantec para ser instalado**
        O Portal da Empresa na loja apresenta os termos e condições ao utilizador, mas o ficheiro ssp.xap no Centro de Transferências não o faz O Portal da Empresa na loja é um ficheiro .appx em vez de .xap

        -   Posso obter o ficheiro do Portal da Empresa e enviá-lo para os meus utilizadores, em vez de os direcionar para a loja?

        -   Sim.

        -   A aplicação Portal da Empresa pode ser transferida para os seguintes sistemas operativos a partir do Centro de Transferências:

        **Windows Phone 8.1: [http://go.microsoft.com/fwlink/?LinkId=615799](http://go.microsoft.com/fwlink/?LinkId=615799)**
        Windows Phone 8.0 : [http://go.microsoft.com/fwlink/?LinkId=268440](http://go.microsoft.com/fwlink/?LinkId=268440) Windows 8.1: [http://go.microsoft.com/fwlink/?LinkId=615800](http://go.microsoft.com/fwlink/?LinkId=615800) As empresas ainda podem utilizar a Ferramenta de Suporte para a Gestão de Versões de Avaliação do Windows Intune do Windows Phone se não tiverem um certificado da Symantec e continuarem a indicar aos utilizadores para instalarem o Portal da Empresa a partir da loja?

        Sim.

        > [!IMPORTANT]
        > Se precisar de efetuar uma prova de conceito que inclua a instalação de aplicações de LOB, a ferramenta de gestão de versões de avaliação funciona com a versão de loja do portal da empresa. No entanto, dado que o AET do certificado da Symantec já não é necessário para inscrever dispositivos Windows Phone 8.1, as empresas podem testar a instalação de aplicações através de ligações avançadas para aplicações na loja.

        **A Ferramenta de Suporte para a Gestão de Versões de Avaliação do Windows Intune do Windows Phone é apenas destinada a subscrições de avaliação do Intune.**
        Utilize a ferramenta de gestão de versões de avaliação apenas para testes. Os dispositivos inscritos com o AET da ferramenta de gestão de versões de avaliação têm de anular a inscrição e inscrever-se novamente se o certificado da Symantec da ferramenta de gestão de versões de avaliação já não estiver disponível ou se a empresa obtiver o seu próprio certificado da Symantec para assinar aplicações. As empresas podem começar sem um certificado da Symantec e adicionar um mais tarde, mesmo após terem sido inscritos dispositivos Windows Phone 8.1? Sim. Mesmo que já tenham sido inscritos dispositivos Windows Phone 8.1, pode obter um certificado da Symantec, assinar o ficheiro ssp.xap e carregá-lo juntamente com o ficheiro .pfx.


-   **O Intune irá então gerar o AET.**

    -   **Os dispositivos Windows Phone 8.1 obterão o AET na próxima vez que sincronizarem, até oito horas.**

        Aguarde, pelo menos, oito horas antes de implementar aplicações de linha de negócio, após carregar os ficheiros .xap e .pfx.

-   **Android**

    -   **Quanto tempo demora a encriptar um dispositivo Android?**

        Depende principalmente da velocidade do processador do dispositivo e da quantidade de memória total e utilizada, além de que não é uma função do Intune. iOS

    -   **Ao implementar aplicações iOS com o Intune, se os ficheiros IPA e de Manifesto da aplicação tiverem sido carregados, a aplicação necessita de um ID Apple especificado para continuar a instalação?**

        Não. Quando o Intune está a fornecer os bits (IPA carregado para o Intune), as aplicações são carregadas em sideload e não necessitam de um ID Apple.

    -   **Existe alguma forma de permitir a instalação de aplicações no iOS sem permitir o acesso à Apple Store?**

        Não, mas pode ativar a App Store e utilizar a função das aplicações permitidas e bloqueadas no iOS para controlar o que os utilizadores estão a fazer.

    -   **As aplicações LOB de sideload não necessitam de acesso à Apple App Store.**

        As aplicações da Apple Store distribuídas através do Portal da Empresa necessitam de que o utilizador final tenha uma conta do iTunes? Sim, o utilizador final não poderá obter as aplicações se não tiver uma conta do iTunes.

## Posso bloquear a App Store?

-   **Sim, pode, mas também irá bloquear todas as instalações e atualizações das aplicações da App Store, não apenas das iniciadas pelo utilizador final.**

    Isto significa que todas as aplicações públicas da App Store que implementar a partir do Intune também irão falhar.

-   **Implementação de aplicações**

    Como posso adicionar uma aplicação recomendada? No Intune estas são designadas por "aplicações em destaque" e estão documentadas em [Implementar aplicações no Microsoft Intune](/Intune/Deploy-Use/deploy-apps-in-microsoft-intune.md)

## Posso obter armazenamento na nuvem adicional para as aplicações que quero implementar?

-   **Sim.**

    Pode ler sobre este tópico em [Implementar aplicações](/Intune/Deploy-Use/deploy-apps.md), na secção *Requisitos do armazenamento na nuvem* Segurança O BitLocker pode ser imposto pelo Intune?

-   **O agente OMA-DM no Windows 8.1/RT permite-lhe ler (obter) o estado da encriptação.**

    Não é possível defini-lo. Isto aplica-se ao Intune e a outros serviços de gestão de dispositivos móveis. Se utilizar o BitLocker para encriptar um tablet com Windows 8, posso impor a eliminação completa de dispositivo se um utilizador falhar o início de sessão várias vezes consecutivas?

## Não existe nenhuma opção para eliminação completa nos dispositivos com Windows 8.1/RT relativamente a qualquer serviço de gestão de dispositivos móveis, incluindo o Intune.

-   **O Intune possibilita a eliminação seletiva para esses dispositivos.**

    Para obter mais informações sobre a eliminação/eliminação seletiva no Intune, consulte [Proteger aplicações e dados com o Microsoft Intune](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md) Portal da Empresa

## Posso personalizar o Portal da Empresa?

-   **Sim.**

    Na consola de administração do Intune, aceda a **Admin&gt;Portal da Empresa** para aceder a essas definições. Microsoft Intune com Configuration Manager

-   **Quando utilizar o Configuration Manager com o Intune, onde posso gerir os meus dispositivos?**

    Pode gerir todos os seus dispositivos a partir da consola do Configuration Manager, ainda que os dispositivos com o agente do Intune instalado apareçam na consola do Intune. Os dispositivos móveis não aparecem na consola do Intune.

-   **Posso efetuar uma eliminação seletiva nos dispositivos?**

    Se estiver a utilizar o System Center 2012 R2 Configuration Manager ou posterior com o Intune, pode efetuar uma eliminação seletiva que remove dados da empresa. Para mais informações, consulte [Proteger aplicações e dados com o Microsoft Intune](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md)



<!--HONumber=May16_HO2-->


