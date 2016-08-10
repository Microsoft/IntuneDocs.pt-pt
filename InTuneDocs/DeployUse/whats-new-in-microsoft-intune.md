---
title: Novidades | Microsoft Intune
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b93c6fe16e598c6f4b0d87981de8655f3de9c8d3
ms.openlocfilehash: 051f2994c59b2886a81a50d7c72f51627064bc6a


---

# Novidades do Microsoft Intune
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).

## Agosto de 2016
## Atualizações ao Portal da Empresa

### Android
- **Aplicação do Portal da Empresa para Android**<br/>
A aplicação Intune Company Portal para Android fornece suporte no "dia 0" para o lançamento do sistema operativo Android 7.0 para dispositivos móveis.  

- **A remoção da funcionalidade de reposição de códigos de acesso remotos por parte da Google em dispositivos com o Android 7.0**<br/>
Em dispositivos Android 7.0, os administradores de TI do Intune e os utilizadores finais não terão a possibilidade de repor remotamente o código de acesso ao dispositivo, dado que a Google removeu essa funcionalidade para os dispositivos com Android 7.0. Para as versões anteriores ao Android 7.0, os administradores de TI ainda conseguirão repor remotamente o código de acesso de um utilizador, assim como os utilizadores finais conseguirão repor os seus códigos de acesso a partir do website do Portal da Empresa.

## Julho de 2016
## Gestão de aplicações
### Melhorar a experiência de atualização de perfis de aprovisionamento de aplicações
As aplicações de linha de negócio iOS da Apple são criadas com um perfil de aprovisionamento incluído e o respetivo código assinado com um certificado. Quando as aplicações são executadas num dispositivo iOS, o iOS confirma a integridade das mesmas e aplica as políticas definidas pelo perfil de aprovisionamento.

Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Com esta atualização, o Intune proporciona-lhe as ferramentas para implementar proativamente uma nova política de perfil de aprovisionamento em dispositivos que tenham aplicações prestes a expirar enquanto o certificado ainda é válido. Para obter mais informações, veja [Use iOS mobile provisioning profile policies to keep your line of business apps up to date (Utilizar políticas de perfis de aprovisionamento móvel de iOS para manter as aplicações de linha de negócio atualizadas)](/intune/deploy-use/ios-mobile-app-provisioning-profiles).
<!--- TFS 1280247--->
### Está disponível o SDK para Xamarin para aplicações do Intune
O componente Xamarin do SDK da Aplicação Intune permite-lhe ativar as funcionalidades de gestão de aplicações móveis do Intune nas suas aplicações móveis iOS e Android criadas com Xamarin. Pode obter o componente no [arquivo Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) ou na [página do Microsoft Intune no Github](https://github.com/msintuneappsdk).
<!--- TFS 1061478 --->

## Gestão de dispositivos
### Aumento nos limites de inscrição de dispositivos
O Intune aumentou o limite máximo de inscrição de dispositivos configuráveis de cinco para 15 dispositivos por utilizador.
<!---TFS 1289896 --->

### Integração do TeamViewer para PCs Windows com o software de cliente Intune
A integração do [TeamViewer](https://www.teamviewer.com) para PCs Windows que executem o cliente do Intune vai permitir estabelecer sessões de assistência remota com PCs Windows para ajudar a dar apoio aos departamentos de suporte técnico ao utilizador final. Isto inclui o Windows 7, 8, 8.1 e o Windows 10. Para saber mais, veja [Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune](intune/deploy-use/common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client).
<!---TFS 1284856--->

## Atualizações ao Portal da Empresa
### Web site do Portal da Empresa
- **Experiência do utilizador na inscrição de dispositivos Windows melhorada**<br/>
Se estiver a utilizar o acesso condicional, os passos de inscrição para Windows 8.1, ambiente de trabalho do Windows 10 e Windows 10 Mobile foram clarificados no Web site do Portal da Empresa. Agora, os utilizadores vão ver dois passos separados, “Inscrição de dispositivos” e “Workplace Join”, o que lhes permite ver mais facilmente o estado dos respetivos dispositivos e concluir o processo se se depararem com falhas na Workplace Join (WPJ). Espera-se que os passos separados também simplifiquem o processo de resolução de problemas para os administradores de TI. Anteriormente, quando os utilizadores finais tentavam inscrever e todos os passos da inscrição eram bem-sucedidos, menos a WPJ, o dispositivo inscrito não aparecia na lista de dispositivos para os utilizadores identificarem, confundindo-os.

### Android
- **Aplicação do Portal da Empresa para Android**<br/>
Se os utilizadores finais do Azure virem uma mensagem de erro a dizer que falta um certificado necessário nos respetivos dispositivos, podem tocar num botão chamado “Como resolver isto” para obter [passos](/intune/enduser/your-device-is-missing-a-required-certificate-android#your-device-is-missing-a-certificate-required-by-your-it-administrator) para instalar o certificado em falta. Se os utilizadores concluírem os passos, mas virem uma mensagem de erro “certificado em falta” adicional, é-lhes pedido que contactem o administrador de TI e lhe forneçam esta [ligação](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#android-certificate-issues), que contém os passos que os administradores de TI podem utilizar para corrigir o problema do certificado.

- **Restringir instalações de aplicações sideload em dispositivos inscritos**<br/>
Os dispositivos Android já não podem instalar aplicações através do Web site do Portal da Empresa, a não ser que esses dispositivos tenham sido inscritos no Intune com a aplicação do Portal da Empresa para Android do Intune.
<!---TFS 1299082--->

### iOS
- **Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para iOS**<br/>
Para melhorar o desempenho e o dimensionamento, o Intune deixa de mostrar todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel **Os Meus Dispositivos** da aplicação do Portal da Empresa para iOS. Apenas é apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa.

    O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só pode ser efetuada a partir da consola de administração do Intune. Além disso, o Intune está a descontinuar a utilização de contas DEM com o Programa de registo de dispositivos da Apple ou com a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados.

    Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível. Para obter mais informações, veja [Inscrever dispositivos pertencentes à empresa com o Gestor de Inscrição de Dispositivos no Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune).
<!---TFS 1233681--->

## Alteração de nomes de funcionalidades do Windows
- O [Microsoft Passport for Work](/intune/deploy-use/control-microsoft-passport-settings-on-devices-with-microsoft-intune) é agora conhecido como **Windows Hello para Empresas**.
- A [Proteção de dados da empresa](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-intune) é agora conhecida como **Windows Information Protection**.

## Novidades futuras
### Os Grupos do Intune vão transitar para os Grupos do Azure Active Directory a partir de agosto de 2016
O Intune está a criar uma nova experiência de gestão de grupos que utiliza os grupos de segurança do Azure Active Directory (AAD). Estes grupos de segurança do Azure Active Directory podem contar utilizadores e dispositivos e serão utilizados para a gestão de todos os grupos, implementações de políticas e implementações de perfis quando introduzirmos o novo portal de administração do Intune baseado no Azure.

Esta nova experiência irá:
- Libertá-lo da necessidade de duplicar grupos entre serviços.
- Permitir-lhe aceder a algumas novas funcionalidades de grupos do Azure Active Directory Premium (AADP).
- Proporcionar extensibilidade através do PowerShell e do Graph.
- Unificar a experiência de gestão de grupos ao nível da gestão de mobilidade empresarial.

Para permitir a mudança para os Grupos de Segurança, a experiência na consola de administração atual vai sofrer algumas alterações. Estas alterações e a utilização dos grupos de segurança do AAD serão registadas na documentação do Intune.

Os clientes que só agora estão a utilizar o Intune verão algumas das alterações aos grupos de segurança antes dos inquilinos atuais.

Para além das alterações à gestão de grupos, as funcionalidades seguintes vão ser preteridas:
- Excluir membros ou grupos ao criar um novo grupo
- Grupos **Utilizadores desagrupados** e **Dispositivos desagrupados**
- **Gerir Grupos** na função Administrador de Serviço
- Alertas personalizados com base em grupos para Regras de Notificação
- Ordenar com grupos em relatórios

Serão lançadas em agosto mais informações sobre como mitigar estas preterições.

### Inclusão de “Notificações” no Portal da Empresa para Android
Vamos lançar uma atualização para o Portal da Empresa para Android em setembro, que vai introduzir um ícone **Notificações** novo na home page. Tocar neste ícone vai permitir aceder à página **Notificações**, que mostrará ao utilizador final todos os itens que requerem atenção na aplicação do Portal da Empresa, como dispositivos não conformes, atualizações de inscrições e ativação de inscrições. Se também utilizar a aplicação do Portal da Empresa para iOS, já vai beneficiar da experiência de notificações. Com a introdução da página **Notificações**, não verá a página **Configuração do Acesso da Empresa** sempre que iniciar ou retomar o Portal da Empresa para Android, desde que o dispositivo já esteja inscrito. Sabemos que muitos dos nossos utilizadores criaram orientações para o utilizador final e agradecemos o aviso antecipado sempre que as suas orientações/capturas de ecrã precisem de ser atualizadas. Atualize a sua documentação de modo a refletir a alteração futura à experiência. Pode obter as capturas de ecrã atualizadas em https://aka.ms/androidcpupdate.  



### Roteiro da nuvem
Mantenha-se informado sobre os desenvolvimentos futuros do Intune com o [roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Depreciação de serviço
- **Alterações ao suporte para a aplicação do Portal da Empresa para iOS**<br/>
Em julho, todos os utilizadores da aplicação do Portal da Empresa do Microsoft Intune para iOS terão de utilizar a última versão. Os novos utilizadores só conseguirão transferir a versão mais recente e os utilizadores atuais terão de atualizar para a mesma. A versão mais recente requer o iOS 8.0 ou posterior, pelo que os utilizadores com dispositivos com versões do iOS mais antigas não poderão utilizar o Portal da Empresa nem inscrever enquanto não os atualizarem para o iOS 8.0 ou posterior e atualizarem a aplicação do Portal da Empresa para a última versão. Os dispositivos inscritos que tenham versões anteriores ao iOS 8.0 continuarão a ser geridos e listados na Consola de Administração do Intune.  

- **Versão do Browser Gerido para iOS mínima atualizada para 8.0**<br/>
Em agosto, o Intune vai lançar uma aplicação Browser Gerido do Microsoft Intune para iOS atualizada que só vai suportar dispositivos com o iOS 8.0 ou posterior. Embora os dispositivos iOS 7.1 continuem a poder utilizar a aplicação Browser Gerido atual, incentive os seus utilizadores a atualizarem para o iOS 8.0 ou posterior para aceder e tirar partido das novas funcionalidades do Browser Gerido.  
<!---TFS 1313253--->

- **As aplicações do Portal da Empresa para Windows 8 e Windows Phone 8 vão ser preteridas a partir de setembro de 2016.** <br/>
A partir de setembro de 2016, o Microsoft Intune vai terminar o suporte para as aplicações do Portal da Empresa do Microsoft Intune nas plataformas Windows Phone 8 e Windows 8. Para continuar a distribuir aplicações para estes dispositivos, atualize-os para o Windows 8.1 e o Windows Phone 8.1 e utilize as aplicações do Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 correspondentes.
<!---TFS 1255391--->

- **Aplicações do Visualizador do Intune** <br/>
Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
    - Visualizador AV do Intune
    - Visualizador de PDFs do Intune
    - Visualizador de Imagens do Intune para Android a partir do Google Play

  Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova [aplicação Rights Management (partilha RMS) para Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android. Quando a aplicação do visualizador do Intune deixar de ser suportada, será removida da Google Store e indisponibilizada para utilização futura.

<!--- - **Custom Group Targeting of Notification Rules Removal.**<br/>
Intune notification rules define who an email alert will be sent to from Intune. Currently, you can configure notification rules to send emails to all users of devices in an Intune device group that you created. From around June 1st 2016 moving forward, targeting user-created groups will no longer be supported.

    Today, to target a notification rule to a group you created from the Microsoft Intune administration console, you would take the following steps:

    In the **Admin** workspace, click **Notification Rules** > **Create New Rule**

    In step two of the Create Notification Rule Wizard, select the device groups which the rule will target. This step, “select device groups”, is being removed from the Intune Console.

    The preliminary timeline for this change is as follows:
    - In August, 2016, new tenants will not see step two of the Create Notification Rule Wizard. Exiting tenants are unaffected.
    - Around September, 2016, some existing tenants will not see the “select device groups” in the wizard.
    - Around November, 2016, we expect that all tenants will not see the “select device groups” in the wizard.

--->



## Versões anteriores do Intune
Se pretender ver o que foi disponibilizado no Intune durante os últimos seis meses, pode encontrar esta informação no artigo [Versões anteriores do Intune](previous-intune-releases.md).

### Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)



<!--HONumber=Aug16_HO1-->


