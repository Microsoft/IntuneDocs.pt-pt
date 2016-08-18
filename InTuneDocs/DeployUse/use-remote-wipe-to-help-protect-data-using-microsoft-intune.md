---
title: "Utilizar a eliminação remota para ajudar a proteger dados | Microsoft Intune"
description: "O Intune fornece capacidades de eliminação seletiva e completa para remover dados confidenciais da empresa e remover o acesso a vários recursos da empresa."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 8519e411-3d48-44eb-9b41-3e4fd6a93112
ms.reviewer: lancecra
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: dcfa3af374a7e64e931508e1a8022bf8a50c71a7
ms.openlocfilehash: a09c9b55d7906ab792bda90b172a36b3656ed6dd


---

# Ajudar a proteger os dados com a eliminação completa ou seletiva através do Microsoft Intune
Se pelo facto de um dispositivo já não ser necessário, estar a ser reaproveitado ou ter sido perdido, pode eliminar as aplicações e os dados dos dispositivos geridos com o Intune. Para tal, o Intune fornece as funcionalidades de eliminação completa e eliminação seletiva. Além disso, os utilizadores podem emitir um comando de eliminação remota de dados no dispositivo a partir do Portal da Empresa do Intune em dispositivos de propriedade privada inscritos no Intune.

  > [!NOTE]
  > Este tópico aborda apenas a eliminação de dispositivos geridos pela gestão de dispositivos móveis do Intune. Também pode utilizar o [portal de pré-visualização do Azure](https://portal.azure.com) para [apagar dados da empresa das aplicações](wipe-managed-company-app-data-with-microsoft-intune.md). Também pode [extinguir computadores geridos com o software de cliente Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client#retire-a-computer.md).

## Eliminação completa

A **Eliminação completa** restaura as predefinições do dispositivo, removendo todos os dados e definições da empresa e do utilizador. O dispositivo é removido do Intune. A eliminação completa é útil para repor um dispositivo antes de o atribuir a um novo utilizador ou em caso de perda ou roubo do dispositivo.  **Seja cuidadoso com a seleção da eliminação completa. Não é possível recuperar os dados no dispositivo**.


> [!Warning]
> A eliminação pode fazer com que os dispositivos Windows 10 RTM (ou seja, mais dispositivos anteriores ao Windows 10 versão 1511) com menos de 4 GB de RAM fiquem inacessíveis. Para aceder a um dispositivo Windows 10 que deixou de responder, pode arrancá-lo a partir de uma unidade USB ou com outra solução semelhante.

### Apagar remotamente um dispositivo a partir da consola do administrador do Intune

1.  Selecione dispositivos a serem apagados. Pode encontrá-los através do utilizador ou do dispositivo.

    -   **Por utilizador:**

        1.  Na [consola de administrador do Intune](https://manage.microsoft.com/), escolha **Grupos** &gt; **Todos os Utilizadores**.

        2.  Escolha o nome do utilizador cujo dispositivo móvel pretende apagar. Escolha **Ver Propriedades**.

        3.  Na página **Propriedades** do utilizador, escolha **Dispositivos** e, em seguida, escolha o nome do dispositivo móvel que pretende apagar. Utilize Ctrl + clique para selecionar vários dispositivos.

    -   **Por dispositivo:**

        1.  Na [consola de administrador do Intune](https://manage.microsoft.com/), escolha **Grupos** &gt; **Todos os Dispositivos Móveis**.

      ![Iniciar uma operação de extinção ou eliminação de dados](../media/dev-sa-wipe.png)

        2.  Escolha **Dispositivos** e, em seguida, escolha o nome do dispositivo móvel que pretende apagar. Utilize Ctrl + clique para selecionar vários dispositivos.

2.  Escolha **Extinguir/Apagar**.

3.  É apresentada uma mensagem que lhe pede para confirmar se pretende extinguir o dispositivo.

    -   Para executar uma **Eliminação seletiva** que remova apenas as aplicações e dados da empresa, escolha **Sim**.

    -   Para efetuar uma **Eliminação completa** que apague todas as aplicações e dados e devolva o dispositivo às predefinições de fábrica, selecione **Apagar o dispositivo antes de o extinguir**. Esta ação aplica-se a todas as plataformas exceto ao Windows 8.1. **Não é possível recuperar os dados removidos por uma eliminação completa**.

Desde que o dispositivo esteja ativo e ligado, demora menos de 15 minutos até um comando de eliminação ser propagado em todos os tipos de dispositivo.

## Eliminação seletiva

A **eliminação seletiva** remove os dados da empresa, incluindo os dados de gestão de aplicações móveis (MAM) onde for aplicável, definições e perfis de e-mail de um dispositivo. A eliminação seletiva mantém os dados pessoais do utilizador no dispositivo. O dispositivo é removido do Intune. As tabelas seguintes descrevem os dados que são removidos e o efeito nos dados que permanecem no dispositivo após uma eliminação seletiva, por plataforma.

**iOS**

|Tipo de dados|iOS|
|-------------|-------|
|Aplicações da empresa e dados associados instalados pelo Intune.|As aplicações são desinstaladas. Os dados da aplicação da empresa são removidos.<br /><br />Os dados de aplicações da Microsoft que utilizam a gestão de aplicações móveis são removidos. A aplicação não é removida.|
|Definições|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidas|
|Definições de perfil de certificado|Certificados removidos e revogados.|
|Agente de Gestão|O perfil de gestão é removido.|
|E-mail|Os perfis de e-mail aprovisionados através do Intune são removidos e o e-mail em cache no dispositivo é eliminado.|
|Anulação da associação ao Azure Active Directory (AAD)|Registo do ADD removido|
|Contactos | Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos.  Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. <br /> <br />Atualmente, apenas o Outlook é suportado.

**Android**

|Tipo de dados|Android|Android Samsung KNOX|
|-------------|-----------|------------------------|
|Ligações Web|Removidos.|Removidas|
|Aplicações não geridas do Google Play|As aplicações e os dados permanecem instalados|As aplicações e os dados permanecem instalados|
|Aplicações de linha de negócio não geridas|As aplicações e os dados permanecem instalados|As aplicações são desinstaladas e, como resultado, os dados locais da aplicação são removidos. Não foram removidos dados fora da aplicação (cartão SD, etc.)|
|Aplicações geridas do Google Play|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (cartão SD, etc.) permanecem encriptados e inutilizáveis, mas não são removidos.|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (cartão SD, etc.) permanecem encriptados mas não são removidos.|
|Aplicações de linha empresarial geridas|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (cartão SD, etc.) permanecem encriptados e inutilizáveis, mas não são removidos.|Os dados da aplicação são removidos. A aplicação não é removida. Os dados protegidos pela encriptação MAM fora da aplicação (cartão SD, etc.) permanecem encriptados e inutilizáveis, mas não são removidos.|
|Definições|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidas|Removidas|
|Definições de perfil de certificado|Certificados revogados mas não removidos.|Certificados removidos e revogados.|
|Agente de Gestão|O privilégio de Administrador de Dispositivos é revogado.|O privilégio de Administrador de Dispositivos é revogado.|
|E-mail|Os e-mails recebidos pela aplicação Microsoft Outlook para a aplicação Android são removidos.|Os perfis de e-mail aprovisionados através do Intune são removidos e o e-mail em cache no dispositivo é eliminado.|
|Anulação da associação ao Azure Active Directory (AAD)|Registo do ADD removido|Registo do ADD removido|
|Contactos | Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos.  Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. <br /> <br />Atualmente, apenas o Outlook é suportado.|Os contactos sincronizados diretamente da aplicação para o livro de endereços nativo são removidos.  Não é possível limpar contactos sincronizados do livro de endereços nativo para outra origem externa. <br /> <br />Atualmente, apenas o Outlook é suportado.

**Windows**

|Tipo de dados|Windows 8.1 (MDM) e Windows RT 8.1|Windows RT|Windows Phone 8 e Windows Phone 8.1|Windows 10|
|-------------|----------------------------------------------------------------|--------------|-----------------------------------------|--------|
|Aplicações da empresa e dados associados instalados pelo Intune.|Os ficheiros protegidos pelo EFS terão as respetivas chaves revogadas e o utilizador não poderá abrir os ficheiros.|Não remove aplicações da empresa.|As aplicações instaladas originalmente através do portal da empresa são desinstaladas. Os dados da aplicação da empresa são removidos.|As aplicações são desinstaladas e as chaves de sideload são removidas.|
|Definições|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|As configurações que foram definidas pela política do Intune já não são aplicadas e os utilizadores podem alterar as definições.|
|Definições de perfis de Wi-Fi e da VPN|Removidas|Removidas|Não suportado|Removidas|
|Definições de perfil de certificado|Certificados removidos e revogados.|Certificados removidos e revogados.|Não suportado|Certificados removidos e revogados.|
|E-mail|Remove o e-mail que que tenha o EFS ativado, que inclui a aplicação Correio para e-mail e anexos do Windows.|Não suportado|Os perfis de e-mail aprovisionados através do Intune são removidos e o e-mail em cache no dispositivo é eliminado.|Remove o e-mail que que tenha o EFS ativado, que inclui a aplicação Correio para e-mail e anexos do Windows. Remove as contas de e-mail que tenham sido aprovisionadas pelo Intune.|
|Anulação da associação ao Azure Active Directory (AAD)|Não|Não|Registo do ADD removido|Não aplicável. O Windows 10 não suporta a eliminação seletiva para dispositivos associados ao Azure Active Directory|

## Apagar conteúdo com o Sistema de Encriptação de Ficheiros (EFS) ativado
A eliminação seletiva de conteúdo encriptado com o EFS é suportada pelo Windows 8.1 e Windows RT 8.1. As seguintes informações aplicam-se a uma eliminação seletiva de conteúdo com o EFS ativado:

-   Apenas as aplicações e os dados protegidos pelo EFS através do mesmo domínio de Internet que a conta do Intune são apagados seletivamente. Para mais informações, consulte o artigo [Eliminação Seletiva do Windows para a Gestão de Dados de Dispositivos](http://technet.microsoft.com/library/dn486874.aspx).

-   Se forem efetuadas alterações ao domínio associado ao EFS, as alterações podem demorar até 48 horas antes de as aplicações e os dados que utilizam o novo domínio poderem ser apagados seletivamente.

-   Cada domínio registado no Intune será apagado.

As aplicações e os dados atualmente suportados pela eliminação seletiva com o EFS são:

-   Aplicação Correio para Windows

-   Pastas de Trabalho

-   Ficheiros e pastas encriptados pelo EFS. Para mais informações, consulte o artigo [Melhores práticas para o Sistema de Encriptação de Ficheiros](http://support.microsoft.com/kb/223316).

-   Se a sua organização manter a respetiva identidade no Active Directory, tem de utilizar a ferramenta Sincronização de Diretórios (DirSync) para sincronizar informações com o AAD para que a eliminação seletiva com o EFS funcione corretamente.  Para mais informações sobre o DirSync, consulte o tópico [Cenário de Sincronização de Diretórios](http://technet.microsoft.com/library/dn441212.aspx) na documentação do Azure Active Directory.

## Monitorizar as ações de extinção e eliminação
Para obter um relatório dos dispositivos que foram extintos, apagados ou eliminados e de quem efetuou a ação:

1.  Na [consola de administrador do Intune](https://manage.microsoft.com/), escolha **Relatórios** &gt; **Relatórios de Histórico de Dispositivos**.

2.  Forneça uma data de início e de fim para o relatório e, em seguida, escolha **Ver Relatório**.


### Consulte também
[Extinguir dispositivos](retire-devices-from-microsoft-intune-management.md)

[Windows Selective Wipe for Device Data Management (Eliminação Seletiva do Windows para Gestão de Dados do Dispositivo)](http://technet.microsoft.com/library/dn486874.aspx)



<!--HONumber=Aug16_HO1-->


