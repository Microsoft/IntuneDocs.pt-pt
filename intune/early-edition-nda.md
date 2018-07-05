---
title: Edição antecipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 06/28/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 0500194f5afaba11f37b84bbdf606e6167632a71
ms.sourcegitcommit: afa2e84d5cadf5542ecabc26e61dc71919992a22
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37340187"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>A edição antecipada do Microsoft Intune – julho de 2018

> [!Note]
> Notificação de contrato de confidencialidade: as seguintes alterações estão em desenvolvimento para o Intune. Estas informações são partilhadas ao abrigo de um contrato de confidencialidade numa base muito limitada. Não publique estas informações em redes sociais ou em sites públicos como o Twitter, UserVoice, Reddit, entre outros. 

A **edição antecipada** oferece uma lista de funcionalidades, partilhadas ao abrigo de um contrato de confidencialidade, disponíveis em versões futuras do Microsoft Intune. Estas informações são fornecidas numa base limitada e estão sujeitas a alterações. Não publique no Twitter nem no UserVoice, nem partilhe estas informações de nenhuma outra forma com pessoas fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

<!-- 1807 start -->

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Repor códigos de acesso de dispositivos a partir da aplicação Portal da Empresa para Windows 10 <!-- 2101282 --> 
Em breve, os seus colaboradores poderão repor o PIN ou o código de acesso dos respetivos dispositivos diretamente a partir da aplicação Portal da Empresa para Windows 10. Esta funcionalidade estará disponível em dispositivos remotos e locais geridos pelo Intune que suportem a reposição de códigos de acesso. Consoante o tipo de dispositivo, um pedido feito para um dispositivo remoto irá remover o código de acesso atual do dispositivo ou criar um código de acesso temporário. Os utilizadores que efetuarem um pedido de reposição para um dispositivo local serão redirecionados para a aplicação Definições do dispositivo.

### <a name="use-smime-to-encrypt-and-sign-a-users-multiple-devices-----1333642---"></a>Utilizar S/MIME para encriptar e inscrever múltiplos dispositivos de um utilizador <!-- 1333642 -->
Uma futura atualização irá incluir a encriptação de e-mails com S/MIME através de um novo perfil de certificado importado (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > selecione a plataforma > tipo de perfil **Certificados PKCS importados**). No Intune, pode importar certificados no formato PFX. O Intune pode enviar esses mesmos certificados para múltiplos dispositivos inscritos por um único utilizador. Isto também inclui:

- O perfil de e-mail nativo do iOS suporta a ativação da encriptação S/MIME através de certificados importados no formato PFX.
- A aplicação de e-mail nativa dos dispositivos Windows Phone 10 utiliza automaticamente o certificado S/MIME.
- Os certificados privados podem ser fornecidos a várias plataformas. No entanto, nem todas as aplicações de e-mail suportam S/MIME.
- Noutras plataformas, talvez seja necessário configurar manualmente a aplicação de e-mail para permitir o S/MIME.  
- As aplicações de e-mail que suportam a encriptação S/MIME conseguem obter certificados para a encriptação S/MIME de e-mails de uma forma que não é suportada por MDM, como a leitura a partir do arquivo de certificados do respetivo publicador.

Suportado no: Windows, Windows Phone 10, macOS, iOS, Android

### <a name="use-vpp-device-licenses-to-pre-provision-the-company-portal-during-dep-enrollment----1608345---"></a>Utilizar licenças de dispositivos VPP para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP <!-- 1608345 -->
Poderá utilizar licenças de dispositivos do Programa de Compras em Volume (VPP) para aprovisionar previamente o Portal da Empresa durante as inscrições do Programa de Registo de Aparelho (DEP). Para tal, ao criar ou editar um perfil de inscrição, especifique o token VPP que pretende utilizar para instalar o Portal da Empresa. Certifique-se de que o token não expira e que tem licenças suficientes para a aplicação Portal da Empresa. Nos casos em que o token expirar ou esgotar as licenças, o Intune irá iniciar o Portal da Empresa a partir da App Store (esta ação irá exigir um ID Apple).

### <a name="bulk-delete-devices-on-devices-blade----1793693---"></a>Eliminar dispositivos em massa no painel Dispositivos <!-- 1793693 -->
Poderá eliminar múltiplos dispositivos de uma só vez no painel Dispositivos. Selecione **Dispositivos** > **Todos os dispositivos** > selecione os dispositivos que pretende eliminar > **Eliminar**. Será apresentado um alerta para os dispositivos que não puderem ser eliminados.

### <a name="new-wi-fi-device-configuration-profile-for-windows-10-and-later----1879077---"></a>Novo perfil de configuração de dispositivos Wi-Fi para Windows 10 e posterior <!-- 1879077 -->
Atualmente, pode importar e exportar perfis Wi-Fi através de ficheiros XML. Poderá criar um perfil de configuração de dispositivos Wi-Fi diretamente no Intune, tal como o faria em algumas outras plataformas.

Para criar o perfil, abra o menu **Configuração do dispositivo** > **Perfis** > **Criar Perfil** > **Windows 10 e versões posteriores** > **Wi-Fi**. 

Aplica-se ao Windows 10 e posterior.

###  <a name="windows-line-of-business-lob-apps-file-extension-rename----1884873---"></a>Mudança no nome das extensões de ficheiros de aplicações de linha de negócio (LOB) do Windows <!-- 1884873 -->
O nome das extensões de ficheiros de aplicações LOB do Windows será mudado de *.appx* e *.appxbundle* para *.msix* e *.msixbundle*. Pode adicionar uma aplicação no Microsoft Intune ao selecionar **Aplicações móveis** > **Aplicações** > **Adicionar**. O painel **Adicionar aplicação** é apresentado, o qual lhe permite selecionar o **Tipo de aplicação**. Para aplicações LOB do Windows, selecione o tipo de aplicação **Linha de negócio**, selecione o **Ficheiro de pacote de aplicação** e, em seguida, introduza um ficheiro de instalação com a extensão adequada.

### <a name="windows-defender-atp-configuration-package-automatically-added-to-configuration-profile----2144658---"></a>Pacote de configuração do Windows Defender ATP adicionado automaticamente ao perfil de configuração <!-- 2144658 -->
Agora, ao utilizar dispositivos de [Proteção Avançada Contra Ameaças e inclusão](advanced-threat-protection.md#onboard-devices-using-a-configuration-profile) no Intune, irá transferir um pacote de configuração e adicioná-lo ao seu perfil de configuração. Numa atualização futura, o Intune passará a obter automaticamente o pacote a partir do Centro de Segurança do Windows Defender e a adicioná-lo ao seu perfil.

Aplica-se ao Windows 10 e posterior.

### <a name="kiosk---obsolete-is-grayed-out-and-cant-be-changed----2149998---"></a>A funcionalidade Quiosque (Obsoleto) foi desativada e não pode ser alterada <!-- 2149998 -->
A [funcionalidade Quiosque](device-restrictions-windows-10.md#kiosk-preview---obsolete) (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e versões posteriores** > **Restrições do dispositivo**) irá tornar-se obsoleta e será substituída pelas [definições do Quiosque para Windows 10 e posterior](kiosk-settings.md). A funcionalidade **Quiosque (Obsoleto)** será desativada e a interface de utilizador não poderá ser alterada nem atualizada. 

Para ativar o modo de quiosque, veja [Definições de quiosque para Windows 10 e posterior](kiosk-settings.md).

Aplica-se ao Windows 10 e posterior e ao Windows Holographic for Business

### <a name="apis-to-use-3rd-party-certification-authorities----2184013---"></a>APIs para utilização de autoridades de certificação externas <!-- 2184013 -->
Será disponibilizada uma API de Java que permite a integração de autoridades de certificação externas no Intune e no SCEP. A partir daí, os utilizadores podem adicionar o certificado SCEP a um perfil e aplicá-lo aos dispositivos com MDM.

Atualmente, o Intune suporta [pedidos de SCEP que utilizam os Serviços de Certificados do Active Directory](certificates-scep-configure.md).

### <a name="check-for-sccm-compliance----2192052---"></a>Verificar a conformidade com o SCCM <!-- 2192052 -->
Uma futura atualização irá incluir uma nova definição de conformidade do System Center Configuration Manager (SCCM) (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Windows 10**). O SCCM envia sinais de conformidade ao Intune. Com a definição do Intune, pode exigir que todos os sinais do SCCM devolvam o estado "compatível".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No SCCM, este requisito apresenta o estado "Instalado". Se algum dos programas no dispositivo apresentar um estado desconhecido, o dispositivo será marcado como não compatível no Intune.

Aplica-se ao Windows 10 e posterior

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas de token VPP prestes a expirar ou de licenças do Portal da Empresa que se estão a esgotar <!-- 2237572 -->
Se utilizar o Programa de Compras em Volume (VPP) para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP, o Intune irá alertá-lo quando o token VPP estiver prestes a expirar e quando as licenças do Portal da Empresa se estiverem a esgotar.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmação necessária para eliminar o token VPP que está a ser utilizado para aprovisionar previamente o Portal da Empresa <!-- 2237634 -->
Será pedida uma confirmação para eliminar um token de Programa de Compras em Volume (VPP) se o mesmo estiver a ser utilizado para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP.

### <a name="automatically-mark-android-devices-enrolled-by-using-samsung-knox-mobile-enrollment-as-corporate----2404851---"></a>Marcar automaticamente dispositivos Android inscritos através do Samsung Knox Mobile Enrollment como "empresarial" <!-- 2404851 -->
Por predefinição, os dispositivos Android inscritos através do Samsung Knox Mobile Enrollment serão marcados como **empresarial** em **Propriedade do Dispositivo**. Não terá de identificar manualmente os dispositivos empresariais através dos números de série ou do IMEI antes da inscrição com o Knox Mobile Enrollment.

### <a name="toggle-to-show-or-not-show-the-end-session-button-on-a-kiosk-browser----2455253---"></a>Alternar entre mostrar ou não mostrar o botão Terminar Sessão num browser do Quiosque <!-- 2455253 -->
Poderá configurar as opções para determinar se os browsers do Quiosque devem ou não mostrar o botão Terminar Sessão. Pode ver o controlo em **Configuração do dispositivo** > **Quiosque (pré-visualização)** > **Browser da Web do Quiosque**. Se o botão estiver ativado e quando o utilizador clicar no mesmo, a aplicação pede confirmação para terminar a sessão. Ao confirmar, o browser limpa todos os dados de navegação e regressa ao URL predefinido.

### <a name="create-an-esim-cellular-configuration-profile----2564077---"></a>Criar um perfil de configuração de rede móvel eSIM <!-- 2564077 -->
Em **Configuração do dispositivo**, poderá criar um perfil de rede móvel eSIM. Pode importar um ficheiro com códigos de ativação de rede móvel fornecidos pela sua operadora móvel. Em seguida, poderá implementar estes perfis nos seus dispositivos Windows 10 compatíveis com eSIM LTE, como o Surface Pro LTE e outros dispositivos compatíveis com eSIM.

Verifique se os seus [dispositivos suportam perfis eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

Aplica-se ao Windows 10 e posterior. 




<!-- 1806 start -->

### <a name="see-device-configuration-profiles-in-conflict----1556983---"></a>Ver perfis de configuração de dispositivos em conflito <!-- 1556983 -->
Em **Configuração do dispositivo**, é apresentada uma lista dos perfis existentes. Com esta atualização, é adicionada uma nova coluna que fornece detalhes sobre os perfis que apresentam um conflito. Pode selecionar uma linha de conflito para ver a definição e o perfil que está em conflito. 

Saiba mais sobre os [perfis de configuração de dispositivos](device-profiles.md).

### <a name="corporate-owned-single-use-cosu-support-for-android-devices----1630973---"></a>Suporte de utilização única, pertencente à empresa (COSU) para dispositivos Android <!-- 1630973 -->

O Intune irá suportar dispositivos Android ao estilo de quiosque, bloqueados e altamente geridos. Isto permite que os administradores bloqueiem a utilização de um dispositivo para uma única aplicação ou pequeno conjunto de aplicações e impede que os utilizadores ativem outras aplicações ou efetuem outras ações no dispositivo.

### <a name="macos-support-for-apple-device-enrollment-program----747651---"></a>Suporte do macOS para o Programa de Inscrição de Dispositivos da Apple <!-- 747651 -->

O Intune irá suportar a inscrição de dispositivos macOS no Programa de Inscrição de Dispositivos da Apple (DEP). Para tal:

1. Em deploy.apple.com, atribua números de série do macOS a um servidor MDM.
2. Importe os números de série para o Intune.
3. Crie um perfil do programa de inscrição específico para dispositivos macOS.

### <a name="google-name-changes-for-android-for-work-and-play-for-work---842873---"></a>Alterações de nome da Google para Android for Work e Play for Work <!--842873 -->
O Intune irá atualizar a terminologia do "Android for Work" para refletir as alterações de imagem corporativa da Google.  Os termos "Android for Work" e "Play for Work" deixarão de ser utilizados. Será utilizada terminologia diferente consoante o contexto:

- "Android Enterprise" refere-se à pilha de gestão de Android global e moderna.
- "Perfil Profissional" ou "Proprietário do Perfil" refere-se a dispositivos BYOD geridos com perfis profissionais.
- "Google Play Gerido" refere-se à loja de aplicações da Google.

### <a name="monitor-ios--app-configuration-status-per-device----880037-eeready-eestaged---"></a>Monitorizar o estado de configuração da aplicação iOS por dispositivo <!-- 880037 eeready eestaged -->

Enquanto administrador do Microsoft Intune, poderá monitorizar o estado de configuração da aplicação iOS para cada dispositivo gerido. No **Microsoft Intune**, no portal do Azure, selecione **Dispositivos** > **Todos os dispositivos**. Na lista de dispositivos geridos, selecione um dispositivo específico para apresentar um painel do dispositivo. No painel do dispositivo, selecione **Configuração da aplicação**.  

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Os teclados de terceiros podem ser bloqueados por definições de APP no iOS <!-- 1248481 -->
Em dispositivos iOS, os administradores do Intune poderão bloquear a utilização de teclados de terceiros ao aceder a dados da organização em aplicações protegidas por políticas. Quando a Política de Proteção de Aplicações (APP) estiver definida para bloquear teclados de terceiros, o utilizador do dispositivo irá receber uma mensagem da primeira vez que interagir com dados da empresa ao utilizar um teclado de terceiros. Todas as opções, além do teclado nativo, serão bloqueadas e os utilizadores de dispositivos não irão vê-las. Os utilizadores de dispositivos só verão a mensagem de diálogo uma vez. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Criar política de conformidade de dispositivos com as definições de firewall em dispositivos macOS <!-- 1497640 -->
Quando criar uma nova política de conformidade do macOS (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Plataforma: macOS** > **Segurança do sistema**), estarão disponíveis algumas definições de **Firewall** novas: 
- **Firewall**: configure a forma como as ligações de entrada são processadas no seu ambiente.
- **Ligações de entrada**: **bloqueia** todas as ligações de entrada, exceto as ligações necessárias para serviços básicos de Internet, tal como o DHCP, Bonjour e IPSec. Esta definição também bloqueia todos os serviços de partilha.
- **Modo invisível**: **ative** o modo invisível para impedir que o dispositivo responda aos pedidos de pesquisa. O dispositivo continua a responder a pedidos recebidos de aplicações autorizadas.

Aplica-se a: macOS 10.12 e posterior

### <a name="use-samaccountname-as-the-account-username-for-email-profiles----1500307---"></a>Utilizar sAMAccountName como o nome de utilizador da conta para perfis de e-mail <!-- 1500307 -->

Poderá utilizar **sAMAccountName** no local como o nome de utilizador da conta para perfis de e-mail para Android, iOS e Windows 10. Também poderá obter o domínio do atributo `domain` ou `ntdomain` no Azure Active Directory (Azure AD). Em alternativa, introduza um domínio estático personalizado.

Para utilizar esta funcionalidade, tem de sincronizar o atributo `sAMAccountName` do seu ambiente do Active Directory no local com o Azure AD.

Aplica-se a: Android, iOS, Windows 10 e posterior

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Exigir código de acesso não biométrico na inicialização da aplicação e após o tempo limite <!-- 1506985 -->

Ao exigir um código de acesso não biométrico na inicialização da aplicação e após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.

### <a name="selective-wipe-of-organizations-app-data----1507030---"></a>Eliminação seletiva dos dados da aplicação da organização <!-- 1507030 -->
Os administradores poderão configurar uma eliminação seletiva dos dados da organização como uma nova ação quando as condições de definições de Acesso de Políticas de Proteção de Aplicações (APP) não são cumpridas.  Esta funcionalidade ajuda os administradores a proteger e remover automaticamente dados confidenciais da organização de aplicações com base em critérios pré-configurados.

### <a name="revoking-an-ios-app-purchased-through-vpp----1777384---"></a>Revogar uma aplicação iOS comprada através do VPP <!-- 1777384 -->
Enquanto administrador do Microsoft Intune, poderá revogar a licença de uma aplicação iOS selecionada comprada através do programa de compra em volume (VPP). Pode notificar os utilizadores quando uma aplicação já não estiver atribuída aos mesmos. Revogar a licença de uma aplicação não desinstala a aplicação VPP relacionada do dispositivo. Para desinstalar uma aplicação VPP, tem de alterar a ação de atribuição para **Desinstalar**. A contagem de licenças recuperadas será refletida no nó **Aplicações Licenciadas** na carga de trabalho **Aplicação** do Intune. Para obter mais informações relacionadas com aplicações iOS obtidas pelo VPP, veja [Como gerir aplicações iOS compradas através de um programa de compra em volume com o Microsoft Intune](vpp-apps-ios.md).

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Pacotes de Idiomas do Office 365 Pro Plus <!-- 1833450 -->
Enquanto administrador do Intune, poderá implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal do Azure, selecione **Microsoft Intune** > **Aplicações móveis** > **Aplicações** > **Adicionar**. Na lista **Tipo de aplicação**, no painel **Adicionar aplicação**, selecione **Windows 10** em **Office 365 Suite**. Selecione **Idiomas** no painel **Definições do Conjunto de Aplicações**.

### <a name="revoke-ios-vpp-app-license----1863797---"></a>Revogar licença de aplicação iOS obtida pelo VPP <!-- 1863797 -->
Enquanto administrador, poderá recuperar uma licença de aplicação iOS obtida pelo VPP atribuída a um utilizador ou dispositivo. Desinstalar uma aplicação iOS obtida pelo VPP também permitirá recuperar a licença da aplicação. Em seguida, pode optar por atribuir a licença da aplicação a outro utilizador ou dispositivo. Para obter mais informações sobre licenças de aplicação iOS obtida pelo VPP, veja [Gerir aplicações iOS compradas em volume no Microsoft Intune](vpp-apps-ios.md).

### <a name="preview-a-new-user-experience-update-for-the-company-portal-website---2000968---"></a>Pré-visualização de uma nova atualização da experiência de utilizador do site do Portal da Empresa <!--2000968 -->
Estamos a adicionar novas funcionalidades ao site do Portal da Empresa/catálogo de aplicações iOS com base no feedback dos clientes. Irá ver uma melhoria significativa na usabilidade e funcionalidades existentes nos seus dispositivos Android, iOS e Windows. As áreas do site – tal como detalhes, feedback, suporte e descrição geral do dispositivo – irão receber uma nova estrutura moderna e responsiva. A atualização inclui ainda:

- Fluxos de trabalho simplificados em todas as plataformas de dispositivos
- Fluxos de inscrição e identificação de dispositivos melhorados
- Mensagens de erro mais úteis
- Linguagem mais simples, menos termos técnicos
- Capacidade de partilhar ligações diretas para as aplicações
- Desempenho melhorado para grandes catálogos de aplicações
- Acessibilidade melhorada para todos os utilizadores

A atualização está atualmente em pré-visualização. Pode registar-se para aderir à pré-visualização em http://aka.ms/webcpflighting

### <a name="updates-to-out-of-compliance-messages-in-company-portal-app----1832222---"></a>Atualizações às mensagens de não conformidade na aplicação Portal da Empresa <!-- 1832222 -->
Estamos a rever as mensagens que são apresentadas aos utilizadores dos dispositivos quando um dispositivo não está em conformidade. As mensagens irão manter o significado original, mas serão atualizadas de modo a incluir uma linguagem mais simples e com menos termos técnicos. Também estamos a atualizar as ligações para documentação e passos de remediação.  

O seguinte exemplo do texto anterior e do novo demonstra as melhorias que poderá ver nas mensagens:  

Anterior: *Este dispositivo não contactou o serviço do Intune no período de tempo especificado exigido pelo seu administrador de TI. Para resolver este problema, abra a aplicação Portal da Empresa no seu dispositivo e clique no botão Verificar Conformidade.*  

Novo: *O seu dispositivo não é verificado pela sua organização há algum tempo. Para voltar a estabelecer ligação, abra a aplicação Portal da Empresa no seu dispositivo e toque em Verificar Definições no mesmo*.  

### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Editar as implementações de aplicações do Office 365 Pro Plus <!-- 2150145 -->
Enquanto administrador do Microsoft Intune, terá maior capacidade de editar as suas implementações de aplicações do Office 365 Pro Plus. No portal do Azure, selecione **Microsoft Intune** > **Aplicações móveis** > **Aplicações**. A partir da lista de aplicações, selecione o Office 365 Pro Plus Suite.  

### <a name="per-row-review-of-duplicate-corporate-device-identifiers-uploaded----2203794---"></a>Revisão por linha de identificadores de dispositivos da empresa duplicados carregados <!-- 2203794 -->
Ao carregar IDs empresariais, o Intune fornece uma lista de duplicados e dá-lhe a opção de substituir ou manter as informações existentes. O relatório será apresentado se existirem duplicados após selecionar **Inscrição do dispositivo** > **Identificadores de Dispositivo da Empresa** > **Adicionar Identificadores**. 

### <a name="manually-add-corporate-device-identifiers----2203803---"></a>Adicionar manualmente identificadores de dispositivos da empresa <!-- 2203803 -->
Poderá adicionar manualmente IDs de dispositivos da empresa. Selecione **Inscrição de dispositivos** > **Identificadores de Dispositivo da Empresa** > **Adicionar**.

### <a name="new-status-for-devices-in-device-compliance----2308882---"></a>Novo estado dos dispositivos em Conformidade do dispositivo <!-- 2308882 -->
Em **Conformidade do dispositivo** > **Políticas** > selecione uma política > **Descrição geral**, serão adicionados os novos estados seguintes:
- com êxito
- erro
- conflito
- pendente
- não aplicável

Também é apresentada uma imagem que mostra a contagem de dispositivos de uma plataforma diferente. Por exemplo, se observar um perfil iOS, o novo mosaico mostra a contagem de dispositivos não iOS atribuídos a este perfil. 

### <a name="device-compliance-supports-3rd-party-anti-virus-solutions----2325484---"></a>A conformidade do dispositivo suporta soluções de antivírus de terceiros <!-- 2325484 -->
Quando cria uma política de conformidade do dispositivo (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Plataforma: Windows 10** > **Definições** > **Segurança do sistema**), estarão disponíveis novas opções de **Segurança do Dispositivo**: 
- **Antivírus**: quando estiver definido como **Exigir**, pode verificar a conformidade com soluções de antivírus registadas com o Centro de Segurança do Windows, tal como Symantec. 
- **Antisspyware**: quando estiver definido como **Exigir**, pode verificar a conformidade com soluções de antisspyware registadas com o Centro de Segurança do Windows, tal como Symantec. 

Aplica-se a: Windows 10 e posterior 

<!-- 1805 start -->

### <a name="improved-troubleshooting-for-app-installation----928990---"></a>Melhorias na resolução de problemas de instalação de aplicações <!-- 928990 -->
Por vezes, a instalação de aplicações em dispositivos geridos por MDM do Microsoft Intune pode falhar. Quando uma instalação de aplicações falha, pode ser difícil compreender o motivo da falha ou resolver o problema. Vamos lançar uma Pré-visualização Pública das nossas funcionalidades de Resolução de Problemas de Aplicações. Verá um novo nó em cada dispositivo denominado **Aplicações Geridas**. Este nó apresenta as aplicações que foram enviadas através do Intune MDM. Dentro do nó, verá uma lista de estados de instalação das aplicações. Se selecionar uma única aplicação, ser-lhe-á apresentada a vista de resolução de problemas dessa aplicação específica. Na vista de resolução de problemas, verá o ciclo de vida ponto a ponto da aplicação, por exemplo quando é que a aplicação foi criada, modificada, visada e enviada para um dispositivo. Além disso, se a instalação da aplicação não tiver sido concluída com êxito, ser-lhe-á apresentado o código de erro e uma mensagem útil sobre a causa do erro.

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Exigir código de acesso não biométrico na inicialização da aplicação progressiva e tempo limite <!-- 1506985 --> 

Ao exigir um código de acesso não biométrico na inicialização da aplicação progressiva e após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloquear o acesso a aplicações baseado em fornecedores e modelos de dispositivos não aprovados <!-- 1425689 ! -->
O administrador de TI do Intune poderá impor uma lista específica de fabricantes Android e/ou de modelos iOS nas Políticas de Proteção de Aplicações do Intune. O administrador de TI pode fornecer uma lista separada por ponto e vírgula de fabricantes para políticas para Android e de modelos de dispositivos para políticas iOS. As Políticas de Proteção de Aplicações do Intune destinam-se apenas a Android e iOS. Existirão duas ações separadas que podem ser realizadas na lista especificada:
- O bloqueio do acesso a aplicações em dispositivos não especificados.
- Uma eliminação seletiva de dados empresariais em dispositivos não especificados. 

O utilizador não conseguirá aceder à aplicação visada se os requisitos da política não forem cumpridos. Com base nas definições escolhidas, os dados empresariais do utilizador podem ser bloqueados ou eliminados seletivamente da aplicação. Em dispositivos iOS, esta funcionalidade requer que a participação das aplicações (por exemplo, o WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune para que as definições de versão mínima sejam impostas nas aplicações visadas. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. No Android, esta funcionalidade necessita da versão mais recente do Portal da Empresa. 

Nos dispositivos dos utilizadores finais, o cliente do Intune toma medidas com base numa única correspondência das cadeias especificadas no painel Intune das Políticas de Proteção de Aplicações. Isto depende inteiramente do valor comunicado pelo dispositivo. Como tal, recomendamos que o administrador de TI se certifique de que o comportamento pretendido é preciso. Pode fazê-lo ao testar esta definição com base em vários fabricantes e modelos de dispositivos direcionados para um grupo de utilizadores pequeno. No Microsoft Intune, selecione **Aplicações móveis** > **Políticas de proteção de aplicações** para ver e adicionar políticas de proteção de aplicações. Para obter mais informações sobre políticas de proteção de aplicações, veja [What are app protection policies](app-protection-policy.md) (O que são as políticas de proteção de aplicações?).

### <a name="access-actions-for-app-protection-policies----1483510-eeready---"></a>Ações de acesso das políticas de proteção de aplicações <!-- 1483510 EEready -->
Brevemente, poderá configurar políticas de proteção de aplicações para avisar, apagar ou bloquear explicitamente dispositivos que não estiverem em conformidade. A ação mais recente, denominada *Apagar*, remove os seus dados empresariais de um dispositivo. Se ocorrer uma eliminação, o utilizador do dispositivo será notificado sobre os motivos da eliminação e os passos de remediação. Para algumas definições, como a versão mínima do SO, poderá realizar múltiplas ações, tais como bloquear e apagar. Estas ações são acionadas quando a aplicação é iniciada.

<!-- 1804 start -->

### <a name="rules-for-removing-devices----1609459---"></a>Regras para remover dispositivos <!-- 1609459 -->
Estarão disponíveis novas regras que lhe permitem remover automaticamente dispositivos que não se tenham registado durante o número de dias que definir. Para ver a nova regra, aceda ao painel **Intune**, selecione **Dispositivos** e selecione **Regras de remoção de dispositivo**.

<!-- 1803 start -->

### <a name="ability-to-deploy-required-line-of-business-lob-apps-to-all-users-on-windows-10-desktop-devices----1627835-rs4---"></a>Capacidade de implementar as aplicações de linha de negócio (LOB) necessárias em Todos os Utilizadores com computadores com o Windows 10 <!-- 1627835 RS4 -->
Os clientes poderão implementar as aplicações do Windows 10 de linha de negócio necessárias para as instalar em dispositivos. Isto permitirá que estas aplicações fiquem disponíveis para todos os utilizadores no dispositivo. Isto só é aplicável a computadores com o Windows 10.

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Atualizar a experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android <!--1631531 -->

A experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android será atualizada para estarmos alinhados com as melhores práticas para aplicações Android. A aplicação Portal da Empresa para Android será atualizada nos próximos meses para dividir o item de menu **Ajuda e Feedback** em itens de menu **Ajuda** e **Enviar Feedback** separados. A página **Ajuda** terá uma secção de **Perguntas Frequentes** e o botão **Suporte por E-mail** para que os utilizadores finais carreguem registos para a Microsoft e enviem e-mails para a empresa de suporte com a descrição do problema. O menu **Enviar Feedback** orientará o utilizador ao longo do processo padrão de submissão de feedback da Microsoft, que lhe pedirá para escolher entre "Gosto de algumas coisas", "Não de gosto de algumas coisas" ou "Tenho uma ideia".

<!-- the following are present prior to 1801 -->

### <a name="app-protection-policies-----679615---"></a>Políticas de Proteção de Aplicações <!-- 679615 -->
As Políticas de Proteção de Aplicações do Intune permitirão criar políticas predefinidas globais para ativar rapidamente a proteção em todos os utilizadores em todo o inquilino.

<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.

### <a name="see-also"></a>Veja também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.