---
title: Configurar o Microsoft Intune para início de sessão único num dispositivo iOS
titlesuffix: ''
description: Saiba como configurar o Microsoft Intune para início de sessão único num dispositivo iOS.
keywords: ''
author: vhorne
ms.author: victorh
manager: dougeby
ms.date: 3/2/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b9afd14fd3ba4e464f0bf09c228290ef2f19eac3
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/16/2018
---
# <a name="configure-microsoft-intune-for-ios-device-single-sign-on"></a>Configurar o Microsoft Intune para início de sessão único num dispositivo iOS

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

A maioria das aplicações de Linha de Negócio (LOB) exige algum nível de autenticação do utilizador para suportar a segurança. Na maioria dos casos, isto exige que o utilizador escreva as mesmas credenciais múltiplas vezes, o que pode ser frustrante para os utilizadores. Para melhorar a experiência do utilizador, os programadores podem criar aplicações com o início de sessão único e, assim, reduzir o número de vezes que um utilizador tem de fornecer credenciais.

Para tirar partido do Início de Sessão Único em dispositivos iOS, precisa de ter o seguinte:

- Uma aplicação codificada para procurar o arquivo de credenciais dos utilizadores no payload de início de sessão único no dispositivo iOS.
- O Intune configurado para o início de sessão único em dispositivos iOS.

## <a name="to-configure-intune-for-ios-device-single-sign-on"></a>Para configurar o Intune para o início de sessão único em dispositivos iOS


1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Configuração do dispositivo**.
4. No painel **Configuração do dispositivo**, na secção **Gerir**, selecione **Perfis**.
5. No painel de perfis, selecione **Criar perfil**.
6. Forneça um nome e descrição e configure as seguintes definições:
   - **Plataforma**: selecione **iOS**.
   - **Tipo de perfil**: selecione **Funcionalidades do dispositivo**.
7. No painel **Funcionalidades de dispositivos**, selecione **Início de Sessão Único**.

   ![Painel Início de Sessão Único](./media/sso-blade.png)

8. Utilize a seguinte tabela de resumo para obter ajuda no preenchimento dos campos no painel **Início de Sessão Único**. Para obter detalhes, veja as secções a seguir à tabela.

   |Campo  |Notas|
   |---------|---------|
   |**Atributo de nome de utilizador do AAD**|O atributo que o Intune procura para cada utilizador no AAD e cujo campo (como o UPN) povoa antes de gerar o payload XML que é instalado no dispositivo.|
   |**Realm**|A parte do domínio do URL.|
   |**Prefixos de URL que utilizarão o Início de Sessão Único**|Todos os URLs na sua organização que exigem uma autenticação de utilizador de início de sessão única.|
   |**Aplicações que utilizarão o Início de Sessão Único**|Aplicações no dispositivo do utilizador final que utilizam o payload de início de sessão único.|
   |**Certificado de renovação de credenciais**|Se utilizar certificados para a autenticação, selecione o certificado SCEP ou PFX implementado para o utilizador como certificado de autenticação.|

As seguintes secções fornecem mais detalhes sobre cada um dos campos do início de sessão único.

### <a name="username-attribute-from-aad-and-realm"></a>Atributo de nome de utilizador do AAD e Realm

- Se o **Nome Principal de Utilizador** estiver selecionado para este campo, será analisado da seguinte forma:

   ![Atributo de nome de utilizador](media/User-name-attribute.png)

   Também pode substituir o realm pelo texto que escrever na caixa de texto **Realm**.

   Por exemplo, a Contoso poderá ter várias subregiões, como a Europa, Ásia e América do Norte. Poderão querer que os seus utilizadores na Ásia utilizem o payload de SSO e a aplicação exige o UPN na forma *username@asia.contoso.com*. Neste caso, se selecionar o **Nome Principal de Utilizador**, o realm para cada utilizador é retirado do AAD por predefinição e poderá ser apenas *contoso.com*. Assim, especificamente para os utilizadores na Ásia, pode criar este payload e substituir o realm pelo valor *asia.contoso.com*. Agora, o UPN do utilizador final será *username@asia.contoso.com* e não *username@contoso.com*.

- Se selecionar **ID do Dispositivo**, o Intune selecionará automaticamente o ID de Dispositivo do Intune.

   Por predefinição, as aplicações só precisam de utilizar o ID do dispositivo. No entanto, se a sua aplicação utilizar o realm juntamente com o ID do dispositivo, pode escrever o realm na caixa de texto **Realm**.

   > [!NOTE]
   > Por predefinição, mantenha o realm em branco se utilizar o ID do dispositivo.

### <a name="url-prefixes-that-will-use-single-sign-on"></a>Prefixos de URL que utilizarão o Início de Sessão Único

Escreva aqui todos os URLs que existam na sua organização e exijam a autenticação do utilizador.

Por exemplo, quando um utilizador se ligar a um destes sites, o dispositivo iOS utilizará as credenciais de início de sessão único e o utilizador não precisará de introduzir credenciais adicionais. No entanto, se tiver a autenticação multifator ativada, os utilizadores terão de introduzir a segunda autenticação.

> [!NOTE]
> Estes URLs têm de ter um FQDN formatado adequadamente. A Apple exige que estes estejam no formato `http://<yourURL.domain>`

Os padrões de correspondências do URL têm de começar com `http://` ou `https://`. É feita uma correspondência de cadeia simples, para que o prefixo de URL `http://www.contoso.com/` não corresponda a `http://www.contoso.com:80/`. No entanto, com o iOS 9.0 ou posterior, pode ser utilizado um único caráter universal \* para especificar todos os valores correspondentes. Por exemplo, `http://*.contoso.com/` corresponde a `http://store.contoso.com/` e a `http://www.contoso.com`.
Os padrões `http://.com` e `https://.com` correspondem a todos os URLs HTTP e HTTPS, respetivamente.

### <a name="apps-that-will-use-single-sign-on"></a>Aplicações que utilizarão o Início de Sessão Único

Indique que aplicações num dispositivo de utilizador final podem utilizar o payload de Início de Sessão Única.

A matriz `AppIdentifierMatches` tem de conter cadeias que correspondam aos IDs da coleção de pacotes de aplicação. Estas cadeias devem ser correspondências exatas (por exemplo: `com.contoso.myapp`) ou especificar uma correspondência de prefixo no ID da coleção de pacotes com o caráter universal \*. O caráter universal tem de aparecer após um caráter de ponto final (.) e só pode aparecer uma vez, no final da cadeia (por exemplo: `com.contoso.*`). Quando um caráter universal é incluído, todas as aplicações cujo ID da coleção de pacotes começa com o prefixo têm acesso à conta.

O campo **Nome da Aplicação** é utilizado para adicionar um nome simples para o ajudar a identificar o ID da coleção de pacotes.

### <a name="credential-renewal-certificate"></a>Certificado de renovação de credenciais

Se autenticar os seus utilizadores finais com certificados (não palavras-passe), utilize este campo para selecionar o certificado SCEP ou PFX implementado para o utilizador como certificado de autenticação. Normalmente, este é o mesmo certificado que é implementado para o utilizador para outros perfis, como VPN, Wi-Fi ou e-mail.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre a configuração de funcionalidades dos dispositivos, veja [Como configurar as definições das funcionalidades dos dispositivos no Microsoft Intune](device-features-configure.md).
