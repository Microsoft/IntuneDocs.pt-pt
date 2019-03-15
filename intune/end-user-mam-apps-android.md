---
title: Aplicações Android com políticas de proteção de aplicações
description: Este tópico descreve o que esperar quando a sua aplicação é gerida por políticas de proteção de aplicações.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 02/15/2018
ms.topic: conceptual
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: tisilver
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6122016f660e01b19862145d1a358fa154bf18f
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57396952"
---
# <a name="what-to-expect-when-your-android-app-is-managed-by-app-protection-policies"></a>O que esperar quando a aplicação Android é gerida por políticas de proteção de aplicações

[!INCLUDE [both-portals](./includes/note-for-both-portals.md)]

Este artigo descreve a experiência do utilizador em aplicações com políticas de proteção de aplicações. As políticas de proteção de aplicações são aplicadas apenas quando as aplicações são utilizadas num contexto de trabalho: por exemplo, quando o utilizador está a aceder a aplicações com uma conta profissional ou a aceder a ficheiros armazenados numa localização do OneDrive para Empresas.

##  <a name="access-apps"></a>Acesso às aplicações

A aplicação Portal da Empresa é exigida para todas as aplicações associadas a políticas de proteção de aplicações em dispositivos Android.

Para dispositivos que não estão inscritos no Intune, a aplicação Portal da Empresa tem de estar instalada no dispositivo. No entanto, o utilizador não tem de utilizar ou iniciar sessão na aplicação Portal da Empresa para poder utilizar aplicações geridas por políticas de proteção de aplicações.

A aplicação Portal da Empresa é uma forma de o Intune partilhar dados numa localização segura. Por conseguinte, a aplicação Portal da Empresa é um requisito para todas as aplicações que estão associadas a políticas de proteção de aplicações, mesmo se o dispositivo não estiver inscrito no Intune.


##  <a name="use-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de identidades múltiplas

As políticas de proteção de aplicações só são aplicadas no contexto profissional. Por conseguinte, a aplicação pode comportar-se de forma diferente consoante se o contexto é profissional ou pessoal.

Por exemplo, o utilizador obtém um pedido de PIN ao aceder a dados de trabalho. Para a **aplicação Outlook**, é pedido ao utilizador um PIN ao iniciar a aplicação. Para a **aplicação OneDrive**, é pedido ao utilizador o pin quando escreve na conta profissional. Para o Microsoft **Word**, **PowerPoint** e **Excel**, é pedido o pin ao utilizador quando acede a documentos armazenados na localização empresarial do OneDrive para Empresas.

##  <a name="manage-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo

As aplicações de identidades múltiplas permitem aos utilizadores adicionar várias contas.  A aplicação Intune apenas suporta uma conta gerida.  A aplicação Intune não limita o número de contas não geridas.

Quando existe uma conta gerida numa aplicação:
*   Se um utilizador tentar adicionar uma segunda conta gerida, é-lhe pedido para selecionar a conta gerida a utilizar.  A outra conta é removida.
*   Se o administrador de TI adicionar uma política a uma segunda conta existente, é pedido ao utilizador que selecione a conta gerida a utilizar.  A outra conta é removida.

Leia o seguinte cenário de exemplo para obter uma compreensão mais aprofundada de como são tratadas as várias contas de utilizador.

O utilizador A trabalha para duas empresas — a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de proteção de aplicações. A **Empresa X** implementa políticas de proteção de aplicações **antes da** **Empresa Y**. A conta que está associada à **Empresa X** obtém a política de proteção de aplicações, mas a conta que está associada à Empresa Y não. Se pretender que a conta de utilizador que está associada à Empresa Y seja gerida pelas políticas de proteção de aplicações, terá de remover a conta de utilizador que está associada à Empresa X e adicionar a conta que está associada à Empresa Y.
### <a name="add-a-second-account"></a>Adicionar uma segunda conta
####  <a name="android"></a>Android
Se estiver a utilizar um dispositivo Android, poderá ver uma mensagem a informá-lo de que essa ação não é permitida, com instruções sobre como remover a conta existente e adicionar uma nova.  Para remover a conta existente, aceda a **Definições &gt;Geral &gt; Gestor de Aplicações &gt;Portal da Empresa.** Em seguida, escolha **Limpar Dados**.

![Captura de ecrã da mensagem de erro e instruções para remover a conta](./media/Android_SwitchUser.png)

##  <a name="view-media-files-with-the-azure-information-protection-app"></a>Ver ficheiros de multimédia com a aplicação Azure Information Protection
Para ver ficheiros AV, PDF e de imagem da empresa em dispositivos Android, utilize a [aplicação Azure Information Protection](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) (anteriormente conhecida como aplicação de partilha Rights Management).

Transfira esta aplicação a partir da Google Play store.  

São suportados os seguintes tipos de ficheiro:

* **Áudio:** AAC LC, HE-AACv1 (AAC + melhorado), HE-AACv2 (AAC + melhorado), AAC ELD (AAC de atraso), AMR-NB, AMR-WB, FLAC, MP3, MIDI, Ogg Vorbis, PCM/WAVE
* **Vídeo:** H.263, H.264 AVC, MPEG-4 SP, VP8
* **Imagem:** .jpg, .pjpg, .png, .ppng, .bmp, .pbmp, .gif, .pgif, .jpeg, .pjpeg
* **Documentos:** PDF, PPDF


|**pfile**|
|----|
|Pfile é um formato de "encapsulamento" genérico para ficheiros protegidos que encapsula o conteúdo encriptado e as licenças do Azure Information Protection. Pode servir para proteger qualquer tipo de ficheiro.|

## <a name="next-steps"></a>Passos Seguintes
[O que esperar quando a sua aplicação iOS é gerida por políticas de proteção de aplicações](end-user-mam-apps-ios.md)
