---
title: Edição antecipada
description: ''
keywords: ''
author: ErikjeMS
ms.author: erikje
manager: dougeby
ms.date: 09/4/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f49650f4-31fa-406c-a4da-d8c9a4a8384d
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: cacampbell
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: beee1462c1b6e683287b4d304df386ce525be820
ms.sourcegitcommit: 8fdddb684ecf5eabf071907168413bcd89a2f702
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/07/2018
ms.locfileid: "44141648"
---
# <a name="the-early-edition-for-microsoft-intune---september-2018"></a>Edição antecipada do Microsoft Intune – setembro de 2018

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

<!-- 1809 start -->

### <a name="user-account-access-of-intune-apps-on-managed-android-and-ios-devices-----1248496----"></a>Acesso a contas de utilizadores por parte de aplicações do Intune em dispositivos Android e iOS geridos <!-- ! 1248496  -->

Enquanto administrador do Microsoft Intune, poderá controlar as contas de utilizadores que são adicionadas a aplicações do Microsoft Office em dispositivos geridos. Poderá limitar o acesso exclusivamente a contas de utilizadores autorizadas e bloquear contas pessoais em dispositivos inscritos. 

### <a name="create-dns-suffixes-in-vpn-configuration-profiles-on-devices-running-windows-10----1333668---"></a>Criar sufixos DNS em perfis de configuração VPN em dispositivos com o Windows 10 <!-- 1333668 -->
Quando criar um perfil de configuração de um dispositivo VPN (**Configuração do dispositivo** > **Perfis** > **Criar perfil** >  plataforma **Windows 10 e versões posteriores** > tipo de perfil **VPN**), terá de introduzir algumas definições de DNS. Também poderá introduzir múltiplos **sufixos DNS** no Intune. Quando utilizar sufixos DNS, pode procurar um recurso de rede através do respetivo nome abreviado, em vez do nome de domínio completamente qualificado (FQDN). Esta atualização também permite alterar a ordem dos sufixos DNS no Intune.
O artigo [Definições de VPN do Windows 10](vpn-settings-windows-10.md#dns-settings) indica as definições de DNS atuais.
Aplica-se a: dispositivos com o Windows 10

### <a name="support-for-always-on-vpn-for-android-enterprise-work-profiles----1333705---"></a>Suporte para VPN Sempre Ativada para perfis de trabalho do Android Enterprise <!-- 1333705 -->
Poderá utilizar ligações VPN Sempre Ativada em dispositivos Android Enterprise com perfis de trabalho geridos. As ligações VPN Sempre Ativada permanecem ativadas ou voltam a ativar-se quando o utilizador desbloqueia o dispositivo, quando o dispositivo é reiniciado ou quando a rede sem fios é alterada. Também pode colocar a ligação em modo de "bloqueio". Este modo permite bloquear todo o tráfego de rede até à ativação da ligação de VPN.
A definição de VPN Sempre Ativada estará em **Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Android Enterprise** para a plataforma > **Restrições do dispositivo** em **Apenas Perfis de Trabalho** para Tipo de perfil > definições de **Conectividade**. 

### <a name="outlook-for-ios-and-android-app-configuration-policy---1828527---"></a>Política de configuração da aplicação Outlook para iOS e Android <!--1828527 -->
Poderá criar uma política de configuração da aplicação Outlook para iOS e Android. Serão adicionadas outras definições de configuração à medida que sejam ativadas para o Outlook para iOS e Android.

### <a name="remotely-lock-noncompliant-devices----2064495---"></a>Bloquear remotamente dispositivos que não estejam em conformidade <!-- 2064495 -->
Quando um dispositivo não estiver em conformidade, poderá criar uma ação na política de conformidade que bloqueie remotamente o dispositivo. No Intune > **Conformidade do dispositivo**, crie uma nova política ou selecione uma política existente. Selecione **Ações para não conformidade** > **Adicionar** e selecione a opção para bloquear remotamente o dispositivo.
Suportado no: 
- Android
- iOS
- macOS
- Windows 10 Mobile 
- Windows Phone 8.1 e posterior 

### <a name="intune-app-data-transfer-settings-on-ios-mdm-enrolled-devices----2244713---"></a>Definições de transferência de dados de aplicações do Intune em dispositivos iOS inscritos na MDM <!-- 2244713 -->
Poderá separar o controlo das definições de transferência de dados de aplicações do Intune em dispositivos iOS inscritos na MDM ao especificar a identidade do utilizador inscrito. Os administradores que não utilizarem o IntuneMAMUPN não notarão a existência de uma alteração de comportamento. Quando esta funcionalidade estiver disponível, os administradores que utilizam o IntuneMAMUPN para controlar o comportamento de transferência de dados em dispositivos inscritos devem rever as novas definições e atualizar as respetivas definições das aplicações conforme necessário.

### <a name="use-a-pre-shared-key-in-a-windows-10-wi-fi-profile----2662938---"></a>Utilizar uma chave pré-partilhada num perfil de Wi-Fi do Windows 10 <!-- 2662938 -->
Poderá utilizar uma chave pré-partilhada (PSK) com o protocolo de segurança WPA/WPA2-Pessoal para autenticar um perfil de configuração de Wi-Fi para o Windows 10.
Atualmente, tem de importar um perfil de Wi-Fi ou criar um perfil personalizado para utilizar uma chave pré-partilhada. O artigo [Definições de Wi-Fi para o Windows 10](wi-fi-settings-windows.md) indica as definições atuais. 

### <a name="autopilot-device-sync-frequency-increasing-to-every-12-hours----2753673---"></a>Aumentar a frequência de sincronização de dispositivos Autopilot para que seja de 12 em 12 horas <!-- 2753673 -->
Os dispositivos Autopilot sincronizarão de 12 em 12 horas, em vez de a cada 24 horas.

### <a name="apply-autopilot-profile-to-enrolled-win-10-devices-not-already-registered-for-autopilot----1558983---"></a>Aplicar um perfil do Autopilot a dispositivos com o Windows 10 inscritos e que ainda não estejam registados no Autopilot <!-- 1558983 -->
Pode aplicar um perfil do Autopilot a dispositivos com o Windows 10 inscritos e que ainda não tenham sido registados no Autopilot. No perfil do Autopilot, selecione a opção **Converter todos os dispositivos visados para o Autopilot** para registar automaticamente dispositivos não Autopilot com o serviço de implementação do Autopilot. O processo de registo demora até 48 horas, pelo que deverá aguardar. Quando a inscrição do dispositivo for anulada e o dispositivo for reposto, o Autopilot aprovisioná-lo-á. 

### <a name="create-and-assign-multiple-enrollment-status--page-profiles-to-azure-ad-groups----2526564--"></a>Criar e atribuir múltiplos perfis de Página de Estado de Inscrição a grupos do Azure AD <!-- 2526564-->
Poderá criar e atribuir múltiplos perfis de Página de Estado de Inscrição a grupos de utilizadores do Azure AD.

### <a name="intune-landing-page-updates-and-node-rename---2867309---"></a>Mudança de nome de nós e atualizações da página de destino do Intune <!--2867309 -->
As atualizações da página de destino do Intune incluirão gráficos e mosaicos de monitorização novos e alterados para uma melhor visualização dos dados. O nó **Aplicações móveis** mudará para **Aplicações cliente**.

### <a name="increased-end-user-access-using-the-company-portal-app----772203---"></a>Acesso por parte dos utilizadores finais alargado com recurso à aplicação Portal da Empresa <!-- 772203 -->
Os utilizadores finais poderão aceder às principais ações de conta, tais como a reposição de palavra-passe e o respetivo perfil do AAD, a partir da aplicação Portal da Empresa.

### <a name="issue-scep-certificates-to-user-less-devices----1744554---"></a>Emitir certificados SCEP para dispositivos sem utilizador <!-- 1744554 -->
De momento, os certificados são emitidos para utilizadores. Poderá emitir certificados SCEP para dispositivos, incluindo para dispositivos sem utilizador, tais como quiosques (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e versões posteriores** para a plataforma > **Certificado SCEP** para o perfil). Outras atualizações incluirão o seguinte:
- A propriedade **Requerente** nos perfis SCEP é agora uma caixa de texto personalizada e pode incluir novas variáveis. 
- A propriedade **Nome alternativo do requerente (SAN)** nos perfis SCEP tem agora um formato de tabela e pode incluir novas variáveis. Na tabela, os administradores podem adicionar um atributo e preencher o valor numa caixa de texto personalizada. O SAN suportará os seguintes atributos: 
  - DNS
  - Endereço de e-mail
  - UPN Estas variáveis novas podem ser adicionadas com texto estático numa caixa de texto de valor personalizado. Por exemplo, o atributo de DNS pode ser adicionado como `DNS = {{AzureADDeviceId}}.domain.com`.
  > [!NOTE]
  > As chavetas, os pontos e vírgulas e as barras verticais " { } ; | " não funcionarão no texto estático do SAN. As chavetas só podem delimitar uma das novas variáveis de certificado de dispositivo para que sejam aceites em `Subject` ou `Subject alternative name`. Variáveis de certificado de dispositivo novas:  
```
"{{AAD_Device_ID}}",
"{{Device_Serial}}",
"{{Device_IMEI}}",
"{{SerialNumber}}",
"{{IMEINumber}}",
"{{AzureADDeviceId}}",
"{{WiFiMacAddress}}",
"{{IMEI}}",
"{{DeviceName}}",
"{{FullyQualifiedDomainName}}",
"{{MEID}}",
```

> [!NOTE]
>  - `{{FullyQualifiedDomainName}}` só funciona em dispositivos com Windows e dispositivos associados a um domínio. 
>  -  Quando especificar as propriedades do dispositivo, tais como o IMEI, o Número de Série e o Nome de Domínio Completamente Qualificado, no requerente ou no SAN de um certificado de dispositivo, tenha em atenção que estas propriedades podem ser falsificadas por uma pessoa que tenha acesso ao dispositivo. 

O artigo [Criar um perfil de certificado SCEP](certificates-scep-configure.md#create-a-scep-certificate-profile) indica as variáveis atuais durante a criação de um perfil de configuração SCEP. 

Aplica-se a: Windows 10 e versões posteriores e ao iOS, com suporte para Wi-Fi



<!-- 1808 start -->

### <a name="apple-vpp-token-used-by-another-mdm----1488946---"></a>Token Apple VPP utilizado por outra MDM <!-- 1488946 -->
O Intune irá detetar e mostrar detalhes se um token de programa de compras em volume (VPP) da Apple estiver a ser utilizado pelo Intune e outra MDM.

### <a name="ios-version-number-and-build-number-are-shown----1892471---"></a>O número da versão do iOS e o número de compilação são apresentados <!-- 1892471 -->
Em **Conformidade do dispositivo** > **Conformidade do dispositivo**, é apresentada a versão do sistema operativo iOS. Numa atualização futura, também será apresentado o número de compilação.
Quando as atualizações de segurança são lançadas, normalmente, a Apple não altera o número da versão, mas atualiza o número de compilação. Ao apresentar o número de compilação, pode verificar facilmente se foi instalada uma atualização da vulnerabilidade.

### <a name="retired-devices-in-the-device-compliance-dashboard----1981119---"></a>Dispositivos extintos no dashboard de conformidade do dispositivo <!-- 1981119 -->
Numa atualização futura, os dispositivos extintos serão removidos do dashboard de conformidade do dispositivo. Tal irá alterar os seus números de conformidade.


### <a name="change-in-the-update-process-for-on-premises-connectors----2277554---"></a>Alteração no processo de atualização de conectores no local <!-- 2277554 -->
Com base no feedback dos clientes, a forma como as atualizações são realizadas nos conectores no local será alterada. Depois da instalação inicial de um conector no local, as atualizações serão automáticas. Esta alteração começará com o novo PFX Certificate Connector para o Microsoft Intune e, em seguida, estender-se-á a outros tipos de conectores no local. 

### <a name="windows-10-and-later-kiosk-profile-improvements-in-the-azure-portal----2748224-eeready---"></a>Melhorias ao nível do perfil de Quiosque do Windows 10 e versões posteriores no portal do Azure <!-- 2748224 eeready -->
O perfil de configuração de dispositivos de Quiosque do Windows 10 (**Configuração do dispositivo** > **Perfis** > **Criar perfil** > **Windows 10 e versões posteriores** para a plataforma > **Pré-visualização de quiosque** para o tipo de perfil) será melhorado: 
- Atualmente, pode criar múltiplos perfis de quiosque no mesmo dispositivo. Com esta atualização, o Intune suportará apenas um perfil de quiosque por dispositivo. Se continuar a necessitar de múltiplos perfis de quiosque num só dispositivo, pode utilizar um URL personalizado.
– Num perfil **Quiosque de várias aplicações**, pode selecionar o tamanho e a ordem dos mosaicos das aplicações para o **Esquema do menu Iniciar** na grelha das aplicações. Se preferir um nível superior de personalização, pode avançar para carregar um ficheiro XML.
- As definições do Browser de Quiosque estão a passar para as definições de **Quiosque**. Neste momento, as definições do **browser de Quiosque** têm a sua própria categoria no portal do Azure.
Aplica-se a: Windows 10 e posterior

<!-- 1807 start -->

### <a name="improved-company-portal-app-experience-for-device-enrollment-manager-users----675800---"></a>Experiência da aplicação Portal da Empresa melhorada para gestores de inscrições de dispositivos <!-- 675800 -->
Quando um gestor de inscrições de dispositivos (DEM) inicia sessão na aplicação Portal da Empresa para Windows, a aplicação só apresentará o dispositivo atual do DEM. Esta melhoria irá reduzir os erros de tempo limite que ocorriam quando a aplicação tentava carregar todos os dispositivos inscritos pelo DEM.  

### <a name="check-for-configuration-manager-compliance----2192052---"></a>Verificar a conformidade do Configuration Manager <!-- 2192052 -->
Uma futura atualização irá incluir uma nova definição de conformidade do System Center Configuration Manager (**Conformidade do dispositivo** > **Políticas** > **Criar política** > **Windows 10**). O Configuration Manager envia sinais de conformidade ao Intune. Com a definição do Intune, pode exigir que todos os sinais do Configuration Manager devolvam o estado "conforme".

Por exemplo, pode exigir que todas as atualizações do software sejam instaladas nos dispositivos. No Configuration Manager, este requisito apresenta o estado "Instalado". Se algum dos programas no dispositivo apresentar um estado desconhecido, o dispositivo será marcado como não compatível no Intune.

Aplica-se ao Windows 10 e posterior

### <a name="alerts-for-expiring-vpp-token-or-company-portal-license-running-low----2237572---"></a>Alertas de token VPP prestes a expirar ou de licenças do Portal da Empresa que se estão a esgotar <!-- 2237572 -->
Se utilizar o Programa de Compras em Volume (VPP) para aprovisionar previamente o Portal da Empresa durante a inscrição do DEP, o Intune irá alertá-lo quando o token VPP estiver prestes a expirar e quando as licenças do Portal da Empresa se estiverem a esgotar.

### <a name="additional-security-settings-for-windows-installer----2282430---"></a>Definições de segurança adicionais para o Windows Installer <!-- 2282430 -->
Poderá permitir que os utilizadores controlem a instalação de aplicações. Se estiver ativada, esta definição permite continuar as instalações que, caso contrário, seriam interrompidas devido a uma violação de segurança. Poderá configurar o Windows Installer para utilizar permissões elevadas ao instalar programas num sistema. Além disso, poderá ativar itens do Windows Information Protection (WIP) para serem indexados e os metadados acerca dos mesmos que estão armazenados numa localização não encriptada. Quando a política estiver desativada, os itens protegidos pelo WIP não serão indexados e não serão apresentados nos resultados na Cortana ou no explorador de ficheiros. A funcionalidade destas opções estará desativada por predefinição. 

<!-- 1806 start -->

### <a name="3rd-party-keyboards-can-be-blocked-by-app-settings-on-ios----1248481---"></a>Os teclados de terceiros podem ser bloqueados por definições de APP no iOS <!-- 1248481 -->
Em dispositivos iOS, os administradores do Intune poderão bloquear a utilização de teclados de terceiros ao aceder a dados da organização em aplicações protegidas por políticas. Quando a Política de Proteção de Aplicações (APP) estiver definida para bloquear teclados de terceiros, o utilizador do dispositivo irá receber uma mensagem da primeira vez que interagir com dados da empresa ao utilizar um teclado de terceiros. Todas as opções, além do teclado nativo, serão bloqueadas e os utilizadores de dispositivos não irão vê-las. Os utilizadores de dispositivos só verão a mensagem de diálogo uma vez. 

### <a name="office-365-pro-plus-language-packs----1833450---"></a>Pacotes de Idiomas do Office 365 Pro Plus <!-- 1833450 -->
Enquanto administrador do Intune, poderá implementar idiomas adicionais para aplicações do Office 365 Pro Plus geridas através do Intune. A lista de idiomas disponíveis inclui o **Tipo** do pacote de idiomas (núcleo, parcial e verificação). No portal do Azure, selecione **Microsoft Intune** > **Aplicações móveis** > **Aplicações** > **Adicionar**. Na lista **Tipo de aplicação**, no painel **Adicionar aplicação**, selecione **Windows 10** em **Office 365 Suite**. Selecione **Idiomas** no painel **Definições do Conjunto de Aplicações**.

<!-- 1805 start -->

### <a name="require-non-biometric-after-specified-timeout----1506985---"></a>Exigir um PIN não biométrico após o tempo limite especificado <!-- 1506985 --> 

Ao exigir um PIN não biométrico após o tempo limite especificado pelo administrador, o Intune irá fornecer segurança melhorada para aplicações com Gestão de Aplicações Móveis (MAM) ativada ao restringir a utilização da identificação biométrica para aceder a dados da empresa. As definições irão afetar os utilizadores que dependem do Touch ID (iOS), Face ID (iOS), Android Biometric ou outros métodos de autenticação biométricos futuros para aceder a aplicações com APP/MAM ativada. Estas definições poderão permitir que os administradores do Intune tenham um controlo mais abrangente sobre o acesso do utilizador, eliminando os casos em que um dispositivo com múltiplas impressões digitais ou outros métodos de acesso biométrico pode revelar dados da empresa a um utilizador errado. No portal do Azure, abra o **Microsoft Intune**. Selecione **Aplicações móveis** > **Políticas de proteção de aplicações** > **Adicionar uma política** > **Definições**. Localize a secção **Acesso** para obter definições específicas.

<!-- 1803 start -->

### <a name="updating-the-help-and-feedback-experience-on-company-portal-app-for-android---1631531---"></a>Atualizar a experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android <!--1631531 -->

A experiência de Ajuda e Feedback na aplicação Portal da Empresa para Android será atualizada para estarmos alinhados com as melhores práticas para aplicações Android. A aplicação Portal da Empresa para Android será atualizada nos próximos meses para dividir o item de menu **Ajuda e Feedback** em itens de menu **Ajuda** e **Enviar Feedback** separados. A página **Ajuda** terá uma secção de **Perguntas Frequentes** e o botão **Suporte por E-mail** para que os utilizadores finais carreguem registos para a Microsoft e enviem e-mails para a empresa de suporte com a descrição do problema. O menu **Enviar Feedback** orientará o utilizador ao longo do processo padrão de submissão de feedback da Microsoft, que lhe pedirá para escolher entre "Gosto de algumas coisas", "Não de gosto de algumas coisas" ou "Tenho uma ideia".



<!-- the following are present prior to 1711 -->

## <a name="notices"></a>Avisos

Neste momento, não existem avisos ativos.

### <a name="see-also"></a>Consulte também
Veja [Novidades do Microsoft Intune](whats-new.md) para obter detalhes sobre os desenvolvimentos recentes.



