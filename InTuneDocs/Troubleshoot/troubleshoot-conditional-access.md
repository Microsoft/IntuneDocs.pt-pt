---
title: Resolver problemas de acesso condicional | Microsoft Intune
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4f79d2890c450a803bfb84ffa3c12b0de58a158c
ms.openlocfilehash: 373b9bf9794840f999d5e5b21fc411ff621a23e1


---

# Resolver problemas de acesso condicional

Este tópico descreve o que fazer quando os utilizadores não conseguem obter acesso aos recursos através de acesso condicional do Intune. 

### Princípios básicos sobre êxito no acesso condicional

Para que o acesso condicional funcione, é necessário respeitar as seguintes condições:

-   O dispositivo deve ser gerido pelo Intune.
-   O utilizador deve ser registado no Azure Active Directory (AAD)
-   O dispositivo tem de estar em conformidade com as políticas de conformidade que configurou no Intune. 
-   O EAS tem de ser ativado no dispositivo se o utilizador tentar obter correio através do cliente de correio nativo do dispositivo, em vez de através do Outlook.

Estas condições podem ser visualizadas para cada dispositivo no Portal de Gestão do Azure e no relatório de inventário do dispositivo.





Normalmente, um utilizador tenta aceder ao e-mail ou ao SharePoint e recebe uma mensagem para se inscrever. Esse pedido direciona o utilizador para o portal da empresa. Seguem-se explicações possíveis para este comportamento e soluções sugeridas:

## Cenários de autenticação moderna

### Problemas de inscrição

 -  O dispositivo não está inscrito, pelo que a inscrição irá resolver o problema.
 -  O utilizador inscreveu o dispositivo, mas a associação à área de trabalho falhou. O utilizador deve atualizar a inscrição no portal da empresa. 
 
### Resolver problemas de compatibilidade

 -  O dispositivo não está em conformidade com as políticas do Intune. Os problemas comuns são os requisitos de encriptação e palavra-passe. O utilizador será redirecionado para o portal da empresa, onde pode configurar o respetivo dispositivo para estar em conformidade.
 -  Para dispositivos iOS, um perfil de e-mail existente criado pelo utilizador irá bloquear a implementação de um perfil de conformidade (criado pelo administrador do Intune) a partir do Intune. Este é um problema comum, uma vez que os utilizadores do iOS criam um perfil de e-mail e depois fazem a inscrição. O portal da empresa irá informar o utilizador que não são compatíveis devido ao respetivo perfil de e-mail configurado manualmente e solicitam ao utilizador para remover esse perfil. O utilizador deve remover o respetivo perfil de e-mail, para que o perfil do Intune possa ser implementado. Para evitar este problema, indique aos seus utilizadores para inscreverem-se sem instalar um perfil de e-mail e para permitir que o Intune implemente o perfil.  
 -  Pode demorar algum tempo para que as informações de compatibilidade sejam registadas num dispositivo. Aguarde alguns minutos e tente novamente.

### Problemas de políticas

Quando cria uma política de conformidade e associa-a a uma política de e-mail, ambas as políticas têm de ser implementadas para o mesmo utilizador, por isso tenha cuidado quando planear que políticas devem ser implementadas para os grupos. É provável que os utilizadores que tenham apenas uma política aplicada verifiquem que os seus dispositivos não são compatíveis.


## Cenários do Exchange ActiveSync


- Um dispositivo Android inscrito e compatível poderá receber um aviso de quarentena quando tentar aceder a recursos empresariais. Antes de escolher a ligação que indica **Começar**, o utilizador deve certificar-se de que o portal da empresa não estava aberto quando tentou aceder aos recursos. Os utilizadores devem fechar o portal da empresa, tentar aceder de novo aos recursos e, em seguida, selecionar a ligação **Começar**.

- Um dispositivo extinto pode continuar a ter acesso várias horas depois de ser retirado. Isto acontece porque o Exchange coloca os direitos de acesso à memória cache a cada 6 horas. Considere outros meios de proteger dados em dispositivos extintos neste cenário.
- Possível problema, não é possível corrigir o EASID para o AAD. Uma causa comum deste problema é a limitação, por isso, aguarde alguns minutos e tente novamente. 

## Recolher registos de caixa de correio do OWA

Se os problemas de conetividade do Exchange persistirem depois de resolver os problemas de implementação, recolha os registos da caixa de correio do OWA antes de contactar a Microsoft Support, conforme descrito no artigo [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

1. Inicie sessão através do OWA e escolha o símbolo de definições (engrenagem) junto ao seu nome no canto superior direito. 
2. Selecione **Opções**
3. Selecione **Telemóvel** (poderá ser **Dispositivos Móveis**) na coluna no lado esquerdo.
4. No menu superior, selecione **Dispositivos Móveis**. 
5. Escolha o seu dispositivo da lista e, em seguida, escolha **Iniciar o registo**. 
6. Quando for solicitado, selecione **Sim** na caixa de diálogo de pop-up. 
7. Execute a ação que causou o problema, para que possa reproduzi-la. 
8. Aguarde 1-2 minutos e depois volte para a lista telefónica no OWA (certifique-se de que o seu telemóvel está selecionado na lista) e a partir do menu superior escolha **Obter Registo**. 
9. Deverá receber um e-mail enviar por si com um anexo. Quando abre um pedido de suporte, forneça o conteúdo do e-mail ao Microsoft Support.


### Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Jun16_HO4-->


