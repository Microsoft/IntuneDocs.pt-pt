---
title: Criar a política de conformidade de dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
description: Crie ou configure uma política de conformidade de dispositivos do Microsoft Intune para dispositivos macOS para utilizar a Proteção da Integridade do Sistema, definir a versão do sistema operativo mínima e máxima, escolher os requisitos de palavra-passe e encriptar o armazenamento de dados.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 469c0b7c3e67135c53de7c58583d820e1750ad7f
ms.sourcegitcommit: ecd6aebe50b1440a282dfdda771e37fbb8750d42
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2018
ms.locfileid: "52728808"
---
# <a name="add-a-device-compliance-policy-for-macos-devices-with-intune"></a>Adicionar uma política de conformidade para dispositivos macOS com o Intune

Uma política de conformidade de dispositivos macOS no Intune determina as regras e as definições que os dispositivos macOS têm de cumprir para estarem em conformidade. Quando utiliza políticas de conformidade de dispositivos com acesso condicional, pode permitir ou bloquear o acesso aos recursos da empresa. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade. Pode criar as políticas de conformidade de dispositivos para cada plataforma no portal do Azure no Intune. Para saber mais sobre as políticas de conformidade, veja [Introdução à conformidade de dispositivos](device-compliance-get-started.md).

A tabela seguinte descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional:

---------------------------

| Definição de política | macOS 10.11 e posterior |
| --- | --- |
| **Configuração do PIN ou da palavra-passe** | Corrigido |   
| **Encriptação do dispositivo** | Corrigido (ao definir um PIN) |
| **Perfil de e-mail** | Em quarentena |
|**Versão mínima do SO** | Em quarentena |
| **Versão máxima do SO** | Em quarentena |

---------------------------

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. Por exemplo, forçar o utilizador a definir um PIN.

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando o dispositivo não é conforme, são efetuadas as seguintes ações:

- O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Em **Plataforma**, selecione **macOS**. 
5. Escolher **configurar as definições**e introduza o **estado de funcionamento do dispositivo**, **propriedades do dispositivo**, e **segurança do sistema** definições descritas na Este artigo. Quando tiver terminado, selecione **OK** e **Criar**.

## <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Exigir uma proteção da integridade do sistema**: **exija** que os seus dispositivos macOS tenham a [Proteção da Integridade do Sistema](https://support.apple.com/HT204899) ativada.

## <a name="device-properties"></a>Propriedades do dispositivo

- **Versão do SO mínima**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não estando em conformidade. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão do SO máxima**: quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não poderá aceder aos recursos da empresa.
- **Versão de compilação de SO mínimo**: Apple quando publica atualizações de segurança, o número de compilação, normalmente, é atualizado, não a versão do SO. Utilize esta funcionalidade para inserir um número de compilação permitido mínimo no dispositivo.
- **Versão de compilação do SO máximo**: Apple quando publica atualizações de segurança, o número de compilação, normalmente, é atualizado, não a versão do SO. Utilize esta funcionalidade para inserir um número de compilação permitido máximo no dispositivo.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exige** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos.
- **Palavras-passe simples**: defina como **Bloquear** para que os utilizadores não possam criar palavras-passe simples, como **1234** ou **1111**. Defina como **Não configurado** para permitir aos utilizadores criar palavras-passe como **1234** ou **1111**.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.
- **Tipo de palavra-passe**: escolha se uma palavra-passe deve ter apenas carateres **Numéricos** ou se deve existir uma combinação de números e de outros carateres (**Alfanuméricos**).
- **Número de carateres não alfanuméricos na palavra-passe**: introduza o número mínimo de carateres especiais (&, #, %, !, etc.) que têm de ser incluídos na palavra-passe.

    Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe expirar e ser preciso criar uma nova.
- **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas.

    > [!IMPORTANT]
    > As alterações ao requisito de palavra-passe num dispositivo macOS só têm efeito na próxima alteração de palavra-passe do utilizador. Por exemplo, se definir uma restrição de comprimento da palavra-passe para oito dígitos e o dispositivo macOS tiver atualmente uma palavra-passe de seis dígitos, o mesmo permanecerá em conformidade até à próxima vez que o utilizador atualizar a palavra-passe no dispositivo.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo**: escolha **Exigir** a encriptação do armazenamento de dados nos dispositivos.

### <a name="device-security"></a>Segurança do Dispositivo
A firewall protege os dispositivos contra o acesso não autorizado à rede. Pode utilizar a firewall para controlar as ligações por aplicação. 

- **Firewall**: a opção **Ativada** ativa a firewall que ajuda a proteger os dispositivos contra o acesso não autorizado. Ativar esta funcionalidade permite-lhe processar as ligações recebidas da Internet e utilizar o modo furtivo. A opção **Não configurada** (predefinição) deixa a firewall desativada e permite o tráfego de rede (não bloqueado).
- **Ligações de entrada**: a opção **Bloquear** bloqueia todas as ligações de rede de entrada, exceto as ligações necessárias para serviços básicos de Internet, tal como o DHCP, Bonjour e IPSec. Esta definição também bloqueia todos os serviços de partilha, incluindo a partilha de ecrã, o acesso remoto, a partilha de música do iTunes, entre outros. A opção **Não configurado** (predefinição) permite ligações de entrada e a partilha de serviços. 
- **Modo invisível**: a opção **Ativar** ativa o modo invisível para impedir que o dispositivo responda aos pedidos de pesquisa que podem ser feitos por utilizadores mal-intencionados. Quando ativado, o dispositivo continua a responder a pedidos recebidos de aplicações autorizadas. A opção **Não configurado** (predefinição) deixa o modo furtivo desativado.

### <a name="gatekeeper"></a>Controlador de chamadas

**Permitir aplicações transferidas a partir destas localizações**: permite a instalação de aplicações suportadas nos seus dispositivos a partir de diferentes localizações. As suas opções de localização:

- **Não configurado**: predefinição. A opção do controlador de chamadas não tem impacto na conformidade ou não conformidade. 
- **Mac App Store**: instalar apenas aplicações da Mac App Store. Não é possível instalar aplicações de terceiros nem de programadores identificados. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não sejam da Mac App Store, o dispositivo será considerado não conforme.
- **Mac App Store e programadores identificados**: instalar aplicações da Mac App Store e programadores identificados. O macOS verifica a identidade dos programadores e faz outras verificações para confirmar a integridade da aplicação. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não estejam abrangidas por estas opções, o dispositivo será considerado não conforme.
- **Em qualquer lado**: as aplicações podem ser instaladas a partir de qualquer localização e por qualquer programador. Esta é a opção menos segura.

Para obter mais detalhes na documentação da Apple, veja [Controlador de Chamadas no macOS](https://support.apple.com/HT202491).

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

1. Escolha uma política configurada por si. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Escolha a política e, em seguida, **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e escolha **Guardar** para implementar a política aos utilizadores.

> [!TIP]
> Por predefinição, os dispositivos realizam uma verificação de conformidade a cada oito horas. No entanto, os utilizadores podem impor este processo através da aplicação Portal da Empresa do Intune.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores visados pela política são avaliados quanto à conformidade.

## <a name="next-steps"></a>Passos Seguintes
[Automatizar o e-mail e adicionar ações para dispositivos não conformes](actions-for-noncompliance.md)  
[Monitorizar as políticas de conformidade do Dispositivo do Intune](compliance-policy-monitor.md)
