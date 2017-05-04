---
title: "Atualização da IU para aplicações de utilizadores finais do Intune | Documentos da Microsoft"
description: "Saiba o que foi alterado na IU das aplicações que funcionam com o Intune nos dispositivos de utilizadores finais."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 04/20/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: 62dcb40ad5a7921c514a9d41da14b991e39f3bcd
ms.openlocfilehash: f4a48b889702147abe20fd513fdb0f774020a54a
ms.lasthandoff: 04/20/2017


---
# <a name="ui-updates-for-intune-end-user-apps"></a>Atualização da IU para aplicações de utilizadores finais do Intune
Saiba que atualizações efetuámos à IU das aplicações que os seus utilizadores finais irão ver com esta versão do Microsoft Intune. Isto pode ajudá-lo com as comunicações aos utilizadores e na atualização da documentação que tenha criado para dar suporte à sua implementação. Também pode ajudá-lo a compreender melhor como resolver os problemas que os seus utilizadores estão a experienciar se ligarem para o suporte técnico para obterem suporte sobre como utilizar o Portal da Empresa.

> [!Note]
> Tenha em atenção que as imagens abaixo são pré-visualizações e que o produto anunciado poderá ser diferente das versões apresentadas.

## <a name="april-2017"></a>Abril de 2017

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Experiência de início de sessão melhorada nas aplicações Portal da Empresa para todas as plataformas<!--User Story 1132123-->

Estamos a melhorar a experiência de início de sessão para as aplicações Portal da Empresa do Intune para Android, iOS e Windows.  A nova experiência de utilizador será apresentada automaticamente em todas as plataformas da aplicação Portal da Empresa quando o Azure AD fizer esta alteração. Além disso, os utilizadores podem agora iniciar sessão no Portal da Empresa a partir de outro dispositivo com um código gerado, de utilização única. Tal é especialmente útil nos casos em que os utilizadores precisam de iniciar sessão sem credenciais.  

Abaixo, pode ver a experiência de início de sessão anterior, a nova experiência de início de sessão com credenciais e a nova experiência de início de sessão a partir de outro dispositivo.

__Experiência de início de sessão anterior__

![A página de início de sessão do Portal da Empresa, com o ícone de uma pessoa à frente de uma representação gráfica de um site. Abaixo, está o botão “Iniciar sessão”. Uma ligação na parte inferior direciona para as informações de Privacidade e Cookies da Microsoft.](./media/cp_ios_aad_signin_before_1704_001.png)

![Depois de tocar em Iniciar sessão, o utilizador deverá introduzir as credenciais nesta página, que pede o e-mail e a palavra-passe do utilizador e proporciona formas de resolver falhas de palavras-passe.](./media/cp_ios_aad_signin_before_1704_002.png)

![Depois de indicar a palavra-passe, a aplicação Portal da Empresa inicia sessão, apresentando uma barra de carregamento.](./media/cp_ios_aad_signin_before_1704_003.png)

__Nova experiência de início de sessão__

![A página de início de sessão do Portal da Empresa, com o ícone de uma pessoa à frente de uma representação gráfica de um site. Abaixo, está o botão “Iniciar sessão”. Uma ligação na parte inferior direciona para as informações de Privacidade e Cookies da Microsoft.](./media/cp_ios_aad_signin_after_1704_001.png)

![É pedido ao utilizador que indique apenas o endereço de e-mail, em vez do e-mail e palavra-passe no mesmo ecrã.](./media/cp_ios_aad_signin_after_1704_002.png)

![É pedido ao utilizador que indique a palavra-passe depois de ter sido aceite o endereço de e-mail.](./media/cp_ios_aad_signin_after_1704_003.png)

__Nova experiência de início de sessão quando iniciar sessão a partir de outro dispositivo__

![A página de início de sessão do Portal da Empresa, com o ícone de uma pessoa à frente de uma representação gráfica de um site. Abaixo, está o botão “Iniciar sessão”. Uma ligação na parte inferior direciona para as informações de Privacidade e Cookies da Microsoft.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Toque na ligação __Iniciar sessão a partir de outro dispositivo__.

![É pedido ao utilizador que indique apenas o endereço de e-mail, em vez do e-mail e palavra-passe no mesmo ecrã. A ligação abaixo do campo de e-mail diz “Iniciar sessão a partir de outro dispositivo”.](./media/cp_ios_aad_signin_from_another_device_after_1704_002.png)

![As instruções indicam para ir para a página aka.ms/devicelogin com um código de acesso exclusivo a partir do computador de trabalho e, em seguida, para utilizar o código para iniciar sessão.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Inicie um browser e aceda a [http://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Uma imagem do browser do utilizador no computador de trabalho em vez da aplicação Portal da Empresa. A página “Início de sessão do dispositivo” apresentada solicita ao utilizador o código que recebeu na aplicação Portal da Empresa.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Introduza o código que viu na aplicação Portal da Empresa. Ao selecionar __Continuar__, poderá autenticar através de qualquer método suportado pela sua empresa, tal como um smartcard.

![O utilizador introduziu o seu código exclusivo no campo e o site “Início de sessão do dispositivo” pediu a confirmação de que o Portal da Empresa do Intune foi a aplicação correta para receber a autorização para iniciar sessão.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Uma página de confirmação que indica que o utilizador tem agora sessão iniciada na aplicação Portal da Empresa no seu dispositivo e que esta página pode ser fechada.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

A aplicação Portal da Empresa começará a iniciar sessão.

![Depois do processo de autenticação, a aplicação Portal da Empresa inicia sessão, apresentando uma barra de carregamento.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Novos ícones para o Managed Browser e o Portal da Empresa <!--918433, 918431-->

O Managed Browser receberá ícones atualizados nas versões para Android e iOS da aplicação. O novo ícone incluirá o emblema do Intune atualizado para o tornar mais consistente com as outras aplicações no Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

O Portal da Empresa também receberá ícones atualizados para as versões para Android, iOS e Windows da aplicação para melhorar a consistência com as outras aplicações no EM+S. Estes ícones serão lançados gradualmente nas plataformas a partir de abril até finais de maio.

### <a name="sign-in-progress-indicator-in-android-company-portal---953374--"></a>Indicador de progresso de início de sessão no Portal da Empresa para Android <!--953374-->

Uma atualização à aplicação Portal da Empresa para Android mostra um indicador de progresso de início de sessão quando o utilizador inicia ou retoma a aplicação. O indicador mostra novos estados de progresso, a começar com “A ligar...”, “A iniciar sessão...” e “A verificar os requisitos de segurança...” antes de o utilizador poder aceder à aplicação.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

## <a name="february-2017"></a>Fevereiro de 2017

### <a name="new-user-experience-for-the-company-portal-app-for-android---621622-announced-1702--"></a>Nova experiência de utilizador da aplicação Portal da Empresa para Android<!--621622, announced 1702-->
A partir de março, a aplicação Portal da Empresa para Android seguirá as [diretrizes de conceção do material](https://material.io/guidelines/material-design/introduction.html) para criar um aspeto e funcionalidade mais modernos. Esta experiência de utilizador melhorada inclui:

* __Cores__: os cabeçalhos dos separadores podem ser coloridos de acordo com a sua paleta de cores personalizada.

![À esquerda, uma imagem da aplicação Portal da Empresa para Android antes da atualização. À direita, uma imagem da aplicação Portal da Empresa para Android depois da atualização. Ambas as imagens mostram o separador Dispositivos como o separador selecionado dos três separadores disponíveis (Aplicações, Dispositivos e Contactar TI).](./media/CP_Android_DevicesTab_BeforeAfter.png)

* __Interface__: os botões __Aplicações em Destaque__ e __Todas as Aplicações__ foram atualizados no separador __Aplicações__. O botão __Procurar__ é agora um botão de ação flutuante.

![À esquerda, uma imagem da aplicação Portal da Empresa para Android antes da atualização. À direita, uma imagem da aplicação Portal da Empresa para Android depois da atualização. Ambas as imagens mostram o separador Aplicações como o separador selecionado dos três separadores disponíveis (Aplicações, Dispositivos e Contactar TI).](./media/CP_Android_AppsTab_BeforeAfter.png)

* __Navegação__: a secção Todas as Aplicações mostra uma vista com os separadores __Em destaque__, __Todas__ e __Categorias__ para uma navegação mais fácil. O separador __Contactar TI__ foi simplificado para facilitar a leitura.

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="https://docs.microsoft.com/InTune/whats-new/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Janeiro de 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Modernizar o site do Portal da Empresa <!--753980, announced 1701-->
A partir de fevereiro, o site do Portal da Empresa irá suportar aplicações visadas para utilizadores que não têm dispositivos geridos. O site será alinhado com outros produtos e serviços Microsoft através de um novo esquema de cores contrastante, ilustrações dinâmicas e um menu de opções, ![Pequena imagem do menu de opções adicionado ao canto superior esquerdo do site do Portal da Empresa](./media/CP_hamburger_menu.png) que irá conter os detalhes e informações de contacto do suporte técnico nos dispositivos geridos existentes. A página de destino será reorganizada de forma a realçar as aplicações que estão disponíveis para os utilizadores, com carrosséis para aplicações Em Destaque e Recentemente Atualizadas.

![À esquerda, uma imagem da versão atual do site do Portal da Empresa com as versões anteriores de Aplicações, Os Meus Dispositivos e das vistas Em destaque e Categorias. À direita, uma imagem da versão atualizada do site do Portal da Empresa com um carrossel de aplicações atualizado, uma lista de aplicações Publicadas Recentemente e a vista Categorias atualizada.](./media/CP_Website_BeforeAfter_Feb2016.png)


### <a name="see-also"></a>Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades na pré-visualização do Azure](https://docs.microsoft.com/intune-azure/introduction/whats-new)
* [Novidades – Arquivo](whats-new-archive.md)

