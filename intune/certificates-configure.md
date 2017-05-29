---
title: Como configurar certificados com o Intune | Microsoft Docs
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como utilizar o Intune para criar e atribuir certificados que o ajudam a proteger ligações Wi-Fi, VPN, entre outras."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.date: 05/02/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.translationtype: Human Translation
ms.sourcegitcommit: 9ff1adae93fe6873f5551cf58b1a2e89638dee85
ms.openlocfilehash: 81c7e04d4b4cc7599b63917e5507775b38b65ba7
ms.contentlocale: pt-pt
ms.lasthandoff: 05/23/2017


---

# <a name="how-to-configure-certificates-in-microsoft-intune"></a>Como configurar certificados no Microsoft Intune

[!INCLUDE[azure_preview](./includes/azure_preview.md)]

Quando conceder aos utilizadores acesso aos recursos da empresa através de VPN, Wi-Fi ou perfis de e-mail, pode autenticar estas ligações ao utilizar certificados. Desta foram, deixa de precisar introduzir os nomes de utilizador e as palavras-passe para autenticar as ligações.

Pode utilizar o Intune para atribuir estes certificados aos dispositivos que gere. O Intune suporta a atribuição e a gestão destes tipos de certificado:

- Protocolo SCEP (Simple Certificate Enrollment Protocol)
- PKCS#12 (ou PFX)

Cada um destes tipos de certificado tem os seus próprios pré-requisitos e requisitos de infraestrutura.

## <a name="general-workflow"></a>Fluxo de trabalho geral

1. Confirme que tem aplicada a infraestrutura de certificado correta. Pode utilizar [certificados SCEP](certificates-scep-configure.md) e [certificados PKCS](certficates-pfx-configure.md).
2. Instale um certificado de raiz ou um certificado de Autoridade de Certificação (AC) intermediária em cada dispositivo, para que estes reconheçam a legitimidade da sua AC. Para tal, crie e implemente um **perfil de certificado fidedigno**. Ao atribuir este perfil, os dispositivos que gere com o Intune vão pedir e receber o certificado de raiz. Tem de criar um perfil separado para cada plataforma. Os perfis de certificado fidedigno estão disponíveis para estas plataformas:
    - iOS 8.0 e posterior
    - macOS 10.9 e posterior
    - Android 4.0 e posterior
    - Android for Work
    - Windows 8.1 e posterior
    - Windows Phone 8.1 e posterior
    - Windows 10 e posterior
3. Crie perfis de certificados para que os dispositivos solicitem a utilização de um certificado para autenticação do acesso a VPN, Wi-Fi e e-mail. Pode criar e atribuir um perfil de certificado **PKCS** ou **SCEP** a dispositivos com as seguintes plataformas:
    - iOS 8.0 e posterior
    - Android 4.0 e posterior
    - Android for Work
    - Windows 10 (para Computadores e Dispositivos Móveis) e posterior

    Apenas pode utilizar um perfil de certificado SCEP com estas plataformas:

-     macOS 10.9 e posterior
-     Windows Phone 8.1 e posterior

Tem de criar um perfil separado para cada plataforma de dispositivo. Ao criar o perfil, associe-o ao perfil de certificado de raiz fidedigna criado.

### <a name="further-considerations"></a>Considerações adicionais

- Se não tiver uma Autoridade de Certificação Empresarial, tem de criar uma.
- Se decidir, com base nas suas plataformas de dispositivos, utilizar o perfil de protocolo SCEP (Simple Certificate Enrollment Protocol), terá também de configurar um servidor do Serviço de Inscrição de Dispositivos de Rede (NDES).
- Se planear utilizar os perfis SCEP ou PKCS, terá de transferir e configurar o Microsoft Intune Certificate Connector.


## <a name="step-1--configure-your-certificate-infrastructure"></a>Passo 1 – Configurar a infraestrutura de certificados

Veja um dos seguintes tópicos para ajudar a configurar a infraestrutura para cada tipo de perfil de certificado:

- [Configurar e gerir certificados SCEP com o Intune](certificates-scep-configure.md)
- [Configurar e gerir certificados PKCS com o Intune](certficates-pfx-configure.md)


## <a name="step-2---export-your-trusted-root-ca-certificate"></a>Passo 2 – Exportar o certificado da AC de raiz confiável

Exporte o certificado de Autoridades de Certificação(AC) de Raiz Fidedigna como um ficheiro **.cer** a partir da AC emissora ou de qualquer dispositivo que confie na sua AC emissora. Não exporte a chave privada.

Irá importar este certificado quando configurar um perfil de certificado Fidedigno.

## <a name="step-3-create-trusted-certificate-profiles"></a>Passo 3 – Criar perfis de certificado fidedigno
Tem de criar um perfil de certificado fidedigno para poder criar um perfil de certificado SCEP ou PKCS. Precisa de um perfil de certificado fidedigno e de um perfil SCEP ou PKCS para cada plataforma de dispositivo. O fluxo para a criação de certificados fidedignos é semelhante para cada plataforma de dispositivo.

### <a name="to-create-a-trusted-certificate-profile"></a>Para criar um perfil de certificado fidedigno

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de certificado fidedigno.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado fidedigno. Atualmente, pode escolher uma das seguintes plataformas para as definições de certificados:
    - **Android**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**
6. Na lista pendente **Tipo de perfil**, escolha **Certificado fidedigno**.
7. Navegue para o certificado guardado na tarefa 1 e, em seguida, clique em **OK**.
8. Apenas para os dispositivos Windows 8.1 e Windows 10, selecione o **Arquivo de Destino** do certificado fidedigno em:
    - **Arquivo de certificados no computador – Raiz**
    - **Arquivo de certificados no computador – Intermédio**
    - **Armazenamento de certificados de utilizador – Intermédio**
8. Quando tiver terminado, escolha **OK**, volte ao painel **Criar Perfil** e clique em **Criar**.

O perfil será criado e é apresentado no painel da lista de perfis.

Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).


> [!Note]
> Os dispositivos Android apresentarão um aviso a indicar que uma aplicação de terceiros instalou um certificado fidedigno.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Passo 4: Criar perfis de certificado SCEP ou PKCS

Veja um dos seguintes tópicos para ajudar a configurar e a atribuir cada tipo de perfil de certificado:

- [Configurar e gerir certificados SCEP com o Intune](certificates-scep-configure.md)
- [Configurar e gerir certificados PKCS com o Intune](certficates-pfx-configure.md)

Após criar um perfil de certificado fidedigno, crie perfis de certificado SCEP ou PKCS para cada plataforma que queira utilizar. Ao criar um perfil de certificado SCEP, tem de especificar um perfil de certificado fidedigno para a mesma plataforma. Esta ação liga os dois perfis de certificado, mas mesmo assim tem de atribuir cada perfil separadamente.


## <a name="next-steps"></a>Próximos passos
Veja [Como atribuir perfis de dispositivo](device-profile-assign.md) para obter informações gerais sobre como atribuir perfis de dispositivo.

