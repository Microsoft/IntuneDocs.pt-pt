---
# required metadata

title: Utilizar aplicações geridas no dispositivo | Microsoft Intune
description:
keywords:
author: Staciebarker
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 3232c5c1-cb9f-45ca-806f-7e74eeb3533e

# optional metadata

ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Utilizar aplicações geridas no dispositivo

As aplicações geridas são as aplicações que o seu administrador de TI pode configurar para ajudar a proteger os dados da empresa que pode aceder nessa aplicação. Ao aceder aos dados da empresa numa aplicação gerida no seu dispositivo iOS, poderá reparar que a aplicação funciona de forma ligeiramente diferente do que o que esperava. Por exemplo, poderá não conseguir copiar e colar dados protegidos da empresa ou poderá não conseguir guardar os dados em determinadas localizações.

As diferentes aplicações geridas também podem trabalhar em conjunto no seu dispositivo para que possa efetuar as tarefas diárias, mantendo os dados empresariais protegidos. Por exemplo, se abrir um ficheiro da empresa numa aplicação gerida e for necessária outra aplicação gerida para ver esse ficheiro, a aplicação gerida que lhe permite ver o ficheiro abre-se automaticamente. Se não estiver disponível uma aplicação necessária, determinadas ações, como abrir um documento ou aceder a uma ligação Web a partir de um documento gerido, poderão não estar disponíveis.

Ao aceder a dados da empresa numa aplicação gerida, verá uma mensagem como a que se apresenta abaixo, que lhe permite saber que a aplicação que está a abrir é gerida.

![managed-apps-message-ios](./media/managed-apps-message.png)

### Como obtenho aplicações geridas?
Obtém aplicações geridas de duas formas diferentes:

-   Quando o dispositivo está inscrito no Microsoft Intune, pode instalar a aplicação a partir da sua aplicação do Portal da Empresa ou do Web site do Portal da Empresa, ou o seu administrador de TI poderá instalá-la no seu dispositivo. Para informações sobre a inscrição, consulte [Inscrever o seu dispositivo iOS no Intune](enroll-your-device-in-intune-ios.md) ou [Inscrever o seu dispositivo Mac OS X no Intune](enroll-your-device-in-intune-mac-os-x.md).

-   Instala uma aplicação da App Store e, em seguida, inicia sessão com a sua conta de utilizador empresarial gerida pelo Intune.

### O que o meu administrador de TI pode gerir na minha aplicação?
Aqui estão alguns exemplos das opções que o seu administrador de TI pode gerir numa aplicação e que podem afetar as suas interações com os dados da empresa no seu dispositivo:

-   Acesso a Web sites específicos

-   Transferências de dados entre aplicações

-   Guardar ficheiros

-   Operações de copiar e colar

-   Requisitos de acesso do PIN

-   Início de sessão com as credenciais da empresa

-   Capacidade de cópia de segurança para a nuvem

-   Capacidade para tirar capturas de ecrã

-   Requisitos de encriptação de dados

Algumas aplicações comuns que o seu departamento de TI poderá gerir são:

-   Permitir browser gerido

-   Visualizador de imagem gerido

-   Visualizador de PDF gerido

-   Leitor de AV gerido

-   Microsoft Word, Excel, PowerPoint

Contacte o seu administrador de TI para obter mais informações sobre as aplicações geridas no seu dispositivo.

### Consulte também
[Using your iOS or Mac OS X device with Intune](using-your-ios-or-mac-os-x-device-with-intune.md)

<!--HONumber=May16_HO2-->


