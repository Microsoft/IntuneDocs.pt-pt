---
# required metadata

title: Novidades futuras | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 06/10/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: mamoriss
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Novidades futuras no Microsoft Intune
Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Esteja atento a novas atualizações de Novidades futuras.

As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas em implementações de clientes híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Gestão de aplicações
- **Experiência de configuração de política de dados do Windows 10 enterprise melhorada.** Efetuamos melhorias para à experiência de configuração de política de proteção de dados do Windows 10 enterprise à volta de criação de regras de aplicação, especificando da definição de limites de rede, entre outras definições de proteção de dados da empresa.
<!---TFS 1303011--->

- **Acesso condicional para browser.** Poderá definir uma política de acesso condicional para o Exchange Online e o SharePoint Online, para que apenas dispositivos iOS e Android geridos e conformes possam aceder aos mesmos. Aos utilizadores finais que tentarem iniciar sessão no Outlook Web Access (OWA) e em sites do SharePoint com dispositivos iOS e Android será pedido que inscrevam o respetivo dispositivo no Intune, bem como que corrijam quaisquer problemas de não conformidade, para poderem concluir o início de sessão.
<!---TFS 1175844--->

- **O Dynamics CRM Online suporta o acesso condicional.** Os clientes poderão definir uma política de acesso condicional para o Dynamics CRM Online, para que apenas dispositivos iOS e Android geridos e conformes possam aceder ao mesmo. Aos utilizadores finais que tentarem iniciar sessão na aplicação móvel Dynamics CRM Online em dispositivos iOS e Android será pedido que se inscrevam primeiro no Intune e que corrijam quaisquer problemas de não conformidade para que o início de sessão possa ser concluído.
<!---TFS1295358--->

### Suporte de Xamarin
O SDK da aplicação Microsoft Intune suportará aplicações Xamarin nos seguintes cenários:

- Escrever novas aplicações ou modificar o código de aplicações de linha de negócio existentes com o Intune SDK. Poderá obter o plug-in na página [Microsoft Intune Github](https://github.com/msintuneappsdk).
- Adicionar suporte de MAM a aplicações de linha de negócio existentes com a ferramenta de encapsulamento de aplicações do Intune

Para obter ajuda para escolher que método utilizar, consulte [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).
<!--- TFS 1061478 & TFS 1152340--->

## Gestão de dispositivos
- **Definição de política do Windows Defender contra aplicações potencialmente indesejáveis.** Uma nova definição do Windows Defender com o nome **Deteção de Aplicação Potencialmente Indesejável** foi adicionado à política de configuração geral para computadores de secretária com o Windows 10 e para o telemóvel. Pode utilizar esta definição para proteger computadores de secretária Windows inscritos contra software em execução classificado pelo Windows Defender como potencialmente indesejado. Pode proteger contra estas aplicações em execução ou utilizar o modo de auditoria para relatar quando uma aplicação potencialmente indesejável é instalada.
<!---TFS 1244478--->

## Acesso condicional
**Política de controlo de acesso da rede Cisco ISE para o Intune.**  Os clientes que utilizam o Motor de Serviço de Identidade Cisco (ISE) 2.1 e que também utilizam o Microsoft Intune podem definir uma política de controlo de acesso de rede no ISE.

Ao utilizar esta política, os dispositivos que precisa de ligar à rede através de Wi-Fi ou VPN devem cumprir seguintes condições antes de lhes ser concedido acesso:

* Deve ser gerido pelo Intune
* Deve ser compatível com todas políticas de conformidade do Intune implementadas

Os utilizadores finais de dispositivos não conformes serão solicitados para inscrever-se e para retificar quaisquer problemas de compatibilidade para obter acesso.
<!---TFS 1299144--->

## Portal da Empresa
**Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para iOS.** Para melhorar o desempenho e o dimensionamento, o Intune irá deixar de mostrar todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel Os Meus Dispositivos da aplicação do Portal da Empresa iOS. Apenas será apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só poderá ser efetuada a partir da consola de administração do Intune.  Além disso, o Intune está a descontinuar a utilização de contas DEM com o Programa de registo de dispositivos da Apple ou com a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados. Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível.
<!---TFS 1233681--->

## Depreciação de serviço
**As aplicações do Portal da Empresa para Windows 8 e Windows Phone 8 vão ser preteridas a partir de setembro de 2016.** A partir de setembro de 2016, o Microsoft Intune vai terminar o suporte para as aplicações do Portal da Empresa do Microsoft Intune nas plataformas Windows Phone 8 e Windows 8. Para continuar a distribuir aplicações para estes dispositivos, atualize-os para o Windows 8.1 e o Windows Phone 8.1 e utilize as aplicações do Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 correspondentes.
<!---TFS 1255391--->

**Remoção da Filtragem Personalizada de Grupo de Regras de Notificação.**
As regras de notificações do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificação para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune criado por si. A partir de 1 de junho de 2016 em diante, a segmentação de grupos criados pelo utilizador deixará de ser suportada.

O calendário preliminar para esta alteração é o seguinte:
- Em agosto de 2016, os novos inquilinos deixarão de ver o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não serão afetados.
- Por volta de setembro de 2016, alguns inquilinos existentes não verão “selecionar grupos de dispositivos” no assistente.
- Por volta de novembro de 2016, esperamos que nenhum inquilino veja “selecionar grupos de dispositivos” no assistente.
<!---   TFS 1278864--->

**Alterações ao suporte para a aplicação do Portal da Empresa para iOS.**
Em julho, todos os utilizadores da aplicação do Portal da Empresa do Microsoft Intune para iOS terão de utilizar a última versão. Os novos utilizadores só conseguirão transferir a versão mais recente e os utilizadores atuais terão de atualizar para a mesma. A versão mais recente requer o iOS 8.0 ou posterior, pelo que os utilizadores com dispositivos com versões do iOS mais antigas não poderão utilizar o Portal da Empresa nem inscrever enquanto não os atualizarem para o iOS 8.0 ou posterior e atualizarem a aplicação do Portal da Empresa para a última versão. Os dispositivos inscritos que tenham versões anteriores ao iOS 8.0 continuarão a ser geridos e listados na Consola de Administração do Intune.  

**Aplicações do Visualizador do Intune.** Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
- Visualizador AV do Intune
- Visualizador de PDFs do Intune
- Visualizador de Imagens do Intune para Android a partir do Google Play

Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova aplicação Rights Management (partilha RMS) para Android, o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android. Saiba mais sobre a aplicação de partilha RMS (com ligação para a documentação).


### Consulte também
Consulte [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.


<!--HONumber=Jun16_HO3-->


