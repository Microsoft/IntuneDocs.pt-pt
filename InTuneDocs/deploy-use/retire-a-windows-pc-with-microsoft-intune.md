---
title: Extinguir um PC Windows | Microsoft Intune
description: Como extinguir um PC Windows gerido pelo Intune.
keywords: 
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 08/04/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5c916182-d99c-44c5-a779-3f596f261c40
ms.reviewer: owenyen
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 19e8e2b6a7eaa3cf02e4296a6fd147baa1472b61


---

# <a name="retire-a-windows-pc"></a>Extinguir um PC Windows
Utilize os seguintes passos para extinguir PCs geridos pelo Intune.

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Grupos** &gt; **Todos os Dispositivos** (ou outro grupo que contenha o computador que pretende extinguir).

2.  Selecione os dispositivos que pretende extinguir e, em seguida, escolha **Extinguir/Limpar**.

Para inscrever novamente um computador no Intune, reinstale o cliente de software no PC, com as orientações em [Instalar o cliente do PC Windows com o Microsoft Intune](install-the-windows-pc-client-with-microsoft-intune.md).

Se um computador não conseguir ligar ao Intune, é apresentada uma mensagem na área de trabalho **Dashboard**.

Quando extingue um computador:

-   Este é removido da gestão e do inventário do Intune e a licença associada ao computador é disponibilizada para reutilização. Extinguir/Eliminar remove o cliente de software do Intune, mas não remove aplicações ou dados do computador. Este extinção não efetua uma eliminação completa no computador.

-   O estado do mesmo já não é apresentado na consola do Intune.

-   O Intune remove o cliente de software do computador. Se o computador não estiver ligado ao serviço Intune, o cliente de software será removido na próxima vez que for ligado.

-   O Endpoint Protection do Microsoft Intune é removido do computador. Se o computador tiver outra aplicação de ponto final instalada e esta estiver desativada, essa aplicação pode ser ativada novamente quando o Endpoint Protection do Microsoft Intune for removido, para garantir a proteção dos seus computadores.

-   Todas as políticas serão removidas do computador e os valores que estavam definidos pela política serão alterados.

-   O computador deixará de receber atualizações de software e atualizações de definições de software maligno do serviço Intune.

-   Dependendo de como estiverem configurados, os computadores extintos poderão continuar a receber atualizações ao utilizar os Windows Server Update Services, o Windows Update ou o Microsoft Update.

    > [!IMPORTANT]
    > Se o software de cliente tiver sido instalado com um Objeto de Política de Grupo (GPO), tem de remover o Objeto de Política de Grupo (GPO) antes de poder remover o software de cliente, para impedir que o software seja reinstalado.

    Se o cliente não for desinstalado, leia [Resolução de problemas do Endpoint Protection](/intune/troubleshoot/troubleshoot-endpoint-protection-in-microsoft-intune) para obter mais ajuda.

### <a name="see-also"></a>Consulte também

[Tarefas de gestão comuns de PCs Windows com o cliente de software do Intune](common-windows-pc-management-tasks-with-the-microsoft-intune-computer-client.md)


<!--HONumber=Nov16_HO4-->


