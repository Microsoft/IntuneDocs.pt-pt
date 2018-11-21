---
title: Assinatura e encriptação de e-mail com S/MIME – Azure | Microsoft Docs
description: Utilizar ou ativar S/MIME para assinar e encriptar e-mails no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: eaa85870b289bb3b65ce997d8610324f43d69452
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52185649"
---
# <a name="smime-email-signing-and-encryption-in-intune"></a>Assinatura e encriptação de e-mail com S/MIME no Intune

> [!IMPORTANT]
> Estamos a fazer algumas melhorias à funcionalidade S/MIME descrita neste artigo. Por esse motivo, a funcionalidade S/MIME será removida temporariamente do Intune. Quando esta funcionalidade for lançada, iremos remover esta nota.

O protocolo S/MIME disponibiliza um nível de segurança adicional para as suas comunicações de e-mail ao utilizar encriptação e desencriptação. O Microsoft Intune pode utilizar S/MIME para assinar e encriptar e-mails para dispositivos móveis a executar iOS, Windows, Windows Phone, Android e macOS.

Em dispositivos iOS, pode criar um perfil de e-mail gerido pelo Intune que utiliza S/MIME e certificados para assinar e encriptar e-mails recebidos e enviados. Para outras plataformas, o protocolo S/MIME poderá ou não ser suportado. Se for suportado, pode instalar certificados que utilizam S/MIME para assinar e encriptar. Em seguida, um utilizador pode ativar o protocolo S/MIME na respetiva aplicação de e-mail.

Para mais informações acerca da encriptação e assinaturas de e-mail com S/MIME, veja [S/MIME for message signing and encryption](https://docs.microsoft.com/Exchange/policy-and-compliance/smime) (S/MIME para assinatura e encriptação de mensagens).

## <a name="signing-certificates"></a>Certificados de assinatura

Os certificados utilizados para assinatura permitem à aplicação de e-mail de cliente comunicar de forma segura com o servidor de e-mail.

Para utilizar certificados de assinatura, crie um modelo na sua autoridade de certificação que se concentre em assinaturas. Relativamente à Autoridade de Certificação do Microsoft Active Directory, o artigo [Configure the server certificate template](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) (Configurar o modelo de certificado de servidor) inclui os passos para criar modelos de certificados.

Os certificados de assinatura no Intune utilizam certificados PKCS. O artigo [Configurar e utilizar certificados PKCS](certficates-pfx-configure.md) descreve como implementar e utilizar certificados PKCS no seu ambiente do Intune. Estes passos incluem:

- Transferir e instalar o Microsoft Intune Certificate Connector para suportar pedidos de certificados PKCS.
- Criar um perfil de certificado de raiz fidedigna para os seus dispositivos. Este passo inclui utilizar certificados de raiz fidedigna e intermédios para a sua autoridade de certificação e, em seguida, implementar o perfil nos dispositivos.
- Criar um perfil de certificado PKCS através de um modelo de certificado que criou. Este perfil emite certificados de assinatura para os dispositivos e implementa o perfil de certificado PKCS nos dispositivos.

Também pode importar um certificado de assinatura para um utilizador específico. O certificado de assinatura é implementado em qualquer dispositivo que um utilizador inscreva. Para importar certificados para o Intune, utilize os [cmdlets no PowerShell no GitHub](https://github.com/Microsoft/Intune-Resource-Access). Para implementar um certificado PKCS importado no Intune para ser utilizado para assinatura de e-mail, siga os passos em [Configurar e utilizar certificados PKCS com o Intune](certficates-pfx-configure.md). Estes passos incluem:

- Transferir e instalar o PFX Certificate Connector for Microsoft Intune. Este conector entrega certificados PKCS importados nos dispositivos.
- Importar certificados de assinatura de e-mail com S/MIME para o Intune.
- Criar um perfil de certificado PKCS importado. Este perfil entrega certificados PKCS importados nos dispositivos do utilizador adequado.

## <a name="encryption-certificates"></a>Certificados de encriptação

Os certificados utilizados para encriptação confirmam que um e-mail encriptado só pode ser desencriptado pelo destinatário especificado. A encriptação S/MIME é uma camada adicional de segurança que pode ser utilizada em comunicações de e-mail.

Ao enviar um e-mail encriptado para outro utilizador, a chave pública do certificado de encriptação desse utilizador é obtida e encripta o e-mail enviado. O destinatário desencripta o e-mail ao utilizar a chave privada no dispositivo. Os utilizadores podem ter um histórico dos certificados utilizados para encriptar e-mails. Cada um dos certificados tem de ser implementado em todos os dispositivos de um utilizador específico para que o e-mail seja desencriptado com êxito.

Recomenda-se que os certificados de encriptação de e-mail não sejam criados no Intune. Apesar de o Intune suportar certificados PKCS que suportem encriptação, o Intune cria um certificado exclusivo por dispositivo. Um certificado exclusivo por dispositivo não é ideal para um cenário de encriptação S/MIME em que o certificado de encriptação deveria ser partilhado em todos os dispositivos do utilizador.

Para implementar certificados S/MIME com o Intune, tem de importar todos os certificados de encriptação de um utilizador para o Intune. Em seguida, o Intune implementa esses certificados em cada dispositivo que o utilizador inscrever. Para importar certificados para o Intune, utilize os [cmdlets no PowerShell no GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Para implementar um certificado PKCS importado no Intune para ser utilizado para encriptação de e-mails, siga os passos em [Configurar e utilizar certificados PKCS com o Intune](certficates-pfx-configure.md). Estes passos incluem:

- Transferir e instalar o PFX Certificate Connector for Microsoft Intune. Este conector entrega certificados PKCS importados nos dispositivos.
- Importar certificados de encriptação de e-mails com S/MIME para o Intune.
- Criar um perfil de certificado PKCS importado. Este perfil entrega certificados PKCS importados nos dispositivos do utilizador adequado.

 > [!NOTE]
 > Os certificados de encriptação S/MIME importados são removidos pelo Intune quando os dados empresariais são removidos ou quando a inscrição dos utilizadores é removida da gestão. No entanto, os certificados não são revogados na autoridade de certificação.

## <a name="smime-email-profiles"></a>Perfis de e-mail com S/MIME

Após ter criado os perfis de certificado de encriptação e assinatura S/MIME, pode [ativar o S/MIME para o correio nativo de iOS](email-settings-ios.md).