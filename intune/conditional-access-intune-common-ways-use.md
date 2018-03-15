---
title: Acesso condicional com o Intune
titlesuffix: Azure portal
description: Formas comuns de utilizar o acesso condicional com o Intune
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 02/22/2018
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d5ec945cdbc4efa791edc51e659a1546876446c5
ms.sourcegitcommit: 1978a30ab1af0f43aa5f447690d0bbcdcb9b563b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/24/2018
---
# <a name="common-ways-to-use-conditional-access-with-intune"></a>Formas comuns de utilizar o acesso condicional com o Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Existem dois tipos principais de acesso condicional com o Intune. O acesso condicional baseado no dispositivo é o primeiro tipo. O acesso condicional baseado na aplicação é o segundo tipo. Precisa de configurar as políticas de conformidade relacionadas para promover a conformidade de acesso condicional na sua organização.

As informações abaixo ajudam-no a compreender como utilizar as funcionalidades de conformidade de *dispositivos móveis* do Intune e as funcionalidades de gestão (MAM) de *aplicações móveis* do Intune. 

## <a name="device-based-conditional-access"></a>Acesso condicional baseado no dispositivo

O Intune e o Azure Active Directory funcionam em conjunto para garantir que apenas os dispositivos geridos e conformes têm acesso ao e-mail, aos serviços do Office 365, a aplicações de Software como um serviço (SaaS) e a [aplicações no local](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). Além disso, pode definir uma política no Azure Active Directory para permitir que apenas os computadores que estão associados a um domínio ou os dispositivos móveis inscritos no Intune acedam aos serviços do Office 365.

O Intune fornece capacidades de política de conformidade de dispositivos que avaliam o estado de conformidade dos dispositivos. O estado de conformidade é comunicado ao Azure Active Directory que o utiliza para a imposição da política de acesso condicional no Azure Active Directory quando o utilizador tenta aceder aos recursos da empresa.

As políticas de acesso condicional com base no dispositivo para o Exchange Online e outros produtos do Office 365 são configuradas através do [portal do Azure](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).

-   Saiba mais sobre o [acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal).

-   Saiba mais sobre [a conformidade de dispositivos do Intune](device-compliance.md).

-   Saiba mais sobre a [proteção de e-mail, do Office 365 e de outros serviços que utilizam o acesso condicional com o Intune](https://docs.microsoft.com/intune-classic/deploy-use/restrict-access-to-email-and-o365-services-with-microsoft-intune).

### <a name="conditional-access-for-exchange-on-premises"></a>Acesso condicional para o Exchange no local

O acesso condicional pode servir para permitir ou bloquear o acesso ao **Exchange no local** com base nas políticas de conformidade de dispositivos e no estado de inscrição. Quando o acesso condicional é utilizado em combinação com uma política de conformidade de dispositivos, apenas os dispositivos compatíveis têm permissão para aceder ao Exchange no local.

Pode configurar definições avançadas no acesso condicional para um controlo mais granular, tais como:

-   Permitir ou bloquear determinadas plataformas.

-   Bloquear imediatamente dispositivos que não são geridos pelo Intune.

Qualquer dispositivo utilizado para aceder ao Exchange no local é verificado quanto à conformidade quando a conformidade do dispositivo e as políticas de acesso condicional são aplicadas.

Quando os dispositivos não cumprem as condições definidas, o utilizador final é orientado ao longo do processo de inscrição do dispositivo para corrigir o problema que está a fazer com que o dispositivo não esteja em conformidade.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Como o acesso condicional funciona para o Exchange no local

O conector do Intune Exchange solicita todos os registos do Exchange Active Sync (EAS) que existem no servidor do Exchange para que o Intune possa ter em conta esses registos EAS e mapeá-los para registos de dispositivo do Intune. Esses registos são dispositivos inscritos e reconhecido pelo Intune. Este processo permite ou bloqueia o acesso do e-mail.

Se o registo EAS for novo e o Intune não tiver conhecimento dele, o Intune emite um comandlet que bloqueia o acesso ao e-mail. Veja a seguir mais detalhes sobre como este processo funciona:

![Fluxograma do Exchange no local com CA](./media/ca-intune-common-ways-1.png)

1.  O utilizador tenta aceder ao e-mail empresarial, que está alojado no Exchange 2010 SP1 ou posterior no local.

2.  Se o dispositivo não for gerido pelo Intune, o acesso ao e-mail será bloqueado. O Intune envia uma notificação de bloqueio ao cliente EAS.

3.  O EAS recebe a notificação de bloqueio, move o dispositivo para a quarentena e envia o e-mail de quarentena com os passos de correção que incluem ligações para que os utilizadores possam inscrever os dispositivos.

4.  Ocorre o processo de Associação à área de trabalho, que é o primeiro passo para que o dispositivo seja gerido pelo Intune.

5.  O dispositivo é inscrito no Intune.

6.  O Intune mapeia o registo EAS para um registo de dispositivo e guarda o estado de conformidade do dispositivo.

7.  O ID de cliente EAS é registado pelo processo de Registo de Dispositivo do Azure AD, que cria uma relação entre o registo de dispositivo do Intune e o ID de cliente EAS.

8.  O Registo de Dispositivo do Azure AD guarda as informações de estado do dispositivo.

9.  Se o utilizador cumprir as políticas de acesso condicional, o Intune emite um comandlet através do conector do Intune Exchange que permite a sincronização da caixa de correio.

10. O servidor do Exchange envia a notificação ao cliente EAS para que o utilizador possa aceder ao e-mail.

#### <a name="whats-the-intune-role"></a>Qual é a função do Intune?

O Intune avalia e gere o estado do dispositivo.

#### <a name="whats-the-exchange-server-role"></a>Qual é a função de servidor do Exchange?

O servidor do Exchange fornece a API e a infraestrutura para mover os dispositivos para a quarentena.

> [!IMPORTANT]
> Tenha em atenção que o utilizador que está a utilizar o dispositivo tem de ter um perfil de conformidade atribuído para que o dispositivo seja avaliado em termos de conformidade. Se não estiver implementada nenhuma política de conformidade para o utilizador, o dispositivo será tratado como compatível e não serão aplicadas restrições de acesso.

### <a name="conditional-access-based-on-network-access-control"></a>Acesso condicional com base no controlo de acesso de rede

O Intune integrado com parceiros tais como Cisco ISE, Aruba Clear Pass e Citrix NetScaler fornece controlos de acesso com base na inscrição do Intune e o estado de conformidade do dispositivo.

Os utilizadores podem ter o acesso permitido ou recusado quando tentam aceder aos recursos de Wi-Fi ou VPN empresariais com base no facto de o dispositivo ser gerido e estar conforme com políticas de conformidade de dispositivo do Intune.

-   Saiba mais sobre a [integração de NAC com o Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Acesso condicional com base no risco do dispositivo

O Intune em parceria com fornecedores de Defesa Contra Ameaças para Dispositivos Móveis fornece uma solução de segurança para detetar malwares, trojans e outras ameaças em dispositivos móveis.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Como funciona a integração da Defesa Contra Ameaças para Dispositivos Móveis com o Intune

Quando os dispositivos móveis têm o agente de Defesa Contra Ameaças para Dispositivos Móveis instalado, o agente pode enviar mensagens de estado de conformidade para o Intune a comunicar se foi encontrada uma ameaça no próprio dispositivo móvel.

A integração da defesa contra ameaças para dispositivos móveis com o Intune constitui um fator importante nas decisões de acesso condicional com base no risco do dispositivo.

-   Saiba mais sobre a [defesa contra ameaças para dispositivos móveis do Intune](https://docs.microsoft.com/intune-classic/deploy-use/mobile-threat-defense).

### <a name="conditional-access-for-windows-pcs"></a>Acesso condicional para PCs Windows

O acesso condicional para PCs fornecem capacidades semelhantes disponíveis para dispositivos móveis. Vamos falar sobre as formas em que pode utilizar o acesso condicional ao gerir PCs com o Intune.

#### <a name="corporate-owned"></a>Pertencentes à empresa

-   **Associação a um domínio do AD no local:** esta tem sido a opção de implementação mais comum do acesso condicional para organizações, que estão razoavelmente confortáveis com o facto de que já estão a gerir os seus PCs através de políticas de grupo do AD e/ou do System Center Configuration Manager.

-   **Associação a um domínio do Azure AD e gestão do Intune:** este cenário está normalmente voltado para Escolha o Seu Próprio Dispositivo (CYOD) e cenários de computador portátil móvel, em que estes dispositivos são raramente ligados à rede da empresa. O dispositivo efetua a adesão ao Azure AD e é inscrito no Intune, que remove qualquer dependência no AD no local e controladores de domínio. Este procedimento pode ser utilizado como critério de acesso condicional ao aceder a recursos empresariais.

-   **Associação a um domínio do AD e System Center Configuration Manager:** a partir do ramo atual, o System Center Configuration Manager fornece capacidades de acesso condicional que podem avaliar a critérios específicos de conformidade, além de ser um PC associado a um domínio:

    -   O PC está encriptado?

    -   O malware está instalado? Está atualizado?

    -   O dispositivo tem jailbreak ou root?

#### <a name="bring-your-own-device-byod"></a>Bring your own device (BYOD)

-   **Associação à área de trabalho e gestão do Intune:** aqui, o utilizador pode associar os seus dispositivos pessoais para aceder a serviços e recursos da empresa. Pode utilizar a Associação à área de trabalho e inscrever dispositivos no Intune para receber políticas com base no nível do dispositivo, que também é outra opção para avaliar os critérios de acesso condicional.

## <a name="app-based-conditional-access"></a>Acesso condicional com base nas aplicações

O Intune e o Azure Active Directory funcionam em conjunto para garantir que apenas aplicações geridas podem aceder ao e-mail empresarial ou a outros serviços do Office 365.

-   Saiba mais sobre o [acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md).

## <a name="next-steps"></a>Passos seguintes

[Como configurar o acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Como instalar o conector do Exchange no local com o Intune](https://docs.microsoft.com/intune/exchange-connector-install).

[Como criar uma política de acesso condicional para o Exchange no local](conditional-access-exchange-create.md)
