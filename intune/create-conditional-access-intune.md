---
title: Configurar o acesso condicional com base no dispositivo com o Intune
titleSuffix: Microsoft Intune
description: Saiba como criar uma política de acesso condicional com base no dispositivo com base na conformidade de dispositivos do Microsoft Intune e a gestão de aplicações móveis.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/22/2019
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5299ef8c0159592c9754f886fe1c3d90a6637599
ms.sourcegitcommit: 4980c094faaca452f8ec8ddded04f47b3229ff38
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/16/2019
ms.locfileid: "65765378"
---
# <a name="create-a-device-based-conditional-access-policy"></a>Criar uma política de acesso condicional com base no dispositivo

Com o Intune, pode melhorar o acesso condicional no Azure Active Directory através da adição de conformidade de dispositivos móveis para os controlos de acesso. Depois de criar uma política de conformidade do Intune que define os requisitos de dispositivos estar em conformidade, pode utilizar o estado de conformidade de um dispositivo para permitir ou bloquear o acesso às suas aplicações e serviços. Pode fazê-lo ao criar uma política de acesso condicional utiliza a definição **pedir que o dispositivo ser marcado como compatível**.  

Uma política de acesso condicional Especifica a aplicação ou serviços que pretende proteger, as condições sob as quais podem aceder a aplicações ou serviços e os utilizadores a quem se aplica a política. Acesso condicional é uma funcionalidade premium do Azure AD que pode ser configurada no Azure Active Directory, mas também pode configurar estas políticas mesmo no portal do Intune. O nó de Acesso Condicional acedido a partir do *Intune* é o mesmo nó acedido a partir do *Azure AD*.  

> [!IMPORTANT]
> Antes de configurar o acesso condicional, terá de configurar políticas de conformidade de dispositivos do Intune para avaliar os dispositivos com base em se eles satisfazer os requisitos específicos. Ver [começar a utilizar com políticas de conformidade de dispositivos no Intune](device-compliance-get-started.md).

## <a name="create-conditional-access-policy"></a>Criar uma política de acesso condicional

1.  No portal do Intune, selecione **acesso condicional** > **políticas** > **nova política**.
   
    ![Criar uma nova política de acesso condicional](media/create-conditional-access-intune/create-ca.png)
 
2.  Em **Atribuições**, selecione **Utilizadores e grupos**. 
3.  Sobre o **inclusão** separador, identifique os utilizadores ou grupos a quem pretende que esta política de acesso condicional para aplicar. Depois de escolher quem incluir, pode utilizar o **excluir** separador se existirem quaisquer utilizadores, funções ou grupos que pretende excluir desta política.  
    - **Todos os utilizadores**: Selecione esta opção para aplicar a política a todos os utilizadores e grupos, incluindo usuários internos e convidados.
  
    - **Selecionar utilizadores e grupos**: Selecione esta opção e especificar um ou mais das seguintes opções:
  
      a. **Todos os utilizadores convidados**: Selecione esta opção para incluir ou excluir utilizadores convidados externos (por exemplo, parceiros, colaboradores externos)
       
      b. **Funções de diretório**: Selecione um ou mais funções do Azure AD para incluir ou excluir utilizadores que estão atribuídos estas funções.
      
      c. **Utilizadores e grupos**: Selecione esta opção para procurar e selecionar utilizadores individuais ou grupos aos que quais pretende incluir ou excluir.
     
       > [!TIP]  
       > Teste a política em relação a um grupo de utilizadores para se certificar de que funciona como esperado.
4.  Selecione **Done** (Concluído).
5.  Em **Atribuições**, selecione **Aplicações na Cloud**. 
6.  Sobre o **inclusão separador**, identificar as aplicações e serviços que pretende proteger com esta política de acesso condicional. Pode utilizar o **excluir** separador se existirem quaisquer aplicações ou serviços que pretende excluir desta política.
    - **Todas as aplicações na cloud**: Selecione esta opção para aplicar a política a todas as aplicações.
      > [!IMPORTANT]  
      > A aplicação de gestão do Microsoft Azure para o acesso ao portal do Azure está incluída nesta lista. Certifique-se de que utilize o **excluir** separador um aqui ou no **utilizadores e grupos** opções para se certificar de que (ou os utilizadores ou grupos designados por si) será capazes de iniciar sessão no portal do Azure. 

    - **Selecionar aplicações**: Selecione esta opção, escolha **selecione**e, em seguida, utilize a lista de aplicações para procurar e selecione as aplicações ou serviços que pretende proteger.
    
      ![Criar uma nova política de acesso condicional](media/create-conditional-access-intune/create-ca-select-apps.png)

7.  Selecione **Done** (Concluído).
8.  Sob **atribuições**, selecione **condições**.
    - **Início de sessão de risco**: Escolha Sim para utilizar a deteção de risco de início de sessão do Azure AD Identity Protection com esta política e, em seguida, selecione os níveis de risco de início de sessão que deve aplicar a política para.
    - **Plataformas de dispositivos**: Sobre o **inclusão** separador, identificar as plataformas de dispositivos que pretende esta política de acesso condicional para aplicar a. Utilize o **excluir** separador para excluir plataformas desta política.
    - **Localizações**: Sobre o **inclusão** separador, especifique se a política se aplica a qualquer localização, localizações de rede fidedigna, que estão sob o controle do seu departamento de TI ou localizações de rede específicas. Utilize o **excluir** separador para excluir localizações de rede desta política. 
    - **Aplicações de cliente**: Escolher **Sim** para especificar se deve aplicar a política para aplicações de browser, aplicações móveis e clientes de ambiente de trabalho. Também pode selecionar **clientes de autenticação moderna** (como o Outlook para iOS ou o Outlook para Android) e **clientes do Exchange ActiveSync**.
    - **Estado do dispositivo**: Será aplicada a política de acesso condicional para todos os Estados de dispositivo, a menos que escolha Sim e exclua especificamente os Estados de dispositivo híbrido do Azure AD associado ou dispositivo marcado como compatível (ou ambos).
    
      ![Criar uma nova política de acesso condicional](media/create-conditional-access-intune/create-ca-device-platforms.png)

      > [!TIP]  
      > Se pretender proteger tanto **autenticação moderna** clientes e **clientes do Exchange ActiveSync**, criar duas políticas de acesso condicional separados, um para cada tipo de cliente. Embora o Exchange ActiveSync suporta autenticação moderna, a única condição que é suportada pelo Exchange ActiveSync é a plataforma. Outras condições, incluindo autenticação multifator, não são suportadas. Para proteger efetivamente o acesso ao Exchange Online do Exchange ActiveSync, crie uma política de acesso condicional que especifica a aplicação de cloud do Office 365 Exchange Online e a aplicação de cliente do Exchange ActiveSync com aplicar política apenas a plataformas suportadas selecionadas.

9.  Selecione **Done** (Concluído).
10. Em **Controlos de acesso**, selecione **Concessão**. Configure o que acontece com base nas condições que configurou.  Pode selecionar entre as seguintes opções:
    - **Bloquear o acesso**: Os utilizadores especificados nesta política serão negados acesso às aplicações sob as condições que especificou.
    - **Conceder acesso**: Os utilizadores especificados nesta política serão concedidos acesso, mas pode exigir que qualquer uma das seguintes ações adicionais:
      - **Exigir autenticação multifator**: O utilizador terá de concluir os requisitos de segurança adicionais, como uma chamada telefónica ou texto.
      - **Exigir dispositivo seja marcado como compatível**: O dispositivo tem de estar em conformidade com Intune. Se o dispositivo não está em conformidade, o utilizador terá a opção para inscrever o dispositivo no Intune. 
      - **Requerer dispositivo associado do Azure AD híbrido**: Dispositivos têm de estar associados ao Azure AD híbrido.
      - **Exigir aplicação aprovada do cliente**: O dispositivo tem de utilizar aplicações aprovadas do cliente. 
      - **Para vários controles**: Selecione **necessitam de todos os controlos selecionados** para que todos os requisitos acima são aplicados quando um dispositivo se tentar aceder à aplicação.
    
      ![Definições de concessão de controles de acesso](media/create-conditional-access-intune/create-ca-grant-access-settings.png)
 
11. Em **Ativar política**, selecione **Ativar**.
     
     ![Ativar a política](media/create-conditional-access-intune/enable-policy.png)

12. Selecione **Criar**.

## <a name="see-also"></a>Consulte também
[Acesso condicional com base na aplicação com o Intune](app-based-conditional-access-intune.md)

[Resolução de problemas de acesso condicional do Intune](https://support.microsoft.com/help/4456106)
