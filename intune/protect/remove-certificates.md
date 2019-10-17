---
title: Remover certificados SCEP ou PKCS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Os administradores podem utilizar a ação de eliminação ou extinção para remover certificados do Microsoft Intune. Existem alguns cenários em que os certificados são removidos automaticamente, como anular a inscrição de um dispositivo ou remover uma política de conformidade. Existem alguns cenários em que os certificados permanecem automaticamente no dispositivo, como em caso de perda ou remoção da licença do Intune. Veja as diferentes formas para dispositivos Android, Android Enterprise, iOS, macOS e Windows.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/27/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.reviewer: lacranda
ms.openlocfilehash: e00600abb8327623eff4efe8509670779710ab7d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72509027"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Remover certificados SCEP e PKCS no Microsoft Intune

No Microsoft Intune, você pode usar os perfis de certificado SCEP (protocolo SCEP) e padrões de criptografia de chave pública (PKCS) para adicionar certificados a dispositivos.

Esses certificados podem ser removidos quando você [apaga](../remote-actions/devices-wipe.md#wipe) ou [desativa](../remote-actions/devices-wipe.md#retire) o dispositivo. Também há cenários em que os certificados são removidos automaticamente e cenários nos quais os certificados permanecem no dispositivo. Este artigo apresenta alguns cenários comuns e o impacto nos certificados PKCS e SCEP.

> [!NOTE]
> Para remover e revogar certificados para um usuário que está sendo removido do Active Directory local ou Azure Active Directory (AD do Azure), siga estas etapas na ordem:
>
> 1. Apagar ou desativar o dispositivo do usuário.
> 2. Remova o usuário do Active Directory local ou do Azure AD.

## <a name="manually-deleted-certificates"></a>Certificados excluídos manualmente

A exclusão manual de um certificado é um cenário que se aplica a várias plataformas e certificados provisionados por perfis de certificado SCEP ou PKCS. Por exemplo, um usuário pode excluir um certificado de um dispositivo, quando o dispositivo permanece direcionado por uma política de certificado.

Nesse cenário, depois que o certificado for excluído, na próxima vez que o dispositivo fizer check-in com o Intune, ele será considerado fora de conformidade, pois o certificado esperado está ausente. Em seguida, o Intune emite um novo certificado para restaurar o dispositivo para conformidade. Nenhuma ação adicional é necessária para restaurar o certificado.

## <a name="windows-devices"></a>Dispositivos Windows

### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:

- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .
- O dispositivo é removido de um grupo do Azure AD.
- Um perfil de certificado é removido da atribuição de grupo.

Um certificado SCEP é revogado quando:
- Um administrador altera ou atualiza o perfil SCEP.

Um certificado raiz é removido quando:
- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .

Os certificados SCEP *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:
- Um usuário perde a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o usuário ou grupo do Azure AD.

### <a name="pkcs-certificates"></a>Certificados PKCS

Um certificado SCEP é revogado *e* removido quando:

- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .

Um certificado raiz é removido quando:
- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .

Os certificados PKCS *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:
- Um usuário perde a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o usuário ou grupo do Azure AD.
- Um administrador altera ou atualiza o perfil PKCS.
- Um perfil de certificado é removido da atribuição de grupo.


## <a name="ios-devices"></a>Dispositivos iOS

### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:

- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .
- O dispositivo é removido do grupo do Azure AD.
- Um perfil de certificado é removido da atribuição de grupo.

Um certificado SCEP é revogado quando:
- Um administrador altera ou atualiza o perfil SCEP.

Um certificado raiz é removido quando:
- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .

Os certificados SCEP *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:
- Um usuário perde a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o usuário ou grupo do Azure AD.

### <a name="pkcs-certificates"></a>Certificados PKCS

Um certificado SCEP é revogado *e* removido quando:

- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .

Um certificado PKCS é removido quando:
- Um perfil de certificado é removido da atribuição de grupo.

Um certificado raiz é removido quando:
- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .

Os certificados PKCS *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:
- Um usuário perde a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o usuário ou grupo do Azure AD.
- Um administrador altera ou atualiza o perfil PKCS.

## <a name="android-knox-devices"></a>Dispositivos Android KNOX

### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:
- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .

Um certificado SCEP é revogado quando:
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .
- O dispositivo é removido de um grupo do Azure AD.
- Um perfil de certificado é removido da atribuição de grupo.
- Um administrador remove o usuário ou grupo do Azure AD.
- Um administrador altera ou atualiza o perfil SCEP.

Um certificado raiz é removido quando:
- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .

Os certificados SCEP *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:
- Um usuário perde a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o usuário ou grupo do Azure AD.

### <a name="pkcs-certificates"></a>Certificados PKCS

Um certificado SCEP é revogado *e* removido quando:

- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .

Um certificado raiz é removido quando:
- Um usuário cancela o registro.
- Um administrador executa a ação de [apagamento](../remote-actions/devices-wipe.md#wipe) .
- Um administrador executa a ação de [desativação](../remote-actions/devices-wipe.md#retire) .

Os certificados PKCS *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:
- Um usuário perde a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o usuário ou grupo do Azure AD.
- Um administrador altera ou atualiza o perfil PKCS.
- Um perfil de certificado é removido da atribuição de grupo.


> [!NOTE]
> Dispositivos Android for Work não são validados para os cenários anteriores.
> Dispositivos Android herdados (quaisquer dispositivos de perfil não Samsung, não de trabalho) não estão habilitados para remoção de certificado.

## <a name="macos-certificates"></a>Certificados macOS

### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:
- Um usuário cancela o registro.
- Um administrador executa uma ação de [desativação](../remote-actions/devices-wipe.md#retire) .
- O dispositivo é removido de um grupo do Azure AD.
- Um perfil de certificado é removido da atribuição de grupo.

Um certificado SCEP é revogado quando:
- Um administrador altera ou atualiza o perfil SCEP.

Os certificados SCEP *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:
- Um usuário perde a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o usuário ou grupo do Azure AD.

> [!NOTE]
> A utilização da ação de [eliminação](../remote-actions/devices-wipe.md#wipe) para efetuar a reposição de fábrica de dispositivos macOS não é suportada.

### <a name="pkcs-certificates"></a>Certificados PKCS

Não há suporte para certificados PKCS no macOS.

