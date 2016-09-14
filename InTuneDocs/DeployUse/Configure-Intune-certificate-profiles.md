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
ms.sourcegitcommit: 8e3f7cac8eb3495aad3835ec4713d67a58383c66
ms.openlocfilehash: 8b08f8fde6136b8eca61f6ae7a8c21635f7d452e


---

# Configurar perfis de certificado do Intune
Após ter configurado a infraestrutura e os certificados, conforme descrito em [Configurar a infraestrutura de certificados para SCEP](configure-certificate-infrastructure-for-scep.md) ou em [Configurar a infraestrutura de certificados para PFX](configure-certificate-infrastructure-for-pfx.md), pode criar perfis de certificados. Eis o processo:

- **Tarefa 1**: exportar o certificado da AC de Raiz Fidedigna
- **Tarefa 2**: criar perfis de certificado Fidedignos
- **Tarefa 3**: criar um de dois tipos de perfil de certificado:
  - Perfis de certificado SCEP
  - Perfis de certificado .PFX

## **Tarefa 1**: exportar o certificado da AC de Raiz Fidedigna
Exporte o certificado de Autoridades de Certificação(AC) de Raiz Fidedigna como um ficheiro **.cer** a partir da AC emissora ou de qualquer dispositivo que confie na sua AC emissora. Não exporte a chave privada.

Irá importar este certificado quando configurar um perfil de certificado Fidedigno.

## **Tarefa 2**: criar perfis de certificado Fidedignos
Tem de criar um perfil de certificado Fidedigno antes de poder criar um protocolo SCEP (Simple Certificate Enrollment Protocol) ou um perfil de certificado PKCS n.º 12 (.PFX). Precisará de um perfil de certificado Fidedigno e de um perfil SCEP ou .PFX para cada plataforma de dispositivo móvel.

### Para criar um perfil de certificado Fidedigno

1.  Na [consola de administração do Intune](https://manage.microsoft.com), escolha **Política** &gt; **Adicionar Política**.
2.  Adicione um dos seguintes tipos de política:
    - **Android &gt; Perfil de Certificado Fidedigno (Android 4 e posterior)**
    - **iOS &gt; Perfil de Certificado Fidedigno (iOS 7.1 e posterior)**
    - **Mac OS X &gt; Perfil de Certificado Fidedigno (Mac OS X 10.9 e posterior)**
    - **Windows &gt; Perfil de Certificado Fidedigno (Windows 8.1 e posterior)**
    - **Windows &gt; Perfil de Certificado Fidedigno (Windows Phone 8.1 e posterior)**

    Saiba mais: [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Introduza as informações pedidas para configurar as definições de perfil de certificado Fidedigno para Android, iOS, Mac OS X, Windows 8.1 ou Windows Phone 8.1.

    - Na definição **Ficheiro de certificado**, importe o certificado da AC de Raiz Fidedigna (ficheiro .cer) que exportou a partir da sua AC emissora. A definição **Arquivo de destino** aplica-se apenas a dispositivos com o Windows 8.1 e posterior e apenas se o dispositivo tiver mais do que um arquivo de certificados.
    -  Em **Formato do nome do requerente**, selecione **Personalizado** para introduzir um formato de nome de requerente personalizado.  
        As duas variáveis atualmente suportadas pelo formato personalizado são `Common Name (CN)` e `Email (E)`. Através de uma combinação destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado,como o seguinte:  

        `CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US`  

        Neste exemplo, o administrador criou um formato de nome de requerente que, além das variáveis `CN` e `E`, utiliza cadeias para os valores Unidade Organizacional, Organização, Localização, Estado e País. A [função CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) lista as cadeias suportadas.  
4.  Escolha **Guardar Política**.

A nova política é mostrada na área de trabalho **Política**. Pode agora implementá-la.

## **Tarefa 3**: criar perfis de certificado SCEP ou .PFX
Após criar um perfil de certificado da AC Fidedigna, crie perfis de certificado SCEP ou .PFX para cada plataforma que pretende utilizar. Ao criar um perfil de certificado SCEP, tem de especificar um perfil de certificado Fidedigno para a mesma plataforma. Esta ação liga os dois perfis de certificado, mas tem na mesma de implementar cada perfil separadamente.

### Para criar um perfil de certificado SCEP

1.  Na [consola de administração do Intune](https://manage.microsoft.com), escolha **Política** &gt; **Adicionar Política**.
2.  Adicione um dos seguintes tipos de política:
    - **Android &gt; Perfil de Certificado SCEP (Android 4 e posterior)**
    - **iOS &gt; Perfil de Certificado SCEP (iOS 7.1 e posterior)**
    - **Mac OS X &gt; Perfil de Certificado de SCEP (Mac OS X 10.9 e posterior)**
    - **Windows &gt; Perfil de Certificado SCEP (Windows 8.1 e posterior)**
    - **Windows &gt; Perfil de Certificado SCEP (Windows Phone 8.1 e posterior)**

    Saiba mais: [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).

3.  Siga as instruções na página de configuração do perfil para configurar as definições do perfil de certificado SCEP.
    > [!NOTE]
    >
    > Em **Formato do nome do requerente**, selecione **Personalizado** para introduzir um formato de nome de requerente personalizado.
    >
    > As duas variáveis atualmente suportadas pelo formato personalizado são `Common Name (CN)` e `Email (E)`. Através de uma combinação destas variáveis e cadeias estáticas, pode criar um formato de nome de requerente personalizado,como o seguinte:

    >     CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US

    > Neste exemplo, o administrador criou um formato de nome de requerente que, além das variáveis `CN` e `E`, utiliza cadeias para os valores Unidade Organizacional, Organização, Localização, Estado e País. A [função CertStrToName](https://msdn.microsoft.com/en-us/library/windows/desktop/aa377160.aspx) lista as cadeias suportadas.

4.  Escolha **Guardar Política**.

A nova política é mostrada na área de trabalho **Política**. Pode agora implementá-la.

### Para criar um perfil de certificado .PFX

1.  Na [consola de administração do Intune](https://manage.microsoft.com), escolha **Política** &gt; **Adicionar Política**.
2.  Adicione um dos seguintes tipos de política:
  - **Android &gt; Perfil de Certificado .PFX (Android 4 e posterior)**
  - **Windows &gt; Perfil de Certificado PKCS n.º 12 (.PFX) (Windows 10 e posterior)**
  - **Windows &gt; Perfil de Certificado PKCS n.º 12 (.PFX) (Windows Phone 10 e posterior)**
  - **iOS > Perfil de Certificado PKCS #12 (.PFX) (iOS 7.1 e posterior)**    
    Saiba mais: [Gerir definições e funcionalidades nos seus dispositivos com as políticas do Microsoft Intune](manage-settings-and-features-on-your-devices-with-microsoft-intune-policies.md).
3.  Introduza as informações pedidas no formulário da política.
4.  Escolha **Guardar Política**.

A nova política é mostrada na área de trabalho **Política**. Pode agora implementá-la.

## Implementar perfis de certificado
Ao implementar perfis de certificado, o ficheiro de certificado do perfil de certificado da AC fidedigna é instalado no dispositivo. O dispositivo utiliza o perfil de certificado SCEP ou .PFX para criar um pedido de certificado por parte do dispositivo.

Os perfis de certificado são instalados apenas em dispositivos que executam a plataforma que utiliza ao criar o perfil.

-   Pode implementar perfis de certificado em coleções de utilizadores ou de dispositivos.

    > [!TIP]
    > Para publicar um certificado num dispositivo rapidamente após a inscrição do mesmo, implemente o perfil de certificado num grupo de utilizadores, em vez de num grupo de dispositivos. Se implementar num grupo de dispositivos, é necessário um registo do dispositivo completo antes de o dispositivo receber políticas.

-   Apesar de implementar cada perfil separadamente, também terá de implementar a AC da Raiz Fidedigna e o perfil SCEP ou .PFX. Caso contrário, a política de certificados SCEP ou .PFX irá falhar.

Implemente perfis de certificado da mesma forma que implementa outras políticas no Intune:

1.  Na área de trabalho **Política**, selecione a política que pretende implementar e, em seguida, escolha **Gerir Implementação**.
2.  Na caixa de diálogo **Gerir a Implementação** , para:
    -   **Para implementar a política**, selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, escolha **Adicionar** &gt; **OK**.
    -   **Para fechar a caixa de diálogo sem implementar a política**, escolha **Cancelar**.

Ao selecionar uma política implementada, pode ver mais informações sobre a implementação na parte inferior da lista de políticas.

### Passos seguintes

Em seguida, pode utilizar certificados para ajudar a proteger os perfis de e-mail, Wi-Fi e VPN.

-  [Configurar o acesso a e-mail empresarial através de perfis de e-mail](configure-access-to-corporate-email-using-email-profiles-with-Microsoft-Intune.md)
-  [Ligações Wi-Fi no Microsoft Intune](wi-fi-connections-in-microsoft-intune.md)
-  [Ligações VPN no Microsoft Intune](vpn-connections-in-microsoft-intune.md)



<!--HONumber=Aug16_HO5-->


