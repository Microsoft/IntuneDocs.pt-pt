---
title: Criar um perfil de certificado no Microsoft Intune – Azure | Microsoft Docs
description: Para os seus dispositivos, adicione ou crie um perfil de certificado ao configurar um ambiente de certificado SCEP ou PKCS, exporte o certificado público, crie o perfil no portal do Azure e, em seguida, atribua o SCEP ou PKCS ao perfil de certificado no Microsoft Intune no portal do Azure
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/03/2019
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
ms.openlocfilehash: 345d039fede2a77ba0485944cb601683bdcebfda
ms.sourcegitcommit: 29b1113dc04534c4c87c33c773c5a0e24266e042
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/07/2019
ms.locfileid: "71999299"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Usar certificados para autenticação no Microsoft Intune  

Use certificados com o Intune para autenticar seus usuários em aplicativos e recursos corporativos por meio de VPN, Wi-Fi ou perfis de email. Quando você usa certificados para autenticar essas conexões, os usuários finais não precisam inserir nomes de usuário e senhas, o que ajuda a tornar seu acesso contínuo. Os certificados também são usados para assinatura e criptografia de email usando S/MIME.

## <a name="intune-supported-certificates-and-usage"></a>Certificados e uso com suporte do Intune
| Type              | Authentication | Assinatura S/MIME | Criptografia S/MIME  |
|--|--|--|--|
| Certificado PKCS importado |  | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png)|
| PKCS#12 (ou PFX)    | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) |  |
| Protocolo SCEP (Simple Certificate Enrollment Protocol)  | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) | |

Para implantar esses certificados, você criará e atribuirá perfis de certificado a dispositivos.  

Cada perfil de certificado individual que você cria oferece suporte a uma única plataforma. Por exemplo, se você usar certificados PKCS, criará o perfil de certificado PKCS para Android e um perfil de certificado PKCS separado para iOS. Se você também usar certificados SCEP para essas duas plataformas, criará um perfil de certificado SCEP para Android e outro para iOS.  

**Considerações gerais**:  
- Se você não tiver uma AC (autoridade de certificação) corporativa, deverá criar uma ou usar uma de [um dos nossos parceiros com suporte](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners).
- Se você usar perfis de certificado SCEP usando os serviços de certificados do Microsoft Active Directory, você configurará um servidor NDES (serviço de registro de dispositivo de rede).
- Se você usar o SCEP com um de nossos parceiros de autoridade de certificação, você precisará [integrá-lo ao Intune](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).
- Os perfis de certificado SCEP e PKCS exigem que você baixe, instale e configure o Microsoft Intune Certificate Connector. 
- PCKS certificados importados exigem que você baixe, instale e configure o conector de certificado PFX para Microsoft Intune.
- Certificados PKCS importados exigem que você exporte certificados de sua autoridade de certificação e importe-os para Microsoft Intune. Consulte [o projeto do PFXImport PowerShell](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)
- Para que um dispositivo use perfis de certificado SCEP, PCKS ou PKCS importados, esse dispositivo deve confiar em sua autoridade de certificação raiz. Você usa um *perfil de certificado confiável* para implantar seu certificado de autoridade de certificação raiz confiável em dispositivos.  

## <a name="supported-platforms-and-certificate-profiles"></a>Plataformas com suporte e perfis de certificado  
| Plataforma              | Perfil de certificado confiável | Perfil de certificado PKCS | Perfil de certificado SCEP | Perfil de certificado importado PKCS  |
|--|--|--|--|---|
| Administrador do dispositivo Android | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png)|  ![Suportadas](./media/certificates-configure/green-check.png) |
| Android Enterprise <br> -Proprietário do dispositivo   | ![Suportadas](./media/certificates-configure/green-check.png) |   |  |   |
| Android Enterprise <br> -Perfil de trabalho    | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) |
| iOS                   | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) |
| macOS                 | ![Suportadas](./media/certificates-configure/green-check.png) |   |![Suportadas](./media/certificates-configure/green-check.png)|![Suportadas](./media/certificates-configure/green-check.png)|
| Windows Phone 8.1     |![Suportadas](./media/certificates-configure/green-check.png)  |  | ![Suportadas](./media/certificates-configure/green-check.png)| ![Suportadas](./media/certificates-configure/green-check.png) |
| Windows 8.1 e posterior |![Suportadas](./media/certificates-configure/green-check.png)  |  |![Suportadas](./media/certificates-configure/green-check.png) |   |
| Windows 10 e posterior  | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) | ![Suportadas](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Exportar o certificado de AC raiz confiável  
Para usar certificados PKCS, SCEP e PKCS importados, os dispositivos devem confiar em sua autoridade de certificação raiz. Para estabelecer essa relação de confiança, exporte o certificado de autoridade de certificação (CA) raiz confiável, bem como quaisquer certificados de autoridade de certificação intermediários ou emissores, como um certificado público (. cer). Você pode obter esses certificados da AC emissora ou de qualquer dispositivo que confie na AC emissora.  

Para exportar o certificado, consulte a documentação da autoridade de certificação. Você precisará exportar o certificado público como um arquivo. cer.  Não exporte a chave privada, um arquivo. pfx.  

Você usará esse arquivo. cer ao [criar perfis de certificado confiáveis](#create-trusted-certificate-profiles) para implantar esse certificado em seus dispositivos.  

## <a name="create-trusted-certificate-profiles"></a>Criar perfis de certificado confiável  
Crie um perfil de certificado confiável antes de criar um perfil de certificado SCEP, PKCS ou PKCS importado. A implantação de um perfil de certificado confiável garante que cada dispositivo reconheça a legitimidade de sua autoridade de certificação. Os perfis de certificado SCEP fazem referência direta a um perfil de certificado confiável. Os perfis de certificado PKCS não fazem referência direta ao perfil de certificado confiável, mas fazem referência direta ao servidor que hospeda sua autoridade de certificação. Os perfis de certificado PKCS importados não fazem referência direta ao perfil de certificado confiável, mas podem utilizá-lo no dispositivo. A implantação de um perfil de certificado confiável para dispositivos garante que essa confiança seja estabelecida. Quando um dispositivo não confiar na AC raiz, a política de perfil de certificado SCEP ou PKCS falhará.  

Crie um perfil de certificado confiável separado para cada plataforma de dispositivo à qual você deseja dar suporte, assim como você fará para os perfis de certificado SCEP, PCKS e PKCS importados.  


### <a name="to-create-a-trusted-certificate-profile"></a>Para criar um perfil de certificado fidedigno  

1. Entre no portal do [Intune](https://aka.ms/intuneportal).  
2. Selecione **Configuração do dispositivo** > **Gerir** > **Perfis** > **Criar perfil**.  
3. Insira um **nome e uma descrição** para o perfil de certificado confiável.  
4. Na lista pendente **Plataforma**, selecione a plataforma do dispositivo para este certificado fidedigno.  
5. Na lista pendente **Tipo de perfil**, selecione **Certificado fidedigno**.  
6. Navegue até o arquivo. cer do certificado de AC raiz confiável que você exportou para uso com este perfil de certificado e selecione **OK**.  
7. Apenas para os dispositivos Windows 8.1 e Windows 10, selecione o **Arquivo de Destino** do certificado fidedigno em:  
   - **Arquivo de certificados no computador – Raiz**
   - **Arquivo de certificados no computador – Intermédio**
   - **Armazenamento de certificados de utilizador – Intermédio**
8. Quando tiver terminado, selecione **OK**, volte ao painel **Criar perfil** e selecione **Criar**.
O perfil aparece na lista de perfis no painel *configuração do dispositivo –* exibição de perfis, com um tipo de perfil de **certificado confiável**.  Certifique-se de atribuir esse perfil a dispositivos que usarão certificados SCEP ou PCKS. Para atribuir o perfil a grupos, consulte [atribuir perfis de dispositivo](../configuration/device-profile-assign.md).

> [!NOTE]  
> Os dispositivos Android podem exibir uma mensagem de que uma terceira parte instalou um certificado confiável.  

## <a name="additional-resources"></a>Recursos adicionais  
- [Atribuir perfis de dispositivo](../configuration/device-profile-assign.md)  
- [Use S/MIME to sign and encrypt emails (Utilizar S/MIME para assinar e encriptar e-mails)](certificates-s-mime-encryption-sign.md)  
- [Usar autoridade de certificação de terceiros](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Passos seguintes  
Depois de criar e atribuir perfis de certificado confiáveis, crie os perfis de certificado SCEP, PKCS ou PKCS importados para cada plataforma que você deseja usar. Para continuar, consulte os seguintes artigos:  
- [Configurar a infraestrutura para dar suporte a certificados SCEP com o Intune](certificates-scep-configure.md)  
- [Configurar e gerir certificados PKCS com o Intune](certficates-pfx-configure.md)  
- [Criar um perfil de certificado do PKCS importado](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)  

