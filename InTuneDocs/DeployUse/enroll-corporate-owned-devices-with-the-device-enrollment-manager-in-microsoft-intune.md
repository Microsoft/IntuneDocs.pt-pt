<<<<<<< HEAD
---
title: "Inscrever com o gestor de inscrição de dispositivos | Microsoft Intune"
description: "A conta do gestor de inscrição de dispositivos (DEM) pode gerir um grande número de dispositivos móveis pertencentes à empresa partilhados com uma única conta de utilizador."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e2daff5dae435df55c866adbf602f554500d50e0
ms.openlocfilehash: 4ed3222f45cb438dea807b1df268f47fff660d5f

||||||| merged common ancestors
---
title: "Inscrever com o gestor de inscrição de dispositivos | Microsoft Intune"
description: "A conta do gestor de inscrição de dispositivos (DEM) pode gerir um grande número de dispositivos móveis pertencentes à empresa partilhados com uma única conta de utilizador."
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e2daff5dae435df55c866adbf602f554500d50e0
ms.openlocfilehash: 4ed3222f45cb438dea807b1df268f47fff660d5f

=======
---
title: "Inscrever com o gestor de inscrição de dispositivos | Microsoft Intune"
description: "A conta do gestor de inscrição de dispositivos (DEM) pode gerir um grande número de dispositivos móveis pertencentes à empresa partilhados com uma única conta de utilizador."
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 07/12/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a23abc61-69ed-44f1-9b71-b86aefc6ba03
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: cfbf04627892dd700d2e31fabe8bca357f692d51
ms.openlocfilehash: fd289e355aca46eb0abe55edf09ebe5e030bcc63

>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2

---

<<<<<<< HEAD

# Inscrever dispositivos pertencentes à empresa com o gestor de inscrição de dispositivos no Microsoft Intune
As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador. A conta do *gestor de inscrição de dispositivos* (DEM) é uma conta especial do Intune, que pode inscrever mais de 1000 dispositivos. Recomendamos que utilize os dispositivos inscritos através desta conta como dispositivos partilhados em vez de dispositivos pessoais (“BYOD”). Os utilizadores não poderão utilizar as aplicações de e-mail “nativas”, por exemplo.
||||||| merged common ancestors

# Inscrever dispositivos pertencentes à empresa com o gestor de inscrição de dispositivos no Microsoft Intune
As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador. A conta do *gestor de inscrição de dispositivos* (DEM) é uma conta especial do Intune, que pode inscrever mais de 1000 dispositivos. Recomendamos que utilize os dispositivos inscritos através desta conta como dispositivos partilhados em vez de dispositivos pessoais (“BYOD”). Os utilizadores não poderão utilizar as aplicações de e-mail “nativas”, por exemplo.
=======

# <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune"></a>Inscrever dispositivos pertencentes à empresa com o gestor de inscrição de dispositivos no Microsoft Intune
As organizações podem utilizar o Intune para gerir um grande número de dispositivos móveis com uma única conta de utilizador. A conta do *gestor de inscrição de dispositivos* (DEM) é uma conta especial do Intune, que pode inscrever mais de 1000 dispositivos. Cada dispositivo inscrito utiliza uma única licença. Recomendamos que utilize os dispositivos inscritos através desta conta como dispositivos partilhados em vez de dispositivos pessoais (“BYOD”). Os utilizadores não poderão utilizar as aplicações de e-mail “nativas”, por exemplo.
>>>>>>> 6851ab9d7bde3f80f14f27ebf43e5f2b265939e2

Como exemplo, pode atribuir uma conta de utilizador do gestor de inscrição de dispositivos a um gerente ou supervisor de loja para:

-   Inscrever dispositivos no Intune.

-   Iniciar sessão no Portal da Empresa para obter aplicações da empresa.

-   Instalar e desinstalar software.

-   Configurar o acesso a dados da empresa.


**Um cenário do gestor de inscrição de dispositivos:** um restaurante pretende obter tablets de ponto de venda para os empregados de mesa e monitores de apresentação de pedidos para o pessoal da cozinha. Os funcionários não precisam nunca de aceder aos dados da empresa nem de iniciar sessão como utilizadores. O administrador do Intune cria uma conta do gestor de inscrição de dispositivos e inscreve os dispositivos da empresa através dessa conta. Em alternativa, o administrador pode conceder as credenciais de gestor de inscrição de dispositivos ao gestor do restaurante, o que lhe permitirá inscrever e gerir os dispositivos.

O administrador ou gestor pode implementar aplicações específicas de cada função nos dispositivos do restaurante. Um administrador também pode selecionar o dispositivo na consola do Intune e extingui-lo da gestão de dispositivos móveis com a consola de administração.

Os dispositivos inscritos com uma conta de gestor de inscrição de dispositivos têm as seguintes limitações:
  - Não existe um “utilizador” de dispositivo específico, por conseguinte, não existe acesso aos dados da empresa ou ao e-mail. No entanto, a VPN, por exemplo, poderá continuar a fornecer aplicações de dispositivos com acesso a dados.
  - Não há acesso condicional, porque estes cenários são por utilizador.
  - Não é possível repor dispositivos a partir do Portal da Empresa.
  - Apenas o dispositivo local é apresentado na aplicação do Portal da Empresa ou do site.
  - Não podem utilizar aplicações Apple Volume Purchase Program (VPP) devido aos requisitos do Apple ID por utilizador para a gestão de aplicações.
  - (iOS) Também não podem ser inscritos com o Apple Configurator ou com o Apple Device Enrollment Program (DEP), mas os serviços geridos pelo DEP ou pelo Apple Configurator podem ser inscritos sem afinidade de utilizador.

> [!NOTE]
> Para implementar aplicações da empresa em dispositivos geridos com o gestor de inscrição de dispositivos, implemente a aplicação Portal da Empresa como uma **Instalação Obrigatória** na conta de utilizador do gestor de inscrição de dispositivos.
> Para melhorar o desempenho, a visualização da aplicação Portal da Empresa num dispositivo DEM mostra apenas os dispositivos locais. A gestão remota de outros dispositivos DEM só pode ser efetuada a partir da consola de administração do Intune.

## <a name="create-device-enrollment-manager-accounts"></a>Criar contas de gestor de inscrição de dispositivos
As contas de gestor de inscrição de dispositivos são contas de utilizador que têm permissão para inscrever um grande número de dispositivos pertencentes à empresa. Apenas os utilizadores da consola do Intune podem ser gestores de inscrição de dispositivos.

#### <a name="add-a-device-enrollment-manager-to-intune"></a>Adicionar um gestor de inscrição de dispositivos ao Intune

1.  Aceda ao [Portal de contas do Microsoft Intune](http://go.microsoft.com/fwlink/?LinkId=698854) e inicie sessão na sua conta de administrador.

2.  Selecione **Adicionar utilizador**.

3.  Confirme que a conta de utilizador que será o gestor de inscrição de dispositivos é apresentada. Caso contrário, adicione o utilizador ao escolher **Novo** e ao concluir o processo **Adicionar utilizador**. É necessária uma licença de subscrição para cada utilizador que aceda ao serviço. O gestor de inscrição de dispositivos não pode ser um administrador do Intune. Determine se precisa de adicionar mais licenças antes de utilizar esta funcionalidade.

4.  Inicie sessão na [Consola de administração do Microsoft Intune](http://manage.microsoft.com) com as suas credenciais de administrador.

5.  No painel de navegação, selecione **Admin**, aceda à **Gestão de Administrador** e selecione **Gestor de Inscrição de Dispositivos**. A página **Gestores de Inscrição de Dispositivos** é apresentada.

6.  Selecione **Adicionar...**. A caixa de diálogo **Adicionar Gestor de Inscrição de Dispositivos** é aberta.

7.  Introduza o **ID de Utilizador** da conta do Intune e, em seguida, selecione **OK**. O utilizador do gestor de inscrição de dispositivos não pode ser um administrador do Intune.

8.  O gestor de inscrição de dispositivos agora pode inscrever dispositivos móveis com o mesmo procedimento utilizado por um utilizador final num cenário BYOD no Portal da Empresa.

## <a name="delete-a-device-enrollment-manager-from-intune"></a>Eliminar um gestor de inscrição de dispositivos do Intune

1.  Inicie sessão no [Portal de administração do Microsoft Intune](http://manage.microsoft.com) com as credenciais de administrador.

2.  No painel de navegação, selecione **Admin**, aceda à **Gestão de Administrador** e selecione **Gestor de Inscrição de Dispositivos**. A página **Gestores de Inscrição de Dispositivos** é apresentada.

3.  Selecione o **Utilizador** do gestor de inscrição de dispositivos que pretende eliminar e, em seguida, selecione **Eliminar**. Este utilizador não será eliminado do Intune e os dispositivos geridos pelo mesmo continuarão inscritos no Intune. A eliminação de um gestor de inscrição de dispositivos impede o utilizador de inscrever mais dispositivos no Intune.

4.  Selecione **Sim** para confirmar que pretende eliminar o gestor de inscrição de dispositivos.

A eliminação de um gestor de inscrição de dispositivos não afeta os dispositivos inscritos. Quando um gestor de inscrição de dispositivos é eliminado:

-   Os dispositivos inscritos não são afetados.

-   Os dispositivos inscritos continuam a ser completamente geridos.

-   As credenciais da conta de gestor de inscrição de dispositivos eliminada mantêm-se válidas para o início de sessão no Portal da Empresa para aceder a aplicações.

-   As credenciais da conta de gestor de inscrição de dispositivos eliminada continuam sem poder apagar ou extinguir dispositivos.

-   A relação da conta do gestor de inscrição de dispositivos eliminada com os dispositivos inscritos é mantida, mas não é possível inscrever mais dispositivos.



<!--HONumber=Nov16_HO3-->


