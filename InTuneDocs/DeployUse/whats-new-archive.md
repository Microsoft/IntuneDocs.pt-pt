---
title: Arquivo de novidades | Microsoft Intune
description: 
keywords: 
author: Lindavr
manager: angrobe
ms.date: 07/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ed2db991-4729-49a7-a1e6-be2ffa0d03d1
ROBOTS: noindex,nofollow
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: 458ee268d0c6a8fa6cbe6cc23ad07f0e45eff3e5


---
## Dezembro de 2015
### Alterações e atualizações do Portal da Empresa da Microsoft
As seguintes alterações foram efetuadas no Portal da Empresa nesta versão:

**Aplicação do Portal da Empresa para Android**

As seguintes alterações foram efetuadas para cumprir os novos requisitos da Google. Nos dispositivos Android 6.0 e superior, duas novas mensagens são apresentadas aos utilizadores:
* Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?
* Permitir que o Portal da Empresa aceda às fotografias, multimédia e ficheiros no seu dispositivo?

Consulte as tabelas seguintes para obter detalhes acerca destas duas mensagens.



Texto da mensagem  |Permitir que o Portal da Empresa efetue e faça a gestão de chamadas telefónicas?  
---------|---------
Significado da mensagem     |  Permite que o número de telefone e o IMEI do dispositivo do utilizador sejam enviados para o serviço Intune e apresentados na consola de Administração, na página de Hardware.   </br></br>**NOTA: a aplicação Portal da Empresa nunca efetua ou gere chamadas telefónicas!** O texto da mensagem é controlado pelo Google e não pode ser alterado. </br></br>Para ver a página **Hardware**, aceda a **Grupos** > **Todos os dispositivos móveis** > **Dispositivos**. Selecione o dispositivo do utilizador e aceda a **Ver Propriedades** > **Hardware**.    
Onde e quando é apresentada a mensagem  | A mensagem é apresentada quando os utilizadores iniciam sessão na aplicação do Portal da Empresa pela primeira vez para iniciar a inscrição do dispositivo.|         
O que acontece se os utilizadores permitirem o acesso  |  O número de telefone e o IMEI do dispositivo serão apresentados na página de Hardware na consola de Administração. |         
O que acontece se os utilizadores recusarem o acesso     | Podem continuar a utilizar a aplicação do Portal da Empresa e inscrever o respetivo dispositivo, mas o número de telefone e o IMEI do dispositivo do cliente estará em branco na página de Hardware da consola de Administração.       </br></br> Na segunda vez que os utilizadores iniciam sessão na aplicação Portal da Empresa após negarem o acesso, a mensagem mostra uma caixa de verificação **Não voltar a perguntar**, que os utilizadores podem selecionar para que a mensagem não volte a aparecer.</br></br>Se os utilizadores permitirem o acesso, mas o negarem mais tarde, a mensagem é apresentada quando os utilizadores iniciarem sessão novamente na aplicação do Portal da Empresa depois da inscrição.</br></br>Se, posteriormente, os utilizadores decidirem permitir o acesso, podem aceder a **Settings (Definições)** > **Apps (Aplicações)** > **Company Portal (Portal da Empresa)** > **Permissions (Permissões)** > **Phone (Telemóvel)** e, em seguida, ativar a permissão.
Mais informações     |  Para os seus utilizadores: [Iniciar sessão no Portal da Empresa](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_signin_cp)  </br></br>Para Profissionais de TI: a informação contida nesta tabela também se encontra em [Ajudar os utilizadores a compreender as mensagens da aplicação Portal da Empresa](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   

Texto da mensagem  |Permitir que o Portal da Empresa aceda às fotografias, multimédia e ficheiros no seu dispositivo?  
---------|---------
Significado da mensagem     |  Permite que o dispositivo escreva registos de dados no cartão SD do dispositivo, permitindo que os registos sejam movidos com um cabo USB.   </br></br>**NOTA: a aplicação Portal da Empresa nunca acede a multimédia, ficheiros e fotografias dos utilizadores!** O texto da mensagem é controlado pelo Google e não pode ser alterado.     
Onde e quando é apresentada a mensagem  | A mensagem é apresentada quando os utilizadores tocam em **Enviar Dados**, para enviar registos de dados ao seu administrador de TI.|         
O que acontece se os utilizadores permitirem o acesso  |  Os registos serão copiados para o cartão SD. |         
O que acontece se os utilizadores recusarem o acesso     | Podem ainda enviar registos de dados, mas os registos não serão copiados para o cartão SD do dispositivo.       </br></br> Na segunda vez que os utilizadores iniciam sessão na aplicação Portal da Empresa após negarem o acesso, a mensagem mostra uma caixa de verificação **Não voltar a perguntar**, que os utilizadores podem selecionar para que a mensagem não volte a aparecer.</br></br>Se os utilizadores permitirem o acesso, mas o negarem mais tarde, a mensagem é apresentada quando os utilizadores tentarem enviar registos.</br></br>Se, posteriormente, os utilizadores decidirem permitir o acesso, podem aceder a **Settings (Definições)** > **Apps (Aplicações)** > **Company Portal (Portal da Empresa)** > **Permissions (Permissões)** > **Storage (Armazenamento)** e, em seguida, ativar a permissão.
Mais informações     |  Para os seus utilizadores: [Enviar registos de dados de diagnóstico ao administrador de TI por e-mail](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_send_diag_logs)  </br></br>Para Profissionais de TI: a informação contida nesta tabela também se encontra em [Ajudar os utilizadores a compreender as mensagens da aplicação Portal da Empresa](https://technet.microsoft.com/library/dn948527.aspx#BKMK_help_users_understd_msgs)   


**Aplicação Portal da Empresa para iOS**
* Os utilizadores podem agora utilizar o Microsoft Outlook ou outras aplicações de e-mail para enviarem registos de diagnóstico para o administrador de TI. Anteriormente, só era possível utilizar a aplicação nativa.
* O suporte de dispositivos inscritos pela empresa e do Programa de Inscrição de Dispositivos (DEP) da Apple foi melhorado. Para detalhes, consulte [É-lhe pedido para identificar o seu dispositivo quando está a tentar inscrever-se](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_id_your_device).
* Na lista de dispositivos inscritos do utilizador aparece agora uma marca de verificação verde junto ao dispositivo que o utilizador está atualmente a utilizar. Antes de esta marca de verificação ser adicionada, os utilizadores não conseguiam saber qual era o dispositivo inscrito que estavam a utilizar.

**Aplicação do Portal da Empresa do Windows**

A Microsoft recolhe automaticamente dados anónimos sobre o desempenho e a utilização do portal da empresa para melhorar os produtos e serviços Microsoft. Os utilizadores finais podem desativar a recolha de dados através da definição Dados de Utilização nos respetivos dispositivos, mas os administradores não têm qualquer controlo sobre a recolha de dados e não podem alterar a seleção do utilizador final para esta definição.



## Novembro de 2015
### Gestão de aplicações
O Intune suporta políticas de gestão de aplicações móveis (MAM) que ajudam a impedir a divulgação de dados empresariais para aplicações ou serviços de consumidor. Historicamente, estas políticas apenas eram impostas em aplicações móveis em execução em dispositivos que também estavam inscritos para gestão de dispositivos móveis (MDM) no Intune.

Com a atualização deste mês, o Intune está a expandir as suas capacidades MAM para novas classes de dispositivos. Para além dos dispositivos inscritos no Intune, pode agora impor políticas MAM em:
* dispositivos geridos por outra solução de gestão de dispositivos móveis (MDM)
* dispositivos que não estão inscritos em qualquer sistema de gestão de dispositivos, normalmente dispositivos BYOD (Bring Your Own Device)

Pode encontrar mais informações sobre estas novas capacidades MAM nas seguintes mensagens de blogue:
* [Enhancing managed mobile productivity](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)
* [Announcing new Microsoft Enterprise Mobility capabilities](http://blogs.technet.com/b/microsoftintune/archive/2015/11/17/enhancing-managed-mobile-productivity.aspx)

Além disso, seguem-se alguns destaques e informações adicionais sobre as funcionalidades MAM do Intune:
* Os dados empresariais são isolados dos dados de consumidor nas aplicações otimizadas para o Intune, incluindo aplicações do Office Mobile, aplicações de terceiros que adotaram o Intune SDK ou aplicações de linha de negócio cobertas pelo Intune.
* Os dados empresariais podem ser partilhados (**cortar/copiar/colar**) em todas as aplicações da empresa, impedindo simultaneamente a partilha dos dados da empresa em aplicações pessoais. Leia o tópico [Como é que as políticas de MAM protegem os dados das aplicações](https://technet.microsoft.com/library/mt627825.aspx) para obter mais detalhes. Este cenário de exemplo, [Utilizar a aplicação do Microsoft Word para tarefas pessoais e de trabalho](https://technet.microsoft.com/library/mt627827.aspx), mostra como é impedida a partilha de dados da empresa em aplicações pessoais.
* Políticas de prevenção de perda de dados chave, como PINs por aplicação, controlos de salvaguarda e partilha de dados geridos entre aplicações. Leia o tópico [Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx) para ver uma lista de todas as políticas.
* O Word, o Excel, o PowerPoint, o Outlook, o OneNote e o OneDrive para Empresas têm estas novas capacidades e podem ser geridos com e sem a inscrição de dispositivos. As capacidades de proteção contra perda de dados estão nativamente incorporadas nas aplicações Office padrão da Apple Store ou da Google Play Store e não necessitam de sideloading ou de encapsulamento de aplicações.
* Para saber como começar, consulte o tópico [Introdução às políticas de gestão de aplicações móveis no portal do Azure](https://technet.microsoft.com/library/mt627830.aspx). Para saber como configurar e implementar políticas de gestão de aplicações móveis, consulte [Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx).
* Quando os utilizadores finais efetuam a autenticação na aplicação com as respetivas credenciais de empresa, as capacidades de proteção contra perda de dados são configuradas automaticamente. O tópico [Experiência do utilizador final para aplicações associadas a políticas de gestão de aplicações móveis do Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx) inclui alguns cenários de exemplo para aceder ao OneDrive em dispositivos iOS e Android.
* Funciona em dispositivos Android e iOS.

A lista de [Aplicações da Microsoft que pode utilizar com políticas de gestão de aplicações móveis do Microsoft Intune](https://technet.microsoft.com/library/dn708489.aspx) foi atualizada para apresentar as aplicações mais recentes.

### Gestão de dispositivos
 **Gestão de dispositivos Mac OS X** Com o Intune, pode agora inscrever e gerir dispositivos Mac OS X. Pode efetuar o seguinte com os dispositivos Mac OS X:
* Inscrever dispositivos para serem geridos pelo Intune. Consulte [Configurar a gestão de iOS e Mac com o Microsoft Intune](https://technet.microsoft.com/library/dn408185.aspx).
* Controlar as definições do dispositivo com uma política de configuração geral. Consulte [Definições de política de configuração do Mac OS X no Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx).
* Implementar as definições de Mac OS X que criou com o Apple Configurator. Consulte [Definições de política personalizada do Mac OS X no Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx).
* Recolher inventário de hardware e software a partir de dispositivos Mac OS X. Consulte [Compreender os seus dispositivos com o inventário no Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx).
* Executar os novos relatórios que apresentam detalhes sobre os dispositivos Mac OS X que gere. Consulte [Compreender as operações do Microsoft Intune através de relatórios](https://technet.microsoft.com/library/dn646977.aspx).

**Novas definições do browser Edge para dispositivos Windows 10** Foram adicionadas novas definições à política de configuração geral do Windows 10, que permitem gerir definições e funcionalidades do browser Microsoft Edge. Consulte [Definições de política de configuração do Windows 10 no Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx).

**Perfis de e-mail** Foi adicionada uma nova política de perfis de e-mail para o ambiente de trabalho do Windows 10 e dispositivos móveis Windows 10. Consulte [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](https://technet.microsoft.com/library/dn646984.aspx).

**Novas definições de política de conformidade** As novas definições de política de sistema e segurança que se seguem foram adicionadas à lista de políticas de conformidade:
* Para se certificar de que os dispositivos Windows 8.1 ou posteriores que acedem aos recursos da sua empresa têm as atualizações mais recentes instaladas, utilize a definição **Ativar atualizações automáticas**. Também pode especificar o tipo de atualizações a instalar automaticamente: instalar todas as atualizações marcadas como importantes ou todas as atualizações marcadas como importantes ou recomendadas. Para ver a lista completa de definições de políticas de conformidade, consulte [Gerir políticas de conformidade de dispositivos para o Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx).
* A nova definição **Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo**, combinada com a definição existente **Minutos de inatividade antes da palavra-passe ser exigida**, permite-lhe criar uma definição de conformidade que requer que o utilizador final introduza uma palavra-passe para utilizar um dispositivo que está inativo há um determinado período de tempo.

**Novas opções de política de acesso condicional** Pode aplicar políticas de acesso condicional a **todos os utilizadores** em políticas de acesso condicional novas ou existentes. Todos os utilizadores que possuem licenças do Intune e do Office 365 serão obrigados a inscrever os respetivos dispositivos e, se a plataforma do dispositivo não for suportada pelo Intune, o acesso é bloqueado para as aplicações cliente que utilizem o [Início de sessão baseado em autenticação do Active Directory (autenticação moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/).

Também pode especificar que a política de acesso condicional é aplicável a **todas as plataformas**.  Qualquer aplicação cliente que utilize a [início de sessão baseado em autenticação do Active Directory (autenticação moderna)](https://blogs.office.com/2014/11/12/office-2013-updated-authentication-enabling-multi-factor-authentication-saml-identity-providers/) está sujeita à política de acesso condicional e, se a plataforma não for suportada pelo Intune, será bloqueada.

### Alterações e atualizações do Portal da Empresa da Microsoft
As seguintes alterações foram efetuadas às aplicações do portal da empresa nesta versão:

* **Android**: um ecrã de boas-vindas foi adicionado à aplicação Portal da Empresa para Android, para ajudar os utilizadores a compreenderem a finalidade da aplicação Portal da Empresa. Este ecrã visa reduzir as transferências da aplicação por utilizadores cujas empresas não sejam subscritores do Intune.

* **iOS**: o Intune suporta agora a inscrição de dispositivos Mac OS X através do [site do Portal da Empresa](https://portal.manage.microsoft.com). Para instruções, consulte [Inscrever o dispositivo Mac OS X no Intune](https://technet.microsoft.com/library/mt598622.aspx).

* **Site do Portal da Empresa**: os utilizadores que tenham inscrito os respetivos dispositivos no Intune podem agora repor o seu código de acesso através da opção **Repor Código de Acesso** no site do Portal da Empresa. Anteriormente, apenas os administradores de TI podiam repor códigos de acesso dos utilizadores. A opção Repor Código de Acesso não é suportada em dispositivos com o Windows 8.1 e Windows RT e a opção é apresentada apenas quando os dispositivos estão inscritos na gestão de dispositivos móveis (MDM) ou MDM com o Exchange ActiveSync. Para instruções, consulte [Repor o código de acesso](https://technet.microsoft.com/library/mt590895.aspx).

### Alterações ao licenciamento Administradores Globais
Em outubro, partilhámos que os Administradores Globais (também designados por Administradores Inquilinos) podiam continuar a realizar tarefas diárias de administração sem uma licença separada do Intune ou do Enterprise Mobility Suite (EMS). No entanto, se os Administradores Globais pretenderem utilizar o serviço, como, por exemplo, para inscrever os seus próprios dispositivos, um dispositivo da empresa ou utilizar o Portal da Empresa do Intune, precisarão de uma licença do Intune ou do EMS como qualquer outro utilizador. Seguem-se alguns detalhes adicionais.
* O Portal da Empresa do Intune é o local onde os utilizadores finais podem:
    * inscrever os respetivos dispositivos
    * ver o estado dos respetivos dispositivos
    * transferir software que um Administrador Global tenha implementado na organização
    * localizar hiperligações publicadas pelo Administrador Global sobre como contactar o respetivo departamento de TI

    [Saiba mais sobre o Portal da Empresa](https://technet.microsoft.com/library/dn646966.aspx#BKMK_CompanyPortal) e sobre [formas de personalizar o Portal da Empresa](https://technet.microsoft.com/library/dn646983.aspx#BKMK_ConfigureCompanyPortal).
* A pessoa que se inscreve para comprar o Intune ou o EMS em nome de uma organização torna-se, automaticamente, no primeiro Administrador Global no seu inquilino. Este outono, o Intune começou a atribuir automaticamente uma licença do Intune ou do EMS a esse primeiro Administrador Global, como parte da transição para o [Portal do Office 365](http://portal.office.com/) e da extinção do [Portal de Contas do Intune](http://account.manage.microsoft.com/). Quaisquer outros Administradores Globais adicionados podem continuar a realizar tarefas diárias de administração sem uma licença separada do Intune ou do EMS. Agir como um utilizador final e inscrever o seu próprio dispositivo (ou da empresa) ou transferir software a partir do portal da empresa, desencadearia a necessidade de uma licença, tal como qualquer outro utilizador.
* A alteração será introduzida gradualmente e começará agora em janeiro de 2016.
* Para os Parceiros da Microsoft, esta alteração não deve afetar a capacidade de administrar o serviço em nome dos clientes. Para as tarefas do utilizador final, um utilizador terá de ter uma licença do Intune ou do EMS para inscrever um dispositivo e aceder ou transferir software a partir do Portal da Empresa.

Se tiver dúvidas em relação a esta alteração, pode contactar a equipa de suporte do Intune:
* [Canais de suporte do Microsoft Intune](https://technet.microsoft.com/library/jj839713.aspx)
* [Suporte da comunidade](https://social.technet.microsoft.com/Forums/en-US/home?forum=microsoftintuneprod)

Para comentários gerais sobre o Microsoft Intune, incluindo a apresentação de pedidos de alteração de design (DCRs) ou erros, visite o site [Intune user voice](https://microsoftintune.uservoice.com/).


### Novidades na documentação do Intune -- novembro de 2015
**Novo conteúdo**
* [Definições de política de configuração do Mac OS X no Microsoft Intune](https://technet.microsoft.com/library/mt627823.aspx): como controlar as definições e funcionalidades do dispositivo em dispositivos Mac OS X.
* [Definições de política personalizada do Mac OS X no Microsoft Intune](https://technet.microsoft.com/library/mt627820.aspx): como implementar definições de dispositivos Mac OS X criadas com a ferramenta Apple Configurator.
* [Configurar políticas de aplicações de prevenção de perda de dados com o Microsoft Intune](https://technet.microsoft.com/library/mt627825.aspx): contém informações sobre os cenários suportados por políticas de gestão de aplicações móveis e como funciona a política para proteger dados.
* [Introdução às políticas de gestão de aplicações móveis no portal do Azure](https://technet.microsoft.com/library/mt627830.aspx): do que necessita para começar a utilizar o portal de pré-visualização do Azure para políticas de gestão de aplicações móveis.
* [Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](https://technet.microsoft.com/library/mt627829.aspx): contém instruções passo a passo sobre como criar políticas de gestão de aplicações móveis no portal de pré-visualização do Azure .
* [Monitorizar políticas de gestão de aplicações móveis com o Microsoft Intune](https://technet.microsoft.com/library/mt627824.aspx): informações sobre como pode monitorizar as suas políticas de gestão de aplicações móveis no portal de pré-visualização do Azure.
* [Políticas de gestão de aplicações móveis do Microsoft Intune e iOS Open In](https://technet.microsoft.com/library/mt627821.aspx): informações sobre como funcionam as políticas de gestão de aplicações móveis com a funcionalidade iOS Open In.
* [Experiência do utilizador final para aplicações associadas a políticas de gestão de aplicações móveis do Microsoft Intune](https://technet.microsoft.com/library/mt627827.aspx): qual é a experiência do utilizador final ao utilizar aplicações associadas a uma política de gestão de aplicações móveis.
* [Eliminar dados de aplicações geridas pela empresa com o Microsoft Intune](https://technet.microsoft.com/library/mt627826.aspx): como pode remover os dados de aplicações da empresa.

**Conteúdo atualizado**
* [Definições de política de configuração do Windows 10 no Microsoft Intune](https://technet.microsoft.com/library/mt404697.aspx): foram adicionadas novas definições do browser Edge.
* [Configurar a gestão de iOS e Mac com o Microsoft Intune](http://technet.microsoft.com/library/dn408185.aspx): foram adicionadas informações sobre como inscrever dispositivos Mac OS X.
* [Compreender os seus dispositivos com o inventário no Microsoft Intune](https://technet.microsoft.com/library/jj733634.aspx): foram adicionadas informações sobre o inventário recolhido a partir de dispositivos Mac OS X. Além disso, o tópico foi atualizado com as informações mais recentes para todas as plataformas de dispositivos.
* [Compreender as operações do Microsoft Intune através de relatórios](https://technet.microsoft.com/library/dn646977.aspx): foram adicionadas informações sobre os dois novos relatórios utilizados para apresentar informações sobre os seus dispositivos Mac OS X geridos.
* [Gerir políticas de conformidade de dispositivos para o Microsoft Intune](https://technet.microsoft.com/library/dn705843.aspx): foram adicionadas informações sobre as novas políticas de conformidade para exigir atualizações automáticas e exigir uma palavra-passe quando um dispositivo regressa de um estado inativo.
* [Gerir o acesso ao e-mail com o Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx): foram adicionadas informações sobre a capacidade de aplicar a política de acesso condicional a todas as plataformas e a todos os utilizadores.
* [Gerir o acesso ao SharePoint Online com o Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx): foram adicionadas informações sobre a capacidade de aplicar a política de acesso condicional a todas as plataformas e a todos os utilizadores.

## Outubro de 2015

### Atualizações ao acesso condicional para o Exchange no local
**Agora, pode permitir o acesso ao e-mail do Exchange Active Sync para dispositivos compatíveis inscritos no Intune quando a regra global do Exchange está definida como bloquear ou colocar em quarentena** Até agora, para permitir o acesso ao e-mail em dispositivos inscritos e conformes, era necessário definir a regra global predefinida do Exchange para **Permitir**.

Com esta atualização de serviço, esta definição já não é um requisito de acesso condicional. Se o seu ambiente do Exchange exigir que a regra global predefinida seja estabelecida para **Bloquear/Quarentena**, basta selecionar a caixa de verificação **Substituição da Regra Predefinida** na página da política de acesso condicional do Exchange no local. O tópico [Gerir o acesso ao e-mail com o Microsoft Intune](https://technet.microsoft.com/library/dn705841.aspx) inclui mais detalhes sobre as regras e as notificações de utilizador final resultantes.

**Nova experiência de quarentena de um só clique** Simplificámos a experiência de e-mail de quarentena para permitir a inscrição num só clique. Com esta atualização de serviço, os utilizadores finais podem clicar numa única ligação no e-mail de quarentena para concluir o processo de inscrição na aplicação do portal da empresa.
### Atualizações de gestão de aplicações e dispositivos móveis
**Android** Todas as funcionalidades de gestão do Intune suportam agora o Android 6.0 (Marshmallow), conforme descrito nesta mensagem de blogue: [Microsoft Intune Provides Day 0 Support for Android Marshmallow](http://blogs.technet.com/b/microsoftintune/archive/2015/10/09/microsoft-intune-to-provide-day-0-support-for-android-marshmallow.aspx).

**iOS** Já não pode criar novas implementações de aplicações em dispositivos iOS com uma versão anterior ao iOS 7.1. Quaisquer implementações de aplicações existentes em dispositivos com uma versão anterior ao iOS 7.1 continuarão a funcionar e a ser geridas pelo Intune.

**Windows 10** O Intune suporta agora a implementação de aplicações do Windows 10 Universal com o tipo de instalador de software **Pacote de aplicações do Windows**. Para detalhes e requisitos, consulte [Introdução à implementação de aplicações no Microsoft Intune](http://technet.microsoft.com/en-US/library/dn646955.aspx).


### Alterações e atualizações de aplicações do Portal da Empresa da Microsoft
As seguintes alterações foram efetuadas às aplicações do portal da empresa nesta versão: **iOS** Foram adicionados novos botões à aplicação Portal da Empresa para tornar mais fácil para os utilizadores enviar registos de diagnóstico para os administradores de TI:

|Nome do botão|Onde aparece|
|------------|---------------|
|Relatório|Mensagens de alerta de erros|
|Enviar Relatório de Diagnóstico|Ecrã Acerca da aplicação Portal da Empresa|



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



<!--HONumber=Jul16_HO4-->


