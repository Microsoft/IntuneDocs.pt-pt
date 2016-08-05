---
title: "Inscrever com o Gestor de Inscrição de Dispositivos | Microsoft Intune"
description: "A conta do gestor de inscrição de dispositivos (DEM) pode gerir um grande número de dispositivos móveis pertencentes à empresa partilhados com uma única conta de utilizador."
keywords: 
author: NathBarn
manager: arob98
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1f6f98d582ce9a686ca02682a9066d8b2162d6ab
ms.openlocfilehash: d126bbfc40cada71458b03c23e571490b4af4d44


---


# Inscrever dispositivos pertencentes à empresa com o Gestor de Inscrição de Dispositivos no Microsoft Intune
As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador. A conta do *gestor de inscrição de dispositivos* (DEM) é uma conta especial do Intune, que tem permissão para inscrever mais de 1000 dispositivos. Utilize os dispositivos inscritos através da conta do gestor de inscrição de dispositivos como dispositivos partilhados em vez de dispositivos pessoais ("BYOD"). Os utilizadores não poderão utilizar as aplicações de e-mail "nativas", por exemplo. Pode atribuir uma conta de utilizador de gestor de inscrição de dispositivos a um gerente ou supervisor de loja para, por exemplo, permitir ao mesmo:

-   Inscrever dispositivos no Intune

-   Iniciar sessão no portal da empresa para obter aplicações da empresa

-   Instalar e desinstalar software

-   Configurar acesso a dados da empresa


**Exemplos de cenários do gestor de inscrição de dispositivos:** um restaurante pretende obter tablets de ponto de venda para os empregados de mesa e monitores de apresentação de pedidos para os empregados da cozinha. Os empregados nunca precisam de aceder a dados da empresa ou de iniciar sessão como um utilizador. O administrador do Intune cria uma conta do gestor de inscrição de dispositivos e inscreve os dispositivos da empresa através dessa conta. Em alternativa, o administrador pode conceder as credenciais de gestor de inscrição de dispositivos ao gestor do restaurante, o que lhe permitirá inscrever e gerir os dispositivos.

O administrador ou gestor podem implementar aplicações específicas de cada função nos dispositivos do restaurante. Um administrador também pode selecionar o dispositivo na consola do Intune e extingui-lo da gestão de dispositivos móveis com a consola de administração.

Os dispositivos inscritos com uma conta de gestor de inscrição de dispositivos têm as seguintes restrições:
  - Nenhum utilizador específico, de modo que todos os dispositivos "não têm utilizadores;" por conseguinte, não está disponível o acesso a dados de e-mail ou empresariais apesar de a VPN, por exemplo, poder fornecer acesso a dados de aplicações de dispositivos
  - Sem acesso condicional porque estes cenários são por utilizador
  - Não é possível repor dispositivos a partir do Portal da Empresa
  - Apenas o dispositivo local é apresentado na aplicação do Portal da Empresa ou do Web site
  - Não existem aplicações de Apple Volume Purchase Program devido aos requisitos de Apple ID por utilizador para a gestão de aplicações
  - Também não podem ser inscritos com o Apple Configurator ou o programa de inscrição de dispositivos Apple (dispositivos iOS)

> [!NOTE]
> Para implementar aplicações da empresa em dispositivos geridos com o gestor de inscrição de dispositivos, implemente a aplicação Portal da Empresa como uma **Instalação Obrigatória** na conta de utilizador do gestor de inscrição de dispositivos.
> Para melhorar o desempenho, a visualização da aplicação Portal da Empresa num dispositivo DEM mostra apenas os dispositivos locais. A gestão remota de outros dispositivos DEM só pode ser efetuada a partir da consola de administração do Intune.

## Criar contas de gestor de inscrição de dispositivos
As contas de gestor de inscrição de dispositivos são contas de utilizador que têm permissão para inscrever um grande número de dispositivos pertencentes à empresa. Apenas os utilizadores da consola do Intune podem ser gestores de inscrição de dispositivos.

#### Adicionar um gestor de inscrição de dispositivos ao Intune

1.  Aceda ao [portal de contas do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) e inicie sessão na sua conta de administrador.

2.  Selecione **Adicionar utilizador**.

3.  Confirme que a conta de utilizador que será o gestor de inscrição de dispositivos é apresentada. Caso contrário, clique em **Novo** para adicionar o utilizador e conclua o processo Adicionar utilizador. É necessária uma licença de subscrição para cada utilizador que aceda ao Serviço. O *gestor de inscrição de dispositivos* não pode ser um administrador do Intune. Determine se precisa de adicionar mais licenças antes de utilizar esta funcionalidade.

4.  Inicie sessão na [consola de administração do Microsoft Intune](http://manage.microsoft.com) com o seu início de sessão de administrador.

5.  No painel de navegação, selecione **Admin**, aceda à **Gestão de Administrador** e selecione **Gestor de Inscrição de Dispositivos**. A página Gestores de Inscrição de Dispositivos é aberta.

6.  Selecione **Adicionar...**. A caixa de diálogo **Adicionar Gestor de Inscrição de Dispositivos** é aberta.

7.  Introduza o **ID de Utilizador** da conta do Intune e, em seguida, selecione **OK**. O utilizador do gestor de inscrição de dispositivos não pode ser um administrador do Intune.

8.  O gestor de inscrição de dispositivos agora pode inscrever dispositivos móveis com o mesmo procedimento utilizado por um utilizador final num cenário BYOD no portal da empresa.

## Eliminar um gestor de inscrição de dispositivos do Intune

1.  Inicie sessão no [Portal de administração do Microsoft Intune](http://manage.microsoft.com) com o seu início de sessão de administrador.

2.  No painel de navegação, selecione **Admin**, aceda a **Gestão de Administrador** e selecione **Gestor de Inscrição de Dispositivos**. A página Gestores de Inscrição de Dispositivos é aberta.

3.  Selecione o **Utilizador** do gestor de inscrição de dispositivos que pretende eliminar e, em seguida, selecione **Eliminar**. Este utilizador não será eliminado do Intune e os dispositivos geridos pelo mesmo continuarão inscritos no Intune. A eliminação de um gestor de inscrição de dispositivos impede o utilizador de inscrever mais dispositivos no Intune.

4.  Selecione **Sim** para confirmar que pretende eliminar o gestor de inscrição de dispositivos.

A eliminação de um gestor de inscrição de dispositivos não afeta os dispositivos inscritos. Quando um gestor de inscrição de dispositivos é eliminado:

-   Os dispositivos inscritos não são afetados

-   Os dispositivos inscritos continuam a ser completamente geridos

-   As credenciais da conta de gestor de inscrição de dispositivos eliminada mantêm-se válidas para o início de sessão no portal da empresa para aceder a aplicações

-   As credenciais da conta de gestor de inscrição de dispositivos eliminada continuam sem poder apagar ou extinguir dispositivos

-   A relação da conta do gestor de inscrição de dispositivos eliminada com os dispositivos inscritos é mantida, mas não é possível inscrever mais dispositivos



<!--HONumber=Jul16_HO4-->


