---
title: Novidades | Microsoft Intune
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c636efee82331d6feac75153b872526f7af7c882
ms.openlocfilehash: 814312b0ac6055ffff2efad2ddbdaa8664f84fde


---

# Novidades do Microsoft Intune
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

>[!IMPORTANT] 
>Mensagem do blogue - garantir que os dispositivos móveis são atualizados com o Microsoft Intune<br>
>Tendo em conta os recentes ataques do software malicioso "Trident" em dispositivos iOS, publicámos uma nova mensagem de blogue, [Ensuring mobile devices are up to date using Microsoft Intune (Garantir que os dispositivos móveis são atualizados com o Microsoft Intune – em inglês)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) para o ajudar a saber mais sobre as diferentes formas como o Intune o pode ajudar a manter os seus dispositivos seguros e atualizados.

## Setembro de 2016

## Atualizações ao Portal da Empresa
### Android

**Inclusão de "Notificações" no Portal da Empresa para Android**

Foi adicionado um novo ícone Notificações à homepage do Portal da Empresa para Android. Tocar neste ícone permite aceder à página Notificações, que mostra ao utilizador final todos os itens que necessitam de atenção na aplicação Portal da Empresa, como dispositivos que não estejam em conformidade, atualizações de inscrições e ativação de inscrições. A aplicação Portal da Empresa para iOS já tem esta experiência de notificações. A nova página Notificações permite que o utilizador não tenha de ver a página da Configuração do Acesso da Empresa sempre que iniciar ou retomar o Portal da Empresa, desde que o dispositivo já esteja inscrito. Se criar as suas próprias orientações para o utilizador final, poderá querer atualizar a sua documentação para que a mesma reflita esta alteração. Consulte as capturas de ecrã atualizadas [aqui](https://aka.ms/androidcpupdate).  
<!---TFS 1095560--->

### Windows
**Botão de feedback adicionado à aplicação Portal da Empresa para Windows 8.1**

A aplicação Portal da Empresa para Windows 8.1 permite que os utilizadores finais enviem feedback sobre a aplicação através do novo botão "enviar feedback". Para localizar o botão, os utilizadores têm de tocar no menu de "três pontos"que se encontra no canto inferior direito do ecrã da aplicação Portal da Empresa e, em seguida, tocar em **enviar feedback**. O feedback recolhido é anónimo e irá ajudar a Microsoft a melhorar a experiência da aplicação Portal da Empresa para os utilizadores.
<!---TFS 1317806--->

## Agosto de 2016
## Gestão de aplicações
<!---@Barry, I created the buckets of App management, Device management, etc but am not tied to them. Just wanted to break up and organize the feature list. If you're going to take over the Company Portal section, please talk to Stacie about how she's been organizing it. --->

### Aplicações ocultas e apresentadas para iOS 9.3
Para os dispositivos supervisionados com o iOS 9.3 ou posterior, pode utilizar a lista das aplicações ocultas e apresentadas na política de configuração geral do iOS para:
- Especificar uma lista de aplicações que serão ocultas dos utilizadores. Os utilizadores não poderão ver ou iniciar estas aplicações.
- Especificar uma lista de aplicações que os utilizadores poderão ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.

As aplicações que pode especificar incluem ambas as aplicações implementadas e as aplicações incorporadas do iOS como Mensagens e Notas. Para obter detalhes, veja [Definições de política para iOS no Microsoft Intune]( https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)
<!---TFS 1279009 checked--->
### Política de aplicações permitidas e bloqueadas para os dispositivos Samsung KNOX
Agora pode configurar uma política personalizada para os dispositivos Samsung KNOX que lhe permitem criar um dos seguintes:
- Uma lista de aplicações que estão bloqueadas de executar no dispositivo. Mesmo que esteja instalada, uma aplicação definida na lista de bloqueadas não pode ser ativada no dispositivo.
- Uma lista de aplicações que os utilizadores do dispositivo estão autorizados a instalar a partir da loja Google Play. Mais nenhuma outra aplicação pode ser instalada a partir da loja.

Estas definições só podem ser utilizadas por dispositivos que executem Samsung KNOX.
Para obter detalhes, veja [Utilizar políticas personalizadas para permitir e bloquear aplicações para dispositivos Samsung KNOX]( custom-policy-to-allow-and-block-samsung-knox-apps.md).
<!---TFS 1311629 checked --->
### Novas aplicações compatíveis com as políticas de gestão de aplicações móveis (MAM)
A aplicação Yammer para [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) é agora compatível com as [políticas de gestão de aplicações móveis do Intune (MAM)](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), quer o dispositivo esteja inscrito ou não.

Para obter uma lista completa das aplicações compatíveis com o MAM, veja o site dos [parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336 checked--->


<!--- I started putting TFS numbers in the What's Coming topic and found it helpful when updating the What's New. Up to you if you want to continue. --->

### Aplicações do Visualizador do Intune
Com o lançamento da nova aplicação de partilha RMS, estamos a remover as seguintes aplicações do Visualizador do Intune, a partir de agosto de 2016:
- Visualizador AV do Intune
- Visualizador de PDFs do Intune
- Visualizador de Imagens do Intune para Android a partir do Google Play

Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova [aplicação Rights Management (partilha RMS) para Android](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app), o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android. Quando a aplicação do visualizador do Intune deixar de ser suportada, será removida da Google Store e indisponibilizada para utilização futura.

## Gestão de dispositivos
### Suporte para Android 7.0
O Intune fornece suporte no "dia 0" para o lançamento do sistema operativo Android 7.0 para dispositivos móveis.
<!---TFS 1262053--->
### A remoção da funcionalidade de reposição de códigos de acesso remotos por parte da Google em dispositivos com o Android 7.0
A Google está a remover a funcionalidade dos administradores de TI e os utilizadores finais poderem repor remotamente o código de acesso a dispositivos com o Android 7.0. Anteriormente, os administradores de TI podiam repor remotamente o código de acesso de um utilizador, assim como os utilizadores finais podiam repor os seus códigos de acesso a partir do site do Portal da Empresa.



## Atualizações ao Portal da Empresa
### Web site do Portal da Empresa
- **Ligação de comentários no Portal da Empresa para a Microsoft** <br/>
O site do Portal da Empresa permite que os utilizadores finais toquem numa nova ligação de "Comentários", na parte inferior da página, para enviar comentários à Microsoft sobre as suas experiências com o site. Os comentários recolhidos são anónimos e vão ajudar a Microsoft a melhorar a experiência do site do Portal da Empresa para os utilizadores.
<!--- TFS 1313657 checked--->

### iOS
- **Versão mínima do Managed Browser para iOS atualizada para 8.0**<br/>
A aplicação Microsoft Intune Managed Browser para iOS foi atualizada para suportar dispositivos com o iOS 8.0 ou posterior. Embora os dispositivos iOS 7.1 continuem a poder utilizar a aplicação Managed Browser atual, incentive os seus utilizadores a atualizarem para o iOS 8.0 ou posterior para aceder e tirar partido das novas funcionalidades do Managed Browser.  
<!---TFS 1313253 checked--->

## Novidades futuras

### Suporte do iOS 10
O Intune irá suportar totalmente o iOS 10. Serão publicadas mais informações após o lançamento do iOS 10 ao público.

### Os Grupos do Intune vão transitar para os Grupos do Azure Active Directory a partir de setembro de 2016
O Intune está a criar uma nova experiência de gestão de grupos que utiliza os grupos de segurança do Azure Active Directory (AAD) como grupos de utilizadores e de dispositivos no Intune. Estes grupos vão ser utilizados para a gestão de todos os grupos, implementações de políticas e implementações de perfis **quando introduzirmos o novo portal de administração do Intune baseado no Azure**.

Esta experiência nova evita que tenha de duplicar grupos entre os serviços, **permite-lhe aceder a algumas funcionalidades novas dos grupos do Azure Active Directory Premium (AADP)** e proporciona extensibilidade através da utilização do PowerShell e do Graph. Esta alteração também vai unificar a experiência de gestão de grupos ao nível da gestão de mobilidade empresarial.

Para permitir a mudança para os Grupos de Segurança, a experiência na **consola de administração atual** vai sofrer algumas alterações. **Estas alterações e a utilização dos grupos de segurança do AAD serão registadas na documentação do Intune**.

Os clientes que só agora estão a utilizar o Intune verão **algumas das alterações aos grupos de segurança antes dos inquilinos atuais**.

Para além das alterações à gestão de grupos, **as funcionalidades seguintes vão ser preteridas**:
- Excluir membros ou grupos ao criar um novo grupo
- Grupos **Utilizadores desagrupados** e **Dispositivos desagrupados**
- **Gerir Grupos** na função Administrador de Serviço
- Alertas personalizados com base em grupos para Regras de Notificação
- Ordenar com grupos em relatórios
<!--- TFS 1295329--->

### Inclusão de “Notificações” no Portal da Empresa para Android
Vamos lançar uma atualização para o Portal da Empresa para Android em setembro, que vai introduzir um ícone **Notificações** novo na home page. Tocar neste ícone vai permitir aceder à página **Notificações**, que mostrará ao utilizador final todos os itens que requerem atenção na aplicação do Portal da Empresa, como dispositivos não conformes, atualizações de inscrições e ativação de inscrições. Se também utilizar a aplicação do Portal da Empresa para iOS, já vai beneficiar da experiência de notificações. Com a introdução da página **Notificações**, não verá a página **Configuração do Acesso da Empresa** sempre que iniciar ou retomar o Portal da Empresa para Android, desde que o dispositivo já esteja inscrito. Sabemos que muitos dos nossos utilizadores criaram orientações para o utilizador final e agradecemos o aviso antecipado sempre que as suas orientações/capturas de ecrã precisem de ser atualizadas. Atualize a sua documentação de modo a refletir a alteração futura à experiência. Pode obter as capturas de ecrã atualizadas em https://aka.ms/androidcpupdate.  

### Melhorias na forma como os utilizadores finais do iOS obtêm as aplicações
As seguintes alterações vão ser efetuadas em setembro nos mosaicos de aplicações na aplicação do Portal da Empresa para iOS de modo a direcionar os utilizadores para vistas diferentes numa única localização, o site do Portal da Empresa, para todas as suas aplicações. Atualmente, as restrições da Apple proíbem a linha de negócio e as aplicações geridas da App Store de serem listadas na aplicação do Portal da Empresa, exigindo também que os utilizadores visitem vistas diferentes para localizar todas as suas aplicações.

- Atualmente, o mosaico **Aplicações da Empresa** direciona para uma lista de todas as aplicações no separador TODOS do site do Portal da Empresa e continuará a funcionar da mesma forma. O nome de mosaico será alterado para **Todas as Aplicações**.
- Atualmente, o mosaico **Outras Aplicações** direciona para uma vista, dentro da aplicação do Portal da Empresa, que apresenta uma lista de todas as aplicações que a Apple permite que a aplicação do Portal da Empresa mostre. O nome de mosaico será alterado para **Aplicações em Destaque** e, ao tocar no mosaico, os utilizadores serão encaminhados para o separador EM DESTAQUE do site do Portal da Empresa.
-  Atualmente, o mosaico **Categorias** direciona para uma vista, dentro da aplicação do Portal da Empresa, que lista as categorias das aplicações. O nome do mosaico não será alterado, mas passará a direcionar para o separador CATEGORIAS do site do Portal da Empresa. Pode encontrar capturas de ecrã atualizadas [aqui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

### Roteiro da nuvem
Mantenha-se informado sobre os desenvolvimentos futuros do Intune com o [roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune).

### Depreciação de serviço
<!---@Barry, we started listing service deprecations earlier this summer. --->
- **Alterações ao suporte para a aplicação do Portal da Empresa para iOS**<br/>
Em setembro, todos os utilizadores da aplicação do Portal da Empresa do Microsoft Intune para iOS terão de utilizar a última versão. Os novos utilizadores só conseguirão transferir a versão mais recente e os utilizadores atuais terão de atualizar para a mesma. A versão mais recente requer o iOS 8.0 ou posterior, pelo que os utilizadores com dispositivos com versões do iOS mais antigas não poderão utilizar o Portal da Empresa nem inscrever enquanto não os atualizarem para o iOS 8.0 ou posterior e atualizarem a aplicação do Portal da Empresa para a última versão. Os dispositivos inscritos que tenham versões anteriores ao iOS 8.0 continuarão a ser geridos e listados na Consola de Administração do Intune.  

- **Versão mínima do Managed Browser para iOS atualizada para 8.0**<br/>
Em agosto, o Intune vai lançar uma aplicação atualizada do Microsoft Intune Managed Browser para iOS que só irá suportar dispositivos com o iOS 8.0 ou posterior. Embora os dispositivos iOS 7.1 continuem a poder utilizar a aplicação Managed Browser atual, incentive os seus utilizadores a atualizarem para o iOS 8.0 ou posterior para acederem e tirarem partido das novas funcionalidades do Managed Browser.  
<!---TFS 1313253--->

- **As aplicações do Portal da Empresa para Windows 8 e Windows Phone 8 vão ser preteridas** <br/>
A partir de outubro de 2016, o Microsoft Intune irá preterir o suporte para aplicações Windows 8 e Windows Phone 8 do Portal da Empresa. O Microsoft Intune irá também preterir o suporte para a plataforma do Windows Phone 8. Como resultado, não será capaz de inscrever ou atualizar dispositivos Windows Phone 8. Pode continuar a gerir dispositivos Windows Phone 8 e Windows 8 que já tenham sido inscritos. Atualize dispositivos Windows Phone 8 e Windows 8 para Windows Phone 8.1 e Windows 8.1, e utilize as aplicações do Portal da Empresa para Windows 8.1 e Windows Phone 8.1 correspondentes para continuar a distribuir aplicações para estes dispositivos, sem interrupções.
<!---TFS 1255391--->

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



<!--HONumber=Sep16_HO2-->


