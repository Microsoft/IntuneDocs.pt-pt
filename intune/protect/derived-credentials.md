---
title: Usar credenciais derivadas para dispositivos móveis no Microsoft Intune-Azure | Microsoft Docs
description: Use credenciais derivadas em dispositivos móveis como um método de autenticação para VPN do Intune, email, perfis de Wi-Fi, aplicativos e S/MIME e criptografia. As credenciais derivadas são uma implementação das diretrizes do NIST para a publicação especial 800-157.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/31/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c4d0772f9a0afce0607d0193bfb82ea6bd22709d
ms.sourcegitcommit: d2d18eef64bcf16eec1a48fcb67f1362537c0245
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/02/2019
ms.locfileid: "73445321"
---
# <a name="use-derived-credentials-in-microsoft-intune"></a>Usar credenciais derivadas no Microsoft Intune

*Este artigo se aplica a dispositivos que executam o iOS*

Em um ambiente em que os cartões inteligentes são necessários para autenticação ou criptografia e assinatura, agora você pode usar o Intune para provisionar dispositivos móveis com um certificado derivado do cartão inteligente de um usuário. Esse certificado é chamado de uma *credencial derivada*. O Intune [dá suporte a vários emissores de credencial derivados](#supported-issuers), embora você possa usar apenas um único emissor por locatário por vez.

As credenciais derivadas são uma implementação das diretrizes do National Institute of Standards and Technology (NIST) para as credenciais de PIV (verificação de identidade pessoal) derivadas como parte da publicação especial (SP) 800-157.

**Com a implementação do Intune**:

- O administrador do Intune configura seu locatário para trabalhar com um emissor de credencial derivada com suporte. Você não precisa definir configurações específicas do Intune no sistema do emissor da credencial derivada.

- O administrador do Intune especifica a **credencial derivada** como o *método de autenticação* para os seguintes objetos:

  - Tipos de perfil comuns como Wi-Fi, VPN e email, que inclui o aplicativo de email nativo do iOS

  - Autenticação de aplicativo

  - Assinatura e criptografia S/MIME

- Os usuários obtêm uma credencial derivada usando seu cartão inteligente em um computador para se autenticarem no emissor de credencial derivada. O emissor então emite para o dispositivo móvel um certificado que é derivado de seu cartão inteligente.

- Depois que o dispositivo recebe a credencial derivada, ele é usado para autenticação e para assinatura S/MIME e criptografia quando os aplicativos ou perfis de acesso a recursos exigem a credencial derivada. 

## <a name="prerequisites"></a>Pré-requisitos

Examine as seguintes informações antes de configurar seu locatário para usar credenciais derivadas.

### <a name="supported-platforms"></a>Plataformas suportadas

O Intune dá suporte a credenciais derivadas nas seguintes plataformas de sistema operacional:

- iOS/iPadOS

### <a name="supported-issuers"></a>Emissores com suporte

O Intune dá suporte a um emissor de credencial derivada único por locatário. Você pode configurar o Intune para trabalhar com os seguintes emissores:

- **Disa purebred**: https://cyber.mil/pki-pke/purebred/
- **Entrust Datacard**: https://www.entrustdatacard.com/
- **Intercedam**: https://www.intercede.com/

Para obter detalhes importantes sobre como usar os diferentes emissores, consulte as diretrizes para esse emissor<!-- , including the issuers end-user workflow-->. Para obter mais informações, consulte [Plan for Derived Credentials](#plan-for-derived-credentials) neste artigo.

> [!IMPORTANT]  
> Se você excluir um emissor de credencial derivado do seu locatário, as credenciais derivadas que foram configuradas por meio desse emissor deixarão de funcionar.
>
> Consulte [alterar o emissor de credenciais derivadas](#change-the-derived-credential-issuer) mais adiante neste artigo.

### <a name="company-portal-app"></a>Aplicação Portal da Empresa

Planeje implantar o aplicativo Portal da Empresa do Intune em dispositivos que serão registrados para uma credencial derivada. Os usuários do dispositivo usam o aplicativo Portal da Empresa para iniciar o processo de registro de credenciais.

Para dispositivos iOS, consulte [adicionar aplicativos da loja do Ios ao Microsoft Intune](../apps/store-apps-ios.md).

## <a name="plan-for-derived-credentials"></a>Planejar as credenciais derivadas

Entenda as considerações a seguir antes de configurar um emissor de credencial derivado.

### <a name="1-review-the-documentation-for-your-chosen-derived-credential-issuer"></a>1) examine a documentação do emissor de credencial derivada escolhido  

Antes de configurar um emissor, examine a documentação do emissor para entender como o sistema fornece credenciais derivadas para dispositivos.

Dependendo do emissor escolhido, talvez você precise que a equipe esteja disponível no momento do registro para ajudar os usuários a concluir o processo. Você também deve examinar suas configurações atuais do Intune para garantir que elas não bloqueiem o acesso necessário para que os dispositivos ou usuários concluam a solicitação de credenciais.

Por exemplo, você pode usar o acesso condicional para bloquear o acesso ao email para dispositivos sem conformidade. Se você depender de notificações por email para informar ao usuário para iniciar o processo de registro de credenciais derivadas, os usuários poderão não receber essas instruções até que estejam em conformidade com a política.

Da mesma forma, alguns fluxos de trabalho de solicitação de credenciais derivadas exigem o uso da câmera do dispositivo para verificar um código QR na tela. Esse código vincula esse dispositivo à solicitação de autenticação que ocorreu no emissor de credencial derivada com as credenciais de cartão inteligente do usuário. Se as políticas de configuração de dispositivo bloquearem o uso da câmera, o usuário não poderá concluir a solicitação de registro de credencial derivada.

Informações gerais:

- Você só pode configurar um único emissor por locatário por vez e esse emissor está disponível para todos os usuários e dispositivos com suporte em seu locatário.

- Os usuários não serão notificados de que devem se registrar para as credenciais derivadas até que você as direcione com uma política que exija credenciais derivadas.

- A notificação pode ser por meio de notificação de aplicativo para o Portal da Empresa, por email ou ambos. Se você optar por usar notificações por email e usar o acesso condicional habilitado, os usuários poderão não receber a notificação por email se o dispositivo não estiver em conformidade.

### <a name="2-review-the-end-user-workflow-for-your-chosen-issuer"></a>2) examine o fluxo de trabalho do usuário final para o emissor escolhido

A seguir estão as principais considerações para cada parceiro com suporte.  Familiarize-se com essas informações para garantir que suas políticas e configurações do Intune não bloqueiem usuários e dispositivos de concluir o registro com êxito para uma credencial derivada desse emissor.

#### <a name="disa-purebred"></a>DISA purebred

Examine o [fluxo de trabalho do usuário para Disa purebred](https://docs.microsoft.com/intune-user-help/enroll-ios-device-disa-purebred). Os principais requisitos para esse fluxo de trabalho incluem:

- Os usuários precisam de acesso a um computador ou quiosque, onde podem usar seu cartão inteligente para se autenticarem no emissor.

- Os dispositivos que serão registrados para uma credencial derivada devem instalar o aplicativo Portal da Empresa do Intune.

- Use o Intune para [implantar o aplicativo Disa purebred](#deploy-the-disa-purebred-app) em dispositivos que serão registrados para uma credencial derivada. Esse aplicativo deve ser implantado por meio do Intune para que seja gerenciado e, em seguida, pode trabalhar com o aplicativo Portal da Empresa do Intune. Este aplicativo é usado por usuários do dispositivo para concluir a solicitação de credencial derivada.

- O aplicativo DISA purebred requer uma [VPN por aplicativo](../configuration/vpn-settings-configure.md) para garantir que o aplicativo possa acessar Disa purebred durante o registro para a credencial derivada.

- Os usuários do dispositivo devem trabalhar com um agente ao vivo durante o processo de registro. Durante o registro, são fornecidas senhas de uso único de tempo limitado ao usuário à medida que eles passam pelo processo de registro.

Para obter informações sobre como obter e configurar o aplicativo DISA purebred, consulte [implantar o aplicativo Disa purebred](#deploy-the-disa-purebred-app) mais adiante neste artigo.

#### <a name="entrust-datacard"></a>Entrust Datacard

Examine o [fluxo de trabalho do usuário para Entrust Datacard](https://docs.microsoft.com/intune-user-help/enroll-ios-device-entrust-datacard). Os principais requisitos para esse fluxo de trabalho incluem:

- Os usuários precisam de acesso a um computador ou quiosque, onde podem usar seu cartão inteligente para se autenticarem no emissor.

- Os dispositivos que serão registrados para uma credencial derivada devem instalar o aplicativo Portal da Empresa do Intune.

- Uso de uma câmera de dispositivo para digitalizar um código QR que vincula a solicitação de autenticação à solicitação de credencial derivada do dispositivo móvel.

#### <a name="intercede"></a>Intercedam

Examine o [fluxo de trabalho do usuário para intercedam](https://docs.microsoft.com/intune-user-help/enroll-ios-device-intercede). Os principais requisitos para esse fluxo de trabalho incluem:

- Os usuários precisam de acesso a um computador ou quiosque, onde podem usar seu cartão inteligente para se autenticarem no emissor.

- Os dispositivos que serão registrados para uma credencial derivada devem instalar o aplicativo Portal da Empresa do Intune.

- Uso de uma câmera de dispositivo para digitalizar um código QR que vincula a solicitação de autenticação à solicitação de credencial derivada do dispositivo móvel.

### <a name="3-deploy-a-trusted-root-certificate-to-devices"></a>3) implantar um certificado raiz confiável em dispositivos

Um certificado raiz confiável é usado com credenciais derivadas para verificar se a cadeia de certificados de credencial derivada é válida e confiável. Mesmo quando não é referenciado diretamente pela política, um certificado raiz confiável é necessário. Consulte [configurar um perfil de certificado para seus dispositivos no Microsoft Intune](certificates-configure.md).

### <a name="4-provide-end-user-instructions-for-how-to-get-the-derived-credential"></a>4) fornecer instruções do usuário final sobre como obter a credencial derivada

Crie e forneça orientações para os usuários sobre como iniciar o processo de registro de credenciais derivadas e para navegar pelo fluxo de trabalho de registro de credenciais derivadas para o emissor escolhido.

Recomendamos que você forneça uma URL que hospedará suas diretrizes. Você especifica essa URL ao configurar o emissor de credencial derivada para seu locatário e essa URL é disponibilizada no aplicativo Portal da Empresa. Se você não especificar sua própria URL, o Intune fornecerá um link para detalhes genéricos. Esses detalhes não podem abranger todos os cenários e podem não ser precisos para o seu ambiente.

### <a name="5-deploy-intune-policies-that-require-derived-credentials"></a>5) implantar políticas do Intune que exigem credenciais derivadas

Crie novas políticas ou edite as políticas existentes para usar credenciais derivadas. As credenciais derivadas substituem outros métodos de autenticação para autenticação de aplicativo, Wi-Fi, VPN, email e assinatura S/MIME e criptografia.

Evite a necessidade de usar uma credencial derivada para acessar um processo que você usará como parte do processo para obter a credencial derivada, pois isso pode impedir que os usuários concluam a solicitação.

## <a name="set-up-a-derived-credential-issuer"></a>Configurar um emissor de credencial derivada

Antes de criar políticas que exigem o uso de uma credencial derivada, configure um emissor de credencial no console do Intune. Um emissor de credencial derivado é uma configuração de todo o locatário. Os locatários dão suporte a apenas um único emissor por vez.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e vá para **configuração do dispositivo**  > **credenciais derivadas**.

   ![Configurar credenciais derivadas no console](./media/derived-credentials/configure-provider.png)

2. Especifique um **nome de exibição** amigável para a política de emissor de credencial derivada.  Esse nome não é mostrado para os usuários do dispositivo.

3. Para **emissor de credencial derivada**, selecione o emissor de credencial derivada que você escolheu para seu locatário:
   - DISA purebred
   - Entrust Datacard
   - Intercedam  

4. Especifique uma **URL de ajuda de credencial derivada** para fornecer um link para um local que inclui instruções personalizadas para ajudar os usuários a obter credenciais derivadas para sua organização. As instruções devem ser específicas à sua organização e ao fluxo de trabalho necessário para obter uma credencial do emissor escolhido. O link aparece no aplicativo Portal da Empresa e deve ser acessível a partir do dispositivo.

   Se você não especificar sua própria URL, o Intune fornecerá um link para detalhes genéricos que não podem abranger todos os cenários. Essa orientação genérica pode não ser precisa para o seu ambiente.

5. Selecione uma ou mais opções para **tipo de notificação**. Os tipos de notificação são os métodos que você usa para informar os usuários sobre os seguintes cenários:

   - Registre um dispositivo com um emissor para obter uma nova credencial derivada.
   - Obtenha uma nova credencial derivada quando a credencial atual estiver perto da expiração.
   - Use uma credencial derivada com uma política para Wi-Fi, VPN, email ou autenticação de aplicativo e para assinatura e criptografia S/MIME.

6. Quando estiver pronto, selecione **salvar** para concluir a configuração do emissor de credencial derivada.

Depois de salvar a configuração, você pode fazer alterações em todos os campos, exceto para o *emissor de credencial derivada*.  Para alterar o emissor, consulte [alterar o emissor de credencial derivada](#change-the-derived-credential-issuer).

## <a name="deploy-the-disa-purebred-app"></a>Implantar o aplicativo DISA purebred

*Esta seção se aplica somente quando você usa Disa purebred*.

Para usar o **Disa purebred** como seu emissor de credencial derivado para o Intune, você deve obter o aplicativo Disa purebred e, em seguida, usar o Intune para implantar o aplicativo em dispositivos. Os usuários do dispositivo usam o aplicativo em seu dispositivo para solicitar a credencial derivada de DISA purebred.

Além de implantar o aplicativo com o Intune, configure uma VPN por aplicativo do Intune para o aplicativo DISA purebred.

**Conclua as seguintes tarefas**:
  
1. Baixe o [aplicativo Disa purebred](https://cyber.mil/pki-pke/purebred/).
2. Implante o aplicativo DISA purebred no Intune.  Consulte [Adicionar um aplicativo de linha de negócios do Ios a Microsoft Intune](../apps/lob-apps-ios.md).
3. [Crie uma VPN por aplicativo](../configuration/vpn-settings-configure.md) para o aplicativo Disa purebred.

## <a name="use-derived-credentials-for-authentication-and-smime-signing-and-encryption"></a>Usar credenciais derivadas para autenticação e assinatura e criptografia S/MIME

Você pode especificar **credenciais derivadas** para os seguintes tipos de perfil e finalidades:

- [Aplicativos](#use-derived-credentials-for-app-authentication)
- [Email](../configuration/email-settings-ios.md)
- [VPN](../configuration/vpn-settings-ios.md)
- [Assinatura e criptografia S/MIME](certificates-s-mime-encryption-sign.md)
- [Wi-Fi](../configuration/wi-fi-settings-ios.md)

  Para perfis Wi-Fi, o *método de autenticação* estará disponível somente quando o tipo de **EAP** for definido como um dos seguintes valores:
  - EAP – TLS
  - EAP-TTLS
  - PEAP

### <a name="use-derived-credentials-for-app-authentication"></a>Usar credenciais derivadas para autenticação de aplicativo

Use credenciais derivadas para a autenticação baseada em certificado para sites e aplicativos da Web. Para fornecer uma credencial derivada para autenticação de aplicativo, execute as seguintes etapas no console do Intune:  

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e vá para **configuração do dispositivo**  > **perfis** e selecione **Criar perfil**.

2. Insira um nome amigável para o perfil em **nome**.

3. Em **Plataforma**, selecione **iOS**.

4. Para **tipo de perfil**, selecione **credencial derivada**.

5. Selecione **OK** e, em seguida, clique em **criar**.

6. Selecione **atribuições** para escolher quais grupos devem receber a política.
 
Os usuários recebem a notificação de aplicativo ou email dependendo das configurações que você especificou ao configurar o emissor de credencial derivada. A notificação informa o usuário para iniciar o Portal da Empresa para que as políticas de credenciais derivadas possam ser processadas.

## <a name="renew-a-derived-credential"></a>Renovar uma credencial derivada

As credenciais derivadas não podem ser estendidas ou renovadas. Em vez disso, os usuários devem usar o fluxo de trabalho de solicitação de credenciais para solicitar uma nova credencial derivada para seu dispositivo.

Se você configurar um ou mais métodos para o **tipo de notificação**, o Intune notificará automaticamente os usuários quando a credencial derivada atual atingir 80% de seu período de vida. A notificação direciona os usuários para passar pelo processo de solicitação de credencial para obter uma nova credencial derivada.

Depois que um dispositivo recebe uma nova credencial derivada, as políticas que usam credenciais derivadas Reimplantam nesse dispositivo.


## <a name="change-the-derived-credential-issuer"></a>Alterar o emissor de credencial derivada

No nível do locatário, você pode alterar o emissor de credencial, embora apenas um emissor tenha suporte para um locatário por vez.

Depois de alterar o emissor, os usuários receberão uma solicitação para obter uma nova credencial derivada do novo emissor. Eles devem fazer isso antes de poderem usar uma credencial derivada para autenticação.

### <a name="change-the-issuer-for-your-tenant"></a>Alterar o emissor para seu locatário

> [!IMPORTANT]  
> Se você excluir um emissor e reconfigurar imediatamente esse mesmo emissor, ainda deverá atualizar perfis e dispositivos para usar credenciais derivadas desse emissor. As credenciais derivadas que foram obtidas antes da exclusão do emissor não são mais válidas.

1. Entre no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e vá para **configuração do dispositivo**  > **credenciais derivadas**.

2. Selecione **excluir** para remover o emissor de credencial derivada atual.

3. Configure um novo emissor.

### <a name="update-profiles-that-use-derived-credentials"></a>Atualizar perfis que usam credenciais derivadas

Depois de excluir um emissor e, em seguida, adicionar um novo, edite cada perfil que usa credenciais derivadas. Essa regra se aplica mesmo se você restaurar o emissor anterior. Qualquer edição do perfil disparará uma atualização, incluindo uma edição simples para a *Descrição*do perfil.

### <a name="update-derived-credentials-on-devices"></a>Atualizar credenciais derivadas em dispositivos

Depois de excluir um emissor e, em seguida, adicionar um novo, os usuários do dispositivo deverão solicitar uma nova credencial derivada. Essa regra se aplica mesmo quando você adiciona o mesmo emissor que você removeu. O processo para solicitar a nova credencial derivada é o mesmo para registrar um novo dispositivo ou renovar uma credencial existente.

## <a name="next-steps"></a>Próximos passos

[Criar perfis de configuração de dispositivo](../configuration/device-profile-create.md)
