---
title: Relatório de criptografia para dispositivos criptografados no Microsoft Intune
titleSuffix: Microsoft Intune
description: Exiba um relatório no status de criptografia do dispositivo iOS ou Windows e acesse o FileVault e as chaves de recuperação do BitLocker de dentro do portal de Microsoft Intune.
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
ms.openlocfilehash: 5d9508c5d69b0790efa37ee633f8216bfd2bb30c
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164675"
---
# <a name="monitor-device-encryption-with-intune"></a>Monitorar a criptografia de dispositivo com o Intune

O relatório de criptografia Microsoft Intune é um local centralizado para exibir detalhes sobre o status de criptografia de um dispositivo e encontrar opções para gerenciar as chaves de recuperação do dispositivo. As opções de chave de recuperação que estão disponíveis dependem do tipo de dispositivo que você está exibindo.

Para localizar o relatório, entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431). Selecione **dispositivos** > **Monitor**e, em *configuração*, selecione **relatório de criptografia**.

## <a name="view-encryption-details"></a>Exibir detalhes de criptografia

O relatório de criptografia mostra detalhes comuns nos dispositivos com suporte que você gerencia. As seções a seguir fornecem detalhes sobre as informações que o Intune apresenta no relatório.

### <a name="prerequisites"></a>Pré-requisitos

O relatório de criptografia dá suporte a relatórios em dispositivos que executam as seguintes versões de sistema operacional:

- macOS 10,13 ou posterior
- Windows versão 1607 ou posterior

### <a name="report-details"></a>Detalhes do relatório

O painel relatório de criptografia exibe uma lista dos dispositivos que você gerencia com detalhes de alto nível sobre esses dispositivos. Você pode selecionar um dispositivo na lista para fazer drill-in e exibir detalhes adicionais no painel [status de criptografia de dispositivo](#device-encryption-status) de dispositivos.

- **Nome do dispositivo** -o nome do dispositivo.
- **Sistema operacional** – a plataforma do dispositivo, como Windows ou MacOS.
- **Versão do sistema operacional** – a versão do Windows ou MacOS no dispositivo.
- **Versão do TPM** *(aplica-se somente ao Windows 10)* – a versão do chip Trusted Platform Module (TPM) no dispositivo Windows 10.
- **Prontidão de criptografia** – uma avaliação da preparação dos dispositivos para dar suporte a uma tecnologia de criptografia aplicável, como o BitLocker ou a criptografia FileVault. Os dispositivos são identificados como:
  - **Pronto**: o dispositivo pode ser criptografado usando a política de MDM, que exige que o dispositivo atenda aos seguintes requisitos:

    **Para dispositivos MacOS**:
    - MacOS versão 10,13 ou posterior

    **Para dispositivos Windows 10**:
    - Versão 1703 ou posterior, do *Business*, *Enterprise*, *education*ou da versão 1809 ou posterior do *pro*
    - O dispositivo deve ter um chip TPM

    Para obter mais informações, consulte o [provedor de serviços de configuração do BitLocker (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) na documentação do Windows.

  - **Não está pronto**: o dispositivo não tem recursos de criptografia completos, mas ainda oferece suporte à criptografia. Por exemplo, um dispositivo Windows pode ser criptografado manualmente por um usuário ou por meio de Política de Grupo que pode ser definido para permitir a criptografia sem um TPM.
  - **Não aplicável**: não há informações suficientes para classificar este dispositivo.

- **Status de criptografia** – se a unidade do sistema operacional está criptografada.

- **Nome principal do usuário** – o usuário principal do dispositivo.

### <a name="device-encryption-status"></a>Status de criptografia do dispositivo

Quando você seleciona um dispositivo no relatório de criptografia, o Intune exibe o painel **status de criptografia do dispositivo** . Esse painel fornece os seguintes detalhes:

- **Nome do dispositivo** – o nome do dispositivo que você está exibindo.

- **Prontidão para criptografia** -uma avaliação da preparação dos dispositivos para dar suporte à criptografia por meio da política de MDM.

  Por exemplo: quando um dispositivo Windows 10 tem uma prontidão de *não estar pronto*, ele ainda pode dar suporte à criptografia. Para ter a designação *pronta* , o dispositivo Windows 10 deve ter um chip TPM. Os chips do TPM não são necessários para dar suporte à criptografia. (Para obter mais informações, consulte *prontidão de criptografia* na seção anterior.)

- **Status de criptografia** – se a unidade do sistema operacional está criptografada. Pode levar até 24 horas para que o Intune relate o status de criptografia de um dispositivo ou uma alteração nesse status. Esse tempo inclui o tempo para o sistema operacional criptografar, mais o tempo para o dispositivo relatar de volta para o Intune.

  Para acelerar o relatório do status de criptografia do FileVault antes que o check-in do dispositivo normalmente ocorra, os usuários sincronizam seus dispositivos após a criptografia ser concluída.

- **Perfis** – uma lista dos perfis de *configuração do dispositivo* que se aplicam a este dispositivo e são configurados com os seguintes valores:

  - MacOS
    - Tipo de perfil = *Endpoint Protection*
    - Configurações > FileVault > FileVault = *habilitar*

  - Windows 10:
    - Tipo de perfil = *Endpoint Protection*
    - Configurações > criptografia do Windows > dispositivos de criptografia = *exigir*

  Você pode usar a lista de perfis para identificar políticas individuais para revisão caso o *Resumo do estado do perfil* indique problemas.

- **Resumo do estado do perfil** – um resumo dos perfis que se aplicam a este dispositivo. O resumo representa a condição menos favorável nos perfis aplicáveis. Por exemplo, se apenas um dos vários perfis aplicáveis resultar em um erro, o *Resumo do estado do perfil* exibirá um *erro*.

  Para exibir mais detalhes de um status, acesse **Intune** > **configuração do dispositivo** > **perfis**e selecione o perfil. Opcionalmente, selecione **status do dispositivo** e, em seguida, selecione um dispositivo.

- **Detalhes do status** – detalhes avançados sobre o estado de criptografia do dispositivo.

  > [!IMPORTANT]
  > Para dispositivos Windows 10, o Intune mostra *detalhes de status* somente para dispositivos que executam a *atualização do Windows 10 de abril de 2019* ou posterior.

  Este campo exibe informações para cada erro aplicável que pode ser detectado. Você pode usar essas informações para entender por que um dispositivo pode não estar pronto para criptografia.

  Veja a seguir exemplos dos detalhes de status que o Intune pode relatar:

  **MacOS**:
  - A chave de recuperação ainda não foi recuperada e armazenada. Provavelmente, o dispositivo não foi desbloqueado ou não fez check-in.

    *Considere: esse resultado não representa necessariamente uma condição de erro, mas um estado temporário que pode ser devido ao tempo no dispositivo em que a caução para chaves de recuperação deve ser configurada antes que a solicitação de criptografia seja enviada para o dispositivo. Esse status também pode indicar que o dispositivo permanece bloqueado ou não fez check-in no Intune recentemente. Por fim, como a criptografia FileVault não é iniciada até que um dispositivo seja conectado (carregando), é possível que um usuário receba uma chave de recuperação para um dispositivo que ainda não esteja criptografado*.

  - O usuário está desfazendo a criptografia ou está atualmente no processo de criptografia.

    *Considere: o usuário ainda não fez logoff depois de receber a solicitação de criptografia, o que é necessário antes que o FileVault possa criptografar o dispositivo ou o usuário tenha descriptografado manualmente o dispositivo. O Intune não pode impedir que um usuário descriptografe seu dispositivo.*

  - O dispositivo já está criptografado. O usuário do dispositivo deve descriptografar o dispositivo para continuar.

    *Considere: o Intune não pode configurar o FileVault em um dispositivo que já está criptografado. Em vez disso, o usuário precisa descriptografar manualmente seu dispositivo antes que ele possa ser gerenciado por uma política de configuração de dispositivo e o Intune*.

  - O FileVault precisa que o usuário aprove seu perfil de gerenciamento no MacOS Catalina e superior.

    *Considere: a partir da versão 10,15 do MacOS, as configurações de registro aprovadas pelo usuário podem resultar no requisito de que os usuários aprovem manualmente a criptografia FileVault. Para obter mais informações, consulte [registro aprovado pelo usuário](../enrollment/macos-enroll.md) na documentação do Intune*.

  - Conhecidos.

    *Considere: uma possível causa de um status desconhecido é que o dispositivo está bloqueado e o Intune não pode iniciar o processo de caução ou de criptografia. Depois que o dispositivo estiver desbloqueado, o progresso poderá continuar*.

  **Windows 10**:
  - A política do BitLocker requer consentimento do usuário para iniciar o assistente de Criptografia de Unidade de Disco BitLocker para iniciar a criptografia do volume do sistema operacional, mas o usuário não consentiu.

  - O método de criptografia do volume do sistema operacional não corresponde à política do BitLocker.

  - A política de BitLocker requer um protetor TPM para proteger o volume do sistema operacional, mas um TPM não é usado.

  - A política do BitLocker requer um protetor somente TPM para o volume do sistema operacional, mas a proteção do TPM não é usada.

  - A política do BitLocker requer proteção TPM + PIN para o volume do sistema operacional, mas um protetor TPM + PIN não é usado.

  - A política do BitLocker requer proteção de chave TPM + inicialização para o volume do sistema operacional, mas um protetor de chave TPM + Startup não é usado.

  - A política do BitLocker requer TPM + PIN + proteção de chave de inicialização para o volume do sistema operacional, mas um TPM + PIN + protetor de chave de inicialização não é usado.

  - O volume do sistema operacional está desprotegido.

  - Falha no backup da chave de recuperação.

  - Uma unidade fixa está desprotegida.

  - O método de criptografia da unidade fixa não corresponde à política do BitLocker.

  - Para criptografar unidades, a política do BitLocker exige que o usuário entre como administrador ou, se o dispositivo for ingressado no Azure AD, a política AllowStandardUserEncryption deverá ser definida como 1.

  - O ambiente de recuperação do Windows (WinRE) não está configurado.

  - Um TPM não está disponível para o BitLocker porque não está presente, se tornou indisponível no registro ou se o sistema operacional está em uma unidade removível.

  - O TPM não está pronto para o BitLocker.

  - A rede não está disponível, o que é necessário para o backup de chave de recuperação.

## <a name="export-report-details"></a>Exportar detalhes do relatório

Ao exibir o painel relatório de criptografia, você pode selecionar **Exportar** para criar um download de arquivo *. csv* dos detalhes do relatório. Este relatório inclui os detalhes de alto nível do painel *relatório de criptografia* e detalhes do *status de criptografia do dispositivo* para cada dispositivo gerenciado.

![Exportar detalhes](./media/encryption-monitor/export.png)

Esse relatório pode ser usado para identificar problemas de grupos de dispositivos. Por exemplo, você pode usar o relatório para identificar uma lista de dispositivos macOS que todos os *FileVault de relatório já estão habilitados pelo usuário*, o que indica dispositivos que devem ser descriptografados manualmente antes que o Intune possa gerenciar suas configurações de FileVault.

## <a name="filevault-recovery-keys"></a>Chaves de recuperação FileVault

Quando o Intune criptografa primeiro um dispositivo macOS com FileVault, uma chave de recuperação pessoal é criada. Após a criptografia, o dispositivo exibe a chave pessoal uma única vez para o usuário final.

Para dispositivos gerenciados, o Intune pode caução em uma cópia da chave de recuperação pessoal. A caução de chaves permite que os administradores do Intune giram as chaves para ajudar a proteger os dispositivos e os usuários a recuperarem uma chave de recuperação pessoal perdida ou girada.

O Intune dá suporte a várias opções para girar e recuperar as chaves de recuperação pessoal. Um motivo para girar uma chave é se a chave pessoal atual é perdida ou pensa em risco.

> [!IMPORTANT]
> Os dispositivos criptografados por usuários, e não pelo Intune, não podem ser gerenciados pelo Intune. Isso significa que o Intune não pode fazer a garantia da recuperação pessoal desses dispositivos nem gerenciar a rotação da chave de recuperação. Antes que o Intune possa gerenciar FileVault e chaves de recuperação para o dispositivo, o usuário deve descriptografar seu dispositivo e, em seguida, permitir que o Intune criptografe o dispositivo.

### <a name="rotate-recovery-keys"></a>Girar as chaves de recuperação

- **Rotação automática**: como administrador, você pode configurar a FileVault configuração de chave de recuperação pessoal para gerar automaticamente a nova chave de recuperação periodicamente. Quando uma nova chave é gerada para um dispositivo, a chave não é exibida para o usuário. Em vez disso, o usuário deve obter a chave de um administrador ou usando o aplicativo do portal da empresa.

- **Rotação manual**: como administrador, você pode exibir informações para um dispositivo que você gerencia com o Intune e que é criptografado com o FileVault. Você pode optar por girar manualmente a chave de recuperação para dispositivos corporativos. Não é possível girar as chaves de recuperação para dispositivos pessoais.

  Para girar uma chave de recuperação:

  1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
  
  2. Selecione **dispositivos** > **todos os dispositivos**.
  
  3. Na lista de dispositivos, selecione o dispositivo que está criptografado e para o qual você deseja girar sua chave. Em monitor, selecione **chaves de recuperação**.
  
  4. No painel chaves de recuperação, selecione **girar chave de recuperação FileVault**.

     Na próxima vez que o dispositivo fizer check-in no Intune, a chave pessoal será girada. Quando necessário, a nova chave pode ser obtida pelo usuário final por meio do portal da empresa.

### <a name="recover-recovery-keys"></a>Recuperar chaves de recuperação

- **Administrador**: os administradores não podem exibir chaves de recuperação pessoal para dispositivos que são criptografados com o FileVault.

- **Usuário final**: os usuários finais usam o site Portal da empresa de qualquer dispositivo para exibir a chave de recuperação pessoal atual para qualquer um de seus dispositivos gerenciados. Não é possível exibir as chaves de recuperação do aplicativo Portal da Empresa.

  Para exibir uma chave de recuperação:
  
  1. Entre no site do *portal da empresa do Intune* em qualquer dispositivo.

  2. No portal, vá para **dispositivos** e selecione o dispositivo MacOS que é criptografado com FileVault.

  3. Selecione **obter chave de recuperação**. A chave de recuperação atual é exibida.

## <a name="bitlocker-recovery-keys"></a>Chaves de recuperação do BitLocker

O Intune fornece acesso à folha do Azure AD para o BitLocker para que você possa exibir IDs de chave e chaves de recuperação do BitLocker para seus dispositivos Windows 10, de dentro do portal do Intune. Para estar acessível, o dispositivo deve ter suas chaves com garantia para o Azure AD.

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > **Todos os dispositivos**.

3. Selecione um dispositivo na lista e, em *Monitor*, selecione chaves de **recuperação**.
  
   Quando as chaves estão disponíveis no Azure AD, as seguintes informações estão disponíveis:
   - ID da chave do BitLocker
   - Chave de recuperação do BitLocker
   - Tipo de unidade

   Quando as chaves não estiverem no Azure AD, o Intune não exibirá *nenhuma chave do BitLocker encontrada para este dispositivo*.

As informações do BitLocker são obtidas usando o [provedor de serviços de configuração do BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (CSP). O CSP do BitLocker tem suporte no Windows 10 versão 1703 e posterior e para o Windows 10 pro versão 1809 e posterior.

## <a name="next-steps"></a>Próximos passos

Criar uma política de [conformidade do dispositivo](compliance-policy-create-windows.md) .
