---
title: Utilizar dispositivos geridos para trabalhar | Documentos da Microsoft
description: Compreenda o que significa inscrever o seu dispositivo para gestão com o Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 04/19/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 523caa6b-d792-4bb6-bddb-24b2479932d8
searchScope:
- User help
ROBOTS: ''
ms.reviewer: esmich
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2f698f03ed3c7523ef1d768d2a1361d6d1a55008
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883876"
---
# <a name="enroll-device-for-access-to-work-or-school-resources"></a>Registrar o dispositivo para acesso a recursos corporativos ou de estudante
Para registrar seu dispositivo e obter acesso a email e aplicativos, você precisará instalar o aplicativo Portal da Empresa do Intune ou Microsoft Intune aplicativo. Quando você se registra, as políticas básicas de gerenciamento que sua organização configurou, como senha, PIN e criptografia, são aplicadas ao seu dispositivo. Depois que as configurações do dispositivo atenderem a todos os requisitos da sua organização, você poderá acessar com segurança suas informações de trabalho de praticamente qualquer lugar.  

Os aplicativos Portal da Empresa e Microsoft Intune mantêm seu dispositivo registrado seguro, garantindo que as configurações do dispositivo correspondam às políticas da organização. 

O aplicativo Portal da Empresa também:  
* Mantém suas informações pessoais e de trabalho separadas.  
* Torna fácil localizar e instalar aplicativos relevantes de trabalho e escolares.   

## <a name="get-the-apps"></a>Obter os aplicativos
Para obter Portal da Empresa:

- Instale o aplicativo Portal da Empresa da loja de aplicativos específica da plataforma. Em alguns casos, sua organização instalará o aplicativo Portal da Empresa para você.  
- Acesse o [site Portal da empresa](https://go.microsoft.com/fwlink/?linkid=2010980) para acessar o aplicativo em um navegador.  

Se for necessário usar o aplicativo Microsoft Intune, sua organização irá instalá-lo para você.  


## <a name="what-information-can-my-company-see-when-i-enroll"></a>Quais informações minha empresa pode ver quando eu me registro?
Depois que o dispositivo for registrado, as pessoas de suporte da sua organização poderão ver apenas as informações relevantes para o trabalho. Eles não podem ver suas informações pessoais. Se você estiver registrando um dispositivo pessoal para uso no trabalho, [saiba exatamente o que pode ou não ser visto](what-info-can-your-company-see-when-you-enroll-your-device-in-intune.md).  


## <a name="whats-the-difference-between-the-apps-and-the-website"></a>Qual é a diferença entre os aplicativos e o site?
O aplicativo Portal da Empresa está disponível para dispositivos Windows 10, iOS, macOS e Android. Ele se integra perfeitamente à respectiva plataforma do dispositivo. A versão do site pode ser acessada de qualquer dispositivo e oferece a mesma experiência universal, independentemente do dispositivo que você estiver usando. 

O aplicativo Microsoft Intune é para dispositivos Android de propriedade corporativa.  

## <a name="what-kind-of-devices-can-you-enroll-with-company-portal"></a>Que tipo de dispositivos você pode registrar com Portal da Empresa?
- Dispositivos Apple com iOS (como iPhone e iPad) e macOS (como MacBook e iMac)
- Dispositivos Android
- Dispositivos Windows
  - Windows 10 Mobile
  - Computadores com o Windows 10
  - Windows Phone 8.1
  - Windows 8.1

## <a name="what-kind-of-devices-can-you-enroll-with-the-microsoft-intune-app"></a>Que tipo de dispositivos você pode registrar com o aplicativo Microsoft Intune?  
Você pode registrar dispositivos Android de propriedade corporativa que sua organização configurou para usar com o aplicativo. O aplicativo dá suporte ao Android 6,0 e posterior. 

## <a name="can-you-remove-a-computer-or-device-from-the-company-portal"></a>Pode remover um computador ou dispositivo do Portal da Empresa?
Sim, pode remover ou repor um computador ou dispositivo a partir do Portal da Empresa. Existe uma diferença entre **remover** e **repor**.

Quando você remove um computador ou dispositivo da Portal da Empresa, você está cancelando o registro do dispositivo do Intune. Ao anular a inscrição, deixa de poder aceder ao Portal da Empresa a partir desse dispositivo, e alguns dados da empresa poderão ser removidos do mesmo. Para saber como remover seu dispositivo do Portal da Empresa, consulte os links a seguir:  

- [Anular a inscrição do dispositivo Android](unenroll-your-device-from-intune-android.md)
- [Anular a inscrição do seu dispositivo iOS](unenroll-your-device-from-intune-ios.md)
- [Anular a inscrição do seu dispositivo macOS](unenroll-your-device-from-intune-macos.md)
- [Anular a inscrição do dispositivo Windows](unenroll-your-device-from-intune-windows.md)

Quando você redefine um computador ou dispositivo, o Portal da Empresa tenta redefinir seu computador ou dispositivo de volta para as configurações padrão do fabricante. A redefinição do dispositivo remove todos os dados pessoais e da empresa do dispositivo. Se você perdeu seu dispositivo, você também pode redefini-lo remotamente do site Portal da Empresa.  

Para saber como redefinir seu dispositivo, consulte [redefinir seu dispositivo no site Portal da empresa](reset-erase-your-device-cpwebsite.md).  

## <a name="can-you-remove-a-computer-or-device-from-the-microsoft-intune-app"></a>Você pode remover um computador ou dispositivo do aplicativo Microsoft Intune?
Não, não há como remover um dispositivo de propriedade corporativa do aplicativo Microsoft Intune.  

## <a name="what-if-i-cant-see-my-device-in-the-company-portal-or-microsoft-intune-app"></a>E se eu não conseguir ver meu dispositivo no Portal da Empresa ou Microsoft Intune aplicativo?
Para que consiga ver um dispositivo, primeiro este tem de ser adicionado ao Portal da Empresa. Aceda ao Portal da Empresa recomendado pelo seu administrador e siga os passos relativos ao seu dispositivo. Também não verá dispositivos que são propriedade e são geridos pela sua empresa.

Se você estiver usando o aplicativo Microsoft Intune, verá apenas o dispositivo que está usando no momento. Outros dispositivos registrados não serão visíveis para você no aplicativo.  

## <a name="where-else-can-i-go-for-help"></a>Como posso obter ajuda adicional?  
Para solucionar problemas e perguntas comuns, confira estes documentos específicos da plataforma:  

- [Corrigir problemas comuns no seu dispositivo Android](check-compliance-on-your-device-android.md)  
- [Corrigir problemas comuns no seu dispositivo iOS](troubleshoot-your-device-ios.md)
- [Corrigir problemas comuns no seu dispositivo macOS](troubleshoot-your-device-macos.md)
- [Corrigir problemas comuns no seu dispositivo Windows](troubleshoot-your-device-windows.md)

Você também pode entrar em contato com o seu pessoal de suporte. O Portal da Empresa e o aplicativo Microsoft Intune oferecem páginas de ajuda e suporte que listam informações de contato e maneiras de relatar um problema. As informações de contato também estão disponíveis no [site Portal da empresa](https://go.microsoft.com/fwlink/?linkid=2010980)da sua organização.  

## <a name="next-steps"></a>Passos Seguintes  

Obtenha a ajuda começando com o registro, que é específico para a plataforma do dispositivo:  

- [Utilizar o dispositivo Android](using-your-android-device-with-intune.md)
- [Utilizar o seu dispositivo iOS](using-your-ios-device-with-intune.md)
- [Utilizar o seu dispositivo macOS](using-your-macos-device-with-intune.md)
- [Utilizar o dispositivo Windows](using-your-windows-device-with-intune.md)
- [Utilizar o site do Portal da Empresa](using-the-intune-company-portal-website.md)


