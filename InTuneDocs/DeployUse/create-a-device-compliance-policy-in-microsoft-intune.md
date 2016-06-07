---
# required metadata

title: Criar uma política de conformidade de dispositivos no Microsoft Intune | Microsoft Intune
description:
keywords:
author: karthikaraman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 5336dac0-a2cc-4cd4-8511-67e4f95bd700

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Criar uma política de conformidade de dispositivos no Microsoft Intune
Este tópico descreve os passos que pode utilizar para criar uma política de conformidade que um dispositivo tem de seguir para ser considerado conforme.

##  Passo 1: Adicionar uma nova política
  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), escolha **Política** &gt; **Políticas de Conformidade** &gt; **Adicionar**

  ![Captura de ecrã da página de política de conformidade na consola de administração do Intune, que mostra a opção de adicionar no menu na parte superior da página](./media/intune-sa-3a-add-compliance-policy.png)

##  Passo 2: Configurar as definições
Na página **Criar Política**, ative as definições necessárias:
  -   As definições de segurança do sistema, como palavra-passe e encriptação
  -   As definições de estado de funcionamento do dispositivo, como se o dispositivo tem ou não jailbrake ou se é considerado como estando em bom estado de funcionamento pelo serviço de atestado de estado de funcionamento de dispositivos do Windows.
  -   Definições de propriedades do dispositivo, como a versão mínima do SO necessária ou a versão máxima do SO permitida.
![Captura de ecrã do separador Geral da página Criar Política ](./media/intune-sa-3b-create-policy.png)

##  Passo 3: Guardar a política
Quando terminar, escolha **Guardar Política**

Terá a opção de implementar a política logo após guardá-la ou pode optar por implementá-la mais tarde. A nova política é apresentada no nó **Políticas de Conformidade** da área de trabalho **Política**.

## Definições de política suportadas
A tabela seguinte lista as definições de política de conformidade e as plataformas em que são suportadas.

-------------
|Definição|iOS|Android|Windows|
|-----|----|-----|-----|
|Palavra-passe obrigatória para desbloquear os dispositivos móveis|iOS 6 e posterior|Android 4.0 e posterior <br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8 e posterior|
|Permitir palavras-passe simples|iOS 6 e posterior|Não suportado|Windows Phone 8 e posterior|
|Comprimento mínimo da palavra-passe|iOS 6 e posterior| Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior| Windows Phone 8 e posterior<br>Windows 8,1|
|Tipo obrigatório de palavra-passe|iOS 6 e posterior|Não disponível|Windows Phone 8 e posterior <br>Windows RT<br> Windows RT 8.1 <br>Windows 8,1|
|Número mínimo de conjuntos de carateres|iOS 6 e posterior|Não disponível|Windows Phone 8 e posterior <br>Windows RT<br> Windows RT 8.1 <br>Windows 8,1|
|Qualidade da palavra-passe|Não disponível|Android 4.0 e posterior <br>Samsung KNOX Standard 4.0 e posterior|Não disponível|
|Minutos de inatividade antes da palavra-passe ser exigida|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8 e posterior<br>Windows RT e Windows RT 8.1<br>Windows 8,1|
|Expiração da Palavra-passe (dias)|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8 e posterior<br>Windows RT e Windows RT 8.1<br>Windows 8,1|
|Memorizar histórico de palavras-passe|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8 e posterior<br>Windows RT e Windows RT 8.1<br>Windows 8,1|
|Impedir a reutilização de palavras-passe anteriores|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8 e posterior<br>Windows RT e Windows RT 8.1<br>Windows 8,1|
|Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo| Não disponível| Não disponível|Windows 10 Mobile|
|Encriptação obrigatória no dispositivo móvel|Não aplicável|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8 e posterior<br> Windows 8,1|
|Exigir que os dispositivos sejam comunicados como estando em bom estado de funcionamento| Não disponível| Não disponível|Windows <br>Windows 10 Mobile|
|O dispositivo não pode ter jailbreak nem root|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Não disponível|
|A conta de e-mail tem de ser gerida pelo Intune|iOS 6 e posterior|Não disponível| Não disponível|
|Selecionar o perfil de e-mail que deve ser gerido pelo Intune|iOS 6 e posterior|Não disponível| Não disponível|
|SO Mínimo obrigatório|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior| Windows Phone 8 e posterior<br>Windows 8,1|
|Versão máxima de SO permitida|iOS 6 e posterior|Android 4.0 e posterior<br>Samsung KNOX Standard 4.0 e posterior|Windows Phone 8 e posterior<br>Windows 8,1|

Selecione um dos seguintes passos para obter mais informações sobre as definições de conformidade suportadas em cada plataforma:
> [!div class="op_single_selector"]
- [Definições de política de conformidade para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Windows Phone ](windows-compliance-policy-settings-in-microsoft-intune.md)


## Passos seguintes
[Implementar e monitorizar políticas de conformidade](deploy-and-monitor-a-device-compliance-policy-in-microsoft-intune.md)

### Consulte também
[Introdução às políticas de conformidade de dispositivos](introduction-to-device-compliance-policies-in-microsoft-intune.md)


<!--HONumber=May16_HO2-->

