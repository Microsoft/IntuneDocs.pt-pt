---
title: Cenários de acesso condicional | Microsoft Intune
description: Saiba como o acesso condicional do Intune é geralmente utilizado para acesso condicional baseado no dispositivo e baseado na aplicação.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 03/31/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1538693923a1fcefcfee06022ed4c11d746c3be9
ms.sourcegitcommit: e63e3debb5f4d9a757f767913e72e39742137b17
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58788503"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Quais são as formas comuns de utilizar o acesso condicional com o Intune?

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Existem dois tipos de acesso condicional com o Intune: acesso condicional baseado no dispositivo e acesso condicional baseado na aplicação. Precisa de configurar as políticas de conformidade relacionadas para promover a conformidade de acesso condicional na sua organização. O acesso condicional é normalmente utilizado para fazer coisas como permitir ou bloquear o acesso ao Exchange no local, controlar o acesso à rede ou integrar com uma solução de Defesa Contra Ameaças para Dispositivos Móveis.

As informações abaixo ajudam-no a compreender como utilizar as funcionalidades de conformidade de *dispositivos móveis* do Intune e as funcionalidades de gestão (MAM) de *aplicações móveis* do Intune. 

> [!NOTE]
> O acesso condicional é uma funcionalidade do Azure Active Directory incluída com uma licença do Azure Active Directory Premium. O Intune melhora esta funcionalidade ao adicionar à solução a conformidade de dispositivos móveis e a gestão de aplicações móveis. O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*.  

## <a name="device-based-conditional-access"></a>Acesso condicional baseado no dispositivo

O Intune e o Azure Active Directory funcionam em conjunto para garantir que apenas os dispositivos geridos e conformes têm acesso ao e-mail, aos serviços do Office 365, a aplicações de Software como um serviço (SaaS) e a [aplicações no local](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). Além disso, pode definir uma política no Azure Active Directory para permitir que apenas os computadores que estão associados a um domínio ou os dispositivos móveis inscritos no Intune acedam aos serviços do Office 365.

O Intune fornece capacidades de política de conformidade de dispositivos que avaliam o estado de conformidade dos dispositivos. O estado de conformidade é comunicado ao Azure Active Directory que o utiliza para a imposição da política de acesso condicional no Azure Active Directory quando o utilizador tenta aceder aos recursos da empresa.

As políticas de acesso condicional com base no dispositivo para o Exchange Online e outros produtos do Office 365 são configuradas através do [portal do Azure](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).
-   Saiba mais sobre [necessitam de dispositivos com acesso condicional no Azure Active Directory geridos](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/require-managed-devices).

-   Saiba mais sobre [a conformidade de dispositivos do Intune](device-compliance.md).

-   Saiba mais sobre [suportado navegadores com o acesso condicional no Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/conditional-access/technical-reference#supported-browsers).

> [!NOTE]
> Em dispositivos Android, quando ativar o acesso com base do dispositivo para o Sharepoint Online ou acesso ao Exchange Online, baseada no Browser utilizadores tem de ativar a **ativar o acesso ao Browser** opção no dispositivo inscrito da seguinte forma:
> 1. Inicie a aplicação **Portal da Empresa**.
> 2. Aceda à página **Definições** a partir das reticências (…) ou do botão do menu de hardware.
> 3. Prima o botão **Ativar o Acesso ao Browser**. 
> 4. No browser Chrome, termine a sessão no Office 365 e reinicie o Chrome.

### <a name="conditional-access-for-exchange-on-premises"></a>Acesso condicional para o Exchange no local

O acesso condicional pode servir para permitir ou bloquear o acesso ao **Exchange no local** com base nas políticas de conformidade de dispositivos e no estado de inscrição. Quando o acesso condicional é utilizado em combinação com uma política de conformidade de dispositivos, apenas os dispositivos compatíveis têm permissão para aceder ao Exchange no local.

Pode configurar definições avançadas no acesso condicional para um controlo mais granular, tais como:

-   Permitir ou bloquear determinadas plataformas.

-   Bloquear imediatamente dispositivos que não são geridos pelo Intune.

Qualquer dispositivo utilizado para aceder ao Exchange no local é verificado quanto à conformidade quando a conformidade do dispositivo e as políticas de acesso condicional são aplicadas.

Quando os dispositivos não cumprem as condições definidas, o utilizador final é orientado ao longo do processo de inscrição do dispositivo para corrigir o problema que está a fazer com que o dispositivo não esteja em conformidade.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Como o acesso condicional funciona para o Exchange no local

O conector do Intune Exchange solicita todos os registos do Exchange Active Sync (EAS) que existem no servidor do Exchange para que o Intune possa ter em conta esses registos EAS e mapeá-los para registos de dispositivo do Intune. Esses registos são dispositivos inscritos e reconhecido pelo Intune. Este processo permite ou bloqueia o acesso do e-mail.

Se o registo EAS for novo e o Intune não tiver conhecimento dele, o Intune emite um cmdlet (pronunciado "command-let"), que bloqueia o acesso a emails. Veja a seguir mais detalhes sobre como este processo funciona:

![Fluxograma do Exchange no local com CA](./media/ca-intune-common-ways-1.png)

1.  O utilizador tenta aceder ao e-mail empresarial, que está alojado no Exchange 2010 SP1 ou posterior no local.

2.  Se o dispositivo não for gerido pelo Intune, será bloqueado o acesso ao e-mail. O Intune envia uma notificação de bloqueio para o cliente EAS.

3.  O EAS recebe a notificação de bloqueio, move o dispositivo para a quarentena e envia o e-mail de quarentena com os passos de remediação que incluem ligações para que os utilizadores podem inscrever os respetivos dispositivos.

4.  Ocorre o processo de Associação à área de trabalho, que é o primeiro passo para que o dispositivo seja gerido pelo Intune.

5.  O dispositivo é inscrito no Intune.

6.  O Intune mapeia o registo EAS para um registo de dispositivo e guarda o estado de conformidade do dispositivo.

7.  O ID de cliente EAS é registado pelo processo de Registo de Dispositivo do Azure AD, que cria uma relação entre o registo de dispositivo do Intune e o ID de cliente EAS.

8.  O Registo de Dispositivo do Azure AD guarda as informações de estado do dispositivo.

9.  Se o utilizador cumprir as políticas de acesso condicional, o Intune emite um cmdlet através do conector do Intune Exchange que permite que a caixa de correio a sincronizar.

10. O servidor do Exchange envia a notificação ao cliente EAS para que o utilizador possa aceder ao e-mail.

#### <a name="whats-the-intune-role"></a>Qual é a função do Intune?

O Intune avalia e gere o estado do dispositivo.

#### <a name="whats-the-exchange-server-role"></a>Qual é a função de servidor do Exchange?

Servidor do Exchange fornece a API e a infraestrutura para mover os dispositivos para colocar em quarentena.

> [!IMPORTANT]
> Tenha em atenção que o utilizador que está a utilizar o dispositivo tem de ter um perfil de conformidade atribuído a elas para que o dispositivo pode ser avaliado relativamente à conformidade. Se não estiver implementada nenhuma política de conformidade para o utilizador, o dispositivo será tratado como compatível e não serão aplicadas restrições de acesso.

### <a name="conditional-access-based-on-network-access-control"></a>Acesso condicional com base no controlo de acesso de rede

O Intune integrado com parceiros tais como Cisco ISE, Aruba Clear Pass e Citrix NetScaler fornece controlos de acesso com base na inscrição do Intune e o estado de conformidade do dispositivo.

Os utilizadores podem ter o acesso permitido ou recusado quando tentam aceder aos recursos de Wi-Fi ou VPN empresariais com base no facto de o dispositivo ser gerido e estar conforme com políticas de conformidade de dispositivo do Intune.

-   Saiba mais sobre a [integração de NAC com o Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Acesso condicional com base no risco do dispositivo

O Intune em parceria com fornecedores de Defesa Contra Ameaças para Dispositivos Móveis fornece uma solução de segurança para detetar malware, trojans e outras ameaças em dispositivos móveis.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Como funciona a integração da Defesa Contra Ameaças para Dispositivos Móveis com o Intune

Quando os dispositivos móveis têm o agente de Defesa Contra Ameaças para Dispositivos Móveis instalado, o agente pode enviar mensagens de estado de conformidade para o Intune a comunicar se foi encontrada uma ameaça no próprio dispositivo móvel.

A integração da defesa contra ameaças para dispositivos móveis com o Intune constitui um fator importante nas decisões de acesso condicional com base no risco do dispositivo.

-   Saiba mais sobre a [defesa contra ameaças para dispositivos móveis do Intune](mobile-threat-defense.md).

### <a name="conditional-access-for-windows-pcs"></a>Acesso condicional para PCs Windows

O acesso condicional para PCs fornece funcionalidades semelhantes às que se encontram disponíveis para dispositivos móveis. Vamos falar sobre as formas em que pode utilizar o acesso condicional ao gerir PCs com o Intune.

#### <a name="corporate-owned"></a>Pertencentes à empresa

-   **No local associados a um domínio do AD:** Esta opção é utilizada frequentemente por organizações que estão razoavelmente confortáveis com a forma como eles já estão gerenciando seus PCs através de políticas de grupo do AD e/ou o System Center Configuration Manager.

-   **O Azure AD associado a um domínio e de gestão do Intune:** Este cenário está normalmente voltado para escolha seu próprio dispositivo (CYOD) e o roaming de laptop de cenários em que estes dispositivos são raramente ligados à rede empresarial. O dispositivo efetua a adesão ao Azure AD e é inscrito no Intune, que remove qualquer dependência no AD no local e controladores de domínio. Este procedimento pode ser utilizado como critério de acesso condicional ao aceder a recursos empresariais.

-   **AD associados a um domínio e o System Center Configuration Manager:** A partir do ramo atual, o System Center Configuration Manager fornece capacidades de acesso condicional que podem avaliar a critérios específicos de conformidade, além de ser um PC associado a um domínio:

    -   O PC está encriptado?

    -   O malware está instalado? Está atualizado?

    -   O dispositivo tem jailbreak ou root?

#### <a name="bring-your-own-device-byod"></a>Bring your own device (BYOD)

-   **Associação à área de trabalho e gestão do Intune:** Aqui, o utilizador pode associar seus dispositivos pessoais para aceder a recursos da empresa e serviços. Pode utilizar a associação à área de trabalho e inscrever dispositivos no MDM do Intune para receber políticas ao nível do dispositivo, que também é outra opção para avaliar os critérios de acesso condicional.

Saiba mais sobre [gestão de dispositivos no Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/devices/overview).

## <a name="app-based-conditional-access"></a>Acesso condicional com base nas aplicações

O Intune e o Azure Active Directory funcionam em conjunto para garantir que apenas aplicações geridas podem aceder ao e-mail empresarial ou a outros serviços do Office 365.

-   Saiba mais sobre o [acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md).

## <a name="next-steps"></a>Passos Seguintes

[Como configurar o acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Como instalar o conector do Exchange no local com o Intune](https://docs.microsoft.com/intune/exchange-connector-install).

[Como criar uma política de acesso condicional para o Exchange no local](conditional-access-exchange-create.md)
