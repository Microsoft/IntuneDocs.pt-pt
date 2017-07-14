---
title: "Aplicações Android com políticas de proteção de aplicações"
description: "Este tópico descreve o que esperar quando a sua aplicação é gerida por políticas de proteção de aplicações."
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: 030e17a9f28a9476c82e89d4dd26151a2d3cb953
ms.sourcegitcommit: f100c943a635f5a08254ba7cf30f1aaebb7e810e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/13/2017
---
# O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações
<a id="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies" class="xliff"></a>

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Este tópico descreve a experiência do utilizador em aplicações com políticas de proteção. As políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas num contexto de trabalho: por exemplo, quando o utilizador está a aceder a aplicações com uma conta profissional ou a aceder a ficheiros armazenados na localização empresarial do OneDrive para Empresas.
##  Acesso às aplicações
<a id="access-apps" class="xliff"></a>

A aplicação Portal da Empresa é exigida para todas as aplicações associadas a políticas de proteção de aplicações em dispositivos Android.

Para dispositivos que não estão inscritos no Intune, a aplicação Portal da Empresa tem de estar instalada no dispositivo. No entanto, o utilizador não tem de utilizar ou iniciar sessão na aplicação Portal da Empresa para poder utilizar aplicações geridas por políticas de proteção de aplicações.

A aplicação Portal da Empresa é uma forma de o Intune partilhar dados numa localização segura. Por conseguinte, a aplicação Portal da Empresa é um requisito para todas as aplicações que estão associadas a políticas de proteção de aplicações, mesmo se o dispositivo não estiver inscrito no Intune.


##  Utilizar aplicações com suporte de identidades múltiplas
<a id="use-apps-with-multi-identity-support" class="xliff"></a>

As políticas de proteção de aplicações só são aplicadas no contexto profissional. Por conseguinte, a aplicação pode comportar-se de forma diferente consoante se o contexto é profissional ou pessoal.

Por exemplo, o utilizador obtém um pedido de PIN ao aceder a dados de trabalho. Para a **aplicação Outlook**, é pedido ao utilizador um PIN ao iniciar a aplicação. Para a **aplicação OneDrive**, é pedido ao utilizador o pin quando escreve na conta profissional. Para o Microsoft **Word**, **PowerPoint** e **Excel**, é pedido o pin ao utilizador quando acede a documentos armazenados na localização empresarial do OneDrive para Empresas.

##  Gerir contas de utilizador no dispositivo
<a id="manage-user-accounts-on-the-device" class="xliff"></a>

O Intune suporta a implementação de políticas de proteção de aplicações apenas numa conta de utilizador por dispositivo.

* Consoante a aplicação que estiver a utilizar, o segundo utilizador poderá estar bloqueado no dispositivo. No entanto, em todos os casos, apenas o primeiro utilizador que obtém as políticas de proteção de aplicações é afetado pela política.

  * O **Microsoft Word**, **Excel** e **PowerPoint** não bloqueiam uma segunda conta de utilizador, mas a segunda conta de utilizador não é afetada pelas políticas de proteção de aplicações.

  * Nas **aplicações OneDrive** e **Outlook**, só pode utilizar uma conta profissional.  Não pode adicionar várias contas profissionais para estas aplicações.  Pode, contudo, remover um utilizador e adicionar um utilizador diferente no dispositivo.


* Se um dispositivo tiver várias contas de utilizador antes de as políticas de proteção de aplicações serem implementadas, a conta em que as políticas de proteção de aplicações são implementadas em primeiro lugar é gerida pelas políticas de proteção de aplicações do Intune.


Leia o seguinte cenário de exemplo para obter uma compreensão mais aprofundada de como são tratadas as várias contas de utilizador.

O utilizador A trabalha para duas empresas — a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de proteção de aplicações. A **Empresa X** implementa políticas de proteção de aplicações **antes da** **Empresa Y**. A conta que está associada à **Empresa X** obtém a política de proteção de aplicações, mas a conta que está associada à Empresa Y não. Se pretender que a conta de utilizador que está associada à Empresa Y seja gerida pelas políticas de proteção de aplicações, terá de remover a conta de utilizador que está associada à Empresa X.
### Adicionar uma segunda conta
<a id="add-a-second-account" class="xliff"></a>
####  Android
<a id="android" class="xliff"></a>
Se estiver a utilizar um dispositivo Android, poderá ver uma mensagem a informá-lo de que essa ação não é permitida, com instruções sobre como remover a conta existente e adicionar uma nova.  Para remover a conta existente, aceda a **Definições &gt;Geral &gt; Gestor de Aplicações &gt;Portal da Empresa.** Em seguida, escolha **Limpar Dados**.

![Captura de ecrã da mensagem de erro e instruções para remover a conta](./media/Android_SwitchUser.png)

##  Ver ficheiros de multimédia com a aplicação Azure Information Protection
<a id="view-media-files-with-the-azure-information-protection-app" class="xliff"></a>
Para ver ficheiros AV, PDF e de imagem da empresa em dispositivos Android, utilize a [aplicação Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (anteriormente conhecida como aplicação de partilha Rights Management).

Transfira esta aplicação a partir da Google Play store.  

São suportados os seguintes tipos de ficheiro:

* **Áudio:** AAC LC, HE-AACv1 (AAC+), HE-AACv2 (AAC+ melhorado), AAC ELD (AAC de atraso lento melhorado), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **Vídeo:** H.263, H.264 AVC, MPEG-4 SP, VP8
* **Imagem:** .jpg, .pjpg, .png, .ppng, .bmp, .pbmp, .gif, .pgif, .jpeg, .pjpeg
* **:** PDF, PPDF


|**pfile**|**text**|
|----|----|
|Pfile é um formato de "encapsulamento" genérico para ficheiros protegidos que encapsula o conteúdo encriptado e as licenças do Azure Information Protection. Pode servir para proteger qualquer tipo de ficheiro.|Os ficheiros de texto, incluindo XML, CSV, etc. podem ser abertos para visualização na aplicação, mesmo que estejam protegidos. Tipos de ficheiro: .txt, .ptxt, .csv, .pcsv, .log, .plog, .xml, .pxml.|

## Próximos passos
<a id="next-steps" class="xliff"></a>
[O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](end-user-mam-apps-ios.md)