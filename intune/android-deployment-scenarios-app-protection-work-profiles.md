---
title: Proteção políticas e de trabalho de perfis de aplicações no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver as diferenças e prós e contras ao decidir utilizar as políticas de proteção de aplicações ou trabalhar perfis para pessoal ou de dispositivos empresariais Android de BYOD no Microsoft Intune. Comparar as diferenças e os recursos que obtém com políticas de proteção de aplicações sem inscrição (aplicação-PODEMOS) e o Android Enterprise perfis de trabalho.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/13/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: chrisbal
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: fbdd89e6d26042258cd4c5a3d93cfdb68d73756d
ms.sourcegitcommit: 5708ec1d7ae50494be44ed5064f150b636188c84
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/13/2019
ms.locfileid: "56240117"
---
# <a name="application-protection-policies-and-work-profiles-on-android-enterprise-devices-in-intune"></a>Proteção políticas e de trabalho de perfis de aplicação em dispositivos Android Enterprise no Intune

Em muitas organizações, os administradores são desafiados a proteger os dados em diferentes dispositivos e recursos. Um desafio é proteger os recursos para os utilizadores com dispositivos de empresa Android pessoais, também conhecido como bring-your-own device (BYOD). O Microsoft Intune suporta dois cenários de implementação do Android para bring-your-own device (BYOD):

- Políticas de proteção de aplicações sem inscrição (aplicação-nós)
- Perfis de trabalho do Android Enterprise

A aplicação-nós e os cenários de implementação do perfil de trabalho Android incluem os seguintes principais recursos importantes para ambientes de BYOD:

1. **Proteção e segregação de dados geridos pelo organização**: Ambas as soluções de proteger os dados de organização através da imposição de controlos de prevenção (DLP) de perda de dados em dados geridos de organização. Estas proteções impedem fugas acidentais de dados protegidos, como um utilizador final acidentalmente partilhando-a para uma conta ou aplicações pessoais. Também podem ser utilizados para se certificar de que um dispositivo de acesso aos dados está em bom estado e não comprometidos.

2. **Privacidade do utilizador final**: Aplicações-PODEMOS e perfis de trabalho do Android Enterprise separam o conteúdo dos utilizadores finais no dispositivo e os dados geridos pela gestão de dispositivos móveis administrador (MDM). Em ambos os cenários, os administradores de TI impõem políticas, como autenticação apenas com PIN em aplicações geridas por organização ou de identidades. Os administradores de TI não conseguem ler, aceder a ou apagar os dados que pertencentes ou controladas pelos usuários finais.

Se escolher aplicação-PODEMOS ou perfis de trabalho do Android Enterprise para a implementação de BYOD depende de seus requisitos e as empresas precisam. O objetivo deste artigo é fornecer orientações para ajudar a decidir.

## <a name="about-intune-app-protection-policies"></a>Sobre as políticas de proteção de aplicações do Intune

Políticas de proteção de aplicações do Intune (aplicação) são visadas para utilizadores de políticas de proteção de dados. As políticas se aplicam a proteção de perda de dados ao nível da aplicação. Aplicação do Intune requer que os desenvolvedores de aplicativos ativar funcionalidades de aplicações nas aplicações que criaram.

Aplicações Android individuais são habilitadas para a aplicação de diversas formas:

1. **Integrado em aplicações originais da Microsoft de forma nativa**: Aplicações do Microsoft Office para Android e uma seleção de outras aplicações da Microsoft, são fornecidos com incorporado da aplicação Intune. Estas aplicações do Office, como o Word, OneDrive, Outlook etc., não é necessário qualquer personalização mais para aplicar políticas. Estas aplicações podem ser instaladas pelos utilizadores finais diretamente a partir do Google Play Store.

2. **Integrado em compilações de aplicação pelos desenvolvedores que usam o SDK do Intune**: Os desenvolvedores de aplicativos podem integrar o SDK do Intune no seu código-fonte e recompilar as suas aplicações para suportar funcionalidades de política de aplicação do Intune.

3. **Encapsuladas com a ferramenta de encapsulamento de aplicações do Intune**: Alguns clientes compilam aplicações Android (. Ficheiro APK) sem acesso ao código-fonte. Sem o código-fonte, o desenvolvedor não é possível integrar com o SDK do Intune. Sem o SDK, eles não é possível ativar a sua aplicação para políticas de aplicações. O desenvolvedor tem de modificar ou recodificar a aplicação para suportar políticas de aplicações.

    Para ajudar, o Intune inclui a **ferramenta de encapsulamento de aplicações** a ferramenta para aplicações Android existentes (APKs) e cria uma aplicação que reconhece as políticas de aplicações.

    Para obter mais informações sobre esta ferramenta, consulte [repare aplicações de linha de negócio para políticas de proteção de aplicações](apps-prepare-mobile-application-management.md).

Para ver uma lista de aplicações ativada com a aplicação, consulte [aplicações com um conjunto avançado de políticas de proteção de aplicações móveis geridas](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

## <a name="deployment-scenarios"></a>Cenários de implementação

Esta secção descreve as características importantes da aplicação-PODEMOS e cenários de implementação de perfil de trabalho de Android Enterprise.

#### <a name="app-we"></a>APP-WE

Uma aplicação-implementação PODEMOS (políticas de proteção de aplicações sem inscrição) define políticas nas aplicações e não a dispositivos. Neste cenário, dispositivos, normalmente, não são inscritos ou geridos por uma autoridade de MDM, como o Intune. Para proteger o acesso aos dados organizacionais e de aplicações, os administradores utilizem aplicações gerenciável para a aplicação em aplicam políticas de proteção de dados para estas aplicações.

Esta funcionalidade aplica-se a:

- Android 4.4 e posterior

> [!TIP]
> Para obter mais informações, consulte [quais são as políticas de proteção de aplicações?](app-protection-policy.md).

Aplicações-cenários são para os utilizadores finais que quer um reduzidos organizacional nos respetivos dispositivos e não quer a inscrição na MDM. Como administrador, ainda precisa proteger os seus dados. Estes dispositivos não são geridos. Tarefas MDM tão comum e de recursos, como Wi-Fi, o dispositivo VPN e gestão de certificados, não fazem parte deste cenário de implementação.

#### <a name="android-enterprise-work-profiles"></a>Perfis de trabalho do Android Enterprise

Perfis de trabalho são o cenário de implementação do Android Enterprise core e o único cenário destinado a BYOD casos de utilização. O perfil de trabalho é uma partição separada, criada no nível do SO Android que pode ser gerido pelo Intune.

Esta funcionalidade aplica-se a:

- Dispositivos de Android 5.0 e posteriores com os serviços móveis Google

Um perfil de trabalho inclui as seguintes funcionalidades:

- **Funcionalidades MDM tradicionais**: Capacidades de MDM de chave, como gestão de ciclo de vida de aplicações com o Google Play gerido, está disponível em qualquer cenário de Android Enterprise. Google Play gerido fornece uma experiência robusta para instalar e atualizar as aplicações sem qualquer intervenção do utilizador. IT pode também enviar por push as definições de configuração de aplicação para aplicações organizacionais. Ele também não requer que os utilizadores finais permitir instalações de origens desconhecidas. Outras atividades MDM comuns, como a implementação de certificados, Wi-Fi/VPNs de configuração e definição de códigos de acesso do dispositivo estão disponíveis com perfis de trabalho.

- **DLP nos limites do perfil de trabalho**: Como o APP-WE, IT pode impor políticas de proteção de dados. Com um perfil de trabalho, as políticas DLP são impostas no nível de perfil de trabalho, não no nível da aplicação. Por exemplo, a proteção de copiar/colar é imposta pelas definições de aplicações aplicadas a uma aplicação ou imposto pelo perfil de trabalho. Quando a aplicação é implementada para um perfil de trabalho, os administradores podem interromper a proteção de copiar/colar para o perfil de trabalho ao desativar esta política ao nível da aplicação.

## <a name="tips-to-optimize-the-work-profile-experience"></a>Experiência de dicas para otimizar o perfil de trabalho

### <a name="when-to-use-app-within-work-profiles"></a>Quando utilizar a aplicação dentro de perfis de trabalho

Os perfis de aplicação do Intune e de trabalho são tecnologias complementares que podem ser utilizadas em conjunto ou separadamente. Em termos de arquitetura, as duas soluções impõem políticas em camadas diferentes – a aplicação na camada de aplicações individuais e perfil de trabalho na camada de perfil. Implementar aplicações geridas com a política de uma aplicação no perfil de trabalho é um cenário válido e suportado. Para utilizar a aplicação, perfis de trabalho ou uma combinação depende dos requisitos de DLP.

Perfis de trabalho e aplicações complementam as definições do outro, fornecendo cobertura adicional, se um perfil não cumprir os requisitos de proteção de dados da sua organização. Por exemplo, perfis de trabalho nativamente não fornecem controlos para impedir uma aplicação de poupança para uma localização de armazenamento na cloud não fidedigno. Aplicação inclui esta funcionalidade. Pode decidir que DLP fornecido exclusivamente pelo perfil de trabalho é suficiente e optar por não utilizar a aplicação. Ou talvez seja necessário as proteções de uma combinação dos dois.

### <a name="suppress-app-policy-for-work-profiles"></a>Suprimir a política de aplicações para perfis de trabalho

Poderá ter de oferecer suporte a usuários individuais que têm vários dispositivos - dispositivos não geridos numa aplicação-cenário de nós e os dispositivos geridos com perfis de trabalho. 

Por exemplo, exigir que os utilizadores finais introduzam um PIN ao abrir uma aplicação de trabalho. Dependendo do dispositivo, as funcionalidades PIN são processadas pela aplicação ou ao perfil de trabalho. Para a aplicação-, dispositivos, o comportamento de PIN para lançamento é imposta pela aplicação. Para dispositivos de perfil de trabalho, pode utilizar um dispositivo ou PIN imposta pelo sistema operacional de perfil de trabalho. Para concluir este cenário, a configurar as definições da aplicação, para que eles não se aplicam *quando* uma aplicação for implementada para um perfil de trabalho. Se não configurar desta forma, o usuário final obtém pedido um PIN ao dispositivo e novamente ao nível da aplicação.

### <a name="control-multi-identity-behavior-in-work-profiles"></a>Controlar o comportamento de várias identidades em perfis de trabalho

Aplicações do Office, como o Outlook e o OneDrive, tem o comportamento de "várias identidade". Dentro de uma instância do aplicativo, o utilizador final pode adicionar ligações a várias contas distintas ou localizações de armazenamento da cloud. Dentro do aplicativo, os dados obtidos a partir destas localizações podem ser separados ou intercalado. E, o utilizador pode alternar o contexto entre identidades pessoais (user@outlook.com) e identidades de organização (user@contoso.com).

Ao utilizar perfis de trabalho, pode querer desativar esse comportamento de várias identidades. Quando desabilitá-la, distintivas instâncias da aplicação no perfil de trabalho só podem ser configuradas com uma identidade da organização. Utilize a definição de configuração de aplicação de contas permitidas para suportar as aplicações Android do Office.

Para obter mais informações, consulte [implementar o Outlook para iOS e as definições de configuração de aplicação Android](https://docs.microsoft.com/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-configuration-with-microsoft-intune).

## <a name="when-to-use-intune-app"></a>Quando utilizar a aplicação do Intune

Existem vários cenários de mobilidade empresarial em que a utilização de aplicações do Intune é a melhor recomendação.

#### <a name="older-devices-running-android-44-51-are-being-used"></a>Estão a ser utilizados dispositivos mais antigos que executam o Android 4.4-5.1

Oficialmente, qualquer dispositivo Android 5.0 ou posterior com os serviços do Google móveis suporta perfis de trabalho e é elegível para ser gerido dessa forma. No entanto, alguns Android 5.0 e 5.1 dispositivos a partir de alguns OEMs não suportam perfis de trabalho.

Se utilizar versões que não suportam perfis de trabalho, e para garantir a DLP para dados da organização nos dispositivos, tem de utilizar funcionalidades da aplicação do Intune.

#### <a name="no-mdm-no-enrollment-google-services-are-unavailable"></a>Sem MDM, sem inscrição, não estão disponíveis serviços do Google

Alguns clientes não querem a qualquer outra forma de gestão de dispositivos, incluindo gestão de perfis de trabalho, por motivos diferentes:

- Motivos legais e responsabilidade
- Para manter a consistência da experiência do usuário
- O ambiente de dispositivo Android é altamente heterogêneo
- Não há nenhuma conectividade com serviços do Google, que é necessário para a gestão de perfis de trabalho.

Por exemplo, os clientes na ou têm utilizadores na China não é possível utilizar a gestão de dispositivos Android, uma vez que os serviços do Google são bloqueados. Neste caso, utilize da aplicação Intune para DLP.

## <a name="summary"></a>Resumo

Utilizar o Intune, as duas aplicações-PODEMOS e perfis de trabalho do Android Enterprise estão disponíveis para o seu programa Android BYOD. Para escolher aplicação-PODEMOS ou perfis de trabalho depende dos requisitos de negócios e de utilização. Em resumo, utilize os perfis de trabalho se precisar de atividades MDM em dispositivos geridos, tais como a implementação de certificados push da aplicação e assim por diante. Utilizar a aplicação-que se não quer ou não é possível gerir dispositivos e estiver a utilizar aplicações apenas com o da aplicação Intune.

## <a name="next-steps"></a>Passos Seguintes
[Começar a utilizar as políticas de proteção de aplicações](app-protection-policy.md), ou [inscrever os dispositivos](android-enroll.md).
