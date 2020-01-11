---
title: Cenários de acesso condicional
titleSuffix: Microsoft Intune
description: Saiba como o acesso condicional do Intune é comumente usado para acesso condicional baseado em dispositivo e em aplicativo.
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
ms.openlocfilehash: 92e6aa1a66429c6407556444e903c158aff9dfa0
ms.sourcegitcommit: 2506cdbfccefd42587a76f14ee50c3849dad1708
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75885987"
---
# <a name="what-are-common-ways-to-use-conditional-access-with-intune"></a>Quais são as maneiras comuns de usar o acesso condicional com o Intune?

[!INCLUDE [azure_portal](../includes/azure_portal.md)]


Existem dois tipos de acesso condicional com o Intune: acesso condicional baseado no dispositivo e acesso condicional baseado na aplicação. Precisa de configurar as políticas de conformidade relacionadas para promover a conformidade de acesso condicional na sua organização. O acesso condicional é comumente usado para fazer coisas como permitir ou bloquear o acesso ao Exchange, controlar o acesso à rede ou integrá-lo a uma solução de defesa contra ameaças móveis.
 
As informações neste artigo podem ajudá-lo a entender como usar os recursos de conformidade do *dispositivo* móvel do Intune e os recursos de MAM (gerenciamento de *aplicativo* móvel) do Intune. 

> [!NOTE]
> O acesso condicional é um recurso Azure Active Directory que é incluído em uma licença Azure Active Directory Premium. O Intune melhora esta funcionalidade ao adicionar à solução a conformidade de dispositivos móveis e a gestão de aplicações móveis. O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*.  

## <a name="device-based-conditional-access"></a>Acesso condicional com base no dispositivo

O Intune e o Azure Active Directory trabalham juntos para garantir que somente dispositivos gerenciados e compatíveis possam acessar email, serviços do Office 365, aplicativos SaaS (software como serviço) e [aplicativos locais](https://docs.microsoft.com/azure/active-directory/active-directory-application-proxy-get-started). Além disso, você pode definir uma política no Azure Active Directory para habilitar apenas computadores ingressados no domínio ou dispositivos móveis registrados no Intune para acessar os serviços do Office 365.

O Intune fornece capacidades de política de conformidade de dispositivos que avaliam o estado de conformidade dos dispositivos. O status de conformidade é relatado para Azure Active Directory que o usa para impor a política de acesso condicional criada em Azure Active Directory quando o usuário tenta acessar os recursos da empresa.

As políticas de acesso condicional com base no dispositivo para o Exchange Online e outros produtos do Office 365 são configuradas por meio do [portal do Azure](https://docs.microsoft.com/intune-azure/introduction/what-is-microsoft-intune).  

- Saiba mais sobre [exigir dispositivos gerenciados com acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices).

- Saiba mais sobre [a conformidade de dispositivos do Intune](device-compliance-get-started.md).

- Saiba mais sobre os [navegadores com suporte com acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/conditional-access/technical-reference#supported-browsers).

> [!NOTE]
> Em dispositivos Android, quando você habilita o acesso baseado em dispositivo para o SharePoint Online ou acesso baseado em navegador ao Exchange Online, os usuários devem habilitar a opção **habilitar acesso do navegador** no dispositivo registrado da seguinte maneira:
> 1. Inicie a aplicação **Portal da Empresa**.
> 2. Aceda à página **Definições** a partir das reticências (…) ou do botão do menu de hardware.
> 3. Prima o botão **Ativar o Acesso ao Browser**. 
> 4. No browser Chrome, termine a sessão no Office 365 e reinicie o Chrome.

### <a name="conditional-access-based-on-network-access-control"></a>Acesso condicional com base no controlo de acesso de rede

O Intune se integra com parceiros como o Cisco ISE, o Aruba Clear Pass e o Citrix Netscaler para fornecer controles de acesso com base no registro do Intune e no estado de conformidade do dispositivo.

Os usuários podem ter acesso permitido ou negado a recursos de VPN ou Wi-Fi corporativos com base em se o dispositivo que está usando é gerenciado e em conformidade com as políticas de conformidade do dispositivo do Intune.

- Saiba mais sobre a [integração de NAC com o Intune](network-access-control-integrate.md).

### <a name="conditional-access-based-on-device-risk"></a>Acesso condicional com base no risco do dispositivo

O Intune em parceria com fornecedores de Defesa Contra Ameaças para Dispositivos Móveis fornece uma solução de segurança para detetar malware, trojans e outras ameaças em dispositivos móveis.

#### <a name="how-the-intune-and-mobile-threat-defense-integration-works"></a>Como funciona a integração da Defesa Contra Ameaças para Dispositivos Móveis com o Intune

Quando os dispositivos móveis têm o agente de defesa contra ameaças móveis instalado, o agente envia mensagens de estado de conformidade de volta ao Intune relatando quando uma ameaça é encontrada no próprio dispositivo móvel.

A integração do Intune e da defesa contra ameaças móveis exerce um fator nas decisões de acesso condicional com base no risco do dispositivo.

- Saiba mais sobre a [defesa contra ameaças para dispositivos móveis do Intune](mobile-threat-defense.md).

### <a name="conditional-access-for-windows-pcs"></a>Acesso condicional para PCs Windows

O acesso condicional para PCs fornece funcionalidades semelhantes às que se encontram disponíveis para dispositivos móveis. Vamos falar sobre as formas em que pode utilizar o acesso condicional ao gerir PCs com o Intune.

#### <a name="corporate-owned"></a>Pertencentes à empresa

- **Ingressado no domínio do AD local:** Essa opção é normalmente usada por organizações que são razoavelmente confortáveis com a forma como eles já estão gerenciando seus PCs por meio de políticas de grupo do AD ou Configuration Manager.

- **Azure ad ingressado no domínio e gerenciamento do Intune:** Esse cenário destina-se a organizações que desejam ser a primeira nuvem (ou seja, usam principalmente serviços de nuvem, com um objetivo de reduzir o uso de uma infraestrutura local) ou somente em nuvem (sem infraestrutura local). O ingresso no Azure AD funciona bem em um ambiente híbrido, permitindo o acesso a aplicativos e recursos locais e na nuvem. O dispositivo se une ao Azure AD e é registrado no Intune, que pode ser usado como critério de acesso condicional ao acessar recursos corporativos.

#### <a name="bring-your-own-device-byod"></a>Bring your own device (BYOD)

- **Associação à área de trabalho e gestão do Intune:** aqui, o utilizador pode associar os seus dispositivos pessoais para aceder a serviços e recursos da empresa. Você pode usar o ingresso no local de trabalho e registrar dispositivos no MDM do Intune para receber políticas no nível do dispositivo, que são outra opção para avaliar critérios de acesso condicional.

Saiba mais sobre o [Gerenciamento de dispositivos no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/devices/overview).

## <a name="app-based-conditional-access"></a>Acesso condicional com base nas aplicações

O Intune e o Azure Active Directory funcionam em conjunto para garantir que apenas aplicações geridas podem aceder ao e-mail empresarial ou a outros serviços do Office 365.

- Saiba mais sobre o [acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md).

### <a name="intune-conditional-access-for-exchange-on-premises"></a>Acesso condicional do Intune para o Exchange local

O acesso condicional pode servir para permitir ou bloquear o acesso ao **Exchange no local** com base nas políticas de conformidade de dispositivos e no estado de inscrição. Quando o acesso condicional é utilizado em combinação com uma política de conformidade de dispositivos, apenas os dispositivos compatíveis têm permissão para aceder ao Exchange no local.

Pode configurar definições avançadas no acesso condicional para um controlo mais granular, tais como:

- Permitir ou bloquear determinadas plataformas.

- Bloquear imediatamente os dispositivos que não são gerenciados pelo Intune.

Qualquer dispositivo utilizado para aceder ao Exchange no local é verificado quanto à conformidade quando a conformidade do dispositivo e as políticas de acesso condicional são aplicadas.

Quando os dispositivos não atendem às condições definidas, o usuário final é guiado pelo processo de registro do dispositivo para corrigir o problema que está tornando o dispositivo não compatível.

#### <a name="how-conditional-access-for-exchange-on-premises-works"></a>Como o acesso condicional funciona para o Exchange no local

O acesso condicional para o Exchange local funciona de maneira diferente das políticas baseadas no acesso condicional do Azure. Você instala o conector do Exchange local do Intune para interagir diretamente com o Exchange Server. O conector do Intune Exchange solicita todos os registos do Exchange Active Sync (EAS) que existem no servidor do Exchange para que o Intune possa ter em conta esses registos EAS e mapeá-los para registos de dispositivo do Intune. Esses registos são dispositivos inscritos e reconhecido pelo Intune. Este processo permite ou bloqueia o acesso do e-mail.

Se o registro de EAS for novo e o Intune não estiver ciente dele, o Intune emitirá um cmdlet (pronunciado "command-let") que instrui o servidor Exchange a bloquear o acesso ao email. Veja a seguir mais detalhes sobre como esse processo funciona:

![Fluxograma do Exchange no local com CA](./media/conditional-access-intune-common-ways-use/ca-intune-common-ways-1.png)

1. O utilizador tenta aceder ao e-mail empresarial, que está alojado no Exchange 2010 SP1 ou posterior no local.

2. Se o dispositivo não for gerenciado pelo Intune, o acesso ao email será bloqueado. O Intune envia uma notificação de bloqueio para o cliente EAS.

3. O EAS recebe a notificação de bloco, move o dispositivo para quarentena e envia o email de quarentena com etapas de correção que contêm links para que os usuários possam registrar seus dispositivos.

4. Ocorre o processo de Associação à área de trabalho, que é o primeiro passo para que o dispositivo seja gerido pelo Intune.

5. O dispositivo é inscrito no Intune.

6. O Intune mapeia o registo EAS para um registo de dispositivo e guarda o estado de conformidade do dispositivo.

7. O ID de cliente EAS é registado pelo processo de Registo de Dispositivo do Azure AD, que cria uma relação entre o registo de dispositivo do Intune e o ID de cliente EAS.

8. O Registo de Dispositivo do Azure AD guarda as informações de estado do dispositivo.

9. Se o usuário atender às políticas de acesso condicional, o Intune emitirá um cmdlet por meio do Intune Exchange Connector que permite que a caixa de correio seja sincronizada.

10. O servidor do Exchange envia a notificação ao cliente EAS para que o utilizador possa aceder ao e-mail.


#### <a name="whats-the-intune-role"></a>Qual é a função do Intune?

O Intune avalia e gere o estado do dispositivo.

#### <a name="whats-the-exchange-server-role"></a>Qual é a função de servidor do Exchange?

O Exchange Server fornece API e infraestrutura para mover os dispositivos para quarentena.

> [!IMPORTANT]
> Tenha em mente que o usuário que está usando o dispositivo deve ter um perfil de conformidade e a licença do Intune atribuídos a eles para que o dispositivo possa ser avaliado quanto à conformidade. Se não estiver implementada nenhuma política de conformidade para o utilizador, o dispositivo será tratado como compatível e não serão aplicadas restrições de acesso.

## <a name="next-steps"></a>Próximos passos

[Como configurar o acesso condicional no Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)

[Configurar políticas de acesso condicional com base no aplicativo](app-based-conditional-access-intune-create.md)

[Como instalar o conector do Exchange no local com o Intune](exchange-connector-install.md).

[Como criar uma política de acesso condicional para o Exchange local](conditional-access-exchange-create.md)
