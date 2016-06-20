---
# required metadata

experiment_id: lindavr-abtest-20160527
experimental: true
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


## Junho de 2016

### Atualizações ao portal da empresa

#### Aplicação Portal da Empresa para iOS

- Quando os utilizadores finais estiverem a instalar aplicações de linha de negócio, irão ver agora uma experiência de instalação de aplicações melhorada. Se a instalação da aplicação estiver a demorar muito tempo, os utilizadores podem sincronizar manualmente os respetivos dispositivos para forçar a continuação do processo de sincronização. Para ver as instruções para utilizadores finais, veja [Sync your iOS device manually (Sincronizar o dispositivo iOS manualmente)](/Intune/EndUser/sync-your-device-manually-ios.md).

- A aplicação do Portal da Empresa do Microsoft Intune para iOS foi atualizada para suportar a versão 8.0 do iOS e posteriores. Esta atualização significa que os utilizadores finais só podem instalar a aplicação do Portal da Empresa e inscrever dispositivos novos no Intune se estes executarem a versão 8.0 do iOS ou posterior. Os utilizadores que já inscreveram dispositivos que executem uma versão não suportada do iOS podem continuar a utilizar a aplicação Portal da Empresa que está nos dispositivos deles.

## Maio de 2016


Todas estas funcionalidades são também suportadas em implementações híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a página [Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-us/library/mt718155.aspx).

### Documentação

Bem-vindo à versão de pré-visualização de [docs.microsoft.com](https://docs.microsoft.com/en-us/intune)!
Esta é uma plataforma de conteúdos completamente nova e moderna, concebida para ser mais fácil para si e para os nossos clientes compreenderem e utilizarem o Intune.
Para ler mais sobre todas as novas funcionalidades, veja [Introducing docs.microsoft.com (Introdução ao docs.microsoft.com)](https://docs.microsoft.com/teamblog/introducing-docs-microsoft-com/)

### Estado de funcionamento do serviço do Intune
As informações de estado de funcionamento do serviço do Intune foram movidas para uma localização central com outros serviços Microsoft. Agora, pode encontrar estas informações no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx), em **Estado de Funcionamento do Serviço**.
Para obter mais informações, veja [esta mensagem do blogue](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).


### Gestão de aplicações

- **MAM SDK: suporta a configuração do comprimento do PIN.** Poderá especificar o comprimento do PIN para aplicações MAM, semelhante a um PIN de dispositivo. Isto irá necessitar que os utilizadores finais respeitem as novas restrições que definiu. Verão um ecrã de PIN ligeiramente modificado para caber a entrada mais longa. Para obter mais detalhes, veja [Definições de política de MAM para Android](/intune/deploy-use/android-mam-policy-settings), e [Definições de política de MAM para iOS](/intune/deploy-use/ios-mam-policy-settings).

- **Skype para Empresas para iOS e Android.** Agora, pode segmentar o Skype para empresas com [MAM sem políticas de inscrição](/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Depois de os utilizadores iniciarem sessão, as políticas de MAM serão aplicadas.

- **Novas aplicações disponíveis para gestão com políticas de MAM.** As aplicações do Microsoft Word, Excel e PowerPoint para Android podem agora ser associadas a políticas de MAM em dispositivos que não estão inscritos no Intune. Para ver uma lista completa de aplicações suportadas, aceda à Galeria de aplicações móveis do Microsoft Intune, na página de [parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


### Atualizações ao Portal da Empresa

#### Aplicação do Portal da Empresa para Android

- **Notificações de alerta do utilizador final**: os utilizadores finais irão agora ver notificações de alerta da aplicação do Portal da Empresa para Android quando estiverem a inscrever ou a remover os respetivos dispositivos do Portal da Empresa.

- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para Android.** Para melhorar o desempenho e o dimensionamento, o Intune já não mostra todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel Os Meus Dispositivos da aplicação do Portal da Empresa para Android. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune.

#### Web site do Portal da Empresa

- **Web site do Portal da Empresa: a faixa de identificação do dispositivo vai dar mais informações aos utilizadores finais.** Agora, os utilizadores finais podem identificar facilmente o dispositivo que selecionaram quando estão a utilizar o Web site do Portal da Empresa. Se for selecionado o dispositivo incorreto, poderão selecionar o dispositivo correto ao tocar na ligação **Tocar aqui** na faixa da página inicial.


## Novidades futuras

- **Inclusão da IU do centro de mensagens**. Como parte da migração do Intune para o [portal de gestão do Office 365](https://portal.office.com/), vamos começar a tirar partido do respetivo Centro de Mensagens para comunicar novas funcionalidades e outras notificações. Além disso, ao instalar a aplicação móvel Office 365 Admin complemento, pode receber notificações no seu telemóvel e reencaminhar facilmente mensagens para utilizadores ou para um alias de distribuição.
Vamos começar a utilizar o Centro de Mensagens com a versão de maio para o notificar quando as atualizações estiverem concluídas e incluiremos informações sobre funcionalidades novas e melhoradas do Intune. Inicie sessão no [portal de gestão do Office 365](https://portal.office.com/) e selecione a opção CENTRO DE MENSAGENS no painel de navegação esquerdo para espreitar ainda hoje o Centro de Mensagens.

- **Alterações às contas de Gestores de Inscrição de Dispositivos**. Para melhorar o desempenho e o dimensionamento, o Intune já não mostra **todos** os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel **Os Meus Dispositivos** da aplicação do Portal da Empresa para iOS. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune. Além disso, o Intune está a descontinuar a utilização de contas DEM com o Programa de registo de dispositivos da Apple ou com a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados. Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível.

### Roteiro da nuvem
Mantenha-se informado sobre os desenvolvimentos futuros do Intune com o [roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Depreciação de serviço
- **Aplicações do Visualizador do Intune.** Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
    - Visualizador AV do Intune
    - Visualizador de PDFs do Intune
    - Visualizador de Imagens do Intune para Android a partir do Google Play

  Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova aplicação Rights Management (partilha RMS) para Android, o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android. Saiba mais sobre a aplicação de partilha RMS (com ligação à documentação).

- **Remoção da Filtragem Personalizada de Grupo de Regras de Notificação.**
As regras de notificações do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificações para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune que criou. A partir de 1 de junho de 2016 em diante, a segmentação de grupos criados pelo utilizador deixará de ser suportada.

    Atualmente, para filtrar uma regra de notificação para um grupo que criou a partir da consola de administração do Microsoft Intune, terá de efetuar os seguintes passos:

    Na área de trabalho **Administração**, clique em **Regras de Notificações** > **Criar Nova Regra**

    No passo dois do Assistente para Criar Regra de Notificação, selecione os grupos de dispositivos que a regra irá visar. Este passo, “selecionar grupos de dispositivos”, vai ser removido da Consola do Intune.

    O calendário preliminar para esta alteração é o seguinte:
    - Em junho de 2016, os novos inquilinos deixarão de ver o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não serão afetados.
    - Por volta de agosto de 2016, alguns inquilinos existentes não verão “selecionar grupos de dispositivos” no assistente.
    - Por volta de outubro de 2016, esperamos que nenhum inquilino veja “selecionar grupos de dispositivos” no assistente.


- **Alterações ao suporte para a aplicação do Portal da Empresa para iOS**. Nos próximos meses, existirá uma atualização para a aplicação do Portal da Empresa do Microsoft Intune para iOS que só irá suportar dispositivos que executem o iOS 8.0 ou posterior. Os utilizadores não poderão inscrever novos dispositivos que executem versões anteriores ao iOS 8.0. Os dispositivos inscritos que executem versões anteriores ao iOS 8.0 continuarão a ser geridos e, durante um período de tempo limitado, será possível continuar a utilizar a aplicação do Portal da Empresa. No entanto, os dispositivos devem ter o iOS 8.0 ou posterior para aceder às versões mais recentes da aplicação do Portal da Empresa. Aconselhamo-lo a notificar os utilizadores para atualizarem para o iOS 8.0 ou posterior, de modo a tirarem o máximo partido das novas funcionalidades do Intune.  



## Versões anteriores do Intune
Se pretender ver o que foi disponibilizado no Intune durante os últimos seis meses, pode encontrar esta informação no artigo [Versões anteriores do Intune](previous-intune-releases.md).



### Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)


<!--HONumber=Jun16_HO2-->


