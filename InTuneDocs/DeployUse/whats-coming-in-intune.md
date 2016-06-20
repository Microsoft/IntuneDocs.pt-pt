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

As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas em implementações de clientes híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Gestão de aplicações
- **Alterações à política de dados do Windows 10 enterprise.** Devido a melhoramentos na política de aplicações da política de dados do Windows 10 enterprise, se guardar uma política que tenha sido configurada com regras de aplicações (anteriormente chamadas “aplicações protegidas”), as regras existentes que possa ter configurado perder-se-ão. Para continuar, terá de reconfigurar estas regras de aplicação.

- **Acesso condicional para browser.** Poderá definir uma política de acesso condicional para o Exchange Online e o SharePoint Online, para que apenas dispositivos iOS e Android geridos e conformes possam aceder aos mesmos. Aos utilizadores finais que tentarem iniciar sessão no Outlook Web Access (OWA) e em sites do SharePoint com dispositivos iOS e Android será pedido que inscrevam o respetivo dispositivo no Intune, bem como que corrijam quaisquer problemas de não conformidade, para poderem concluir o início de sessão.
<!---TFS 1175844--->

- **O Dynamics CRM Online suporta o acesso condicional.** Os clientes poderão definir uma política de acesso condicional para o Dynamics CRM Online, para que apenas dispositivos iOS e Android geridos e conformes possam aceder ao mesmo. Aos utilizadores finais que tentarem iniciar sessão na aplicação móvel Dynamics CRM Online em dispositivos iOS e Android será pedido que se inscrevam primeiro no Intune e que corrijam quaisquer problemas de não conformidade para que o início de sessão possa ser concluído.
<!---TFS1295358--->

### Suporte de Xamarin
O SDK da aplicação Microsoft Intune suporta agora aplicações Xamarin nos seguintes cenários:

- Escrever novas aplicações ou modificar o código de aplicações de linha de negócio existentes com o Intune SDK. Pode obter o plug-in na página [Microsoft Intune Github](https://github.com/msintuneappsdk).
- Adicionar suporte de MAM a aplicações de linha de negócio existentes com a ferramenta de encapsulamento de aplicações do Intune

Para obter ajuda para escolher que método utilizar, veja [Decide how to prepare apps for mobile application management with Microsoft Intune (Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune)](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->


## Portal da Empresa
**Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para iOS.** Para melhorar o desempenho e o dimensionamento, o Intune já não mostra todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel Os Meus Dispositivos da aplicação do Portal da Empresa para iOS. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune.  Além disso, o Intune está a descontinuar a utilização de contas DEM com o Programa de registo de dispositivos da Apple ou com a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados.  Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível.
<!---TFS 1233681--->

## Depreciação de serviço
**As aplicações do Portal da Empresa para Windows 8 e Windows Phone 8 vão ser preteridas a partir de setembro de 2016.** A partir de setembro de 2016, o Microsoft Intune vai terminar o suporte para as aplicações do Portal da Empresa do Microsoft Intune nas plataformas Windows Phone 8 e Windows 8. Para continuar a distribuir aplicações para estes dispositivos, atualize-os para o Windows 8.1 e o Windows Phone 8.1 e utilize as aplicações do Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 correspondentes.
<!---TFS 1255391--->

**Remoção da Filtragem Personalizada de Grupo de Regras de Notificação.**
As regras de notificações do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificações para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune que criou. A partir de 1 de junho de 2016 em diante, a segmentação de grupos criados pelo utilizador deixará de ser suportada.

O calendário preliminar para esta alteração é o seguinte:
- Em junho de 2016, os novos inquilinos deixarão de ver o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não serão afetados.
- Por volta de agosto de 2016, alguns inquilinos existentes não verão “selecionar grupos de dispositivos” no assistente.
- Por volta de outubro de 2016, esperamos que nenhum inquilino veja “selecionar grupos de dispositivos” no assistente.

<!---   TFS 1278864--->
**Alterações ao suporte para a aplicação do Portal da Empresa para iOS.**
Os utilizadores têm de atualizar para a mais recente aplicação do Portal da Empresa para iOS. Nos próximos meses, todos os utilizadores da aplicação do Portal da mpresa do Microsoft Intune para iOS terão de utilizar a última versão. Os novos utilizadores só conseguirão transferir a versão mais recente e os utilizadores atuais terão de atualizar para a mesma. A versão mais recente requer o iOS 8.0 ou posterior, pelo que os utilizadores com dispositivos com versões do iOS mais antigas não poderão utilizar o Portal da Empresa nem inscrever enquanto não os atualizarem para o iOS 8.0 ou posterior e atualizarem a aplicação do Portal da Empresa para a última versão. Os dispositivos inscritos que tenham versões anteriores ao iOS 8.0 continuarão a ser geridos e listados na Consola de Administração do Intune.  

**Aplicações do Visualizador do Intune.** Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
- Visualizador AV do Intune
- Visualizador de PDFs do Intune
- Visualizador de Imagens do Intune para Android a partir do Google Play

Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova aplicação Rights Management (partilha RMS) para Android, o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android. Saiba mais sobre a aplicação de partilha RMS (com ligação à documentação).


### Consulte também
Consulte [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.


<!--HONumber=Jun16_HO2-->


