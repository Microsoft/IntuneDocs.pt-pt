---
title: "O que acontece se instalar a aplicação do Portal da Empresa e inscrever o seu dispositivo Windows no Intune? | Microsoft Intune"
description: 
keywords: 
author: Staciebarker
manager: angrobe
ms.date: 7/8/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d65e3452-5bbf-4d26-a06e-401ddcc47f39
ROBOTS: noindex,nofollow
ms.reviewer: priyar
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 618e2abda642c3b9b2e813824dfd4235c9309faa
ms.openlocfilehash: 8b6e9b1bbf2d870b57dfcd7cdefefa2550d07d14


---


# O que acontece se instalar a aplicação do Portal da Empresa e inscrever o seu dispositivo Windows no Intune?

Quando instala a aplicação do Portal da Empresa e, em seguida, a utiliza para inscrever um dispositivo Windows ou Windows Phone, o seu administrador de TI pode gerir o seu dispositivo para manter aos dados da empresa ou da escola protegidos, conforme é descrito abaixo relativamente a dispositivos anteriores ao Windows 10. Para obter informações sobre os dispositivos Windows 10, veja [esta página](what-happens-if-you-install-the-company-portal-app-and-enroll-your-device-in-intune-windows10.md).

## O que acontece a todos os dispositivos Windows após a inscrição
Quando inscreve o seu dispositivo Windows ou Windows Phone no Intune, pode:

-   Aceder à rede da empresa e ao seu e-mail e ficheiros de trabalho

-   Obter aplicações empresariais a partir do Web site do Portal da Empresa (no Windows 7 e Vista, só pode obter aplicações empresariais a partir do Web site do Portal da Empresa)

-   Configurar automaticamente a conta de e-mail da empresa ou escola

-   Repor o telemóvel para as definições de fábrica em caso de perda ou roubo

Quando inscreve o seu dispositivo, dá permissão ao seu administrador de TI para fazer coisas como:

-   Repor as predefinições do fabricante do seu dispositivo. Esta ação é útil em caso de perda ou roubo do dispositivo.

-   Remover todos os dados relacionados com a empresa e todas as aplicações empresariais que foram instaladas. Os dados e definições pessoais não são removidos.

-   O seu administrador de TI pode fazer um inventário de todo o software instalado no computador, incluindo software que o utilizador tenha instalado pessoalmente.

-   Exigir que tenha uma palavra-passe ou PIN no dispositivo, o que pode impedi-lo de aceder ao mesmo ou repor as predefinições do fabricante do seu dispositivo, o que pode incluir a eliminação de dados, se ocorrerem demasiadas tentativas de introdução incorreta de palavra-passe.

-   Exigir que todos os dados no dispositivo sejam encriptados, o que ajuda a proteger os dados se o dispositivo se perder ou for roubado.

-   O seu administrador de TI pode exigir que aceite os termos e condições.

-   O seu administrador de TI pode impor políticas no computador. Por exemplo, poderá ser necessário definir uma palavra-passe ou PIN no computador, o que pode impedi-lo de aceder ao mesmo, ou eliminar todos os dados do disco rígido do seu computador, se ocorrerem demasiadas tentativas de introdução incorreta de palavra-passe.

-   Desativar o cartão SD.

## O que acontece a todos os PCs Windows após a inscrição

-  Será instalado software no seu computador para permitir ao administrador de TI geri-lo e a si aceder a recursos da empresa, como aplicações e informações de suporte. O administrador de TI pode atualizar automaticamente este software.

-  O Endpoint Protection do Intune pode ser instalado no seu computador. É um software que verifica a existência de vírus e software maligno.

-  O seu administrador de TI pode fazer um inventário de todo o software instalado no computador, incluindo software que o utilizador tenha instalado pessoalmente.

-  Poderá ter de aceitar os termos e condições.

-  O seu administrador de TI pode recolher ou eliminar dados do disco rígido do seu computador. O seu administrador de TI também pode eliminar o seu disco rígido inteiro.

-  O seu administrador de TI pode instalar aplicações e atualizações no seu computador.

-  O seu administrador de TI pode impor políticas no computador. Por exemplo, poderá ser necessário definir uma palavra-passe ou PIN no computador, o que pode impedi-lo de aceder ao mesmo, ou eliminar todos os dados do disco rígido do seu computador, se ocorrerem demasiadas tentativas de introdução incorreta de palavra-passe.


## O que acontece a cada oito horas após a inscrição de dispositivos
A cada oito horas aproximadamente, os dispositivos inscritos irão:

-   Transferir atualizações de políticas ou aplicações disponibilizadas pelo seu administrador de TI.

-   Enviar atualizações de inventário de hardware.

-   Enviar atualizações de inventário de aplicações da empresa.

Para obter os passos para a inscrição, veja [Enroll your Windows device in Intune (Inscrever o seu dispositivo Windows no Intune)](enroll-your-device-in-intune-windows.md). Para saber o que o seu administrador de TI pode ver no seu dispositivo, consulte [O que pode o administrador de TI ver se inscrever o meu dispositivo no Intune?](what-can-your-it-administrator-see-when-you-enroll-your-device-in-intune-windows.md).

Se tiver dúvidas, contacte o administrador de TI. Para encontrar as informações de contacto dele, verifique o [Web site do Portal da Empresa](http://portal.manage.microsoft.com).

### Consulte também
[Utilizar o dispositivo Windows com o Intune](using-your-windows-device-with-intune.md)



<!--HONumber=Jul16_HO4-->


