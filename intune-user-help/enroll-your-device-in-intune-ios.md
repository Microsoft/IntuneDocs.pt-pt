---
title: Configurar o acesso do dispositivo iOS aos recursos da empresa | Microsoft Docs
description: Descreve como fazer com que o dispositivo iOS seja gerido pelo Intune
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 12/18/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.subservice: end-user
ms.technology: ''
ms.assetid: 6eeec7aa-1b07-4ce3-894c-13e09b89bdd4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: tisilv
ms.suite: ems
ms.custom: intune-enduser
ms.collection: ''
ms.openlocfilehash: 92d1ca850d8bb542f0b7fe027ab7af8c12089ef8
ms.sourcegitcommit: 9ee2401a2f01373a962749b0728c22385dbcba6d
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/29/2020
ms.locfileid: "78181760"
---
# <a name="set-up-ios-device-access-to-your-company-resources"></a>Configurar o acesso do dispositivo iOS aos recursos da empresa  

Inscreva o seu dispositivo iOS na aplicação Portal da Empresa do Intune para obter acesso seguro ao e-mail, ficheiros e aplicações da sua organização.

Depois de o seu dispositivo estar matriculado, torna-se *gerido*. A sua organização pode atribuir políticas e aplicações ao dispositivo através de um fornecedor de gestão de dispositivos móveis (MDM), como o Intune.  

> [!NOTE]
> Não vendemos quaisquer dados recolhidos pelo nosso serviço a terceiros por qualquer motivo.  

Para manter o acesso a informações laborais ou escolares a partir do seu dispositivo, terá de configurar o seu dispositivo de acordo com as definições preferidas da sua organização. Este artigo descreve como usar o Portal da Empresa para o inscrever e manter os requisitos de definição da sua organização.  
</br>
> [!VIDEO https://www.youtube.com/embed/mJyv6YcHi7c?rel=0]

> [!NOTE]
> Se tentou aceder ao e-mail da empresa na aplicação Mail e recebeu uma mensagem para ter o dispositivo gerido, está no sítio certo. Siga as instruções abaixo para obter acesso ao seu e-mail e a outros recursos empresariais no seu dispositivo iOS.  


## <a name="what-to-expect-from-the-company-portal-app"></a>O que esperar da aplicação Portal da Empresa  

### <a name="security"></a>Segurança  
Durante a configuração inicial, a aplicação requer que se autentique na sua organização. Em seguida, informa-o de quaisquer definições do dispositivo que tenha de atualizar. Muitas vezes, por exemplo, as organizações definem requisitos de palavra-passe com limites de carateres mínimos e máximos que terá de cumprir.

### <a name="protection"></a>Protection  
Após a inscrição do seu dispositivo, a aplicação Portal da Empresa irá continuar a garantir que o mesmo se encontra protegido. Se, por exemplo, instalar uma aplicação de uma origem não fidedigna, a aplicação Portal da Empresa irá alertá-lo e, por vezes, revogar o acesso aos dados da empresa. Este tipo de política é comum nas organizações, e muitas vezes requer que você desinstale a app não confiável antes de poder recuperar o acesso.  

### <a name="setting-notifications"></a>Definir as notificações  
Se, após a inscrição, a sua organização aplicar um novo requisito de segurança, como a autenticação multifator, a aplicação Portal da Empresa irá notificá-lo. Terá a oportunidade de ajustar as suas definições para que possa continuar a trabalhar a partir do seu dispositivo.  

Para obter mais informações sobre a inscrição, veja [O que acontece quando instalo a aplicação Portal da Empresa e inscrevo o meu dispositivo?](https://docs.microsoft.com//intune-user-help/what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-ios)  

## <a name="enroll-your-ios-device"></a>Inscreva o seu dispositivo iOS  

Vá à loja de aplicações para descarregar e instalar a [aplicação Intune Company Portal](install-and-sign-in-to-the-intune-company-portal-app-ios.md) no seu dispositivo. Você também precisa manter uma conexão Wi-Fi e ter acesso ao Safari durante a inscrição. 

Fazer uma pausa durante mais de alguns minutos durante a inscrição pode fazer com que a aplicação feche ou termine a configuração. Se isso acontecer, abra a aplicação Portal da Empresa e tente novamente.  

1. Abra o Portal da Empresa e inscreva-se com o seu trabalho ou conta escolar.  

2. Quando solicitado a receber notificações do Portal da Empresa, toque **em Permitir.** O Portal da Empresa utiliza notificações para o alertar se, por exemplo, as definições do seu dispositivo precisarem de ser atualizadas.  

3. No ecrã de **acesso configurar, selecione** **Iniciar.**   

    ![Exemplo de screenshot do Portal da Empresa, ecrã "Configurar o acesso".](./media/ios-enrollment-checklist-1909.PNG)  

4. O dispositivo Select e o **ecrã do tipo de inscrição** aparecem e solicitam o tipo de dispositivo.  
    * A TAP **(Organização) é proprietária deste dispositivo** se receber o seu dispositivo da sua organização. Em seguida, salte para [Proteger todo](#secure-entire-device) o dispositivo neste artigo para terminar a configuração.  
    * Toque **em mim, dono deste dispositivo,** se estiver a usar um dispositivo pessoal que trouxe de casa. Então continue para o próximo passo.  

    Se não vir este ecrã, salte para [proteger todo o dispositivo](#secure-entire-device) para terminar a configuração.  
    
    ![Exemplo de screenshot do Portal da Empresa, ecrã "Select device and registration type", opções do tipo de dispositivo.](./media/ios-device-type-1909.PNG)  


5. Escolha como proteger os dados do seu dispositivo uma vez matriculado.  
    * Toque **em Proteger todo** o dispositivo para proteger todas as aplicações e dados do dispositivo. Em seguida, vá para [Secure todo o dispositivo](enroll-your-device-in-intune-ios.md#secure-entire-device) para terminar a configuração.
    * Toque em **aplicativos e dados relacionados com o trabalho seguros apenas** para proteger apenas as aplicações e dados a que acede com a sua conta de trabalho. Em seguida, vá para [Secure apps e dados relacionados](enroll-your-device-in-intune-ios.md#secure-work-related-apps-and-data)com o trabalho .  

    ![Exemplo de screenshot do Portal da Empresa, ecrã "Select device and registration type", opções do tipo de inscrição.](./media/ios-enrollment-type-1909.PNG)  


### <a name="secure-entire-device"></a>Proteja todo o dispositivo  

1. No ecrã de **gestão e privacidade** do Dispositivo, leia a lista de informações do dispositivo que a sua organização pode e não consegue ver. Em seguida, toque **em Continuar**.  


 > [!IMPORTANT]
> Estes próximos passos e ecrãs diferirão consoante a sua versão iOS. Siga os passos para a sua versão iOS. 

2. O Safari abre o website do Portal da Empresa no seu dispositivo. Quando for solicitado para descarregar o perfil de configuração, toque **em Permitir**. Se estiver num dispositivo em funcionamento:  
    * iOS 12.2 e mais tarde: Quando o download estiver concluído, toque em **Fechar**. Então continue a passo 3.  
    * iOS 12.1 e mais cedo: Quando o download estiver concluído, é automaticamente redirecionado para a aplicação Definições. Passe para o passo 4.  
 
    Se tocar acidentalmente **em Ignore,** refresque a página. Ser-lhe-á pedido que abra a aplicação portal da empresa. Assim que lá estiver, toque **em Baixar novamente.**

  > [!NOTE]
  > Deve instalar o perfil de gestão conforme descrito nos próximos passos dentro de 8 minutos após o seu download. Se não o fizer, o perfil será removido e terá de reiniciar a inscrição.  

3. Quando for solicitado a abrir o Portal da Empresa, toque **em Open**. Leia as informações sobre o ecrã **'Perfil de Gestão'.**  

4. Vá à aplicação Definições e toque **em Inscrever-se em < nome da organização >** ou Perfil **Descarregado**.  

    ![Exemplo de screenshot da aplicação Definições, Inscreva-se na opção de organização.](./media/enroll-in-organization-ios-1909.PNG)  

   Se nenhuma das opções aparecer, vá ao **Perfil geral** de perfis de > e ao perfil de **gestão**> de **dispositivos.** Se ainda não vir um perfil de gestão, poderá ter de o descarregar novamente.  

5. Toque em **Instalar**.  
    
6. Introduza a palavra-passe do seu dispositivo. Em seguida, toque em **instalar**.    

7. O próximo ecrã é um sistema padrão alertando sobre a gestão do dispositivo. Para continuar com a instalação, toque em **instalar**. Se for solicitado a confiar na gestão remota, toque no **Trust.**  

8. Depois de a instalação estar concluída, toque em **Done**. Para verificar se o perfil foi instalado, vá às definições de Gestão de **Perfis e Dispositivos.** Deve ver o perfil listado no âmbito da **Mobile Device Management**.   

    ![Exemplo de screenshot da aplicação Definições, Definições de Gestão de Perfis e Dispositivos, mostrando o perfil de gestão.](./media/ios-12-cp-enroll-1904.PNG)  

9. Volte à aplicação Portal da Empresa. O Portal da Empresa começará a sincronizar e a configurar o seu dispositivo. O Portal da Empresa pode instá-lo a atualizar as definições adicionais do dispositivo. Se isso acontecer, toque **em Continuar**.  

10. Saberá que a configuração está completa quando todos os itens da lista mostrarem uma marca de verificação verde. Toque em **Concluído**.   

> [!Note]
> Se a sua organização monitorizar os limites de voz e dados, ou lhe fornecer um dispositivo da empresa, poderá ter mais alguns passos para ser concluído. Se for solicitado a instalar a aplicação **Datalert,** consulte [a inscrição do seu dispositivo na gestão](enroll-your-device-with-telecom-expense-management-ios.md)de despesas de telecomunicações. Se a sua organização faz parte do Programa de Inscrição de Dispositivos da Apple, descubra [como inscrever o seu dispositivo da empresa.](enroll-your-device-dep-ios.md)  

### <a name="secure-work-related-apps-and-data"></a>Aplicativos e dados relacionados com o trabalho seguros  
1. O ecrã **de download microsoft authenticator** aparece (se já tiver autenticador, não verá este ecrã por isso salte para o passo 2).  
    1. Toque **em download a partir da App Store.**
    2. Quando a App Store abrir, instale a aplicação. 
    3. Volte ao Portal da Empresa e toque **em Continuar.**    
    
   Depois de instalar o Microsoft Authenticator, não terá de fazer mais nada com a aplicação. Só precisa estar presente no seu dispositivo. 

   ![Exemplo de screenshot do Portal da Empresa, ecrã "Download Microsoft Authenticator".](./media/download-ms-authenticator-1909.PNG)  

2. No ecrã de **gestão e privacidade** do Dispositivo, leia a lista de informações do dispositivo que a sua organização pode e não consegue ver. Em seguida, toque **em Continuar**.  


 > [!IMPORTANT]
> Estes próximos passos e ecrãs diferirão consoante a sua versão iOS. Siga os passos para a sua versão iOS. 

3. O Safari abre o website do Portal da Empresa no seu dispositivo. Quando for solicitado para descarregar o perfil de configuração, toque **em Permitir**. Se estiver num dispositivo em funcionamento:  
    * iOS 12.2 e mais tarde: Quando o download estiver concluído, toque em **Fechar**. Então continue a passo 4.  
    * iOS 12.1 e mais cedo: Quando o download estiver concluído, é automaticamente redirecionado para a aplicação Definições. Passe para o passo 5.  
 
    Se tocar acidentalmente **em Ignore,** refresque a página. Ser-lhe-á pedido que abra a aplicação portal da empresa. A partir da aplicação, pode voltar a tocar no **Download**.

  > [!NOTE]
  > Deve instalar o perfil de gestão conforme descrito nos próximos passos dentro de 8 minutos após o seu download. Se não o fizer, o perfil será removido e terá de reiniciar a inscrição.  

4. Quando for solicitado a abrir o Portal da Empresa, toque **em Open**. Leia as informações sobre o ecrã **'Perfil de Gestão'.** 

5. Vá à aplicação Definições e toque **em Inscrever-se em < nome da organização >** ou Perfil **Descarregado**.  

    ![Exemplo de screenshot da aplicação Definições, Inscreva-se na opção de organização.](./media/enroll-in-organization-ios-1909.PNG)  

   Se nenhuma das opções aparecer, vá ao **Perfil geral** de perfis de > e ao perfil de **gestão**> de **dispositivos.** Se ainda não vir um perfil de gestão, poderá ter de o descarregar novamente.   


6. No ecrã de inscrição do **utilizador,** toque **em Inscrever o meu iPhone**.  

    ![Exemplo de screenshot da aplicação Definições, ecrã de inscrição do utilizador, realçando o botão de inscrição.](./media/user-enrollment-information-1909.PNG)  

7. Introduza a senha do dispositivo. Em seguida, toque em **instalar**.  

8. No **ecrã do Sign o** ecrã, introduza a palavra-passe para o seu Apple ID gerido. Na maioria dos casos, estas credenciais serão as mesmas que usa para iniciar sessão na sua conta de trabalho ou escolar, a menos que a sua organização lhe tenha fornecido um conjunto diferente de credenciais. 
9. Toque **em Iniciar sessão**.  
10. Uma mensagem de sucesso aparecerá no ecrã brevemente após a instalação do perfil. Para verificar se o perfil está instalado, vá às definições de de **Gestão** de Perfis e Dispositivos. Deve ver o perfil listado na Gestão de **Dispositivos Móveis.**  

    ![Exemplo de screenshot da aplicação Definições, Definições de Gestão de Perfis e Dispositivos, mostrando o perfil de gestão.](./media/ios-12-cp-enroll-1904.PNG)  

11. Volte à aplicação Portal da Empresa. O Portal da Empresa começará a sincronizar e a configurar o seu dispositivo. O Portal da Empresa pode instá-lo a atualizar as definições adicionais do dispositivo. Se isso acontecer, toque **em Continuar**.    

12. Saberá que a configuração está completa quando todos os itens da lista mostrarem uma marca de verificação verde. Toque **pronto.**  

## <a name="it-administrator-support"></a>Suporte do administrador de TI  
Se for administrador de TI e se encontrar com problemas durante a inscrição de dispositivos, consulte problemas de [inscrição de dispositivos iOS de resolução de problemas no Microsoft Intune](https://support.microsoft.com/en-us/help/4039809). Este artigo enumera erros comuns, as suas causas e passos para os resolver.  

## <a name="next-steps"></a>Próximos passos  
Encontre aplicativos que o ajudem no trabalho ou na escola. Saiba como as [aplicações são disponibilizadas](use-managed-apps-on-your-device-ios.md) através do Portal da Empresa.  

Ainda precisa de ajuda? Contacte o suporte da empresa. Pode encontrar as informações de contacto no [Site do Portal da Empresa](https://go.microsoft.com/fwlink/?linkid=2010980).  
