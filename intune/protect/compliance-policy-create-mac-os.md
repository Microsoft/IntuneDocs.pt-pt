---
title: Definições de conformidade de dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições que pode utilizar quando define a conformidade para os seus dispositivos macOS no Microsoft Intune. Exija a proteção de integridade do sistema da Apple, defina as restrições de palavra-passe, exija uma firewall, permita o controlador de chamadas e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: cada774003f73f487f87ed8051115dfcaaae6a20
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502484"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do macOS para marcar dispositivos como conformes ou não conformes com o Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos macOS no Intune. Como parte da sua solução de gestão de dispositivos móveis (MDM), utilize estas definições para definir uma versão mínima e máxima do SO, definir a data de expiração de palavras-passe e muito mais.

Esta funcionalidade aplica-se a:

- macOS

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **macOS**.

## <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Exigir uma proteção de integridade do sistema**: **exigir** que seus dispositivos MacOS tenham proteção de [integridade do sistema](https://support.apple.com/HT204899) (abre o site da Apple) habilitado. Quando define como **Não configurada** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

## <a name="device-properties"></a>Propriedades do dispositivo

- **Versão do SO mínima**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não estando em conformidade. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão do SO máxima**: quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. O usuário é solicitado a entrar em contato com o administrador de ti. Até que haja uma alteração de regra para permitir a versão do sistema operacional, esse dispositivo não poderá acessar os recursos da empresa.
- **Versão mínima de Build do so**: quando a Apple publica atualizações de segurança, o número de Build é normalmente atualizado, não a versão do sistema operacional. Utilize esta funcionalidade para introduzir um número mínimo de compilação permitido no dispositivo.
- **Versão máxima de Build do so**: quando a Apple publica atualizações de segurança, o número de Build é normalmente atualizado, não a versão do sistema operacional. Utilize esta funcionalidade para introduzir um número máximo de compilação permitido no dispositivo.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exige** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos.
- **Palavras-passe simples**: defina como **Bloquear** para que os utilizadores não possam criar palavras-passe simples, como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Tipo de palavra-passe**: escolha se uma palavra-passe deve ter apenas carateres **Numéricos** ou se deve existir uma combinação de números e de outros carateres (**Alfanuméricos**).
- **Número de caracteres não alfanuméricos na senha**: Insira o número mínimo de caracteres especiais, como `&`, `#`, `%`, `!` e assim por diante, que deve estar na senha.

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)** : selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Número de senhas anteriores para evitar a reutilização**: Insira o número de senhas usadas anteriormente que não podem ser usadas.

    > [!IMPORTANT]
    > As alterações ao requisito de palavra-passe num dispositivo macOS só têm efeito na próxima alteração de palavra-passe do utilizador. Por exemplo, se definir uma restrição de comprimento da palavra-passe para oito dígitos e o dispositivo macOS tiver atualmente uma palavra-passe de seis dígitos, o mesmo permanecerá em conformidade até à próxima vez que o utilizador atualizar a palavra-passe no dispositivo.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo**: escolha **Exigir** a encriptação do armazenamento de dados nos dispositivos.

### <a name="device-security"></a>Segurança do Dispositivo

A firewall protege os dispositivos contra o acesso não autorizado à rede. Pode utilizar a firewall para controlar as ligações por aplicação. 

- **Firewall**: selecione **habilitar** para ajudar a proteger dispositivos contra acesso não autorizado. Ativar esta funcionalidade permite-lhe processar as ligações recebidas da Internet e utilizar o modo furtivo. A opção **Não configurada** (predefinição) deixa a firewall desativada e permite o tráfego de rede (não bloqueado).
- **Conexões de entrada**: **bloqueie** todas as conexões de rede de entrada, exceto as conexões necessárias para os serviços de Internet básicos, como DHCP, Bonjour e IPsec. Esta definição também bloqueia todos os serviços de partilha, incluindo a partilha de ecrã, o acesso remoto, a partilha de música do iTunes, entre outros. A opção **Não configurado** (predefinição) permite ligações de entrada e a partilha de serviços.
- **Modo furtivo**: **habilite** o modo furtivo para impedir que os dispositivos respondam às solicitações de investigação, que podem ser transformadas por meus usuários mal-intencionados. Quando ativado, o dispositivo continua a responder a pedidos recebidos de aplicações autorizadas. A opção **Não configurado** (predefinição) deixa o modo furtivo desativado.

### <a name="gatekeeper"></a>Controlador de chamadas

Para obter mais informações, veja [Controlador de chamadas no macOS](https://support.apple.com/HT202491) (abre o site da Apple).

**Permitir aplicações transferidas a partir destas localizações**: permite a instalação de aplicações suportadas nos seus dispositivos a partir de diferentes localizações. As suas opções de localização:

- **Não configurado**: predefinição. A opção do controlador de chamadas não tem impacto na conformidade ou não conformidade. 
- **Mac App Store**: instalar apenas aplicações da Mac App Store. Não é possível instalar aplicações de terceiros nem de programadores identificados. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não sejam da Mac App Store, o dispositivo será considerado não conforme.
- **Mac App Store e programadores identificados**: instalar aplicações da Mac App Store e programadores identificados. O macOS verifica a identidade dos programadores e faz outras verificações para confirmar a integridade da aplicação. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não estejam abrangidas por estas opções, o dispositivo será considerado não conforme.
- **Em qualquer lado**: as aplicações podem ser instaladas a partir de qualquer localização e por qualquer programador. Esta é a opção menos segura.

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos iOS](compliance-policy-create-ios.md).