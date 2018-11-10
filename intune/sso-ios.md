---
title: Adicionar o início de sessão único para dispositivos iOS no Microsoft Intune – Azure | Microsoft Docs
description: No Microsoft Intune, crie, configure, permita ou ative dispositivos iOS para utilizar o início de sessão único (SSO) em vez da palavra-passe para a autenticação em recursos e dados da sua organização. Para utilizar o SSO, crie um perfil de configuração do dispositivo e introduza o UPN, o ID de dispositivo, as suas aplicações e um certificado para autenticar o utilizador e o dispositivo.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/24/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: d1add113222c2aa7eaea10679c329e877b1a136f
ms.sourcegitcommit: 437eaf364c3b8a38d294397310c770ea4d8a8015
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/24/2018
ms.locfileid: "49992014"
---
# <a name="use-single-sign-on-ios-device-in-microsoft-intune"></a>Utilizar dispositivos iOS com o início de sessão único no Microsoft Intune

A maioria das aplicações de Linha de Negócio (LOB) exige algum nível de autenticação do utilizador para suportar a segurança. Na maioria dos casos, esta autenticação exige que o utilizador introduza as mesmas credenciais múltiplas vezes, o que é frustrante. Para melhorar a experiência do utilizador, os programadores podem criar aplicações com o início de sessão único (SSO) e, assim, reduzir o número de vezes que um utilizador tem de introduzir credenciais.

Este artigo mostra-lhe como ativar o início de sessão único para dispositivos iOS com um perfil de configuração do dispositivo no Microsoft Intune.

## <a name="before-you-begin"></a>Antes de começar

Certifique-se de que tem uma aplicação codificada para procurar o arquivo de credenciais dos utilizadores no payload de início de sessão único no dispositivo iOS.

## <a name="create-the-sso-profile"></a>Criar o perfil SSO

1. No [portal do Azure](https://portal.azure.com), selecione **Todos os serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes definições:

    - **Nome**: introduza um nome para o perfil, como `ios sso profile`.
    - **Descrição**: introduza uma descrição com termos-chave para o ajudar a localizar o perfil na lista.
    - **Plataforma**: selecione **iOS**.
    - **Tipo de perfil**: selecione **Funcionalidades do dispositivo**.

4. Selecione **Início de Sessão Único**.

    ![Painel Início de Sessão Único](./media/sso-blade.png)

5. Introduza as seguintes definições: 

    - **Atributo de nome de utilizador do AAD**: o Intune procura este atributo para cada utilizador no Azure AD. Em seguida, o Intune preenche o campo respetivo (como o UPN) antes de gerar o payload XML que é instalado no dispositivo. As opções são:
    
        - **Nome Principal de Utilizador**: o UPN é analisado da seguinte forma:

            ![Atributo de nome de utilizador](media/User-name-attribute.png)

            Também pode substituir o âmbito pelo texto que introduzir na caixa de texto **Âmbito**.

            Por exemplo, a Contoso poderá ter várias subregiões, como a Europa, Ásia e América do Norte. Poderá querer que os seus utilizadores na Ásia utilizem o payload de SSO, e a aplicação exige o UPN no formato `username@asia.contoso.com`. Neste caso, se selecionar **Nome Principal de Utilizador**, por predefinição, o âmbito de cada utilizador será obtido do Azure AD e poderá ser simplesmente *contoso.com*. Assim, especificamente para os utilizadores na Ásia, pode criar este payload e substituir o âmbito pelo valor *asia.contoso.com*. Agora, o UPN do utilizador final será username@asia.contoso.com em vez de username@contoso.com.

        - **ID de Dispositivo do Intune**: o Intune seleciona automaticamente o ID de Dispositivo do Intune. 

            Por predefinição, as aplicações só precisam de utilizar o ID do dispositivo. No entanto, se a sua aplicação utilizar o âmbito *e* o ID do dispositivo, pode escrever o âmbito na caixa de texto **Âmbito**.

            > [!NOTE]
            > Por predefinição, mantenha o âmbito em branco se utilizar o ID do dispositivo.

    - **Âmbito**: a parte do domínio do URL.
    
    - **Prefixos de URL que vão utilizar o Início de Sessão Único**: **adicione** todos os URLs na sua organização que exigem a autenticação de início de sessão único do utilizador. 

        Por exemplo, quando um utilizador se ligar a um destes sites, o dispositivo iOS utilizará as credenciais de início de sessão único. O utilizador não tem de introduzir credenciais adicionais. No entanto, se tiver a autenticação multifator ativada, os utilizadores terão de introduzir a segunda autenticação.

        > [!NOTE]
        > Estes URLs têm de ter um FQDN formatado adequadamente. A Apple exige que os URLs estejam no formato `http://<yourURL.domain>`.

        Os padrões de correspondências do URL têm de começar com `http://` ou `https://`. É feita uma correspondência de cadeia simples, para que o prefixo de URL `http://www.contoso.com/` não corresponda a `http://www.contoso.com:80/`. No entanto, com o iOS 10.0 ou posterior, pode ser utilizado um único caráter universal (\*) para introduzir todos os valores correspondentes. Por exemplo, `http://*.contoso.com/` corresponde a `http://store.contoso.com/` e a `http://www.contoso.com`.

        Os padrões `http://.com` e `https://.com` correspondem a todos os URLs HTTP e HTTPS, respetivamente.
    
    - **Aplicações que vão utilizar o Início de Sessão Único**: **adicione** aplicações a dispositivos dos utilizadores finais que podem utilizar o início de sessão único. 

        A matriz `AppIdentifierMatches` tem de conter cadeias que correspondam aos IDs da coleção de pacotes de aplicação. Estas cadeias poderão ser correspondências exatas (como `com.contoso.myapp`) ou introduzir uma correspondência de prefixo no ID da coleção de pacotes com o caráter universal \*. O caráter universal tem de aparecer após um caráter de ponto final (.) e só pode aparecer uma vez, no final da cadeia (por exemplo: `com.contoso.*`). Quando um caráter universal é incluído, todas as aplicações cujo ID da coleção de pacotes começa com o prefixo têm acesso à conta.

        Utilize o **Nome da Aplicação** para introduzir um nome simples, para o ajudar a identificar o ID do pacote.
    
    - **Certificado de renovação de credencial**: se utilizar certificados para a autenticação (sem palavras-passe), selecione o certificado SCEP ou PFX implementado para o utilizador como certificado de autenticação. Normalmente, este é o mesmo certificado que é implementado para o utilizador para outros perfis, como VPN, Wi-Fi ou e-mail.

6. Selecione **OK** > **OK** > **Criar** para guardar as alterações e criar o perfil. Depois de criado, o perfil é apresentado na lista **Configuração do dispositivo – Perfis**. 

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre a configuração de funcionalidades dos dispositivos, veja [Como configurar as definições das funcionalidades dos dispositivos no Microsoft Intune](device-features-configure.md).

[Atribuir este perfil](device-profile-assign.md) aos seus dispositivos iOS.
