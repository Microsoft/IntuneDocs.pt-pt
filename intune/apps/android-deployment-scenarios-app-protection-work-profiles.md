---
title: Políticas de proteção de aplicações e perfis de trabalho no Microsoft Intune - Azure Microsoft Docs
description: Veja as diferenças, prós e contras ao decidir usar políticas de proteção de aplicações ou perfis de trabalho para dispositivos pessoais ou BYOD Android Enterprise no Microsoft Intune. Compare as diferenças e funcionalidades que obtém com as políticas de proteção de aplicações sem inscrições (APP-WE) e perfis de trabalho Android Enterprise.
keywords: ''
author: Erikre
ms.author: erikre
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
ms.openlocfilehash: 99738de7efc473c7886762534c6e377b4dba8397
ms.sourcegitcommit: 51591b862d97904291af7aa53a6eb341b11a761e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415099"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Políticas de proteção de aplicações e perfis de trabalho em dispositivos Android Enterprise em Intune

Em muitas organizações, os administradores são desafiados a proteger recursos e dados em diferentes dispositivos. Um dos desafios é proteger recursos para utilizadores com dispositivos pessoais Android Enterprise, também conhecidos como bring-your-your-device (BYOD). O Microsoft Intune suporta dois cenários de implementação do Android para trazer o seu próprio dispositivo (BYOD):

- Políticas de proteção de aplicações sem inscrição (APP-WE)
- Perfis de trabalho android Enterprise

Os cenários de implementação do perfil de trabalho APP-WE e Android incluem as seguintes funcionalidades-chave importantes para ambientes BYOD:

1. **Proteção e segregação de dados geridos pela organização**: Ambas as soluções protegem os dados da organização através da aplicação de controlos de prevenção de perdas de dados (DLP) sobre dados geridos pela organização. Estas proteções evitam fugas acidentais de dados protegidos, como um utilizador final que os partilha acidentalmente numa aplicação ou conta pessoal. Servem também para garantir que um dispositivo de acesso aos dados é saudável e não comprometido.

2. **Privacidade do utilizador final**: OS perfis de trabalho APP-WE e Android Enterprise separam os conteúdos dos utilizadores finais do dispositivo e os dados geridos pelo administrador de gestão de dispositivos móveis (MDM). Em ambos os cenários, os administradores de TI aplicam políticas, como a autenticação apenas pin em aplicações ou identidades geridas pela organização. Os administradores de TI não conseguem ler, aceder ou apagar dados que sejam propriedade ou controlados pelos utilizadores finais.

Quer escolha perfis de trabalho APP-WE ou Android Enterprise para a sua implementação BYOD depende dos seus requisitos e necessidades de negócio. O objetivo deste artigo é fornecer orientação para ajudá-lo a decidir.

## <a name="about-intune-app-protection-policies"></a>Sobre as políticas de proteção de aplicações Intune

As políticas de proteção de aplicações intune (APP) são políticas de proteção de dados direcionadas aos utilizadores. As políticas aplicam a proteção de perda de dados ao nível da aplicação. A Intune APP requer que os desenvolvedores de aplicações permitam funcionalidades de APP nas aplicações que criam.

As aplicações individuais do Android estão ativadas para APP de várias formas:

1. **Integradas de forma nativa em aplicações de primeira parte**da Microsoft : Aplicações do Microsoft Office para Android, e uma seleção de outras aplicações da Microsoft, vêm com intune APP incorporado. Estas aplicações do Office, como word, OneDrive, Outlook, e assim por diante, não precisam de mais personalização para aplicar políticas. Estas aplicações podem ser instaladas por utilizadores finais diretamente da Google Play Store.

2. **Integrados em apps construídas por desenvolvedores que utilizam o Intune SDK**: Os desenvolvedores de aplicações podem integrar o Intune SDK no seu código fonte e recompilar as suas aplicações para suportar as funcionalidades da política intune APP.

3. Embrulhado sem ferramenta de embrulho de **aplicativos Intune**: Alguns clientes compilam aplicações Android (. Ficheiro APK) sem acesso ao código fonte. Sem o código fonte, o desenvolvedor não pode integrar-se com o Intune SDK. Sem o SDK, não conseguem ativar a sua aplicação para políticas de APP. O desenvolvedor deve modificar ou recodificar a aplicação para apoiar as políticas de APP.

    Para ajudar, intune inclui a ferramenta app **Wrapping Tool** para aplicações Android existentes (APKs), e cria uma app que reconhece as políticas de APP.

    Para obter mais informações sobre esta ferramenta, [consulte a preparação de aplicações de linha de negócio para políticas de proteção de aplicações.](../developer/apps-prepare-mobile-application-management.md)

Para ver uma lista de aplicações ativadas com APP, consulte [aplicações geridas com um conjunto rico de políticas de proteção de aplicações móveis.](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)

## <a name="deployment-scenarios"></a>Cenários de implantação

Esta secção descreve as características importantes dos cenários de implementação do perfil de trabalho APP-WE e Android Enterprise.

### <a name="app-we"></a>APP-WE

Uma implementação app-WE (políticas de proteção de aplicações sem inscrição) define políticas em apps, não em dispositivos. Neste cenário, os dispositivos normalmente não são matriculados ou geridos por uma autoridade de MDM, como o Intune. Para proteger aplicações e acesso a dados organizacionais, os administradores usam aplicações geríveis por APP e aplicam políticas de proteção de dados a estas aplicações.

Esta funcionalidade aplica-se a:

- Android 4.4 e mais tarde

> [!TIP]
> Para mais informações, consulte as políticas de proteção de [aplicações?](app-protection-policy.md)

Os cenários APP-WE são para utilizadores finais que querem uma pequena pegada organizacional nos seus dispositivos, e não querem inscrever-se no MDM. Como administrador, ainda precisa de proteger os seus dados. Estes dispositivos não são geridos. Assim, tarefas e funcionalidades comuns do MDM, tais como WiFi, dispositivo VPN e gestão de certificados, não fazem parte deste cenário de implementação.

### <a name="android-enterprise-work-profiles"></a>Perfis de trabalho android Enterprise

Os perfis de trabalho são o cenário de implementação do Android Enterprise e o único cenário direcionado para casos de utilização byod. O perfil de trabalho é uma partição separada criada ao nível do Sistema Operativo Android que pode ser gerida pela Intune.

Esta funcionalidade aplica-se a:

- Android 5.0 e dispositivos posteriores com Serviços Móveis google

Um perfil de trabalho inclui as seguintes funcionalidades:

- **Funcionalidade tradicional do MDM**: As principais capacidades de MDM, como a gestão do ciclo de vida de aplicações utilizando o Google Play gerido, estão disponíveis em qualquer cenário Android Enterprise. O Google Play gerido proporciona uma experiência robusta para instalar e atualizar apps sem qualquer intervenção do utilizador. O IT também pode empurrar as definições de configuração de aplicativos para aplicações organizacionais. Também não requer que os utilizadores finais permitam instalações de fontes desconhecidas. Outras atividades comuns do MDM, tais como a implementação de certificados, configuração wi-fi/VPNs e definição de códigos de acesso do dispositivo estão disponíveis com perfis de trabalho.

- **DLP sobre a fronteira do perfil de trabalho**: Como APP-WE, TI pode impor políticas de proteção de dados. Com um perfil de trabalho, as políticas de DLP são aplicadas ao nível do perfil de trabalho, não ao nível da aplicação. Por exemplo, a proteção de cópia/pasta é executada pelas definições da APP aplicadas a uma aplicação ou executadas pelo perfil de trabalho. Quando a aplicação é implantada num perfil de trabalho, os administradores podem interromper a proteção de cópia/pasta para o perfil de trabalho desligando esta política ao nível da APP.

## <a name="tips-to-optimize-the-work-profile-experience"></a>Dicas para otimizar a experiência do perfil de trabalho

### <a name="when-to-use-app-within-work-profiles"></a>Quando utilizar a APP dentro dos perfis de trabalho

App intoninizada e perfis de trabalho são tecnologias complementares que podem ser usadas em conjunto ou separadamente. Em termos arquitetónicos, ambas as soluções aplicam políticas em diferentes camadas – APP na camada de aplicação individual, e perfil de trabalho na camada de perfil. Implementar aplicações geridas com uma política de APP para uma aplicação num perfil de trabalho é um cenário válido e suportado. Para utilizar APP, perfis de trabalho ou uma combinação depende dos seus requisitos dLP.

Os perfis de trabalho e a APP complementam as definições uns dos outros, fornecendo cobertura adicional se um dos perfis não cumprir os requisitos de proteção de dados da sua organização. Por exemplo, os perfis de trabalho não fornecem controlos nativos para restringir uma aplicação de poupar para um local de armazenamento de nuvem não confiável. A APP inclui esta funcionalidade. Pode decidir que o DLP fornecido unicamente pelo perfil de trabalho é suficiente e optar por não utilizar a APP. Ou pode exigir as proteções de uma combinação dos dois.

### <a name="suppress-app-policy-for-work-profiles"></a>Suprimir a política de APP para perfis de trabalho

Pode ser necessário suportar utilizadores individuais que tenham vários dispositivos - dispositivos não geridos num cenário APP-WE e dispositivos geridos com perfis de trabalho.

Por exemplo, é necessário que os utilizadores finais introduzam um PIN ao abrir uma aplicação de trabalho. Dependendo do dispositivo, as funcionalidades PIN são manuseadas por APP ou pelo perfil de trabalho. Para os dispositivos APP-WE, o comportamento PIN-to-launch é aplicado pela APP. Para dispositivos de perfil de trabalho, pode utilizar um PIN de dispositivo ou perfil de trabalho imposto pelo OS. Para concretizar este cenário, configure as definições de APP para que não se *apliquem quando* uma aplicação é implementada num perfil de trabalho. Se não configurar desta forma, o utilizador final é solicitado para um PIN pelo dispositivo e novamente na camada APP.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>Controlar o comportamento multi-identidade nos perfis de trabalho

As aplicações de escritório, como o Outlook e o OneDrive, têm um comportamento "multi-identidade". Dentro de um caso da aplicação, o utilizador final pode adicionar ligações a múltiplas contas distintas ou locais de armazenamento em nuvem. Dentro da aplicação, os dados recolhidos destes locais podem ser separados ou fundidos. E, o utilizador pode contextualizar o alterndar entre identidades pessoais (user@outlook.com) e identidades de organização (user@contoso.com).

Ao utilizar perfis de trabalho, pode querer desativar este comportamento multi-identidade. Quando a desativa, as instâncias insígnias da app no perfil de trabalho só podem ser configuradas com uma identidade de organização. Utilize a configuração de configuração de aplicativos Contas Permitidas para apoiar aplicações Android do Office.

Para mais informações, consulte [o outlook de implementação para configurações de configurações de aplicações iOS/iPadOS e Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="when-to-use-intune-app"></a>Quando utilizar a APP Intune

Existem vários cenários de mobilidade empresarial onde a utilização da INTune APP é a melhor recomendação.

### <a name="older-devices-running-android-44-51-are-being-used"></a>Dispositivos mais antigos com android 4.4-5.1 estão a ser usados

Oficialmente, qualquer dispositivo Android 5.0 ou superior com o Google Mobile Services suporta perfis de trabalho, e é elegível para ser gerido dessa forma. No entanto, alguns dispositivos Android 5.0 e 5.1 de alguns OEMs não suportam perfis de trabalho.

Se utilizar versões que não suportem perfis de trabalho e para garantir o DLP para os dados da organização nos dispositivos, deve utilizar as funcionalidades da APP Intune.

### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>Sem MDM, sem matrícula, os serviços do Google estão indisponíveis

Alguns clientes não querem qualquer forma de gestão de dispositivos, incluindo a gestão do perfil de trabalho, por diferentes razões:

- Razões legais e de responsabilidade
- Para a consistência da experiência do utilizador
- O ambiente do dispositivo Android é altamente heterogéneo
- Não existe qualquer conectividade com os serviços da Google, o que é necessário para a gestão do perfil de trabalho.

Por exemplo, os clientes em ou com utilizadores na China não podem usar a gestão de dispositivos Android uma vez que os serviços da Google estão bloqueados. Neste caso, utilize a Intune APP para DLP.

## <a name="summary"></a>Resumo

Utilizando o Intune, tanto os perfis de trabalho APP-WE como Android Enterprise estão disponíveis para o seu programa Android BYOD. Para escolher APP-WE ou perfis de trabalho depende dos seus requisitos de negócio e de utilização. Em resumo, utilize perfis de trabalho se precisar de atividades de MDM em dispositivos geridos, tais como implementação de certificados, impulso de aplicação, e assim por diante. Utilize APP-WE se não quiser ou não consegue gerir dispositivos, e estiver a utilizar apenas aplicações ativadas por APP.

## <a name="next-steps"></a>Próximos passos
[Comece a utilizar políticas de proteção de aplicações,](app-protection-policy.md)ou [inscreva os seus dispositivos.](../enrollment/android-enroll.md)
