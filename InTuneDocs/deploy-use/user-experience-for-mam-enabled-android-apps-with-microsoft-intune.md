---
title: "Aplicações Android com políticas de MAM | Microsoft Intune"
description: "Este tópico descreve o que esperar quando a sua aplicação é gerida por políticas de gestão de aplicações móveis."
keywords: 
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.date: 10/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 53c8e2ad-f627-425b-9adc-39ca69dbb460
ms.reviewer: andcerat
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 87e37cd8334ddb9331c0662b691545cd0ab0553a
ms.openlocfilehash: 945c9f48846fc37358c44b83990feed1f3694966


---

# <a name="what-to-expect-when-your-android-app-is-managed-by-mam-policies"></a>O que esperar quando a sua aplicação Android é gerida por políticas de MAM
Este tópico descreve a experiência do utilizador para aplicações com políticas de MAM (gestão de aplicações móveis). As políticas de MAM são aplicadas apenas quando as aplicações são utilizadas num contexto de trabalho: por exemplo, quando o utilizador está a aceder a aplicações com a sua conta profissional ou aceder a ficheiros armazenados na localização empresarial do OneDrive para Empresas.
##  <a name="access-apps"></a>Acesso às aplicações

A aplicação Portal da Empresa é obrigatória para todas as aplicações associadas a políticas de MAM em dispositivos Android.

Para dispositivos que não estão inscritos no Intune, a aplicação Portal da Empresa tem de estar instalada no dispositivo. No entanto, o utilizador não tem de utilizar ou iniciar sessão na aplicação Portal da Empresa para poder utilizar aplicações geridas por políticas de MAM.

A aplicação Portal da Empresa é uma forma de o Intune partilhar dados numa localização segura. Por conseguinte, a aplicação Portal da Empresa é um requisito para todas as aplicações que estão associadas a políticas de MAM, mesmo se o dispositivo não estiver inscrito no Intune.


##  <a name="use-apps-with-multi-identity-support"></a>Utilizar aplicações com suporte de identidades múltiplas

As políticas de MAM só são aplicadas no contexto profissional. Por conseguinte, a aplicação pode comportar-se de forma diferente consoante se o contexto é profissional ou pessoal.

Por exemplo, o utilizador obtém um pedido de PIN ao aceder a dados de trabalho. Para a **aplicação Outlook**, é pedido ao utilizador um PIN ao iniciar a aplicação. Para a **aplicação OneDrive**, é pedido ao utilizador o pin quando escreve na conta profissional. Para o Microsoft **Word**, **PowerPoint** e **Excel**, é pedido o pin ao utilizador quando acede a documentos armazenados na localização empresarial do OneDrive para Empresas.

##  <a name="manage-user-accounts-on-the-device"></a>Gerir contas de utilizador no dispositivo

O Intune só suporta a implementação de políticas de MAM apenas numa conta de utilizador por dispositivo.

* Consoante a aplicação que estiver a utilizar, o segundo utilizador poderá estar bloqueado no dispositivo. No entanto, em todos os casos, apenas o primeiro utilizador que obtém as políticas de MAM é afetado pela política.

  * O **Microsoft Word**, **Excel** e **PowerPoint** não bloqueiam uma segunda conta de utilizador, mas a segunda conta de utilizador não é afetada pelas políticas de MAM.

  * Nas **aplicações OneDrive** e **Outlook**, só pode utilizar uma conta profissional.  Não pode adicionar várias contas profissionais para estas aplicações.  Pode, contudo, remover um utilizador e adicionar um utilizador diferente no dispositivo.


* Se um dispositivo tiver várias contas de utilizador existentes antes de as políticas de MAM serem implementadas, a conta em que as políticas de MAM são implementadas em primeiro lugar é gerida pelas políticas de MAM do Intune.


Leia o seguinte cenário de exemplo para obter uma compreensão mais aprofundada de como são tratadas as várias contas de utilizador.

O utilizador A trabalha para duas empresas — a **Empresa X** e a **Empresa Y**. O utilizador A tem uma conta profissional para cada empresa e ambas utilizam o Intune para implementar políticas de MAM. A **Empresa X** implementa políticas de MAM **antes da** **Empresa Y**. A conta que está associada à **Empresa X** obtém a política de MAM, mas a conta que está associada à Empresa Y não. Se pretender que a conta de utilizador que está associada à Empresa Y seja gerida pelas políticas de MAM, tem de remover a conta de utilizador que está associada à Empresa X.
### <a name="add-a-second-account"></a>Adicionar uma segunda conta
####  <a name="android"></a>Android
Se estiver a utilizar um dispositivo Android, poderá ver uma mensagem a informá-lo de que essa ação não é permitida, com instruções sobre como remover a conta existente e adicionar uma nova.  Para remover a conta existente, aceda a **Definições &gt;Geral &gt; Gestor de Aplicações &gt;Portal da Empresa.** Em seguida, escolha **Limpar Dados**.

![Captura de ecrã da mensagem de erro e instruções para remover a conta](../media/AppManagement/Android_SwitchUser.png)

##  <a name="view-media-files-with-the-azure-information-protection-app"></a>Ver ficheiros de multimédia com a aplicação Azure Information Protection
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

## <a name="next-steps"></a>Próximos passos
[O que esperar quando a sua aplicação iOS é gerida por políticas de MAM](user-experience-for-mam-enabled-ios-apps-with-microsoft-intune.md)

### <a name="see-also"></a>Consulte também
[Criar e implementar políticas de gestão de aplicações móveis com o Microsoft Intune](create-and-deploy-mobile-app-management-policies-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->

