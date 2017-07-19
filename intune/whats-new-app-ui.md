---
title: "Atualização da IU para aplicações de utilizadores finais do Intune"
description: "Saiba o que foi alterado na IU das aplicações que funcionam com o Intune nos dispositivos de utilizadores finais."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b782e382-8deb-48a7-a437-d7c5a17163f1
ms.reviewer: priyar
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 1e2e1eb6da9114c689aae5eb06f7d7c780f35817
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="ui-updates-for-intune-end-user-apps"></a>Atualização da IU para aplicações de utilizadores finais do Intune
Saiba que atualizações efetuámos à IU das aplicações que os seus utilizadores finais irão ver com esta versão do Microsoft Intune. Isto pode ajudá-lo com as comunicações aos utilizadores e na atualização da documentação que tenha criado para dar suporte à sua implementação. Também pode ajudá-lo a compreender melhor como resolver os problemas que os seus utilizadores estão a experienciar se ligarem para o suporte técnico para obterem suporte sobre como utilizar o Portal da Empresa.

## <a name="week-of-june-12-2017"></a>Semana de 12 de junho de 2017

### <a name="company-portal-app-for-android-now-has-a-new-end-user-experience-for-app-protection-policies---1305217--"></a>A aplicação Portal da Empresa para Android tem agora uma nova experiência de utilizador final para Políticas de Proteção de Aplicações <!--1305217-->
Com base no feedback dos clientes, modificámos a aplicação Portal da Empresa para Android para apresentar o botão **Aceder a Conteúdos da Empresa**. O objetivo é evitar que os utilizadores finais passem desnecessariamente pelo processo de inscrição quando apenas precisarem de acesso a aplicações que suportem Políticas de Proteção de Aplicações, uma funcionalidade da gestão de aplicações móveis do Intune.

O utilizador irá tocar no botão **Aceder a Conteúdos da Empresa** em vez de a começar a inscrever o dispositivo.

![Uma imagem da aplicação Portal da Empresa para Android, que mostra o texto "Aceder a Conteúdos da Empresa" em tamanho grande, ao meio, em vez de apresentar de imediato as opções de inscrição, como acontece normalmente](./media/and_access_company_content_after_1706.png)

O utilizador é direcionado para o site do Portal da Empresa para autorizar a aplicação para utilização no respetivo dispositivo, onde o site do Portal da Empresa verifica as credenciais.

![Uma imagem do site do Portal da Empresa, a confirmar o início de sessão.](./media/and_iwp_sign_in_auth_page_after_1706.png)

Pode sempre inscrever o dispositivo para gestão completa ao tocar no menu **ação**.

![Uma imagem da aplicação Portal da Empresa para Android, a mostrar o menu no canto superior direito do ecrã com uma opção para inscrever o dispositivo.](./media/and_sign_in_menu_after_app_protection_policy_enrolled_after_1706.png)

### <a name="improvements-to-app-syncing-with-windows-10-creators-update---676505--"></a>Melhorias na sincronização da aplicação com a Atualização para Criativos do Windows 10 <!--676505-->

A aplicação Portal da Empresa para Windows 10 iniciará agora automaticamente uma sincronização para pedidos de instalação de aplicações para dispositivos com a Atualização para Criativos do Windows 10 (versão 1703). Tal reduzirá o problema da interrupção da instalação de aplicações durante o estado “Sincronização Pendente”. Além disso, os utilizadores poderão iniciar manualmente uma sincronização a partir da própria aplicação.

![Uma imagem da aplicação Portal da Empresa no Windows 10, onde a transferência do Microsoft Word está em estado pendente na loja de aplicações do Portal da Empresa.](./media/w10_download_pending_after_1706.png)

![Uma imagem da aplicação Portal da Empresa no Windows 10, com o novo estado de sincronização automática a apresentar uma mensagem de estado que indica que o dispositivo está a sincronizar e a tentar transferir a aplicação.](./media/w10_download_pending_syncing_after_1706.png)

### <a name="new-guided-experience-for-windows-10-company-portal----1058938---"></a>Nova experiência orientada para o Portal da Empresa do Windows 10 <!---1058938--->
A aplicação Portal da Empresa para Windows 10 vai incluir uma experiência de instruções orientada do Intune para dispositivos que não foram identificados ou inscritos. A nova experiência disponibiliza instruções passo a passo que orientam o utilizador no registo do Azure Active Directory (obrigatório para as funcionalidades de Acesso Condicional) e na inscrição MDM (obrigatória para as funcionalidades de gestão de dispositivos). A experiência guiada estará acessível na página inicial do Portal da Empresa. Os utilizadores podem continuar a utilizar a aplicação se não concluírem o registo e a inscrição, mas terão funcionalidades limitadas.

Esta atualização só é visível em dispositivos com a Atualização de Aniversário do Windows 10 (compilação 1607) ou superior.

![Uma imagem da página de destino da aplicação Portal da Empresa no Windows 10, com uma mensagem de estado no meio da lista "dispositivos" a informar o utilizador que o dispositivo que está a utilizar ainda não foi configurado para utilização empresarial e que o utilizador deve selecionar a mensagem para iniciar a configuração.](./media/win10_guided_enroll_select_setup_after_1706.png)

![Uma imagem da página de configuração da aplicação Portal da Empresa no Windows 10, que apresenta um aviso a indicar que o utilizador precisa de adicionar uma conta empresarial a este dispositivo para poder inscrevê-lo para gestão.](./media/win10_guided_enroll_we_help_setup_after_1706.png)

![Uma imagem da página "adicionar uma conta empresarial a este dispositivo" da aplicação Portal da Empresa no Windows 10 a informar o utilizador que terá de aceder à aplicação Definições e selecionar "Ligar" para concluir a inscrição. Depois disto, o ecrã indica que o utilizador tem de regressar à aplicação Portal da Empresa para concluir a inscrição.](./media/win10_guided_enroll_leaving_for_iwp_after_1706.png)

![Uma imagem do ecrã de inscrição para gestão da aplicação Portal da Empresa no Windows 10, a mostrar uma mensagem com o estado concluído, a indicar que o dispositivo do utilizador já está inscrito e que deve tocar no botão "seguinte" para continuar.](./media/win10_guided_enroll_youre_now_enrolled_after_1706.png)

![Uma imagem do ecrã de conclusão da aplicação Portal da Empresa no Windows 10 a informar o utilizador de que tudo está pronto e que o dispositivo está devidamente inscrito numa conta empresarial adicionada ao mesmo.](./media/win10_guided_enroll_youre_all_set_after_1706.png)

### <a name="new-menu-action-to-easily-remove-company-portal---1164569--"></a>Nova ação de menu para remover facilmente o Portal da Empresa <!--1164569-->
Com base nos comentários dos utilizadores, a aplicação Portal da Empresa para Android adicionou uma nova ação de menu para iniciar a remoção do Portal da Empresa do seu dispositivo. Esta ação remove o dispositivo da gestão do Intune para que a aplicação possa ser removida do dispositivo pelo utilizador.

![Uma imagem da aplicação Portal da Empresa para Android, com o menu de ação aberto no canto superior direito. A nova opção “Remover Portal da Empresa” está disponível como a terceira opção, abaixo de “O Meu Perfil” e “Definições” e acima de “Termos e Condições”, “Ajuda e Comentários” e “Acerca de”.](./media/android_remove_cp_menu_action_after_1705.png)

![Uma imagem da caixa de diálogo de confirmação, que está disponível depois de selecionar a nova opção “Remover Portal da Empresa” no menu de ação. A caixa de diálogo informa o utilizador de que “ao remover o portal da empresa, o dispositivo já não será gerido pelo administrador de TI e que poderá remover o acesso aos dados da empresa, às aplicações da empresa e ao e-mail da empresa”. Em seguida, pede ao utilizador para confirmar se quer remover a aplicação Portal da Empresa ao selecionar “Sim”.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="week-of-june-5-2017"></a>Semana de 5 de junho de 2017

### <a name="improvements-to-the-app-tiles-in-the-company-portal-app-for-ios"></a>Melhorias dos mosaicos de aplicação na aplicação Portal da Empresa para iOS
Atualizamos a estrutura dos mosaicos de aplicação na home page para refletir a cor corporativa que definiu para o Portal da Empresa.

**Antes**

![Uma imagem da aplicação Portal da Empresa para iOS anterior à atualização, que mostrava imagens de preenchimento predefinidas para “Todas as Aplicações”, “Aplicações em Destaque” e “Categorias”.](./media/cp_ios_homepage_before_1705.png)

**Depois**

![Uma imagem da aplicação Portal da Empresa para iOS após a atualização, que agora reflete a capacidade de selecionar quaisquer cores relevantes para a sua organização.](./media/cp_ios_homepage_after_1705.png)

### <a name="account-picker-now-available-for-the-company-portal-app-for-ios"></a>Seletor de conta agora disponível para a aplicação Portal da Empresa para iOS
Se os utilizadores tiverem usado a conta profissional ou escolar deles para iniciar sessão noutras aplicações da Microsoft no dispositivo iOS, poderão ver o nosso novo seletor de conta ao iniciar sessão no Portal da Empresa pela primeira vez.

![Uma imagem do seletor de conta, que mostra um utilizador de teste chamado “Alexandre Azevedo” a escolher um dos seus dois endereços de e-mail. Existe um botão sob os dois endereços que permite ao utilizador iniciar sessão com uma conta diferente.](./media/cp_ios_multi-account-selector-after-1705.png)

## <a name="april-2017"></a>Abril de 2017

### <a name="new-icons-for-the-managed-browser-and-the-company-portal---918433-918431--"></a>Novos ícones para o Managed Browser e o Portal da Empresa <!--918433, 918431-->

O Managed Browser receberá ícones atualizados nas versões para Android e iOS da aplicação. O novo ícone incluirá o emblema do Intune atualizado para o tornar mais consistente com as outras aplicações no Enterprise Mobility + Security (EM+S).

<html>
<body>
   <table id="wrapper">
      <tr>
         <td>
            <img src="/intune/media/cp_manbro_before_042017.png" alt="The previous version of the Managed Browser app icon." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_manbro_after_042017.png" alt="The updated version of the Managed Browser app icon." width=200 height=366 align=center>
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
            <img src="/intune/media/cp_android_connecting_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Connecting' underneath it." width=200 height=366 align=center>
          </td>
          <td>
             <img src="/intune/media/cp_android_signing_in_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Signing in' underneath it." width=200 height=366 align=center>
           </td>
           <td>
              <img src="/intune/media/cp_android_checking_security_reqs_042017.png" alt="The Company Portal app for Android sign in screen that shows a partially filled loading bar with the phrase 'Checking for security requirements' underneath it." width=200 height=366 align=center>
           </td>
      </tr>
   </table>
</body>
</html>

### <a name="improved-app-install-status-for-the-windows-10-company-portal-app---676495--"></a>Estado da instalação de aplicações melhorado para a aplicação Portal da Empresa do Windows 10 <!--676495-->
A aplicação do Portal da Empresa do Windows 10 apresenta agora uma barra de progresso da instalação na página de detalhes da aplicação. A barra de progresso está presente nas aplicações modernas em dispositivos com a Atualização de Aniversário do Windows 10 e versões superiores.

__Antes__ ![Uma imagem da versão anterior do ecrã de carregamento em que o estado mostrava simplesmente "a instalar".](./media/cp_win10_install_status_before_1704.png)

__Depois__ ![Uma imagem da versão atualizada do ecrã de carregamento que mostra agora uma barra de progresso da instalação.](./media/cp_win10_install_status_after_1704.png)

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
            <img src="/intune/media/cp_android_contactit_after.png" alt="The Company Portal app for Android displaying an updated version of the Contact IT tab. The tab shows available contact information for IT, including phone number, email address, IT website, and IT contact information." width=200 height=366 align=center>
          </td>
      </tr>
   </table>
</body>
</html>

## <a name="january-2017"></a>Janeiro de 2017

### <a name="modernizing-the-company-portal-website---753980-announced-1701--"></a>Modernizar o site do Portal da Empresa <!--753980, announced 1701-->
A partir de fevereiro, o site do Portal da Empresa irá suportar aplicações visadas para utilizadores que não têm dispositivos geridos. O site será alinhado com outros produtos e serviços Microsoft através de um novo esquema de cores contrastante, ilustrações dinâmicas e um menu de opções, ![Pequena imagem do menu de opções adicionado ao canto superior esquerdo do site do Portal da Empresa](./media/CP_hamburger_menu.png) que irá conter os detalhes e informações de contacto do suporte técnico nos dispositivos geridos existentes. A página de destino será reorganizada de forma a realçar as aplicações que estão disponíveis para os utilizadores, com carrosséis para aplicações Em Destaque e Recentemente Atualizadas.

![À esquerda, uma imagem da versão atual do site do Portal da Empresa com as versões anteriores de Aplicações, Os Meus Dispositivos e das vistas Em destaque e Categorias. À direita, uma imagem da versão atualizada do site do Portal da Empresa com um carrossel de aplicações atualizado, uma lista de aplicações Publicadas Recentemente e a vista Categorias atualizada.](./media/CP_Website_BeforeAfter_Feb2016.png)

## <a name="coming-soon-in-the-ui"></a>Brevemente na IU
Saiba como planeamos melhorar a experiência de utilizador através da atualização da nossa interface de utilizador.

> [!Note]
> Tenha em atenção que as imagens abaixo podem ser pré-visualizações e que o produto anunciado poderá ser diferente das versões apresentadas.

### <a name="improved-sign-in-experience-across-company-portal-apps-for-all-platforms---user-story-1132123--"></a>Experiência de início de sessão melhorada nas aplicações Portal da Empresa para todas as plataformas<!--User Story 1132123-->

Anunciamos uma alteração que ficará disponível nos próximos meses e irá melhorar a experiência de início de sessão nas aplicações do Portal da Empresa do Intune para Android, iOS e Windows. A nova experiência de utilizador será apresentada automaticamente em todas as plataformas da aplicação Portal da Empresa quando o Azure AD fizer esta alteração. Além disso, os utilizadores podem agora iniciar sessão no Portal da Empresa a partir de outro dispositivo com um código gerado, de utilização única. Tal é especialmente útil nos casos em que os utilizadores precisam de iniciar sessão sem credenciais.  

Abaixo, pode ver a experiência de início de sessão anterior, a nova experiência de início de sessão com credenciais e a nova experiência de início de sessão a partir de outro dispositivo.

__Experiência de início de sessão anterior__

![A página de início de sessão do Portal da Empresa, com o ícone de uma pessoa à frente de uma representação gráfica de um site. Abaixo, está o botão “Iniciar sessão”. Uma ligação na parte inferior direciona para as informações de Privacidade e Cookies da Microsoft.](./media/cp_ios_aad_signin_before_1704_001.png)

![Depois de tocar em Iniciar sessão, o utilizador deverá introduzir as credenciais nesta página, que pede o e-mail e a palavra-passe do utilizador e proporciona formas de resolver falhas de palavras-passe.](./media/cp_ios_aad_signin_before_1704_002.png)

![Depois de indicar a palavra-passe, a aplicação Portal da Empresa inicia sessão, apresentando uma barra de carregamento.](./media/cp_ios_aad_signin_before_1704_003.png)

__Nova experiência de início de sessão__

![A página de início de sessão do Portal da Empresa, com o ícone de uma pessoa à frente de uma representação gráfica de um site. Abaixo, está o botão “Iniciar sessão”. Uma ligação na parte inferior direciona para as informações de Privacidade e Cookies da Microsoft.](./media/cp_ios_aad_signin_after_1704_001.png)

![É pedido ao utilizador que indique apenas o endereço de e-mail, em vez do e-mail e palavra-passe no mesmo ecrã.](./media/cp_ios_aad_signin_after_1704_002.png)

![É pedido ao utilizador que indique a palavra-passe depois de ter sido aceite o endereço de e-mail.](./media/cp_ios_aad_signin_after_1704_003.png)

![Depois do processo de autenticação, a aplicação Portal da Empresa inicia sessão, apresentando uma barra de carregamento.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)

__Nova experiência de início de sessão quando iniciar sessão a partir de outro dispositivo__

![A página de início de sessão do Portal da Empresa, com o ícone de uma pessoa à frente de uma representação gráfica de um site. Abaixo, está o botão “Iniciar sessão”. Uma ligação na parte inferior direciona para as informações de Privacidade e Cookies da Microsoft.](./media/cp_ios_aad_signin_from_another_device_after_1704_001.png)

Toque na ligação __Iniciar sessão a partir de outro dispositivo__.

![As instruções indicam para ir para a página aka.ms/devicelogin com um código de acesso exclusivo a partir do computador de trabalho e, em seguida, para utilizar o código para iniciar sessão.](./media/cp_ios_aad_signin_from_another_device_after_1704_003.png)

Inicie um browser e aceda a [https://aka.ms/devicelogin](https://aka.ms/devicelogin).

![Uma imagem do browser do utilizador no computador de trabalho em vez da aplicação Portal da Empresa. A página “Início de sessão do dispositivo” apresentada solicita ao utilizador o código que recebeu na aplicação Portal da Empresa.](./media/cp_ios_aad_signin_from_another_device_after_1704_004.png)

Introduza o código que viu na aplicação Portal da Empresa. Ao selecionar __Continuar__, poderá autenticar através de qualquer método suportado pela sua empresa, tal como um smartcard.

![O utilizador introduziu o seu código exclusivo no campo e o site “Início de sessão do dispositivo” pediu a confirmação de que o Portal da Empresa do Intune foi a aplicação correta para receber a autorização para iniciar sessão.](./media/cp_ios_aad_signin_from_another_device_after_1704_005.png)

![Uma página de confirmação que indica que o utilizador tem agora sessão iniciada na aplicação Portal da Empresa no seu dispositivo e que esta página pode ser fechada.](./media/cp_ios_aad_signin_from_another_device_after_1704_006.png)

A aplicação Portal da Empresa começará a iniciar sessão.

![Depois do processo de autenticação, a aplicação Portal da Empresa inicia sessão, apresentando uma barra de carregamento.](./media/cp_ios_aad_signin_from_another_device_after_1704_007.png)
### <a name="see-also"></a>Consulte também
* [Blogue do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=273882)
* [Roteiro da Cloud Platform](https://www.microsoft.com/server-cloud/roadmap/Indevelopment.aspx?TabIndex=0&dropValue=Intune)
* [Novidades do Intune](https://docs.microsoft.com/intune/whats-new)
