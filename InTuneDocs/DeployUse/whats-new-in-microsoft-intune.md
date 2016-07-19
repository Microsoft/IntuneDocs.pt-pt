---
title: Novidades | Microsoft Intune
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 06/16/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79617dd41e51402a73759da792f581028095a2f5
ms.openlocfilehash: 65e53ad6a74fbf0e9249c367f517ab52ea0efa80


---

# Novidades do Microsoft Intune
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

Seguem-se as novidades nesta versão. Exceto a atualização de definição da política do Windows Defender, todas estas funcionalidades são também suportadas para implementações de clientes híbridos (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Junho de 2016
### Estado de funcionamento do serviço do Intune
As informações de estado de funcionamento do serviço do Intune foram movidas para uma localização central com outros serviços Microsoft. Agora, pode encontrar estas informações no portal de gestão do Office 365, em Estado de Funcionamento do Serviço. Para obter mais informações, veja [esta mensagem do blogue](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

## Gestão de aplicações
- **Experiência de configuração de política de dados do Windows 10 enterprise melhorada.** Efetuamos melhoramentos para a experiência de configuração da política de proteção de dados empresariais do Windows 10 sobre a criação de regras de aplicação, como especificar a definição de limites de rede e outras definições de proteção de dados empresariais. Para saber mais, veja o artigo [Criar uma política de proteção de dados empresariais (EDP) através do Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune).


## Gestão de dispositivos
- **Definição de política do Windows Defender contra aplicações potencialmente indesejáveis.** Uma nova definição do Windows Defender com o nome **Deteção de Aplicação Potencialmente Indesejável** foi adicionado à política de configuração geral para computadores de secretária com o Windows 10 e para o telemóvel. Pode utilizar esta definição para proteger computadores de secretária Windows inscritos contra software em execução classificado pelo Windows Defender como potencialmente indesejado. Pode proteger contra estas aplicações em execução ou utilizar o modo de auditoria para relatar quando uma aplicação potencialmente indesejável é instalada. Para obter mais informações, veja [Definições de política do Windows 10 no Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/windows-10-policy-settings-in-microsoft-intune).
<!---TFS 1244478--->

## Acesso condicional
- **Política de controlo de acesso da rede Cisco ISE para o Intune.**  Os clientes que utilizam o Motor de Serviço de Identidade Cisco (ISE) 2.1 e que também utilizam o Microsoft Intune podem definir uma política de controlo de acesso de rede no ISE.

    Ao utilizar esta política, os dispositivos que precisa de ligar à rede através de Wi-Fi ou VPN devem cumprir seguintes condições antes de lhes ser concedido acesso:

    * Deve ser gerido pelo Intune
    * Deve ser compatível com todas políticas de conformidade do Intune implementadas

 Os utilizadores finais de dispositivos não conformes serão solicitados para inscrever-se e para retificar quaisquer problemas de compatibilidade para obter acesso.
- **Acesso condicional para browser.** Pode definir uma política de acesso condicional para o [Exchange Online](restrict-access-to-exchange-online-with-microsoft-intune.md) e o [SharePoint Online](restrict-access-to-sharepoint-online-with-microsoft-intune.md) para que apenas os dispositivos iOS e Android geridos e compatíveis possam ser acedidos a partir de Web browsers suportados. Aos utilizadores finais que tentarem iniciar sessão no Outlook Web Access (OWA) e em sites do SharePoint com dispositivos iOS e Android será pedido que inscrevam o respetivo dispositivo no Intune, bem como que corrijam quaisquer problemas de não conformidade, para poderem concluir o início de sessão.
<!---TFS 1175844--->

- **O Dynamics CRM Online suporta o acesso condicional.** Pode definir uma política de acesso condicional para o [Dynamics CRM Online](restrict-access-to-dynamics-crm-online-with-microsoft-intune.md) para que apenas dispositivos iOS e Android geridos e compatíveis possam aceder ao mesmo. Aos utilizadores finais que tentarem iniciar sessão na aplicação móvel Dynamics CRM Online em dispositivos iOS e Android será pedido que se inscrevam primeiro no Intune e que corrijam quaisquer problemas de não conformidade para que o início de sessão possa ser concluído.
<!---TFS1295358--->

## Atualizações ao Portal da Empresa

### Aplicação do Portal da Empresa para Android

- Quando os administradores de TI aplicam a nova política "Exigir que os dispositivos não permitam a instalação de aplicações a partir de origens desconhecidas (Android 4.0 +)", os utilizadores finais com Android 4.0 ou dispositivos posteriores irão ver a mensagem "A instalação tem de ser desativada a partir de origens desconhecidas." Os utilizadores terão de ir para **Definições** > **Segurança**, e desativar **Origens desconhecidas**. Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/Intune/EndUser/you-are-asked-to-turn-off-unknown-sources-android) sobre a mensagem e por que motivo é necessário desativar a definição.

- Quando os administradores de TI aplicam a nova política "Exigir que os dispositivos ativem a análise de ameaças de segurança em aplicações (Android 4.0 +)", os utilizadores finais com Android 4.0 ou dispositivos posteriores irão ver a mensagem "Analisar se o dispositivo apresenta ameaças de segurança." Os utilizadores terão de ir para **Definições** > **Google** > **Segurança** e ativar **Analisar se o dispositivo apresenta ameaças de segurança**. Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre a mensagem e por que motivo é necessário ativar a definição.

- Quando os administradores de TI aplicam a nova política "Exigir a desativação da depuração de USB (Android 4.2 +)", os utilizadores finais com Android 4.2 ou dispositivos posteriores irão ver a mensagem "A depuração de USB deve ser desativada." Os utilizadores terão de ir para **Definições** > **Opções de programador** e desativar **Depuração de USB**." Uma ligação na mensagem de compatibilidade permite aos utilizadores obterem mais [informações](/Intune/EndUser/you-are-asked-to-turn-off-usb-debugging-android) sobre a mensagem e por que motivo é necessário desativar a definição.

- Quando os administradores de TI aplicam a nova política "Nível mínimo de patch de segurança do Android (Android 6.0 +)", os utilizadores finais com Android 6.0 ou dispositivos posteriores irão ver a mensagem "Este dispositivo não cumpre o nível mínimo de patch de segurança do Android." Os utilizadores têm de instalar o patch de segurança necessário. Uma ligação na mensagem de compatibilidade permite aos utilizadores obter [informações](/Intune/EndUser/you-are-asked-to-turn-on-scan-device-for-security-threats-android) sobre como instalar o patch de segurança necessário e ver que patch de segurança está atualmente instalado.

### Aplicação Portal da Empresa para iOS

- Quando os utilizadores finais estiverem a instalar aplicações de linha de negócio, irão ver agora uma experiência de instalação de aplicações melhorada. Se a instalação da aplicação estiver a demorar muito tempo, os utilizadores podem sincronizar manualmente os respetivos dispositivos para forçar a continuação do processo de sincronização. Para ver as instruções para utilizadores finais, veja [Sincronizar o dispositivo iOS manualmente](/Intune/EndUser/sync-your-device-manually-ios).

- A aplicação do Portal da Empresa do Microsoft Intune para iOS foi atualizada para suportar a versão 8.0 do iOS e posteriores. Esta atualização significa que os utilizadores finais só podem instalar a aplicação do Portal da Empresa e inscrever dispositivos novos no Intune se estes executarem a versão 8.0 do iOS ou posterior. Os utilizadores que já inscreveram dispositivos que executem uma versão não suportada do iOS podem continuar a utilizar a aplicação Portal da Empresa que está nos dispositivos deles.


## Novidades futuras

### Roteiro da nuvem
Mantenha-se informado sobre os desenvolvimentos futuros do Intune com o [roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Depreciação de serviço
- **Aplicações do Visualizador do Intune.** Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
    - Visualizador AV do Intune
    - Visualizador de PDFs do Intune
    - Visualizador de Imagens do Intune para Android a partir do Google Play

  Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova aplicação Rights Management (partilha RMS) para Android, o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android.

- **Remoção da Filtragem Personalizada de Grupo de Regras de Notificação.**
As regras de notificações do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificação para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune criado por si. A partir de 1 de junho de 2016, a filtragem de grupos criados pelo utilizador já não será suportada.

    Atualmente, para filtrar uma regra de notificação para um grupo que criou a partir da consola de administração do Microsoft Intune, terá de efetuar os seguintes passos:

    Na área de trabalho **Administração**, clique em **Regras de Notificações** > **Criar Nova Regra**

    No passo dois do Assistente para Criar Regra de Notificação, selecione os grupos de dispositivos que a regra irá visar. Este passo, “selecionar grupos de dispositivos”, vai ser removido da Consola do Intune.

    O calendário preliminar para esta alteração é o seguinte:
    - Em agosto de 2016, os novos inquilinos deixarão de ver o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não serão afetados.
    - Por volta de setembro de 2016, alguns inquilinos existentes não verão “selecionar grupos de dispositivos” no assistente.
    - Por volta de novembro de 2016, esperamos que nenhum inquilino veja “selecionar grupos de dispositivos” no assistente.


- **Alterações ao suporte para a aplicação do Portal da Empresa para iOS**. Em julho, todos os utilizadores da aplicação do Portal da Empresa do Microsoft Intune para iOS terão de utilizar a última versão. Os novos utilizadores só conseguirão transferir a versão mais recente e os utilizadores atuais terão de atualizar para a mesma. A versão mais recente requer o iOS 8.0 ou posterior, pelo que os utilizadores com dispositivos com versões do iOS mais antigas não poderão utilizar o Portal da Empresa nem inscrever enquanto não os atualizarem para o iOS 8.0 ou posterior e atualizarem a aplicação do Portal da Empresa para a última versão. Os dispositivos inscritos que tenham versões anteriores ao iOS 8.0 continuarão a ser geridos e listados na Consola de Administração do Intune.





## Versões anteriores do Intune
Se pretender ver o que foi disponibilizado no Intune durante os últimos seis meses, pode encontrar esta informação no artigo [Versões anteriores do Intune](previous-intune-releases.md).



### Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Jul16_HO1-->


