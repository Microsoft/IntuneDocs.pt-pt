---
title: Como iniciar sessão na aplicação Portal da Empresa | Documentos da Microsoft
description: Saiba como iniciar sessão na aplicação Portal da Empresa em várias plataformas.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/02/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: cfd214bc-f072-4808-af2e-a3cbf7af9bca
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 370d6372cf3df2ff807069fe8d54f30da23e7ba2
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842614"
---
# <a name="how-do-i-sign-in-to-the-company-portal-app---user-story-1132123--"></a>Como posso iniciar sessão na aplicação Portal da Empresa? <!--User Story 1132123-->

Pode utilizar a aplicação Portal da Empresa para aceder aos recursos da sua empresa, como o e-mail e as aplicações empresariais. Existem duas formas principais de iniciar sessão no Portal da Empresa:

* Através do seu endereço de e-mail de trabalho e respetiva palavra-passe
* Iniciar sessão a partir de outro dispositivo

Apesar de as seguintes imagens serem referentes ao iOS, o processo é praticamente idêntico para os seus dispositivos Android e Windows.

## <a name="signing-in-with-your-email-address-and-password"></a>Iniciar sessão com o seu endereço de e-mail e palavra-passe

1. Abra a aplicação Portal da Empresa no seu dispositivo e toque em **Iniciar Sessão**.

   ![A página de início de sessão do Portal da Empresa, com o ícone de uma pessoa à frente de uma representação gráfica de um site. Abaixo, está o texto "Obter acesso a recursos da empresa e mantê-los seguros" e o botão "Iniciar sessão". Uma ligação na parte inferior direciona para as informações de Privacidade e Cookies da Microsoft.](/intune-user-help/media/cp_ios_aad_signin_after_1804_001.png)

   Não tem a aplicação Portal da Empresa? Saiba como instalar e transferir a aplicação para [iOS](install-and-sign-in-to-the-intune-company-portal-app-ios.md) ou [Android](install-the-company-portal-app-android.md).

2. Introduza a sua **Conta escolar ou profissional** e toque em **Seguinte**.

   ![É pedido ao utilizador que indique apenas o endereço de e-mail, em vez do e-mail e palavra-passe no mesmo ecrã.](/intune-user-help/media/cp_ios_aad_signin_after_1804_002.png)

3. Introduza a sua palavra-passe e toque em **Iniciar Sessão**.

   ![É pedido ao utilizador que indique a palavra-passe depois de ter sido aceite o endereço de e-mail.](/intune-user-help/media/cp_ios_aad_signin_after_1804_003.png)

4. Assim que o Portal da Empresa aceitar as suas credenciais, a sua sessão será iniciada e poderá começar a aceder aos recursos da empresa.   

   ![Depois do processo de autenticação, a aplicação Portal da Empresa inicia sessão, apresentando uma barra de carregamento.](/intune-user-help/media/cp_ios_aad_signin_after_1804_004.png)

## <a name="signing-in-with-certificate-based-authentication"></a>Iniciar sessão com a autenticação baseada em certificados

1.  Abra a aplicação Portal da Empresa no dispositivo.

2.  Introduza a sua **Conta escolar ou profissional**.

3.  Toque na ligação **Iniciar sessão com um certificado**.

4.  Toque em **Continuar** para utilizar o certificado.

## <a name="signing-in-from-another-device"></a>Iniciar sessão a partir de outro dispositivo

Se não utiliza uma palavra-passe para iniciar sessão nos recursos da sua empresa, pode utilizar outro dispositivo para confirmar que é a pessoa certa com os níveis de acesso certos. Se a sua empresa utiliza smart cards para aceder aos seus computadores, é provável que tenha de iniciar sessão com outro dispositivo.

1. Em vez de introduzir o seu endereço de e-mail, selecione a ligação **Iniciar sessão a partir de outro dispositivo** por baixo da caixa de texto do e-mail.

   ![A página de início de sessão do Portal da Empresa pede ao utilizador um endereço de e-mail.  Abaixo, está o botão "Seguinte" e uma ligação para "Iniciar sessão a partir de outro dispositivo". Além disso, inclui uma ligação para "Não consegue aceder à conta?" Uma ligação na parte inferior direciona para as informações de Privacidade e Cookies da Microsoft.](/intune-user-help/media/cp_ios_aad_signin_after_1804_005.png)

2. Receberá um código único e exclusivo para iniciar sessão no Portal da Empresa.

   ![As instruções indicam para ir para a página https://microsoft.com/devicelogin com um código de acesso exclusivo a partir do computador de trabalho e, em seguida, para utilizar o código para iniciar sessão.](/intune-user-help/media/cp_ios_aad_signin_after_1804_006.png)

3. No outro dispositivo, abra o browser e aceda a [https://microsoft.com/devicelogin](https://microsoft.com/devicelogin) para introduzir o código.

   ![Uma imagem do browser do utilizador no computador de trabalho em vez da aplicação Portal da Empresa. A página “Início de sessão do dispositivo” apresentada solicita ao utilizador o código que recebeu na aplicação Portal da Empresa.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

4. Assim que a página **Início de Sessão do Dispositivo** verificar o código, selecione __Continuar__ para permitir que o Portal da Empresa inicie sessão no seu outro dispositivo.

   ![O utilizador introduziu o seu código exclusivo no campo e o site “Início de sessão do dispositivo” pediu a confirmação de que o Portal da Empresa do Intune foi a aplicação correta para receber a autorização para iniciar sessão.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

5. Assim que o código for verificado, pode fechar a janela.

   ![Uma página de confirmação que indica que o utilizador tem agora sessão iniciada na aplicação Portal da Empresa no seu dispositivo e que esta página pode ser fechada.](/intune/media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

6. No seu dispositivo original, a aplicação Portal da Empresa começa a iniciar sessão.

   ![Depois do processo de autenticação, a aplicação Portal da Empresa inicia sessão, apresentando o respetivo processo com uma barra de carregamento.](/intune-user-help/media/cp_ios_aad_signin_after_1804_007.png)

Ainda precisa de ajuda? Contacte o suporte da empresa. Para encontrar as informações de contacto dele, verifique o [site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).
