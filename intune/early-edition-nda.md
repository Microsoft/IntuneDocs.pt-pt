---
title: Edição antecipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 07/25/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: ad49b983bd5dc72a3355cba5645192456a555e38
ms.sourcegitcommit: e8e8164586508f94704a09c2e27950fe6ff184c3
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/27/2018
ms.locfileid: "39321259"
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


### <a name="check-for-sccm-compliance----2192052---"></a>Verificar a conformidade com o SCCM <!-- 2192052 -->
Uma futura atualização irá incluir uma nova definição de conformidade do System Center Configuration Manager (SCCM) (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Windows 10**). O SCCM envia sinais de conformidade ao Intune. Com a definição do Intune, pode exigir que todos os sinais do SCCM devolvam o estado "compatível".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No SCCM, este requisito apresenta o estado "Instalado". Se algum dos programas no dispositivo apresentar um estado desconhecido, o dispositivo será marcado como não compatível no Intune.

Aplica-se ao Windows 10 e posterior

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas de token VPP prestes a expirar ou de licenças do Portal da Empresa que se estão a esgotar <!-- 2237572 -->
Se utilizar o Programa de Compras em Volume (VPP) para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP, o Intune irá alertá-lo quando o token VPP estiver prestes a expirar e quando as licenças do Portal da Empresa se estiverem a esgotar.

### <a name="confirmation-required-to-delete-vpp-token-that-is-being-used-for-company-portal-pre-provisioning----2237634---"></a>Confirmação necessária para eliminar o token VPP que está a ser utilizado para aprovisionar previamente o Portal da Empresa <!-- 2237634 -->
Será pedida uma confirmação para eliminar um token de Programa de Compras em Volume (VPP) se o mesmo estiver a ser utilizado para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP.


#### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Definições de segurança adicionais para o Windows Installer <!-- 2282430 -->
Poderá permitir que os utilizadores controlem a instalação de aplicações. Se estiver ativada, esta definição permite continuar as instalações que, caso contrário, seriam interrompidas devido a uma violação de segurança. Poderá configurar o Windows Installer para utilizar permissões elevadas ao instalar programas num sistema. Além disso, poderá ativar os itens do Windows Information Protection (WIP) para serem indexados e os metadados acerca dos mesmos para serem armazenados numa localização não encriptada. Quando a política estiver desativada, os itens protegidos pelo WIP não serão indexados e não serão apresentados nos resultados na Cortana ou no explorador de ficheiros. A funcionalidade destas opções estará desativada por predefinição. 


<!-- 1806 start -->


### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Os teclados de terceiros podem ser bloqueados por definições de APP no iOS <!-- 1248481 -->
Em dispositivos iOS, os administradores do Intune poderão bloquear a utilização de teclados de terceiros ao aceder a dados da organização em aplicações protegidas por políticas. Quando a Política de Proteção de Aplicações (APP) estiver definida para bloquear teclados de terceiros, o utilizador do dispositivo irá receber uma mensagem da primeira vez que interagir com dados da empresa ao utilizar um teclado de terceiros. Todas as opções, além do teclado nativo, serão bloqueadas e os utilizadores de dispositivos não irão vê-las. Os utilizadores de dispositivos só verão a mensagem de diálogo uma vez. 

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


<!-- 1805 start -->

### <a name="require-non-biometric-passcode-on-cold-app-launch-and-timeout----1506985---"></a>Exigir código de acesso não biométrico na inicialização da aplicação progressiva e tempo limite <!-- 1506985 --> 

Ao exigir um código de acesso não biométrico na inicialização da aplicação progressiva e após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.


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
