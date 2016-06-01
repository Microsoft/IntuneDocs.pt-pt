---
# required metadata

title: Novidades futuras | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 05/03/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

#ROBOTS:
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

As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas em implementações de clientes híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, consulte a nossa [página de Novidades híbridas](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Inclusão do Centro de Mensagens
Como parte da migração do Intune para o [portal de gestão do Office 365](https://portal.office.com/), vamos começar a tirar partido do respetivo Centro de Mensagens para comunicar novas funcionalidades e outras notificações.  Além disso, ao instalar a aplicação móvel Office 365 Admin complemento, pode receber notificações no seu telemóvel e reencaminhar facilmente mensagens para utilizadores ou para um alias de distribuição.<br>  
Vamos começar a utilizar o Centro de Mensagens com a versão de maio para o notificar quando as atualizações estiverem concluídas e incluiremos informações sobre funcionalidades novas e melhoradas do Intune.  Consulte o Centro de Mensagens ainda hoje, iniciando sessão no [portal de gestão do Office 365](https://portal.office.com/) e selecionando a opção **CENTRO DE MENSAGENS** no painel de navegação esquerdo.
<!---TFS 1242782--->


## Gestão de aplicações
- **Acesso condicional para browser.** Poderá definir uma política de acesso condicional para o Exchange Online e o SharePoint Online, para que apenas dispositivos iOS e Android geridos e conformes possam aceder aos mesmos. Aos utilizadores finais que tentarem iniciar sessão no Outlook Web Access (OWA) e em sites do SharePoint com dispositivos iOS e Android será pedido que inscrevam o respetivo dispositivo no Intune, bem como que corrijam quaisquer problemas de não conformidade, para poderem concluir o início de sessão.
<!---TFS 1175844--->

- **MAM SDK: suporta a configuração do comprimento do PIN.** Poderá especificar o comprimento do PIN para aplicações MAM, semelhante a um PIN de dispositivo. Isto irá necessitar que os utilizadores finais respeitem as novas restrições que definiu. Verão um ecrã de PIN ligeiramente modificado para caber a entrada mais longa.
<!--- TFS 1104753--->

- **Controlos de MAM para impedir a sincronização de contactos do Outlook (iOS).** Uma nova definição está disponível para a gestão de aplicações móveis sem inscrição de dispositivos. Esta definição permite que o administrador do Intune impeça que uma aplicação sincronize contactos com o livro de endereços nativo em dispositivos iOS. Quando esta definição estiver ativada, a aplicação já não poderá guardar contactos no livro de endereços nativo. Quando esta definição estiver desativada, a aplicação poderá guardar contactos no livro de endereços nativo. Quando um administrador do Intune apaga seletivamente os dados de um dispositivo, todos os contactos que já tenham sido guardados no livro de endereços nativo serão removidos. Esta nova definição é agora suportada pela aplicação Outlook em dispositivos iOS.
<!---TFS item 1276166--->

- **Skype para Empresas para Android.** Os administradores do Intune podem agora visar o Skype para Empresas com MAM sem políticas de inscrição.  Depois de os utilizadores iniciarem sessão, as políticas MAM serão aplicadas.
<!--- TFS item 1248444 --->

- **Skype para Empresas para iOS.** Os administradores do Intune podem agora visar o Skype para Empresas com MAM sem políticas de inscrição.  Depois de os utilizadores iniciarem sessão, as políticas MAM serão aplicadas.
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


<!--- TFS item 1274326 --->

## Controlo de acesso
* **O Skype para Empresas Online suporta o acesso condicional.** Os administradores do Intune poderão definir uma política de acesso condicional para o Skype para Empresas Online, para que apenas dispositivos iOS e Android geridos e conformes possam aceder ao mesmo. Aos utilizadores finais que tentarem iniciar sessão na aplicação Skype para Empresas para dispositivos móveis em dispositivos iOS e Android será pedido que se inscrevam primeiro no Intune e que corrijam quaisquer problemas de não conformidade para que o início de sessão possa ser concluído.
<!---TFS item 1254499--->

## Portal da Empresa
* **A faixa de identificação do dispositivo irá fornecer mais informações aos utilizadores finais.** Os utilizadores finais serão capazes de identificar facilmente o dispositivo que selecionaram quando estão a utilizar o site do Portal da Empresa. Se for selecionado o dispositivo incorreto, poderão selecionar o dispositivo correto ao tocar na ligação "Tocar aqui" na faixa da página inicial.
<!--- TFS 1231157--->

* **Pacotes de aplicações do Windows disponíveis diretamente a partir do Portal da Empresa**: os utilizadores de PCs Windows 8, Windows 8.1 e Windows RT podem agora instalar pacotes de aplicações do Windows (com a extensão .appx) diretamente a partir do site do Portal da Empresa. Anteriormente, os administradores do Intune tinham de implementar, ou os utilizadores tinham de instalar, a aplicação Portal da Empresa nos respetivos dispositivos para instalar aplicações.
<!--- TFS item 1082481 --->

* **Os utilizadores podem bloquear remotamente o dispositivo a partir do Portal da Empresa** Foi adicionada uma nova opção de bloqueio remoto ao site do Portal da Empresa para permitir que os utilizadores finais bloqueiem remotamente o seu dispositivo a partir do portal, em caso de perda ou roubo do dispositivo. A tabela seguinte lista o suporte de plataforma do bloqueio remoto para o Intune e o Intune com o Configuration Manager.
<!--- TFS item 1195661 --->

|Plataforma  |Detalhes do suporte|
|---------|---------|
|iOS | Suportado|
|Android | Suportado|
|Windows Phone 8.1 | Suportado|
|Windows 10 Mobile | Suportado apenas se o telemóvel tiver um código de acesso definido|
|PC (Windows 8.0 e anterior) | Não suportado|
|PC (Windows 8.1) | Não suportado|
|Windows Phone 8.0 | Não Suportado|
|Windows 10 Desktop | Não suportado|

## Depreciação de serviço
* **Remoção da Filtragem Personalizada de Grupo de Regras de Notificação.** A partir do início de junho de 2016, já não será possível utilizar o Assistente para Criar Regra de Notificação para visar grupos criados pelo utilizador com regras de notificação.

    Atualmente, para visar um grupo criado pelo utilizador a partir da consola de administração do Microsoft Intune, tem de escolher **Admin** > **Regras de Notificação** > **Criar Nova Regra**. No passo dois do Assistente para Criar Regra de Notificação, tem de selecionar os grupos de dispositivos que a regra irá visar. Este passo, **Selecionar grupos de dispositivos**, está a ser preterido na Consola do Intune.

    A opção **Selecionar grupos de dispositivos** deixará de ser suportada após a versão 1606 de junho do Intune. No entanto, irá continuar a ver esta opção até agosto de 2016. Depois de agosto, começaremos a introduzir gradualmente os nossos inquilinos na nova experiência durante um período de dois meses. Até outubro de 2016, todos os clientes existentes devem ser transitados para a nova experiência. Depois de migrar para a nova experiência, deixará de ser apresentada a opção de visar regras de notificação num grupo específico.
<!---   TFS 1278864--->







### Consulte também
Consulte [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.


<!--HONumber=May16_HO1-->


