---
# required metadata

title: Escolher como gerir dispositivos com o Microsoft Intune | Microsoft Intune
description:
keywords:
author: jeffgilb
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 770aad50-fd7a-4cf1-a793-f95fe47fc3f8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Escolher como gerir dispositivos
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] permite gerir uma vasta gama de dispositivos ao *inscrevê-los* no serviço. Os utilizadores podem utilizar um *portal da empresa* para efetuar várias operações, como inscrever os respetivos dispositivos, procurar e instalar aplicações, assegurar que o dispositivo está em conformidade com as políticas da empresa e contactar o respetivo suporte de TI.

## Formas de gerir dispositivos móveis
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] pode gerir as seguintes plataformas de dispositivos:

- Apple iOS 7.1 e posterior
- Google Android 4.0 e posterior (incluindo o Samsung KNOX)
- Windows Phone 8.0 e posterior
- Windows RT e Windows 8.1 RT
- PCs com o Windows 8.1 e posterior
- Mac OS X 10.9 e posterior

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Sugestão</h5>
  <p>Se tiver inscrito anteriormente dispositivos com uma versão anterior do iOS que a versão suportada acima, estes permanecerão inscritos. No entanto, consulte a documentação para cada [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] para assegurar que a versão do iOS é suportada pela funcionalidade.</p>
</div>

[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] pode gerir dispositivos de utilizadores, conhecidos popularmente como "bring your own device" (BYOD). Também pode gerir dispositivos pertencentes à empresa, incluindo cenários em que a empresa fornece uma lista de dispositivos que os utilizadores poderão escolher, conhecido como "choose your own device" (CYOD).

### Inscrever dispositivos para gestão
Para sistemas operativos de dispositivos móveis, incluindo iOS, Android e Windows Phone, tem sempre de inscrever os dispositivos. No entanto, a forma como inscreve os dispositivos depende das necessidades da sua organização:

|Tipo de inscrição|BYOD|CYOD|Dispositivo partilhado com conta de gestor|Dispositivo partilhado sem uma conta de utilizador|
|-------------------|--------|--------|--------------------------------------|----------------------------------------|
|**Descrição**|Dispositivo pessoal inscrito através do Microsoft Intune|Dispositivo que é propriedade da empresa para um único utilizador|Dispositivo que é propriedade da empresa gerido através de uma conta de gestor partilhada por vários utilizadores|Dispositivo sem utilizadores que é propriedade da empresa utilizado por vários utilizadores.|
|**Utilizador do dispositivo**|Proprietário|Utilizador atribuído|Nenhuma conta de utilizador específica|Nenhum utilizador específico|
|**Quem inscreve?**|Proprietário|Admistrador|Gestor de Dispositivos|Qualquer pessoa|
|**Quem cancela a inscrição?**|Proprietário ou administrador|Admistrador|Admistrador|Admistrador|
|**Quem pode redefinir?**|Proprietário ou administrador|Admistrador|Admistrador|Admistrador|

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Sugestão</h5>
  <p>Consulte [Capacidades de gestão de dispositivos móveis](mobile-device-management-capabilities-in-microsoft-intune.md) para obter uma lista completa das capacidades fornecidas pela inscrição de dispositivos.</p>
</div>



## Formas de gerir PCs Windows
[!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] pode gerir o Windows Vista e PCs Windows posteriores utilizando o cliente do computador do Intune. No entanto, para PCs Windows, pode optar entre inscrevê-los ou instalar o software de cliente do PC [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)] que disponibiliza algumas capacidades não disponíveis quando inscreve dispositivos. Na maioria dos cenários, irá inscrever o dispositivo Windows com o Intune, o que fornece um conjunto maior de capacidades que o computador cliente.

Considere utilizar o cliente do computador Intune quando pretender:
<ul>
<li>Utilizar qualquer uma das capacidades ativadas para o cliente do computador do Microsoft Intune para gerir os seus PCs Windows.</li>
<li>Gerir um PC Windows com um sistema operativo não suportado para inscrição.</li>
</ul>

<div class="alert alert-tip">
  <h5><span class="icon-tip"></span> Sugestão</h5>
  <p>Consulte [Capacidades de gestão de PCs Windows](windows-pc-management-capabilities-in-microsoft-intune.md) para obter uma lista completa das capacidades fornecidas pela instalação do cliente do computador do Intune em PCs Windows suportados.</p>
</div>

## Gestão do Exchange ActiveSync
Também pode gerir dispositivos através do Exchange ActiveSync. Isto requer a instalação do Conector No Local ou a utilização do Conector de Serviços incorporado para ligar ao seu Exchange Server.

Para saber mais sobre os requisitos de hardware e software para instalar o Conector No Local, consulte [Requisitos do Conector No Local](/Intune/network-infrastructure-requirements-for-microsoft-intune.md).

Para saber mais sobre como utilizar o Conector No Local ou o Conector de Serviços com o Exchange, consulte [Gestão de dispositivos móveis com o Exchange ActiveSync e o Microsoft Intune](/Intune/get-started/mobile-device-management-with-exchange-activesync-and-microsoft-intune.md).



## Passos seguintes
Agora que já descobriu algumas das capacidades que pode utilizar quando inscrever os seus dispositivos com o [!INCLUDE[wit_nextref](../includes/wit_nextref_md.md)], terá de [preparar-se para inscrever os seus dispositivos](/Intune/get-started/get-ready-to-enroll-devices-in-microsoft-intune.md). Após ter inscrito os seus dispositivos, pode tirar partido de todas as capacidades que leu neste tópico. <!--lindavr: There's a logical flaw in our "get to know/get started" content. You can take the path in this topic or you can take the path in the What to know before your get started topic. And they don't cover the same ground. -->


<!--HONumber=May16_HO1-->

