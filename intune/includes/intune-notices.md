
Estes avisos fornecem importante de informações que podem ajudá-lo a se preparar para as funcionalidades e alterações futuras do Intune. 

### <a name="change-in-enrollment-workflow-with-intune-company-portal-on-corporate-ios-devices-authenticating-with-setup-assistant----1927359---"></a>Alterar inscrição fluxo de trabalho com o Portal da empresa do Intune em dispositivos iOS empresariais, a autenticação com o Assistente de configuração <!-- 1927359 -->
Há uma futura alteração ao fluxo de trabalho para a inscrição de dispositivos iOS através de um dos dispositivo da empresa métodos de inscrição da Apple - Apple Configurator, gerente de negócios da Apple, Apple School Manager ou o Apple dispositivo programa de inscrição (DEP), ao utilizar o programa de configuração Assistente para a autenticação. Esta alteração aplica-se apenas a dispositivos inscritos com afinidade do utilizador.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Quando esta alteração é implementada ~~Março~~ Abril, perfis de inscrição no Intune no portal do Azure serão atualizados para que pode especificar a forma como os dispositivos serão autenticados e se eles recebem a aplicação Portal da empresa. Haverá um fluxo de trabalho melhorado para inscrever dispositivos iOS através dos métodos indicados acima. Nota:

- Quando inscrever novos dispositivos e a autenticação com o Assistente de configuração, poderá escolher se deve ou não implementar automaticamente a aplicação Portal da empresa. Os utilizadores finais já não verá a tela de "Identificar o dispositivo" e a tela de "Confirmar o seu dispositivo" no fluxo de inscrição.  
- Nos dispositivos já inscritos através do Assistente de configuração através de um dos métodos de inscrição de dispositivos da empresa da Apple, tem de tomar uma ação se pretender ativar o acesso condicional. Terá de configurar uma política de configuração de aplicação com um xml específico para enviar por push o Portal da empresa para estes dispositivos. Instruções para tal são na mensagem de blogue em ligação informações adicionais. Se optar por enviar por push o Portal da empresa, desta forma, os utilizadores finais já não verá a tela de "Identificar o dispositivo" e a tela de "Confirmar o seu dispositivo" no fluxo de inscrição. 
- Após esta alteração é implementada, se não tiver implementado o Portal da empresa com o perfil de configuração de aplicação mencionados acima e se a transferência dos utilizadores finais a aplicação Portal da empresa a partir da aplicação armazenar, pode iniciar sessão, mas irá receber uma mensagem de erro. Eles não será possível utilizar a aplicação para o acesso condicional. 

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>O que preciso de fazer para me preparar para esta alteração?
Se pretender utilizar o fluxo de trabalho modificado, poderá ser útil atualizar a sua documentação de orientação do utilizador final para indicar que:

- Os utilizadores finais já não verá os dois ecrãs mencionados acima no fluxo de inscrição. 
- Precisam de iniciar sessão no Portal da empresa quando é implementada automaticamente e não baixá-lo a partir da app store. 

Pode optar por criar uma política de configuração de aplicações agora, se for necessário, em preparação para esta alteração. Quando este novo fluxo de trabalho for implementada, verá os perfis de inscrição atualizado na consola do. Podemos irá também informar sobre esta implementação através do Centro de mensagens. Depois disso, terá de executar a ação para que os utilizadores finais podem inscrever através do DEP ao autenticar com o Assistente de configuração e pode utilizar o Portal da empresa para o acesso condicional.

Consulte o nosso suporte postagem no blog em ligação informações adicionais para obter mais detalhes sobre esta alteração.

#### <a name="additional-information"></a>Informações adicionais 
[https://aka.ms/enrollment_setup_assistant](https://aka.ms/enrollment_setup_assistant)


### <a name="company-portal-changes-for-ios-122-enrollment-in-intune"></a>Alterações de portais da empresa para iOS 12.2 inscrição no Intune
Partilhámos na MC172534 Apple anunciou algumas alterações relacionadas com dispositivos iOS, a inscrição para os serviços de gestão de dispositivos móveis (MDM). A alteração provavelmente será vista na versão do iOS na de 2019 de Março, bem como todas as versões futuras do iOS. Vamos fazer algumas atualizações no Portal da empresa para refletir as alterações da Apple. 
 
#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se os utilizadores finais atualizarem os seus dispositivos para dispositivos iOS 12.2 e superior, sabe-se de que existe um fluxo de trabalho modificado e têm de realizar passos adicionais que conclua a inscrição no Intune. Após a atualização de Março ao Intune, eis o que irá fazer-  

- Iniciar o processo de inscrição na aplicação Portal da empresa para transferir um perfil de gestão
- Aceda a definições > geral > perfis e buscar uma notificação de destaque vermelho
- Selecione o perfil correto e clicar para instalação
- Regresse ao Portal da empresa que conclua a inscrição

Clique em obter informações adicionais para obter informações detalhadas sobre o fluxo de inscrição.

Não devem ser afetados, a menos que estão a anular a inscrição e precisam de uma nova inscrição, os dispositivos que já estão inscritos e atualizar para o iOS 12.2 e acima. Experiência de inscrição em dispositivos com iOS 12.1 ou anterior não será alterada com essa nova versão pela Apple. Dispositivos inscritos através de um ou métodos de inscrição da empresa da Apple (programa de inscrição de dispositivos, do Apple School Manager ou gerente de negócios da Apple) não serão afetados.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Deve planear a atualização a documentação e as diretrizes de utilizador final. Também poderá permitir que o suporte técnico sabe dessas alterações. Vamos mantê-lo informado por meio de nosso, o que é a nova página quando esta alteração entra no ar. 

Se pretender tirar partido das alterações de Portal da empresa que estamos a introduzir, peça aos utilizadores finais para atualizar o seu dispositivo para a nova versão do iOS após a atualização de Março para o Intune service quando Portal da empresa 3.9.0 versão da aplicação. é libertado.

Clique em obter informações adicionais para uma mensagem de blogue de suporte com capturas de ecrã de pré-visualização das alterações do Portal da empresa.

Informações Adicionais [https://aka.ms/CP_changes_iOS12](https://aka.ms/CP_changes_iOS12)

### <a name="plan-for-change-workflow-changes-for-ios-12-enrollment-in-intune"></a>Planear a alteração: Alterações de fluxo de trabalho para iOS 12 inscrição no Intune
Apple anunciou algumas alterações relacionadas com dispositivos iOS, a inscrição para os serviços de gestão de dispositivos móveis (MDM). A alteração provavelmente será vista na versão da Primavera de 2019 do iOS, bem como todas as versões futuras do iOS.

#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Se os utilizadores finais atualizarem os seus dispositivos para esta nova versão do iOS 12 na Primavera, sabe-se de que existe um fluxo de trabalho modificado e precisam de efetuar passos adicionais que conclua a inscrição no Intune. Quando Apple apresenta estas alterações, os utilizadores finais terá de:

- Iniciar o processo de inscrição na aplicação Portal da empresa para transferir um perfil de gestão
- Aceda a definições > geral > perfis
- Selecione o perfil correto e clicar para instalação
- Regresse ao Portal da empresa que conclua a inscrição 

Não deve ser afetado, a menos que estão a anular a inscrição e precisam de uma nova inscrição, os dispositivos já inscritos e atualizar para a nova versão do iOS.

Experiência de inscrição em dispositivos com iOS 12.1 ou anterior não será alterada com essa nova versão pela Apple.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Deve planear a atualização a documentação e as diretrizes de utilizador final. Também poderá permitir que o suporte técnico sabe dessas alterações. Iremos mantê-lo informado por meio do Centro de mensagens e nossa, o que é a nova página quando esta alteração entra no ar.

#### <a name="additional-information"></a>Informações adicionais
[Suporte a mensagem de blogue com capturas de ecrã e vídeos do fluxo de inscrição esperado](https://aka.ms/iOS_enrollment_changes).

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

#### <a name="additional-information"></a>Informações adicionais
[https://aka.ms/cp_update_iOS](https://aka.ms/cp_update_iOS)


### <a name="reminder-removal-of-existing-exchange-online-to-intune-connectors----3105122---"></a>Lembrete: Remoção de existentes Exchange Online para conectores do Intune <!-- 3105122 -->
No MC165575, partilhámos que podemos seria possível remover o Exchange Online para a funcionalidade de conector do Intune 'De serviços' numa atualização futura. Com a atualização de Fevereiro ao serviço do Intune, iremos irá desativar o botão configurar novos conectores. Estamos a planear remover todos os existentes Exchange Online para conectores do Intune em Março de 2019.
 
#### <a name="how-does-this-affect-me"></a>Como é que isto me afeta?
Está recebendo esta mensagem, uma vez que os nossos registos indicam que pode utilizar a funcionalidade de conector "De serviços" no seu ambiente. O conector de 'De serviços' suporta a gestão do Exchange Active Sync apenas os dispositivos do Intune para o Exchange Online e não suporta a infraestrutura no local. Este conector, por conta da forma que é apresentado no console, é apresentada como necessários para acesso condicional (AC), quando, na realidade, não é necessária para a AC. Pode tem estado a utilizar este conector para compreender a utilização do Exchange Online antes de aplicar acesso condicional. Estas informações já são fornecidas pelo centro de administração do Microsoft 365. Aqui, encontrará fornece relatórios de utilização para o tipo de Exchange Online incluindo a aplicação a ser utilizado para entre 7 e 180 dias. Para obter mais informações, consulte [Office 365 relatórios no Centro de administração - utilização de aplicações de E-Mail](https://docs.microsoft.com/office365/admin/activity-reports/email-apps-usage?view=o365-worldwide).  
 
Se utilizar este conector no seu ambiente, não será possível monitorizar ou eliminar os Exchange Active Sync apenas os dispositivos no Intune após conectores foram desativados em Fevereiro. Não há nenhum impacto previsto aos seus utilizadores finais durante esta alteração.
 
#### <a name="what-can-i-do-to-prepare-for-this-change"></a>O que posso fazer para me preparar para esta alteração?
Se tiver o conector de serviços, configurar e executar o Exchange Active Sync apenas os dispositivos, mude para outros métodos de gerir os seus dispositivos. Tem as seguintes opções:

- Inscrever dispositivos na gestão de dispositivos móveis (MDM) 
- Utilizar políticas de proteção de aplicações do Intune para gerir os seus dispositivos 
- Utilizar controlos de Exchange, conforme descrito na documentação aqui 

#### <a name="additional-information"></a>Informações adicionais  
https://docs.microsoft.com/intune/exchange-service-connector-configure
