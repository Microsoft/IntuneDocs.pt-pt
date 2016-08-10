---
title: "Inscrever dispositivos iOS pertencentes à empresa | Microsoft Intune"
description: "Inscrição de dispositivos iOS pertencentes à empresa através do Programa de Inscrição de Dispositivos (DEP) da Apple ou do Apple Configurator"
keywords: 
author: NathBarn
manager: angrobe
ms.date: 07/19/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 2d3ca4ab-f20c-4d56-9413-f8ef19cf0722
ms.reviewer: dagerrit
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9b7b8f6e5182e228458f5ea75e804a638f1e2a2b
ms.openlocfilehash: ca05e94e72269c11db24b667f1d113c794cd8b23


---

# Inscrever dispositivos iOS pertencentes à empresa no Microsoft Intune
O Microsoft Intune suporta a inscrição de dispositivos iOS pertencentes à empresa através do Programa de registo de dispositivos da Apple (DEP) ou da ferramenta [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) em execução num computador Mac.

**Pré-requisito:** [Certificado do serviço Apple Push Notification](set-up-ios-and-mac-management-with-microsoft-intune.md)

Pode inscrever dispositivos iOS pertencentes à empresa de três formas diferentes:

-   **Apple Configurator** - é possível inscrever dispositivos iOS ao exportar um perfil de Inscrição Empresarial e, em seguida, ligar esses dispositivos móveis a um Mac com o Apple Configurator. O Apple Configurator suporta duas formas de inscrição:

    - **Inscrição com o Assistente de Configuração** - repõe o dispositivo para as definições de fábrica e prepara-o para a configuração por parte do novo utilizador do dispositivo. Este método requer que o administrador ligue o dispositivo iOS por USB ao computador Mac que está a executar o [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para pré-configurar a inscrição. Os dispositivos são, depois, entregues aos utilizadores, que executam o processo Assistente de configuração, configurando os dispositivos com as credenciais escolares ou profissionais e concluindo o processo de inscrição. [Inscrever dispositivos iOS com o Apple Configurator e o Assistente de configuração](ios-setup-assistant-enrollment-in-microsoft-intune.md)

    - **Inscrição Direta** - cria um ficheiro compatível com o Apple Configurator para utilização durante a preparação do dispositivo. Não é efetuada a reposição do dispositivos para as definições de fábrica mas não existe uma afiliação a utilizadores. Este método requer que o administrador ligue o dispositivo iOS por USB ao computador Mac que está a executar o [Apple Configurator](http://go.microsoft.com/fwlink/?LinkId=518017) para o inscrever. [Inscrever dispositivos iOS com o Apple Configurator e a Inscrição Direta](ios-direct-enrollment-in-microsoft-intune.md)

-   **Programa de inscrição de dispositivos (DEP)** – implementa um perfil de inscrição por ondas eletromagnéticas em dispositivos comprados através do Programa de inscrição de dispositivos da Apple. Quando o utilizador executa o Assistente de configuração no dispositivo, este é inscrito no Intune.  Os utilizadores não podem anular a inscrição de dispositivos inscritos através do DEP. [Inscrição de dispositivos iOS do Programa de inscrição de dispositivos](ios-device-enrollment-program-in-microsoft-intune.md)

## Utilizar o Portal da Empresa no DEP ou dispositivos inscritos pelo Apple Configurator

Os dispositivos configurados com a afinidade de utilizador podem instalar e executar a aplicação do Portal da Empresa para transferir aplicações e gerir dispositivos. Assim que os utilizadores recebem os respetivos dispositivos, têm de executar vários passos adicionais para concluir o Assistente de Configuração e instalar a aplicação do Portal da Empresa.

Como inscrever dispositivos iOS pertencentes à empresa com afinidade de utilizador
1. Quando os utilizadores ligam os dispositivos, é-lhes pedido que concluam o Assistente de Configuração. Durante a configuração, os utilizadores recebem um pedido de credenciais. Terão de utilizar as credenciais (ou seja, o nome pessoal exclusivo ou UPN) associadas à respetiva subscrição no Intune.

2. Durante a configuração, os utilizadores recebem um pedido do Apple ID. Tem de ser fornecido um Apple ID para permitir que o dispositivo instale o Portal da Empresa. Também pode ser fornecido um Apple ID após a configuração estar concluída no menu de definições do iOS.

3. Depois de concluir a configuração, o dispositivo iOS tem de instalar a aplicação do Portal da Empresa a partir da App Store, como, por exemplo, a aplicação do Portal da Empresa.

4. O utilizador poderá então iniciar sessão no Portal da Empresa, utilizando o UPN utilizado quando configurou o dispositivo.

5. Após iniciar sessão, é pedido ao utilizador que inscreva o dispositivo. O primeiro passo é Identificar o dispositivo. A aplicação apresenta uma lista de dispositivos iOS que já foram inscritos pela empresa e atribuídos à conta do Intune do utilizador final. Selecione o dispositivo correspondente.

  Se este dispositivo não estiver já inscrito pela empresa, selecione “novo dispositivo” para continuar o fluxo de inscrição padrão.

6. No ecrã seguinte, o utilizador tem de confirmar o número de série do novo dispositivo. O utilizador pode tocar na ligação “confirme o número de série” de modo a iniciar a aplicação Definições para verificar o número de série. Em seguida, o utilizador tem de introduzir os últimos 4 carateres do número de série na aplicação Portal da Empresa.

  Este passo verifica se o dispositivo é o dispositivo da empresa inscrito no Intune. Se o número de série do dispositivo não coincidir, significa que foi selecionado o dispositivo errado. Volte ao ecrã anterior e selecione um dispositivo diferente.

7. Depois de verificar o número de série, a aplicação Portal da Empresa redireciona o utilizador ao site Portal da Empresa para finalizar a inscrição e, em seguida, pede ao utilizador para regressar à aplicação.

8. A inscrição está agora concluída. Agora, pode utilizar este dispositivo com o conjunto completo de capacidades.

### Sobre dispositivos pertencentes à empresa geridos sem afinidade de utilizador

Os dispositivos configurados sem afinidade de utilizador não suportam o Portal da Empresa e não devem instalar a aplicação. O Portal da Empresa foi concebido para utilizadores com credenciais da empresa e que necessitam de acesso a recursos empresariais personalizados (por exemplo, e-mail). Os dispositivos inscritos sem afinidade de utilizador não se destinam a ter um início de sessão de utilizador dedicado. Os dispositivos de quiosque, ponto de venda (POS) ou utilitário partilhado são casos de utilização típicos para dispositivos inscritos sem afinidade de utilizador. Se for necessária afinidade de utilizador, confirme que o perfil de inscrição do dispositivo tem a opção Afinidade de Utilizador selecionada antes de o inscrever. Para alterar o estado de afinidade num dispositivo, tem de extinguir e voltar a inscrever o dispositivo.



### Consulte também
[Prepare-se para inscrever dispositivos no Microsoft Intune](get-ready-to-enroll-devices-in-microsoft-intune.md)



<!--HONumber=Aug16_HO1-->


