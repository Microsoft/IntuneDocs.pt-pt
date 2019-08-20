---
title: Criar um perfil de certificado no Microsoft Intune – Azure | Microsoft Docs
description: Para os seus dispositivos, adicione ou crie um perfil de certificado ao configurar um ambiente de certificado SCEP ou PKCS, exporte o certificado público, crie o perfil no portal do Azure e, em seguida, atribua o SCEP ou PKCS ao perfil de certificado no Microsoft Intune no portal do Azure
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 08/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f13b5b92ca442f4b5ae05d3567f8385288d92909
ms.sourcegitcommit: 6b5907046f920279bbda3ee6c93e98594624c05c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69582931"
---
# <a name="configure-a-certificate-profile-for-your-devices-in-microsoft-intune"></a>Configurar um perfil de certificado para os seus dispositivos no Microsoft Intune

O acesso aos recursos da empresa é fornecido aos utilizadores através de perfis de e-mail, VPN ou Wi-Fi. Pode autenticar estas ligações através de certificados. Ao utilizar certificados, os seus utilizadores finais não precisam de introduzir nomes de utilizador e palavras-passe para autenticar.

Pode utilizar o Intune para atribuir estes certificados aos dispositivos que gere. O Intune suporta a atribuição e a gestão dos seguintes tipos de certificado:

- Protocolo SCEP (Simple Certificate Enrollment Protocol)
- PKCS#12 (ou PFX)

Cada um destes tipos de certificado tem os seus próprios pré-requisitos e requisitos de infraestrutura.


## <a name="overview"></a>Descrição geral

1. Certifique-se de que a infraestrutura de certificado correta está configurada. Pode utilizar [certificados SCEP](certificates-scep-configure.md) e [certificados PKCS](certficates-pfx-configure.md).

2. Instale um certificado de raiz ou um certificado de Autoridade de Certificação (AC) intermediária em cada dispositivo, para que estes reconheçam a legitimidade da sua AC. Para instalar o certificado, crie e atribua um **perfil de certificado confiável** a cada dispositivo. Ao atribuir este perfil, os dispositivos geridos pelo Intune pedem e recebem o certificado de raiz. Tem de criar um perfil separado para cada plataforma. Os perfis de certificado fidedigno estão disponíveis para as seguintes plataformas:

    - iOS 8.0 e posterior
    - macOS 10.11 e posterior
    - Android 4.0 e posterior
    - Android Enterprise  
    - Windows 8.1 e posterior
    - Windows Phone 8.1 e posterior
    - Windows 10 e posterior

    > [!NOTE]  
    > Não há suporte para perfis de certificado em dispositivos que executam o *Android Enterprise para dispositivos dedicados*.

3. Crie perfis de certificados para que os dispositivos solicitem a utilização de um certificado para autenticação do acesso a VPN, Wi-Fi e e-mail. Os seguintes tipos de perfil estão disponíveis para diferentes plataformas:  

   | Plataforma     |Certificado PKCS|Certificado SCEP| Certificado PKCS importado | 
   |--------------|----------------|----------------|-------------------|
   | Android                | Sim    | Sim    | Sim    |
   | Android Enterprise     | Sim    | Sim    | Sim    |
   | iOS                    | Sim    | Sim    | Sim    |
   | macOS                  |        | Sim    | Sim    |
   | Windows Phone 8.1      |        | Sim    | Sim    |
   | Windows 8.1 e posterior  |        | Sim    |        |
   | Windows 10 e posterior   | Sim    | Sim    | Sim    |

   Certifique-se de que cria um perfil separado para cada plataforma de dispositivo. Ao criar o perfil, associe-o ao perfil de certificado de raiz fidedigna criado.

### <a name="further-considerations"></a>Considerações adicionais

- Se não tiver uma Autoridade de Certificação Empresarial, tem de criar uma
- Se utilizar perfis SCEP, configure um servidor de Serviço de Inscrição de Dispositivos de Rede (NDES)
- Se planear utilizar os perfis SCEP ou PKCS, transfira e configure o Microsoft Intune Certificate Connector


## <a name="step-1-configure-your-certificate-infrastructure"></a>Passo 1: Configurar sua infraestrutura de certificado

Consulte um dos artigos a seguir para obter ajuda com a configuração da infraestrutura para cada tipo de perfil de certificado:

- [Configurar e gerir certificados SCEP com o Intune](certificates-scep-configure.md)
- [Configurar e gerir certificados PKCS com o Intune](certficates-pfx-configure.md)


## <a name="step-2-export-your-trusted-root-ca-certificate"></a>Passo 2: Exportar seu certificado de autoridade de certificação raiz confiável

Exporte o certificado de Autoridades de Certificação (AC) de Raiz Fidedigna como um certificado público (.cer) a partir da AC emissora ou de qualquer dispositivo que confie na sua AC emissora. Não exporte a chave privada (. pfx).

Importará este certificado quando configurar um perfil de certificado fidedigno.

## <a name="step-3-create-trusted-certificate-profiles"></a>Passo 3: Criar perfis de certificado confiável

Crie um perfil de certificado fidedigno para poder criar um perfil de certificado SCEP ou PKCS. Precisa de um perfil de certificado fidedigno e de um perfil SCEP ou PKCS para cada plataforma de dispositivo. Os passos para criar certificados fidedignos são semelhantes para todas as plataformas de dispositivos.

1. No [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), selecione **configuração** > do dispositivo**gerenciar** > **perfis** > **Criar perfil**.
2. Introduza as seguintes propriedades:

    - **Nome**: introduza um nome descritivo para o perfil. Atribua nomes aos perfis de forma que possa identificá-los facilmente mais tarde. Por exemplo, um bom nome de perfil é o **perfil de certificado confiável para dispositivos Android Enterprise de proprietário do dispositivo** ou **perfil de certificado confiável para dispositivos IOS**.
    - **Descrição**: introduza uma descrição para o perfil. Esta definição é opcional, mas recomendada.
    - **Plataforma**: escolha a plataforma dos dispositivos. As opções são:

      - **Android**
      -  > **Somente proprietário do dispositivo** Android Enterprise
      -  > **Somente perfil de trabalho** do Android Enterprise
      - **iOS**
      - **macOS**
      - **Windows Phone 8.1**
      - **Windows 8.1 e posterior**
      - **Windows 10 e posterior**

    - **Tipo de perfil**: Escolha **certificado confiável**.

3. Navegue até o certificado que você salvou [na etapa 2: Exporte seu certificado](#step-2-export-your-trusted-root-ca-certificate)de AC raiz confiável e, em seguida, selecione **OK**.
4. Apenas para os dispositivos Windows 8.1 e Windows 10, selecione o **Arquivo de Destino** do certificado fidedigno em:

    - **Repositório de certificados do computador-raiz** SCEP
    - **Repositório de certificados do computador-intermediário** SCEP
    - **Repositório de certificados do usuário-intermediário** (PKCS, SCEP)

5. Quando tiver terminado, selecione **OK**, volte ao painel **Criar perfil** e selecione **Criar**.

O perfil é criado e apresentado na lista. Para atribuir este perfil a grupos, veja [atribuir perfis de dispositivo](device-profile-assign.md).

   >[!NOTE]
   > Os dispositivos Android podem apresentar uma mensagem a indicar que uma aplicação de terceiros instalou um certificado fidedigno.

## <a name="step-4-create-scep-or-pkcs-certificate-profiles"></a>Passo 4: Criar perfis de certificado SCEP ou PKCS

Consulte um dos artigos a seguir para obter ajuda com a configuração e atribuição de cada tipo de perfil de certificado:

- [Configurar e gerir certificados SCEP com o Intune](certificates-scep-configure.md)
- [Configurar e gerir certificados PKCS com o Intune](certficates-pfx-configure.md)

Após criar um perfil de certificado fidedigno, crie perfis de certificado SCEP ou PKCS para cada plataforma que queira utilizar. Ao criar um perfil de certificado SCEP, introduza um perfil de certificado fidedigno para a mesma plataforma. Este passo liga os dois perfis de certificado, mas mesmo assim tem de atribuir cada perfil separadamente.

## <a name="next-steps"></a>Passos Seguintes

[Atribuir perfis de dispositivo](device-profile-assign.md)  
[Use S/MIME to sign and encrypt emails (Utilizar S/MIME para assinar e encriptar e-mails)](certificates-s-mime-encryption-sign.md)  
[Use third-party certificate authority (Utilizar uma autoridade de certificação de terceiros)](certificate-authority-add-scep-overview.md)

## <a name="see-also"></a>Consulte também

[Solução de problemas de configuração de NDES para uso com Microsoft Intune perfis de certificado](https://support.microsoft.com/help/4459540)

[Solucionando problemas de implantação do perfil de certificado SCEP no Microsoft Intune](https://support.microsoft.com/help/4457481)
