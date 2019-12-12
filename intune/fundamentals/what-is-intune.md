---
title: O que é Microsoft Intune-Azure | Microsoft Docs
description: Saiba como Microsoft Intune é o componente MDM (gerenciamento de dispositivo móvel) e MAM (gerenciamento de aplicativo móvel) da solução Enterprise Mobility + Security e como ele ajuda a proteger os dados da empresa.
keywords: o que é o Intune
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/14/2019
ms.topic: overview
ms.service: microsoft-intune
ms.subservice: fundamentals
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 3b4e778d-ac13-4c23-974f-5122f74626bc
ms.reviewer: pmay
ms.suite: ems
search.appverid: MET150
ms.custom: get-started
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3c03c67a99b78804c999250f8d1148a4b3d1d97
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72504760"
---
# <a name="microsoft-intune-is-an-mdm-and-mam-provider-for-your-devices"></a>Microsoft Intune é um provedor de MDM e MAM para seus dispositivos

Microsoft Intune é um serviço baseado em nuvem que se concentra no gerenciamento de dispositivo móvel (MDM) e no gerenciamento de aplicativo móvel (MAM). O Intune está incluído no pacote de Enterprise Mobility + Security da Microsoft [(EMS)](https://www.microsoft.com/microsoft-365/enterprise-mobility-security)e permite que os usuários sejam produtivos enquanto mantêm os dados da sua organização protegidos. Ele se integra a outros serviços, incluindo Microsoft 365 e Azure Active Directory (AD do Azure) para controlar quem tem acesso e o que eles têm acesso e a proteção de informações do Azure para proteção de dados. Ao usá-lo com o Microsoft 365, você pode permitir que sua força de equipe seja produtiva em todos os seus dispositivos, mantendo as informações da sua organização protegidas.

![Imagem da arquitetura do Intune](./media/what-is-intune/intunearch_sm.png)

Veja uma [versão maior](./media/what-is-intune/intunearchitecture.svg) do diagrama da arquitetura do Intune.

Com o Intune, pode:

- Escolha ser 100% Cloud com o Intune ou ser [cogerenciado](https://docs.microsoft.com/sccm/comanage/overview) com o Configuration Manager e o Intune.
- Defina regras e defina configurações em dispositivos pessoais e de propriedade da organização para acessar dados e redes.
- Implantar e autenticar aplicativos em dispositivos-locais e móveis.
- Proteja as informações da empresa controlando a maneira como os usuários acessam e compartilham informações.
- Certifique-se de que os dispositivos e aplicativos estejam em conformidade com seus requisitos de segurança.

## <a name="manage-devices"></a>Efetue a gestão dos dispositivos

No Intune, você gerencia dispositivos usando uma abordagem adequada para você. Para dispositivos de propriedade da organização, talvez você queira controle total sobre os dispositivos, incluindo configurações, recursos e segurança. Nessa abordagem, os dispositivos e os usuários desses dispositivos "registram-se" no Intune. Depois de registrados, eles recebem suas regras e configurações por meio de políticas configuradas no Intune. Por exemplo, você pode definir os requisitos de senha e PIN, criar uma conexão VPN, configurar a proteção contra ameaças e muito mais.

Para dispositivos pessoais ou BYOD (Traga seu próprio dispositivo), os usuários podem não querer que seus administradores de organização tenham controle total. Nessa abordagem, dê aos usuários opções. Por exemplo, os usuários [registram](../enrollment/device-enrollment.md) seus dispositivos se desejam acesso completo aos recursos da sua organização. Ou, se esses usuários só quiserem acessar o email ou o Microsoft Teams, use as políticas de proteção de aplicativo que exigem a autenticação multifator (MFA) para usar esses aplicativos.

Quando os dispositivos são registrados e gerenciados no Intune, os administradores podem:

- Consulte os dispositivos registrados e obtenha um inventário dos dispositivos que acessam os recursos da organização.
- Configure dispositivos para que eles atendam aos seus padrões de segurança e integridade. Por exemplo, você provavelmente desejará bloquear dispositivos com jailbreak.
- Envie certificados por push para dispositivos para que os usuários possam acessar facilmente sua rede Wi-Fi ou usar uma VPN para se conectar à sua rede.
- Consulte relatórios sobre usuários e dispositivos que estão em conformidade e sem conformidade.
- Remova os dados da organização se um dispositivo for perdido, roubado ou não for mais usado.

**Recursos online**:

- [O que é a inscrição de dispositivos?](../enrollment/device-enrollment.md)

- [Aplicar recursos e configurações em seus dispositivos usando perfis de dispositivo](../configuration/device-profiles.md)

- [Proteger dispositivos com o Microsoft Intune](../protect/device-protect.md)

## <a name="manage-apps"></a>Gerir aplicações

O MAM (gerenciamento de aplicativo móvel) no Intune foi projetado para proteger os dados da organização no nível do aplicativo, incluindo aplicativos personalizados e aplicativos da loja. O gerenciamento de aplicativos pode ser usado em dispositivos pessoais e de propriedade da organização.

Quando os aplicativos são gerenciados no Intune, os administradores podem:

- Adicione e atribua aplicativos móveis a grupos de usuários e dispositivos, incluindo usuários em grupos específicos, dispositivos em grupos específicos e muito mais.
- Configure aplicativos para iniciar ou executar com configurações específicas habilitadas e atualize os aplicativos existentes que já estão no dispositivo.
- Veja relatórios sobre quais aplicativos são usados e acompanhe seu uso.
- Faça um apagamento seletivo removendo somente os dados da organização dos aplicativos.

Uma maneira que o Intune fornece segurança de aplicativo móvel é por meio de **[políticas de proteção de aplicativo](../apps/app-protection-policy.md)** . Políticas de proteção do aplicativo:

- Use a identidade do Azure AD para isolar dados da organização de dados pessoais. Portanto, as informações pessoais são isoladas do reconhecimento de ti organizacional. Os dados acessados usando as credenciais da organização recebem proteção de segurança adicional.
- Ajude a proteger o acesso em dispositivos pessoais restringindo ações que os usuários podem executar, como copiar e colar, salvar e exibir.
- Pode ser criado e implantado em dispositivos registrados no Intune, registrados em outro serviço de MDM ou não registrados em nenhum serviço MDM. Em dispositivos registrados, as políticas de proteção de aplicativo podem adicionar uma camada extra de proteção.

Por exemplo, um usuário entra em um dispositivo com suas credenciais de organização. Sua identidade de organização permite o acesso a dados que são negados à sua identidade pessoal. Conforme os dados da organização são usados, as políticas de proteção de aplicativo controlam como os dados são salvos e compartilhados. Quando os usuários entram com sua identidade pessoal, essas mesmas proteções não são aplicadas. Dessa forma, ele tem controle dos dados da organização, enquanto os usuários finais mantêm o controle e a privacidade sobre seus dados pessoais.

E você pode usar o Intune com outros serviços no EMS. Esse recurso fornece segurança de aplicativo móvel da sua organização além do que está incluído no sistema operacional e em qualquer aplicativo. Os aplicativos gerenciados com o EMS têm acesso a um conjunto mais amplo de recursos de proteção de dados e aplicativos móveis.

![Imagem que mostra os níveis da segurança de dados de gestão de aplicações](./media/what-is-intune/managing-mobile-apps.png)

## <a name="compliance-and-conditional-access"></a>Conformidade e acesso condicional

O Intune está integrado no Azure AD para possibilitar um conjunto abrangente de cenários de controlo de acesso. Por exemplo, exigir que os dispositivos móveis estejam em conformidade com os padrões da organização definidos no Intune antes de acessar recursos de rede, como email ou SharePoint. Da mesma forma, você pode bloquear os serviços para que eles fiquem disponíveis apenas para um conjunto específico de aplicativos móveis. Por exemplo, você pode bloquear o Exchange Online para que ele seja acessado somente pelo Outlook ou pelo Outlook Mobile.

**Recursos online**:

- [Definir regras em dispositivos para permitir o acesso aos recursos da sua organização](../protect/device-compliance-get-started.md)

- [Maneiras comuns de usar o acesso condicional com o Intune](../protect/conditional-access-intune-common-ways-use.md)

## <a name="how-to-get-intune"></a>Como obter o Intune

O Intune está disponível:

- Como um [serviço autônomo do Azure](https://go.microsoft.com/fwlink/?linkid=2090973)
- Incluído com [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise-mobility-security/microsoft-intune) e [Microsoft 365 governo](https://www.microsoft.com/microsoft-365/government)
- Como [Gerenciamento de dispositivos móveis no Office 365](https://support.office.com/article/choose-between-mdm-for-office-365-and-microsoft-intune-c93d9ab9-efb2-4349-9b93-30c30562ee22), que consiste em alguns recursos limitados do Intune

O Intune é usado em muitos setores, incluindo [governo](https://docs.microsoft.com/enterprise-mobility-security/solutions/ems-govt-service-description), [educação](https://www.microsoft.com/en-us/education/intune), [quiosque ou dispositivo dedicado](../configuration/kiosk-settings.md) para fabricação e varejo e muito mais.

## <a name="next-steps"></a>Próximos passos

- Leia alguns dos [problemas de negócios comuns que o Intune ajuda a resolver](https://docs.microsoft.com/intune/common-scenarios).
- Comece com uma [avaliação de 30 dias do Intune](free-trial-sign-up.md).
- Planeje sua [migração para o Intune](migration-guide.md).
- Usando sua assinatura ou avaliação gratuita, percorra o [início rápido: criar um perfil de dispositivo de email para IOS](../configuration/quickstart-email-profile.md).
