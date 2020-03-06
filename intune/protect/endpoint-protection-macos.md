---
title: Adicionar proteção de ponto final ao macOS no Microsoft Intune – Azure | Microsoft Docs
description: Em dispositivos macOS, utilize o controlador de chamadas para determinar onde as aplicações podem ser instaladas, incluindo a Mac App Store. Ativar ou configurar uma firewall permite aplicações específicas, bloqueia aplicações específicas, utiliza o modo invisível e até bloqueia determinados tipos de ligações de entrada com o Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
ms.topic: reference
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 358a396e762f1f20051abadfc2f3df80f37ca8c8
ms.sourcegitcommit: 25e4847ead0f56c269cfefe1e01c1b9106a28cf1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2020
ms.locfileid: "78368486"
---
# <a name="macos-endpoint-protection-settings-in-intune"></a>Definições de proteção de pontos finais MacOS em Intune  

Este artigo mostra-lhe as definições de proteção de pontofinal que pode configurar para dispositivos que executam o macOS. Configura estas definições utilizando um perfil de configuração do dispositivo macOS para proteção de [pontos finais](endpoint-protection-configure.md) no Intune.  

## <a name="gatekeeper"></a>Controlador de chamadas  

- **Permitir aplicações descarregadas a partir destes locais**  
  Limite as aplicações que um dispositivo pode lançar, dependendo de onde as aplicações foram descarregadas. A intenção é proteger os dispositivos contra malware, e permitir aplicações apenas das fontes em que confia.  

  - **Não configurado**  
  - **Mac App Store**  
  - **Mac App Store e programadores identificados**  
  - **Em qualquer lugar**  

  **Predefinição**: Não configurado  

- **O utilizador pode substituir o Gatekeeper**  
  Impede que os utilizadores ultrapassem a definição do Gatekeeper e impede que os utilizadores do Control clique para instalar uma aplicação. Quando estiver ativado, os utilizadores podem manter a tecla Ctrl premida e clicar em qualquer aplicação e instalá-la.  
 
  - **Não configurado** - Os utilizadores podem controlar o clique para instalar aplicações.  
  - **Block** - Impede que os utilizadores utilizem o 'Control-click' para instalar aplicações.  

  **Predefinição**: Não configurado  

## <a name="firewall"></a>Firewall  

Utilize a firewall para controlar ligações por aplicação e não por porta. Utilizar definições por aplicação torna mais fácil obter as vantagens de proteção da firewall. Também ajuda a impedir que aplicações indesejáveis controlem as portas da rede que estão abertas para as aplicações legítimas.  

**Geral**
- **Firewall**  
  Ative a Firewall para configurar a forma como as ligações de entrada são tratadas no seu ambiente.  
  - **Não configurado**  
  - **Ativar**  

  **Predefinição**: Não configurado  

- **Ligações de entrada**  
  Bloqueie todas as ligações de entrada, exceto as ligações necessárias para serviços básicos de Internet, tais como DHCP, Bonjour e IPSec. Esta funcionalidade também bloqueia todos os serviços de partilha, tal como a Partilha de Ficheiros e a Partilha de Ecrãs. Se estiver a utilizar serviços de partilha, mantenha esta definição como *Não configurado*.  
  - **Não configurado**  
  - **Bloquear**  

  **Predefinição**: Não configurado  

**Permitir ou bloquear ligações de entrada para aplicações específicas.**  

  - **Aplicativos permitidos**  
    Selecione as aplicações que estão explicitamente autorizadas a receber ligações de entrada.  

  - **Aplicativos bloqueados**  
    Selecione as aplicações que devem bloquear as ligações de entrada.  

  - **Modo stealth**  
    Para evitar que o computador responda a pedidos de sondagem, ative o modo de stealth. O dispositivo continua a responder a pedidos recebidos de aplicações autorizadas. São ignorados pedidos inesperados, tais como o protocolo ICMP (ping).  
    - **Não configurado**  
    - **Ativar**  

    **Predefinição**: Não configurado  

## <a name="filevault"></a>FileVault  
Para obter mais informações sobre as definições do Apple FileVault, consulte [o FDEFileVault](https://developer.apple.com/documentation/devicemanagement/fdefilevault) no conteúdo do desenvolvedor da Apple. 

> [!IMPORTANT]  
> A partir do macOS 10.15, a configuração do FileVault requer a inscrição do MDM aprovada pelo utilizador. 

- **FileVault**  
  Pode *ativar* a encriptação full disk utilizando xTS-AES 128 com FileVault em dispositivos que executam o macOS 10.13 e posteriormente.  
  - **Não configurado**  
  - **Ativar**  

  **Predefinição**: Não configurado  

  - **Tipo de chave de recuperação**  
    As chaves de recuperação *das chaves pessoais* são criadas para dispositivos. Configure as seguintes definições para a chave pessoal.  

    - **Localização da chave de recuperação pessoal** - Especifique uma mensagem curta para o utilizador que explique como e onde pode recuperar a sua chave de recuperação pessoal. Este texto é inserido na mensagem que o utilizador vê no seu login no ecrã quando solicitado a introduzir a sua chave de recuperação pessoal se uma palavra-passe for esquecida.  
      
    - Rotação da chave de **recuperação pessoal** - Especifique com que frequência a chave de recuperação pessoal de um dispositivo girará. Pode selecionar o padrão de **Não configurado,** ou um valor de **1** a **12** meses.  

  - **Desativar o pedido de sinalização**  
    Evite a solicitação ao utilizador que solicita que ative o FileVault quando assinar.  Quando programado para desativar, o aviso de inscrição é desativado e, em vez disso, o utilizador é solicitado quando faz o início.  
    - **Não configurado**  
    - **Desativar** - Desative o pedido de inscrição.

    **Predefinição**: Não configurado  

  - **Número de vezes permitidos para contornar**  
  Detete o número de vezes que um utilizador pode ignorar as instruções para ativar o FileVault antes de o FileVault ser necessário para que o utilizador faça o início. 

    - **Não configurado** - A encriptação no dispositivo é necessária antes da próxima inscrição ser permitida.  
    - **1** a **10** - Permita que um utilizador ignore a solicitação de 1 a 10 vezes antes de necessitar de encriptação no dispositivo.  
    - **Sem limite, sempre solicitado** - O utilizador é solicitado para ativar o FileVault, mas a encriptação nunca é necessária.  
 
    **Predefinição**: *Varia* - Quando a definição *Desativar o aviso* de sinal está definida para **Não configurada,** esta definição deprecia **para não configurada**. Quando o *aviso de desativação no sinal* é definido para **Desativar,** esta definição não se aplica a **1** e um valor de **Não configurado** não é uma opção.

Para mais informações sobre fileVault com Intune, consulte as chaves de [recuperação do FileVault](encryption-monitor.md#filevault-recovery-keys).

