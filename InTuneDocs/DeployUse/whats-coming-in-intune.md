---
# required metadata

title: Novidades futuras | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/17/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Novidades futuras no Microsoft Intune
Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Esteja atento a novas atualizações de Novidades futuras.

As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas em implementações de clientes híbridas (Configuration Manager com o Intune). Para mais informações sobre as novas funcionalidades híbridas, consulte a nossa [página de Novidades híbridas](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Comunicações do Intune
- **Informações do estado de funcionamento do serviço Intune.** do Intune foram movidas para uma localização central com outros serviços Microsoft. Irá agora encontrar estas informações no [portal de gestão do Office 365](https://portal.office.com/Admin/Default.aspx) em Estado de Funcionamento do Serviço. Para mais informações, consulte [esta mensagem no blogue](https://blogs.technet.microsoft.com/microsoftintune/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

- **Inclusão da IU do Centro de Mensagens.** Como parte da migração do Intune para o [portal de gestão do Office 365](https://portal.office.com/), vamos começar a tirar partido do respetivo Centro de Mensagens para comunicar novas funcionalidades e outras notificações. Além disso, ao instalar a aplicação móvel Office 365 Admin complemento, pode receber notificações no seu telemóvel e reencaminhar facilmente mensagens para utilizadores ou para um alias de distribuição.
Vamos começar a utilizar o Centro de Mensagens com a versão de maio para o notificar quando as atualizações estiverem concluídas e incluiremos informações sobre funcionalidades novas e melhoradas do Intune. Consulte o Centro de Mensagens ainda hoje, iniciando sessão no [portal de gestão do Office 365](https://portal.office.com/) e selecionando a opção **Centro de Mensagens** no painel de navegação esquerdo.

## Gestão de aplicações
- **Novas aplicações disponíveis para a gestão com as políticas de MAM.** As aplicações do Microsoft Word, Excel e PowerPoint para Android podem agora ser associadas a políticas de MAM em dispositivos que não estão inscritos no Intune. Para uma lista completa de aplicações suportadas, aceda à galeria de aplicações móveis do Microsoft Intune na [página de parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx).


- **Acesso condicional para browser.** Poderá definir uma política de acesso condicional para o Exchange Online e o SharePoint Online, para que apenas dispositivos iOS e Android geridos e conformes possam aceder aos mesmos. Aos utilizadores finais que tentarem iniciar sessão no Outlook Web Access (OWA) e em sites do SharePoint com dispositivos iOS e Android será pedido que inscrevam o respetivo dispositivo no Intune, bem como que corrijam quaisquer problemas de não conformidade, para poderem concluir o início de sessão.
<!---TFS 1175844--->

- **MAM SDK: suporta a configuração do comprimento do PIN.** Poderá especificar o comprimento do PIN para aplicações MAM, semelhante a um PIN de dispositivo. Isto irá necessitar que os utilizadores finais respeitem as novas restrições que definiu. Verão um ecrã de PIN ligeiramente modificado para caber a entrada mais longa.
<!--- TFS 1104753--->

- **Skype para Empresas, para Android.** Os administradores do Intune podem agora visar o Skype para Empresas com MAM sem políticas de inscrição.  Depois de os utilizadores iniciarem sessão, as políticas MAM serão aplicadas.
<!--- TFS item 1248444 --->

- **Skype para Empresas, para iOS.** Os administradores do Intune podem agora visar o Skype para Empresas com MAM sem políticas de inscrição.  Depois de os utilizadores iniciarem sessão, as políticas MAM serão aplicadas.
<!--- TFS item 1248443 --->

### Suporte de Xamarin
O SDK da aplicação Microsoft Intune suporta agora aplicações Xamarin nos seguintes cenários:

- Escrever novas aplicações ou modificar o código de aplicações de linha de negócio existentes com o Intune SDK. Pode obter o plug-in na página [Microsoft Intune Github](https://github.com/msintuneappsdk).
- Adicionar suporte de MAM a aplicações de linha de negócio existentes com a ferramenta de encapsulamento de aplicações do Intune

Para obter ajuda para escolher que método utilizar, consulte [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->


## Gestão de dispositivos
- **Sessões de assistência remota para PCs Windows.** A integração do TeamViewer para PCs geridos por agente de ambiente de trabalho Windows permitirá estabelecer sessões de assistência remota com computadores geridos por agente de ambiente de trabalho Windows em departamentos de suporte técnico do utilizador final. Isto inclui o Windows 7, 8, 8.1 e o Windows 10.
<!--- TFS 1284856--->



## Portal da Empresa

- **Notificações de alerta do utilizador final.** Os utilizadores finais irão agora ver notificações de alerta da aplicação Portal da Empresa para Android ao inscreverem os respetivos dispositivos ou ao removerem-nos do Portal da Empresa.
- **A faixa de identificação do dispositivo irá fornecer mais informações aos utilizadores finais.** Os utilizadores finais serão capazes de identificar facilmente o dispositivo que selecionaram quando estão a utilizar o site do Portal da Empresa. Se for selecionado o dispositivo incorreto, poderão selecionar o dispositivo correto ao tocar na ligação "Tocar aqui" na faixa da página inicial.
<!--- TFS 1231157--->

- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação Portal da Empresa para Android.** Para melhorar o desempenho e o dimensionamento, o Intune irá deixar de mostrar todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel **Os Meus Dispositivos** da aplicação Portal da Empresa para Android. Apenas será apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só poderá ser efetuada a partir da consola de administração do Intune.

- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para iOS.** Para melhorar o desempenho e o dimensionamento, o Intune já não mostra todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel Os Meus Dispositivos da aplicação Portal da Empresa para iOS. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune.  Além disso, o Intune pretere a utilização de contas DEM com o Programa de Inscrição de Dispositivos Apple ou a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados.  Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível.



## Depreciação de serviço
**Remoção da Filtragem Personalizada de Grupo de Regras de Notificação.**
As regras de notificação do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificação para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune criado por si. A partir de 1 de junho de 2016, a filtragem de grupos criados pelo utilizador já não será suportada.

Atualmente, para filtrar uma regra de notificação para um grupo que criou a partir da consola de administração do Microsoft Intune, terá de efetuar os seguintes passos:

Na área de trabalho **Admin**, clique em **Regras de Notificação** > **Criar Nova Regra**

No passo dois do Assistente para Criar Regra de Notificação, selecione os grupos de dispositivos que a regra irá filtrar. Este passo, “selecionar grupos de dispositivos”, está a ser removido da Consola do Intune.

A linha cronológica preliminar para esta alteração é a seguinte:
- Em junho de 2016, os novos inquilinos não verão o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não serão afetados.
- Por volta de agosto de 2016, alguns inquilinos existentes não verão “selecionar grupos de dispositivos” no assistente.
- Por volta de outubro de 2016, esperamos que nenhum inquilino veja “selecionar grupos de dispositivos” no assistente.

<!---   TFS 1278864--->
**Alterações ao suporte para a aplicação Portal da Empresa para iOS.**
Nos próximos meses, existirá uma atualização para a aplicação Portal da Empresa do Microsoft Intune para iOS que só irá suportar dispositivos que executam o iOS 8.0 ou posterior. Os utilizadores não poderão inscrever novos dispositivos que executam versões anteriores à iOS 8.0. Os dispositivos inscritos que executem versões anteriores à iOS 8.0 continuarão a ser geridos e, durante um período de tempo limitado, poderão continuar a utilizar a aplicação Portal da Empresa. No entanto, os dispositivos devem ter instalado o iOS 8.0 ou posterior para aceder às versões mais recentes da aplicação Portal da Empresa. Aconselhamo-lo a notificar os utilizadores para atualizarem para o iOS 8.0 ou posterior, de modo a tirarem o máximo partido das novas funcionalidades do Intune.  

- **Aplicações do Visualizador do Intune.** Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
    - Visualizador de AV do Intune
    - Visualizador de PDFs do Intune
    - Visualizador de Imagens do Intune para Android a partir do Google Play

  Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova aplicação de Rights Management (partilha RMS) para Android, que permite implementar uma aplicação em vez de três aplicações separadas para ver, com segurança, ficheiros empresariais em dispositivos Android. Saiba mais sobre a aplicação de partilha RMS (com ligação para a documentação).






### Consulte também
Consulte [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.


<!--HONumber=May16_HO5-->


