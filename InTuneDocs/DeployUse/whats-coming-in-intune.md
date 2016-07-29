---
title: Novidades futuras | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 9b536372623632b609433c49991a8bdc70e6da49


---

# Novidades futuras do Microsoft Intune - Julho
Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Esteja atento a novas atualizações de Novidades futuras.

As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Gestão de aplicações
### Melhorar a experiência de atualização de perfis de aprovisionamento de aplicações
As aplicações de linha de negócio iOS da Apple são criadas com um perfil de aprovisionamento incluído e o respetivo código assinado com um certificado. Quando as aplicações são executadas num dispositivo iOS, o iOS confirma a integridade das mesmas e aplica as políticas definidas pelo perfil de aprovisionamento.

Geralmente, o certificado de assinatura da empresa que utiliza para assinar as aplicações dura três anos. No entanto, o perfil de aprovisionamento expira após um ano. Com esta atualização, o Intune vai proporcionar-lhe as ferramentas para implementar proativamente uma nova política de perfil de aprovisionamento em dispositivos que tenham aplicações prestes a expirar enquanto o certificado ainda é válido.
<!--- TFS 1280247--->

### Suporte de Xamarin
O SDK da aplicação Microsoft Intune suportará aplicações Xamarin nos seguintes cenários:

- Escrever novas aplicações ou modificar o código de aplicações de linha de negócio existentes com o Intune SDK. Poderá obter o plug-in na página [Microsoft Intune Github](https://github.com/msintuneappsdk).
- Adicionar suporte de MAM a aplicações de linha de negócio existentes com a ferramenta de encapsulamento de aplicações do Intune

Para obter ajuda para escolher que método utilizar, consulte [Decidir como preparar as aplicações para a gestão de aplicações móveis com o Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/decide-how-to-prepare-apps-for-mobile-application-management-with-microsoft-intune).

<!--- TFS 1061478 & TFS 1152340--->

## Gestão de dispositivos
### Aumento nos limites de inscrição de dispositivos
O Intune vai aumentar o limite máximo de inscrição de dispositivos configuráveis de cinco para 15 dispositivos por utilizador.
<!---TFS 1289896 --->

## Gestão de grupos
### Os Grupos do Intune vão transitar para os Grupos do Azure Active Directory a partir de agosto de 2016
O Intune está a criar uma nova experiência de gestão de grupos que utiliza os grupos de segurança do Azure Active Directory (AAD) como grupos de utilizadores e de dispositivos no Intune. Estes grupos vão ser utilizados para a gestão de todos os grupos, implementações de políticas e implementações de perfis **quando introduzirmos o novo portal de administração do Intune baseado no Azure**.

Esta experiência nova evita que tenha de duplicar grupos entre os serviços, **permite-lhe aceder a algumas funcionalidades novas dos grupos do Azure Active Directory Premium (AADP)** e proporciona extensibilidade através da utilização do PowerShell e do Graph. Esta alteração também vai unificar a experiência de gestão de grupos ao nível da gestão de mobilidade empresarial.

Para permitir a mudança para os Grupos de Segurança, a experiência na **consola de administração atual** vai sofrer algumas alterações. **Estas alterações e a utilização dos grupos de segurança do AAD serão registadas na documentação do Intune**.

Os clientes que só agora estão a utilizar o Intune verão **algumas das alterações aos grupos de segurança antes dos inquilinos atuais**.

Para além das alterações à gestão de grupos, **as funcionalidades seguintes vão ser preteridas**:
- Excluir membros ou grupos ao criar um novo grupo
- “Gerir Grupos” na função Administrador de Serviço
- Alertas personalizados com base em grupos para Regras de Notificação
- Ordenar com grupos em relatórios


## Portal da Empresa

### Inclusão de “Notificações” no Portal da Empresa para Android
Vamos lançar uma atualização para o Portal da Empresa para Android em agosto, que vai introduzir um ícone **Notificações** novo na home page. Tocar neste ícone vai permitir aceder à página **Notificações**, que mostrará ao utilizador final todos os itens que requerem atenção na aplicação do Portal da Empresa, como dispositivos não conformes, atualizações de inscrições e ativação de inscrições. Se também utilizar a aplicação do Portal da Empresa para iOS, já vai beneficiar da experiência de notificações. Com a introdução da página **Notificações**, não verá a página **Configuração do Acesso da Empresa** sempre que iniciar ou retomar o Portal da Empresa para Android, desde que o dispositivo já esteja inscrito. Sabemos que muitos dos nossos utilizadores criaram orientações para o utilizador final e agradecemos o aviso antecipado sempre que as suas orientações/capturas de ecrã precisem de ser atualizadas. Atualize a sua documentação de modo a refletir a alteração futura à experiência. Para ver capturas de ecrã atualizadas, aceda a https://aka.ms/androidcpupdate  

### Ajudar os utilizadores a resolver problemas de inscrição quando Workplace Join falha
Se estiver a utilizar o acesso condicional, os passos de inscrição para Windows 8.1, ambiente de trabalho do Windows 10 e Windows 10 Mobile foram simplificados no Web site do Portal da Empresa para os utilizadores finais que se deparem com falhas de Workplace Join (WPJ). Anteriormente, quando os utilizadores finais tentavam inscrever e fazer uma WPJ e a inscrição era bem-sucedida, mas a WPJ falhava, o dispositivo inscrito não aparecia na lista de dispositivos para os utilizadores identificarem, confundindo-os. Agora, os utilizadores vão ver dois passos separados, “Inscrição de dispositivos” e “Workplace Join”, o que lhes permite ver mais facilmente o estado dos respetivos dispositivos e concluir o processo depois de a WPJ falhar. Espera-se que os passos separados também simplifiquem o processo de resolução de problemas para os administradores de TI.

### Alterações às contas de Gestores de Inscrição de Dispositivos na aplicação do Portal da Empresa para iOS
Para melhorar o desempenho e o dimensionamento, o Intune irá deixar de mostrar todos os dispositivos de Gestores de Inscrição de Dispositivos (DEM) no painel Os Meus Dispositivos da aplicação do Portal da Empresa iOS. Apenas será apresentado o dispositivo local que está a executar a aplicação e apenas se estiver inscrito através da aplicação Portal da Empresa. O utilizador DEM pode executar ações no dispositivo local, mas a gestão remota de outros dispositivos inscritos só poderá ser efetuada a partir da consola de administração do Intune.  Além disso, o Intune está a descontinuar a utilização de contas DEM com o Programa de registo de dispositivos da Apple ou com a ferramenta Apple Configurator. Ambos os métodos de inscrição já suportam a inscrição sem a ação do utilizador para dispositivos iOS partilhados. Utilize apenas contas DEM quando a inscrição sem a ação do utilizador para dispositivos partilhados não estiver disponível.
<!---TFS 1233681--->
### Restringir a instalação de aplicações sideload em dispositivos Android inscritos
Os dispositivos Android já não podem instalar aplicações através do Web site do Portal da Empresa, a não ser que esses dispositivos tenham sido inscritos no Intune com a aplicação do Portal da Empresa para Android do Intune.
<!---TFS 1299082--->

## Depreciação de serviço
**As aplicações do Portal da Empresa para Windows 8 e Windows Phone 8 vão ser preteridas a partir de setembro de 2016.** A partir de setembro de 2016, o Microsoft Intune vai terminar o suporte para as aplicações do Portal da Empresa do Microsoft Intune nas plataformas Windows Phone 8 e Windows 8. Para continuar a distribuir aplicações para estes dispositivos, atualize-os para o Windows 8.1 e o Windows Phone 8.1 e utilize as aplicações do Portal da Empresa para Windows 8.1 e o Windows Phone 8.1 correspondentes.
<!---TFS 1255391--->

**Remoção da Filtragem Personalizada de Grupo de Regras de Notificação.**
As regras de notificações do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificação para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune criado por si. A partir de 1 de junho de 2016 em diante, a segmentação de grupos criados pelo utilizador deixará de ser suportada.

O calendário preliminar para esta alteração é o seguinte:
- Em agosto de 2016, os novos inquilinos deixarão de ver o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não são afetados.
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



<!--HONumber=Jul16_HO4-->


