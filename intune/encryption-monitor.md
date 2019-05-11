---
title: Relatório de encriptação e chaves do BitLocker no Microsoft Intune
titleSuffix: Microsoft Intune
description: Ver um relatório no seu estado de encriptação de dispositivos e aceder a chaves de recuperação do BitLocker no portal do Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 04/23/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: shpate
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: 52b92483ddafadf460911caaa472825a0bc0a20f
ms.sourcegitcommit: b4483c8476a209de83102e8993d8074dbb323493
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/10/2019
ms.locfileid: "65527225"
---
# <a name="monitor-bitlocker-and-device-encryption"></a>Monitorizar a encriptação BitLocker e o dispositivo  
O Intune fornece uma localização centralizada para identificar o estado de encriptação dos seus dispositivos Windows 10 e ajuda-o a aceder a informações importantes para o BitLocker dos seus dispositivos, como encontrada no Azure Active Directory (Azure AD).  

- O [relatório de encriptação (em pré-visualização pública)](#encryption-report) fornece detalhes sobre o estado de encriptação e a preparação de um dispositivo. Os detalhes do relatório podem ajudá-lo a identificar problemas que impedem a encriptação com êxito de dispositivos que pretende proteger.  
- [Ver detalhes de disco BitLocker (em pré-visualização pública)](#bitlocker-recovery-keys) , como as chaves de ID de chave e a recuperação para os dispositivos a partir do portal do Intune.  

## <a name="encryption-report"></a>Relatório de encriptação
Pode utilizar o relatório de encriptação (em pré-visualização pública) para ver detalhes sobre o estado de encriptação dos seus dispositivos Windows 10.  

Para encontrar o relatório, inicie sessão para o [Intune](https://aka.ms/intuneportal) e aceda a **configuração do dispositivo**e, em *Monitor*, selecione **relatório de encriptação (pré-visualização)**.  

### <a name="prerequisites"></a>Pré-requisitos:
A aparecer no relatório de encriptação, um dispositivo tem de executar o Windows versão 1607 ou posterior.  

### <a name="report-details"></a>Detalhes do relatório
O relatório apresenta os **nome do dispositivo** para os seus dispositivos Windows 10 e detalhes de alto nível sobre cada uma, incluindo:  
- **Versão do SO** – versão do Windows.  
- **Versão do TPM** – a versão do chip Trusted Platform Module (TPM) no dispositivo.  
- **Preparação de encriptação** -uma avaliação de preparação de dispositivos para oferecer suporte a criptografia de disco BitLocker. Dispositivos podem ser identificados como:
  - **Pronto**: O dispositivo pode ser encriptado utilizando a política MDM, que requer o dispositivo tem um TPM e cumpre os requisitos de SKU e versão do Windows 10 seguinte:
    - Versão 1703 ou posterior, de empresas, Enterprise, educação
    - Versão 1809 ou posterior, do Pro  
  
    Para obter mais informações, consulte a [fornecedor de serviços de configuração do BitLocker (CSP)](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) na documentação do Windows.  

  - **Não está pronta**: O dispositivo não tem capacidades de encriptação completa, mas ainda suporta a encriptação. Por exemplo, o dispositivo pode estar encriptado manualmente por um utilizador ou por meio da diretiva de grupo que pode ser definida para permitir a encriptar sem um TMP.
  - **Não aplicável**: Não há informações suficientes para classificar este dispositivo.  

- **Estado de encriptação** – se a unidade do SO é encriptada.  


### <a name="device-encryption-status"></a>Estado de encriptação do dispositivo
Quando um dispositivo é selecionado, o Intune apresenta os **estado de encriptação de dispositivo** painel.

Este painel fornece os seguintes detalhes:  
- **Nome do dispositivo** – o nome do dispositivo que está a ver.  
- **Preparação de encriptação** – um avaliação de preparação de dispositivos para oferecer suporte a criptografia de disco BitLocker. Um dispositivo pode ter um Estado de encriptação de *Encrypted* , mesmo que seja sua prontidão de encriptação *não está pronta*, porque não tem um TPM. (Consulte a preparação de encriptação na secção anterior para obter mais detalhes.)
- **Estado de encriptação** - se a unidade do SO é encriptada.  
- **Perfis** – uma lista da *configuração do dispositivo* perfis aplicáveis a este dispositivo e incluem o seguinte tipo de perfil e as definições:  
  - Tipo de perfil = *Endpoint protection*  
  - Definições > encriptação Windows > encriptar dispositivos = *necessário*  

  Esta lista pode ser de uso na localização políticas individuais para revisão deve o resumo de estado do perfil indicar problemas.  

- **Resumo do Estado de perfil** – um resumo dos perfis de que se aplicam a este dispositivo. O resumo representa a condição, pelo menos, favorável em todos os perfis aplicáveis. Por exemplo, se um perfil resulta num erro, o resumo de estado do perfil apresentará *erro*.  
- **Detalhes do estado** – Advanced detalhes sobre o estado de encriptação do dispositivo. 
  > [!NOTE]  
  > O Intune só mostra *detalhes do estado* para dispositivos que executam o *atualizar do Windows 10 de Abril de 2019* ou posterior.
  
  Este campo apresenta informações para cada erro aplicável que pode ser detetado. Pode usar essas informações para compreender por que um dispositivo pode não ser encriptação pronta.  

  Seguem-se exemplos do Intune pode comunicar os detalhes de estado:  

   - A política de disco BitLocker requer o consentimento do utilizador para iniciar o Assistente de criptografia de unidade do BitLocker para começar a encriptação do volume de sistema operacional, mas não autorizar o utilizador.  
   - O método de encriptação do volume de sistema operacional não corresponde a diretiva do BitLocker.  
   - A política de disco BitLocker requer um protetor de TPM proteger o volume do sistema operacional, mas não é utilizado um TPM.  
   - A diretiva do BitLocker requer um protetor de TPM apenas para o volume do sistema operacional, mas não é utilizada a proteção de TPM.  
   - A política de disco BitLocker requer a proteção de TPM + PIN para o volume do sistema operacional, mas não é utilizado um protetor de TPM + PIN.  
   - A política de disco BitLocker requer TPM + arranque chave proteção para o volume do sistema operacional, mas um TPM + protetor de chave de arranque não é utilizado.  
   - A política de disco BitLocker requer TPM + PIN + proteção de chaves de arranque para o volume do sistema operacional, mas um TPM + PIN + protetor de chave de arranque não é utilizado.  
   - O volume do sistema operacional é não protegido.  
   - Cópia de segurança de chave de recuperação falhou.  
   - Uma unidade fixa fica desprotegida.  
   - O método de encriptação da unidade fixa não corresponde a diretiva do BitLocker.  
   - Para encriptar unidades, a diretiva do BitLocker requer que o utilizador iniciar sessão como administrador ou, se o dispositivo estiver associado ao Azure AD, a política de AllowStandardUserEncryption deve ser definida como 1.  
   - Ambiente de recuperação do Windows (WinRE) não está configurado.  
   - Um TPM não está disponível para o BitLocker, porque ele não estiver presente, ele se tornou indisponível no Registro ou o sistema operacional estiver numa unidade removeable.  
   - O TPM não está preparado para o BitLocker.  
   - A rede não estiver disponível, que é necessário para o backup da chave de recuperação.  

## <a name="bitlocker-recovery-keys"></a>Chaves de recuperação do BitLocker
Como pré-visualização pública, o Intune fornece acesso o painel do Azure AD para o BitLocker, para que possa visualizar IDs de chave do BitLocker e chaves de recuperação para os seus dispositivos Windows 10, no portal do Intune.  Para ser acessível, o dispositivo tem de ter as chaves colocadas em caução em para o Azure AD. 
1. Inicie sessão no [Intune](https://aka.ms/intuneportal), aceda à **dispositivos** e, em *gerir*, selecione **todos os dispositivos**.
2. Selecione um dispositivo da lista e, em seguida, em *Monitor*, selecione **chaves de recuperação – pré-visualização**.  
  
Quando as chaves estão disponíveis no Azure AD, as seguintes informações estão disponíveis:
- ID da chave BitLocker
- Chave de recuperação do BitLocker
- Tipo de unidade  

Quando as chaves não estão no Azure AD, o Intune irá apresentar *chave do BitLocker não encontrado para este dispositivo*.  

Informações para o BitLocker são obtidas utilizando-o [fornecedor de serviços de configuração do BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) (CSP). BitLocker CSP é suportada no Windows 10 versão 1703 e posteriores e para o Windows 10 Pro versão 1809 e posterior. 

## <a name="next-steps"></a>Passos Seguintes
Criar uma [conformidade do dispositivo](compliance-policy-create-windows.md) política para dispositivos Windows 10 para configurar o BitLocker e encriptação.
