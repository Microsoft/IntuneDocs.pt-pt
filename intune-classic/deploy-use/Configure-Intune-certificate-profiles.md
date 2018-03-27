---
title: Configurar perfis de certificado
description: Saiba como criar um perfil de certificado do Intune.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 10/25/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ROBOTS: NOINDEX,NOFOLLOW
ms.reviewer: kmyrup
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: d6230fbc50ae79702cfd938f158d2961b5d720c9
ms.sourcegitcommit: df60d03a0ed54964e91879f56c4ef0a7507c17d4
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/22/2018
---
# <a name="configure-intune-certificate-profiles"></a>Configurar perfis de certificado do Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Após ter configurado a infraestrutura e os certificados, conforme descrito em [Configurar a infraestrutura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) ou em [Configurar a infraestrutura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md), pode criar perfis de certificados. Eis o processo:

- **Tarefa 1**: exportar o certificado da AC de Raiz Fidedigna
- **Tarefa 2**: criar perfis de certificado Fidedignos
- **Tarefa 3**: criar um de dois tipos de perfil de certificado:
  - Perfis de certificado de SCEP
  - Perfis de certificado .PFX

## <a name="task-1-export-the-trusted-root-ca-certificate"></a>**Tarefa 1**: exportar o certificado da AC de Raiz Fidedigna
Exporte o certificado de Autoridades de Certificação(AC) de Raiz Fidedigna como um ficheiro **.cer** a partir da AC emissora ou de qualquer dispositivo que confie na sua AC emissora. Não exporte a chave privada.

Irá importar este certificado quando configurar um perfil de certificado Fidedigno.

## <a name="task-2-create-trusted-certificate-profiles"></a>**Tarefa 2**: criar perfis de certificado Fidedignos
Tem de criar um perfil de certificado Fidedigno antes de poder criar um protocolo SCEP (Simple Certificate Enrollment Protocol) ou um perfil de certificado PKCS n.º 12 (.PFX). Precisará de um perfil de certificado Fidedigno e de um perfil SCEP ou .PFX para cada plataforma de dispositivo móvel.

### <a name="to-create-a-trusted-certificate-profile"></a>Para criar um perfil de certificado Fidedigno

1.  Na [consola de administração do Intune](https://manage.microsoft.com), selecione **Política** &gt; **Adicionar Política** e selecione uma plataforma de dispositivo. Pode criar um perfil de certificado fidedigno para estes dispositivos:

-  Android 4 e posterior

-  Android for Work

-  iOS 7.1 e posterior

-  Mac OS X 10.9 e posterior

-  Windows 8.1 e posterior

-  Windows Phone 8.1 e posterior

2.  Adicione uma política **Perfil de Certificado Fidedigno**.

    Saiba mais: [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Introduza as informações pedidas para configurar as definições de perfil de certificado Fidedigno para Android, iOS, Mac OS X, Windows 8.1 ou Windows Phone 8.1.
4.  Na definição **Ficheiro de certificado**, importe o certificado da AC de Raiz Fidedigna (ficheiro .cer) que exportou a partir da sua AC emissora. A definição **Arquivo de destino** aplica-se apenas a dispositivos com o Windows 8.1 e posterior e apenas se o dispositivo tiver mais do que um arquivo de certificados.

4.  Escolha **Guardar Política**.

A nova política é mostrada na área de trabalho **Política**. Pode agora implementá-la.

> [!NOTE]
>
> Os dispositivos Android e Android for Work irão apresentar um aviso a indicar que uma aplicação de terceiros instalou um certificado fidedigno.


## <a name="task-3-create-scep-or-pfx-certificate-profiles"></a>**Tarefa 3**: criar perfis de certificado de SCEP ou .PFX
Após criar um perfil de certificado da AC Fidedigna, crie perfis de certificado de SCEP ou .PFX para cada plataforma que pretende utilizar. Ao criar um perfil de certificado de SCEP, tem de especificar um perfil de certificado Fidedigno para a mesma plataforma. Esta ação liga os dois perfis de certificado, mas tem na mesma de implementar cada perfil separadamente.

### <a name="to-create-an-scep-certificate-profile"></a>Para criar um perfil de certificado de SCEP

1.  Na [consola de administração do Intune](https://manage.microsoft.com), selecione **Política** &gt; **Adicionar Política** e selecione uma plataforma de dispositivo.  Pode criar um perfil de certificado de SCEP para estes dispositivos:

-  Android 4 e posterior

-  Android for Work

-  iOS 7.1 e posterior

-  Mac OS X 10.9 e posterior

-  Windows 8.1 e posterior

-  Windows Phone 8.1 e posterior

2.  Adicionar uma política **Perfil de Certificado de SCEP**

    Saiba mais: [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Siga as instruções na página de configuração do perfil para configurar as definições do perfil de certificado de SCEP.
    > [!NOTE]
    >
    > Em **Formato de nome do requerente**, selecione **Personalizado** para introduzir um formato de nome do requerente (apenas nos perfis iOS).
    >
    > As duas variáveis atualmente suportadas pelo formato personalizado são `Common Name (CN)` e `Email (E)`. Através de uma combinação destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado, como o seguinte:

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > Neste exemplo, o administrador criou um formato de nome de requerente que, além das variáveis `CN` e `E`, utiliza cadeias para os valores Unidade Organizacional, Organização, Localização, Estado e País. A [função CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) lista as cadeias suportadas.

4.  Escolha **Guardar Política**.

A nova política é mostrada na área de trabalho **Política**. Pode agora implementá-la.

### <a name="to-create-a-pfx-certificate-profile"></a>Para criar um perfil de certificado .PFX

1.  Na [consola de administração do Intune](https://manage.microsoft.com), selecione **Política** &gt; **Adicionar Política** e selecione uma plataforma de dispositivo. Os certificados .PFX são suportados para:
  - Android 4 e posterior
  - Android for Work
  - Windows 10 e posterior
  - Windows Phone 10 e posterior
  - iOS 8.0 e posterior)    


2.  Adicione uma política **Perfil de Certificado .PFX**.
      Saiba mais: [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3.  Introduza as informações pedidas no formulário da política.
4.  Escolha **Guardar Política**.

A nova política é mostrada na área de trabalho **Política**. Pode agora implementá-la.

## <a name="deploy-certificate-profiles"></a>Implementar perfis de certificado
Ao implementar perfis de certificado, o ficheiro de certificado do perfil de certificado da AC fidedigna é instalado no dispositivo. O dispositivo utiliza o perfil de certificado de SCEP ou .PFX para criar um pedido de certificado por parte do dispositivo.

Os perfis de certificado são instalados apenas em dispositivos que executam a plataforma que utiliza ao criar o perfil.

-   Pode implementar perfis de certificado em coleções de utilizadores ou de dispositivos.

    > [!TIP]
    > Para publicar um certificado num dispositivo rapidamente após a inscrição do mesmo, implemente o perfil de certificado num grupo de utilizadores, em vez de num grupo de dispositivos. Se implementar num grupo de dispositivos, é necessário um registo do dispositivo completo antes de o dispositivo receber políticas.

-   Apesar de implementar cada perfil separadamente, também terá de implementar a AC da Raiz Fidedigna e o perfil SCEP ou .PFX. Caso contrário, a política de certificados de SCEP ou .PFX irá falhar.

Implemente perfis de certificado da mesma forma que implementa outras políticas no Intune:

1.  Na área de trabalho **Policy**, selecione a política que pretende implementar e, em seguida, escolha **Manage Deployment**.
2.  Na caixa de diálogo **Manage Deployment**, para:
    -   **To deploy the policy**, selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, escolha **Add** &gt; **OK**.
    -   **Para fechar a caixa de diálogo sem implementar a política**, escolha **Cancel**.

Ao selecionar uma política implementada, pode ver mais informações sobre a implementação na parte inferior da lista de políticas.

### <a name="next-steps"></a>Próximos passos

Em seguida, pode utilizar certificados para ajudar a proteger os perfis de e-mail, Wi-Fi e VPN.

-  [Configurar o acesso a e-mail empresarial através de perfis de e-mail](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Ligações Wi-Fi no Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [Ligações VPN no Microsoft Intune](vpn-connections-in-microsoft-intune.md)
