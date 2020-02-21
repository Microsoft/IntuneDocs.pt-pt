---
title: Relatório de encriptação de dispositivos encriptados no Microsoft Intune
titleSuffix: Microsoft Intune
description: Veja um relatório sobre o seu iOS/iPadOS ou o estado de encriptação do dispositivo Windows e aceda às chaves de recuperação fileVault e BitLocker a partir do portal Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: daa302813c7ea3ad35ecfa7dd8d70436bfe5e1a4
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77510508"
---
# <a name="monitor-device-encryption-with-intune"></a>Monitorizar encriptação do dispositivo com Intune

O relatório de encriptação Microsoft Intune é um local centralizado para visualizar detalhes sobre o estado de encriptação de um dispositivo e encontrar opções para gerir as chaves de recuperação do dispositivo. As opções-chave de recuperação disponíveis dependem do tipo de dispositivo que está a ver.

Para encontrar o relatório, inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431). Selecione **Dispositivos** > **Monitor**, e, em seguida, em *Configuração,* selecione **relatório de encriptação**.

## <a name="view-encryption-details"></a>Ver detalhes de encriptação

O relatório de encriptação mostra detalhes comuns em todos os dispositivos suportados que gere. As seguintes secções fornecem detalhes sobre as informações que Intune apresenta no relatório.

### <a name="prerequisites"></a>Pré-requisitos

O relatório de encriptação suporta relatórios de reporte em dispositivos que executam as seguintes versões do sistema operativo:

- macOS 10.13 ou posterior
- Versão 1607 ou mais tarde do Windows

### <a name="report-details"></a>Reportar detalhes

O painel de relatório de encriptação apresenta uma lista dos dispositivos que gere com detalhes de alto nível sobre esses dispositivos. Pode selecionar um dispositivo da lista para perfurar e visualizar detalhes adicionais do painel de estado de encriptação do [dispositivo.](#device-encryption-status)

- **Nome** do dispositivo - O nome do dispositivo.
- **OS** – A plataforma do dispositivo, como windows ou macOS.
- **Versão OS** – A versão do Windows ou macOS no dispositivo.
- **Versão TPM** *(aplica-se apenas ao Windows 10)* – A versão do chip Trusted Platform Module (TPM) no dispositivo Windows 10.
- **Prontidão de encriptação** – Uma avaliação da prontidão dos dispositivos para suportar uma tecnologia de encriptação aplicável, como a encriptação BitLocker ou FileVault. Os dispositivos são identificados como:
  - **Ready**: O dispositivo pode ser encriptado utilizando a política de MDM, que requer que o dispositivo cumpra os seguintes requisitos:

    **Para dispositivos macOS:**
    - MacOS versão 10.13 ou mais tarde

    **Para dispositivos Windows 10:**
    - Versão 1703 ou posterior, de *Negócios,* *Empresa,* *Educação,* ou versão 1809 ou posterior da *Pro*
    - O dispositivo deve ter um chip TPM

    Para mais informações, consulte o fornecedor de serviços de [configuração BitLocker (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) na documentação do Windows.

  - **Não está pronto**: O dispositivo não tem capacidades de encriptação completas, mas ainda suporta encriptação. Por exemplo, um dispositivo Windows pode ser encriptado manualmente por um utilizador, ou através da Política de Grupo que pode ser configurado para permitir encriptar sem um TPM.
  - **Não aplicável**: Não há informação suficiente para classificar este dispositivo.

- **Estado de encriptação** – Se a unidade de SO está encriptada.

- **Nome principal** do utilizador - O utilizador principal do dispositivo.

### <a name="device-encryption-status"></a>Estado de encriptação do dispositivo

Quando seleciona um dispositivo a partir do relatório de encriptação, intune exibe o painel de estado de encriptação do **Dispositivo.** Este painel fornece os seguintes detalhes:

- **Nome** do dispositivo – O nome do dispositivo que está a ver.

- **Prontidão de encriptação** - Uma avaliação da prontidão dos dispositivos para suportar a encriptação através da política do MDM.

  Por exemplo: Quando um dispositivo Windows 10 tem uma prontidão de *Não Estar pronto,* pode ainda suportar encriptação. Para ter a designação *Ready,* o dispositivo Windows 10 deve ter um chip TPM. Os chips TPM não são necessários para suportar a encriptação. (Para mais informações, consulte *a prontidão* de encriptação na secção anterior.)

- **Estado de encriptação** - Se a unidade de SO está encriptada. Pode levar até 24 horas para intune reportar sobre o estado de encriptação de um dispositivo ou uma alteração a esse estado. Este tempo inclui tempo para o SISTEMA encriptar, mais tempo para o dispositivo reportar de volta a Intune.

  Para acelerar o relato do estado de encriptação do FileVault antes de ocorrer normalmente o check-in do dispositivo, os utilizadores sincronizam os seus dispositivos após o completede.

- **Perfis** – Uma lista dos perfis de *configuração* do Dispositivo que se aplicam a este dispositivo e são configurados com os seguintes valores:

  - macOS:
    - Tipo de perfil = *Proteção de Ponto final*
    - Definições > FileVault > FileVault = *Ativar*

  - Windows 10:
    - Tipo de perfil = *Proteção de Ponto final*
    - Definições > Encriptação do Windows > Encriptar dispositivos = *Exigir*

  Pode utilizar a lista de perfis para identificar políticas individuais de revisão caso o *resumo do Estado* do Perfil indique problemas.

- **Resumo** do estado de perfil – Um resumo dos perfis que se aplicam a este dispositivo. O resumo representa a condição menos favorável entre os perfis aplicáveis. Por exemplo, se apenas um em cada vários perfis aplicáveis resultar num erro, o *resumo do estado do Perfil* mostrará *Erro*.

  Para ver mais detalhes de um estado, vá à **configuração** do dispositivo **intune** >  > **Perfis**, e selecione o perfil. Opcionalmente, selecione **o estado do Dispositivo** e, em seguida, selecione um dispositivo.

- **Detalhes** do estado – Detalhes avançados sobre o estado de encriptação do dispositivo.

  > [!IMPORTANT]
  > Para dispositivos Windows 10, intune apenas mostra *detalhes de Estado* para dispositivos que executam a *Atualização do Windows 10 de abril de 2019* ou posteriormente.

  Este campo apresenta informações para cada erro aplicável que podem ser detetados. Pode usar esta informação para entender porque é que um dispositivo pode não estar pronto para encriptar.

  Seguem-se exemplos dos detalhes do estado que intune pode reportar:

  **macOS**:
  - A chave de recuperação ainda não foi recuperada e armazenada. O mais provável é que o dispositivo não tenha sido desbloqueado, ou ainda não fez o check-in.

    Considere: Este resultado não representa necessariamente uma condição de erro, mas um estado temporário que pode ser devido ao tempo no dispositivo onde deve ser configurado o depósito para as chaves de recuperação antes do pedido de *encriptação ser enviado para o dispositivo. Este estado também pode indicar que o dispositivo permanece bloqueado ou não fez o check-in com intune recentemente. Finalmente, porque a encriptação fileVault não começa até que um dispositivo esteja ligado (carregamento), é possível que um utilizador receba uma chave de recuperação para um dispositivo que ainda não está encriptado*.

  - O utilizador está a adiar a encriptação ou está atualmente em processo de encriptação.

    *Considere: Ou o utilizador ainda não registou o registo depois de receber o pedido de encriptação, o que é necessário antes que o FileVault possa encriptar o dispositivo, ou o utilizador desencriptao manualmente o dispositivo. A Intune não pode impedir um utilizador de desencriptar o seu dispositivo.*

  - O dispositivo já está encriptado. O utilizador do dispositivo deve desencriptar o dispositivo para continuar.

    *Considere: Intune não pode configurar fileVault num dispositivo que já está encriptado. Em vez disso, o utilizador precisa de desencriptar manualmente o seu dispositivo antes de poder ser gerido por uma política de configuração do dispositivo e insoina .*

  - O FileVault precisa que o utilizador aprove o seu perfil de gestão no MacOS Catalina e superior.

    *Considere: Começando com a versão 10.15 do MacOS (Catalina), as definições de inscrição aprovadas pelo utilizador podem resultar na exigência de que os utilizadores aprovem manualmente a encriptação do FileVault. Para mais informações, consulte a [inscrição aprovada](../enrollment/macos-enroll.md) pelo utilizador na documentação Intune*.

  - Desconhecida.

    *Considere: Uma causa possível para um estado desconhecido é que o dispositivo está bloqueado e Intune não pode iniciar o processo de caução ou encriptação. Depois de o dispositivo ser desbloqueado, o progresso pode continuar.*

  **Windows 10:**
  - A política BitLocker requer o consentimento do utilizador para lançar o Assistente de Encriptação BitLocker Drive para iniciar a encriptação do volume de OS, mas o utilizador não consentiu.

  - O método de encriptação do volume de OS não corresponde à política bitLocker.

  - A política BitLocker requer um protetor TPM para proteger o volume de SPm, mas não é utilizado um TPM.

  - A política BitLocker requer um protetor apenas tPM para o volume de SPm, mas a proteção TPM não é usada.

  - A política BitLocker requer proteção TPM+PIN para o volume de OS, mas não é utilizado um protetor TPM+PIN.

  - A política BitLocker requer proteção de chaves de arranque TPM+para o volume de S, mas não é utilizado um protetor de chaves de arranque TPM+.

  - A política BitLocker requer proteção de teclas de arranque TPM+PIN+para o volume de OS, mas não é utilizado um protetor de teclas TPM+PIN+.

  - O volume de SO está desprotegido.

  - A chave de recuperação falhou.

  - Uma unidade fixa está desprotegida.

  - O método de encriptação da unidade fixa não corresponde à política bitLocker.

  - Para encriptar as unidades, a política BitLocker requer que o utilizador se inscreva como Administrador ou, se o dispositivo estiver ligado ao Azure AD, a política de encriptação AllowStandardUserDeve ser definida para 1.

  - O Ambiente de Recuperação do Windows (WinRE) não está configurado.

  - Um TPM não está disponível para o BitLocker, seja porque não está presente, foi indisponível no Registo, ou o SISTEMA está numa unidade amovível.

  - O TPM não está pronto para o BitLocker.

  - A rede não está disponível, o que é necessário para a chave de recuperação.

## <a name="export-report-details"></a>Detalhes do relatório de exportação

Ao visualizar o painel de relatórios de encriptação, pode selecionar **exportação** para criar um download de ficheiro *.csv* dos detalhes do relatório. Este relatório inclui os detalhes de alto nível do painel de relatório de *encriptação* e detalhes do estado de *encriptação* do dispositivo para cada dispositivo que gere.

![Detalhes da exportação](./media/encryption-monitor/export.png)

Este relatório pode ser utilizado na identificação de problemas para grupos de dispositivos. Por exemplo, pode utilizar o relatório para identificar uma lista de dispositivos macOS que todos os ficheiros do *relatório FileVault já estão ativados pelo utilizador*, o que indica dispositivos que devem ser desencriptados manualmente antes que intune possa gerir as suas definições de FileVault.

## <a name="filevault-recovery-keys"></a>Chaves de recuperação fileVault

Quando a Intune encripta pela primeira vez um dispositivo macOS com fileVault, é criada uma chave de recuperação pessoal. Após a encriptação, o dispositivo apresenta a chave pessoal uma única vez para o utilizador final.

Para dispositivos geridos, o Intune pode esquendar uma cópia da chave de recuperação pessoal. O depósito de teclas permite que os administradores intune rodem as teclas para ajudar a proteger os dispositivos, e os utilizadores recuperem uma chave de recuperação pessoal perdida ou rotativa.

Intune suporta múltiplas opções para rodar e recuperar chaves de recuperação pessoal. Uma das razões para rodar uma chave é se a chave pessoal atual estiver perdida ou se pensa estar em risco.

> [!IMPORTANT]
> Os dispositivos encriptados pelos utilizadores, e não pelo Intune, não podem ser geridos pela Intune. Isto significa que Intune não pode caucionar a recuperação pessoal destes dispositivos, nem gerir a rotação da chave de recuperação. Antes de a Intune poder gerir o FileVault e as chaves de recuperação do dispositivo, o utilizador deve desencriptar o dispositivo e, em seguida, deixar o Intune encriptar o dispositivo.

### <a name="rotate-recovery-keys"></a>Teclas de recuperação rotativas

- **Rotação automática**: Como administrador, pode configurar a rotação da chave de recuperação pessoal do FileVault para gerar automaticamente a nova chave de recuperação periodicamente. Quando uma nova tecla é gerada para um dispositivo, a chave não é apresentada ao utilizador. Em vez disso, o utilizador deve obter a chave quer a partir de um administrador, quer através da aplicação portal da empresa.

- **Rotação manual**: Como administrador, pode visualizar informações para um dispositivo que gere com o Intune e que está encriptado com fileVault. Em seguida, pode optar por rodar manualmente a chave de recuperação para dispositivos corporativos. Não se pode rodar as chaves de recuperação para dispositivos pessoais.

  Para rodar uma chave de recuperação:

  1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
  
  2. Selecione **Dispositivos** > **Todos os dispositivos**.
  
  3. A partir da lista de dispositivos, selecione o dispositivo encriptado e para o qual pretende rodar a sua chave. Em seguida, sob o Monitor, selecione **Teclas de recuperação**.
  
  4. No painel das teclas recovery, **selecione Rotação fileVault chave**de recuperação .

     Da próxima vez que o dispositivo fizer o check-in com Intune, a chave pessoal é girada. Quando necessário, a nova chave pode ser obtida pelo utilizador final através do portal da empresa.

### <a name="recover-recovery-keys"></a>Recuperar chaves de recuperação

- **Administrador**: Os administradores não podem ver chaves de recuperação pessoais para dispositivos encriptados com FileVault.

- **Utilizador final**: Os utilizadores finais utilizam o website do Portal da Empresa a partir de qualquer dispositivo para visualizar a chave de recuperação pessoal atual para qualquer um dos seus dispositivos geridos. Não é possível ver chaves de recuperação da aplicação Portal da Empresa.

  Para ver uma chave de recuperação:
  
  1. Inscreva-se no site do *Intune Company Portal* a partir de qualquer dispositivo.

  2. No portal, vá a **Dispositivos** e selecione o dispositivo macOS que está encriptado com fileVault.

  3. Selecione **Obter tecla de recuperação**. A chave de recuperação atual é apresentada.

## <a name="bitlocker-recovery-keys"></a>Chaves de recuperação BitLocker

Intune fornece acesso à lâmina AD Azure para BitLocker para que possa ver IDs de chave BitLocker e chaves de recuperação para os seus dispositivos Windows 10, a partir do portal Intune. Para ser acessível, o aparelho deve ter as chaves depositadas na AD Azure.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > **Todos os dispositivos**.

3. Selecione um dispositivo da lista e, em seguida, sob *o Monitor,* selecione **teclas recovery**.
  
   Quando as chaves estiverem disponíveis em Azure AD, as seguintes informações estão disponíveis:
   - Id da chave BitLocker
   - Chave de recuperação bitLocker
   - Tipo de Unidade

   Quando as teclas não estiverem em Azure AD, intune apresentará *nenhuma tecla BitLocker encontrada para este dispositivo*.

A informação para o BitLocker é obtida utilizando o fornecedor de serviços de [configuração BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (CSP). O BitLocker CSP é suportado na versão 1703 do Windows 10 e posteriormente, e para a versão 1809 do Windows 10 Pro.

## <a name="next-steps"></a>Próximos passos

Crie uma política de [conformidade com o dispositivo.](compliance-policy-create-windows.md)
