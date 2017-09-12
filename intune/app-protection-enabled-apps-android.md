---
title: "Aplicações Android com políticas de proteção de aplicações"
titlesuffix: Azure portal
description: "Este tópico descreve o que esperar quando a sua aplicação Android é gerida por políticas de proteção de aplicações.\""
keywords: 
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: a6816285-8e43-4dc8-bca0-e80ec5ef01e6
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: ac70c8ce3bbc8338339e7becb8b28d594bb2fbf6
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/09/2017
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações 

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Este tópico descreve a experiência do utilizador em aplicações com políticas de proteção. As políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas no contexto de trabalho, como aceder a aplicações com a conta profissional ou aceder a ficheiros armazenados na localização empresarial do OneDrive para Empresas.
##  <a name="accessing-apps"></a>Aceder a aplicações

A aplicação Portal da Empresa é exigida para todas as aplicações associadas a políticas de proteção de aplicações em dispositivos Android.

Para dispositivos não inscritos no Intune, a aplicação Portal da Empresa tem de estar instalada no dispositivo. No entanto, o utilizador não tem de utilizar ou iniciar sessão na aplicação Portal da Empresa para poder utilizar aplicações geridas por políticas de proteção de aplicações.
A aplicação Portal da Empresa é uma forma de o Intune partilhar dados numa localização segura, pelo que é um requisito mesmo que o dispositivo não esteja inscrito no Intune.


##  <a name="using-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de várias identidades

As políticas de proteção de aplicações são apenas aplicadas no contexto de trabalho ao utilizar a aplicação, pelo que poderá experimentar diferentes comportamentos da aplicação consoante o contexto: profissional ou pessoal.

Para aplicações que suportam várias identidades, o Intune apenas aplicará as políticas de proteção de aplicações se o utilizador final utilizar a aplicação no contexto de trabalho.  Por exemplo, o utilizador final irá obter um pedido de PIN ao aceder a dados de trabalho.  Para a **aplicação Outlook**, é pedido ao utilizador final um PIN ao iniciar a aplicação. Para a **aplicação OneDrive**, isto acontece quando o utilizador final introduz a conta profissional.  Para o Microsoft **Word**, **PowerPoint* e **Excel**, isto acontece quando o utilizador final acede a documentos armazenados na localização empresarial do OneDrive para Empresas.
##  <a name="managing-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo

O Intune só suporta a implementação de políticas de proteção de aplicações apenas numa conta de utilizador por dispositivo.

* Consoante a aplicação que estiver a utilizar, o segundo utilizador poderá ou não estar bloqueado no dispositivo. No entanto, em todos os casos, apenas o primeiro utilizador que obtém as políticas de proteção de aplicações é afetado pela política.

  * O **Microsoft Word**, **Excel** e **PowerPoint** não bloqueiam uma segunda conta de utilizador, mas a segunda conta de utilizador não é afetada pelas políticas de proteção de aplicações.

  * Nas **aplicações OneDrive e Outlook**, só pode utilizar uma conta profissional.  Não é permitido adicionar várias contas profissionais nestas aplicações.  Pode, contudo, remover um utilizador e adicionar um utilizador diferente no dispositivo.


* Se um dispositivo tiver várias contas de utilizador existentes antes de as políticas de proteção de aplicações serem implementadas, a conta em que as políticas de proteção de aplicações são implementadas em primeiro lugar será gerida pelas políticas de proteção de aplicações do Intune.


Leia o cenário de exemplo abaixo para obter uma compreensão mais aprofundada de como são tratadas as várias contas de utilizador.

O utilizador A trabalha para duas empresas - a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de proteção de aplicações. A **Empresa X** implementa políticas de proteção de aplicações **antes da** **Empresa Y**. A conta associada à **Empresa X** obterá a política de proteção de aplicações, mas a conta associada à Empresa Y não. Se pretender que a conta de utilizador associada à Empresa Y seja gerida pelas políticas de proteção de aplicações, terá de remover a conta de utilizador associada à Empresa X.
### <a name="adding-a-second-account"></a>Adicionar uma segunda conta
####  <a name="android"></a>Android
Se estiver a utilizar um dispositivo Android, poderá ver uma mensagem a informá-lo de que essa ação não é permitida, com instruções sobre como remover a conta existente e adicionar uma nova.  Para remover a conta existente, aceda a **Definições &gt;Geral &gt; Gestor de Aplicações &gt;Portal da Empresa e selecione "Limpar Dados"**.

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
|**pfile**|**text**|
|----|----|
|Pfile é um formato de "encapsulamento" genérico para ficheiros protegidos que encapsula o conteúdo encriptado e as licenças do Azure Information Protection e pode ser utilizado para proteger qualquer tipo de ficheiro.|Os ficheiros de texto, incluindo XML, CSV, etc. podem ser abertos para visualização na aplicação, mesmo que estejam protegidos. Tipos de ficheiro: txt, ptxt, csv, pcsv, log, plog, xml, pxml.|
---------------
## <a name="next-steps"></a>Passos seguintes
[O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](app-protection-enabled-apps-ios.md)

### <a name="see-also"></a>Veja também
[Criar e implementar políticas de proteção de aplicações com o Microsoft Intune](app-protection-policies.md)
