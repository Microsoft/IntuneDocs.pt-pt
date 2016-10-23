---
title: "Restringir o acesso ao utilizar proteção contra ameaças de dispositivos | Microsoft Intune"
description: "Restrinja o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos."
keywords: 
author: karthikaraman
manager: angrobe
ms.date: 09/13/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: 725d9e40-e70c-461a-9413-72ff1b89a938
ms.reviewer: sandera
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 92422c2937c608d1aa6c9d11517fa08e4a8c7798
ms.openlocfilehash: a3c7e7cfef6223103fe0588f900f164635b042aa


---

# Restringir o acesso a recursos da empresa com base em riscos de aplicações, redes e dispositivos
Pode controlar o acesso a partir de dispositivos móveis a recursos empresariais, com base na avaliação de riscos realizada pelo Lookout, uma solução de proteção contra ameaças de dispositivos que está integrada com o Microsoft Intune. O risco baseia-se na telemetria que o serviço Lookout recolhe dos dispositivos relativamente a vulnerabilidades do sistema operativo (SO), aplicações maliciosas instaladas e perfis de rede maliciosos. Com base na avaliação de riscos que é comunicada pelo Lookout e ativada através de políticas de conformidade do Intune, pode configurar as políticas de acesso condicional no Intune e permitir ou bloquear dispositivos que foram identificados como sendo não compatíveis devido a ameaças detetadas nos mesmos.  Atualmente isto é suportado por dispositivos **Android** a executar a **versão 4.1 e posterior** e dispositivos a executar o **iOS 8 e posterior**. Estes dispositivos têm de estar inscritos no Microsoft Intune.  Para obter informações sobre plataformas e idiomas suportados pelo Lookout, consulte este [artigo](https://personal.support.lookout.com/hc/en-us/articles/114094140253).
## Que problema é que isto resolve?
As empresas e organizações precisam de proteger dados confidenciais de ameaças emergentes que incluem ameaças com base na rede, com base na aplicação e físicas, bem como vulnerabilidade do SO.

As empresas e organizações tomaram uma posição ativa na proteção dos PCs contra ataques maliciosos. Os dispositivos móveis são uma área emergente que muitas vezes fica desprotegida. Apesar de as plataformas móveis terem proteção incorporada do SO ao utilizar técnicas como o isolamento de aplicações e lojas de aplicações de clientes avaliadas, estas plataformas continuam a ser vulneráveis a ataques sofisticados. À medida que os dispositivos móveis são cada vez mais utilizados pelos funcionários para efetuarem tarefas e precisam de acesso a informações que podem ser confidenciais e úteis, estes dispositivos têm de ser protegidos de uma variedade de ataques sofisticados.

O Intune permite-lhe controlar o acesso aos dados e aos recursos da empresa com base na avaliação de riscos que as soluções de proteção contra ameaças de dispositivos fornecem, tal como o Lookout.

## Como é que o Intune e a proteção contra ameaças de dispositivos do Lookout ajudam a proteger os recursos da empresa?
A aplicação móvel do Lookout (Lookout for Work), em execução em dispositivos móveis, captura o sistema de ficheiros, a pilha de rede e a telemetria da aplicação e do dispositivo (onde disponível) e envia-os para o serviço de proteção em nuvem contra ameaças de dispositivos do Lookout para calcular o risco agregado de um dispositivo relativamente a ameaças contra dispositivos móveis. Também pode alterar a classificação do nível de risco das ameaças na consola do Lookout para atender às suas necessidades.  

A política de conformidade no Intune inclui uma nova regra para a proteção contra ameaças contra dispositivos móveis do Lookout que se baseia na avaliação do risco de ameaças contra dispositivos do Lookout. Quando esta regra está ativada, o Microsoft Intune avalia a conformidade do dispositivo com a política que ativou.

Se o dispositivo for identificado com sendo não compatível com a política de conformidade, o acesso a recursos como o Exchange Online e o SharePoint Online pode ser bloqueado utilizando políticas de acesso condicional. Quando o acesso é bloqueado, são fornecidas aos utilizadores finais instruções para resolver o problema e obter acesso aos recursos da empresa. Estas instruções são lançadas através da aplicação Lookout for Work.

## Cenários de exemplo
Seguem-se alguns cenários comuns:
### Controlar o acesso com base em ameaças de aplicações maliciosas:
Quando aplicações maliciosas como software maligno são detetadas no dispositivo, pode bloquear esses dispositivos de:
* Estabelecer ligação a e-mail empresarial antes de resolver a ameaça.
* Sincronizar ficheiros empresariais utilizando a aplicação OneDrive for Work.
* Aceder a aplicações empresariais cruciais.

**Acesso bloqueado quando são detetadas aplicações maliciosas:**
![diagrama a mostrar a política de acesso condicional a bloquear o acesso quando o dispositivo é identificado como sendo não compatível devido a aplicações maliciosas no dispositivo](../media/mtp/malicious-apps-blocked.png)

**O dispositivo está desbloqueado e consegue aceder aos recursos da empresa quando a ameaça é corrigida:**

![Diagrama a mostrar a política de acesso condicional a conceder acesso quando o dispositivo é identificado como sendo compatível após a remediação](../media/mtp/malicious-apps-unblocked.png)
### Controlar o acesso com base em ameaças à rede:
Detete ameaças à rede, tal como ataques Man-in-the-middle e restrinja o acesso a redes Wi-Fi com base no risco do dispositivo.

**Acesso à rede através de Wi-Fi bloqueado:**
![diagrama a mostrar o acesso condicional a bloquear o acesso Wi-Fi com base em ameaças à rede](../media/mtp/network-wifi-blocked.png)

**Acesso concedido na remediação:**

![Diagrama a mostrar o acesso condicional a permitir o acesso na remediação da ameaça](../media/mtp/network-wifi-unblocked.png)
### Controlar o acesso ao SharePoint Online com base em ameaças à rede:

Detete ameaças à sua rede, tal como ataques Man-in-the-middle e impeça a sincronização de ficheiros empresariais com base no risco do dispositivo.

**Acesso bloqueado ao SharePoint online com base na ameaça de rede detetada no dispositivo:**

![Diagrama a mostrar o acesso condicional a bloquear o acesso do dispositivo ao SharePoint Online com base na deteção da ameaça](../media/mtp/network-spo-blocked.png)


**Acesso concedido na remediação:**

![Diagrama a mostrar o acesso condicional a permitir o acesso após a ameaça da rede ser corrigida](../media/mtp/network-spo-unblocked.png)

## Passos seguintes
Seguem-se os principais passos que tem de efetuar para implementar esta solução:
1.  [Configurar a sua subscrição com o Lookout Mobile Threat Protection](set-up-your-subscription-with-lookout-mtp.md)
2.  [Ativar a ligação Lookout MTP no Intune](enable-lookout-mtp-connection-in-intune.md)
3.  [Configurar e implementar a aplicação Lookout for Work](configure-and-deploy-lookout-for-work-apps.md)
4.  [Configurar a política de compatibilidade](enable-device-threat-protection-rule-in-compliance-policy.md)
5.  [Resolução de Problemas da Integração do Lookout](http://docs.microsoft.com/en-us/intune/troubleshoot/troubleshooting-lookout-integration)



<!--HONumber=Oct16_HO2-->


