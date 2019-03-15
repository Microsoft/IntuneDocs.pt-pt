---
title: Criar a política de conformidade de dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
description: Crie ou configure uma política de conformidade de dispositivos do Microsoft Intune para dispositivos macOS para utilizar a Proteção da Integridade do Sistema, definir a versão do sistema operativo mínima e máxima, escolher os requisitos de palavra-passe e encriptar o armazenamento de dados.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/14/2018
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
ms.openlocfilehash: 21eca671d40f1ee2f2f9176a272cab5754140a26
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57566612"
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

- **Exigir uma proteção de integridade do sistema**: **Exigir** seus dispositivos macOS tenham [proteção da integridade do sistema](https://support.apple.com/HT204899) ativada.

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
- **Número de carateres não alfanuméricos na palavra-passe**: Introduza o número mínimo de carateres especiais (&, #, %,!, e assim por diante) que têm de ser incluídos na palavra-passe.

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

- **Firewall**: **Ativar** para ajudar a proteger os dispositivos contra acesso não autorizado. Ativar esta funcionalidade permite-lhe processar as ligações recebidas da Internet e utilizar o modo furtivo. A opção **Não configurada** (predefinição) deixa a firewall desativada e permite o tráfego de rede (não bloqueado).
- **Ligações de entrada**: **Bloco** todas as ligações de rede recebidas, exceto as necessárias para serviços básicos de internet, como DHCP, Bonjour e IPSec. Esta definição também bloqueia todos os serviços de partilha, incluindo a partilha de ecrã, o acesso remoto, a partilha de música do iTunes, entre outros. A opção **Não configurado** (predefinição) permite ligações de entrada e a partilha de serviços. 
- **O modo invisível**: **Ativar** Modo Furtivo para impedir que o dispositivo responda aos pedidos, que podem ser efetuados meus utilizadores mal intencionados de pesquisa. Quando ativado, o dispositivo continua a responder a pedidos recebidos de aplicações autorizadas. A opção **Não configurado** (predefinição) deixa o modo furtivo desativado.

### <a name="gatekeeper"></a>Controlador de chamadas

**Permitir aplicações transferidas a partir destas localizações**: Permite que aplicativos suportados ser instalado nos seus dispositivos a partir de localizações diferentes. As suas opções de localização:

- **Não configurado**: Predefinição. A opção de controlador de chamadas não tem qualquer impacto na conformidade ou não conformidade. 
- **Mac App Store**: Instale apenas as aplicações para Mac app store. Não é possível instalar aplicações de terceiros nem de programadores identificados. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não sejam da Mac App Store, o dispositivo será considerado não conforme.
- **Mac App Store e programadores identificados**: Instale aplicações para Mac app store e programadores identificados. O macOS verifica a identidade dos programadores e faz outras verificações para confirmar a integridade da aplicação. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não estejam abrangidas por estas opções, o dispositivo será considerado não conforme.
- **Em qualquer lugar**: Aplicações podem ser instaladas de qualquer lugar e por qualquer programador. Esta é a opção menos segura.

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
