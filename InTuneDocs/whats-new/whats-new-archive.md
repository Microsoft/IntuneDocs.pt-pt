---
title: Arquivo de novidades | Microsoft Intune
description: 
keywords: 
author: barlanmsft
manager: angrobe
ms.date: 10/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ec77bc20bf429c804cb502bb46fc549d080a94ac
ms.openlocfilehash: 14698e5f40e76e370e178aeb6187d89fbc5cb2bd


---
## Setembro de 2016
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
* Utilize a opção **Obter Ajuda** para denunciar problemas relacionados com o Portal da Empresa ao seu departamento de TI. O departamento de TI criará um e-mail com o seu cliente de e-mail e anexará os registos do Portal da Empresa ao mesmo. A opção **Obter Ajuda** substitui a funcionalidade **Enviar Dados** na página **Definições**.
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



<!--HONumber=Oct16_HO2-->


