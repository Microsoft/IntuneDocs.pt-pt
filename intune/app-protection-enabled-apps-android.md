---
title: Aplicações Android com políticas de proteção de aplicações
titlesuffix: Microsoft Intune
description: Saiba o que esperar de uma aplicação Android com políticas de proteção.
keywords: ''
author: msmimart
ms.author: mimart
manager: dougeby
ms.date: 12/07/2016
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 16cef0b3e72c2e7815aada1c45c0e312b84931ab
ms.sourcegitcommit: dbea918d2c0c335b2251fea18d7341340eafd673
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31833022"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações 

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Saiba o que esperar de aplicações Android com políticas de proteção de aplicações. As políticas de proteção de aplicações só são aplicadas quando as aplicações são utilizadas no contexto de trabalho. Por exemplo, quando acede a uma aplicação com uma conta profissional ou quando acede a ficheiros armazenados na localização do OneDrive da sua empresa.
##  <a name="accessing-apps"></a>Aceder a aplicações

A aplicação Portal da Empresa é necessária para todas as aplicações em dispositivos Android que tenham políticas de proteção de aplicações.

Instale o Portal da Empresa em todos os dispositivos que não estiverem inscritos no Intune. Os utilizadores não precisam de iniciar sessão na aplicação Portal da Empresa para utilizar aplicações com políticas de proteção de aplicações.
A aplicação Portal da Empresa permite-lhe partilhar dados numa localização segura. Isto é necessário mesmo para dispositivos não inscritos.


##  <a name="using-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de várias identidades

As políticas de proteção de aplicações entram em vigor quando um utilizador tenta aceder a dados relacionados com o trabalho.  Poderá observar diferentes comportamentos se o utilizador aceder à aplicação para fins pessoais.

Algumas aplicações suportam várias identidades. Neste caso, o Intune só aplica as políticas de proteção de aplicações quando um utilizador aceder a dados de trabalho.  Por exemplo, pode ser pedido ao utilizador que introduza um PIN.  Na **aplicação Outlook**, é apresentada uma mensagem quando um utilizador inicia a aplicação. Na **aplicação OneDrive**, é apresentada uma mensagem quando um utilizador introduz a sua conta profissional.  No Microsoft **Word**, **PowerPoint** e **Excel**, é apresentada uma mensagem quando um utilizador acede a documentos do OneDrive da empresa.
##  <a name="managing-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo

O Intune suporta a implementação de políticas de proteção de aplicações numa conta de utilizador por dispositivo.

* Consoante a aplicação que estiver a utilizar, o segundo utilizador poderá ou não estar bloqueado no dispositivo. No entanto, em todos os casos, apenas o primeiro utilizador que obtém as políticas de proteção de aplicações é afetado pela política.

  * O **Microsoft Word**, o **Excel** e o **PowerPoint** não impedirão o acesso a uma conta de utilizador adicional. No entanto, a conta de utilizador não será afetada pelas políticas de proteção de aplicações.

  * Nas **aplicações OneDrive e Outlook**, só pode utilizar uma conta profissional.  Não é permitido adicionar várias contas profissionais nestas aplicações.  No entanto, pode remover um utilizador de um dispositivo e, em seguida, adicionar um utilizador diferente ao dispositivo.


* Um dispositivo pode ter múltiplas contas de utilizador existentes antes de implementar a política de proteção de aplicações. Neste caso, a primeira conta em que as políticas de proteção de aplicações forem implementadas será gerida pelas políticas de proteção de aplicações do Intune.


Leia o seguinte cenário de exemplo para saber como o Intune lida com múltiplas contas de utilizador.

O Utilizador A trabalha para duas empresas: a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de proteção de aplicações. A **Empresa X** implementa políticas de proteção de aplicações **antes da** **Empresa Y**. A conta associada à **Empresa X** obterá a política de proteção de aplicações, mas a conta associada à Empresa Y não. Para que a conta de utilizador da Empresa Y seja gerida pelas políticas de proteção de aplicações, o Utilizador A tem de remover a conta de utilizador da Empresa X.
### <a name="adding-a-second-account"></a>Adicionar uma segunda conta
####  <a name="android"></a>Android
Poderá ser-lhe pedido que remova a conta existente e adicione uma nova.  Para remover a conta existente, aceda a **Definições &gt;Geral &gt;Gestor de Aplicações &gt;Portal da Empresa. Em seguida, selecione "Limpar Dados"**.

![Captura de ecrã da mensagem de erro e instruções para remover a conta](./media/android-switch-user.png)

##  <a name="viewing-media-files-with-the-azure-information-protection-app-previously-known-as-rights-management-sharing-app"></a>Visualização de ficheiros de multimédia com a aplicação do Azure Information Protection (anteriormente conhecida como aplicação de partilha de Gestão de Direitos)
Para ver ficheiros AV, PDF e de imagem da empresa em dispositivos Android, utilize a [aplicação do Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer).

Transfira esta aplicação a partir da loja Google Play.  

São suportados os seguintes tipos de ficheiro:

* **Áudio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (AAC+ melhorado), AAC ELD (AAC de atraso lento melhorado), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE.
* **Vídeo:** H.263, H.264 AVC, MPEG-4 SP, VP8.
* **Imagem:** jpg, pjpg, png, ppng, bmp, pbmp, gif, pgif, jpeg, pjpeg.
* **:** PDF, PPDF

------------

|                                                                                 <strong>pfile</strong>                                                                                 |                                                                      <strong>text</strong>                                                                      |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| O formato Pfile é um formato de "wrapper" genérico para ficheiros protegidos. Reúne os conteúdos encriptados e as licenças do Azure Information Protection. Pode servir para proteger qualquer tipo de ficheiro. | Os ficheiros de texto, incluindo XML, CSV, etc. podem ser abertos para visualização na aplicação, mesmo que estejam protegidos. Tipos de ficheiro: txt, ptxt, csv, pcsv, log, plog, xml, pxml. |

---------------
## <a name="next-steps"></a>Passos seguintes
[O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>Consulte também
[Criar e implementar políticas de proteção de aplicações com o Microsoft Intune](app-protection-policies.md)
