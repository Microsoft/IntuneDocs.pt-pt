---
title: Criar um perfil de certificado no Microsoft Intune – Azure | Microsoft Docs
description: Para os seus dispositivos, adicione ou crie um perfil de certificado ao configurar um ambiente de certificado SCEP ou PKCS, exporte o certificado público, crie o perfil no portal do Azure e, em seguida, atribua o SCEP ou PKCS ao perfil de certificado no Microsoft Intune no portal do Azure
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 03/01/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 867a846b43edb3392db2be11e7ea544fa9317b6c
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Configurar um perfil de certificado para os seus dispositivos no Microsoft Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Quando conceder aos utilizadores acesso aos recursos da empresa através de VPN, Wi-Fi ou perfis de e-mail, pode autenticar estas ligações ao utilizar certificados. Ao utilizar certificados, não precisa de introduzir nomes de utilizador e palavras-passe para autenticar as ligações

Pode utilizar o Intune para atribuir estes certificados aos dispositivos que gere. O Intune suporta a atribuição e a gestão dos seguintes tipos de certificado:

- Protocolo SCEP (Simple Certificate Enrollment Protocol)
- PKCS#12 (ou PFX)

Cada um destes tipos de certificado tem os seus próprios pré-requisitos e requisitos de infraestrutura.

## <a name="overview"></a>Descrição geral

1. Confirme que tem aplicada a infraestrutura de certificado correta. Pode utilizar [certificados SCEP](certificates-scep-configure.md) e [certificados PKCS](certficates-pfx-configure.md).

2. Instale um certificado de raiz ou um certificado de Autoridade de Certificação (AC) intermediária em cada dispositivo, para que estes reconheçam a legitimidade da sua AC. Para tal, crie e implemente um **perfil de certificado fidedigno**. Ao atribuir este perfil, os dispositivos que gere com o Intune pedem e recebem o certificado de raiz. Tem de criar um perfil separado para cada plataforma. Os perfis de certificado fidedigno estão disponíveis para as seguintes plataformas:

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

   Só pode utilizar um perfil de certificado **SCEP** para os dispositivos que executam as seguintes plataformas:

   - macOS 10.9 e posterior
   - Windows Phone 8.1 e posterior

Certifique-se de que cria um perfil separado para cada plataforma de dispositivo. Ao criar o perfil, associe-o ao perfil de certificado de raiz fidedigna criado.

### <a name="further-considerations"></a>Considerações adicionais

- Se não tiver uma Autoridade de Certificação Empresarial, tem de criar uma
- Se utilizar perfis SCEP, configure um servidor de Serviço de Inscrição de Dispositivos de Rede (NDES)
- Se planear utilizar os perfis SCEP ou PKCS, transfira e configure o Microsoft Intune Certificate Connector


## <a name="step-1-configure-your-certificate-infrastructure"></a>Passo 1: configurar a sua infraestrutura de certificados

Veja um dos seguintes tópicos para ajudar a configurar a infraestrutura para cada tipo de perfil de certificado:

- [Configurar e gerir certificados SCEP com o Intune](certificates-scep-configure.md)
- [Configurar e gerir certificados PKCS com o Intune](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>Passo 2: exportar o seu certificado da AC de raiz confiável

Exporte o certificado de Autoridades de Certificação (AC) de Raiz Fidedigna como um certificado público (.cer) a partir da AC emissora ou de qualquer dispositivo que confie na sua AC emissora. Não exporte a chave privada (.pfx).

Importará este certificado quando configurar um perfil de certificado fidedigno.

## <a name="step-3-create-trusted-certificate-profiles"></a>Passo 3 – Criar perfis de certificado fidedigno
Crie um perfil de certificado fidedigno para poder criar um perfil de certificado SCEP ou PKCS. Precisa de um perfil de certificado fidedigno e de um perfil SCEP ou PKCS para cada plataforma de dispositivo. Os passos para criar certificados fidedignos são semelhantes para cada plataforma de dispositivo.

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
2. No painel **Configuração do dispositivo**, selecione **Gerir** > **Perfis**.
3. No painel de perfis, selecione **Criar perfil**.
4. No painel **Criar perfil**, introduza um **Nome** e uma **Descrição** para o perfil de certificado fidedigno.
5. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado fidedigno. Atualmente, pode escolher uma das seguintes plataformas para as definições de certificados:

    - **Android**
    - **Android for Work**
    - **iOS**
    - **macOS**
    - **Windows Phone 8.1**
    - **Windows 8.1 e posterior**
    - **Windows 10 e posterior**

6. Na lista pendente **Tipo de perfil**, selecione **Certificado fidedigno**.
7. Navegue para o certificado guardado na tarefa 1 e, em seguida, clique em **OK**.
8. Apenas para os dispositivos Windows 8.1 e Windows 10, selecione o **Arquivo de Destino** do certificado fidedigno em:
    - **Arquivo de certificados no computador – Raiz**
    - **Arquivo de certificados no computador – Intermédio**
    - **Armazenamento de certificados de utilizador – Intermédio**
8. Quando tiver terminado, selecione **OK**, volte ao painel **Criar perfil** e selecione **Criar**.

O perfil é criado e apresentado na lista. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).

Os dispositivos Android podem apresentar uma mensagem a indicar que uma aplicação de terceiros instalou um certificado fidedigno.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Passo 4: Criar perfis de certificado SCEP ou PKCS

Veja um dos seguintes tópicos para ajudar a configurar e a atribuir cada tipo de perfil de certificado:

- [Configurar e gerir certificados SCEP com o Intune](certificates-scep-configure.md)
- [Configurar e gerir certificados PKCS com o Intune](certficates-pfx-configure.md)

Após criar um perfil de certificado fidedigno, crie perfis de certificado SCEP ou PKCS para cada plataforma que queira utilizar. Ao criar um perfil de certificado SCEP, introduza um perfil de certificado fidedigno para a mesma plataforma. Este passo liga os dois perfis de certificado, mas mesmo assim tem de atribuir cada perfil separadamente.

## <a name="next-steps"></a>Próximos passos
Veja [Como atribuir perfis de dispositivo](device-profile-assign.md) para obter informações gerais sobre como atribuir perfis de dispositivo.
