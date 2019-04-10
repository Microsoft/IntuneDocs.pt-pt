---
title: definições de conformidade do dispositivo macOS no Microsoft Intune – Azure | Documentos da Microsoft
description: Ver uma lista de todas as definições que pode utilizar quando a definição de conformidade para os seus dispositivos macOS no Microsoft Intune. Exigir proteção de integridade do sistema da Apple, definir restrições de palavra-passe, necessitam de uma firewall, permitir que o controlador de chamadas e muito mais.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 04/04/2019
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b3224e7400ad56f971488aba53bb073a0d33bb9d
ms.sourcegitcommit: 02803863eba37ecf3d8823a7f1cd7c4f8e3bb42c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59423650"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>definições do macOS para marcar dispositivos como compatíveis ou não compatíveis com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos macOS no Intune. Como parte da sua solução de gestão (MDM) de dispositivos móveis, utilize estas definições para definir o mínimo ou máximo SO versão, conjunto de palavras-passe expirar e muito mais.

Esta funcionalidade aplica-se a:

- macOS

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger recursos da sua organização. Para saber mais sobre as políticas de conformidade e o que fazer, consulte [introdução à conformidade de dispositivo](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **macOS**.

## <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Exigir uma proteção de integridade do sistema**: **Exigir** seus dispositivos macOS tenham [proteção da integridade do sistema](https://support.apple.com/HT204899) (abre o site da Apple) ativado. Quando definido como **não configurado** (predefinição), esta definição não é avaliada de conformidade ou de não conformidade.

## <a name="device-properties"></a>Propriedades do dispositivo

- **Versão mínima do SO**: Quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão do SO máxima**: Quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não poderá aceder aos recursos da empresa.
- **Versão de compilação de SO mínimo**: Quando a Apple publica atualizações de segurança, o número de compilação, normalmente, é atualizado, não a versão do SO. Utilize esta funcionalidade para inserir um número de compilação permitido mínimo no dispositivo.
- **Versão de compilação do SO máximo**: Quando a Apple publica atualizações de segurança, o número de compilação, normalmente, é atualizado, não a versão do SO. Utilize esta funcionalidade para inserir um número de compilação permitido máximo no dispositivo.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: **Exigir** que os utilizadores introduzam uma palavra-passe antes de poderem aceder ao respetivo dispositivo.
- **Palavras-passe simples**: Defina como **bloco** para que os utilizadores não é possível criar palavras-passe simples, tal como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Tipo de palavra-passe**: Escolha se uma palavra-passe deve ter apenas **numérico** carateres, ou se deve existir uma combinação de números e outros carateres (**alfanumérico**).
- **Número de carateres não alfanuméricos na palavra-passe**: Introduza o número mínimo de carateres especiais, como `&`, `#`, `%`, `!`e assim por diante, que tem de ser a palavra-passe.

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Máximo de minutos de inatividade antes da palavra-passe é necessária**: Introduza o tempo de inatividade antes do utilizador ter de reintroduzir a palavra-passe.
- **Expiração de palavra-passe (dias)**: Selecione o número de dias antes da palavra-passe expirar e ser necessário criar um novo.
- **Número de palavras-passe anteriores cuja reutilização está**: Introduza o número de palavras-passe utilizadas anteriormente que não pode ser utilizado.

    > [!IMPORTANT]
    > As alterações ao requisito de palavra-passe num dispositivo macOS só têm efeito na próxima alteração de palavra-passe do utilizador. Por exemplo, se definir uma restrição de comprimento da palavra-passe para oito dígitos e o dispositivo macOS tiver atualmente uma palavra-passe de seis dígitos, o mesmo permanecerá em conformidade até à próxima vez que o utilizador atualizar a palavra-passe no dispositivo.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo de**: Escolher **requerem** para encriptar o armazenamento de dados nos seus dispositivos.

### <a name="device-security"></a>Segurança do Dispositivo

A firewall protege os dispositivos contra o acesso não autorizado à rede. Pode utilizar a firewall para controlar as ligações por aplicação. 

- **Firewall**: Selecione **ativar** para ajudar a proteger os dispositivos contra acesso não autorizado. Ativar esta funcionalidade permite-lhe processar as ligações recebidas da Internet e utilizar o modo furtivo. A opção **Não configurada** (predefinição) deixa a firewall desativada e permite o tráfego de rede (não bloqueado).
- **Ligações de entrada**: **Bloco** todas as ligações de rede recebidas, exceto as ligações necessárias para serviços básicos de internet, como DHCP, Bonjour e IPSec. Esta definição também bloqueia todos os serviços de partilha, incluindo o compartilhamento de tela, acesso remoto, compartilhamento de música do iTunes e muito mais. A opção **Não configurado** (predefinição) permite ligações de entrada e a partilha de serviços.
- **O modo invisível**: **Ativar** o modo Furtivo para impedir que os dispositivos a responder aos pedidos, que podem ser efetuados meus utilizadores mal intencionados de pesquisa. Quando ativado, o dispositivo continua a responder a pedidos recebidos de aplicações autorizadas. A opção **Não configurado** (predefinição) deixa o modo furtivo desativado.

### <a name="gatekeeper"></a>Controlador de chamadas

Para obter mais informações, consulte [controlador de chamadas no macOS](https://support.apple.com/HT202491) (abre o site da Apple).

**Permitir aplicações transferidas a partir destas localizações**: Permite que aplicativos suportados ser instalado nos seus dispositivos a partir de localizações diferentes. As suas opções de localização:

- **Não configurado**: Predefinição. A opção de controlador de chamadas não tem qualquer impacto na conformidade ou não conformidade. 
- **Mac App Store**: Instale apenas as aplicações para Mac app store. Não é possível instalar aplicações de terceiros nem de programadores identificados. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não sejam da Mac App Store, o dispositivo será considerado não conforme.
- **Mac App Store e programadores identificados**: Instale aplicações para Mac app store e programadores identificados. O macOS verifica a identidade dos programadores e faz outras verificações para confirmar a integridade da aplicação. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não estejam abrangidas por estas opções, o dispositivo será considerado não conforme.
- **Em qualquer lugar**: Aplicações podem ser instaladas de qualquer lugar e por qualquer programador. Esta é a opção menos segura.

Selecione **OK** > **Criar** para guardar as alterações.

## <a name="next-steps"></a>Passos Seguintes

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para políticas de filtro](scope-tags.md).
- [Monitorizar as suas políticas de conformidade](compliance-policy-monitor.md).
- Consulte a [definições de política de conformidade para iOS](compliance-policy-create-ios.md) dispositivos.