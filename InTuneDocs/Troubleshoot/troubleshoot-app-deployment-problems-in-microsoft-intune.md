---
title: "Resolução de problemas de implementação de aplicações | Microsoft Intune"
description: "Este tópico ajuda a resolver problemas de implementação de aplicações com o Microsoft Intune"
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 08/02/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aa96cf3a1909e3ea2187a3beb0aede3228894504
ms.openlocfilehash: 9f4b91bd523c82665bcac54902b2e8cc9c72ef75


---

# Resolução de problemas de implementação de aplicações no Microsoft Intune
Se estiver a ter problemas de implementação e gestão de aplicações com o Intune, comece por aqui. Este tópico contém alguns problemas comuns que poderá encontrar juntamente com as soluções.

## Problemas comuns de implementação de aplicações

### As informações para Contactar TI estiverem em falta no Portal da Empresa

1.  Na consola de administração do Intune, escolha **Admin**&gt;**Portal da Empresa**.

2.  Defina os detalhes de **Contactar TI** .

### Se não forem apresentadas aplicações específicas na lista

1.  Certifique-se de que está a verificar a lista de aplicações de um utilizador ou dispositivo para o qual a aplicação foi implementada.

2.  Certifique-se de que o dispositivo cumpre os requisitos da aplicação.

### Se receber um erro ao transferir uma aplicação

1.  Certifique-se de que não existe mais do que uma transferência em simultâneo por utilizador. Cada utilizador pode transferir uma aplicação de cada vez.

2.  Certifique-se de que não existem demasiadas transferências em simultâneo por conta. Aguarde alguns minutos e tente novamente.

3.  Se receber uma mensagem nativa do iOS informando-o de que não pode instalar, de que a instalação foi cancelada ou de que tem de tentar novamente, tal poderá dever-se a tráfego elevado. Aguarde alguns minutos e tente novamente.

4.  Se a barra de progresso da transferência da aplicação iOS estiver completa, mas a instalação da aplicação falhar, os ficheiros de aplicação que forneceu poderão ter algum problema.


### Se a aplicação ficar presa “em curso” durante o carregamento

1.  Ao carregar uma aplicação, os metadados são adicionados em primeiro lugar, seguidos pelo pacote da aplicação. Depois de os metadados terem sido carregados, o progresso da aplicação será apresentado. Se constatar que a aplicação fica no estado em curso durante um período de tempo anormalmente longo, elimine a aplicação e volte a carregá-la.

2.  Certifique-se de que não gere a implementação da aplicação enquanto esta se encontra no estado “em curso”.

### Se detetar uma falha ao instalar uma aplicação iOS

1.  Certifique-se de que a firewall da sua organização permite o acesso aos sites de certificação e aprovisionamento da Apple.

2.  Para obter mais informações, consulte a documentação de programador da Apple.

### Se as aplicações geridas não estiverem a comunicar o estado da instalação

O estado de instalação não foi recolhido para instalações de aplicações geridas antes da atualização de serviço Microsoft Intune em Novembro de 2014. No que respeita aos dispositivos que tenham instalado aplicações geridas antes desta atualização de serviço, atualize cada implementação de aplicação associada com a ação de implementação adequada (por exemplo, **Instalação disponível**). Cada dispositivo atualizará a aplicação durante a verificação automática de aplicações disponíveis. Para mais informações, consulte [Atualizar aplicações com o Microsoft Intune](/intune/deploy-use/update-apps-using-microsoft-intune).

## <a name="BKMK_SoftDistErrorCodes"></a>Códigos de erro de implementação de aplicações
A tabela seguinte lista erros comuns que poderão ocorrer durante a implementação da aplicação Intune, as causas prováveis e possíveis soluções para o ajudar a resolvê-los.

|Código de erro|Possível problema|Resolução sugerida|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (erro de cliente)|Para instalar esta aplicação, precisa de ter um sistema preparado para sideloading.|Certifique-se de que o pacote de aplicação está assinado com uma assinatura fidedigna e de que é instalado num dispositivo associado a um domínio com a política AllowAllTrustedApps ativada, ou num dispositivo que tenha uma licença Sideload do Windows com a política AllowAllTrustedApps ativada (aplicada quando um dispositivo Windows RT está inscrito).|
|0x80073CF0|Não foi possível abrir o pacote.|Causas possíveis:<br /><br />-   O pacote não está assinado.<br />-   O nome do publicador não corresponde ao assunto do certificado de assinatura.<br /><br />Verifique o registo de eventos AppxPackagingOM para obter mais informações.|
|0x80073CF3|A atualização, dependência ou validação de conflito do pacote falhou|Causas possíveis:<br /><br />-   O pacote recebido está em conflito com o pacote instalado.<br />-   Não foi encontrada uma dependência de pacote especificada.<br />-   O pacote não suporta a arquitetura de processador correta.<br /><br />Verifique o registo de eventos AppXDeployment-Server para obter mais informações.|
|0x80073CFB|O pacote fornecido já está instalado e a reinstalação do pacote está bloqueada|Poderá receber este erro se estiver a instalar um pacote que não é idêntico ao pacote que já está instalado. Verifique se a assinatura digital também faz parte do pacote. Quando um pacote é reconstruído ou assinado novamente, esse pacote já não é totalmente idêntico ao pacote anteriormente instalado. Existem duas opções possíveis para corrigir este erro:<br /><br />-   Incrementar o número de versão da aplicação e, em seguida, reconstruir e voltar a assinar o pacote.<br />-   Remover o pacote antigo de todos os utilizadores do sistema antes de instalar o pacote novo.|
|0x87D1041C|A aplicação foi instalada com êxito, mas a aplicação não foi detetada.|- A aplicação foi implementada com êxito pelo Intune, e foi desinstalada posteriormente (possivelmente pelo utilizador final). Diga ao utilizador para reinstalar a aplicação a partir do portal da empresa. As aplicações necessárias serão reinstaladas automaticamente quando o dispositivo efetuar a verificação seguinte.|

### Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Aug16_HO5-->


