---
title: Configurar perfis de certificado | Microsoft Intune
description: Saiba como criar um perfil de certificado do Intune.
keywords: 
author: nbigman
manager: angrobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 679a20a1-e66f-4b6b-bd8f-896daf1f8175
ms.reviewer: kmyrup
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 6a7f2eeb0114f525890d1dcb61344d60a19943d1
ms.openlocfilehash: 14419092edc77b2229cf980a74e81048941a2c28


---

# Configurar perfis de certificado do Intune
Após a sua infraestrutura e certificados estarem configurados, conforme descrito em [Configurar a infraestrutura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) ou em [Configurar a infraestrutura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md), pode configurar perfis de certificados:

**Tarefa 1** - Exportar o certificado da AC de Raiz Fidedigna **Tarefa 2** - Criar perfis de certificados CA fidedignos **Tarefa 3** - Criar:

Perfis de certificado SCEP

Perfis de certificado .PFX

### Tarefa 1 - Exportar o certificado de Raiz Fidedigna
Exporte o certificado da AC de Raiz Fidedigna como um ficheiro **.cer** a partir da AC emissora ou de qualquer dispositivo que confie na sua AC emissora. Não exporta a chave privada.

Irá importar este certificado quando configurar um perfil de certificado Fidedigno.

### Tarefa 2 - Criar perfis de certificado Fidedignos
Tem de criar um **Perfil de certificado fidedigno** antes de poder criar um perfil de certificado SCEP ou .PFX. Precisará de um perfil de certificado Fidedigno e de um perfil SCEP ou .PFS para cada plataforma de dispositivo móvel.

##### Para criar um perfil de certificado fidedigno

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com) e clique em **Política** &gt; **Adicionar Política**.

2.  Configure um dos seguintes tipos de política:

    **Android &gt; Perfil de Certificado Fidedigno (Android 4 e posterior)**

    **iOS &gt; Perfil de Certificado Fidedigno (iOS 7.1 e posterior)**

    **Mac OS X &gt; Perfil de Certificado Fidedigno (Mac OS X 10.9 e posterior)**

    **Windows &gt; Perfil de Certificado Fidedigno (Windows 8.1 e posterior)**

    **Windows &gt; Perfil de Certificado Fidedigno (Windows Phone 8.1 e posterior)**

    Saiba mais: [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Forneça as informações pedidas para configurar as definições de perfil de certificado fidedigno para Android, iOS, Mac OS X, Windows 8.1 ou Windows Phone 8.1. 

    - Na definição **Ficheiro de certificado**, importe o certificado de AC de Raiz Fidedigna (**.cer**) que exportou a partir da sua AC emissora. A definição **Arquivo de destino** aplica-se apenas a dispositivos com o Windows 8.1 e posterior e apenas se o dispositivo tiver mais do que um arquivo de certificados.

    
    - Em **Formato do nome do requerente**, selecione **Personalizado** para fornecer um formato de nome de requerente personalizado.  

        As duas variáveis atualmente suportadas pelo formato personalizado são **Nome Comum (CN)** e **E-mail (E)**. Através de uma combinação destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado, tal como o mostrado neste exemplo:  

        `CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US`  

        No exemplo, o administrador criou um formato de nome de requerente que, além das variáveis CN e E, utiliza cadeias para Unidade Organizacional, Organização, Localização, Estado e País. É fornecida uma lista das cadeias suportadas no tópico [Função CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx).  


4.  Quando terminar, clique em **Guardar Política**.

A nova política é apresentada na área de trabalho **Política** e pode agora ser implementada.

### Tarefa 3 - criar perfis de certificado SCEP ou .PFX
Após ter criado um perfil de certificado da AC Fidedigna, crie perfis de certificado SCEP ou .PFX para cada plataforma que pretende utilizar. Ao criar um perfil de certificado SCEP, tem de especificar um perfil de certificado Fidedigno para a mesma plataforma. Esta ação liga os dois perfis de certificado. Contudo, tem de implementar cada perfil separadamente.

##### Para criar um perfil de certificado SCEP

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com), clique em **Política** &gt; **Adicionar Política**.

2.  Configure um dos seguintes tipos de política:

    **Android &gt; Perfil de Certificado SCEP (Android 4 e posterior)**

    **iOS &gt; Perfil de Certificado SCEP (iOS 7.1 e posterior)**

    **Mac OS X &gt; Perfil de Certificado de SCEP (Mac OS X 10.9 e posterior)**

    **Windows &gt; Perfil de Certificado SCEP (Windows 8.1 e posterior)**

    **Windows &gt; Perfil de Certificado SCEP (Windows Phone 8.1 e posterior)**

    Saiba mais: [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Siga as instruções na página de configuração do perfil para configurar as definições do perfil de certificado SCEP.
    > [!NOTE]
    > 
    > Em **Formato do nome do requerente**, selecione **Personalizado** para fornecer um formato de nome de requerente personalizado.
    > 
    >  As duas variáveis atualmente suportadas pelo formato personalizado são Nome Comum (CN) e E-mail (E). Através de uma combinação destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado, tal como o mostrado neste exemplo:
    
    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US
    
    >    No exemplo, o administrador criou um formato de nome de requerente que, além das variáveis *CN* e *E*, utiliza cadeias para Unidade Organizacional, Organização, Localização, Estado e País. É fornecida uma lista das cadeias suportadas no tópico [Função CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx).

4.  Quando terminar, clique em **Guardar Política**.

A nova política é apresentada na área de trabalho **Política** e pode agora ser implementada.

##### Para criar um perfil de certificado .PFX

1.  Abra a [consola de administração do Intune](https://manage.microsoft.com), clique em **Política** &gt; **Adicionar Política**.

2.  Configure um dos seguintes tipos de política:



-   **Android &gt; Perfil de Certificado .PFX (Android 4 e posterior)**

    -   **Windows &gt; Perfil de Certificado PKCS #12 (.PFX) (Windows 10 e posterior)**

    -   **Windows &gt; Perfil de Certificado PKCS #12 (.PFX) (Windows Phone 10 e posterior)**

    -    **iOS > Perfil de Certificado PKCS #12 (.PFX) (iOS 7.1 e posterior)**    

    Saiba mais: [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Forneça as informações pedidas no formulário da política.

4.  Quando terminar, clique em **Guardar Política**.

A nova política é apresentada na área de trabalho **Política** e pode agora ser implementada.

## Implementar perfis de certificado
Ao implementar perfis de certificado, o ficheiro de certificado do perfil de certificado da AC Fidedigna é instalado em dispositivos e o perfil de certificado SCEP ou .PFX é utilizado pelo dispositivo para criar um pedido de certificado por parte do dispositivo.

Os perfis de certificado são instalados apenas em dispositivos aplicáveis com base na plataforma que utilizou quando criou o seu perfil.

-   Pode implementar perfis de certificado em coleções de utilizadores ou de dispositivos.

    > [!TIP]
    > Para permitir que os certificados sejam publicados em dispositivos de forma rápida após a inscrição dos mesmos, implemente o perfil de certificado num grupo de utilizadores (não num grupo de dispositivos). Se implementar num grupo de dispositivos, tem de efetuar um registo do dispositivo completo antes de o dispositivo receber a política.

-   Apesar de cada perfil ser implementado separadamente, tanto a Raiz Fidedigna, como o perfil SCEP/.PFX, têm de ser implementados, caso contrário a política de certificados SCEP/.PFX irá falhar.

Implementa perfis de certificado da mesma forma que implementa outra política no Intune:

1.  Na área de trabalho **Política** , selecione a política que pretende implementar e, em seguida, clique em **Gerir Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação** , para:

    -   **Para implementar a política** - selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, clique em **Adicionar** &gt; **OK**.

    -   **Fechar a caixa de diálogo sem implementar a política** - clique em **Cancelar**.

Ao selecionar uma política implementada, pode ver mais informações sobre a implementação na parte inferior da lista de políticas.
###  Passos seguintes

Agora, pode utilizar certificados para ajudar a proteger os perfis de e-mail, Wi-Fi e VPN:

-  [Configurar o acesso a e-mail empresarial através de perfis de e-mail](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Ligações Wi-Fi no Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [Ligações VPN no Microsoft Intune](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Jul16_HO4-->


