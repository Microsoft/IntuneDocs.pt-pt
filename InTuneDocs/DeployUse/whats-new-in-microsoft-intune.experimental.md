---
# required metadata

experiment_id: lindavr-abtest-20160527
title: Novidades | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Novidades do Microsoft Intune

## Maio de 2016


À exceção da integração do TeamViewer, todas estas funcionalidades também são suportadas para implementações híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a página [ Novidades Híbridas](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Documentação

Bem-vindo à versão de pré-visualização de [docs.microsoft.com](https://docs.microsoft.com/en-us/intune)!
É uma plataforma de conteúdo completamente nova e moderna, concebida para ser mais fácil para si e para os nossos clientes compreenderem e utilizarem o Intune.
Para ler mais sobre todas as novas funcionalidades, consulte [Introdução ao docs.microsoft.com](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Estado de funcionamento do serviço Intune
As informações de estado de funcionamento do serviço Intune foram movidas para uma localização central com outros serviços Microsoft. Irá agora encontrar estas informações no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx) em **Estado de Funcionamento do Serviço**.
Para mais informações, consulte [esta mensagem no blogue](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Gestão de aplicações

- **MAM SDK: suporta a configuração do comprimento do PIN.** Poderá especificar o comprimento do PIN para aplicações MAM, semelhante a um PIN de dispositivo. Isto irá necessitar que os utilizadores finais respeitem as novas restrições que definiu. Verão um ecrã de PIN ligeiramente modificado para caber a entrada mais longa. Para mais detalhes, consulte [Definições de política de MAM para Android](/intune/deploy-use/android-mam-policy-settings), e [Definições de política de MAM para iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype para Empresas, para iOS e Android.** É agora possível segmentar o Skype para empresas com [MAM sem políticas de inscrição](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Depois de os utilizadores iniciarem sessão, as políticas de MAM serão aplicadas.

- **Novas aplicações disponíveis para a gestão com as políticas de MAM.** As aplicações do Microsoft Word, Excel e PowerPoint para Android podem agora ser associadas a políticas de MAM em dispositivos que não estão inscritos no Intune. Para uma lista completa de aplicações suportadas, aceda à galeria de aplicações móveis do Microsoft Intune na [página de parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).

### Gestão de dispositivos

- **Sessões de assistência remota para PCs Windows.** A integração do TeamViewer para PCs Windows geridos pelo software de cliente do Intune irá permitir estabelecer sessões de assistência remota com PCs Windows para dar apoio ao departamento de suporte técnico de ajuda. Os PCs suportados incluem o Windows 7, 8, 8.1 e Windows 10.
Para detalhes, consulte [Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune](/intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#respond-to-a-remote-assistance-request)

### Atualizações ao portal da empresa

#### Aplicação Portal da Empresa para Android

- **Notificações de alerta do utilizador final**: os utilizadores finais irão agora ver notificações de alerta da aplicação Portal da Empresa para Android ao inscreverem os respetivos dispositivos ou ao removerem os respetivos dispositivos do Portal da Empresa.

- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação Portal da Empresa para Android.** Para melhorar o desempenho e o dimensionamento, o Intune já não mostra todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel Os Meus Dispositivos da aplicação Portal da Empresa para Android. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune.
-
#### Web site do Portal da Empresa

**Site do Portal da Empresa: uma faixa de identificação do dispositivo irá fornecer mais informações aos utilizadores finais.** Os utilizadores finais podem agora identificar facilmente o dispositivo que selecionaram quando estão a utilizar o site do Portal da Empresa. Se for selecionado o dispositivo incorreto, poderão selecionar o dispositivo correto ao tocar na ligação **Tocar aqui** na faixa da página inicial.


## Novidades futuras

- **Inclusão da IU do centro de mensagens**. Como parte da migração do Intune para o [portal de gestão do Office 365](https://portal.office.com/), vamos começar a tirar partido do respetivo Centro de Mensagens para comunicar novas funcionalidades e outras notificações. Além disso, ao instalar a aplicação móvel Office 365 Admin complemento, pode receber notificações no seu telemóvel e reencaminhar facilmente mensagens para utilizadores ou para um alias de distribuição.
Vamos começar a utilizar o Centro de Mensagens com a versão de maio para o notificar quando as atualizações estiverem concluídas e incluiremos informações sobre funcionalidades novas e melhoradas do Intune. Consulte o Centro de Mensagens ainda hoje, iniciando sessão no [portal de Gestão do Office 365](https://portal.office.com/) e selecionando a opção CENTRO DE MENSAGENS no painel de navegação esquerdo.

- **Alterações às contas de Gestores de Inscrição de Dispositivos**. Para melhorar o desempenho e o dimensionamento, o Intune já não mostra **todos** os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel **Os Meus Dispositivos** da aplicação Portal da Empresa para iOS. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune. Além disso, o Intune pretere a utilização de contas DEM com o Programa de Inscrição de Dispositivos Apple ou a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados. Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível.

### Plano de nuvem
Mantenha-se informado sobre desenvolvimentos futuros do Intune com o [plano Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Depreciação de serviço
- **Aplicações do Visualizador do Intune.** Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
    - Visualizador de AV do Intune
    - Visualizador de PDFs do Intune
    - Visualizador de Imagens do Intune para Android a partir do Google Play

  Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova aplicação de Rights Management (partilha RMS) para Android, que permite implementar uma aplicação em vez de três aplicações separadas para ver, com segurança, ficheiros empresariais em dispositivos Android. Saiba mais sobre a aplicação de partilha RMS (com ligação para a documentação).

- **Remoção da Filtragem Personalizada de Grupo de Regras de Notificação.**
As regras de notificação do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificação para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune criado por si. A partir de 1 de junho de 2016, a filtragem de grupos criados pelo utilizador já não será suportada.

    Atualmente, para filtrar uma regra de notificação para um grupo que criou a partir da consola de administração do Microsoft Intune, terá de efetuar os seguintes passos:

    Na área de trabalho **Admin**, clique em **Regras de Notificação** > **Criar Nova Regra**

    No passo dois do Assistente para Criar Regra de Notificação, selecione os grupos de dispositivos que a regra irá filtrar. Este passo, “selecionar grupos de dispositivos”, está a ser removido da Consola do Intune.

    A linha cronológica preliminar para esta alteração é a seguinte:
    - Em junho de 2016, os novos inquilinos não verão o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não serão afetados.
    - Por volta de agosto de 2016, alguns inquilinos existentes não verão “selecionar grupos de dispositivos” no assistente.
    - Por volta de outubro de 2016, esperamos que nenhum inquilino veja “selecionar grupos de dispositivos” no assistente.


- **Alterações ao suporte para a aplicação Portal da Empresa para iOS**. Nos próximos meses, existirá uma atualização para a aplicação Portal da Empresa do Microsoft Intune para iOS que só irá suportar dispositivos que executam o iOS 8.0 ou posterior. Os utilizadores não poderão inscrever novos dispositivos que executam versões anteriores à iOS 8.0. Os dispositivos inscritos que executem versões anteriores à iOS 8.0 continuarão a ser geridos e, durante um período de tempo limitado, poderão continuar a utilizar a aplicação Portal da Empresa. No entanto, os dispositivos devem ter instalado o iOS 8.0 ou posterior para aceder às versões mais recentes da aplicação Portal da Empresa. Aconselhamo-lo a notificar os utilizadores para atualizarem para o iOS 8.0 ou posterior, de modo a tirarem o máximo partido das novas funcionalidades do Intune.



## Versões anteriores do Intune
Se pretender ver o que foi disponibilizado no Intune durante os últimos seis meses, pode encontrar esta informação no artigo [Versões anteriores do Intune](previous-intune-releases.md).
> [!div class="op_single_selector"]
- [Abril de 2016](previous-intune-releases.md)
- [Março de 2016](previous-intune-releases.md)
- [Fevereiro de 2016](previous-intune-releases.md)
- [Janeiro de 2016](previous-intune-releases.md)
- [Dezembro de 2015](previous-intune-releases.md)
- [Novembro de 2015](previous-intune-releases.md)




### Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Plano Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)


<!--HONumber=Jun16_HO1-->


