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
ms.sourcegitcommit: bbee6d3fec02a4d96b31a44a31218f684e0267c8
ms.openlocfilehash: ed961a945d0b7872553f2be2917ba273709b6d35


---

# Resolução de problemas de implementação de aplicações no Microsoft Intune
Se estiver a ter problemas de implementação e gestão de aplicações com o Intune, comece por aqui. Este tópico contém alguns problemas comuns que poderá encontrar juntamente com as soluções.

## Problemas comuns de implementação de aplicações

### Os utilizadores não conseguem iniciar sessão no Portal da Empresa do Intune

1.  Certifique-se de que a conta de utilizador existe e está ativada no [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854).

3.  No [portal do Office 365](http://go.microsoft.com/fwlink/p/?LinkId=698854), certifique-se de que o utilizador está a introduzir o nome de utilizador correto para iniciar sessão no Intune e de que está no formato: **joe@domain.com**. Se o utilizador parecer estar a introduzir a palavra-passe errada, peça-lhe para repô-la.

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

### Se uma ligação para uma aplicação iOS for direcionada para uma localização anterior na App Store do iTunes

1.  A sessão atual da App Store do iTunes está aberta na página da aplicação anterior.

2.  Feche a App Store do iTunes no dispositivo e volte a tentar a ligação.

### Se receber um erro ao iniciar uma aplicação iOS

1.  A data de expiração da aplicação poderá não ser válida.

### Se a aplicação ficar presa “em curso” durante o carregamento

1.  Ao carregar uma aplicação, os metadados são adicionados em primeiro lugar, seguidos pelo pacote da aplicação. Depois de os metadados terem sido carregados, o progresso da aplicação será apresentado. Se constatar que a aplicação fica no estado em curso durante um período de tempo anormalmente longo, elimine a aplicação e volte a carregá-la.

2.  Certifique-se de que não gere a implementação da aplicação enquanto esta se encontra no estado “em curso”.

### Se detetar uma falha ao instalar uma aplicação iOS

1.  Certifique-se de que a firewall da sua organização permite o acesso aos sites de certificação e aprovisionamento da Apple.

2.  Para obter mais informações, consulte a documentação de programador da Apple.

### Erro: o Publicador não existe
Utiliza **Adicionar Outro Contrato de Software** para adicionar um contrato de licença de terceiros. Tenta adicionar o publicador a partir da página **Outro contrato de licenciamento de software**. A página fornece uma lista dos publicadores existentes por ordem alfabética.
Introduz o publicador em falta, mas recebe o erro **O publicador não existe**.

Isto é propositado. O Intune fornece monitorização de licenças apenas para títulos de software populares. O Intune requer que, pelo menos, 4 contas diferentes comuniquem o software antes deste ser disponibilizado como opção na carga de trabalho de licenciamento.

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
|0x87D1041C|A aplicação foi instalada com êxito, mas a aplicação não foi detetada.|- O utilizador instalou a aplicação a partir do portal da empresa e depois desinstalou-a diretamente a partir do dispositivo. Reinstale a aplicação no portal da empresa.<br /><br />- Pode ter ocorrido um erro de correspondência entre o número da versão de uma aplicação de linha de negócio reconhecida pelo Intune e a versão instalada no dispositivo. Certifique-se que o Intune tem a versão correta e reinstale a aplicação.|

### Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Aug16_HO2-->


