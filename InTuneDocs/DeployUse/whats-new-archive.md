---
title: Novidades | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 779127bfd39145010f0d9b6609286aaf4dedfdc8
ms.openlocfilehash: 051d06afb0f29f2a97c1f06dc1102138e5f2be8f


---


## Setembro de 2015
### Atualizações de gestão de aplicações e dispositivos móveis
**Todas as funcionalidades de gestão de iOS suportam agora o iOS 9** Para obter detalhes sobre as capacidades de gestão do iOS 9, consulte [esta mensagem de blogue](http://blogs.technet.com/b/microsoftintune/archive/2015/09/09/day-zero-support-for-ios-9-with-intune.aspx).

**Nova política de configuração de aplicações móveis para iOS** Utilize a nova política de configuração de aplicações móveis para fornecer automaticamente definições de que uma aplicação iOS possa precisar quando for executada. Por exemplo, pode fornecer uma porta de rede ou um nome de utilizador. Para obter detalhes, consulte [Configurar aplicações com políticas de configuração de aplicações móveis no Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx).

**Gestão de aplicações mais simples para utilizadores do iOS 9**
 Nesta versão, pode colocar aplicações já implementadas sob a gestão do Intune para utilizadores do iOS 9. Para versões anteriores do iOS, quando implementar uma aplicação e se uma versão não gerida da aplicação estiver já instalada num dispositivo, tem de pedir ao utilizador que desinstale a aplicação manualmente antes de o Intune poder instalar a aplicação gerida.

 Mas começando com esta versão do Intune, pode agora pedir aos utilizadores de dispositivos iOS 9 que permitam que o Intune assuma a gestão da aplicação e aplique quaisquer políticas de gestão de aplicações móveis relevantes.

 **Gestão do Windows 10** Utilize a nova [política de configuração geral do Windows 10](https://technet.microsoft.com/library/mt404697.aspx) para configurar a palavra-passe, o dispositivo, o browser e outras definições para dispositivos inscritos com o Windows 10 e o Windows 10 Mobile.

 **Criar e implementar aplicações em dispositivos Windows 10 inscritos** Um novo tipo de instalador de software, o Windows Installer através de MDM (&#42;.msi), permite criar e implementar aplicações do Windows Installer em dispositivos inscritos com o Windows 10. Para obter detalhes, consulte [Introdução à implementação de aplicações no Microsoft Intune](https://technet.microsoft.com/library/dn646955.aspx).

### Alterações e atualizações de aplicações do Portal da Empresa da Microsoft
As seguintes alterações foram efetuadas às aplicações do portal da empresa nesta versão:

**iOS**
* A Microsoft recolhe automaticamente dados anónimos sobre o desempenho e a utilização do portal da empresa para melhorar os produtos e serviços Microsoft. Os utilizadores finais podem desativar a recolha de dados através da definição Dados de Utilização nos respetivos dispositivos, mas os administradores não têm qualquer controlo sobre a recolha de dados e não podem alterar a seleção do utilizador final para esta definição.
* Suporte de resolução de ecrã inteiro no iPhone 6 e 6 Plus
* Correções de erros para melhorar a segurança

### Documentação das novidades do Intune -- setembro de 2015
**Novos tópicos**

|Nome|Detalhes|
|----|--------|
|[Definições de política de configuração do Windows 10 no Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx)|Esta é uma nova política de configuração que lhe permite gerir as definições e as funcionalidades nos dispositivos com o Windows 10 e o Windows 10 Mobile.
| [Configurar aplicações com as políticas de configuração de aplicações móveis no Microsoft Intune](https://technet.microsoft.com/library/mt481447.aspx)|Trata-se de um novo tipo de política que permite fornecer automaticamente definições que poderão ser necessárias quando o utilizador executar uma aplicação do iOS. |

**Tópicos atualizados**

|Nome|Detalhes|
|----|-------|
|[Utilizar políticas para gerir computadores e dispositivos móveis com o Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx)|Atualizado para incluir as informações mais recentes para ajudá-lo a compreender e criar políticas.|

## Agosto de 2015
### Atualizações de gestão de aplicações e dispositivos móveis
* Os**Termos e condições** da inscrição no Intune e acesso da empresa são [agora geridos através de políticas](https://technet.microsoft.com/library/mt405893.aspx). Pode segmentar diferentes conjuntos de termos e condições para satisfazer requisitos de grupos de utilizadores específicos. Por exemplo, pode implementar os termos e condições em idiomas diferentes para grupos de utilizadores geograficamente definidos. Também pode [editar os termos e condições](https://technet.microsoft.com/library/mt405893.aspx#BKMK_TCVers) e especificar se os números de versão devem ser incrementados, o que obriga os utilizadores a concordar com os novos termos e condições antes de poderem utilizar o portal da empresa.
* **Há uma série de políticas do Intune cujo nome foi mudado** para os tornar mais consistentes no âmbito do produto e facilitar a sua localização. Para obter uma lista de todas as políticas do Intune disponíveis, consulte [Utilizar políticas para gerir computadores e dispositivos móveis com o Microsoft Intune](https://technet.microsoft.com/library/dn743712.aspx).
* Os **Perfis de Certificado PKCS #12 (.PFX)** estão disponíveis para Android 4.0 ou posterior e Windows 10 (ambiente de trabalho e dispositivos móveis) e posterior. A utilização de .PFX não precisa de um servidor NDES. Saiba como utilizar perfis de certificado .PFX em [Ativar o acesso a recursos da empresa através de perfis de certificados com o Microsoft Intune](http://technet.microsoft.com/library/dn818904.aspx)
* As **definições de limites empresariais para Windows 10 Desktop e Mobile** ativam as definições de VPN granulares, conforme descrito em [Ajudar os utilizadores a estabelecer uma ligação com o respetivo trabalho através de perfis da VPN com o Microsoft Intune](https://technet.microsoft.com/library/dn818905.aspx)
* **A aplicação OneDrive para Android suporta agora várias identidades**. Esta e outras atualizações às políticas de gestão de aplicações móveis são descritas na [lista de aplicações Microsoft que pode gerir](https://technet.microsoft.com/library/dn708489.aspx).
* **Ignorar Bloqueio de Ativação de iOS**. Se os dispositivos iOS da empresa estiverem protegidos pelo Bloqueio de Ativação, tem de introduzir o Apple ID e a palavra-passe do utilizador antes de poder eliminar ou reativar o dispositivo. Isto pode apresentar um desafio quando os utilizadores saem da empresa e devolvem um dispositivo da empresa sem desativar a Ativação de Bloqueio. Para ajudar a resolver este problema, pode utilizar a [Desativação de Bloqueio de Ativação do Intune](https://technet.microsoft.com/library/mt414176.aspx)

### Acesso condicional para PCs
Agora, pode configurar políticas de acesso condicional para PCs. Isto permite o acesso das aplicações de ambiente de trabalho do Office aos serviços online do SharePoint e Exchange Online.
Para ativar a política de acesso condicional para PCs, o PC tem de estar associado a um domínio ou estar em conformidade.
* Consulte a secção **Introdução** em [Gerir o acesso ao e-mail e ao SharePoint com o Microsoft Intune](http://technet.microsoft.com/library/dn818907).aspx) para obter a lista completa de requisitos para ativar o acesso condicional em PCs.
* Consulte [Gerir o acesso ao e-mail com o Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) para conhecer as opções que pode definir para ativar o acesso condicional ao e-mail.
* Consulte [Gerir o acesso ao SharePoint Online com o Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx) para conhecer as opções que pode definir para ativar o acesso condicional ao SharePoint Online.

### Alterações e atualizações de aplicações do Portal da Empresa da Microsoft
As seguintes alterações foram efetuadas às aplicações do portal da empresa nesta versão:

**Android**

Agora, os utilizadores passam a ver as instruções de inscrição dos dispositivos depois de iniciarem sessão se ainda não tiverem inscrito os respetivos dispositivos para gestão.

### Novidades na documentação do Intune -- Agosto de 2015
**Novos tópicos**

|Título|Detalhes|
|-----|-------|
|[Ajudar a proteger dispositivos iOS desativando o Bloqueio de Ativação para o Microsoft Intune](https://technet.microsoft.com/library/mt414176.aspx)|Saiba como utilizar o Intune de modo a ignorar o Bloqueio de ativação de iOS quando um utilizador sai da empresa e devolve um dispositivo bloqueado.|

**Tópicos atualizados**

|Título|Detalhes|
|-----|-------|
|[Aplicações da Microsoft que pode utilizar com políticas de gestão de aplicações móveis do Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx)|Atualizado com as informações mais recentes sobre as aplicações que podem ser geridas com políticas de gestão de aplicações móveis.
|[Utilizar políticas para gerir computadores e dispositivos móveis com o Microsoft Intune](http://technet.microsoft.com/library/dn743712.aspx)|Atualizado com as políticas mais recentes adicionadas ao Intune.|
<!---
## July 2015
July updates for Intune are limited to behind-the-scenes enhancements that allow us to continue providing you with a high-quality service experience. New features are not included in this service update.

### Intune Onboarding benefit
Microsoft offers the Intune Onboarding benefit for eligible plans. The Onboarding benefit lets you work remotely with Microsoft specialists to get your Intune environment ready for use. For more information, see [Microsoft Intune Onboarding benefit description](https://technet.microsoft.com/library/mt228266.aspx)
### Changes and updates to Microsoft Company Portal apps
The following changes have been made to the company portal apps in this release.

**Android**

Microsoft automatically collects anonymous data about the performance and use of the company portal to improve Microsoft products and services. End users can turn off data collection by using the Usage Data setting on their device, but administrators have no control over the data collection and cannot change the end user’s selection for this setting.--->



<!--HONumber=Jun16_HO4-->


