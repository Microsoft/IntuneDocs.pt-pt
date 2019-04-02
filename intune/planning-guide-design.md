---
title: Criar a sua estrutura do Microsoft Intune
titleSuffix: Microsoft Intune
description: Este artigo ajuda-o a criar uma estrutura para uma estruturação e implementação apenas na cloud do Microsoft Intune.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 3/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a8e38e29-f5e3-4a71-a170-d3b1a06e37c6
ms.reviewer: jeffbu, cgerth
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 307895935e1cd6fe2489a4ee8ae03333ce97d55b
ms.sourcegitcommit: 484a898d54f5386fdbce300225aaa3495cecd6b0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58799053"
---
# <a name="create-a-design"></a>Criar uma estrutura

A sua estrutura do Intune baseia-se nas informações que recolhe e em decisões que toma quando conclui as [outras secções deste guia](planning-guide.md). Ajuda-o a reunir:

-   O ambiente atual

-   Opções de implementação do Intune

-   Requisitos de identidade para dependências externas

-   Considerações de plataformas de dispositivos

-   Requisitos a serem entregues  

Apesar de os requisitos de infraestrutura no local serem extremamente reduzidos, um plano de estrutura é útil para garantir que tem a solução de gestão de dispositivos móveis correta e que cumpre os seus objetivos, requisitos e metas.

Analisemos cada uma destas áreas mais detalhadamente. 

## <a name="record-your-current-environment"></a>Registar o seu ambiente atual
Além disso, é comum haver mudanças de estrutura durante a fase de teste e implementação. Utilize o seu plano de estrutura para documentar estas alterações e os motivos das mesmas à medida que ocorrem.

O seu ambiente atual pode influenciar decisões de estrutura e deve ser documentado e referenciado quando tomar outras decisões de estrutura do Intune. Seguem-se alguns exemplos de como registar o ambiente atual:

-   **Identidade na cloud**

    -   Utiliza o DirSync ou o Azure Active Directory (Azure AD) Connect?

    -   O seu ambiente é federado?

    -   A autenticação multifator (MFA) está ativada?

-   **Ambiente de e-mail**

    -   Utiliza o Exchange? No local ou na cloud?

    -   Está a meio de um projeto de migração do Exchange para a cloud?

-   **Solução de gestão de dispositivos móveis (MDM) atual**

    -   Atualmente, está a utilizar outras soluções MDM?

    -   Que soluções MDM está a utilizar para cenários de casos de utilização empresarial e BYOD?

    -   Que capacidades está a utilizar (por exemplo, definições de dispositivos de aplicações, configurações Wi-Fi)?

    -   Que plataformas de dispositivos são suportadas?

    -   Que grupos e quantos utilizadores estão a utilizar a solução MDM?

-   **Solução de certificado**

    -   Implementou uma solução de certificado?

    -   Que tipos de certificado utiliza?

-   **Gestão de sistemas**

    -   Como está a gerir o seu ambiente de PC e servidor?

    -   Está a utilizar o System Center Configuration Manager? Está a utilizar uma plataforma de gestão de sistema de terceiros?

-   **Solução VPN**

    -   Qual é a sua solução VPN?

    -   Utiliza-a para cenários de casos de utilização empresarial e BYOD?

Ao registar o atual ambiente MDM, certifique-se de que toma nota de todos os projetos ou outros planos em curso que possam afetar o seu ambiente. Segue-se um exemplo de uma forma de registar o ambiente atual na criação da sua estrutura do Intune:

| **Área de solução** | **Ambiente atual** | **Comentários** |
|---|---|---|
| **Identidade** | Azure AD, Azure AD Connect, não federado, sem MFA | Projeto implementado para ativar o MFA até ao final do ano |                 
| **Ambiente de e-mail** | Exchange no local, Exchange Online | Atualmente a migrar do Exchange no local para o Exchange Online. 75% das caixas de correio migradas. Os restantes 25% serão migrados antes de o Teste do Intune ser iniciado. |                
| **SharePoint** | SharePoint no local | Não existem planos para migrar para o SharePoint Online |  
| **MDM atual** | Exchange ActiveSync |  |
| **Solução de certificado** | Serviços de Certificado do Microsoft Server 2012 R2, AD | Utilizar apenas PKI para Servidores de Sites |
| **Gestão de Sistema** | System Center Configuration Manager CB 1606 | Quer investigar uma solução híbrida do Intune |
| **Solução VPN** | Cisco AnyConnect |  |


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para desenvolver o seu plano de estrutura do Intune.

## <a name="choose-an-intune-deployment-option"></a>Selecionar uma opção de implementação do Intune

O Intune oferece duas opções de implementação: autónoma e híbrida. Autónoma refere-se ao serviço do Intune em execução na cloud, híbridas refere-se para a integração do Intune com o System Center Configuration Manager. Este guia destina-se principalmente para a utilização da opção autónoma. [Escolher a opção que melhor se adapta aos seus requisitos empresariais](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management).

> [!Important]
>Integração de novos clientes MDM híbrida foi preterida. Para obter mais informações, consulte a [mover da gestão de dispositivos móveis híbrida para o Intune no Azure](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150) postagem de blog.


## <a name="intune-tenant-location"></a>Localização de inquilinos do Intune

Se a sua organização tiver uma presença global, quando subscrever o serviço, certifique-se de que planeia onde o seu inquilino reside. O país é definido quando se inscreve numa subscrição do Intune pela primeira vez e mapeado para as regiões do mundo apresentadas abaixo:

-   América do Norte

-   Europa, Médio Oriente e África

-   Ásia e Pacífico

>[!IMPORTANT]
> Não é possível mudar a localização do inquilino nem o país posteriormente.

## <a name="external-dependencies"></a>Dependências externas

As dependências externas são produtos e serviços que estão separados do Intune, mas são um requisito do Intune ou podem integrar-se com o Intune. É importante identificar os requisitos de dependências externas e como configurá-las. Alguns exemplos de dependências externas comuns são:

-   identidade

-   Grupos de utilizadores e de dispositivos

-   Infraestrutura de chaves públicas (PKI)

A seguir, vamos explorar essas dependências externas comuns em mais detalhes.

### <a name="identity"></a>identidade

A identidade é a forma como identificamos os utilizadores que pertencem à sua organização e estão a inscrever um dispositivo. O Intune necessita do Azure Active Directory (Azure AD) como fornecedor de identidade do utilizador. Se já estiver a utilizar este serviço, pode utilizar a sua identidade existente na cloud. Além disso, o Azure AD Connect é a ferramenta recomendada para sincronizar as suas identidades de utilizador no local com os serviços da Microsoft na cloud. Se a sua organização já utilizar o Office 365, é importante que o Intune utilize o mesmo ambiente do Azure AD.

Saiba mais sobre os seguintes requisitos de identidade do Intune:

- [Requisitos de identidade](https://docs.microsoft.com/azure/active-directory/understand-azure-identity-solutions).

- [Requisitos da sincronização de diretórios](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect).

- [Requisitos de autenticação multifator](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

### <a name="user-and-device-groups"></a>Grupos de utilizadores e de dispositivos

Os grupos de utilizadores e de dispositivos determinam o destino de uma implementação, incluindo políticas, aplicações e perfis. Tem de determinar quais os grupos de utilizadores e de dispositivos necessários.

Recomendamos que crie todos os grupos no Active Directory no local e, em seguida, sincronize com o Azure AD. Saiba mais sobre o planeamento e a criação de grupos de utilizadores e de dispositivos:

-   [Planear os grupos de utilizadores e de dispositivos](users-add.md).

-   [Criar grupos de utilizadores e de dispositivos](groups-add.md).

### <a name="public-key-infrastructure-pki"></a>Infraestrutura de chaves públicas (PKI)
A infraestrutura de chaves públicas fornece certificados para dispositivos ou utilizadores de forma a autenticar a um serviço com segurança. O Intune suporta uma infraestrutura PKI da Microsoft. Os certificados de dispositivos e utilizadores podem ser emitidos para um dispositivo móvel para cumprir requisitos de autenticação baseados em certificados. Antes de utilizar certificados, tem de determinar se precisa dos mesmos, se a infraestrutura de rede suporta a autenticação baseada em certificados e se os certificados estão a ser utilizados no ambiente existente.

Se estiver a planear utilizar certificados com VPN, Wi-Fi ou perfis de e-mail com o Intune, certifique-se de que tem uma [infraestrutura PKI suportada no local](certificates-configure.md), pronta para criar e implementar perfis de certificado.

Além disso, se forem emitidos certificados SCEP, tem de determinar que servidor irá alojar a funcionalidade Serviço de Inscrição de Dispositivos de Rede (NDES) e como a comunicação irá ocorrer.

Saiba mais sobre:

-   [Como configurar perfis de certificado do Intune](certificates-configure.md)

-   [Como configurar a infraestrutura de certificados para o SCEP](certificates-scep-configure.md)

-   [Como configurar a infraestrutura de certificados para o PFX](certficates-pfx-configure.md)




## <a name="device-platform-considerations"></a>Considerações de plataformas de dispositivos

Analise mais atentamente os seguintes aspetos dos seus dispositivos para perceber como geri-los corretamente.

-   Plataformas de dispositivos suportadas

-   Dispositivos

-   Propriedade dos dispositivos

-   Inscrição em massa

Analisemos estas áreas mais detalhadamente.

### <a name="determine-supported-device-platforms"></a>Determinar plataformas de dispositivos suportados

É necessário saber que dispositivos estarão no ambiente e confirmar se são ou não suportados pelo Intune durante a criação da sua estrutura. O Intune suporta plataformas iOS, Android e Windows.

[Lista completa dos dispositivos suportados pelo Intune](supported-devices-browsers.md).

### <a name="devices"></a>Dispositivos

O Intune gere dispositivos móveis para proteger dados empresariais e permite que os utilizadores finais trabalhem em mais locais. O Intune suporta várias plataformas de dispositivos, pelo que recomendamos que documente os dispositivos, as plataformas de SO e as versões que serão suportadas na estrutura da sua organização. Por exemplo:

| **Plataforma de dispositivo** | **Versões do SO** |
|:---:|:---:|
| iOS – iPhone | 10.0+ |                
| iOS – iPad | 10.0+ |               
| Android – Samsung Knox Standard | 4.0+ |
| Tablet Windows 10 | 10+ |


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para desenvolver a sua lista de dispositivos.
### <a name="device-ownership"></a>Propriedade dos dispositivos

O Intune suporta dispositivos pessoais e dispositivos pertencentes à empresa. Um dispositivo é considerado propriedade da empresa se for inscrito por um gestor de inscrição de dispositivos ou programa de registo de aparelho. Por exemplo, um dispositivo é inscrito com o Programa de Registo de Aparelho (DEP) da Apple, marcado como empresarial e colocado num grupo de dispositivos que recebe políticas e aplicações empresariais filtradas.

Consulte [secção 3: Determinar requisitos de cenários de casos de utilização](planning-guide-requirements.md) para obter mais informações sobre empresarial e BYOD casos de utilização.

### <a name="bulk-enrollment"></a>Inscrição em massa

 Pode inscrever dispositivos em massa de formas diferentes consoante a plataforma. Se necessitar da inscrição em massa, comece por [determinar o método de inscrição em massa](device-enrollment.md) e inclua-o na sua estrutura.

## <a name="feature-requirements"></a>Requisitos de funcionalidades

Nestas secções, analisamos as seguintes funcionalidades e capacidades que estão alinhadas com os seus requisitos de cenários de casos de utilização:

-   Políticas de termos e condições

-   Políticas de configuração

-   Perfis de recursos

-   Aplicações

-   Política de conformidade

-   Acesso condicional

Analisemos cada uma destas áreas mais detalhadamente.

### <a name="terms-and-conditions-policies"></a>Políticas de termos e condições

Pode utilizar [termos e condições](terms-and-conditions-create.md) para explicar as políticas ou condições que têm de ser aceites por um utilizador final antes da inscrição do respetivo dispositivo. O Intune suporta a capacidade de adicionar e implementar múltiplas políticas de termos e condições a grupos de utilizadores.

Tem de determinar se as políticas de termos e condições são necessárias. Se for o caso, quem será responsável por fornecer essas informações na organização. Segue-se um exemplo de como documentar a política de termos e condições.

| **Nome de Termos e Condições** | **Caso de utilização** | **Grupo de destino** |
|:---:|:---:|:---:|
| T&C Empresarial | Empresarial | Utilizadores empresariais |                 
| T&C BYOD | BYOD | Utilizadores de BYOD |                


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para mapear os seus termos e condições nos seus grupos de utilizadores.

### <a name="configuration-policies"></a>Políticas de configuração

Utilize políticas de configuração para gerir as funcionalidades e as definições de segurança num dispositivo. Ao estruturar as suas políticas de configuração, consulte a secção dos requisitos de casos de utilização para determinar as configurações necessárias para dispositivos do Intune. Documente as definições e como devem ser configuradas. Documente também que grupos de dispositivos ou utilizadores serão filtrados.

Deve criar pelo menos uma política de configuração por plataforma. Se for necessário, pode criar várias políticas de configuração por plataforma. Segue-se um exemplo da estruturação de quatro políticas de configuração diferentes para diversas plataformas e cenários de casos de utilização.

| **Nome da política** | **Plataforma de dispositivo** | **Definições** | **Grupo de destino** |   
|:---:|:---:|:---:|:---:|
| Empresarial – iOS | iOS | PIN é obrigatório, comprimento: 6, restringir a cópia de segurança da Cloud | Dispositivos Empresariais |                                                           
| Empresarial – Android | Android | PIN é obrigatório, comprimento: 6, restringir a cópia de segurança da Cloud | Dispositivos Empresariais |                                                           
| BYOD – iOS  | iOS | PIN é obrigatório, comprimento: 4 | Dispositivos BYOD |
| BYOD – Android  | Android | PIN é obrigatório, comprimento: 4 | Dispositivos BYOD |


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar as suas necessidades de políticas de configuração.

### <a name="profiles"></a>Perfis

Utilize perfis para ajudar o utilizador final a ligar-se a dados da empresa. O Intune suporta muitos tipos de perfis. Veja os requisitos e casos de utilização para determinar quando os perfis serão configurados. Todos os perfis de dispositivos são categorizados por tipo de plataforma e devem ser incluídos na documentação da estrutura.

-   Perfis de certificados

-   Perfil Wi-Fi

-   Perfil VPN

-   Perfil de e-mail

Analisemos cada tipo de perfil mais detalhadamente.

#### <a name="certificate-profiles"></a>Perfis de certificados

Os perfis de certificados permitem ao Intune emitir um certificado para um utilizador ou dispositivo. O Intune suporta o seguinte:

-   Protocolo SCEP (Simple Certificate Enrollment Protocol)

-   Certificado de Raiz Fidedigna

-   Certificado PFX.

Recomendamos que documente que grupos de utilizadores precisam de um certificado, quantos perfis de certificado são necessários e para que grupos de utilizadores devem ser implementados.

>[!NOTE]
> Lembre-se de que o certificado de raiz fidedigna é necessário para o certificado SCEP, pelo que deve garantir que todos os utilizadores filtrados para o certificado SCEP também recebem um certificado de raiz fidedigna. Se precisar de certificados SCEP, estruture e documente que modelos de certificados SCEP serão necessários.

Eis um exemplo de como pode documentar os certificados durante a estruturação:

| **Tipo** | **Nome do perfil** | **Plataforma de dispositivo** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| AC de Raiz | AC de Raiz Empresarial | Android, iOS, Windows Mobile | Empresarial, BYOD  |                                                           
| SCEP | Certificado de Utilizadores | Android, iOS, Windows Mobile | Empresarial, BYOD |                                                           


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar as suas necessidades de perfis de certificado.

#### <a name="wi-fi-profile"></a>Perfil Wi-Fi

Os perfis de Wi-Fi são utilizados para ligar automaticamente um dispositivo móvel a uma rede sem fios. O Intune suporta a implementação de perfis de Wi-Fi em todas as plataformas suportadas. Saiba mais sobre [como o Intune suporta perfis de Wi-Fi.](wi-fi-settings-configure.md)

Segue-se um exemplo de uma estrutura de um perfil de Wi-Fi:

| **Tipo** | **Nome do perfil** | **Plataforma de dispositivo** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| Wi-Fi | Perfil de Wi-Fi na Ásia | Android | Empresarial, BYOD na região da Ásia|                                                           
| Wi-Fi | Perfil de Wi-Fi da América do Norte | Android, iOS, Windows 10 Mobile | Empresarial, BYOD na região da América do Norte |                                                           


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar as suas necessidades de perfis de Wi-Fi.

#### <a name="vpn-profile"></a>Perfil VPN

Os perfis VPN permitem aos utilizadores aceder seguramente à sua rede a partir de localizações remotas. O Intune suporta perfis VPN de ligações VPN móveis nativas e de fornecedores de terceiros. Saiba mais sobre os [fornecedores e perfis VPN suportados pelo Intune](vpn-settings-configure.md).

Segue-se um exemplo de como documentar a estrutura de um perfil VPN.

| **Tipo** | **Nome do perfil** | **Plataforma de dispositivo** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| VPN | Perfil VPN Cisco qualquer ligação | Android, iOS, Windows 10 Mobile | Empresarial, BYOD na América do Norte e Alemanha|                                                           
| VPN | Pulse Secure | Android | Empresarial, BYOD na região da Ásia |                                                           


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar as suas necessidades de perfis de VPN.
#### <a name="email-profile"></a>Perfil de e-mail

Os perfis de e-mail permitem a um cliente de e-mail ser automaticamente configurado com informações de ligação e configuração de e-mail. O Intune suporta perfis de e-mail em determinados países. Saiba mais sobre os [perfis de e-mail e das plataformas suportadas](email-settings-configure.md).

Segue-se um exemplo de como documentar a estrutura de perfis de e-mail:

| **Tipo** | **Nome do perfil** | **Plataforma de dispositivo** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| Perfil de e-mail | Perfil de e-mail iOS | iOS | Empresarial – Técnico de informação BYOD |                                                           
| Perfil de e-mail | Perfil de e-mail Android Knox | Android Knox | BYOD |


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar as suas necessidades de perfis de e-mail.
### <a name="apps"></a>Aplicações

Pode utilizar o Intune para disponibilizar aplicações aos utilizadores ou dispositivos de várias formas. O tipo de aplicação inclui aplicações de instalador de software, aplicações de uma loja de aplicações pública, ligações externas ou aplicações iOS geridas. Além das implementações de aplicações individuais, pode gerir e implementar aplicações compradas em volume obtidas através dos programas de aquisição em volume para iOS e Windows. Saiba mais sobre:

-   [Os tipos de aplicações que pode fornecer](app-management.md)

-   [Volume Purchase Program for Business (VPP) iOS](vpp-apps-ios.md)

-   [Aplicações da Loja Microsoft para Empresas](windows-store-for-business.md)

#### <a name="app-type-requirements"></a>Requisitos de tipos de aplicações

Uma vez que as aplicações podem ser implementadas para utilizadores e dispositivos, recomendamos que decida que aplicações serão geridas pelo Intune. Ao compilar a lista, tente responder às seguintes questões:

-   As aplicações requerem integração com os serviços da cloud?

-   Todas as aplicações estarão disponíveis para utilizadores BYOD?

-   Quais são as opções de implementação disponíveis para estas aplicações?

-   A sua empresa necessita de fornecer acesso a dados de aplicações Software como um serviço (SaaS) aos seus parceiros?

-   As aplicações necessitam de acesso à Internet a partir dos dispositivos dos utilizadores?

-   As aplicações estão publicamente disponíveis numa loja de aplicações ou são aplicações de linha de negócio (LOB) personalizadas?


#### <a name="app-protection-policies"></a>Políticas de proteção de aplicações

As políticas de proteção de aplicações minimizam a perda de dados ao definir como a aplicação gere os dados empresariais. O Intune suporta políticas de proteção de aplicações para qualquer aplicação criada para funcionar com a gestão de aplicações móveis. Ao estruturar a política de proteção de aplicações, tem de decidir que restrições pretende atribuir aos dados empresariais numa determinada aplicação. Recomendamos que reveja como funcionam as [políticas de proteção de aplicações](app-protection-policy.md). Segue-se um exemplo de como documentar as aplicações existentes e que proteção é necessária.

| **Aplicação** | **Objetivo** | **Plataformas** | **Caso de utilização** | **Política de proteção de aplicações** |
|:---:|:---:|:---:|:---:|:---:|
| Outlook Mobile  | Disponível | iOS | Empresarial – Executivos | Não pode ser desbloqueado por jailbreak, encriptar ficheiros |                                                         
| Word | Disponível | iOS, Android – Samsung Knox, não Knox, Windows 10 Mobile | Empresarial, BYOD | Não pode ser desbloqueado por jailbreak, encriptar ficheiros |                                                         


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar as suas necessidades de políticas de proteção de aplicações.
#### <a name="compliance-policies"></a>Políticas de conformidade

As políticas de conformidade determinam se um dispositivo cumpre determinados requisitos. O Intune utiliza políticas de conformidade para determinar se um dispositivo é considerado como estando ou não em conformidade. O estado de conformidade pode depois ser utilizado para restringir ou permitir o acesso a recursos da empresa. Se for necessário acesso condicional, recomendamos que estruture uma [política de conformidade do dispositivo](device-compliance.md).

Veja os requisitos e casos de utilização para determinar quantas políticas de conformidade do dispositivo são necessárias e quais são os grupos de utilizadores de destino. Além disso, terá de decidir durante quanto tempo um dispositivo pode estar offline sem dar entrada, antes de ser considerado como não estando em conformidade.

Segue-se um exemplo de como estruturar uma política de conformidade:

| **Nome da política** | **Plataforma de dispositivo** | **Definições** | **Grupo de destino** |   
|:---:|:---:|:---:|:---:|
| Política de conformidade | iOS, Android – Samsung Knox, não Knox, Windows 10 Mobile | PIN – obrigatório, não pode ser desbloqueado por jailbreak | Empresarial, BYOD |


Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar as suas necessidade de políticas de conformidade.
#### <a name="conditional-access-policies"></a>Políticas de acesso condicional

O acesso condicional é utilizado para permitir que apenas os dispositivos em conformidade acedam ao e-mail e a outros recursos da empresa. O Intune funciona com o Enterprise Mobility + Security (EMS) para controlar o acesso aos recursos da empresa. Decidir se exigir acesso condicional, e o que deve ser protegido. Saiba mais sobre o [acesso condicional](conditional-access.md).

Para acesso online, decida que plataformas e grupos de utilizadores serão visados pelas políticas de acesso condicional. Além disso, determine se precisa de instalar ou configurar o conector do Intune para o Exchange no local: 

-   [Exchange no local](exchange-connector-install.md)

Eis um exemplo de como documentar políticas de acesso condicional:

| **Serviço** | **Plataformas de Autenticação Moderna** | **Autenticação Básica** | **Casos de utilização** |   
|:---:|:---:|:---:|:---:|
| Exchange online | iOS, Android | Bloquear dispositivos não conformes em plataformas suportadas pelo Intune | Empresarial, BYOD |
| SharePoint Online | iOS, Android |  | Empresarial, BYOD |

Pode [transferir um modelo da tabela acima](https://gallery.technet.microsoft.com/Intune-deployment-planning-fae156c2?redir=0) para identificar as suas necessidades de políticas de acesso condicional.

## <a name="next-steps"></a>Passos Seguintes

A próxima secção fornece orientações sobre o [processo de implementação do Intune](planning-guide-onboarding.md).
