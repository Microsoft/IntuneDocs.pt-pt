---
title: Assinar e criptografar email usando S/MIME-Microsoft Intune-Azure | Microsoft Docs
description: Saiba como usar certificados digitais de email no Microsoft Intune para assinar e criptografar emails em dispositivos. Esses certificados são chamados S/MIME e são configurados usando perfis de configuração de dispositivo. Certificados de assinatura e criptografia usam certificados PKCS ou privados e usam um conector para importar certificados.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/10/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure; seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7b16953b3402bf8aa48f0a01e5e11d9f90d56f2d
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72502499"
---
# <a name="smime-overview-to-sign-and-encrypt-email-in-intune"></a>Visão geral de S/MIME para assinar e criptografar email no Intune

Os certificados de email, também conhecidos como certificado S/MIME, fornecem segurança extra para suas comunicações por email usando criptografia e descriptografia. Microsoft Intune pode usar certificados S/MIME para assinar e criptografar emails para dispositivos móveis que executam as seguintes plataformas:

- Android
- iOS
- macOS
- Windows 10 e posterior
- Windows Phone

Em dispositivos iOS, pode criar um perfil de e-mail gerido pelo Intune que utiliza S/MIME e certificados para assinar e encriptar e-mails recebidos e enviados. Para outras plataformas, o protocolo S/MIME poderá ou não ser suportado. Se houver suporte, instale os certificados que usam assinatura e criptografia S/MIME. Em seguida, um usuário final habilita S/MIME em seu aplicativo de email.

Para obter mais informações sobre assinatura e criptografia de email S/MIME com o Exchange, consulte [s/MIME para assinatura e criptografia de mensagens](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).

Este artigo fornece uma visão geral do uso de certificados S/MIME para assinar e criptografar emails em seus dispositivos.

## <a name="signing-certificates"></a>Certificados de assinatura

Os certificados utilizados para assinatura permitem à aplicação de e-mail de cliente comunicar de forma segura com o servidor de e-mail.

Para usar certificados de assinatura, crie um modelo na sua autoridade de certificação (CA) que se concentre na assinatura. Relativamente à Autoridade de Certificação do Microsoft Active Directory, o artigo [Configure the server certificate template](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) (Configurar o modelo de certificado de servidor) inclui os passos para criar modelos de certificados.

Os certificados de assinatura no Intune utilizam certificados PKCS. O artigo [Configurar e utilizar certificados PKCS](certficates-pfx-configure.md) descreve como implementar e utilizar certificados PKCS no seu ambiente do Intune. Essas etapas incluem:

- Transferir e instalar o Microsoft Intune Certificate Connector para suportar pedidos de certificados PKCS.
- Criar um perfil de certificado de raiz fidedigna para os seus dispositivos. Este passo inclui utilizar certificados de raiz fidedigna e intermédios para a sua autoridade de certificação e, em seguida, implementar o perfil nos dispositivos.
- Criar um perfil de certificado PKCS através de um modelo de certificado que criou. Este perfil emite certificados de assinatura para os dispositivos e implementa o perfil de certificado PKCS nos dispositivos.

Também pode importar um certificado de assinatura para um utilizador específico. O certificado de autenticação é implantado em qualquer dispositivo registrado pelo usuário. Para importar certificados para o Intune, utilize os [cmdlets no PowerShell no GitHub](https://github.com/Microsoft/Intune-Resource-Access). Para implementar um certificado PKCS importado no Intune para ser utilizado para assinatura de e-mail, siga os passos em [Configurar e utilizar certificados PKCS com o Intune](certficates-pfx-configure.md). Essas etapas incluem:

- Transferir e instalar o PFX Certificate Connector for Microsoft Intune. Este conector entrega certificados PKCS importados nos dispositivos.
- Importar certificados de assinatura de e-mail com S/MIME para o Intune.
- Criar um perfil de certificado PKCS importado. Este perfil entrega certificados PKCS importados nos dispositivos do utilizador adequado.

## <a name="encryption-certificates"></a>Certificados de encriptação

Os certificados utilizados para encriptação confirmam que um e-mail encriptado só pode ser desencriptado pelo destinatário especificado. A encriptação S/MIME é uma camada adicional de segurança que pode ser utilizada em comunicações de e-mail.

Ao enviar um e-mail encriptado para outro utilizador, a chave pública do certificado de encriptação desse utilizador é obtida e encripta o e-mail enviado. O destinatário desencripta o e-mail ao utilizar a chave privada no dispositivo. Os utilizadores podem ter um histórico dos certificados utilizados para encriptar e-mails. Cada um dos certificados tem de ser implementado em todos os dispositivos de um utilizador específico para que o e-mail seja desencriptado com êxito.

Recomenda-se que os certificados de encriptação de e-mail não sejam criados no Intune. Apesar de o Intune suportar certificados PKCS que suportem encriptação, o Intune cria um certificado exclusivo por dispositivo. Um certificado exclusivo por dispositivo não é ideal para um cenário de encriptação S/MIME em que o certificado de encriptação deveria ser partilhado em todos os dispositivos do utilizador.

Para implementar certificados S/MIME com o Intune, tem de importar todos os certificados de encriptação de um utilizador para o Intune. Em seguida, o Intune implanta todos esses certificados em cada dispositivo registrado por um usuário. Para importar certificados para o Intune, utilize os [cmdlets no PowerShell no GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Para implementar um certificado PKCS importado no Intune para ser utilizado para encriptação de e-mails, siga os passos em [Configurar e utilizar certificados PKCS com o Intune](certficates-pfx-configure.md). Essas etapas incluem:

- Transferir e instalar o PFX Certificate Connector for Microsoft Intune. Este conector entrega certificados PKCS importados nos dispositivos.
- Importar certificados de encriptação de e-mails com S/MIME para o Intune.
- Criar um perfil de certificado PKCS importado. Este perfil entrega certificados PKCS importados nos dispositivos do utilizador adequado.

 > [!NOTE]
 > Os certificados de encriptação S/MIME importados são removidos pelo Intune quando os dados empresariais são removidos ou quando a inscrição dos utilizadores é removida da gestão. No entanto, os certificados não são revogados na autoridade de certificação.

## <a name="smime-email-profiles"></a>Perfis de e-mail com S/MIME

Após ter criado os perfis de certificado de encriptação e assinatura S/MIME, pode [ativar o S/MIME para o correio nativo de iOS](../configuration/email-settings-ios.md).

## <a name="next-steps"></a>Próximos passos

- [Usar SCEP para certificados](certificates-scep-configure.md)
- [Usar certificados PKCS](certficates-pfx-configure.md)
- [Usar uma autoridade de certificação do parceiro](certificate-authority-add-scep-overview.md)
- [Emitir certificados PKCS de um serviço Web do Symantec PKI Manager](certificates-digicert-configure.md)
