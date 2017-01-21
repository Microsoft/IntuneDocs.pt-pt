---
title: "Resolução de problemas de implementação de aplicações | Documentos da Microsoft"
description: "Este tópico ajuda a resolver problemas de implementação de aplicações com o Microsoft Intune"
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 28ac298e-fb73-4c1c-b3fd-8336639e05e6
ms.reviewer: mghadial
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6d5ea579b675d85d4404f289db83055642ffddd
ms.openlocfilehash: 239371198cbbc01b1345c72b3f887055acd44462


---

# <a name="troubleshoot-app-deployment-problems-in-microsoft-intune"></a>Resolução de problemas de implementação de aplicações no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Se estiver a ter problemas de implementação e gestão de aplicações com o Intune, comece por aqui. Este tópico contém alguns problemas comuns que poderá encontrar juntamente com as soluções.

## <a name="common-app-deployment-error-codes"></a>Códigos de erro comuns na implementação de aplicações

|Código de erro|Possível problema|Resolução sugerida|
|--------------|--------------------|------------------------|
|0x80073CFF<br /><br />0x80CF201C (erro de cliente)|Para instalar esta aplicação, precisa de ter um sistema preparado para sideloading.|Certifique-se de que o pacote de aplicação está assinado com uma assinatura fidedigna e de que é instalado num dispositivo associado a um domínio com a política AllowAllTrustedApps ativada ou num dispositivo que tenha uma licença Sideload do Windows com a política AllowAllTrustedApps ativada.|
|0x80073CF0|Não foi possível abrir o pacote.|Causas possíveis:<br /><br />–   O pacote não está assinado.<br />–   O nome do publicador não corresponde ao assunto do certificado de assinatura.<br /><br />Verifique o registo de eventos AppxPackagingOM para obter mais informações.|
|0x80073CF3|A atualização, dependência ou validação de conflito do pacote falhou|Causas possíveis:<br /><br />–   O pacote recebido está em conflito com o pacote instalado.<br />–   Não foi encontrada uma dependência de pacote especificada.<br />–   O pacote não suporta a arquitetura de processador correta.<br /><br />Verifique o registo de eventos AppXDeployment-Server para obter mais informações.|
|0x80073CFB|O pacote fornecido já está instalado e a reinstalação do pacote está bloqueada|Poderá receber este erro se estiver a instalar um pacote que não é idêntico ao pacote que já está instalado. Verifique se a assinatura digital também faz parte do pacote. Quando um pacote é reconstruído ou assinado novamente, esse pacote já não é totalmente idêntico ao pacote anteriormente instalado. Existem duas opções possíveis para corrigir este erro:<br /><br />–   Incrementar o número de versão da aplicação e, em seguida, reconstruir e voltar a assinar o pacote.<br />–   Remover o pacote antigo de todos os utilizadores do sistema antes de instalar o pacote novo.|
|0x87D1041C|A aplicação foi instalada com êxito, mas a aplicação não foi detetada.|– A aplicação foi implementada com êxito pelo Intune, e foi desinstalada posteriormente (possivelmente pelo utilizador final). Diga ao utilizador para reinstalar a aplicação a partir do portal da empresa. As aplicações necessárias serão reinstaladas automaticamente quando o dispositivo efetuar a verificação seguinte.|

## <a name="troubleshooting-apps-from-the-windows-store"></a>Resolução de problemas de aplicações da Loja Windows

As informações presentes no tópico [Resolução de problemas de empacotamento, implementação e consulta de aplicações da Loja Windows](https://msdn.microsoft.com/library/windows/desktop/hh973484.aspx) ajudam-no a resolver problemas comuns que poderá encontrar ao instalar aplicações da Loja Windows, quer seja através do Intune ou de outros meios.

## <a name="troubleshooting-app-deployment-to-pcs-managed-by-the-intune-software-client"></a>Resolução de problemas de implementação de aplicações em PCs geridos pelo cliente de software do Intune
Para obter ajuda na resolução de problemas ao implementar aplicações em PCs geridos pelo cliente de software do Intune, pode consultar os dois ficheiros de registo seguintes:
- Pasta %ProgramFiles%\Microsoft\OnlineManagement\Logs
- %ProgramFiles%\Microsoft\OnlineManagement\Updates\ReportingEvents.log

Além disso, se precisar de abrir um caso de suporte para o Intune, também será útil enviar estes registos para a Microsoft.


### <a name="next-steps"></a>Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Dec16_HO2-->


