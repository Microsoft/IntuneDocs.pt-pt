---
title: Assinar e encriptar e-mails com o S/MIME – Microsoft Intune – Azure | Microsoft Docs
description: Saiba como utilizar certificados digitais de e-mail no Microsoft Intune para assinar e encriptar e-mails nos dispositivos. Estes certificados são chamados de S/MIME e estão configurados ao utilizar perfis de configuração do dispositivo. Certificados de assinatura e encriptação utilizam PKCS ou certificados privados e utilizam um conector para importar certificados.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/10/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: eee495e1294392e495a1f8f632fa33c37325a9dd
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842546"
---
# <a name="smime-overview-to-sign-and-encrypt-email-in-intune"></a>Descrição geral de S/MIME para assinar e encriptar o e-mail no Intune

Certificados de e-mail, também conhecido como certificado de S/MIME, fornecem segurança adicional para as comunicações de e-mail através de encriptação e desencriptação. Microsoft Intune pode utilizar certificados de S/MIME para assinar e encriptar e-mails para dispositivos móveis que executam as seguintes plataformas:

- Android
- iOS
- macOS
- Windows 10 e posterior
- Windows Phone

Em dispositivos iOS, pode criar um perfil de e-mail gerido pelo Intune que utiliza S/MIME e certificados para assinar e encriptar e-mails recebidos e enviados. Para outras plataformas, o protocolo S/MIME poderá ou não ser suportado. Caso seja suportado, instale certificados que utilizam encriptação e assinatura S/MIME. Em seguida, um utilizador final permite S/MIME na respetiva aplicação de e-mail.

Para obter mais informações sobre a assinatura de e-mail de S/MIME e encriptação com o Exchange, consulte [S/MIME para assinatura e encriptação](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).

Este artigo fornece uma descrição geral da utilização de certificados de S/MIME para assinar e encriptar e-mails nos seus dispositivos.

## <a name="signing-certificates"></a>Certificados de assinatura

Os certificados utilizados para assinatura permitem à aplicação de e-mail de cliente comunicar de forma segura com o servidor de e-mail.

Para utilizar certificados de assinatura, crie um modelo na sua autoridade de certificação (AC) que se concentra na assinatura. Relativamente à Autoridade de Certificação do Microsoft Active Directory, o artigo [Configure the server certificate template](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) (Configurar o modelo de certificado de servidor) inclui os passos para criar modelos de certificados.

Os certificados de assinatura no Intune utilizam certificados PKCS. O artigo [Configurar e utilizar certificados PKCS](certficates-pfx-configure.md) descreve como implementar e utilizar certificados PKCS no seu ambiente do Intune. Estes passos incluem:

- Transferir e instalar o Microsoft Intune Certificate Connector para suportar pedidos de certificados PKCS.
- Criar um perfil de certificado de raiz fidedigna para os seus dispositivos. Este passo inclui utilizar certificados de raiz fidedigna e intermédios para a sua autoridade de certificação e, em seguida, implementar o perfil nos dispositivos.
- Criar um perfil de certificado PKCS através de um modelo de certificado que criou. Este perfil emite certificados de assinatura para os dispositivos e implementa o perfil de certificado PKCS nos dispositivos.

Também pode importar um certificado de assinatura para um utilizador específico. O certificado de assinatura é implementado em qualquer dispositivo que um utilizador inscreve. Para importar certificados para o Intune, utilize os [cmdlets no PowerShell no GitHub](https://github.com/Microsoft/Intune-Resource-Access). Para implementar um certificado PKCS importado no Intune para ser utilizado para assinatura de e-mail, siga os passos em [Configurar e utilizar certificados PKCS com o Intune](certficates-pfx-configure.md). Estes passos incluem:

- Transferir e instalar o PFX Certificate Connector for Microsoft Intune. Este conector entrega certificados PKCS importados nos dispositivos.
- Importar certificados de assinatura de e-mail com S/MIME para o Intune.
- Criar um perfil de certificado PKCS importado. Este perfil entrega certificados PKCS importados nos dispositivos do utilizador adequado.

## <a name="encryption-certificates"></a>Certificados de encriptação

Os certificados utilizados para encriptação confirmam que um e-mail encriptado só pode ser desencriptado pelo destinatário especificado. A encriptação S/MIME é uma camada adicional de segurança que pode ser utilizada em comunicações de e-mail.

Ao enviar um e-mail encriptado para outro utilizador, a chave pública do certificado de encriptação desse utilizador é obtida e encripta o e-mail enviado. O destinatário desencripta o e-mail ao utilizar a chave privada no dispositivo. Os utilizadores podem ter um histórico dos certificados utilizados para encriptar e-mails. Cada um dos certificados tem de ser implementado em todos os dispositivos de um utilizador específico para que o e-mail seja desencriptado com êxito.

Recomenda-se que os certificados de encriptação de e-mail não sejam criados no Intune. Apesar de o Intune suportar certificados PKCS que suportem encriptação, o Intune cria um certificado exclusivo por dispositivo. Um certificado exclusivo por dispositivo não é ideal para um cenário de encriptação S/MIME em que o certificado de encriptação deveria ser partilhado em todos os dispositivos do utilizador.

Para implementar certificados S/MIME com o Intune, tem de importar todos os certificados de encriptação de um utilizador para o Intune. Intune, em seguida, implementa todos os certificados em cada dispositivo que um utilizador inscreve. Para importar certificados para o Intune, utilize os [cmdlets no PowerShell no GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Para implementar um certificado PKCS importado no Intune para ser utilizado para encriptação de e-mails, siga os passos em [Configurar e utilizar certificados PKCS com o Intune](certficates-pfx-configure.md). Estes passos incluem:

- Transferir e instalar o PFX Certificate Connector for Microsoft Intune. Este conector entrega certificados PKCS importados nos dispositivos.
- Importar certificados de encriptação de e-mails com S/MIME para o Intune.
- Criar um perfil de certificado PKCS importado. Este perfil entrega certificados PKCS importados nos dispositivos do utilizador adequado.

 > [!NOTE]
 > Os certificados de encriptação S/MIME importados são removidos pelo Intune quando os dados empresariais são removidos ou quando a inscrição dos utilizadores é removida da gestão. No entanto, os certificados não são revogados na autoridade de certificação.

## <a name="smime-email-profiles"></a>Perfis de e-mail com S/MIME

Após ter criado os perfis de certificado de encriptação e assinatura S/MIME, pode [ativar o S/MIME para o correio nativo de iOS](email-settings-ios.md).

## <a name="next-steps"></a>Passos Seguintes

- [Utilizar certificados SCEP](certificates-scep-configure.md)
- [Utilizar certificados PKCS](certficates-pfx-configure.md)
- [Utilize um parceiro da AC](certificate-authority-add-scep-overview.md)
- [Emitir certificados PKCS de uma PKI da Symantec serviço web manager](certificates-symantec-configure.md)
