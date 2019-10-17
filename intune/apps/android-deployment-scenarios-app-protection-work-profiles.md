---
title: Políticas de proteção de aplicativo e perfis de trabalho no Microsoft Intune – Azure | Microsoft Docs
description: Veja as diferenças e os prós e contras ao decidir usar políticas de proteção de aplicativo ou perfis de trabalho para dispositivos BYOD Android Enterprise no Microsoft Intune. Compare as diferenças e os recursos que você obtém com as políticas de proteção de aplicativo sem o registro (APP-WE) e os perfis de trabalho do Android Enterprise.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: a2c71e04cf842fda7b16fb8ad4a05668ccbfaa84
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72507595"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Políticas de proteção de aplicativo e perfis de trabalho em dispositivos Android Enterprise no Intune

Em muitas organizações, os administradores são desafiados a proteger recursos e dados em diferentes dispositivos. Um desafio é proteger os recursos para usuários com dispositivos Android corporativos pessoais, também conhecidos como BYOD (Traga seu próprio dispositivo). O Microsoft Intune dá suporte a dois cenários de implantação do Android para BYOD (Traga seu próprio dispositivo):

- Políticas de proteção de aplicativo sem registro (APP-WE)
- Perfis de trabalho do Android Enterprise

Os cenários de implantação APP-WE e Android de perfil de trabalho incluem os seguintes recursos principais importantes para ambientes BYOD:

1. **Proteção e segregação de dados gerenciados pela organização**: ambas as soluções protegem dados da organização impondo controles de DLP (prevenção contra perda de dados) em dados gerenciados pela organização. Essas proteções impedem vazamentos acidentais de dados protegidos, como um usuário final que o compartilha acidentalmente para um aplicativo ou conta pessoal. Eles também servem para garantir que um dispositivo acessando os dados esteja íntegro e não seja comprometido.

2. **Privacidade do usuário final**: os perfis de trabalho corporativos app-We e Android separam o conteúdo dos usuários finais no dispositivo e os dados gerenciados pelo administrador do MDM (gerenciamento de dispositivo móvel). Em ambos os cenários, os administradores de ti impõem políticas, como a autenticação somente PIN em aplicativos gerenciados pela organização ou identidades. Os administradores de ti não conseguem ler, acessar ou apagar dados pertencentes ou controlados pelos usuários finais.

Se você escolher os perfis de trabalho do APP-WE ou Android Enterprise para sua implantação do BYOD depende de seus requisitos e necessidades de negócios. O objetivo deste artigo é fornecer orientações para ajudá-lo a decidir.

## <a name="about-intune-app-protection-policies"></a>Sobre as políticas de proteção de aplicativo do Intune

As políticas de proteção de aplicativo do Intune (aplicativo) são políticas de proteção de dados direcionadas aos usuários. As políticas aplicam a proteção contra perda de dados no nível do aplicativo. O aplicativo do Intune requer que os desenvolvedores de aplicativos habilitem recursos de aplicativo nos aplicativos que criam.

Os aplicativos Android individuais são habilitados para o aplicativo de algumas maneiras:

1. **Integrado nativamente aos aplicativos primários da Microsoft**: Microsoft Office aplicativos para Android e uma seleção de outros aplicativos da Microsoft, vêm com o aplicativo do Intune interno. Esses aplicativos do Office, como Word, OneDrive, Outlook e assim por diante, não precisam de mais personalização para aplicar políticas. Esses aplicativos podem ser instalados pelos usuários finais diretamente do Google Play Store.

2. **Integrado a compilações de aplicativos por desenvolvedores usando o SDK do Intune**: os desenvolvedores de aplicativos podem integrar o SDK do Intune em seu código-fonte e recompilar seus aplicativos para dar suporte aos recursos de política de aplicativo do Intune.

3. **Encapsulado usando a ferramenta de disposição do aplicativo do Intune**: alguns clientes compilam aplicativos Android (. Arquivo APK) sem acesso ao código-fonte. Sem o código-fonte, o desenvolvedor não pode se integrar ao SDK do Intune. Sem o SDK, eles não podem habilitar seu aplicativo para políticas de aplicativo. O desenvolvedor deve modificar ou recodificar o aplicativo para dar suporte a políticas de aplicativo.

    Para ajudar, o Intune inclui a ferramenta de **ferramenta de encapsulamento de aplicativos** para aplicativos Android existentes (APKs) e cria um aplicativo que reconhece as políticas de aplicativo.

    Para obter mais informações sobre essa ferramenta, consulte [preparar aplicativos de linha de negócios para políticas de proteção de aplicativo](../developer/apps-prepare-mobile-application-management.md).

Para ver uma lista de aplicativos habilitados com o aplicativo, consulte [aplicativos gerenciados com um rico conjunto de políticas de proteção de aplicativo móvel](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="deployment-scenarios"></a>Cenários de implantação

Esta seção descreve as características importantes dos cenários de implantação de perfil de trabalho do APP-WE e Android Enterprise.

### <a name="app-we"></a>APLICATIVO-NÓS

Uma implantação de aplicativo – nós (políticas de proteção de aplicativo sem registro) define políticas em aplicativos, não em dispositivos. Nesse cenário, os dispositivos normalmente não são registrados ou gerenciados por uma autoridade de MDM, como o Intune. Para proteger aplicativos e acesso a dados organizacionais, os administradores usam aplicativos gerenciáveis por aplicativos e aplicam políticas de proteção de dados a esses aplicativos.

Esta funcionalidade aplica-se a:

- Android 4,4 e posterior

> [!TIP]
> Para obter mais informações, consulte [o que são políticas de proteção de aplicativo?](app-protection-policy.md).

Os cenários APP-WE são para usuários finais que desejam uma pequena superfície organizacional em seus dispositivos e não querem se registrar no MDM. Como administrador, você ainda precisa proteger seus dados. Esses dispositivos não são gerenciados. Assim, tarefas e recursos comuns do MDM, como Wi-Fi, VPN de dispositivo e gerenciamento de certificados, não fazem parte desse cenário de implantação.

### <a name="android-enterprise-work-profiles"></a>Perfis de trabalho do Android Enterprise

Os perfis de trabalho são o cenário principal de implantação do Android Enterprise e o único cenário destinado a casos de uso BYOD. O perfil de trabalho é uma partição separada criada no nível do sistema operacional Android que pode ser gerenciada pelo Intune.

Esta funcionalidade aplica-se a:

- Dispositivos Android 5,0 e posteriores com os serviços móveis do Google

Um perfil de trabalho inclui os seguintes recursos:

- **Funcionalidade de MDM tradicional**: os principais recursos do MDM, como o gerenciamento do ciclo de vida do aplicativo usando o Google Play gerenciado, estão disponíveis em qualquer cenário do Android Enterprise. O Google Play gerenciado fornece uma experiência robusta para instalar e atualizar aplicativos sem nenhuma intervenção do usuário. Ele também pode enviar por push definições de configuração de aplicativo para aplicativos organizacionais. Ele também não exige que os usuários finais permitam instalações de fontes desconhecidas. Outras atividades comuns do MDM, como a implantação de certificados, a configuração de Wi-Fi/VPNs, e a definição de senhas de dispositivo estão disponíveis com perfis de trabalho.

- **DLP no limite do perfil de trabalho**: como app-We, ele pode impor políticas de proteção de dados. Com um perfil de trabalho, as políticas de DLP são impostas no nível do perfil de trabalho, não no nível do aplicativo. Por exemplo, a proteção copiar/colar é imposta pelas configurações do aplicativo aplicadas a um aplicativo ou imposta pelo perfil de trabalho. Quando o aplicativo é implantado em um perfil de trabalho, os administradores podem pausar a proteção de copiar/colar no perfil de trabalho desativando essa política no nível do aplicativo.

## <a name="tips-to-optimize-the-work-profile-experience"></a>Dicas para otimizar a experiência do perfil de trabalho

### <a name="when-to-use-app-within-work-profiles"></a>Quando usar o aplicativo em perfis de trabalho

Os perfis de trabalho e de aplicativo do Intune são tecnologias complementares que podem ser usadas juntas ou separadamente. Em termos de arquitetura, ambas as soluções impõem políticas em camadas diferentes – aplicativo na camada de aplicativo individual e perfil de trabalho na camada de perfil. A implantação de aplicativos gerenciados com uma política de aplicativo para um aplicativo em um perfil de trabalho é um cenário válido e com suporte. Para usar o aplicativo, os perfis de trabalho ou uma combinação depende dos seus requisitos de DLP.

Os perfis de trabalho e o aplicativo complementam as configurações de cada um, fornecendo cobertura adicional se um perfil não atender aos requisitos de proteção de dados de sua organização. Por exemplo, os perfis de trabalho não fornecem controles nativamente para impedir que um aplicativo seja salvo em um local de armazenamento de nuvem não confiável. O aplicativo inclui esse recurso. Você pode decidir que a DLP fornecida exclusivamente pelo perfil de trabalho é suficiente e optar por não usar o aplicativo. Ou você pode exigir as proteções de uma combinação das duas.

### <a name="suppress-app-policy-for-work-profiles"></a>Suprimir política de aplicativo para perfis de trabalho

Talvez seja necessário dar suporte a usuários individuais que tenham vários dispositivos – dispositivos não gerenciados em um cenário de aplicativo e dispositivos gerenciados com perfis de trabalho.

Por exemplo, você precisa que os usuários finais insiram um PIN ao abrir um aplicativo de trabalho. Dependendo do dispositivo, os recursos do PIN são tratados pelo aplicativo ou pelo perfil de trabalho. Para os dispositivos APP-WE, o comportamento de PIN para inicialização é imposto pelo aplicativo. Para dispositivos de perfil de trabalho, você pode usar um PIN de dispositivo ou de perfil de trabalho imposto pelo sistema operacional. Para realizar esse cenário, defina as configurações do aplicativo para que elas não se apliquem *quando* um aplicativo for implantado em um perfil de trabalho. Se você não configurá-lo dessa forma, o usuário final receberá uma solicitação para um PIN pelo dispositivo e novamente na camada de aplicativo.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>Controlar o comportamento de várias identidades em perfis de trabalho

Os aplicativos do Office, como o Outlook e o OneDrive, têm comportamento de "várias identidades". Dentro de uma instância do aplicativo, o usuário final pode adicionar conexões a várias contas distintas ou locais de armazenamento em nuvem. Dentro do aplicativo, os dados recuperados desses locais podem ser separados ou mesclados. E, o usuário pode alternar o contexto entre identidades pessoais (user@outlook.com) e identidades de organização (user@contoso.com).

Ao usar perfis de trabalho, talvez você queira desabilitar esse comportamento de várias identidades. Quando você o desabilita, as instâncias com notificação do aplicativo no perfil de trabalho só podem ser configuradas com uma identidade de organização. Use a definição de configuração de aplicativo de contas permitidas para dar suporte a aplicativos Android do Office.

Para obter mais informações, consulte [implantar o Outlook para definições de configuração de aplicativo Android e Ios](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="when-to-use-intune-app"></a>Quando usar o aplicativo do Intune

Há vários cenários de mobilidade corporativa em que o uso do aplicativo do Intune é a melhor recomendação.

### <a name="older-devices-running-android-44-51-are-being-used"></a>Dispositivos mais antigos que executam o Android 4.4-5.1 estão sendo usados

Oficialmente, qualquer dispositivo Android 5,0 ou superior com os serviços móveis do Google dá suporte a perfis de trabalho e está qualificado para ser gerenciado dessa forma. No entanto, alguns dispositivos Android 5,0 e 5,1 de alguns OEMs não dão suporte a perfis de trabalho.

Se estiver usando versões que não dão suporte a perfis de trabalho e para garantir a DLP para dados da organização em dispositivos, você deverá usar os recursos do aplicativo do Intune.

### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>Nenhum MDM, nenhum registro, os serviços do Google não estão disponíveis

Alguns clientes não querem nenhuma forma de gerenciamento de dispositivos, incluindo o gerenciamento de perfil de trabalho, por diferentes motivos:

- Motivos legais e de responsabilidade
- Para a consistência da experiência do usuário
- O ambiente do dispositivo Android é altamente heterogêneo
- Não há nenhuma conectividade com os serviços do Google, que é necessária para o gerenciamento do perfil de trabalho.

Por exemplo, os clientes do ou que têm usuários na China não podem usar o gerenciamento de dispositivos Android, já que os serviços do Google são bloqueados. Nesse caso, use o aplicativo do Intune para DLP.

## <a name="summary"></a>Resumo

Usando o Intune, os perfis de trabalho do APP-WE e do Android Enterprise estão disponíveis para seu programa Android BYOD. Para escolher os perfis de aplicativo ou de trabalho depende de seus requisitos de negócios e de uso. Em resumo, use perfis de trabalho se precisar de atividades MDM em dispositivos gerenciados, como implantação de certificado, push de aplicativo e assim por diante. Usar o aplicativo – se você não quiser ou não puder gerenciar dispositivos e estiver usando somente aplicativos habilitados para aplicativos do Intune.

## <a name="next-steps"></a>Próximos passos
[Comece a usar as políticas de proteção de aplicativo](app-protection-policy.md)ou [Registre seus dispositivos](../enrollment/android-enroll.md).
