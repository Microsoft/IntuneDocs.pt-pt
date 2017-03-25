---
title: Criar uma estrutura do Intune | Documentos da Microsoft
description: "Este artigo ajuda-o a criar uma estrutura para uma estruturação e implementação apenas na cloud do Microsoft Intune."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 6df87e20011f20b99b91d88e669c67bb97ad2277
ms.openlocfilehash: 1768b98cdcb18b5489d9a30b8c1f455f5de58418
ms.lasthandoff: 03/13/2017


---

# <a name="create-an-intune-design"></a>Criar uma estrutura do Intune

[!INCLUDE[note for both-portals](../includes/note-for-both-portals.md)]

A secção do guia deverá ser utilizada em paralelo com outros tópicos na Secção 2. Esta estrutura basear-se-á nas informações que está a recolher e em decisões que irá tomar ao concluir as secções anteriores deste guia. Nesta secção de estruturação, vamos concentrar-nos na versão autónoma do Intune, que é um serviço da Microsoft baseado na cloud.

Apesar de os requisitos de infraestrutura no local serem extremamente reduzidos, trabalhe num plano de estrutura para garantir que tem a solução de gestão de dispositivos móveis correta e de que cumpre os seus objetivos, requisitos e metas.

Além disso, é frequente haver mudanças de estrutura durante as fases de implementação e testes. Documente estas alterações e os motivos das mesmas à medida que ocorrem. Iremos abordar as seguintes áreas:

-   O ambiente atual

-   Opções de implementação do Intune

-   Requisitos de identidade para dependências externas

-   Considerações de plataformas de dispositivos

-   Requisitos a serem entregues  

Analisemos cada uma destas áreas mais detalhadamente. 

## <a name="record-your-environment"></a>Registar o seu ambiente

O primeiro passo antes de criar a sua estrutura é registar o seu atual ambiente. O ambiente atual pode influenciar decisões de estrutura e deve ser documentado e referenciado quando tomar outras decisões de estrutura do Intune. Seguem-se alguns exemplos de como registar o ambiente atual:

-   **Identidade na cloud**

    -   Utiliza o DirSync ou o Azure Active Directory (AAD) Connect?

    -   O seu ambiente é Federado?

    -   A autenticação Multifator está ativada?

-   **Ambiente de e-mail**

    -   O Exchange está a ser utilizado? É no local ou na cloud?

    -   Está a meio de um projeto de migração do Exchange para a cloud?

-   **Solução de MDM atual**

    -   Atualmente, está a utilizar outras soluções MDM?

    -   Que soluções MDM está a utilizar para casos de utilização empresarial e BYOD?

    -   Que capacidades está a utilizar (por exemplo, definições de dispositivos de aplicações, configurações Wi-Fi, etc.)?

    -   Que plataformas de dispositivos são suportadas?

    -   Que grupos e quantos utilizadores estão a utilizar a solução MDM?

-   **Solução de Certificado**

    -   Implementou uma solução de Certificado?

    -   Que tipos de certificado utiliza?

-   **Gestão de Sistemas**

    -   Como está a gerir o seu ambiente de PC e servidor?

    -   O System Center Configuration Manager está a ser utilizado? Está a utilizar uma plataforma de gestão de sistema de terceiros?

-   **Solução VPN**

    -   Qual é a sua solução VPN?

    -   É utilizado em cenários de casos de utilização empresarial e BYOD?

Ao registar o atual ambiente MDM, tome nota de todos os projetos ou outros planos em curso que possam fazer alterações ao seu ambiente. Segue-se um exemplo de uma forma de registar o ambiente atual para auxiliar a criação da sua estrutura do Intune:

| **Área de solução** | **Ambiente atual** | **Comentários** |
|:---:|:---:|:---:|
| **Identidade** | Azure AD, Azure AD Connect, não federado, sem MFA | Projeto implementado para ativar o MFA até ao final do ano |                 
| **Ambiente de e-mail** | Exchange no local, Exchange Online | Atualmente a migrar do Exchange no local para o Exchange Online. 75% das caixas de correio migradas. Os restantes 25% serão migrados antes de o Teste do Intune ser iniciado. |                
| **SharePoint** | SharePoint no local | Não existem planos para migrar para o SharePoint Online |  
| **MDM atual** | Exchange ActiveSync |  |
| **Solução de certificado** | Serviços de Certificado do Microsoft Server 2012 R2, AD | Utilizar apenas PKI para Servidores de Sites |
| **Gestão de Sistema** | System Center Configuration Manager CB 1606 | Quer investigar uma solução híbrida do Intune |
| **Solução VPN** | Cisco AnyConnect |  |

## <a name="choose-an-intune-deployment-option"></a>Selecionar uma opção de implementação do Intune

O Intune oferece duas opções de implementação: autónoma e híbrida. Terá de decidir qual se adequa melhor aos seus requisitos empresariais. Autónoma refere-se ao serviço do Intune executado na cloud, ao passo que híbrida se refere à integração do Intune com o System Center Configuration Manager.

- Saiba mais sobre [escolher entre a gestão de dispositivos móveis do Microsoft Intune autónoma e híbrida com o System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management)

## <a name="intune-tenant-location"></a>Localização de inquilinos do Intune

Se a sua organização tiver uma presença global, planeie onde o seu inquilino irá residir ao subscrever o serviço. O país é definido quando se inscreve numa subscrição do Intune pela primeira vez, e mapeado para as regiões do mundo a seguir indicadas:

-   América do Norte

-   Europa, Médio Oriente e África

-   Ásia e Pacífico

>[!IMPORTANT]
> Não é possível mudar a localização do inquilino/país posteriormente.

## <a name="external-dependencies"></a>Dependências externas

As dependências externas são produtos e serviços que estão separados do Intune, mas são um requisito do Intune ou podem integrar-se com o Intune. É importante identificar os requisitos de dependências externas e como serão configuradas. Seguem-se alguns exemplos de dependências externas comuns.

-   Identidade

-   Grupos de utilizadores e de dispositivos

-   PKI

Vamos explorar mais detalhadamente as seguintes dependências externas comuns

### <a name="identity"></a>Identidade

A identidade é a forma como identificamos os utilizadores que pertencem à sua organização e estão a inscrever um dispositivo. O Intune necessita do Azure Active Directory (Azure AD) como fornecedor de identidade do utilizador. Se já utiliza este serviço, pode tirar partido da sua identidade já existente na cloud. Além disso, o Azure AD Connect é a ferramenta recomendada para sincronizar as suas identidades de utilizador no local com os serviços da Microsoft na cloud. Se a sua organização já utiliza o Office 365, é importante que o Intune utilize o mesmo ambiente do Azure Active Directory.

Pode encontrar mais informações sobre os requisitos de identidade do Intune abaixo.

-   Saiba mais sobre os [requisitos de identidade](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-overview#design-considerations-overview).

-   Saiba mais sobre os [requisitos da sincronização de diretórios](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-directory-sync-requirements).

-   Saiba mais sobre os [requisitos de autenticação multifator](https://docs.microsoft.com/active-directory/active-directory-hybrid-identity-design-considerations-multifactor-auth-requirements).

### <a name="user-and-device-groups"></a>Grupos de utilizadores e de dispositivos

Os grupos de utilizadores e dispositivos determinam o destino de uma implementação. Tal pode incluir filtragem de implementação para políticas, aplicações e perfis. O Intune na cloud suporta apenas os grupos de utilizadores e dispositivos. Tem de determinar quais os grupos de utilizadores e dispositivos necessários. Recomenda-se que todos os grupos sejam criados no Active Directory no local e depois sincronizados com o Azure Active Directory. Encontrará mais informações sobre o planeamento e criação de grupos de utilizadores e dispositivos abaixo.

-   Saiba mais sobre como [planear os seus grupos de utilizadores e de dispositivos](https://docs.microsoft.com/intune/deploy-use/plan-your-user-and-device-groups).

-   Saiba [como criar grupos de utilizadores e dispositivos](https://docs.microsoft.com/en-us/intune/deploy-use/use-groups-to-manage-users-and-devices-with-microsoft-intune).

### <a name="public-key-infrastructure-pki"></a>Infraestrutura de Chaves Públicas (PKI)

A Infraestrutura de Chaves Públicas fornece certificados para dispositivos ou utilizadores de forma a autenticar a um serviço com segurança. O Intune suporta uma infraestrutura PKI do Microsoft. Os certificados de dispositivos e utilizadores podem ser emitidos para um dispositivo móvel para cumprir requisitos de autenticação baseados em certificados. Antes de implementar certificados, tem de determinar se os certificados são necessários, se a infraestrutura de rede consegue suportar a autenticação baseada em certificados e se são atualmente utilizados certificados no ambiente existente.

Se estiver a planear utilizar certificados com a VPN, Wi-Fi ou perfis de e-mail com o Intune, tem de certificar-se de que tem uma [infraestrutura PKI suportada](https://docs.microsoft.com/intune/deploy-use/secure-resource-access-with-certificate-profiles), pronta para criar e implementar perfis de certificados.

Além disso, se vão ser emitidos certificados SCEP, tem de determinar que servidor irá alojar a funcionalidade Serviço de Inscrição de Dispositivos de Rede (NDES) e como a comunicação irá ocorrer.

Mais informações sobre a configuração de certificados no Intune:

-   [Como configurar a infraestrutura de certificados para o SCEP](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-scep).

-   [Como configurar a infraestrutura de certificados para o PFX](https://docs.microsoft.com/intune/deploy-use/configure-certificate-infrastructure-for-pfx).

-   [Como configurar perfis de certificado do Intune](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles).

-   [Como configurar políticas de acesso de recursos](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune).

## <a name="device-platform-considerations"></a>Considerações de Plataformas de Dispositivos

Tem de analisar os seus dispositivos mais atentamente para compreender como os configurar corretamente.

-   Determinar plataformas de dispositivos suportados

-   Dispositivos

-   Propriedade dos dispositivos

-   Inscrição em massa

Analisemos estas áreas mais detalhadamente.

### <a name="determine-supported-device-platforms"></a>Determinar plataformas de dispositivos suportados

É necessário saber que dispositivos estarão no ambiente e confirmar se são ou não suportados pelo Intune durante a criação da sua estrutura. O Intune suporta plataformas iOS, Android e Windows.

-   Saiba mais sobre os [Dispositivos Suportados pelo Intune](https://docs.microsoft.com/intune/get-started/supported-mobile-devices-and-computers).

### <a name="devices"></a>Dispositivos

O Intune gere dispositivos móveis para proteger dados empresariais e permite que os utilizadores finais trabalhem em mais locais. O Intune suporta múltiplas plataformas de dispositivos, pelo que recomendamos que tome nota dos dispositivos e plataformas de SO que serão suportados na estrutura da sua organização. Isto irá expandir os dispositivos e plataformas criados na secção (requisitos de casos de utilização).

Também recomendamos conhecer as versões para referenciar a lista ao procurar capacidades de dispositivos por versão e plataforma de SO. Eis um exemplo:

| **Plataforma de dispositivo** | **Versões do SO** |
|:---:|:---:|
| iOS – iPhone | 9.0+ |                
| iOS – iPad | 8.0+ |               
| Android – Samsung Knox Standard | 4.0+ |
| Tablet Windows 10 | 10+ |

### <a name="device-ownership"></a>Propriedade dos dispositivos

O Intune suporta a propriedade da empresa e BYOD. Um Dispositivo é considerado propriedade da empresa se for inscrito por um gestor de inscrição de dispositivos ou programa de inscrição de dispositivos. Como exemplo, um dispositivo pode ser inscrito através do Apple DEP, marcado como empresarial e colocado num grupo de dispositivos que recebe políticas e aplicações filtradas empresariais.

Consulte a [Secção 3: determinar requisitos de cenários de casos de utilização](section-3-determine-use-case-requirements.md) para obter mais informações sobre os casos de utilização Empresarial e BYOD.

### <a name="bulk-enrollment"></a>Inscrição em massa

Existem múltiplas opções de inscrição disponíveis para inscrever um dispositivo no Intune que complementam a inscrição self-service através do portal da empresa. A inscrição em massa pode ser levada a cabo de formas diferentes, consoante a plataforma. Se a inscrição em massa for necessária, determine primeiro o método de inscrição em massa e incorpore-o na sua estrutura. Encontrará mais informações sobre os diferentes métodos de inscrição em massa abaixo.

-   Saiba mais sobre a [inscrição em massa](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune).

## <a name="feature-requirements"></a>Requisitos de funcionalidades

Nestas secções, iremos analisar as seguintes funcionalidades e capacidades que estão alinhadas com os seus requisitos de cenários de casos de utilização:

-   Políticas de Termos e Condições

-   Políticas de Configuração

-   Perfis de Recursos

-   Aplicações

-   Política de Conformidade

-   Acesso Condicional

Analisemos cada uma destas áreas mais detalhadamente.

### <a name="terms-and-conditions-policies"></a>Políticas de Termos e Condições

Os Termos e Condições podem ser utilizados para explicar políticas ou condições que têm de ser aceites por um utilizador final antes da inscrição. O Intune suporta a capacidade de adicionar e implementar múltiplas políticas de termos e condições a grupos de utilizadores. Tem de determinar se as políticas de termos e condições são necessárias. Se for o caso, quem será responsável por fornecer essas informações na organização.

-   Saiba [como criar políticas de termos e condições](https://docs.microsoft.com/intune/deploy-use/terms-and-condition-policy-settings-in-microsoft-intune) no Intune. Segue-se um exemplo de como documentar a política de termos e condições.

| **Nome de Termos e Condições** | **Caso de utilização** | **Grupo de destino** |
|:---:|:---:|:---:|
| T&C Empresarial | Empresarial | Utilizadores empresariais |                 
| T&C BYOD | BYOD | Utilizadores de BYOD |                

### <a name="configuration-policies"></a>Políticas de configuração

As políticas de configuração são utilizadas para gerir as funcionalidades e as definições de segurança num dispositivo. Ao estruturar as suas políticas de configuração, consulte a secção dos requisitos de casos de utilização para determinar as configurações necessárias para dispositivos do Intune. Documente quais as definições e como devem ser configuradas, bem como a que grupos de dispositivos ou utilizadores serão filtrados.

Deve criar pelo menos uma Política de Configuração por plataforma. Pode criar múltiplas Políticas de Configuração por plataforma, se for necessário. Segue-se um exemplo da estruturação de quatro políticas de configuração diferentes para diversas plataformas e cenários de casos de utilização.

| **Nome da política** | **Plataforma de dispositivo** | **Definições** | **Grupo de destino** |   
|:---:|:---:|:---:|:---:|
| Empresarial – iOS | iOS | O PIN é obrigatório, Comprimento: 6, Cópia de Segurança na Cloud Restrita | Dispositivos Empresariais |                                                           
| Empresarial – Android | Android | O PIN é obrigatório, Comprimento: 6, Cópia de Segurança na Cloud Restrita | Dispositivos Empresariais |                                                           
| BYOD – iOS  | iOS | O PIN é obrigatório, Comprimento: 4 | Dispositivos BYOD |
| BYOD – Android  | Android | O PIN é obrigatório, Comprimento: 4 | Dispositivos BYOD |

### <a name="profiles"></a>Perfis

Os perfis são utilizados para ajudar o utilizador final a ligar a dados da empresa. O Intune suporta muitos tipos de perfis. Consulte os requisitos e casos de utilização para determinar quando os [perfis](https://docs.microsoft.com/intune/deploy-use/enable-access-to-company-resources-with-microsoft-intune) serão configurados. Todos os perfis de dispositivos são categorizados por tipo de plataforma e devem ser incluídos na documentação da estrutura.

-   Perfis de certificados

-   Perfil Wi-Fi

-   Perfil VPN

-   Perfil de e-mail

Analisemos cada tipo de perfil mais detalhadamente.

##### <a name="certificate-profiles"></a>Perfis de certificados

Os perfis de certificados permitem ao Intune emitir um certificado para um utilizador ou dispositivo. O Intune suporta o seguinte:

-   Protocolo SCEP (Simple Certificate Enrollment Protocol)

-   Certificado de Raiz Fidedigna

-   Certificado PFX.

Recomenda-se documentar que grupos de utilizadores precisam de um certificado, quantos perfis de certificados serão necessários e para que grupos de utilizadores devem ser implementados.

>[!NOTE]
> Lembre-se de que o certificado de raiz fidedigna é necessário para o certificado SCEP, pelo que deve garantir que todos os utilizadores filtrados para o certificado SCEP também recebem um certificado de raiz fidedigna. Se forem necessários certificados SCEP, estruture e documente que modelos de certificados SCEP serão necessários.

Eis um exemplo de como pode documentar os certificados durante a estruturação:

| **Tipo** | **Nome do perfil** | **Plataforma de dispositivo** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| AC de Raiz | AC de Raiz Empresarial | Android, iOS, Windows Mobile | Empresarial, BYOD  |                                                           
| SCEP | Certificado de Utilizadores | Android, iOS, Windows Mobile | Empresarial, BYOD |                                                           

##### <a name="wi-fi-profile"></a>Perfil Wi-Fi

Os Perfis de Wi-Fi são utilizados para ligar automaticamente um dispositivo móvel a uma rede sem fios. O Intune suporta a implementação de perfis de Wi-Fi em todas as plataformas suportadas.

-   Saiba mais sobre [como o Intune suporta perfis de Wi-Fi.](https://docs.microsoft.com/intune/deploy-use/wi-fi-connections-in-microsoft-intune)

Segue-se um exemplo de uma estrutura de um perfil de Wi-Fi:

| **Tipo** | **Nome do perfil** | **Plataforma de dispositivo** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | Perfil de Wi-Fi na Ásia | Android | Empresarial, BYOD na região da Ásia|                                                           
| Wi-Fi | Perfil de Wi-Fi da América do Norte | Android, iOS, Windows 10 Mobile | Empresarial, BYOD na região da América do Norte |                                                           

##### <a name="vpn-profile"></a>Perfil VPN

Os perfis VPN permitem aos utilizadores aceder seguramente à sua rede a partir de localizações remotas. O Intune suporta perfis VPN de ligações VPN móveis nativas e fornecedores terceiros.

-   Saiba mais sobre os [fornecedores e perfis VPN suportados pelo Intune](https://docs.microsoft.com/intune/deploy-use/vpn-connections-in-microsoft-intune).

Segue-se um exemplo de como documentar a estrutura de um perfil VPN.

| **Tipo** | **Nome do perfil** | **Plataforma de dispositivo** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| VPN | Perfil VPN Cisco qualquer ligação | Android, iOS, Windows 10 Mobile | Empresarial, BYOD na América do Norte e Alemanha|                                                           
| VPN | Pulse Secure | Android | Empresarial, BYOD na região da Ásia |                                                           

##### <a name="email-profile"></a>Perfil de e-mail

Os perfis de e-mail permitem a um cliente de e-mail ser automaticamente configurado com informações de ligação e configurar o e-mail. O Intune suporta perfis de e-mail em determinados países.

-   Saiba mais sobre os [perfis de e-mail](https://docs.microsoft.com/en-us/intune/deploy-use/configure-access-to-corporate-email-using-email-profiles-with-microsoft-intune) e que plataformas são suportadas.

Segue-se um exemplo de como documentar a estrutura de perfis de e-mail:

| **Tipo** | **Nome do perfil** | **Plataforma de dispositivo** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| Perfil de e-mail | Perfil de e-mail iOS | iOS | Empresarial – Técnico de informação BYOD |                                                           
| Perfil de e-mail | Perfil de e-mail Android Knox | Android Knox | BYOD |

### <a name="apps"></a>Aplicações

O Intune suporta a entrega de aplicações ou dispositivos de diversas formas. O tipo de aplicação entregue pode ser uma aplicação de instalador de software, aplicação de uma loja de aplicações pública, ligações externas ou aplicações iOS geridas. Além de implementações de aplicações individuais, as aplicações adquiridas em volume podem ser geridas e implementadas através de programas de aquisição em volume para iOS e Windows. Seguem-se mais informações sobre como o Intune suporta aplicações e programas de aquisição em volume.

-   Saiba mais sobre os [tipos de aplicações](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)

-   Saiba mais sobre o [iOS Volume Purchase Program for Business (VPP](https://docs.microsoft.com/intune/deploy-use/manage-ios-apps-you-purchased-through-a-volume-purchase-program-with-microsoft-intune)).

-   Saiba mais sobre a [Loja Windows para Empresas](https://docs.microsoft.com/intune/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune).

#### <a name="app-type-requirements"></a>Requisitos de tipos de aplicações

Uma vez que as aplicações podem ser implementadas para utilizadores e dispositivos, recomenda-se que decida que aplicações serão geridas pelo Intune. Ao compilar a lista, tente responder às seguintes questões:

-   As aplicações requerem integração com os serviços da cloud?

-   Todas as aplicações estarão disponíveis para utilizadores BYOD?

-   Quais são as opções de implementação disponíveis para estas aplicações?

-   A sua empresa necessita de fornecer acesso a dados de aplicações Software como um serviço (SaaS) aos seus parceiros?

-   As aplicações necessitam de acesso à Internet a partir dos dispositivos dos utilizadores?

-   As aplicações estão publicamente disponíveis numa loja de aplicações ou são Aplicações de Linha de Negócio personalizadas?


>[!TIP]
> Consulte os [diferentes tipos de aplicações que o Intune suporta](https://docs.microsoft.com/intune/deploy-use/add-apps).

#### <a name="app-protection-policies"></a>Políticas de proteção de aplicações

As políticas de proteção de aplicações minimizam a perda de dados ao definir como a aplicação gere os dados empresariais. O Intune suporta políticas de proteção de aplicações para qualquer aplicação criada para funcionar com a gestão de aplicações móveis. Ao criar a política de proteção de aplicações, tem de determinar que restrições irá atribuir aos dados empresariais numa determinada aplicação. Recomenda-se que reveja como funcionam as [políticas de proteção de aplicações](https://docs.microsoft.com/intune/deploy-use/protect-app-data-using-mobile-app-management-policies-with-microsoft-intune). Segue-se um exemplo de como documentar as aplicações existentes e que proteção é necessária.

| **Aplicação** | **Objetivo** | **Plataformas** | **Caso de utilização** | **Política de proteção de aplicações** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Disponível | iOS | Empresarial – Executivos | Não pode ser desbloqueado por jailbreak, encriptar ficheiros |                                                         
| Word | Disponível | iOS, Android – Samsung Knox, não Knox, Windows 10 Mobile | Empresarial, BYOD | Não pode ser desbloqueado por jailbreak, encriptar ficheiros |                                                         

#### <a name="compliance-policies"></a>Políticas de conformidade

As políticas de conformidade determinam se um dispositivo cumpre determinados requisitos. O Intune utiliza políticas de conformidade para determinar se um dispositivo é considerado como estando ou não em conformidade. O estado de conformidade pode depois ser utilizado para restringir o acesso a recursos da empresa. Se for necessário acesso condicional, recomenda-se a criação de uma [política de conformidade de dispositivo](https://docs.microsoft.com/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune). Consulte os requisitos e casos de utilização para determinar quantas políticas de conformidade de dispositivo são necessárias e quais são os grupos de utilizadores de destino. Além disso, terá de determinar durante quanto tempo um dispositivo pode estar offline sem dar entrada, antes de ser considerado como não estando em conformidade.

Segue-se um exemplo de como estruturar uma política de conformidade:

| **Nome da política** | **Plataforma de dispositivo** | **Definições** | **Grupo de destino** |   
|:---:|:---:|:---:|:---:|
| Política de conformidade | iOS, Android – Samsung Knox, não Knox, Windows 10 Mobile | PIN – obrigatório, não pode ser desbloqueado por jailbreak | Empresarial, BYOD |

#### <a name="conditional-access-policies"></a>Políticas de acesso condicional

O Acesso Condicional é utilizado para permitir que apenas os dispositivos em conformidade acedam aos recursos da empresa. O Intune funciona com todo o Enterprise Mobility + Security (EMS) para controlar o acesso aos recursos da empresa. Terá de determinar se o acesso condicional é necessário e o que tem de ser protegido.

-   Saiba mais sobre o [Acesso Condicional](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

Para acesso online, determine que plataformas e grupos de utilizadores serão filtrados por políticas de acesso condicional.

Além disso, precisa de determinar se é necessário instalar/configurar o conector de serviços do Intune para o Exchange Online ou Exchange no local.

Saiba como instalar e configurar os conectores de serviços do Intune:

-   [Exchange Online](https://docs.microsoft.com/intune/deploy-use/intune-service-to-service-exchange-connector)

-   [Exchange no local](https://docs.microsoft.com/intune/deploy-use/intune-on-premises-exchange-connector)

Eis um exemplo de como documentar políticas de acesso condicional:

| **Serviço** | **Plataformas de Autenticação Moderna** | **Autenticação Básica** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| Exchange online | iOS, Android | Bloquear dispositivos não conformes em plataformas suportadas pelo Intune | Empresarial, BYOD |
| SharePoint Online | iOS, Android |  | Empresarial, BYOD |

## <a name="next-section"></a>Secção Seguinte

A próxima secção fornece orientações sobre o [processo de implementação do Intune](section-8-onboarding-process.md).

