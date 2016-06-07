---
# required metadata

title: Referência de políticas do Microsoft Intune | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: d27f2739-9791-4aae-a9db-01a4e59ccfe5

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Referência de políticas do Microsoft Intune

Utilize as informações neste tópico para ajudá-lo a decidir qual a política do Microsoft Intune a utilizar para gerir os seus dispositivos.

> Para obter mais informações detalhadas sobre como utilizar políticas, consulte [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)


## Políticas de configuração para Android

|Nome da política|Utilize-a quando pretende|
|---------------|------------------------|
|**Configuração personalizada (Android 4 e posterior, Samsung KNOX Standard 4.0 e posterior)**|Implementar definições OMA-URI, como definições de Wi-Fi que podem ser utilizadas para controlar funcionalidades do dispositivo. Isto é útil quando a definição necessária não se encontra disponível numa política de configuração.<br /><br />Para obter detalhes, consulte [Definições de política para Android no Microsoft Intune](android-policy-settings-in-microsoft-intune.md)|
|**Perfil de e-mail (Samsung KNOX Standard 4.0 e posterior)**|Crie, implemente e monitorize as definições de e-mail do Exchange Active Sync em dispositivos geridos. Para permitir que os utilizadores acedam a e-mails da empresa nos seus dispositivos pessoais sem precisarem de efetuar qualquer configuração.<br /><br />Para obter detalhes, consulte [Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)|
|**Configuração Geral (Android 4 e posterior, Samsung KNOX Standard 4.0 e posterior)**|Configurar as definições de segurança e funcionais do dispositivo móvel.<br />Especificar aplicações que são compatíveis ou não compatíveis e comunicar quando estão a ser utilizadas.<br />Configurar o modo de local público que bloqueia dispositivos para permitir que apenas determinadas funcionalidades funcionem, como, por exemplo, permitir que o dispositivo execute apenas uma aplicação ou desativar os botões de volume.<br /><br />Para obter detalhes, consulte [Definições de política para Android no Microsoft Intune](android-policy-settings-in-microsoft-intune.md)|
|**Perfil de Certificado PKCS #12 (.PFX) (Android 4 e posterior)**|Utilize este perfil para criar e implementar definições PFX para pedidos de certificação de dispositivos.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil de Certificado de SCEP (Android 4 e posterior)**|Para configurar um certificado de protocolo SCEP (Simple Certificate Enrollment Protocol) que pode ser utilizado com um certificado fidedigno do dispositivo móvel para autenticar dispositivos móveis para lhes permitir aceder a recursos de rede, como os que são configurados pelos perfis de Wi-Fi e da VPN.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil de Certificado Fidedigno (Android 4 e posterior)**|Para configurar um certificado fidedigno do dispositivo móvel que pode ser utilizado para autenticar dispositivos móveis para lhes permitir aceder a recursos de rede, como os que são configurados pelos perfis de Wi-Fi e da VPN.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil da VPN (Android 4 e posterior)**|Para configurar e implementar definições que permitem que os utilizadores acedam de forma segura à rede da empresa a partir dos seus dispositivos móveis. Ao implementar estas definições, minimiza o esforço que o utilizador final necessita para se ligar ao seu trabalho.<br /><br />Para obter detalhes, consulte [Ligações VPN no Microsoft Intune.md](vpn-connections-in-microsoft-intune.md)|
|**Perfil de Wi-Fi (Android 4 e posterior)**|Para configurar e implementar definições de rede sem fios aos utilizadores na sua organização. Ao implementar estas definições, minimiza o esforço que o utilizador final necessita para se ligar à rede sem fios.<br /><br />Para obter detalhes, consulte [Ligações Wi-Fi no Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)|

## Políticas de configuração para iOS

|Nome da política|Utilize-a quando pretende|
|---------------|------------------------|
|**Configuração Personalizada (iOS 7.1 e posterior)**|Para implementar os perfis de configuração em dispositivos iOS que criou utilizando a ferramenta Configurador da Apple. Isto é útil quando a definição necessária não se encontra disponível numa política de configuração.<br /><br />Para obter detalhes, consulte [Definições de política para iOS no Microsoft Intune](ios-policy-settings-in-microsoft-intune.md)|
|**Perfil de e-mail (iOS 7.1 e posterior)**|Crie, implemente e monitorize as definições de e-mail do Exchange Active Sync em dispositivos geridos. Para permitir que os utilizadores acedam a e-mails da empresa nos seus dispositivos pessoais sem precisarem de efetuar qualquer configuração.<br /><br />Para obter detalhes, consulte [Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)|
|**Configuração geral (iOS 7.1 e posterior)**|Configurar as definições de segurança e funcionais do dispositivo móvel.<br />-   Especificar aplicações que estão ou não em conformidade e comunicar quando estão a ser utilizadas.<br />Configurar o modo de local público que bloqueia dispositivos para permitir que apenas determinadas funcionalidades funcionem, como, por exemplo, permitir que o dispositivo execute apenas uma aplicação ou desativar os botões de volume.<br /><br />Para obter detalhes, consulte [Definições de política para iOS no Microsoft Intune](ios-policy-settings-in-microsoft-intune.md)|
|**Perfil de Certificado de SCEP (iOS 7.1 e posterior)**|Para configurar um certificado de protocolo SCEP (Simple Certificate Enrollment Protocol) que pode ser utilizado com um certificado fidedigno do dispositivo móvel para autenticar dispositivos móveis para lhes permitir aceder a recursos de rede, como os que são configurados pelos perfis de Wi-Fi e da VPN.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil de Certificado Fidedigno (iOS 7.1 e posterior)**|Para configurar um certificado fidedigno do dispositivo móvel que pode ser utilizado para autenticar dispositivos móveis para lhes permitir aceder a recursos de rede, como os que são configurados pelos perfis de Wi-Fi e da VPN.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil da VPN (iOS 7.1 e posterior)**|Para configurar e implementar definições que permitem que os utilizadores acedam de forma segura à rede da empresa a partir dos seus dispositivos móveis. Ao implementar estas definições, minimiza o esforço que o utilizador final necessita para se ligar ao seu trabalho.<br /><br />Para obter detalhes, consulte [Ligações VPN no Microsoft Intune.md](vpn-connections-in-microsoft-intune.md)|
|**Perfil de Wi-Fi (iOS 7.1 e posterior)**|Para configurar e implementar definições de rede sem fios aos utilizadores na sua organização. Ao implementar estas definições, minimiza o esforço que o utilizador final necessita para se ligar à rede sem fios.<br /><br />Para obter detalhes, consulte [Ligações Wi-Fi no Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)|
|**Política de Configuração de Aplicações Móveis (iOS 7.1 e posterior)**|Utilize políticas de configuração de aplicações móveis para fornecer automaticamente definições que poderão ser necessárias quando o utilizador executar uma aplicação do iOS.<br /><br />Para obter detalhes, consulte [Configurar aplicações iOS com políticas de configuração de aplicações móveis no Microsoft Intune](configure-ios-apps-with-mobile-app-configuration-policies-in-microsoft-intune.md)|

## Políticas de configuração para Mac OS X

|Nome da política|Utilize-a quando pretende|
|---------------|------------------------|
|**Configuração Personalizada (Mac OS X 10.9 e posterior)**|Implementar perfis de configuração em computadores Mac que criou com a ferramenta Apple Configurator. Isto é útil quando a definição necessária não se encontra disponível numa política de configuração.<br /><br />Para obter detalhes, consulte [Definições de política para Mac OS X no Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md)|
|**Configuração Geral (Mac OS X 10.9 e posterior)**|Configurar as definições de segurança e funcionais do dispositivo móvel.<br />Especificar aplicações que são compatíveis ou não compatíveis e comunicar quando estão a ser utilizadas.<br /><br />Para obter detalhes, consulte [Definições de política para Mac OS X no Microsoft Intune](mac-os-x-policy-settings-in-microsoft-intune.md)|
|**Perfil de Certificado de SCEP (Mac OS X 10.9 e posterior)**|Para configurar um certificado de protocolo SCEP (Simple Certificate Enrollment Protocol) que pode ser utilizado com um certificado fidedigno do dispositivo móvel para autenticar dispositivos móveis para lhes permitir aceder a recursos de rede, como os que são configurados pelos perfis de Wi-Fi e da VPN.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil de Certificado Fidedigno (Mac OS X 10.9 e posterior)**|Para configurar um certificado fidedigno do dispositivo móvel que pode ser utilizado para autenticar dispositivos móveis para lhes permitir aceder a recursos de rede, como os que são configurados pelos perfis de Wi-Fi e da VPN.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil da VPN (Mac OS X 10.9 e posterior)**|Para configurar e implementar definições que permitem que os utilizadores acedam de forma segura à rede da empresa a partir dos seus dispositivos móveis. Ao implementar estas definições, minimiza o esforço que o utilizador final necessita para se ligar ao seu trabalho.<br /><br />Para obter detalhes, consulte [Ligações VPN no Microsoft Intune.md](vpn-connections-in-microsoft-intune.md)|
|**Perfil de Wi-Fi (Mac OS X 10.9 e posterior)**|Para configurar e implementar definições de rede sem fios aos utilizadores na sua organização. Ao implementar estas definições, minimiza o esforço que o utilizador final necessita para se ligar à rede sem fios.<br /><br />Para obter detalhes, consulte [Ligações Wi-Fi no Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)|

## Políticas de configuração para Windows
Aplica-se apenas ao Windows Phone e aos dispositivos Windows inscritos.

|Nome da política|Utilize-a quando pretende|
|---------------|------------------------|
|**Configuração Personalizada (Windows 10 Desktop e Mobile 10 e posterior).**|Implemente definições OMA-URI que podem ser utilizadas para controlar funcionalidades do dispositivo. Isto é útil quando a definição necessária não se encontra disponível numa política de configuração.<br />    Para obter detalhes, consulte [Definições de política para Windows 10 no Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md)|
|**Configuração personalizada (Windows Phone 8.1 e posterior)**|Implemente definições OMA-URI que podem ser utilizadas para controlar funcionalidades do dispositivo. Isto é útil quando a definição necessária não se encontra disponível numa política de configuração.<br /><br />Para obter detalhes, consulte [Definições de política para Windows 8.1 no Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md)|
|**Política de Atualização de Edição (Windows 10 Desktop e posterior)**<br><br>**Política de Atualização de Edição (Windows 10 Holographic e posterior)**|Configurar e implementar políticas que contenham informações de chave de licenciamento ou de produto que são utilizadas para atualizar os dispositivos Windows 10 para uma versão mais recente<br><br>Para obter detalhes, consulte [Definições de política de atualização de edição no Microsoft Intune](edition-upgrade-policy-settings-in-microsoft-intune.md)|  
|**Perfil de E-mail (Windows Phone 8 e posterior)**<br /><br />**Perfil de E-mail (Windows 10 Desktop e Mobile e posterior)**|Crie, implemente e monitorize as definições de e-mail do Exchange Active Sync em dispositivos geridos. Para permitir que os utilizadores acedam a e-mails da empresa nos seus dispositivos pessoais sem precisarem de efetuar qualquer configuração.<br /><br />Para obter detalhes, consulte [Configurar o acesso a e-mail empresarial através de perfis de e-mail com o Microsoft Intune](configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune.md)|
|**Configuração Geral (Windows 10 Desktop e Mobile e posterior)**|Configure definições de segurança e funcionais do dispositivo móvel para dispositivos Windows 10 de secretária e móveis inscritos.<br /><br />Para obter detalhes, consulte [Definições de política para Windows 10 no Microsoft Intune](windows-10-policy-settings-in-microsoft-intune.md)|
|**Configuração Geral (Windows 10 Team e posterior)**|Configure as definições funcionais e de segurança dos dispositivos Windows 10 Team inscritos (por exemplo, um dispositivo Surface Hub).<br /><br />Para obter detalhes, consulte [Definições de política de configuração para Windows Team no Microsoft Intune](windows-team-configuration-policy-settings-in-microsoft-intune.md)|
|**Configuração Geral (Windows 8.1 e posterior)**|Configure definições de segurança e funcionais do dispositivo móvel para dispositivos Windows inscritos.<br /><br />Para obter detalhes, consulte [Definições de política para Windows no Microsoft Intune](windows-configuration-policy-settings-in-microsoft-intune.md)|
|**Configuração Geral (Windows Phone 8.1 e posterior)**|Configurar as definições de segurança e funcionais do dispositivo móvel.<br />Para especificar as aplicações que os utilizadores podem ou não utilizar e bloquear a instalação e utilização de aplicações não compatíveis.<br /><br />Para obter detalhes, consulte [Definições de política para Windows 8.1 no Microsoft Intune](windows-phone-8-1-policy-settings-in-microsoft-intune.md)|
|**Perfil de Certificado PKCS #12 (PFX) (Windows 10 Desktop e Mobile e posterior)**|Utilize este perfil para criar e implementar definições PFX para pedidos de certificação de dispositivos.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil de Certificado de SCEP (Windows 8.1 e posterior)**<br /><br />**Perfil de Certificado de SCEP (Windows Phone 8.1 e posterior)**|Para configurar um certificado de protocolo SCEP (Simple Certificate Enrollment Protocol) que pode ser utilizado com um certificado fidedigno do dispositivo móvel para autenticar dispositivos móveis para lhes permitir aceder a recursos de rede, como os que são configurados pelos perfis de Wi-Fi e da VPN.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil de Certificado Fidedigno (Windows 8.1 e posterior)**<br /><br />**Perfil de Certificado Fidedigno (Windows Phone 8.1 e posterior)**|Para configurar um certificado fidedigno do dispositivo móvel que pode ser utilizado para autenticar dispositivos móveis para lhes permitir aceder a recursos de rede, como os que são configurados pelos perfis de Wi-Fi e da VPN.<br /><br />Para obter detalhes, consulte [Proteger o acesso a recursos com perfis de certificado no Microsoft Intune](secure-resource-access-with-certificate-profiles.md)|
|**Perfil da VPN (Windows 10 Desktop e Mobile e posterior)**<br /><br />**Perfil da VPN (Windows 8.1 e posterior)**<br /><br />**Perfil da VPN (Windows Phone 8.1 e posterior)**|Para configurar e implementar definições que permitem que os utilizadores acedam de forma segura à rede da empresa a partir dos seus dispositivos móveis. Ao implementar estas definições, minimiza o esforço que o utilizador final necessita para se ligar ao seu trabalho.<br /><br />Para obter detalhes, consulte [Ligações VPN no Microsoft Intune.md](vpn-connections-in-microsoft-intune.md)|
|**Importação de Wi-Fi**|Para importar e implementar as configurações de Wi-Fi do Windows que exportou anteriormente para um ficheiro.<br /><br />Para obter detalhes, consulte [Ligações Wi-Fi no Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)|

## Políticas de software

|Nome da política|Utilize-a quando pretende|
|---------------|------------------------|
|**Política de Browser Gerido (Android 4 e posterior)**<br /><br />**Política de Browser Gerido (iOS 7.1 e posterior)**|Para especificar os sites que os utilizadores podem ou não aceder quando estão a utilizar a aplicação de browsers geridos.<br /><br />Para obter detalhes, consulte [Gerir o acesso à Internet através de políticas de browser gerido com o Microsoft Intune](manage-internet-access-using-managed-browser-policies.md)|
|**Política de Gestão de Aplicações Móveis (Android 4 e posterior)**<br /><br />**Política de Gestão de Aplicações Móveis (iOS 7.1 e posterior)**|Para modificar a funcionalidade das aplicações que implementa para ajudar a torná-las compatíveis com as políticas de conformidade e de segurança da sua empresa. Por exemplo, pode limitar operações de corte, cópia e colagem numa aplicação restrita ou configurar uma aplicação para abrir todas as ligações Web no browser gerido.<br /><br />Para obter detalhes, consulte [Configurar e implementar políticas de gestão de aplicações móveis na consola do Microsoft Intune](configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console.md)|

## Definições Comuns de Dispositivos Móveis

|Nome da política|Utilize-a quando pretende|
|---------------|------------------------|
|**Política do Exchange ActiveSync**|Configure definições de segurança e funcionais do dispositivo móvel em dispositivos geridos pelo Exchange ActiveSync.<br /><br />Para obter detalhes, consulte [Definições de política para Exchange ActiveSync no Microsoft Intune](exchange-activesync-policy-settings-in-microsoft-intune.md)|
|**Política de Segurança de Dispositivos Móveis**|<ul><li>Configura as definições dos dispositivos móveis (todas as plataformas), incluindo:<br /><br /><ul><li>Segurança</li><li>Encriptação</li><li>Sistema</li><li>E-mail</li><li>Aplicações</li></ul></li></ul> **Importante:** agora, o Microsoft Intune inclui **políticas de configuração** separadas para cada plataforma de dispositivo, sendo que estas políticas contêm as definições mais atualizadas à sua disposição. Pode continuar a utilizar a política de segurança do dispositivo móvel e todas as implementações existentes continuarão a funcionar, mas deve planear a migração para as novas políticas de configuração logo que possível.<br />Para obter detalhes, consulte [Definições de política de segurança de dispositivos móveis no Microsoft Intune](mobile-device-security-policy-settings-in-microsoft-intune.md)|

## Políticas de acesso condicional e de conformidade

### Acesso Condicional

|Nome da política|Utilize-a quando pretende|
|---------------|------------------------|
|**Política do Exchange Online**<br /><br />**Política do Exchange No Local**|Gerir o acesso ao e-mail do Microsoft Exchange a partir de dispositivos que não são geridos pelo Intune ou que não estão em conformidade com a política de conformidade que criou.<br /><br />Para obter detalhes, consulte [Restringir o acesso ao e-mail no Exchange Online e no novo ambiente Exchange Online Dedicado com o Intune](restrict-access-to-exchange-online-with-microsoft-intune.md)|
|**Política do SharePoint Online**|Gerir o acesso ao SharePoint Online a partir de dispositivos que não são geridos pelo Intune ou que não estão em conformidade com a política de conformidade que criou.<br /><br />Para obter detalhes, consulte [Restringir o acesso ao SharePoint Online com o Microsoft Intune](restrict-access-to-sharepoint-online-with-microsoft-intune.md)|
|**Skype para Empresas**|Gerir o acesso ao Skype para Empresas a partir de dispositivos que não são geridos pelo Intune ou que não estão em conformidade com a política de conformidade que criou.<br /><br />Para obter detalhes, consulte [Restringir o acesso ao Skype para Empresas com o Microsoft Intune](restrict-access-to-skype-for-business-online-with-microsoft-intune.md)|
> [!NOTE]
> O utilizador implementa políticas de acesso condicional a utilizadores e dispositivos. Em vez disso, configura a política necessária e esta aplica-se a todos os grupos abrangidos pela política.

### Políticas de Conformidade

|Nome da política|Utilize-a quando pretende|
|---------------|------------------------|
|**Políticas de conformidade**|Definir o nível de conformidade dos dispositivos e, em seguida, informar sobre a presença de dispositivos não compatíveis. Estas políticas são utilizadas com acesso condicional para ajudar a avaliar os dispositivos que devem ser bloqueados dos serviços.<br /><br />Para obter detalhes, consulte [Gerir políticas de conformidade de dispositivos para o Microsoft Intune](introduction-to-device-compliance-policies-in-microsoft-intune.md)|

## Gestão de PCs Windows

|Nome da política|Utilize-a quando pretende|
|---------------|------------------------|
|**Definições do Agente do Microsoft Intune**|Configurar o cliente PC do Intune em computadores, incluindo as definições para:<br /><br />-   Endpoint Protection<br />-   Atualizações de software<br />-   Agendamento de verificação de política<br /><br />Este tipo de política só pode ser implementado em grupos de dispositivos.<br /><br />Os clientes do Intune transferem políticas novas e atualizadas de acordo com a definição **Frequência de deteção de atualizações e aplicações**, a qual está predefinida para 8 horas. No entanto, pode forçar a atualização da política em computadores em qualquer altura.<br /><br />Para obter detalhes, consulte [Manter os PCs Windows atualizados com atualizações de software no Microsoft Intune](keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune.md)|
|**Definições do Centro do Microsoft Intune**|Configurar detalhes que são apresentados no Centro do Microsoft Intune em computadores geridos.<br /><br />Este tipo de política só pode ser implementado em grupos de dispositivos.<br /><br />Para obter detalhes, consulte [Tarefas de gestão comuns do PC Windows com o computador cliente do Microsoft Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)|
|**Definições da Firewall do Windows**|Configura as definições e exceções da Firewall do Windows para comunicações de rede comuns em computadores, incluindo:<br /><br />-   BranchCache<br />-   Assistência Remota<br />-   Partilha de Multimédia<br /><br />Este tipo de política só pode ser implementado em grupos de dispositivos.<br /><br />Para obter detalhes, consulte [Ajude a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune.md)|

### Consulte Também

[Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md)



<!--HONumber=May16_HO2-->

