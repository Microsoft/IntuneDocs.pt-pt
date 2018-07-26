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
ms.openlocfilehash: 3aed8fcefd640e5b7df46fe1ef8cd1c973a68044
ms.sourcegitcommit: 5251a630fb2c7a2e6f86abd84ab887f8eabc1481
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/23/2018
ms.locfileid: "39212142"
---
# <a name="the-early-edition-for-microsoft-intune---july-2018"></a>A edição antecipada do Microsoft Intune – julho de 2018

> [!Note]
> Notificação de contrato de confidencialidade: as seguintes alterações estão em desenvolvimento para o Intune. Estas informações são partilhadas ao abrigo de um contrato de confidencialidade numa base muito limitada. Não publique estas informações em redes sociais ou em sites públicos como o Twitter, UserVoice, Reddit, entre outros. 

A **edição antecipada** oferece uma lista de funcionalidades, partilhadas ao abrigo de um contrato de confidencialidade, que estarão disponíveis em versões futuras do Microsoft Intune. Esta informação é fornecida numa base limitada e está sujeita a alterações. Não publique no Twitter nem no UserVoice, nem partilhe estas informações de nenhuma outra forma com pessoas fora da sua empresa. Algumas funcionalidades aqui indicadas estão em risco de não serem incluídas dentro das datas limite e podem ser adiadas até uma versão futura. Outras funcionalidades estão a ser testadas numa implementação piloto (distribuição de pacotes piloto) para garantir que estão prontas para os clientes. Contacte o seu contacto do grupo de produtos da Microsoft se tiver dúvidas ou preocupações.

Esta página é atualizada periodicamente. Volte a consultar posteriormente para obter mais atualizações.

<!--
## What's coming to Intune in the Azure portal  
## What's coming to Intune apps
## Notices
-->
 
## <a name="intune-in-the-azure-portal"></a>Intune no portal do Azure

<!-- 1807 start -->

### <a name="more-sync-opportunities-in-the-company-portal-app-for-windows----2683177---"></a>Mais oportunidades de sincronização na aplicação Portal da Empresa para Windows <!-- 2683177 -->
A aplicação Portal da Empresa para Windows irá adicionar uma ação de sincronização de dispositivos à barra de tarefas do Windows e às listas de atalhos do menu Iniciar. Clique em qualquer uma das localizações para sincronizar rapidamente os seus dispositivos e obter acesso a recursos empresariais.  

### <a name="reset-device-passcodes-from-company-portal-app-for-windows-10----2101282---"></a>Repor códigos de acesso de dispositivos a partir da aplicação Portal da Empresa para Windows 10 <!-- 2101282 --> 
Em breve, os seus colaboradores poderão repor o PIN ou o código de acesso dos respetivos dispositivos diretamente a partir da aplicação Portal da Empresa para Windows 10. Esta funcionalidade estará disponível em dispositivos remotos e locais geridos pelo Intune que suportem a reposição de códigos de acesso. Consoante o tipo de dispositivo, um pedido feito para um dispositivo remoto irá remover o código de acesso atual do dispositivo ou criar um código de acesso temporário. Os utilizadores que efetuarem um pedido de reposição para um dispositivo local serão redirecionados para a aplicação Definições do dispositivo.  

### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows----2317227---"></a>Novas experiências de navegação na aplicação Portal da Empresa para Windows <!-- 2317227 -->  
Ao navegar ou procurar aplicações na aplicação Portal da Empresa para Windows, terá a possibilidade de alternar entre a vista **Mosaicos** existente e a vista **Detalhes** recentemente adicionada. A nova vista apresenta os detalhes das aplicações, como o nome, o publicador, a data de publicação e o estado da instalação.  

A página **Aplicações** irá apresentar uma vista **Instalado** que lhe permite ver detalhes sobre as instalações de aplicações concluídas e em curso. Quer partilhar feedback ou ideias sobre as novas alterações? Envie-nos o seu feedback na aplicação Portal da Empresa.

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Experiência da aplicação Portal da Empresa melhorada para gestores de inscrições de dispositivos <!-- 675800 -->
Quando um gestor de inscrições de dispositivos (DEM) inicia sessão na aplicação Portal da Empresa para Windows, a aplicação só apresentará o dispositivo atual do DEM. Esta melhoria irá reduzir os erros de tempo limite que ocorriam quando a aplicação tentava carregar todos os dispositivos inscritos pelo DEM.  

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

###  <a name="windows-line-of-business-lob-apps-file-extensions----1884873---"></a>Extensões de ficheiros de aplicações de linha de negócio (LOB) do Windows <!-- 1884873 -->
As extensões de ficheiros de aplicações de linha de negócio do Windows agora incluirão *.msi*, *.appx*, *.appxbundle*, *.msix* e *.msixbundle*. Pode adicionar uma aplicação no Microsoft Intune ao selecionar **Aplicações móveis** > **Aplicações** > **Adicionar**. O painel **Adicionar aplicação** é apresentado, o qual lhe permite selecionar o **Tipo de aplicação**. Para aplicações LOB do Windows, selecione o tipo de aplicação **Linha de negócio**, selecione o **Ficheiro de pacote de aplicação** e, em seguida, introduza um ficheiro de instalação com a extensão adequada.

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


### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Os teclados de terceiros podem ser bloqueados por definições de APP no iOS <!-- 1248481 -->
Em dispositivos iOS, os administradores do Intune poderão bloquear a utilização de teclados de terceiros ao aceder a dados da organização em aplicações protegidas por políticas. Quando a Política de Proteção de Aplicações (APP) estiver definida para bloquear teclados de terceiros, o utilizador do dispositivo irá receber uma mensagem da primeira vez que interagir com dados da empresa ao utilizar um teclado de terceiros. Todas as opções, além do teclado nativo, serão bloqueadas e os utilizadores de dispositivos não irão vê-las. Os utilizadores de dispositivos só verão a mensagem de diálogo uma vez. 

### <a name="create-device-compliance-policy-using-firewall-settings-on-macos-devices----1497640---"></a>Criar política de conformidade de dispositivos com as definições de firewall em dispositivos macOS <!-- 1497640 -->
Quando criar uma nova política de conformidade do macOS (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Plataforma: macOS** > **Segurança do sistema**), estarão disponíveis algumas definições de **Firewall** novas: 
- **Firewall**: configure a forma como as ligações de entrada são processadas no seu ambiente.
- **Ligações de entrada**: **bloqueia** todas as ligações de entrada, exceto as ligações necessárias para serviços básicos de Internet, tal como o DHCP, Bonjour e IPSec. Esta definição também bloqueia todos os serviços de partilha.
- **Modo invisível**: **ative** o modo invisível para impedir que o dispositivo responda aos pedidos de pesquisa. O dispositivo continua a responder a pedidos recebidos de aplicações autorizadas.

Aplica-se a: macOS 10.12 e posterior

### <a name="require-non-biometric-passcode-on-app-launch-and-timeout----1506985---"></a>Exigir código de acesso não biométrico na inicialização da aplicação e após o tempo limite <!-- 1506985 -->

Ao exigir um código de acesso não biométrico na inicialização da aplicação e após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Pacotes de Idiomas do Office 365 Pro Plus <!-- 1833450 -->
Enquanto administrador do Intune, poderá implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal do Azure, selecione **Microsoft Intune** > **Aplicações móveis** > **Aplicações** > **Adicionar**. Na lista **Tipo de aplicação**, no painel **Adicionar aplicação**, selecione **Windows 10** em **Office 365 Suite**. Selecione **Idiomas** no painel **Definições do Conjunto de Aplicações**.

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


### <a name="edit-your-office-365-pro-plus-app-deployments----2150145---"></a>Editar as implementações de aplicações do Office 365 Pro Plus <!-- 2150145 -->
Enquanto administrador do Microsoft Intune, terá maior capacidade de editar as suas implementações de aplicações do Office 365 Pro Plus. No portal do Azure, selecione **Microsoft Intune** > **Aplicações móveis** > **Aplicações**. A partir da lista de aplicações, selecione o Office 365 Pro Plus Suite.  

<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Exigir código de acesso não biométrico na inicialização da aplicação progressiva e tempo limite <!-- 1506985 --> 

Ao exigir um código de acesso não biométrico na inicialização da aplicação progressiva e após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.

### <a name="block-app-access-based-on-unapproved-device-vendors-and-models-----1425689----"></a>Bloquear o acesso a aplicações baseado em fornecedores e modelos de dispositivos não aprovados <!-- 1425689 ! -->
O administrador de TI do Intune poderá impor uma lista específica de fabricantes Android e/ou de modelos iOS nas Políticas de Proteção de Aplicações do Intune. O administrador de TI pode fornecer uma lista separada por ponto e vírgula de fabricantes para políticas para Android e de modelos de dispositivos para políticas iOS. As Políticas de Proteção de Aplicações do Intune destinam-se apenas a Android e iOS. Existirão duas ações separadas que podem ser realizadas na lista especificada:
- O bloqueio do acesso a aplicações em dispositivos não especificados.
- Uma eliminação seletiva de dados empresariais em dispositivos não especificados. 

O utilizador não conseguirá aceder à aplicação visada se os requisitos da política não forem cumpridos. Com base nas definições escolhidas, os dados empresariais do utilizador podem ser bloqueados ou eliminados seletivamente da aplicação. Em dispositivos iOS, esta funcionalidade requer que a participação das aplicações (por exemplo, o WXP, Outlook, Managed Browser, Yammer) integre o SDK da Aplicação Intune para que as definições de versão mínima sejam impostas nas aplicações visadas. Esta integração decorre de forma gradual e está dependente das equipas específicas da aplicação. No Android, esta funcionalidade necessita da versão mais recente do Portal da Empresa. 

Nos dispositivos dos utilizadores finais, o cliente do Intune toma medidas com base numa única correspondência das cadeias especificadas no painel Intune das Políticas de Proteção de Aplicações. Isto depende inteiramente do valor comunicado pelo dispositivo. Como tal, recomendamos que o administrador de TI se certifique de que o comportamento pretendido é preciso. Pode fazê-lo ao testar esta definição com base em vários fabricantes e modelos de dispositivos direcionados para um grupo de utilizadores pequeno. No Microsoft Intune, selecione **Aplicações móveis** > **Políticas de proteção de aplicações** para ver e adicionar políticas de proteção de aplicações. Para obter mais informações sobre políticas de proteção de aplicações, veja [What are app protection policies](app-protection-policy.md) (O que são as políticas de proteção de aplicações?).


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

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.
