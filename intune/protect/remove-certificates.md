---
title: Remover certificados SCEP ou PKCS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Os administradores podem utilizar a ação de eliminação ou extinção para remover certificados do Microsoft Intune. Existem alguns cenários em que os certificados são removidos automaticamente, como anular a inscrição de um dispositivo ou remover uma política de conformidade. Existem alguns cenários em que os certificados permanecem automaticamente no dispositivo, como em caso de perda ou remoção da licença do Intune. Veja as diferentes formas para dispositivos Android, Android Enterprise, iOS/iPadOS, macOS e Windows.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/21/2019
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
ms.openlocfilehash: a77780c05b0f637a4ee5100f8c7a1a729c3ec674
ms.sourcegitcommit: 47c9af81c385c7e893fe5a85eb79cf08e69e6831
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77576261"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Remover certificados SCEP e PKCS no Microsoft Intune

No Microsoft Intune, pode utilizar os perfis de certificados simples de inscrição de certificados (SCEP) e de Padrões de Criptografia de Chaves Públicas (PKCS) para adicionar certificados aos dispositivos.

Estes certificados podem ser removidos quando [limpa](../remote-actions/devices-wipe.md#wipe) ou [retira](../remote-actions/devices-wipe.md#retire) o dispositivo. Há também cenários em que os certificados são automaticamente removidos, e cenários em que os certificados permanecem no dispositivo. Este artigo apresenta alguns cenários comuns e o impacto nos certificados PKCS e SCEP.

> [!NOTE]
> Para remover e revogar os certificados para um utilizador que está a ser removido do Diretório Ativo ou azure Ative Directory (Azure AD), siga estes passos por ordem:
>
> 1. Limpe ou retire o dispositivo do utilizador.
> 2. Retire o utilizador do Diretório Ativo ou Azure AD no local.

## <a name="manually-deleted-certificates"></a>Certificados manualmente eliminados

A eliminação manual de um certificado é um cenário que se aplica entre plataformas e certificados previstos nos perfis de certificados SCEP ou PKCS. Por exemplo, um utilizador pode apagar um certificado de um dispositivo, quando o dispositivo permanece alvo de uma política de certificado.

Neste cenário, após a eliminação do certificado, da próxima vez que o dispositivo verificar com o Intune, verifica-se que está fora de conformidade, uma vez que está a faltar o certificado esperado. Intune emite então um novo certificado para restaurar o dispositivo em conformidade. Não são necessárias medidas adicionais para restaurar o certificado.

## <a name="windows-devices"></a>Dispositivos Windows

### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)
- O dispositivo é removido de um grupo Azure AD.
- Um perfil de certificado é removido da atribuição do grupo.

Um certificado SCEP é revogado quando:

- Um administrador altera ou atualiza o perfil SCEP.

Um certificado de raiz é removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)

Os certificados SCEP *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:

- Um utilizador perde a licença Intune.
- Um administrador retira a licença Intune.
- Um administrador remove o utilizador ou grupo da Azure AD.

### <a name="pkcs-certificates"></a>Certificados PKCS

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)

Um certificado de raiz é removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)

Os certificados PKCS *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:

- Um utilizador perde a licença Intune.
- Um administrador retira a licença Intune.
- Um administrador remove o utilizador ou grupo da Azure AD.
- Um administrador altera ou atualiza o perfil PKCS.
- Um perfil de certificado é removido da atribuição do grupo.


## <a name="ios-devices"></a>Dispositivos iOS

### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)
- O dispositivo é removido do grupo Azure AD.
- Um perfil de certificado é removido da atribuição do grupo.

Um certificado SCEP é revogado quando:

- Um administrador altera ou atualiza o perfil SCEP.

Um certificado de raiz é removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)

Os certificados SCEP *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:

- Um utilizador perde a licença Intune.
- Um administrador retira a licença Intune.
- Um administrador remove o utilizador ou grupo da Azure AD.

### <a name="pkcs-certificates"></a>Certificados PKCS

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)

Um certificado PKCS é removido quando:

- Um perfil de certificado é removido da atribuição do grupo.

Um certificado de raiz é removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)

Os certificados PKCS *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:

- Um utilizador perde a licença Intune.
- Um administrador retira a licença Intune.
- Um administrador remove o utilizador ou grupo da Azure AD.
- Um administrador altera ou atualiza o perfil PKCS.

## <a name="android-knox-devices"></a>Dispositivos Android KNOX

### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)

Um certificado SCEP é revogado quando:

- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)
- O dispositivo é removido de um grupo Azure AD.
- Um perfil de certificado é removido da atribuição do grupo.
- Um administrador remove o utilizador ou grupo da Azure AD.
- Um administrador altera ou atualiza o perfil SCEP.

Um certificado de raiz é removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)

Os certificados SCEP *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:

- Um utilizador perde a licença Intune.
- Um administrador retira a licença Intune.
- Um administrador remove o utilizador ou grupo da Azure AD.

### <a name="pkcs-certificates"></a>Certificados PKCS

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)

Um certificado de raiz é removido quando:

- Um utilizador não se matricula.
- Um administrador dirige a ação de [limpeza.](../remote-actions/devices-wipe.md#wipe)
- Um administrador dirige a ação de [aposentadoria.](../remote-actions/devices-wipe.md#retire)

Os certificados PKCS *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:
- Um utilizador perde a licença Intune.

- Um administrador retira a licença Intune.
- Um administrador remove o utilizador ou grupo da Azure AD.
- Um administrador altera ou atualiza o perfil PKCS.
- Um perfil de certificado é removido da atribuição do grupo.


> [!NOTE]
> Os dispositivos Android for Work não são validados para os cenários anteriores.
> Os dispositivos legados Android (quaisquer dispositivos não Samsung e não-work) não estão habilitados para a remoção de certificados.

## <a name="macos-certificates"></a>Certificados macOS

### <a name="scep-certificates"></a>Certificados SCEP

Um certificado SCEP é revogado *e* removido quando:

- Um utilizador não se matricula.
- Um administrador dirige uma ação [de aposentadoria.](../remote-actions/devices-wipe.md#retire)
- O dispositivo é removido de um grupo Azure AD.
- Um perfil de certificado é removido da atribuição do grupo.

Um certificado SCEP é revogado quando:

- Um administrador altera ou atualiza o perfil SCEP.

Os certificados SCEP *permanecem* no dispositivo (os certificados não são revogados ou removidos) quando:

- Um utilizador perde a licença Intune.
- Um administrador retira a licença Intune.
- Um administrador remove o utilizador ou grupo da Azure AD.

> [!NOTE]
> A utilização da ação de [eliminação](../remote-actions/devices-wipe.md#wipe) para efetuar a reposição de fábrica de dispositivos macOS não é suportada.

### <a name="pkcs-certificates"></a>Certificados PKCS

Os certificados PKCS não são suportados no macOS.

## <a name="next-steps"></a>Próximos passos

[Utilizar certificados para autenticação](certificates-configure.md)