---
title: Criar um perfil de certificado no Microsoft Intune – Azure | Microsoft Docs
description: Saiba como usar protocolo SCEP (SCEP) ou certificados PKCS (padrões de criptografia de chave pública) e perfis de certificado com Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/07/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ea2d51b82f0f47ee4bfabc94c2e971e4cb666d4
ms.sourcegitcommit: b5e719fb507b1bc4774674e76c856c435e69f68c
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/08/2019
ms.locfileid: "73801752"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Usar certificados para autenticação no Microsoft Intune

Use certificados com o Intune para autenticar seus usuários em aplicativos e recursos corporativos por meio de VPN, Wi-Fi ou perfis de email. Quando você usa certificados para autenticar essas conexões, os usuários finais não precisarão inserir nomes de usuário e senhas, o que pode tornar seu acesso contínuo. Os certificados também são usados para assinatura e criptografia de email usando S/MIME.

## <a name="intune-supported-certificates-and-usage"></a>Certificados e uso com suporte do Intune

| Tipo              | Autenticação | Assinatura S/MIME | Criptografia S/MIME  |
|--|--|--|--|
| Certificado de padrões de criptografia de chave pública (PKCS) importado |  | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png)|
| PKCS#12 (ou PFX)    | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) |  |
| Protocolo SCEP (Simple Certificate Enrollment Protocol)  | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) | |

Para implantar esses certificados, você criará e atribuirá perfis de certificado a dispositivos.  

Cada perfil de certificado individual que você cria oferece suporte a uma única plataforma. Por exemplo, se você usar certificados PKCS, criará o perfil de certificado PKCS para Android e um perfil de certificado PKCS separado para iOS. Se você também usar certificados SCEP para essas duas plataformas, criará um perfil de certificado SCEP para Android e outro para iOS.

**Considerações gerais**:
- Se você não tiver uma AC (autoridade de certificação) corporativa, deverá criar uma ou usar uma de [um dos nossos parceiros com suporte](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners).
- Se você usar perfis de certificado SCEP usando os serviços de certificados do Microsoft Active Directory, você configurará um servidor NDES (serviço de registro de dispositivo de rede).
- Se você usar o SCEP com um de nossos parceiros de autoridade de certificação, você precisará [integrá-lo ao Intune](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).
- Os perfis de certificado SCEP e PKCS exigem que você baixe, instale e configure o Microsoft Intune Certificate Connector.
- Certificados PKCS importados exigem que você baixe, instale e configure o conector de certificado PFX para Microsoft Intune.
- Certificados PKCS importados exigem que você exporte certificados de sua autoridade de certificação e importe-os para Microsoft Intune. Consulte [o projeto PFXImport PowerShell](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell).
- Para que um dispositivo use perfis de certificado SCEP, PKCS ou PKCS importados, esse dispositivo deve confiar em sua autoridade de certificação raiz. Você usa um *perfil de certificado confiável* para implantar seu certificado de autoridade de certificação raiz confiável em dispositivos.

## <a name="supported-platforms-and-certificate-profiles"></a>Plataformas com suporte e perfis de certificado

| Platform              | Perfil de certificado confiável | Perfil de certificado PKCS | Perfil de certificado SCEP | Perfil de certificado importado PKCS  |
|--|--|--|--|---|
| Administrador do dispositivo Android | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png)|  ![Suportado](./media/certificates-configure/green-check.png) |
| Android Enterprise <br> -Totalmente gerenciado (proprietário do dispositivo)   | ![Suportado](./media/certificates-configure/green-check.png) |   | ![Suportado](./media/certificates-configure/green-check.png) |   |
| Android Enterprise <br> -Dedicado (proprietário do dispositivo)   |  |   |  |   |
| Android Enterprise <br> -Perfil de trabalho    | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) |
| iOS                   | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) |
| macOS                 | ![Suportado](./media/certificates-configure/green-check.png) |  ![Suportado](./media/certificates-configure/green-check.png) |![Suportado](./media/certificates-configure/green-check.png)|![Suportado](./media/certificates-configure/green-check.png)|
| Wnodows Phone 8.1     |![Suportado](./media/certificates-configure/green-check.png)  |  | ![Suportado](./media/certificates-configure/green-check.png)| ![Suportado](./media/certificates-configure/green-check.png) |
| Windows 8.1 e posterior |![Suportado](./media/certificates-configure/green-check.png)  |  |![Suportado](./media/certificates-configure/green-check.png) |   |
| Windows 10 e posterior  | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) | ![Suportado](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Exportar o certificado de AC raiz confiável

Para usar certificados PKCS, SCEP e PKCS importados, os dispositivos devem confiar em sua autoridade de certificação raiz. Para estabelecer a confiança, exporte o certificado de AC (autoridade de certificação) raiz confiável e quaisquer certificados de autoridade de certificação intermediários ou emissores, como um certificado público (. cer). Você pode obter esses certificados da AC emissora ou de qualquer dispositivo que confie na AC emissora.

Para exportar o certificado, consulte a documentação da autoridade de certificação. Você precisará exportar o certificado público como um arquivo. cer.  Não exporte a chave privada, um arquivo. pfx.

Você usará esse arquivo. cer ao [criar perfis de certificado confiáveis](#create-trusted-certificate-profiles) para implantar esse certificado em seus dispositivos.

## <a name="create-trusted-certificate-profiles"></a>Criar perfis de certificado confiável

Crie um perfil de certificado confiável antes de criar um perfil de certificado SCEP, PKCS ou PKCS importado. A implantação de um perfil de certificado confiável garante que cada dispositivo reconheça a legitimidade de sua autoridade de certificação. Os perfis de certificado SCEP fazem referência direta a um perfil de certificado confiável. Os perfis de certificado PKCS não fazem referência direta ao perfil de certificado confiável, mas fazem referência direta ao servidor que hospeda sua autoridade de certificação. Os perfis de certificado PKCS importados não fazem referência direta ao perfil de certificado confiável, mas podem usá-lo no dispositivo. A implantação de um perfil de certificado confiável para dispositivos garante que essa confiança seja estabelecida. Quando um dispositivo não confiar na AC raiz, a política de perfil de certificado SCEP ou PKCS falhará.  

Crie um perfil de certificado confiável separado para cada plataforma de dispositivo à qual você deseja dar suporte, assim como você fará para perfis de certificado SCEP, PKCS e PKCS importados.  


### <a name="to-create-a-trusted-certificate-profile"></a>Para criar um perfil de certificado fidedigno  

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **dispositivos** > **perfis de configuração** > **Criar perfil**.

   ![Navegue até o Intune e crie um novo perfil para um certificado confiável](./media/certficates-pfx-configure/certificates-pfx-configure-profile-new.png)

3. Introduza as seguintes propriedades:

   - O **Nome** do perfil
   - Opcionalmente, defina uma **Descrição**
   - A **Plataforma** na qual vai implementar o perfil
   - Defina o **Tipo de perfil** como **Certificado fidedigno**

4. Selecione **configurações**e, em seguida, navegue até o arquivo. cer do certificado de AC raiz confiável que você exportou para uso com este perfil de certificado e, em seguida, selecione **OK**.

5. Apenas para os dispositivos Windows 8.1 e Windows 10, selecione o **Arquivo de Destino** do certificado fidedigno em:  
   - **Arquivo de certificados no computador – Raiz**
   - **Arquivo de certificados no computador – Intermédio**
   - **Armazenamento de certificados de utilizador – Intermédio**

6. Quando tiver terminado, selecione **OK**, volte ao painel **Criar perfil** e selecione **Criar**.

O perfil aparece na lista de perfis na janela *dispositivos – perfis de configuração* , com um tipo de perfil de **certificado confiável**.  Certifique-se de atribuir esse perfil a dispositivos que usarão certificados SCEP ou PKCS. Para atribuir o perfil a grupos, consulte [atribuir perfis de dispositivo](../configuration/device-profile-assign.md).

> [!NOTE]  
> Os dispositivos Android podem exibir uma mensagem de que uma terceira parte instalou um certificado confiável.  

## <a name="additional-resources"></a>Recursos adicionais

- [Atribuir perfis de dispositivo](../configuration/device-profile-assign.md)  
- [Use S/MIME to sign and encrypt emails (Utilizar S/MIME para assinar e encriptar e-mails)](certificates-s-mime-encryption-sign.md)  
- [Usar autoridade de certificação de terceiros](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Próximos passos

Crie perfis de certificado SCEP, PKCS ou PKCS importados para cada plataforma que você deseja usar. Para continuar, consulte os seguintes artigos:  
- [Configurar a infraestrutura para dar suporte a certificados SCEP com o Intune](certificates-scep-configure.md)  
- [Configurar e gerir certificados PKCS com o Intune](certficates-pfx-configure.md)  
- [Criar um perfil de certificado do PKCS importado](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)  
