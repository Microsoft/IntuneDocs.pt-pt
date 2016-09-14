---
title: Novidades futuras | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b0653af30aa6e75888dd72c5b3a4afa0b2b1d596
ms.openlocfilehash: a3cc5ea639c31e3fec08e86f27f118e193b8f4b3


---

# Novidades futuras do Microsoft Intune - Agosto
Esta informação é fornecida ao abrigo de um contrato de confidencialidade numa base extremamente limitada e está sujeita a alterações. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu camarada do Intune/PM se tiver quaisquer dúvidas ou preocupações.

Esta página é atualizada periodicamente. Esteja atento a novas atualizações de Novidades futuras.

As seguintes alterações estão em desenvolvimento para o Intune. Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/en-US/library/mt718155(TechNet.10).aspx).


## Gestão de aplicações
### Aplicações ocultas e apresentadas para iOS 9.3
Para os dispositivos supervisionados com o iOS 9.3 ou posterior, poderá executar a lista das aplicações ocultas e apresentadas na política de configuração geral do iOS para:
- Especificar uma lista de aplicações que serão ocultas dos utilizadores. Os utilizadores não poderão ver ou iniciar estas aplicações.
- Especificar uma lista de aplicações que os utilizadores poderão ver e iniciar. Mais nenhuma outra aplicação pode ser vista ou lançada.

As aplicações que pode especificar incluem ambas as aplicações implementadas e as aplicações incorporadas do iOS como Mensagens e Notas.
<!---TFS 1279009--->

### Política de aplicações permitidas e bloqueadas para os dispositivos Samsung KNOX

Agora pode configurar uma política personalizada para os dispositivos Samsung KNOX que lhe permitem criar um dos seguintes:
- Uma lista de aplicações que estão bloqueadas de executar no dispositivo. Mesmo que esteja instalada, uma aplicação definida na lista de bloqueadas não pode ser ativada no dispositivo.
- Uma lista de aplicações que os utilizadores do dispositivo estão autorizados a instalar a partir da loja Google Play. Mais nenhuma outra aplicação pode ser instalada a partir da loja.

Estas definições só podem ser utilizadas por dispositivos que executem Samsung KNOX.
<!--- For details, see [Use custom policies to allow and block apps for Samsung KNOX devices]( custom-policy-to-allow-and-block-samsung-knox-apps.md)--->
<!---TFS 1311629 --->

### Novas aplicações compatíveis com as políticas de gestão de aplicações móveis (MAM)
A aplicação Yammer para [iOS](https://itunes.apple.com/app/yammer/id289559439?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.yammer.v1) vai ser compatível com as [políticas de gestão de aplicações móveis do Intune (MAM)](/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune), quer o dispositivo esteja inscrito ou não.

Para obter uma lista completa das aplicações compatíveis com o MAM, veja o site dos [parceiros de aplicações do Microsoft Intune](https://www.microsoft.com/en-us/cloud-platform/microsoft-intune-partners).
<!--- TFS 1252335 & 1252336--->

## Gestão de dispositivos
### Suporte para Android 7.0
Em agosto, o Intune vai prestar suporte no "dia 0" para o lançamento do sistema operativo Android 7.0 para dispositivos móveis.
<!---TFS 1262053--->
### A remoção da funcionalidade de reposição de códigos de acesso remotos por parte da Google em dispositivos com o Android 7.0
A Google está a remover a funcionalidade dos administradores de TI e os utilizadores finais poderem repor remotamente o código de acesso a dispositivos com o Android 7.0. Anteriormente, os administradores de TI podiam repor remotamente o código de acesso de um utilizador, assim como os utilizadores finais podiam repor os seus códigos de acesso a partir do site do Portal da Empresa.

## Gestão de grupos
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

## Portal da Empresa

### Ligação de comentários no Portal da Empresa para a Microsoft
O site do Portal da Empresa permite que os utilizadores finais toquem numa nova ligação de "Comentários", na parte inferior da página, para enviar comentários à Microsoft sobre as suas experiências com o site. Os comentários recolhidos são anónimos e vão ajudar a Microsoft a melhorar a experiência do site do Portal da Empresa para os utilizadores.
<!--- TFS 1313657--->

### Melhorias na forma como os utilizadores finais do iOS obtêm as aplicações
As seguintes alterações vão ser efetuadas em setembro nos mosaicos de aplicações na aplicação do Portal da Empresa para iOS de modo a direcionar os utilizadores para vistas diferentes numa única localização, o site do Portal da Empresa, para todas as suas aplicações. Atualmente, as restrições da Apple proíbem a linha de negócio e as aplicações geridas da App Store de serem listadas na aplicação do Portal da Empresa, exigindo também que os utilizadores visitem vistas diferentes para localizar todas as suas aplicações.

- Atualmente, o mosaico **Aplicações da Empresa** direciona para uma lista de todas as aplicações no separador TODOS do site do Portal da Empresa e continuará a funcionar da mesma forma. O nome de mosaico será alterado para **Todas as Aplicações**.
- Atualmente, o mosaico **Outras Aplicações** direciona para uma vista, dentro da aplicação do Portal da Empresa, que apresenta uma lista de todas as aplicações que a Apple permite que a aplicação do Portal da Empresa mostre. O nome de mosaico será alterado para **Aplicações em Destaque** e, ao tocar no mosaico, os utilizadores serão encaminhados para o separador EM DESTAQUE do site do Portal da Empresa.
-  Atualmente, o mosaico **Categorias** direciona para uma vista, dentro da aplicação do Portal da Empresa, que lista as categorias das aplicações. O nome do mosaico não será alterado, mas passará a direcionar para o separador CATEGORIAS do site do Portal da Empresa.
Pode encontrar capturas de ecrã atualizadas [aqui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

### Solicite a instalação da aplicação Browser Gerido do iOS se o Profissional de TI definir esse requisito para uma aplicação
Na versão de setembro da aplicação do Portal da Empresa do iOS, se tiver configurado um Web Clip para abrir apenas no browser gerido e se este não estiver instalado num dispositivo, a aplicação do Portal da Empresa no dispositivo pedirá ao utilizador para o instalar antes de poder instalar o Web Clip. 
<!---TFS 1228570--->

## Depreciação de serviço
### As aplicações do Portal da Empresa para Windows 8 e Windows Phone 8 vão ser preteridas a partir de setembro de 2016
A partir de outubro de 2016, o Microsoft Intune irá preterir o suporte para aplicações Windows 8 e Windows Phone 8 do Portal da Empresa. O Microsoft Intune irá também preterir o suporte para a plataforma do Windows Phone 8. Como resultado, não será capaz de inscrever ou atualizar dispositivos Windows Phone 8. Pode continuar a gerir dispositivos Windows Phone 8 e Windows 8 que já tenham sido inscritos. Atualize dispositivos Windows Phone 8 e Windows 8 para Windows Phone 8.1 e Windows 8.1, e utilize as aplicações do Portal da Empresa para Windows 8.1 e Windows Phone 8.1 correspondentes para continuar a distribuir aplicações para estes dispositivos, sem interrupções.
<!---TFS 1255391--->

### Remoção da Filtragem Personalizada de Grupo de Regras de Notificação
As regras de notificações do Intune definem a quem será enviado um alerta de e-mail a partir do Intune. Atualmente, pode configurar regras de notificação para enviar e-mails a todos os utilizadores de dispositivos num grupo de dispositivos do Intune criado por si. A partir de junho de 2016, os grupos criados para os utilizadores já não serão suportados.

O calendário preliminar para esta alteração é o seguinte:
- Em setembro de 2016, os novos inquilinos deixarão de ver o passo dois do Assistente para Criar Regra de Notificação. Os inquilinos existentes não são afetados.
- Por volta de outubro de 2016, alguns inquilinos existentes não verão “selecionar grupos de dispositivos” no assistente.
- Mais tarde, esperamos que nenhum inquilino veja “selecionar grupos de dispositivos” no assistente.

<!---   TFS 1278864--->
### Alterações ao suporte para a aplicação do Portal da Empresa para iOS
Em setembro, todos os utilizadores da aplicação do Portal da Empresa do Microsoft Intune para iOS terão de utilizar a última versão. Os novos utilizadores só conseguirão transferir a versão mais recente e os utilizadores atuais terão de atualizar para a mesma. A versão mais recente requer o iOS 8.0 ou posterior, pelo que os utilizadores com dispositivos com versões do iOS mais antigas não poderão utilizar o Portal da Empresa nem inscrever enquanto não os atualizarem para o iOS 8.0 ou posterior e atualizarem a aplicação do Portal da Empresa para a última versão. Os dispositivos inscritos que tenham versões anteriores ao iOS 8.0 continuarão a ser geridos e listados na Consola de Administração do Intune.

<!---TFS 1283165--->


### Aplicações do Visualizador do Intune
Com o lançamento da nova aplicação de partilha RMS, vamos remover as seguintes aplicações do Visualizador do Intune em agosto de 2016:
- Visualizador AV do Intune
- Visualizador de PDFs do Intune
- Visualizador de Imagens do Intune para Android a partir do Google Play

Em vez de utilizar as aplicações do Visualizador do Intune, recomendamos que utilize a nova aplicação Rights Management (partilha RMS) para Android, o que lhe permite implementar uma aplicação em vez de três aplicações separadas para ver com segurança os ficheiros empresariais em dispositivos Android. Saiba mais sobre a [aplicação de partilha RMS](https://docs.microsoft.com/en-us/intune/deploy-use/end-user-experience-for-mam-enabled-apps-with-microsoft-intune#viewing-media-files-with-the-rights-management-sharing-app).
<!--- goes in 1608 What's New--->


### Consulte também
Veja [Novidades do Microsoft Intune](whats-new-in-microsoft-intune.md) para obter detalhes sobre os desenvolvimentos recentes.



<!--HONumber=Sep16_HO2-->


