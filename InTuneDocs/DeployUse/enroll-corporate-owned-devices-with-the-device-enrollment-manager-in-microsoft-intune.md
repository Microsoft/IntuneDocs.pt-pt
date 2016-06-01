---
# required metadata

title: Inscrever dispositivos pertencentes à empresa com o Gestor de Inscrição de Dispositivos no Microsoft Intune | Microsoft Intune
description:
keywords:
author: NathBarn
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Inscrever dispositivos pertencentes à empresa com o Gestor de Inscrição de Dispositivos no Microsoft Intune
As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador. A conta do *gestor de inscrição de dispositivos* é uma conta especial do Intune, que tem permissão para inscrever mais de cinco dispositivos. Pode atribuir uma conta de utilizador de gestor de inscrição de dispositivos a um gerente ou supervisor de loja para, por exemplo, permitir ao mesmo:

-   Inscrever dispositivos no Intune

-   Iniciar sessão no portal da empresa para obter aplicações da empresa

-   Instalar e desinstalar software

-   Configurar acesso a dados da empresa

Utilize apenas a conta do gestor de dispositivos para os dispositivos que não irão receber e-mails ou iniciar sessão como um utilizador específico. Não é possível configurar dispositivos geridos com uma conta do gestor de dispositivos com acesso condicional, uma vez que estes também são cenários por utilizador. O gerente da loja não pode repor o dispositivo a partir do portal da empresa.

Exemplos de cenários do gestor de inscrição de dispositivos: Um restaurante pretende obter tablets de ponto de venda para os seus empregados de mesa e monitores de apresentação de pedidos para os empregados da cozinha. Os empregados nunca precisam de aceder a dados da empresa ou de iniciar sessão como um utilizador. O administrador do Intune cria uma conta do gestor de inscrição de dispositivos e inscreve os dispositivos da empresa através dessa conta.

Em alternativa, o administrador pode conceder as credenciais de gestor de inscrição de dispositivos ao gestor do restaurante, o que lhe permitirá inscrever e gerir os dispositivos. O administrador ou gestor podem implementar aplicações específicas de cada função nos dispositivos do restaurante.

> [!NOTE]
> Um administrador também pode selecionar o dispositivo na consola do Intune e extingui-lo da gestão de dispositivos móveis com a consola de administração. As contas de utilizador do gestor de inscrição de dispositivos com mais de 20 dispositivos inscritos poderão ter problemas ao utilizar a aplicação Portal da Empresa.

## Para implementar aplicações da empresa em dispositivos geridos com o gestor de inscrição de dispositivos, implemente a aplicação Portal da Empresa como uma **Instalação Necessária** na conta de utilizador do gestor de inscrição de dispositivos.
Criar contas de gestor de inscrição de dispositivos As contas de gestor de inscrição de dispositivos são contas de utilizador que têm permissão para inscrever um grande número de dispositivos pertencentes à empresa.

#### Apenas os utilizadores da consola do Intune podem ser gestores de inscrição de dispositivos.

1.  Adicionar um gestor de inscrição de dispositivos ao Intune

2.  Aceda ao [portal de contas do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) e inicie sessão na sua conta de administrador.

3.  Clique em **Adicionar utilizador** Confirme que a conta de utilizador que será o gestor de inscrição de dispositivos é apresentada. Caso contrário, adicione o utilizador ao clicar em **Novo** e concluir o processo Adicionar utilizador. É necessária uma licença de subscrição para cada utilizador que aceda ao Serviço. O *gestor de inscrição de dispositivos* não pode ser um administrador do Intune.

4.  Determine se precisa de adicionar mais licenças antes de utilizar esta funcionalidade.

5.  Inicie sessão na [consola de administração do Microsoft Intune](http://manage.microsoft.com) com o seu início de sessão de administrador. No painel de navegação, clique em **Admin**, aceda à **Gestão de Administrador** e selecione **Gestor de Inscrição de Dispositivos**.

6.  A página Gestores de Inscrição de Dispositivos é aberta. Clique em **Adicionar…**.

7.  A caixa de diálogo **Adicionar Gestor de Inscrição de Dispositivos** é aberta. Introduza o **ID de Utilizador** da conta do Intune e, em seguida, clique em **OK**.

8.  O utilizador do gestor de inscrição de dispositivos não pode ser um administrador do Intune.

## O gestor de inscrição de dispositivos agora pode inscrever dispositivos móveis com o mesmo procedimento utilizado por um utilizador final num cenário BYOD no portal da empresa.

1.  Eliminar um gestor de inscrição de dispositivos do Intune

2.  Inicie sessão no [Portal de administração do Microsoft Intune](http://manage.microsoft.com) com o seu início de sessão de administrador. No painel de navegação, clique em **Admin** , aceda à **Gestão de Administrador** e selecione **Gestor de Inscrição de Dispositivos**.

3.  A página Gestores de Inscrição de Dispositivos é aberta. Selecione o **Utilizador** do gestor de inscrição de dispositivos que pretende eliminar e, em seguida, clique em **Eliminar**. Este utilizador não será eliminado do Intune e os dispositivos geridos pelo mesmo continuarão inscritos no Intune.

4.  A eliminação de um gestor de inscrição de dispositivos impede o utilizador de inscrever mais dispositivos no Intune.

Clique em **Sim** para confirmar que pretende eliminar o gestor de inscrição de dispositivos. A eliminação de um gestor de inscrição de dispositivos não afeta os dispositivos inscritos.

-   Quando um gestor de inscrição de dispositivos é eliminado:

-   Os dispositivos inscritos não são afetados

-   Os dispositivos inscritos continuam a ser completamente geridos

-   As credenciais da conta de gestor de inscrição de dispositivos eliminada mantêm-se válidas para o início de sessão no portal da empresa para aceder a aplicações

-   As credenciais da conta de gestor de inscrição de dispositivos eliminada continuam sem poder apagar ou extinguir dispositivos


<!--HONumber=May16_HO2-->


