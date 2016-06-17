---
# required metadata

title: Versões anteriores | Microsoft Intune
description:
keywords:
author: Lindavr
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 45dad14a-d412-488d-bb1e-ad990ea503df

# optional metadata

ROBOTS: noindex,nofollow
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Versões anteriores do Intune

## Abril de 2016
Todas estas funcionalidades também são suportadas em clientes híbridos (Configuration Manager com o Intune).
### Gestão de aplicações
- **Conformidade de utilizadores MAM.**
Agora, pode ver o [estado](monitor-mobile-app-management-policies-with-Microsoft-Intune.md) das suas políticas de gestão de aplicações para qualquer utilizador no inquilino do Azure Active Directory (AAD). Isto inclui:
   - Dispositivos
   - Aplicações no dispositivo

   Valores de estado:

   **Com entrada dada**: indica que a política foi implementada para o utilizador, e a aplicação foi utilizada no contexto profissional, e recebeu com êxito a política.

    **Sem entrada dada:** indica que a política foi implementada para o utilizador, mas a aplicação não foi utilizada no contexto profissional desde então.


- **Controlos de MAM para impedir a sincronização de contactos do Outlook (Android).**
Uma nova definição está disponível para a [gestão de aplicações móveis](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md) sem inscrição de dispositivos. Esta definição permite impedir que uma aplicação sincronize contactos com o livro de endereços nativo em dispositivos Android. Quando esta definição estiver ativada, as aplicações visadas já não poderão guardar contactos no livro de endereços nativo. Quando esta definição estiver desativada, as aplicações visadas poderão guardar contactos no livro de endereços nativo. Quando [elimina remotamente os dados de um dispositivo ou aplicação](wipe-managed-company-app-data-with-Microsoft-Intune.md), os contactos que já tenham sido guardados no livro de endereços nativo serão removidos. Esta nova definição é suportada inicialmente pela aplicação Outlook em dispositivos Android.

### Gestão de dispositivos
- **Identificação de números de telefone para dispositivos pertencentes à empresa.** Os telefones que são classificados como "Empresa" estão agora identificados com o respetivo número de telefone completo quando, por exemplo, executa um relatório de inventário de dispositivos móveis. Os números de telefone BYOD continuam a ser mascarados com ****, com apenas os 4 últimos dígitos apresentados.


### Atualizações ao portal da empresa
**Aplicação Portal da Empresa para Android** Os utilizadores que não inscreveram o seu dispositivo no Intune e que não tenham o certificado correto instalado não poderão iniciar sessão na aplicação Portal da Empresa para Android e verão a mensagem “Não é possível inscrever-se porque o dispositivo tem um certificado necessário em falta”. A mensagem inclui uma ligação "How to resolve this" na qual os utilizadores podem tocar para ver instruções para instalar o certificado. Para ver os passos que os utilizadores finais têm de seguir para resolver o problema, consulte [O dispositivo tem um certificado necessário em falta](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_cert_missing).

**Aplicação Portal da Empresa para iOS** Foi adicionado suporte para a ação “puxe para atualizar”, para atualizar o conteúdo do ecrã principal, que inclui as aplicações listadas, os dispositivos listados e as informações de contacto de TI. A ação «puxe para atualizar» não verifica se existem informações de conformidade ou de política, o que pode ser efetuado selecionando o mosaico relativo ao seu dispositivo atual e tocando no botão **Sincronizar**.

**Aplicação Portal da Empresa para Windows 10 Mobile e Windows Phone 8.1** Quando os utilizadores finais estiverem a instalar aplicações de linha de negócio, irão ver agora uma experiência melhorada de instalação de aplicações. Se a instalação da aplicação estiver a demorar muito tempo, os utilizadores podem sincronizar manualmente os respetivos dispositivos para forçar a continuação do processo de sincronização. Para consultar as instruções do utilizador final, consulte [Sincronizar o dispositivo manualmente para acelerar a instalação de aplicações](https://technet.microsoft.com/library/mt427782.aspx#BKMK_win10m_wp81_sync_manually).

**Site do Portal da Empresa** Quando os utilizadores do Windows 10 Mobile e Windows Phone 8.1 estiverem a instalar aplicações de linha de negócio, irão ver agora os seguintes estados novos, que fornecem mais detalhes sobre o estado da instalação:

* **A aguardar sincronização do dispositivo** – o utilizador tocou em "Instalar" e o dispositivo tenta agora sincronizar com a infraestrutura do Intune. A sincronização é necessária para que a instalação possa ser concluída. A mensagem "A aguardar sincronização do dispositivo" é também uma ligação na qual os utilizadores podem tocar para ver [instruções](https://technet.microsoft.com/library/mt590895.aspx#BKMK_iwp_sync_manually) sobre como sincronizar manualmente o dispositivo com o Intune se o processo de sincronização estiver a demorar muito tempo ou ficar parado.
* **A transferir** – o pedido de transferência do utilizador está a ser processado e o dispositivo está a transferir e a instalar a aplicação.

Antes de estes estados terem sido adicionados, os utilizadores ficavam confusos se a instalação de uma aplicação demorava muito tempo, porque viam apenas um estado "A instalar", o qual podia permanecer no ecrã durante horas. Adicionar os novos estados significa que, em vez de contactar o suporte, os utilizadores podem agora tocar na ligação "A aguardar sincronização do dispositivo" e seguir as instruções para forçar a continuação do processo de sincronização.


## Março de 2016
### Novidades a partir de 29 de Março de 2016
Com exceção da atualização à política de configuração geral do Windows 10, todas as funcionalidades lançadas em 29 de março de 2016 também são suportadas em clientes híbridos (Configuration Manager integrado no Intune). O suporte híbrido da atualização da política de configuração geral do Windows 10 estará disponível em breve. Tenha em atenção que algumas destas funcionalidades podem necessitar da versão mais recente do Configuration Manager.

### Gestão de aplicações
- **Controlos de MAM para impedir a sincronização de contactos do Outlook (iOS).** Uma nova definição está disponível para a gestão de aplicações móveis sem inscrição de dispositivos. Esta definição permite impedir que uma aplicação sincronize contactos com o livro de endereços nativo em dispositivos iOS. Quando esta definição estiver ativada, a aplicação já não poderá guardar contactos no livro de endereços nativo. Quando esta definição estiver desativada, a aplicação poderá guardar contactos no livro de endereços nativo. Quando apaga seletivamente os dados de um dispositivo, todos os contactos que já tenham sido guardados no livro de endereços nativo serão removidos. Esta nova definição é suportada pela aplicação Outlook em dispositivos iOS. Para mais detalhes acerca desta e de outras definições, consulte [Criar e implementar políticas de MAM](https://technet.microsoft.com/en-us/library/dn292747.aspx).

### Controlo de acesso
- **O Skype para Empresas Online suporta o acesso condicional.** Pode definir uma política de acesso condicional para o Skype para Empresas Online, para que apenas dispositivos iOS e Android geridos e conformes possam aceder ao mesmo. Aos utilizadores finais que tentarem iniciar sessão na aplicação Skype para Empresas para dispositivos móveis em dispositivos iOS e Android será pedido que se inscrevam primeiro no Intune e que corrijam quaisquer problemas de não conformidade para que o início de sessão possa ser concluído. Para mais detalhes, consulte [Gerir o acesso ao Skype para Empresas Online](https://technet.microsoft.com/en-us/library/mt695297.aspx).

### Gestão de dispositivos
- **Suporte do Intune para iOS 9.3.** Na segunda-feira, 21 de março, a Apple anunciou a disponibilidade do iOS 9.3. Estivemos a trabalhar intensamente para garantir que o Microsoft Intune é compatível com a versão mais recente do sistema operativo móvel da Apple, e [temos o prazer de anunciar que o Intune suporta a gestão de dispositivos iOS 9.3](https://blogs.technet.microsoft.com/microsoftintune/2016/03/23/microsoft-intune-provides-support-for-ios-9-3/).

  Todas as funcionalidades existentes do Intune atualmente disponíveis para gerir dispositivos iOS continuarão a funcionar de forma totalmente integrada quando os utilizadores atualizarem os seus dispositivos para iOS 9.3. Além disso, o iOS 9.3 também é suportado atualmente para clientes híbridos (Configuration Manager integrado no Intune).

- **A política de configuração geral do Windows 10 contém agora definições para gerir o Windows Defender em PCs Windows 10 inscritos.** Para detalhes, consulte [Definições de política de configuração do Windows 10 no Microsoft Intune](https://technet.microsoft.com/en-us/library/mt404697.aspx).


### Portal da empresa

- **Pacotes de aplicações do Windows disponíveis diretamente a partir do site do Portal da Empresa.** Os utilizadores de PCs Windows 8, Windows 8.1 e Windows RT podem agora instalar pacotes de aplicações do Windows (com a extensão .appx) diretamente a partir do site do Portal da Empresa. Anteriormente, era necessário implementar, ou os utilizadores tinham de instalar, a aplicação Portal da Empresa nos respetivos dispositivos para instalar aplicações.

- **Os utilizadores podem bloquear remotamente o seu dispositivo a partir do site do Portal da Empresa.** Foi adicionada uma nova opção de bloqueio remoto ao site do Portal da Empresa para permitir que os utilizadores bloqueiem remotamente o seu dispositivo a partir do Portal, em caso de perda ou roubo do dispositivo. Consulte as [instruções do utilizador final](https://technet.microsoft.com/library/mt590895.aspx/?wt.mc_id=ui#BKMK_iwp_remote_lock). A tabela seguinte lista o suporte de plataforma do Bloqueio Remoto para o Intune autónomo e o Intune com o Configuration Manager.

|Plataforma | Detalhes do suporte|
|---------|----------------|
|Android |Suportado|
|iOS |Suportado|
|Windows 10 Mobile |Suportado apenas se o telemóvel tiver um código de acesso definido|
|Windows 10 Desktop |Não suportado|
|Windows Phone 8.1 |Suportado apenas se o telemóvel tiver um código de acesso definido|
|Windows Phone 8.0 |Não suportado|
|PC (Windows 8.0 e anterior) |Não suportado|
|PC (Windows 8.1) |Não suportado|

### Novidades a partir de 10 de março de 2016

### Gestão de aplicações

- **Tirar partido da funcionalidade de gestão "Open-in" do iOS para dispositivos inscritos numa solução MDM de terceiros** Pode utilizar o fornecedor de gestão de dispositivos móveis (MDM) de terceiros para tirar partido da funcionalidade de gestão "Open-in" do iOS. Pode configurar as restrições nas definições do perfil de configuração e implementar a aplicação, utilizando [Gerir a transferência de dados entre aplicações iOS](manage-data-transfer-between-ios-apps-with-microsoft-intune.md).

     Esta abordagem tem duas vantagens principais:

     1. Os utilizadores são obrigados a iniciar sessão com a respetiva conta profissional antes de terem acesso a quaisquer dados empresariais a partir de Serviços Cloud ou de outras aplicações. Isto garante que as políticas de gestão de aplicações móveis (MAM) estão implementadas quando aceder aos dados.

     2. Os perfis de e-mail gerido e outras aplicações geridas implementadas através de uma solução MDM de terceiros podem partilhar ficheiros e dados com aplicações que tenham políticas MAM do Intune.

- **Gerir a aplicação Microsoft Outlook com políticas de MAM para dispositivos que não estão inscritos no Intune** Agora, já pode gerir a aplicação Microsoft Outlook em dispositivos que não estão inscritos no Intune com a política de gestão de aplicações móveis do Intune. A aplicação Microsoft Outlook atualizada com as capacidades MAM está disponível para dispositivos [iOS](https://itunes.apple.com/us/app/microsoft-outlook-email-calendar/id951937596?mt=8) e [Android](https://play.google.com/store/apps/details?id=com.microsoft.office.outlook). Utilize as instruções do tópico [Criar e implementar políticas de gestão de aplicações móveis](https://technet.microsoft.com/library/mt627829.aspx) para criar uma política MAM.  


- **As políticas de configuração de aplicações móveis dão-lhe uma maior flexibilidade para especificar detalhes de utilizador para aplicações iOS** Pode fornecer as definições de utilizador que poderão ser necessárias a uma aplicação iOS quando for aberta. Por exemplo, pode fornecer uma porta de rede ou um nome de utilizador. Para detalhes, consulte [Configurar aplicações com políticas de configuração de aplicações móveis no Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md).


- **Implementar o Adobe Reader para Microsoft Intune em dispositivos iOS geridos pelo Intune na sua empresa** A aplicação Adobe Reader para iOS pode agora ser gerida em dispositivos inscritos com a política de gestão de aplicações móveis do Intune.

- **Garantir que os clips Web são abertos no browser gerido** Pode implementar clips Web direcionados, que só podem ser abertos com o browser gerido em dispositivos iOS e Android. Por exemplo, pode implementar hiperligações para recursos da empresa através do Portal da Empresa e quando os utilizadores navegarem para as hiperligações, estas abrem diretamente no browser gerido, onde podem ser protegidas pela política MAM. Para detalhes, consulte [Implementar aplicações](deploy-apps.md).


- **Localizar, gerir e distribuir aplicações da Loja Windows para Empresas para dispositivos Windows 10 a partir da consola do administrador do Intune** O suporte da Loja Windows para Empresas está disponível no Intune para o ajudar a localizar, gerir e distribuir aplicações para os dispositivos Windows 10 que estiver a gerir. A Loja Windows para Empresas permite-lhe gerir o processo de implementação e monitorização destas aplicações na consola do administrador do Intune — a mesma consola que utiliza para gerir as suas outras aplicações. Especificamente, a Loja Windows para Empresas gere o conteúdo e o licenciamento de "aplicações licenciadas online". Para detalhes, consulte [Gerir aplicações compradas na Loja Windows para Empresas](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).


### Gestão de dispositivos
- **Distribuição de certificados PFX para dispositivos iOS** Os administradores do Intune podem criar e implementar certificados PFX iOS para Wi-Fi, e-mail e autenticação VPN em dispositivos iOS. Esta funcionalidade já se encontra disponível para dispositivos Android e Windows 10. Para detalhes, consulte [Permitir o acesso a recursos da empresa através de perfis de certificados](secure-resource-access-with-certificate-profiles.md).


- **Aplicar aplicações e políticas a diferentes grupos de dispositivos com base na seleção da categoria de utilizador** Os administradores do Intune podem agora definir categorias de dispositivo personalizadas para os utilizadores selecionarem durante a inscrição. Por exemplo, os administradores poderão querer que os utilizadores especifiquem se estão a inscrever um dispositivo utilizado para "Caixa registadora", "Camião de entregas" ou "Sala de inventário". A categoria selecionada fará com que o dispositivo passe a ser membro de um grupo de dispositivos do Intune, que pode ser utilizado para implementar diferentes aplicações e políticas no dispositivo inscrito. Para detalhes, consulte [Categorizar os dispositivos com o mapeamento de grupo de dispositivos](categorize-devices-with-device-group-mapping-in-microsoft-intune.md).

### Alterações e atualizações do Portal da Empresa da Microsoft
As seguintes alterações foram efetuadas no Portal da Empresa nesta versão:

**Aplicação do Portal da Empresa para Android**

* Quando os seus utilizadores iniciarem uma aplicação gerida pela gestão de aplicações móveis (MAM), verão uma mensagem a indicar que a aplicação é gerida pela empresa. Os utilizadores podem agora tocar numa hiperligação "Mais Informações" para obterem [mais informações](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_use_mgd_apps) sobre “aplicações geridas”. Também podem tocar em "Não voltar a mostrar" para que a mensagem deixe de aparecer quando iniciarem a aplicação.
* Foram adicionados novos ecrãs para orientar os utilizadores ao longo do processo de inscrição e fornecer mais informações sobre a razão pela qual os utilizadores devem efetuar a inscrição e o que os administradores de TI podem e não podem ver nos seus dispositivos inscritos. Consulte as [instruções de inscrição](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) para obter mais informações.
* As mensagens de erro de inscrição são agora apresentadas na aplicação Portal da Empresa. Anteriormente, estas mensagens eram apresentados no site do Portal da Empresa. Esta alteração significa que todas as mensagens de erro são agora apresentadas apenas num local em vez de dois locais diferentes.


**Aplicação Portal da Empresa para iOS**
* Quando os seus utilizadores iniciarem uma aplicação gerida pela gestão de aplicações móveis (MAM), verão uma mensagem a indicar que a aplicação é gerida pela empresa. Os utilizadores podem agora tocar numa hiperligação "Mais Informações" para obterem [mais informações](https://technet.microsoft.com/library/mt598622.aspx#BKMK_ios_use_mgd_apps) sobre “aplicações geridas”. Também podem tocar em "Não voltar a mostrar" para que a mensagem deixe de aparecer quando iniciarem a aplicação.
* Foram adicionados novos ecrãs para orientar os utilizadores ao longo do processo de inscrição e fornecer mais informações sobre a razão pela qual os utilizadores devem efetuar a inscrição e o que os administradores de TI podem e não podem ver nos seus dispositivos inscritos. Consulte as [instruções de inscrição](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) para obter mais informações.
* As mensagens de erro de inscrição são agora apresentadas na aplicação Portal da Empresa. Anteriormente, estas mensagens eram apresentados no site do Portal da Empresa. Esta alteração significa que todas as mensagens de erro são agora apresentadas apenas num local em vez de dois locais diferentes.




## Fevereiro de 2016
### Alterações e atualizações do Portal da Empresa da Microsoft

As seguintes alterações foram efetuadas no Portal da Empresa nesta versão:

#### Aplicação do Portal da Empresa para Android
- Foram adicionados novos ecrãs para orientar os utilizadores ao longo do processo de inscrição e fornecer mais informações sobre a razão pela qual os utilizadores devem efetuar a inscrição e o que os administradores de TI podem e não podem ver nos seus dispositivos inscritos. Consulte as [instruções de inscrição](https://technet.microsoft.com/library/mt502762.aspx#BKMK_andr_enroll_devc) para obter mais informações.
- As mensagens de erro de inscrição são agora apresentadas na aplicação Portal da Empresa. Anteriormente, estas mensagens eram apresentados no site do Portal da Empresa. Esta alteração significa que todas as mensagens de erro são agora apresentadas apenas num local em vez de dois locais diferentes.

#### Aplicação Portal da Empresa para iOS
 - Foram adicionados novos ecrãs para orientar os utilizadores ao longo do processo de inscrição e fornecer mais informações sobre a razão pela qual os utilizadores devem efetuar a inscrição e o que os administradores de TI podem e não podem ver nos seus dispositivos inscritos. Consulte as [instruções de inscrição](https://technet.microsoft.com/library/mt598622.aspx#BKMK_enroll_ios_device) para obter mais informações.

 - As mensagens de erro de inscrição são agora apresentadas na aplicação Portal da Empresa. Anteriormente, estas mensagens eram apresentados no site do Portal da Empresa. Esta alteração significa que todas as mensagens de erro são agora apresentadas apenas num local em vez de dois locais diferentes.


## Janeiro de 2016

### Tirar partido das funcionalidades do Windows 10
* **Acesso condicional com Serviço de Atestado de Estado de Funcionamento** Os administradores do Intune podem agora ver o estado do Atestado de Estado de Funcionamento do Dispositivo Windows 10 na consola de administração do Intune. O Device Health Attestation permite ao administrador garantir que os computadores cliente têm configurações fidedignas de BIOS, TPM e software de arranque. Para suportar o atestado de estado de funcionamento do dispositivo, os dispositivos cliente têm de ter o Windows 10 com o TPM 2 ativado. O Device Health Attestation apresenta o número de dispositivos ativados para cada o seguinte:
    * Antimalware de início antecipado
    * BitLocker
    * Arranque Seguro
    * Integridade de Código

    Leia o artigo [Introdução às políticas de conformidade de dispositivos para o Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md) para obter mais detalhes sobre a definição de estado de funcionamento do dispositivo, pontos de dados recolhidos e o relatório de atestado de estado de funcionamento. O tópico [Detalhes do serviço HAS](https://msdn.microsoft.com/en-us/library/dn934876.aspx) explica o serviço em profundidade.

* **Política Passport for Work e gestão de certificados do Windows 10** Com o Intune, é possível efetuar a [integração com o Microsoft Passport for Work](control-microsoft-passport-settings-on-devices-with-microsoft-intune.md), que é um método de início de sessão alternativo para Windows 10 que utiliza o Active Directory ou uma conta do Azure Active Directory para substituir uma palavra-passe, um smart card ou um smart card virtual. O Passport permite utilizar um gesto de utilizador para iniciar sessão, em vez de uma palavra-passe. Um gesto de utilizador pode ser um PIN simples, uma autenticação biométrica, como o Windows Hello, ou um dispositivo externo, como um leitor de impressões digitais.

* **VPN para aplicações específicas** Pode selecionar aplicações que ligam automaticamente à sua rede empresarial através de VPN. Crie a lista de aplicações quando configurar o perfil VPN, conforme descrito no tópico Ajudar os utilizadores a estabelecer uma ligação com o respetivo trabalho através de perfis da VPN com o Microsoft Intune.

* **Suporte de Eliminação Completa de Dados do Windows 10** Agora, pode emitir uma eliminação completa remota de dados de dispositivos de ambiente de trabalho Windows 10 inscritos no Intune, através da consola de administração do Intune. A eliminação completa de dados do Windows 10 efetua uma reposição de fábrica do dispositivo.


### Atualização do Apple Volume Purchase Program (VPP)
O Intune pode agora ajudá-lo a [gerir as aplicações compradas através do Apple Volume Purchase Program (VPP) for Business](manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune.md). Isto inclui sincronizar as informações de licença entre a Apple e o Intune, e controlar a quantidade de cópias de cada aplicação que implementou.

### Utilizar números IMEI para identificar dispositivos pertencentes à empresa
Agora, pode [importar números de identidade internacional do equipamento móvel (IMEI)](specify-corporate-owned-devices-with-international-mobile-equipment-identity-imei-numbers.md) para plataformas de dispositivos móveis que tenham um número IMEI para ajudar a identificar os dispositivos móveis pertencentes à empresa. Depois de inscritos no Intune, os dispositivos com números IMEI importados são etiquetados como Empresa, o que pode ser utilizado na aplicação de políticas diferentes das aplicadas a dispositivos de propriedade pessoal.

### Mais aplicações são agora compatíveis com as políticas MAM do Intune
Mais aplicações de parceiros da Microsoft são agora compatíveis com as políticas de gestão de aplicações móveis (MAM) do Intune (para dispositivos geridos pelo Intune):
* Box for EMM (da Box Inc) – apenas iOS
* Adobe Reader (da Adobe) – apenas Android
* Foxit PDF Reader (da Foxit Corporation) – iOS e Android


### O suporte do IE9 termina em janeiro
A partir de fevereiro de 2016, o Internet Explorer 9 já não será suportado como browser oficial para aceder ao site do portal da empresa do Microsoft Intune, ao portal de contas do Intune e à consola de administração do Intune. Terá de migrar para o Internet Explorer 10 ou posterior.

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


>[!div class="step-by-step"]

>[&larr; **Novidades do Intune**](whats-new-in-microsoft-intune.md)    


<!--HONumber=May16_HO3-->


