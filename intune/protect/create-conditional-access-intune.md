---
title: Configurar o acesso condicional com base no dispositivo com o Intune
titleSuffix: Microsoft Intune
description: Saiba como criar uma política de acesso condicional com base em dispositivo com base na conformidade do dispositivo Microsoft Intune e no gerenciamento de aplicativo móvel.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4a66f16ea681ec75a4a3aa7d85a57c4faa555ab9
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72504518"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Criar uma política de acesso condicional com base no dispositivo

Com o Intune, você pode aprimorar o acesso condicional no Azure Active Directory adicionando a conformidade do dispositivo móvel aos controles de acesso. Depois de criar uma política de conformidade do Intune que define os requisitos para que os dispositivos sejam compatíveis, você pode usar o status de conformidade do dispositivo para permitir ou bloquear o acesso aos seus aplicativos e serviços. Você pode fazer isso criando uma política de acesso condicional que usa a configuração **exigir que o dispositivo seja marcado como compatível**.  

Uma política de acesso condicional especifica o aplicativo ou os serviços que você deseja proteger, as condições sob as quais os aplicativos ou serviços podem ser acessados e os usuários aos quais a política se aplica. O acesso condicional é um recurso do Azure AD Premium que é configurável no Azure Active Directory, mas você também pode configurar essas mesmas políticas no portal do Intune. O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*.  

> [!IMPORTANT]
> Antes de configurar o acesso condicional, você precisará configurar políticas de conformidade do dispositivo do Intune para avaliar dispositivos com base em se eles atendem a requisitos específicos. Consulte Introdução [às políticas de conformidade do dispositivo no Intune](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Criar política de acesso condicional

1. No portal do Intune, selecione **acesso condicional** > **políticas** > **nova política**.
   
    ![Criar uma nova política de acesso condicional](./media/create-conditional-access-intune/create-ca.png)
 
2. Em **Atribuições**, selecione **Utilizadores e grupos**. 
3. Na guia **incluir** , identifique os usuários ou grupos aos quais você deseja que essa política de acesso condicional seja aplicada. Depois de escolher quem deseja incluir, você poderá usar a guia **excluir** se houver usuários, funções ou grupos que você deseja excluir dessa política.  
    - **Todos os usuários**: Selecione esta opção para aplicar a política a todos os usuários e grupos, incluindo usuários internos e convidados.
  
    - **Selecionar usuários e grupos**: Selecione esta opção e especifique uma ou mais das seguintes opções:
  
      a. **Todos os usuários convidados**: Selecione esta opção para incluir ou excluir usuários convidados externos (por exemplo, parceiros, colaboradores externos)
       
      b. **Funções de diretório**: selecione uma ou mais funções do Azure ad para incluir ou excluir usuários que recebem essas funções.
      
      c. **Usuários e grupos**: Selecione esta opção para procurar e Selecionar usuários ou grupos individuais que você deseja incluir ou excluir.
     
       > [!TIP]  
       > Teste a política em relação a um grupo menor de usuários para verificar se ele funciona conforme o esperado.
4. Selecione **Concluído**.
5. Em **Atribuições**, selecione **Aplicações na Cloud**. 
6. Na **guia incluir**, identifique os aplicativos e serviços que você deseja proteger com essa política de acesso condicional. Em seguida, você poderá usar a guia **excluir** se houver aplicativos ou serviços que você deseja excluir dessa política.
    - **Todos os aplicativos de nuvem**: Selecione esta opção para aplicar a política a todos os aplicativos.
      > [!IMPORTANT]  
      > O aplicativo de gerenciamento de Microsoft Azure para acesso ao portal do Azure está incluído nesta lista. Certifique-se de usar a guia **excluir** aqui ou nas opções **usuários e grupos** para verificar se você (ou os usuários ou grupos designados) poderá entrar no portal do Azure. 

    - **Selecionar aplicativos**: Selecione essa opção, escolha **selecionar**e, em seguida, use a lista de aplicativos para procurar e selecionar os aplicativos ou serviços que você deseja proteger.
    
      ![Criar uma nova política de acesso condicional](./media/create-conditional-access-intune/create-ca-select-apps.png)

7. Selecione **Concluído**.
8. Em **atribuições**, selecione **condições**.
    - **Risco de entrada**: escolha Sim para usar Azure ad Identity Protection detecção de risco de entrada com essa política e, em seguida, escolha os níveis de risco de entrada aos quais a política deve se aplicar.
    - **Plataformas de dispositivo**: na guia **incluir** , identifique as plataformas de dispositivo às quais você deseja aplicar essa política de acesso condicional. Use a guia **excluir** para excluir plataformas desta política.
    - **Locais**: na guia **incluir** , especifique se a política se aplica a qualquer local, locais de rede confiáveis que estejam sob o controle do seu departamento de ti ou locais de rede específicos. Use a guia **excluir** para excluir locais de rede desta política. 
    - **Aplicativos cliente**: escolha **Sim** para especificar se a política deve ser aplicada a aplicativos de navegador, aplicativos móveis e clientes de desktop. Você também pode selecionar **clientes de autenticação modernos** (como Outlook para Ios ou Outlook para Android) e **clientes do Exchange ActiveSync**.
    - **Estado do dispositivo**: a política de acesso condicional será aplicada a todos os Estados do dispositivo, a menos que você escolha Sim e exclua especificamente o dispositivo do Azure ad híbrido ingressado no dispositivo ou marcado como em conformidade (ou ambos).
    
      ![Criar uma nova política de acesso condicional](./media/create-conditional-access-intune/create-ca-device-platforms.png)

      > [!TIP]  
      > Se você quiser proteger clientes de **autenticação modernos** e **clientes do Exchange ActiveSync**, crie duas políticas de acesso condicional separadas, uma para cada tipo de cliente. Embora o Exchange ActiveSync dê suporte à autenticação moderna, a única condição com suporte do Exchange ActiveSync é a plataforma. Não há suporte para outras condições, incluindo a autenticação multifator. Para proteger efetivamente o acesso ao Exchange Online do Exchange ActiveSync, crie uma política de acesso condicional que especifique o aplicativo de nuvem Office 365 Exchange Online e o aplicativo cliente Exchange ActiveSync com aplicar política somente a plataformas com suporte selecionadas.

9. Selecione **Concluído**.
10. Em **Controlos de acesso**, selecione **Concessão**. Configure o que acontece com base nas condições que você configurou.  Você pode selecionar uma das seguintes opções:
    - **Bloquear acesso**: os usuários especificados nesta política terão o acesso negado aos aplicativos sob as condições que você especificou.
    - **Conceder acesso**: os usuários especificados nesta política receberão acesso, mas você poderá exigir qualquer uma das seguintes ações adicionais:
      - **Exigir autenticação multifator**: o usuário precisará concluir requisitos de segurança adicionais, como uma chamada telefônica ou um texto.
      - **Exigir que o dispositivo seja marcado como compatível**: o dispositivo deve ser compatível com o Intune. Se o dispositivo não for compatível, o usuário terá a opção de registrar o dispositivo no Intune. 
      - **Requer um dispositivo ingressado no Azure ad híbrido**: os dispositivos devem ser ingressados no Azure ad híbrido.
      - **Exigir aplicativo cliente aprovado**: o dispositivo deve usar aplicativos cliente aprovados. 
      - **Para vários controles**: selecione **exigir todos os controles selecionados** para que todos os requisitos acima sejam aplicados quando um dispositivo tentar acessar o aplicativo.
    
      ![Configurações de concessão de controles de acesso](./media/create-conditional-access-intune/create-ca-grant-access-settings.png)
 
11. Em **Ativar política**, selecione **Ativar**.
     
     ![Habilitar a política](./media/create-conditional-access-intune/enable-policy.png)

12. Selecione **Criar**.

## <a name="see-also"></a>Consulte também
[Acesso condicional baseado em aplicativo com o Intune](app-based-conditional-access-intune.md)

[Solucionando problemas de acesso condicional do Intune](https://support.microsoft.com/help/4456106)