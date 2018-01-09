---
title: "Configurar a VPN por Aplicação no Microsoft Intune para dispositivos iOS"
titleSuffix: Intune on Azure
description: "Especifique que aplicações geridas podem utilizar a VPN em dispositivos iOS geridos pelo Intune."
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 10/5/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: D9958CBF-34BF-41C2-A86C-28F832F87C94
ms.reviewer: karanda
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 1a37fcc372db6fec9f460fdc242cd6d2294f96e1
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/04/2018
---
# <a name="set-up-per-app-vpn-in-microsoft-intune-for-ios-devices"></a>Configurar a VPN por Aplicação no Microsoft Intune para dispositivos iOS

Pode especificar que aplicações geridas podem utilizar a Rede Privada Virtual (VPN) em dispositivos iOS geridos pelo Intune. Quando especifica a VPN por Aplicação no Intune, um utilizador final estabelece ligação automaticamente através da VPN ao aceder a documentos empresariais.

## <a name="prerequisites-for-the-per-app-vpn"></a>Pré-requisitos para a VPN por Aplicação

Para provar a identidade, o servidor VPN apresenta o certificado que tem de ser aceite sem um pedido pelo dispositivo. Para garantir a aprovação automática do certificado, crie um perfil de certificado fidedigno que contém o certificado de raiz do servidor VPN emitido pela Autoridade de Certificação (AC). 

Exporte o certificado e adicione a AC.

1. Abra a consola de administração no servidor VPN.
2. Verifique se o servidor VPN utiliza a Autenticação Baseada em Certificados. 
3. Exporte o ficheiro de certificado de raiz fidedigno. Tem uma extensão .cer e tem de adicioná-la ao criar um perfil de certificado fidedigno.
4. Adicione o nome da AC que emitiu o certificado para autenticação ao servidor VPN.
    Se a AC apresentada pelo dispositivo corresponder a uma das ACs na lista de ACs Fidedignas no servidor VPN, o servidor VPN efetua a autenticação do dispositivo com êxito.

## <a name="create-a--group-for-your-vpn-users"></a>Criar um grupo para os utilizadores de VPN

Crie ou selecione um grupo existente no Azure Active Directory (Azure AD) para conter os membros que têm acesso à VPN por Aplicação.

1. Abra o portal do Azure. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
2. Selecione **Grupos** e clique em **Novo grupo**.
3. Escreva o **Nome** do grupo. 
4. Escreva a **Descrição** do grupo. 
5. Selecione **Atribuído** para o **Tipo de associação**.
6. Selecione **Não** para **Ativar funcionalidades do Office**.
7. Procure os utilizadores de VPN por nome ou endereço de e-mail no painel **Membros**.
8. Selecione cada utilizador e clique em **Selecionar**.
9. Clique em **Criar**

## <a name="create-a-trusted-certificate-profile"></a>Criar um perfil de certificado fidedigno

Importe o certificado de raiz do servidor VPN emitido pela AC para um perfil criado no Intune. O perfil de certificado fidedigno indica ao dispositivo iOS para confiar automaticamente na AC que o servidor VPN apresenta.

1. Abra o portal do Azure. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
2. Selecione **Configuração do dispositivo** e, em seguida, clique em **Perfis**.
3. Clique em **+ Criar perfil**. Em **Criar perfil**:
    1. Escreva o **Nome**.
    2. Escreva a **Descrição**.
    3. Selecione **iOS** para a **Plataforma**.
    4. Selecione **Certificado fidedigno** para o **Tipo de perfil**.
4. Clique no ícone da pasta e procure o certificado VPN (ficheiro .cer) que exportou da consola de administração da VPN. Clique em OK
5. Clique em **Criar**.

    ![Criar um perfil de certificado fidedigno](media\vpn-per-app-create-trusted-cert.png)

## <a name="create-a-scep-certificate-profile"></a>Criar um perfil de certificado SCEP

O perfil do certificado de raiz fidedigno permite que o iOS confie automaticamente no Servidor VPN. O certificado SCEP fornece credenciais do cliente VPN para iOS para o servidor VPN. O certificado permite que o dispositivo seja autenticado automaticamente sem pedir ao utilizador do dispositivo iOS um nome de utilizador e palavra-passe. 

1. Abra o portal do Azure. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**. 
2. Selecione **Configuração do dispositivo** e, em seguida, clique em **Perfis**.
3. Clique em **+ Criar perfil**. Em **Criar perfil**:
    1. Escreva o **Nome**.
    2. Escreva a **Descrição**.
    3. Selecione **iOS** para a **Plataforma**.
    4. Selecione **Certificado SCEP** para o **Tipo de perfil**.
4. Selecione **Anos** e escreva `2` para o **Período de validade do certificado**.
5. Selecione **Nome comum** para o **Formato do nome do requerente**.
6. Selecione **Nome principal de utilizador (UPN)** para o **Nome alternativo do requerente**.
7. Selecione **Assinatura digital** e **Encriptação de chaves** para a **Utilização de chaves**.
8. Selecione **2048** para o **Tamanho de chave (bits)**.
9. Clique em Certificado de Raiz e selecione um Certificado SCEP. Clique em **OK**.
10. Escreva `Client Authentication` no **Nome** para a **Utilização de chave alargada**.
11. Escreva `1.3.6.1.5.5.7.3.2` no **Identificador de Objeto**.
12. Clique em **Adicionar**.
13. Escreva o ***URL do Servidor*** e clique em **Adicionar**.
14. Clique em **OK**.
15. Clique em **Criar**.

    ![Criar um perfil de certificado SCEP](media\vpn-per-app-create-scep-cert.png)

## <a name="create-a-per-app-vpn-profile"></a>Criar um perfil VPN por Aplicação

O perfil VPN contém o certificado SCEP com as credenciais de cliente, as informações de ligação à VPN e o sinalizador de VPN por Aplicação para ativar a funcionalidade VPN por Aplicação para utilização pela aplicação iOS.

1. Abra o portal do Azure. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
2. Selecione **Configuração do dispositivo** e, em seguida, clique em **Perfis**.
3. Clique em **+ Criar perfil**. Em **Criar perfil**:
    1. Escreva o **Nome**.
    2. Escreva a **Descrição**.
    3. Selecione **iOS** para a **Plataforma**.
    4. Selecione **VPN** para o **Tipo de perfil**.
4. Selecione **VPN Base**. Em **VPN Base**:
    1. Escreva o **Nome da ligação**.
    2. Escreva o **Endereço IP ou FQDN**.
    3. Selecione **Certificados** para o **Método de autenticação**.
    4. Selecione o certificado SCEP em **Certificado de autenticação** e clique em **OK**.
    5. Selecione a VPN para o **Tipo de ligação**.
    6. Se necessário, configure os atributos da VPN.
    7. Selecione **Desativar Dividir Túnel**.
5. Clique em **VPN Automática**. Em **VPN Automática**:
    1. Selecione **VPN por Aplicação** para o **Tipo de VPN automática**.
    2. Escreva o URL da VPN e clique em **Adicionar**.
    3. Clique em **OK**.
6. Clique em **OK**.
7. Clique em **Criar**.

    ![Criar um perfil VPN por Aplicação](media\vpn-per-app-create-vpn-profile.png)


## <a name="associate-an-app-with-the-vpn-profile"></a>Associar uma aplicação ao perfil VPN

Depois de adicionar o perfil VPN, associe a aplicação e o grupo do Azure AD ao perfil.

1. Abra o portal do Azure. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
2. Selecione **Aplicações Móveis**.
3. Clique em **Aplicações**.
4. Selecione a aplicação a partir da lista de aplicações.
5. Clique em **Tarefas.**
6. Clique em **Selecionar grupos**, selecione o grupo que definiu anteriormente. Clique em **Selecionar**.
7. Selecione **Necessário** para o **Tipo** no painel **Tarefas**.
8. Selecione a definição de VPN para **VPNS**.
 
    > [!NOTE]  
    > Por vezes a definição de VPN demora um minuto para obter o valor. Aguarde 3 a 5 minutos antes de clicar em **Guardar**.

9. Clique em **Guardar**.

    ![Associar uma aplicação à VPN](media\vpn-per-app-app-to-vpn.png)

## <a name="verify-the-connection-on-the-ios-device"></a>Verificar a ligação no dispositivo iOS

Com a configuração de VPN por Aplicação associada à sua aplicação, verifique se a ligação funciona a partir de um dispositivo.

### <a name="before-you-attempt-to-connect"></a>Antes de tentar estabelecer ligação

 - Certifique-se de que está a executar o iOS 7 ou posterior.
 - Certifique-se de que implementa *todas* as políticas mencionadas acima para o mesmo grupo de utilizadores. Se não o fizer, irá interromper a experiência de VPN por Aplicação.  
 - Certifique-se de que tem a aplicação VPN de terceiros suportada instalada. As seguintes aplicações VPN são suportadas:
    - Pulse Secure
    - Check Point
    - F5
    - SonicWall

### <a name="connect-using-the-per-app-vpn"></a>Estabelecer ligação com a VPN por Aplicação

Verifique a experiência sem contacto ao estabelecer ligação sem ter de selecionar a VPN ou escrever as suas credenciais. A experiência sem contacto significa que:

 - O dispositivo não lhe pede para confiar no servidor VPN. Ou seja, vê a caixa de diálogo **Confiança Dinâmica**.
 - Não tem de escrever as credenciais.
 - Está ligado à VPN após tocar no botão Ligar.

Verifique a ligação num dispositivo iOS.

1. Toque na aplicação VPN.
2. Toque em **Ligar**.  
A VPN estabelece ligação com êxito sem pedidos adicionais.

<!-- ## Troubleshooting the Per-App VPN

The user experiences the feature by silently connecting to the VPN. This experience, however, can provide little information for troubleshooting. You can review the event logs crated by the iOS device.

`Note -- use the Apple Configurator as the supported tool. Only runs on a mac.'

To review event logs:

1. Connect your iOS device to a PC
2. Open the **iPhone Configuration Utility** (IPCU). If you do not have a copy, you can install it from [CompatCenter](http://www.microsoft.com/en-us/windows/compatibility/CompatCenter/ProductDetailsViewer?Name=iPhone%20Configuration%20Utility&vendor=Apple&Locale=1033%2C2057%2C3081%2C4105%2C16393&ModelOrVersion=3&BreadCrumbPath=iphone%20configuration%20utility&LastSearchTerm=iphone%2Bconfiguration%2Butility&Type=Software&tempOsid=Windows%208.1)
3. Review the logs. -->

## <a name="next-steps"></a>Próximos passos

- Para rever as definições do iOS, veja [VPN settings for iOS devices in Microsoft Intune (Definições de VPN para dispositivos iOS no Microsoft Intune)](vpn-settings-ios.md).
-  Para saber mais sobre a definição de VPN e o Intune, veja [How to configure VPN settings in Microsoft Intune (Como configurar as definições de VPN no Microsoft Intune)](vpn-settings-configure.md).