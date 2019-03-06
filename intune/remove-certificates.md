---
title: Remover certificados SCEP ou PKCS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Os administradores podem utilizar a ação de eliminação ou extinção para remover certificados do Microsoft Intune. Existem alguns cenários em que os certificados são removidos automaticamente, como anular a inscrição de um dispositivo ou remover uma política de conformidade. Existem alguns cenários em que os certificados permanecem automaticamente no dispositivo, como em caso de perda ou remoção da licença do Intune. Veja as diferentes formas para dispositivos Android, Android Enterprise, iOS, macOS e Windows.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 01/08/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e19df00a829d0cedb22210cd0ebe6b48c55229fe
ms.sourcegitcommit: 430b290474b11f9df87785b01edc178e6bae2049
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/05/2019
ms.locfileid: "57392735"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Remover certificados SCEP e PKCS no Microsoft Intune

No Microsoft Intune, pode adicionar certificados Simple Certificate Enrollment Protocol (SCEP) e padrões de criptografia de chave pública (PKCS) para dispositivos. Estes certificados também podem ser removidos ao [eliminar](devices-wipe.md#wipe) ou [extinguir](devices-wipe.md#retire) o dispositivo. 

Existem alguns cenários em que os certificados são removidos automaticamente e outros em que os certificados permanecem no dispositivo. Este artigo apresenta alguns cenários comuns e o impacto nos certificados PKCS e SCEP.

> [!NOTE]
> Para remover e revogar certificados para um utilizador que está a ser removido do local do Active Directory ou no Azure Active Directory (Azure AD), siga estes passos por ordem:
>
> 1. Apagar ou extinguir o dispositivo do utilizador.
> 2. Remova o utilizador do Active Directory no local ou do Azure AD.

## <a name="windows-devices"></a>Dispositivos Windows

#### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.
- O dispositivo é removido de um grupo do Azure AD.
- Um perfil de certificado é removido da atribuição de grupo.

Um certificado SCEP é revogado quando:
- Um administrador for alterado ou atualiza o perfil SCEP.

Um certificado de raiz é removido quando:
- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.

Certificados SCEP *permanecer* no dispositivo (certificados não revogados ou removidos) quando:
- Um utilizador perder a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o utilizador ou grupo do Azure AD.

#### <a name="pkcs-certificates"></a>Certificados PKCS

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.

Um certificado de raiz é removido quando:
- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.

Certificados PKCS *permanecer* no dispositivo (certificados não revogados ou removidos) quando:
- Um utilizador perder a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o utilizador ou grupo do Azure AD.
- Um administrador for alterado ou atualiza o perfil PKCS.
- Um perfil de certificado é removido da atribuição de grupo.


## <a name="ios-devices"></a>Dispositivos iOS

#### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.
- O dispositivo é removido do grupo do Azure AD.
- Um perfil de certificado é removido da atribuição de grupo.

Um certificado SCEP é revogado quando:
- Um administrador for alterado ou atualiza o perfil SCEP.

Um certificado de raiz é removido quando:
- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.

Certificados SCEP *permanecer* no dispositivo (certificados não revogados ou removidos) quando:
- Um utilizador perder a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o utilizador ou grupo do Azure AD.

#### <a name="pkcs-certificates"></a>Certificados PKCS

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.

Um certificado PKCS é removido quando:
- Um perfil de certificado é removido da atribuição de grupo.
  
Um certificado de raiz é removido quando:
- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.

Certificados PKCS *permanecer* no dispositivo (certificados não revogados ou removidos) quando:
- Um utilizador perder a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o utilizador ou grupo do Azure AD.
- Um administrador for alterado ou atualiza o perfil PKCS.

## <a name="android-knox-devices"></a>Dispositivos Android KNOX

#### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:
- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.

Um certificado SCEP é revogado quando:
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.
- O dispositivo é removido de um grupo do Azure AD.
- Um perfil de certificado é removido da atribuição de grupo.
- Um administrador remove o utilizador ou grupo do Azure AD.
- Um administrador for alterado ou atualiza o perfil SCEP.

Um certificado de raiz é removido quando:
- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.

Certificados SCEP *permanecer* no dispositivo (certificados não revogados ou removidos) quando:
- Um utilizador perder a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o utilizador ou grupo do Azure AD.

#### <a name="pkcs-certificates"></a>Certificados PKCS

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.

Um certificado de raiz é removido quando:
- Um utilizador anular a inscrição.
- Um administrador executa o [apagar](devices-wipe.md#wipe) ação.
- Um administrador executa o [extinguir](devices-wipe.md#retire) ação.

Certificados PKCS *permanecer* no dispositivo (certificados não revogados ou removidos) quando:
- Um utilizador perder a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o utilizador ou grupo do Azure AD.
- Um administrador for alterado ou atualiza o perfil PKCS.
- Um perfil de certificado é removido da atribuição de grupo.
  
  
> [!NOTE]
> Dispositivos Android for Work não são validadas para os cenários anteriores. Android dispositivos legados (qualquer não Samsung, dispositivos de perfil de descanso) não estão ativados para remoção de certificado. 

## <a name="macos-certificates"></a>Certificados macOS

#### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:
- Um utilizador anular a inscrição.
- Um administrador executa um [extinguir](devices-wipe.md#retire) ação.
- O dispositivo é removido de um grupo do Azure AD.
- Um perfil de certificado é removido da atribuição de grupo.

Um certificado SCEP é revogado quando:
- Um administrador for alterado ou atualiza o perfil SCEP.

Certificados SCEP *permanecer* no dispositivo (certificados não revogados ou removidos) quando:
- Um utilizador perder a licença do Intune.
- Um administrador retira a licença do Intune.
- Um administrador remove o utilizador ou grupo do Azure AD.

> [!NOTE]
> A utilização da ação de [eliminação](devices-wipe.md#wipe) para efetuar a reposição de fábrica de dispositivos macOS não é suportada.

#### <a name="pkcs-certificates"></a>Certificados PKCS

Os certificados PKCS não são suportados no macOS.

