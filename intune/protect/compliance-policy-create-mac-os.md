---
title: Definições de conformidade de dispositivos macOS no Microsoft Intune – Azure | Microsoft Docs
description: Veja uma lista de todas as definições que pode utilizar quando define a conformidade para os seus dispositivos macOS no Microsoft Intune. Exija a proteção de integridade do sistema da Apple, defina as restrições de palavra-passe, exija uma firewall, permita o controlador de chamadas e muito mais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/22/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.reviewer: samyada
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 518f0b825b71a9773ed66dd480b329e998f919c4
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72813513"
---
# <a name="macos-settings-to-mark-devices-as-compliant-or-not-compliant-using-intune"></a>Definições do macOS para marcar dispositivos como conformes ou não conformes com o Intune

Este artigo apresenta e descreve as definições de conformidade diferentes que pode configurar em dispositivos macOS no Intune. Como parte da sua solução de gestão de dispositivos móveis (MDM), utilize estas definições para definir uma versão mínima e máxima do SO, definir a data de expiração de palavras-passe e muito mais.

Esta funcionalidade aplica-se a:

- macOS

Enquanto administrador do Intune, utilize estas definições de conformidade para ajudar a proteger os recursos da sua organização. Para saber mais sobre as políticas de conformidade e para o que servem, veja a [introdução à conformidade de dispositivos](device-compliance-get-started.md).

## <a name="before-you-begin"></a>Antes de começar

[Criar uma política de conformidade](create-compliance-policy.md#create-the-policy). Em **Plataforma**, selecione **macOS**.

## <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Exigir a proteção da integridade do sistema**:  
  - **Não configurado** (*padrão*)-essa configuração não é avaliada quanto à conformidade ou à não conformidade.
  - **Exigir** -exigir que dispositivos MacOS tenham [proteção de integridade do sistema](https://support.apple.com/HT204899) (abre o site da Apple) habilitado.  

## <a name="device-properties"></a>Propriedades do Dispositivo

- **SO mínimo obrigatório**:  
  quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme. É apresentada uma hiperligação com informações sobre como atualizar. O usuário do dispositivo pode optar por atualizar seu dispositivo. Depois, pode aceder aos recursos da organização.

- **Versão máxima de SO permitida**:  
  quando um dispositivo utiliza uma versão do SO posterior à versão na regra, o acesso aos recursos da organização é bloqueado. O usuário do dispositivo é solicitado a entrar em contato com o administrador de ti. O dispositivo não poderá aceder aos recursos da organização, enquanto a regra não for alterada para permitir a versão do SO.

- **Versão mínima da compilação do SO**:  
  quando a Apple publica atualizações de segurança, o número da compilação é normalmente atualizado, não a versão do SO. Utilize esta funcionalidade para introduzir um número mínimo de compilação permitido no dispositivo.

- **Versão máxima da compilação do SO**:  
  quando a Apple publica atualizações de segurança, o número da compilação é normalmente atualizado, não a versão do SO. Utilize esta funcionalidade para introduzir um número máximo de compilação permitido no dispositivo.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**:  
  - **Não configurado** (*padrão*)
  - **Exigir** Os usuários devem inserir uma senha antes que possam acessar seu dispositivo.

- **Palavras-passe simples**:  
  - **Não configurado** (*padrão*)-os usuários podem criar senhas simples, como **1234** ou **1111**.
  - **Bloquear** -os usuários não podem criar senhas simples, como **1234** ou **1111**.

- **Comprimento mínimo da palavra-passe**:  
  introduza o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.

- **Tipo de palavra-passe**: escolha se uma palavra-passe deve ter apenas carateres **Numéricos** ou se deve existir uma combinação de números e de outros carateres (**Alfanuméricos**).

- **Número de carateres não alfanuméricos na palavra-passe**:  
  Insira o número mínimo de caracteres especiais, como `&`, `#`, `%`, `!`e assim por diante, que deve estar na senha.

  Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

- **Minutos de inatividade antes de a palavra-passe ser exigida**:  
  introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da palavra-passe (dias)** :  
  selecione o número de dias antes de a palavra-passe expirar e ser necessário criar uma nova.

- **Número de palavras-passe anteriores para impedir a reutilização**:  
  introduza o número de palavras-passe utilizadas anteriormente que não podem ser utilizadas.
> [!IMPORTANT]
> As alterações ao requisito de palavra-passe num dispositivo macOS só têm efeito na próxima alteração de palavra-passe do utilizador. Por exemplo, se definir uma restrição de comprimento da palavra-passe para oito dígitos e o dispositivo macOS tiver atualmente uma palavra-passe de seis dígitos, o mesmo permanecerá em conformidade até à próxima vez que o utilizador atualizar a palavra-passe no dispositivo.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo**:  
  - **Não configurado** (*padrão*)
  - **Exigir** -use *exigir* para criptografar o armazenamento de dados em seus dispositivos.

### <a name="device-security"></a>Segurança do Dispositivo

A firewall protege os dispositivos contra o acesso não autorizado à rede. Pode utilizar a firewall para controlar as ligações por aplicação. 

- **Firewall**:  
  - **Não configurado** (*padrão*)-essa configuração deixa o firewall desativado e o tráfego de rede é permitido (não bloqueado).
  - **Habilitar** -use *habilitar* para ajudar a proteger dispositivos contra acesso não autorizado. Ativar esta funcionalidade permite-lhe processar as ligações recebidas da Internet e utilizar o modo furtivo. 

- **Ligações de entrada**:  
  - **Não configurado** (*padrão*) – permite conexões de entrada e serviços de compartilhamento.
  - **Bloquear** -bloquear todas as conexões de rede de entrada, exceto as conexões necessárias para os serviços básicos da Internet, como DHCP, Bonjour e IPsec. Esta definição também bloqueia todos os serviços de partilha, incluindo a partilha de ecrã, o acesso remoto, a partilha de música do iTunes, entre outros.  

- **Modo Furtivo**:  
  - **Não configurado** (*padrão*)-essa configuração deixa o modo furtivo desativado.
  - **Habilitar** – ativar o modo furtivo para impedir que os dispositivos respondam às solicitações de investigação, que podem ser transformados por meus usuários mal-intencionados. Quando ativado, o dispositivo continua a responder a pedidos recebidos de aplicações autorizadas.  

### <a name="gatekeeper"></a>Controlador de chamadas

Para obter mais informações, veja [Controlador de chamadas no macOS](https://support.apple.com/HT202491) (abre o site da Apple).

**Permitir aplicações transferidas a partir destas localizações**: permite a instalação de aplicações suportadas nos seus dispositivos a partir de diferentes localizações. As suas opções de localização:

- **Não configurado** (*padrão*)-a opção de gatekeeper não tem impacto sobre a conformidade ou a não conformidade.  
- **Mac App Store** -Instale somente aplicativos para a Mac App Store. Não é possível instalar aplicações de terceiros nem de programadores identificados. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não sejam da Mac App Store, o dispositivo será considerado não conforme.
- **Mac App Store e desenvolvedores identificados** -instale aplicativos para a Mac App Store e de desenvolvedores identificados. O macOS verifica a identidade dos programadores e faz outras verificações para confirmar a integridade da aplicação. Se um utilizador selecionar o Controlador de Chamadas para instalar aplicações que não estejam abrangidas por estas opções, o dispositivo será considerado não conforme.
- **Em qualquer lugar** -os aplicativos podem ser instalados de qualquer lugar e por qualquer desenvolvedor. Esta é a opção menos segura.
 

## <a name="next-steps"></a>Próximos passos

- [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) e [utilizar etiquetas de âmbito para filtrar políticas](../fundamentals/scope-tags.md).
- [Monitorizar as políticas de conformidade](compliance-policy-monitor.md).
- Veja as [definições de política de conformidade para dispositivos iOS](compliance-policy-create-ios.md).