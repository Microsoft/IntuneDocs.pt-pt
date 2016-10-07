---
title: Novidades | Microsoft Intune
description: "Saiba quais são as novidades deste mês e as versões anteriores do Microsoft Intune"
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 09/26/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: fab51ee0-638d-4dd4-8d8f-1f263bc11e5c
ms.reviewer: mamoriss
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ecf43b38e9593375981770583220d4ce2dfd709f
ms.openlocfilehash: 32610d4138fba82e034cc7dadccc09e0a6d31cd3


---
# Novidades do Microsoft Intune – setembro
Saiba quais são as novidades nesta versão do Microsoft Intune. Pode também descobrir quais são as alterações futuras que deve planear, bem como informações sobre versões anteriores.

Todas estas funcionalidades também serão suportadas, em algum momento, em implementações de clientes híbridas (Configuration Manager com o Intune). Para obter mais informações sobre as novas funcionalidades híbridas, veja a [página Hybrid What’s New (Novidades nas Implementações Híbridas)](https://technet.microsoft.com/library/mt718155.aspx).
<!---@Barry, the above blurb stays in each version, but make sure Tyler signs off each time. Also, remember to set the ms.date in the metadata to the sprint release. --->

>[!IMPORTANT]
>Mensagem do blogue - garantir que os dispositivos móveis são atualizados com o Microsoft Intune<br>
>Tendo em conta os recentes ataques do software malicioso "Trident" em dispositivos iOS, publicámos uma nova mensagem de blogue, [Ensuring mobile devices are up to date using Microsoft Intune (Garantir que os dispositivos móveis são atualizados com o Microsoft Intune – em inglês)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/26/ensuring-mobile-devices-are-up-to-date-using-microsoft-intune/) para o ajudar a saber mais sobre as diferentes formas como o Intune o pode ajudar a manter os seus dispositivos seguros e atualizados.

## Novas funcionalidades, anúncios e informações
* [Acesso condicional do Windows](#windows-conditional-access)
* [Suporte do iOS 10](#ios-10-support)
* [A Ferramenta de Encapsulamento de Aplicações suporta serviços MAM para Android e iOS sem a inscrição de dispositivos](#app-wrapping-tool-supports-mam-without-device-enrollment-for-android-and-ios)
* [A transição de grupos do Intune para o Azure Active Directory terá início em setembro](#intune-groups-begin-transitioning-to-azure-active-directory-in-september)
* [Integração com a Lookout para a proteção de dispositivos Android](#lookout-integration-to-protect-android-devices)
* [Atualizações ao Portal da Empresa para Android, iOS e Windows](#company-portal-updates)
* [Glossário do Intune](#intune-glossary)
* [Novidades futuras](#whats-coming)

## Acesso condicional do Windows
Agora pode criar políticas de acesso condicional através da consola de administrador do Intune para bloquear o acesso de PCs Windows ao Exchange Online e ao SharePoint Online. Também pode criar políticas de acesso condicional para bloquear o acesso a aplicações universais e de ambiente de trabalho do Office. 

## Suporte do iOS 10
Os cenários MDM e MAM existentes do Intune são compatíveis com o iOS 10. Para obter sugestões, consulte o [Blogue da Equipa de Suporte do Intune (em inglês)](https://blogs.technet.microsoft.com/intunesupport/2016/09/13/support-tip-intune-support-for-ios-10/).

## A Ferramenta de Encapsulamento de Aplicações suporta serviços MAM para Android e iOS sem a inscrição de dispositivos
A Ferramenta de Encapsulamento de Aplicações é uma ferramenta de linha de comandos utilizada para ativar aplicações de linha de negócio (LOB) MAM do Intune para iOS e Android. É a forma mais simples de incorporar o SDK de MAM do Intune na sua aplicação, de modo a que a mesma possa impor as políticas MAM implementadas através do Intune. Ao utilizar políticas de MAM, pode:

1. Encriptar os dados da aplicação.
2. Pedir ao técnico de informação que introduza um número PIN ao iniciar a aplicação.
3. Permitir que a aplicação transfira dados apenas para outras aplicações geridas.
4. Impedir que a aplicação crie cópias de segurança de dados no Android, no iTunes e no iCloud.
5. Permitir as ações Cortar, Copiar e Colar apenas com outras aplicações geridas.

A pré-visualização pública da Ferramenta de Encapsulamento de Aplicações suporta agora serviços de MAM para iOS e Android sem a inscrição de dispositivos em aplicações LOB internas. Isto significa que os seus utilizadores finais não terão de inscrever os respetivos dispositivos com o Intune para utilizar aplicações LOB preparadas para MAM.

Qualquer pessoa pode testar o software de pré-visualização pública e consultar documentos úteis que se encontram no GitHub de msintuneappsdk:

http://www.github.com/msintuneappsdk/intune-app-wrapper-ios-preview

http://www.github.com/msintuneappsdk/intune-app-wrapper-android-preview

Antes de instalar e utilizar a Versão de Pré-lançamento da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android e iOS, tem de:

* Ler os Termos de Licenciamento da Microsoft para a Versão de Pré-lançamento da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android e iOS
* Imprimir e guardar uma cópia dos termos de licenciamento nos seus registos. Ao transferir e utilizar a Versão de Pré-lançamento da Ferramenta de Encapsulamento de Aplicações do Microsoft Intune para Android, está a aceitar esses termos de licenciamento. Caso não aceite os termos, não deverá utilizar o software.
<!---TFS 1235607--->

## A transição de grupos do Intune para o Azure Active Directory terá início em setembro
Algumas das novas contas do Intune utilizarão os grupos de segurança do Azure Active Directory em vez dos grupos de utilizadores do Intune. A página de grupos do portal do Intune terá uma ligação que o direciona para o portal de gestão do Azure e que lhe permite saber se está a trabalhar com grupos de segurança.

## Integração com a Lookout para a proteção de dispositivos Android
A Microsoft está a integrar a solução de proteção da Lookout contra ameaças que afetam dispositivos móveis para proteger dispositivos móveis Android através da deteção de malware, aplicações de risco e muito mais. A solução da Lookout ajuda-o a determinar o nível da ameaça, que é configurável. Pode criar uma regra de política de conformidade no Intune para determinar a conformidade dos dispositivos com base na avaliação de riscos feita pela Lookout. Ao utilizar políticas de acesso condicional, pode permitir ou bloquear o acesso a recursos da sua empresa com base no estado de conformidade do dispositivo.

Os utilizadores finais de dispositivos em não conformidade receberão um pedido para os inscrever e terão de instalar a aplicação Lookout for Work em dispositivos Android, ativar a aplicação e corrigir as ameaças comunicadas na mesma para obterem acesso. Para saber mais, consulte [Restringir o acesso com base no dispositivo, na rede e no risco da aplicação](restrict-access-based-on-device-network-app-risk.md).


## Atualizações ao Portal da Empresa

### Android

**Inclusão de "Notificações" no Portal da Empresa para Android**<br/>
Foi adicionado um novo ícone Notificações à homepage do Portal da Empresa para Android. Tocar neste ícone permite aceder à página Notificações, que mostra ao utilizador final todos os itens que necessitam de atenção na aplicação Portal da Empresa, como dispositivos que não estejam em conformidade, atualizações de inscrições e ativação de inscrições. A aplicação Portal da Empresa para iOS já tem esta experiência de notificações. A nova página Notificações permite que o utilizador não tenha de ver a página da Configuração do Acesso da Empresa sempre que iniciar ou retomar o Portal da Empresa, desde que o dispositivo já esteja inscrito. Se criar as suas próprias orientações para o utilizador final, poderá querer atualizar a sua documentação para que a mesma reflita esta alteração. Consulte as capturas de ecrã atualizadas [aqui](https://aka.ms/androidcpupdate).  
<!---TFS 1095560--->

**Fornecer feedback no Portal da Empresa para Android**</br>
Foi adicionado um novo item ao menu do Portal da Empresa para Android. Tocar em **Ajuda e Feedback** mostra três ações:
* Utilize a opção **Obter Ajuda** para denunciar problemas relacionados com o Portal da Empresa ao seu departamento de TI. O departamento de TI cria um e-mail através do seu cliente de e-mail e anexa os registos do Portal da Empresa ao mesmo. A opção **Obter Ajuda** substitui a funcionalidade **Enviar Dados** na página **Definições**.
* Utilize a opção **Enviar Feedback** para fornecer feedback à equipa do Portal da Empresa.
* Utilize a opção **Classificar a nossa aplicação** para deixar uma classificação ou uma crítica à aplicação Portal da Empresa no Google Play.

### iOS
**Alterações ao suporte para a aplicação do Portal da Empresa para iOS**<br/>
Todos os utilizadores da aplicação Portal da Empresa do Microsoft Intune para iOS têm de utilizar agora a versão mais recente. Os novos utilizadores só poderão transferir a versão mais recente e aos utilizadores atuais será pedido que atualizem para a mesma. A versão mais recente necessita do iOS 8.0 ou posterior, pelo que os utilizadores com dispositivos com versões mais antigas do iOS não poderão utilizar o Portal da Empresa nem inscrevê-los até os atualizarem para o iOS 8.0 ou posterior e atualizarem a aplicação Portal da Empresa para a versão mais recente. Os dispositivos inscritos que tenham versões anteriores ao iOS 8.0 continuarão a ser geridos e listados na Consola de Administração do Intune.
<!---TFS 1283165--->

**Melhorias na forma como os utilizadores finais do iOS obtêm as aplicações**<br/>
As seguintes alterações foram feitas aos mosaicos de aplicações na aplicação Portal da Empresa para iOS, para direcionar os utilizadores para diferentes vistas numa única localização – o site do Portal da Empresa – em todas as respetivas aplicações. As restrições da Apple proíbem as aplicações geridas da App Store e de linha de negócio de serem listadas na aplicação Portal da Empresa e exigem também que os utilizadores acedam a vistas diferentes para localizar todas as suas aplicações.

- O mosaico **Aplicações da Empresa** apontava anteriormente para uma lista de todas as aplicações no separador TODOS do site do Portal da Empresa e irá continuar a funcionar da mesma forma. O nome do mosaico foi alterado para **Todas as Aplicações**.
- O mosaico **Outras Aplicações** apontava anteriormente para uma vista, dentro da aplicação Portal da Empresa, que indicava todas as aplicações que a Apple permite que a aplicação Portal da Empresa apresente. O nome do mosaico foi alterado para **Aplicações Em Destaque** e tocar no mosaico irá direcionar os utilizadores para o separador EM DESTAQUE do site do Portal da Empresa.
-  O mosaico **Categorias** apontava anteriormente para uma vista, dentro da aplicação Portal da Empresa, que indicava categorias de aplicações. O nome do mosaico não foi alterado, mas aponta agora para o separador CATEGORIAS do site do Portal da Empresa.
Pode encontrar capturas de ecrã atualizadas [aqui](https://gallery.technet.microsoft.com/Improvements-in-how-iOS-d1104186).
<!---TFS 1317133--->

**Solicite a instalação da aplicação Browser Gerido do iOS se o Profissional de TI definir esse requisito para uma aplicação**<br/>
Se tiver configurado um Web Clip para ser aberto apenas no browser gerido e este não estiver instalado num dispositivo, a aplicação Portal da Empresa irá pedir ao utilizador para instalar o browser gerido antes de poder instalar o Web Clip.
<!---TFS 1228570--->

### Windows
**Botão de feedback adicionado à aplicação Portal da Empresa para Windows 8.1**<br/>
A aplicação Portal da Empresa para Windows 8.1 permite que os utilizadores finais enviem feedback sobre a aplicação através do novo botão "enviar feedback". Para localizar o botão, os utilizadores têm de tocar no menu de "três pontos"que se encontra no canto inferior direito do ecrã da aplicação Portal da Empresa e, em seguida, tocar em **enviar feedback**. O feedback recolhido é anónimo e irá ajudar a Microsoft a melhorar a experiência da aplicação Portal da Empresa para os utilizadores.
<!---TFS 1317806--->

## Glossário do Intune</br>
Adicionámos um novo [tópico de glossário](https://docs.microsoft.com/intune/understand-explore/intune-glossary) à biblioteca para o ajudar a compreender alguns dos termos utilizados no produto Intune.

----------

## Novidades futuras

### Transição dos Grupos do Intune para os Grupos do Azure Active Directory
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

### Novas políticas de Acesso Condicional da aplicação para o Exchange Online e SharePoint Online
Poderá restringir o acesso ao Exchange Online e ao SharePoint Online de modo a permitir o acesso apenas a partir de aplicações do Office para dispositivos móveis, como o Outlook, o Word, o Excel e o OneDrive. Esta nova funcionalidade é totalmente compatível com a gestão de aplicações para dispositivos móveis do Intune (MAM), uma vez que pode bloquear o acesso a clientes de e-mail incorporados ou a outras aplicações que não tenham sido configuradas com as políticas MAM do Intune. Isto garante que os seus utilizadores acedem aos dados da sua organização através de aplicações que podem ser protegidas pelos serviços de MAM do Intune. Pode começar a utilizar a gestão de aplicações para dispositivos móveis do Intune através do portal do Azure. Localize a nova secção Acesso Condicional no painel "Definições".


### Depreciação de serviço

- **As aplicações do Portal da Empresa para Windows 8 e Windows Phone 8 vão ser preteridas** <br/>
A partir de outubro de 2016, o Microsoft Intune irá preterir o suporte para aplicações Windows 8 e Windows Phone 8 do Portal da Empresa. O Microsoft Intune irá também preterir o suporte para a plataforma do Windows Phone 8. Como resultado, não será capaz de inscrever ou atualizar dispositivos Windows Phone 8. Pode continuar a gerir dispositivos Windows Phone 8 e Windows 8 que já tenham sido inscritos. Atualize dispositivos Windows Phone 8 e Windows 8 para Windows Phone 8.1 e Windows 8.1, e utilize as aplicações do Portal da Empresa para Windows 8.1 e Windows Phone 8.1 correspondentes para continuar a distribuir aplicações para estes dispositivos, sem interrupções.

### Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](http://www.microsoft.com/en-us/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Versões anteriores do Intune](previous-intune-releases.md)



<!--HONumber=Sep16_HO5-->


