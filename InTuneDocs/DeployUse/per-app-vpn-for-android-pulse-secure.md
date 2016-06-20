---
# required metadata

title: VPN por aplicação para Android com Pulse Secure | Microsoft Intune
description:
keywords:
author: nbigman
manager: jeffgilb
ms.date: 05/08/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ac65e906-3922-429f-8d9c-d313d3126645

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
#ms.reviewer: chrisbal
#ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Utilizar uma política personalizada para criar um perfil de VPN por aplicação para dispositivos Android

Pode criar um perfil de VPN por aplicação para dispositivos Android geridos pelo Intune. Em primeiro lugar, irá criar um perfil de VPN que utiliza o tipo de ligação Pulse Secure e, em seguida, uma política de configuração personalizada que associa esse perfil a aplicações específicas. Depois de implementar essas políticas no dispositivo Android ou grupos de utilizador, abrir uma das aplicações especificadas nesses dispositivos irá abrir uma ligação VPN para essa aplicação. 

### Passo 1: criar um perfil de VPN

1. Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** > **Adicionar Política**.
2. Selecione um modelo para a nova política, expandindo **Android** e, em seguida, escolha **Perfil de VPN (Android 4 e posterior)**.

3. No modelo, em **Tipo de ligação**, escolha **Pulse Secure**.
4. Preencha e guarde o perfil de VPN. Para obter mais detalhes sobre perfis de VPN, veja [Perfis da VPN](Help%20users%20connect%20to%20their%20work%20using%20VPN%20profiles%20with%20Microsoft%20Intune.md).

> [!NOTE]
Tome nota do nome do perfil de VPN para utilização no próximo passo. Por exemplo, **MyAppVpnProfile**.
   
### Passo 2: criar uma política de configuração personalizada
    
   1. Na consola de administração do Intune, clique em **Política** -> **Adicionar Política** -> **Android** -> **Configuração Personalizada** -> **Criar Política**.
   2. Forneça um nome para a política.
   3. Em **Definições OMA-URI**, clique em **Adicionar**.
   4. Forneça um nome para a definição.
   5. Em **Tipo de dados**, especifique **Cadeia**.
   6. em **OMA-URI**, especifique esta cadeia: **./Vendor/MSFT/VPN/Profile/*Name*/PackageList**, onde *Name* é o nome do perfil de VPN que anotou no Passo 1. No nosso exemplo, a cadeia seria **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/PackageList**.
   7.   Em **Valor**, forneça uma lista separada por ponto e vírgula dos pacotes que devem ser associados ao perfil.  Por exemplo, se pretender que o Excel e o browser Google Chrome utilizem a ligação VPN, irá introduzir: **com.microsoft.office.excel;com.android.chrome**.
  

   ![Exemplo de política personalizada de VPN por aplicação Android](..\media\android_per_app_vpn_oma_uri.png) 
#### Definir a lista de aplicações como Lista de Não Permitidos ou Lista de Permitidos (opcional)
Pode especificar que a sua lista de aplicações *não* irá ter permissão para utilizar a ligação VPN com o valor **BLACKLIST**.  Todas as outras aplicações estabelecerão ligação através de VPN.

Em alternativa, pode especificar que *apenas* as aplicações especificadas podem utilizar a ligação VPN com o valor **WHITELIST**.
 

1.  Em Definições OMA-URI, clique em **Adicionar**.
2.  Forneça um nome para a definição.
3.  Em **Tipo de dados**, especifique **Cadeia**.
4.  Em **OMA-URI**, especifique esta cadeia: **./Vendor/MSFT/VPN/Profile/*Name*/Mode**, onde *Name* é o nome do perfil de VPN que anotou no Passo 1. No nosso exemplo, a cadeia seria **./Vendor/MSFT/VPN/Profile/MyAppVpnProfile/Mode**.
5.  Em **Valor**, introduza **BLACKLIST** ou **WHITELIST**. 


   
### Passo 3: implementar as duas políticas

Tem de implementar as *duas* políticas nos *mesmos* grupos do Intune.

   1.  Na área de trabalho **Política** , selecione a política que pretende implementar e, em seguida, clique em **Gerir Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação** , para:

    -   **Para implementar a política** - selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, clique em **Adicionar** &gt; **OK**.

    -   **Fechar a caixa de diálogo sem implementar a política** - clique em **Cancelar**.

Um resumo do estado e alertas na página **Descrição Geral** da área de trabalho **Política** identificam problemas com a política que necessitam da sua atenção. Para além disso, é apresentado um resumo de estado na área de trabalho Dashboard.



<!--HONumber=Jun16_HO1-->

