---
title: Remover certificados SCEP ou PKCS no Microsoft Intune – Azure | Microsoft Docs
titleSuffix: ''
description: Os administradores podem utilizar a ação de eliminação ou extinção para remover certificados do Microsoft Intune. Existem alguns cenários em que os certificados são removidos automaticamente, como anular a inscrição de um dispositivo ou remover uma política de conformidade. Existem alguns cenários em que os certificados permanecem automaticamente no dispositivo, como em caso de perda ou remoção da licença do Intune. Veja as diferentes formas para dispositivos Android, Android Enterprise, iOS, macOS e Windows.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a823ea2f04d8e3a8f1ca5a2f1364060840686501
ms.sourcegitcommit: 2e6851a5c1f934dcdb3f854d8462a4d23cc0453b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561946"
---
# <a name="remove-scep-and-pkcs-certificates-in-microsoft-intune"></a>Remover certificados SCEP e PKCS no Microsoft Intune

No Microsoft Intune, pode adicionar certificados SCEP e PKCS a dispositivos. Estes certificados também podem ser removidos ao [eliminar](devices-wipe.md#wipe) ou [extinguir](devices-wipe.md#retire) o dispositivo. Existem alguns cenários em que os certificados são removidos automaticamente e outros em que os certificados permanecem no dispositivo.

Este artigo apresenta alguns cenários comuns e o impacto nos certificados PKCS e SCEP.

> [!NOTE]
> Para remover e revogar certificados de um utilizador que está a ser removido do Active Directory (AD) ou do Azure AD, certifique-se de que segue os passos por ordem:
>
>    1. Elimine ou extinga o dispositivo do utilizador
>    2. Remova o utilizador do AD ou do Azure AD

## <a name="windows-devices"></a>Dispositivos Windows

#### <a name="scep-certificates"></a>Certificados SCEP

- Um certificado SCEP é revogado *e* removido quando:

  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)
  - O dispositivo é removido do grupo do Azure Active Directory (AD)
  - A política de conformidade é removida da atribuição de grupo
  - O perfil de configuração é removido da atribuição de grupo

- Um certificado SCEP é revogado quando:
  - O administrador altera ou atualiza o perfil SCEP

- O certificado de raiz é removido quando:
  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)
  - A política de conformidade é removida da atribuição de grupo

- Os certificados SCEP **permanecem** no dispositivo (os certificados não são revogados nem removidos) quando:
  - Um utilizador final perde a licença do Intune
  - O administrador retira a licença do Intune
  - O administrador remove o utilizador ou o grupo do Azure AD

#### <a name="pkcs-certificates"></a>Certificados PKCS

- Um certificado SCEP é revogado *e* removido quando:

  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)

- O certificado de raiz é removido quando:
  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)

- Os certificados PKCS **permanecem** no dispositivo (os certificados não são revogados nem removidos) quando:
  - Um utilizador final perde a licença do Intune
  - O administrador retira a licença do Intune
  - O administrador remove o utilizador ou o grupo do Azure AD
  - O administrador altera ou atualiza o perfil PKCS
  - O perfil de configuração é removido da atribuição de grupo
  - A política de conformidade é removida da atribuição de grupo 


## <a name="ios-devices"></a>Dispositivos iOS

#### <a name="scep-certificates"></a>Certificados SCEP

- Um certificado SCEP é revogado *e* removido quando:

  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)
  - O dispositivo é removido do grupo do Azure Active Directory (AD)
  - A política de conformidade é removida da atribuição de grupo
  - O perfil de configuração é removido da atribuição de grupo

- Um certificado SCEP é revogado quando:
  - O administrador altera ou atualiza o perfil SCEP

- O certificado de raiz é removido quando:
  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)
  - A política de conformidade é removida da atribuição de grupo

- Os certificados SCEP **permanecem** no dispositivo (os certificados não são revogados nem removidos) quando:
  - Um utilizador final perde a licença do Intune
  - O administrador retira a licença do Intune
  - O administrador remove o utilizador ou o grupo do Azure AD

#### <a name="pkcs-certificates"></a>Certificados PKCS

- Um certificado SCEP é revogado *e* removido quando:

  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)

- Um certificado PKCS é removido quando:
  - A política de conformidade é removida da atribuição de grupo
  - O perfil de configuração é removido da atribuição de grupo
  
- O certificado de raiz é removido quando:
  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)

- Os certificados PKCS **permanecem** no dispositivo (os certificados não são revogados nem removidos) quando:
  - Um utilizador final perde a licença do Intune
  - O administrador retira a licença do Intune
  - O administrador remove o utilizador ou o grupo do Azure AD
  - O administrador altera ou atualiza o perfil PKCS

## <a name="android-knox-devices"></a>Dispositivos Android KNOX

#### <a name="scep-certificates"></a>Certificados SCEP

- Um certificado SCEP é revogado *e* removido quando:
  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)

- Um certificado SCEP é revogado quando:
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)
  - O dispositivo é removido do grupo do Azure Active Directory (AD)
  - A política de conformidade é removida da atribuição de grupo
  - O perfil de configuração é removido da atribuição de grupo
  - O administrador remove o utilizador ou o grupo do Azure Active Directory (AD)
  - O administrador altera ou atualiza o perfil SCEP

- O certificado de raiz é removido quando:
  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)

- Os certificados SCEP **permanecem** no dispositivo (os certificados não são revogados nem removidos) quando:
  - Um utilizador final perde a licença do Intune
  - O administrador retira a licença do Intune
  - O administrador remove o utilizador ou o grupo do Azure AD

#### <a name="pkcs-certificates"></a>Certificados PKCS

- Um certificado SCEP é revogado *e* removido quando:

  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)

- O certificado de raiz é removido quando:
  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [eliminação](devices-wipe.md#wipe)
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)

- Os certificados PKCS **permanecem** no dispositivo (os certificados não são revogados nem removidos) quando:
  - Um utilizador final perde a licença do Intune
  - O administrador retira a licença do Intune
  - O administrador remove o utilizador ou o grupo do Azure AD
  - O administrador altera ou atualiza o perfil PKCS
  - O perfil de configuração é removido da atribuição de grupo
  - A política de conformidade é removida da atribuição de grupo 
  
  
> [!NOTE]
> Os dispositivos Android for Work não estão validados para os cenários indicados acima. Os dispositivos legados Android (qualquer dispositivo com um perfil não profissional que não seja da Samsung) não permitem a remoção de certificados. 

## <a name="macos-certificates"></a>Certificados macOS

#### <a name="scep-certificates"></a>Certificados SCEP

- Um certificado SCEP é revogado *e* removido quando:
  - Um utilizador final anula a inscrição
  - O administrador executa a ação de [extinção](devices-wipe.md#retire)
  - O dispositivo é removido do grupo do Azure Active Directory (AD)
  - A política de conformidade é removida da atribuição de grupo
  - O perfil de configuração é removido da atribuição de grupo

- Um certificado SCEP é revogado quando:
  - O administrador altera ou atualiza o perfil SCEP

- Os certificados SCEP **permanecem** no dispositivo (os certificados não são revogados nem removidos) quando:
  - Um utilizador final perde a licença do Intune
  - O administrador retira a licença do Intune
  - O administrador remove o utilizador ou o grupo do Azure AD

> [!NOTE]
> A utilização da ação de [eliminação](devices-wipe.md#wipe) para efetuar a reposição de fábrica de dispositivos macOS não é suportada.

#### <a name="pkcs-certificates"></a>Certificados PKCS

Os certificados PKCS não são suportados no macOS.

