---
title: Cenários de Acesso Condicional
titleSuffix: Microsoft Intune
description: Saiba como o Intune Conditional Access é comumente utilizado para acesso condicional baseado em dispositivos e baseado em aplicações.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: a0b8e55e-c3d8-4599-be25-dc10c1027b62
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; get-started; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8fe72ccf07cb0280a7d0ce929f8f08df7738bfcc
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856041"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Quais são as formas comuns de usar o Acesso Condicional com Intune?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


Existem dois tipos de acesso condicional com o Intune: acesso condicional baseado no dispositivo e acesso condicional baseado na aplicação. Precisa de configurar as políticas de conformidade relacionadas para promover a conformidade de acesso condicional na sua organização. O acesso condicional é comumente usado para fazer coisas como permitir ou bloquear o acesso ao Exchange, controlar o acesso à rede ou integrar-se com uma solução de Defesa de Ameaças Móveis.
 
As informações deste artigo podem ajudá-lo a entender como usar as capacidades de conformidade do *dispositivo* móvel Intune e as capacidades de gestão de *aplicações* móveis Intune (MAM). 

> [!NOTE]
> O Acesso Condicional é uma capacidade de Diretório Ativo Azure que está incluída com uma licença Azure Ative Directory Premium. O Intune melhora esta funcionalidade ao adicionar à solução a conformidade de dispositivos móveis e a gestão de aplicações móveis. O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*.  

## <a name="device-based-conditional-access"></a>Acesso Condicional baseado em dispositivos

Intune e Azure Ative Directory trabalham em conjunto para garantir que apenas dispositivos geridos e conformes podem aceder a e-mails, serviços do Office 365, software como um serviço (SaaS) e [aplicações no local.](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started) Além disso, pode definir uma política no Diretório Ativo Azure para permitir apenas computadores ou dispositivos móveis ligados ao domínio que estão matriculados no Intune para aceder aos serviços do Office 365.

O Intune fornece capacidades de política de conformidade de dispositivos que avaliam o estado de conformidade dos dispositivos. O estado de conformidade é comunicado ao Azure Ative Directory que o utiliza para impor a política de Acesso Condicional criada no Diretório Ativo do Azure quando o utilizador tenta aceder aos recursos da empresa.

As políticas de acesso condicional baseadas em dispositivos para o Exchange online e outros produtos do Office 365 estão configuradas através do [portal Azure.](../fundamentals/what-is-intune.md)

- Saiba mais sobre a Necessidade de [dispositivos geridos com acesso condicional no Diretório Ativo Azure.](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)

- Saiba mais sobre [a conformidade de dispositivos do Intune](device-compliance-get-started.md).

- Saiba mais sobre [navegadores Suportados com Acesso Condicional no Diretório Ativo Azure.](https://docs.microsoft.com/azure/active-directory/conditional-access/technical-reference#supported-browsers)

> [!NOTE]
> Nos dispositivos Android, quando ativar o acesso baseado no dispositivo para o SharePoint Online ou o acesso baseado no navegador ao Exchange Online, os utilizadores devem ativar a opção **enable Browser Access** no dispositivo inscrito da seguinte forma:
> 1. Inicie a aplicação **Portal da Empresa**.
> 2. Aceda à página **Definições** a partir das reticências (…) ou do botão do menu de hardware.
> 3. Prima o botão **Ativar acesso ao browser** . 
> 4. No browser Chrome, termine a sessão no Office 365 e reinicie o Chrome.

### <a name="conditional-access-based-on-network-access-control"></a>Acesso condicional com base no controlo de acesso de rede

Intune integra-se com parceiros como cisco ISE, Aruba Clear Pass e Citrix NetScaler para fornecer controlos de acesso com base na inscrição intune e no estado de conformidade do dispositivo.

Os utilizadores podem ser autorizados ou negados acesso a recursos Wi-Fi corporativos ou VPN com base no facto de o dispositivo que estão a usar ser gerido e em conformidade com as políticas de conformidade do dispositivo Intune.

- Saiba mais sobre a [integração de NAC com o Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Acesso condicional com base no risco do dispositivo

O Intune em parceria com fornecedores de Defesa Contra Ameaças para Dispositivos Móveis fornece uma solução de segurança para detetar malware, trojans e outras ameaças em dispositivos móveis.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Como funciona a integração da Defesa Contra Ameaças para Dispositivos Móveis com o Intune

Quando os dispositivos móveis têm o agente de Defesa de Ameaças Móveis instalado, o agente envia mensagens de estado de conformidade para intune reportando quando uma ameaça é encontrada no próprio dispositivo móvel.

A integração da defesa de ameaças insinatos e móveis desempenha um fator nas decisões de acesso condicional baseadas no risco do dispositivo.

- Saiba mais sobre a [defesa contra ameaças para dispositivos móveis do Intune](mobile-threat-defense.md).

### <a name="conditional-access-for-windows-pcs"></a>Acesso condicional para PCs Windows

O acesso condicional para PCs fornece funcionalidades semelhantes às que se encontram disponíveis para dispositivos móveis. Vamos falar sobre as formas como podes usar o acesso condicional ao gerir computadores com o Intune.

#### <a name="corporate-owned"></a>Pertencentes à empresa

- **Nas instalações, o domínio ad:** Esta opção é comumente usada por organizações que são razoavelmente confortáveis com a forma como já estão a gerir os seus Computadores através de políticas de grupo aD ou De Configuração Manager.

- **O domínio Azure AD juntou-se e intune gestão:** Este cenário é para organizações que querem ser em primeiro lugar (isto é, principalmente, usar serviços em nuvem, com o objetivo de reduzir o uso de uma infraestrutura no local) ou apenas em nuvem (sem infraestrutura sem instalações). O Azure AD Join funciona bem num ambiente híbrido, permitindo o acesso a aplicações e recursos em nuvem e no local. O dispositivo junta-se à AD Azure e é matriculado na Intune, que pode ser usado como critérios de acesso condicional no acesso aos recursos corporativos.

#### <a name="bring-your-own-device-byod"></a>Bring your own device (BYOD)

- **Associação à área de trabalho e gestão do Intune:** aqui, o utilizador pode associar os seus dispositivos pessoais para aceder a serviços e recursos da empresa. Pode utilizar a adesão do Workplace e inscrever dispositivos no INTUNE MDM para receber políticas ao nível do dispositivo, que são outra opção para avaliar critérios de acesso condicional.

Saiba mais sobre [gestão de dispositivos no Diretório Ativo Azure.](https://docs.microsoft.com/azure/active-directory/devices/overview)

## <a name="app-based-conditional-access"></a>Acesso condicional com base nas aplicações

O Intune e o Azure Active Directory funcionam em conjunto para garantir que apenas aplicações geridas podem aceder ao e-mail empresarial ou a outros serviços do Office 365.

- Saiba mais sobre o [acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md).

### <a name="intune-conditional-access-for-exchange-on-premises"></a>Acesso condicional intune para intercâmbio no local

O acesso condicional pode servir para permitir ou bloquear o acesso ao **Exchange no local** com base nas políticas de conformidade de dispositivos e no estado de inscrição. Quando o acesso condicional é utilizado em combinação com uma política de conformidade de dispositivos, apenas os dispositivos compatíveis têm permissão para aceder ao Exchange no local.

Pode configurar definições avançadas no acesso condicional para um controlo mais granular, tais como:

- Permitir ou bloquear determinadas plataformas.

- Bloqueie imediatamente dispositivos que não são geridos pela Intune.

Qualquer dispositivo utilizado para aceder ao Exchange no local é verificado quanto à conformidade quando a conformidade do dispositivo e as políticas de acesso condicional são aplicadas.

Quando os dispositivos não cumprem as condições definidas, o utilizador final é guiado através do processo de inscrição do dispositivo para corrigir o problema que está a tornar o dispositivo incompatível.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Como o acesso condicional funciona para o Exchange no local

O acesso condicional à Troca no Local funciona de forma diferente das políticas baseadas no Acesso Condicional do Azure. Instala o conector intune Exchange on-instalações para interagir diretamente com o servidor Exchange. O conector do Intune Exchange solicita todos os registos do Exchange Active Sync (EAS) que existem no servidor do Exchange para que o Intune possa ter em conta esses registos EAS e mapeá-los para registos de dispositivo do Intune. Esses registos são dispositivos inscritos e reconhecido pelo Intune. Este processo permite ou bloqueia o acesso do e-mail.

Se o registo da EAS for novo e o Intune não o tiver conhecimento, intune emite um cmdlet (pronunciado "command-let") que direciona o servidor de Intercâmbio para bloquear o acesso ao e-mail. Seguem-se mais detalhes sobre o funcionamento deste processo:

![Fluxograma do Exchange no local com CA](./media/conditional-access-intune-common-ways-use/ca-intune-common-ways-1.png)

1. O utilizador tenta aceder ao e-mail empresarial, que está alojado no Exchange 2010 SP1 ou posterior no local.

2. Se o dispositivo não for gerido pela Intune, o acesso ao e-mail será bloqueado. Intune envia uma notificação de bloco ao cliente da EAS.

3. A EAS recebe a notificação do bloco, move o dispositivo para a quarentena e envia o e-mail de quarentena com passos de reparação que contêm links para que os utilizadores possam inscrever os seus dispositivos.

4. Ocorre o processo de Associação à área de trabalho, que é o primeiro passo para que o dispositivo seja gerido pelo Intune.

5. O dispositivo é inscrito no Intune.

6. O Intune mapeia o registo EAS para um registo de dispositivo e guarda o estado de conformidade do dispositivo.

7. O ID de cliente EAS é registado pelo processo de Registo de Dispositivo do Azure AD, que cria uma relação entre o registo de dispositivo do Intune e o ID de cliente EAS.

8. O Registo de Dispositivo do Azure AD guarda as informações de estado do dispositivo.

9. Se o utilizador cumprir as políticas de acesso condicional, o Intune emite um cmdlet através do conector Intune Exchange que permite sincronizar a caixa de correio.

10. O servidor do Exchange envia a notificação ao cliente EAS para que o utilizador possa aceder ao e-mail.


#### <a name="whats-the-intune-role"></a>Qual é o papel intune?

O Intune avalia e gere o estado do dispositivo.

#### <a name="whats-the-exchange-server-role"></a>Qual é o papel do servidor de troca?

O servidor de intercâmbio fornece API e infraestruturas para mover dispositivos para a quarentena.

> [!IMPORTANT]
> Tenha em mente que o utilizador que está a utilizar o dispositivo deve ter um perfil de conformidade e licença Intune atribuída a eles para que o dispositivo possa ser avaliado para o cumprimento. Se não estiver implementada nenhuma política de conformidade para o utilizador, o dispositivo será tratado como compatível e não serão aplicadas restrições de acesso.

## <a name="next-steps"></a>Próximos passos

[Como configurar o Acesso Condicional no Diretório Ativo Azure](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Configurar políticas de acesso condicional baseadas em aplicativos](app-based-conditional-access-intune-create.md)

[Como instalar o conector do Exchange no local com o Intune](exchange-connector-install.md).

[Como criar uma política de acesso condicional para o Exchange on-pre-presionéis](conditional-access-exchange-create.md)
