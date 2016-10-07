---
title: "Inscrever dispositivos iOS pertencentes à empresa | Microsoft Intune"
description: "Inscrição de dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos (DEP) da Apple ou do Apple Configurator"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 09/07/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c880bd9dfb998355a18e78af898a96d4cee393f7
ms.openlocfilehash: c28b51146deb6a0a28070f72449972fd60076231


---

# Inscrever dispositivos iOS pertencentes à empresa no Microsoft Intune
O Microsoft Intune suporta a inscrição de dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos (DEP) da Apple ou da ferramenta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) em execução num computador Mac.

**Pré-requisito:** é necessário um [Certificado do serviço Apple Push Notification](set-up-ios-and-mac-management-with-microsoft-intune.md).

Pode inscrever dispositivos iOS pertencentes à empresa de três formas: através do Apple Configurator, do DEP ou do Portal da Empresa.

## Utilizar o Apple Configurator

É possível inscrever dispositivos iOS ao exportar um perfil de Inscrição Empresarial e, em seguida, ligar esses dispositivos móveis a um Mac com o Apple Configurator. O Apple Configurator suporta duas formas de inscrição:

- **Inscrição com o Assistente de Configuração**: repõe o dispositivo para as definições de fábrica e prepara-o para a configuração por parte do novo utilizador do dispositivo. Este método requer que o administrador ligue o dispositivo iOS por USB a um computador Mac com o [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para pré-configurar a inscrição. Em seguida, são entregues dispositivos aos respetivos utilizadores,que executam o processo do Assistente de Configuração. Este processo configura o dispositivo com as credenciais da escola ou do trabalho e conclui o processo de inscrição. Para obter mais informações, veja [Inscrever dispositivos iOS com o Apple Configurator e o Assistente de Configuração](ios-setup-assistant-enrollment-in-microsoft-intune.md).

- **Inscrição Direta**: cria um ficheiro compatível com o Apple Configurator para utilização durante a preparação do dispositivo. Não é efetuada a reposição de fábrica no dispositivo inscrito e não existe nenhuma afiliação de utilizadores. Este método requer que o administrador ligue o dispositivo iOS por USB a um computador Mac a executar o [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para o inscrever. Para obter mais informações, veja [Inscrever dispositivos iOS com o Apple Configurator e a Inscrição Direta](ios-direct-enrollment-in-microsoft-intune.md).

## Utilizar o Programa de Inscrição de Dispositivos (DEP)
O DEP implementa um perfil de inscrição “por ondas eletromagnéticas” para dispositivos que são adquiridos através do DEP. Quando um utilizador executa o Assistente de Configuração no dispositivo, este é inscrito no Intune.  Os utilizadores não podem anular a inscrição de dispositivos inscritos através do DEP. Para obter mais informações, veja [Inscrever dispositivos iOS do Programa de Inscrição de Dispositivos](ios-device-enrollment-program-in-microsoft-intune.md).

## Utilizar o Portal da Empresa em dispositivos inscritos pelo Apple Configurator ou pelo DEP

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação do Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os respetivos dispositivos, têm de executar vários passos adicionais para concluir o Assistente de Configuração e instalar a aplicação do Portal da Empresa.

A afinidade de utilizador é necessária para suportar o seguinte:
  - Aplicações de gestão de aplicações móveis (MAM)
  - Acesso condicional a e-mail e dados da empresa
  - Aplicação do Portal da Empresa

**Como os utilizadores inscrevem dispositivos iOS pertencentes à empresa com afinidade de utilizador**
1. Quando os utilizadores ligam os dispositivos, é-lhes pedido que concluam o Assistente de Configuração. Durante a configuração, os utilizadores recebem um pedido de credenciais. Terão de utilizar as credenciais (ou seja, o nome pessoal exclusivo ou UPN) associadas à respetiva subscrição no Intune.

2. Durante a configuração, os utilizadores recebem um pedido do Apple ID. Terão de fornecer um Apple ID para permitir que o dispositivo instale o Portal da Empresa. Também podem fornecer o ID no menu de definições do iOS após a conclusão da configuração.

3. Depois de concluir a configuração, o dispositivo iOS tem de instalar a aplicação do Portal da Empresa a partir da App Store.

4. O utilizador poderá então iniciar sessão no Portal da Empresa através do UPN utilizado quando configurou o dispositivo.

5. Após iniciar sessão, é pedido ao utilizador que inscreva o dispositivo. O primeiro passo consiste em identificar o dispositivo. A aplicação apresenta uma lista de dispositivos iOS que já foram inscritos pela empresa e atribuídos à conta do Intune do utilizador. Deve escolher o dispositivo correspondente.

  Se este dispositivo ainda não tiver sido inscrito pela empresa, escolha **novo dispositivo** para continuar o fluxo de inscrição padrão.

6. No ecrã seguinte, o utilizador tem de confirmar o número de série do novo dispositivo. O utilizador pode tocar na ligação **confirme o Número de Série**para iniciar a aplicação Definições e verificar o número de série. Em seguida, o utilizador tem de introduzir os últimos quatro carateres do número de série na aplicação Portal da Empresa.

  Este passo verifica se o dispositivo é o dispositivo da empresa inscrito no Intune. Se o número de série do dispositivo não coincidir, significa que foi selecionado o dispositivo errado. O utilizador deve voltar ao ecrã anterior e selecionar um dispositivo diferente.

7. Depois de verificar o número de série, a aplicação Portal da Empresa redireciona o utilizador para o site Portal da Empresa para finalizar a inscrição. Em seguida, o site solicita ao utilizador que volte para a aplicação.

8. A inscrição está agora concluída. Agora, o utilizador pode utilizar este dispositivo com o conjunto completo de capacidades.

### Sobre dispositivos pertencentes à empresa geridos sem afinidade de utilizador

Os dispositivos configurados sem afinidade de utilizador não suportam o Portal da Empresa e não devem ter a aplicação instalada. O Portal da Empresa foi concebido para utilizadores com credenciais da empresa e que necessitam de acesso a recursos empresariais personalizados (por exemplo, e-mail). Os dispositivos inscritos sem afinidade de utilizador não se destinam a ter um início de sessão de utilizador dedicado. Os dispositivos de quiosque, ponto de venda (POS) ou utilitário partilhado são casos de utilização típicos para dispositivos inscritos sem afinidade de utilizador.

Se for necessária afinidade de utilizador, confirme que o perfil de inscrição do dispositivo tem a opção **Afinidade do Utilizador** selecionada antes de o inscrever. Para alterar o estado de afinidade num dispositivo, tem de extinguir e voltar a inscrever o dispositivo.



### Consulte também
[Pré-requisitos para a inscrição de dispositivos no Microsoft Intune](gprerequisites-for-enrollment.md)



<!--HONumber=Sep16_HO4-->


