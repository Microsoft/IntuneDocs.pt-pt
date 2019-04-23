---
title: incluir ficheiro
description: incluir ficheiro
author: ErikjeMS
ms.service: microsoft-intune
ms.topic: include
ms.date: 03/28/2019
ms.author: erikje
ms.custom: include file
ms.openlocfilehash: 073115d33f9a4f22fe3706ef15860c2a8d8a68ee
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61513679"
---
Estes avisos fornecem importante de informações que podem ajudá-lo a se preparar para as funcionalidades e alterações futuras do Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Alterar inscrição fluxo de trabalho com o Portal da empresa do Intune em dispositivos iOS empresariais, a autenticação com o Assistente de configuração <!-- 1927359 -->
Há uma futura alteração ao fluxo de trabalho para a inscrição de dispositivos iOS através de um dos dispositivo da empresa métodos de inscrição da Apple - Apple Configurator, gerente de negócios da Apple, Apple School Manager ou o Apple dispositivo programa de inscrição (DEP), ao utilizar o programa de configuração Assistente para a autenticação. Esta alteração aplica-se apenas a dispositivos inscritos com afinidade do utilizador.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Quando esta alteração é implementada ~~Março~~ Abril, perfis de inscrição no Intune no portal do Azure serão atualizados para que pode especificar a forma como os dispositivos serão autenticados e se eles recebem a aplicação Portal da empresa. Haverá um fluxo de trabalho melhorado para inscrever dispositivos iOS através dos métodos indicados acima. 

- Quando inscrever novos dispositivos e a autenticação com o Assistente de configuração, poderá escolher se deve ou não implementar automaticamente a aplicação Portal da empresa. Os utilizadores finais já não verá a tela de "Identificar o dispositivo" e a tela de "Confirmar o seu dispositivo" no fluxo de inscrição.  
- Nos dispositivos já inscritos através do Assistente de configuração através de um dos métodos de inscrição de dispositivos da empresa da Apple, tem de tomar uma ação se pretender ativar o acesso condicional. Terá de configurar uma política de configuração de aplicação com um xml específico para enviar por push o Portal da empresa para estes dispositivos. Instruções para tal são na mensagem de blogue em ligação informações adicionais. Se optar por enviar por push o Portal da empresa, desta forma, os utilizadores finais já não verá a tela de "Identificar o dispositivo" e a tela de "Confirmar o seu dispositivo" no fluxo de inscrição. 
- Após esta alteração é implementada, se não tiver implementado o Portal da empresa com o perfil de configuração de aplicação mencionados acima e se a transferência dos utilizadores finais, a Portal da empresa a partir da aplicação da loja de aplicações, poderem iniciar sessão, mas irá receber uma mensagem de erro. Eles não será possível utilizar a aplicação para o acesso condicional. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Se pretender utilizar o fluxo de trabalho modificado, poderá ser útil atualizar a sua documentação de orientação do utilizador final para indicar que:

- Os utilizadores finais já não verá os dois ecrãs mencionados acima no fluxo de inscrição. 
- Precisam de iniciar sessão no Portal da empresa quando é implementada automaticamente e não baixá-lo a partir da app store. 

Pode optar por criar uma política de configuração de aplicações agora, se for necessário, em preparação para esta alteração. Quando este novo fluxo de trabalho for implementada, verá os perfis de inscrição atualizado na consola do. Podemos irá também informar sobre esta implementação através do Centro de mensagens. Depois disso, terá de executar a ação para que os utilizadores finais podem inscrever através do DEP ao autenticar com o Assistente de configuração e pode utilizar o Portal da empresa para o acesso condicional.

Consulte o nosso suporte postagem no blog em ligação informações adicionais para obter mais detalhes sobre esta alteração.

#### <a name="additional-information"></a>Informações Adicionais 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)

### <a name="plan-for-change-user-experience-update-to-intune-company-portal-app-for-ios"></a>Planear a alteração: Atualização da experiência de utilizador para a aplicação Portal da empresa do Intune para iOS
Temos o prazer partilhar que Intune em breve lançar uma atualização da experiência de utilizador principais para a aplicação Portal da empresa iOS. A atualização será apresentam uma reformulação visual da home page com filtros avançados e acesso mais rápido para aplicações e livros.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Esta experiência de utilizador atualizada, enquanto mantém iOS atual funcionalidade do Portal da empresa, funcionalidade:
- Uma home page com aspeto e funcionalidade do iOS nativo 
- Recursos de filtragem em listas de conteúdo e pesquisa, incluindo a capacidade de filtrar por tipo de conteúdo (aplicações ou e-Books) e a disponibilidade (gestão necessária ou disponível sem inscrição de dispositivos)
- Capacidade de pesquisar e-Books
- Histórico de pesquisas para aplicações e e-Books

Se é parte do programa TestFlight da Apple, será notificado sobre a versão de pré-lançamento do iOS atualizada do Intune aplicação Portal da empresa quando ela se tornar disponível. Se não tiver a parte do programa TestFlight da Apple, não é muito tarde para se registar. Registar irá permitir-lhe utilizar a aplicação Portal da empresa atualizado antes de ser disponibilizado aos seus utilizadores finais. Também pode fornecer seus comentários diretamente para a equipa do Intune.  

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Não é necessário efetuar qualquer ação; Estas alterações serão lançadas numa versão de aplicação do iOS futuros CP. 

#### <a name="additional-information"></a>Informações Adicionais
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)

### <a name="check-your-delay-visibility-of-software-updates-setting-in-intune"></a>Verifique a definição de "Visibility atraso das atualizações de Software" no Intune 

Partilhámos na MC171466 que podemos foram movimentar algumas definições na consola do. Com a atualização de Março ao Intune, podemos irá remover completamente a definição "Atualizações de visibilidade de atraso do Software" do painel de política de atualização de iOS. Isto não vai alterar a forma de aplicam as atualizações de software agendadas, mas pode afetar o tempo que a visibilidade de uma atualização é atrasada para os utilizadores finais. Terá de executar uma ação antes do final de Março se utilizar esta definição. 

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Após a atualização de serviço do Intune de Fevereiro, perceberá que a definição aparece em perfis de restrição de dispositivos na consola e no iOS atualizar políticas no painel de atualização de Software. Quando vir essa alteração seja refletida na consola do, eis o que poderá ter de fazer.

- Para atualizar as políticas existentes para iOS: Se tiver personalizado configurado esta definição para qualquer coisa diferente da predefinição de 30 dias e quiser as configurações existentes para a definição de visibilidade de atraso continuar a aplicar após o fim de Março, terá que criar um novo iOS perfil de restrição de dispositivos. Aqui, a definição de visibilidade de atraso terá de ter os mesmos valores como a política de atualização de iOS existente e ser direcionadas para os mesmos grupos. Após a atualização do serviço de Março, já não poderá editar os valores para esta definição nas políticas de atualização de iOS existente, uma vez que já não estarão visível neste painel. Em vez disso, irá configurar esta definição nos perfis de novo.
  Se o valor de número de dias pode atrasar visibilidade não corresponde em ambos os locais para os valores de definição configurada personalizado, a visibilidade de atraso definição não funcionará, e os utilizadores finais irão ver a atualização nos respetivos dispositivos, assim que estiver disponível. Isto pode ter um impacto mínimo para a maioria dos clientes, uma vez que as outras definições no painel da política de atualização de Software sempre usaram precedência sobre esta definição na consola do.
- Para novas políticas de atualização para iOS: Se tentar criar novas políticas no painel de atualizações de Software após a atualização do serviço de Fevereiro do Intune, irá ver esta definição a cinzento. Verá uma nota na consola do redirecioná-lo para o painel de configuração do dispositivo se desejar atrasar a visibilidade das atualizações.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Não é necessário executar uma ação se não utilize esta definição ou não pretender que a visibilidade das atualizações de software de seus usuários finais.

Se desejar atrasar a visibilidade das atualizações, começar a configurar a definição em novos perfis no painel da configuração do dispositivo em restrições do dispositivo > geral. Se tiver personalizado esta definição configurada no iOS existente, as políticas de atualização, criar um novo perfil de restrição de dispositivos equivalente com o mesmo valor para "dias" atrasar a visibilidade das atualizações para os seus utilizadores, depois do Fevereiro de atualização e antes de Março de atualização for implementada. 

Pode querer atualizar a sua documentação de orientação para profissionais de TI e informe o suporte técnico.

Consulte o nosso blogue de suporte publicar as informações adicionais para obter detalhes sobre como configurar esta definição.

#### <a name="additional-information"></a>Informações Adicionais 
[https://aka.ms/Delay_visibility_setting_iOS](https://aka.ms/Delay_visibility_setting_iOS)

### <a name="plan-for-change-upcoming-fix-for-windows-10-email-profiles-in-intune---3904031--"></a>Planear a alteração: Futura correção para perfis de e-mail do Windows 10 no Intune <!--3904031-->
Estamos a atualizar a forma como o Intune escreve e-mail perfis para o Windows 10 na Abril da atualização para o serviço do Intune para corrigir um bug, bem como para garantir que seus perfis de e-mail continuam a funcionar em futuras versões do Windows 10. Não existe ação que precisa de tomar depois de implementar esta correção.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Esta alteração irá afetar o se utilizar perfis de e-mail do Windows 10 com
- O cliente de correio nativo em computadores com Windows 10 ou
- O cliente de e-mail do Outlook no Windows 10 Mobile

Este problema afeta os dois clientes de gestão de dispositivos móveis (MDM) Intune autónomo e híbrido.

Depois de efetuada a atualização de Abril, terá de voltar a criar estes perfis na consola do Intune (na consola do administrador do Configuration Manager se estiver a utilizar o MDM híbrida).

Se não tomar medidas, eis o que verá para perfis criados antes da atualização de Abril:

- Perfis de e-mail existentes serão apresentados no Estado com erros na consola do Intune ou consola de administração do Configuration Manager, mas os usuários finais continuam a ter acesso ao e-mail. No entanto, após uma atualização subseqüente do Windows for implementada, estes perfis não funcionará. Os utilizadores finais nos dispositivos visados com estes perfis perderão o acesso ao e-mail.
- As edições efetuadas a esses perfis depois de Abril não será refletida em dispositivos visados.
- Eliminação seletiva não funcionará para remover estes perfis, mesmo após a correção é implementada em Abril.

Se agir e voltar a criar perfis de e-mail, os utilizadores finais terão de seguir passos semelhantes aos quando um perfil de e-mail é implementado pela primeira vez. E-mail será impedido de sincronização até que aceite a atualização que aplica-se o novo perfil.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Terá de tomar medidas apenas após a correção é implementada com a atualização de Abril. Podemos irá contactá-lo através do Centro de mensagens quando esta alteração entra no ar para que possa começar a voltar a criar seus perfis no Intune.

Se utilizar perfis de e-mail do Windows 10 no Intune, terá de seguir estes passos:

1. Capturar definições de perfil existentes do Windows 10
2. Anular a atribuição de e/ou eliminar perfis existentes
3. Criar novos perfis utilizando as definições de capturada e atribuir os novos perfis aos mesmos grupos

Se pretender notificar os utilizadores finais e permitir que o suporte técnico sabe dessa alteração. Consulte a mensagem de blogue de suporte informações adicionais para detalhes de erro e instruções para voltar a criar estes perfis.

#### <a name="additional-information"></a>Informações Adicionais
https://aka.ms/Win10EmailProfiles

