---
title: "Resolver problemas de atualizações de software"
description: "Resolva problemas de atualizações de software no Microsoft Intune."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/27/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: d17b70f4-17b4-4d89-88fd-70fa4f34fbea
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: b33c5978c2cb27eb7e486d139e71937c41f48b28
ms.contentlocale: pt-pt
ms.lasthandoff: 06/08/2017


---

# <a name="troubleshoot-software-updates-in-microsoft-intune"></a>Resolver problemas de atualizações de software no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize as informações nesta secção para obter ajuda para resolver problemas de atualizações de software no Microsoft Intune.

Se estas informações não resolverem o problema, veja [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md) para ver mais formas de obter ajuda.

## <a name="update-agent-error-codes"></a>Códigos de erro do agente de atualização

A seguinte tabela indica os códigos de erro do **Update Agent** do Intune. Se não conseguir localizar um código de erro específico nesta tabela, consulte o artigo [Códigos de Resultados do Windows Update Agent](http://go.microsoft.com/fwlink/?LinkID=221542).

|Código de erro|Nome simbólico|Mais informações|
|--------------|-----------------|--------------------|
|**0x00cf0001**|OM_S_SERVICE_STOP|O agente foi parado com êxito.|
|**0x00cf0003**|OM_S_UPDATE_ERROR|A operação foi concluída com êxito, mas ocorreram erros durante a aplicação de atualizações.|
|**0x00cf0004**|OM_S_MARKED_FOR_DISCONNECT|Uma chamada de retorno foi marcada para ser desligada mais tarde porque o pedido para desligar a operação foi recebido durante uma chamada de retorno.|
|**0x00cf0005**|OM_S_REBOOT_REQUIRED|O sistema tem de ser reiniciado para concluir a instalação da atualização.|
|**0x00cf0006**|OM_S_ALREADY_INSTALLED|A atualização a instalar já está instalada no sistema.|
|**0x00cf0007**|OM_S_ALREADY_UNINSTALLED|A atualização a remover não está instalada no sistema.|
|**0x00cf2015**|OM_S_UH_INSTALLSTILLPENDING|A instalação da atualização está em curso.|
|**0x80cf0001**|OM_E_NO_SERVICE|O agente não conseguiu fornecer o serviço.|
|**0x80cf0002**|OM_E_MAX_CAPACITY_REACHED|A capacidade máxima do serviço foi excedida.|
|**0x80cf0003**|OM_E_UNKNOWN_ID|Não foi possível localizar um ID.|
|**0x80cf0004**|OM_E_NOT_INITIALIZED|Não foi possível inicializar o objeto.|
|**0x80cf0007**|OM_E_INVALIDINDEX|O índice de uma coleção não é válido.|
|**0x80cf0008**|OM_E_ITEMNOTFOUND|Não foi possível localizar a chave do item consultado.|
|**0x80cf0009**|OM_E_OPERATIONINPROGRESS|Estava em curso uma operação em conflito. Algumas operações, tal como múltiplas instalações, não podem ser executadas em simultâneo.|
|**0x80cf000B**|OM_E_CALL_CANCELLED|A operação foi cancelada.|
|**0x80cf000C**|OM_E_NOOP|Não foi necessária nenhuma operação.|
|**0x80cf000D**|OM_E_XML_MISSINGDATA|O agente não conseguiu localizar as informações necessárias nos dados XML da atualização.|
|**0x80cf000E**|OM_E_XML_INVALID|O agente localizou informações que não são válidas nos dados XML da atualização.|
|**0x80cf000F**|OM_E_CYCLE_DETECTED|Foram detetadas relações de atualização circulares nos metadados.|
|**0x80cf0010**|OM_E_TOO_DEEP_RELATION|As relações de atualização estavam demasiado aninhadas para serem avaliadas.|
|**0x80cf0011**|OM_E_INVALID_RELATIONSHIP|Foi localizada uma relação de atualização que não é válida.|
|**0x80cf0012**|OM_E_REG_VALUE_INVALID|Foi lido um valor de registo que não é válido.|
|**0x80cf0013**|OM_E_DUPLICATE_ITEM|A operação tentou adicionar um item duplicado a uma lista.|
|**0x80cf0014**|OM_E_INVALID_INSTALL_REQUESTED|A função invocadora não consegue instalar atualizações pedidas para esta instalação.|
|**0x80cf0016**|OM_E_INSTALL_NOT_ALLOWED|A operação tentou instalar enquanto outra instalação estava em curso ou o sistema tinha um reinício obrigatório pendente.|
|**0x80cf0017**|OM_E_NOT_APPLICABLE|A operação não foi realizada porque não existem atualizações aplicáveis.|
|**0x80cf0018**|OM_E_NO_USERTOKEN|A operação falhou porque um token de utilizador obrigatório está em falta.|
|**0x80cf0019**|OM_E_EXCLUSIVE_INSTALL_CONFLICT|Não é possível instalar uma atualização exclusiva em simultâneo com outras atualizações.|
|**0x80cf001A**|OM_E_POLICY_NOT_SET|Não foi definido um valor de política.|
|**0x80cf001D**|OM_E_INVALID_UPDATE|Uma atualização contém metadados que não são válidos.|
|**0x80cf001E**|OM_E_SERVICE_STOP|Não foi possível concluir a operação porque o serviço ou sistema estava a ser encerrado.|
|**0x80cf001F**|OM_E_NO_CONNECTION|Não foi possível concluir a operação porque a ligação de rede não estava disponível.|
|**0x80cf0020**|OM_E_NO_INTERACTIVE_USER|Não foi possível concluir a operação porque não existe nenhum utilizador interativo com sessão iniciada.|
|**0x80cf0021**|OM_E_TIME_OUT|Não foi possível concluir a operação porque esta excedeu o limite de tempo.|
|**0x80cf0022**|OM_E_ALL_UPDATES_FAILED|A operação falhou para todas as atualizações.|
|**0x80cf0024**|OM_E_NO_UPDATE|Não existem atualizações.|
|**0x80cf0025**|OM_E_USER_ACCESS_DISABLED|As definições da Política de Grupo impediram o acesso ao Windows Update.|
|**0x80cf0026**|OM_E_INVALID_UPDATE_TYPE|O tipo de atualização não é válido.|
|**0x80cf0028**|OM_E_UNINSTALL_NOT_ALLOWED|Não foi possível desinstalar a atualização porque o pedido não teve origem num servidor WSUS.|
|**0x80cf0029**|OM_E_INVALID_PRODUCT_LICENSE|Algumas atualizações podem não ter sido incluídas na pesquisa ou pode existir uma aplicação não licenciada no sistema.|
|**0x80cf002C**|OM_E_BIN_SOURCE_ABSENT|Não foi possível instalar uma atualização com compressão delta porque é necessária a origem.|
|**0x80cf002D**|OM_E_SOURCE_ABSENT|Não foi possível instalar uma atualização completa do ficheiro porque é necessária a origem.|
|**0x80cf002E**|OM_E_WU_DISABLED|Não é permitido o acesso a um servidor não gerido.|
|**0x80cf002F**|OM_E_CALL_CANCELLED_BY_POLICY|Não foi possível concluir a operação porque foi definida a política **DisableWindowsUpdateAccess**.|
|**0x80cf0030**|OM_E_INVALID_PROXY_SERVER|O formato da lista de proxies não é válido.|
|**0x80cf0031**|OM_E_INVALID_FILE|O ficheiro está no formato errado.|
|**0x80cf0032**|OM_E_INVALID_CRITERIA|A cadeia de critérios de pesquisa não é válida.|
|**0x80cf0034**|OM_E_DOWNLOAD_FAILED|A transferência da atualização falhou.|
|**0x80cf0035**|OM_E_UPDATE_NOT_PROCESSED|A atualização não foi processada.|
|**0x80cf0036**|OM_E_INVALID_OPERATION|O estado atual do objeto não permitiu a operação.|
|**0x80cf0037**|OM_E_NOT_SUPPORTED|A operação não é suportada.|
|**0x80cf0038**|OM_E_WINHTTP_INVALID_FILE|O ficheiro transferido tem um tipo de conteúdo inesperado.|
|**0x80cf0039**|OM_E_TOO_MANY_RESYNC|O servidor pediu demasiadas vezes ao agente para ressincronizar.|
|**0x80cf0043**|OM_E_NO_UI_SUPPORT|Não existe suporte para a IU do WUA.|
|**0x80cf0044**|OM_E_PER_MACHINE_UPDATE_ACCESS_DENIED|Só os administradores podem executar esta operação em atualizações por computador.|
|**0x80cf0045**|OM_E_UNSUPPORTED_SEARCHSCOPE|Foi efetuada uma tentativa de pesquisa com um âmbito não suportado.|
|**0x80cf0046**|OM_E_BAD_FILE_URL|O URL não aponta para um ficheiro.|
|**0x80cf0047**|OM_E_NOTSUPPORTED|A operação pedida não é suportada.|
|**0x80cf0049**|OM_E_OUTOFRANGE|Os dados estão fora do intervalo.|
|**0x80cf004A**|OM_E_INVALIDWUAVERSION|Os dados contêm uma versão que não é válida.|
|**0x80cf004B**|OM_E_SEARCH_COMPLETED_WITH_SOME_FAILURES|A chamada de pesquisa foi concluída, mas não conseguiu detetar algumas das atualizações.|
|**0x80cf004C**|OM_E_DOWNLOAD_COMPLETED_WITH_SOME_FAILURES|A chamada de transferência foi concluída, mas não conseguiu transferir algumas das atualizações.|
|**0x80cf004D**|OM_E_INSTALL_COMPLETED_WITH_SOME_FAILURES|A chamada de instalação foi concluída, mas não conseguiu instalar algumas das atualizações.|
|**0x80cf004E**|OM_E_WINUPDATE_CACHE_UNINITIALIZED|A cache do Windows Update está vazia porque não foi inicializada.|
|**0x80cf0436**|OM_E_PT_CATALOG_SYNC_REQUIRED|O servidor não suporta pesquisas em categorias específicas. Em alternativa, é necessário executar uma pesquisa no catálogo inteiro.|
|**0x80cf0437**|OM_E_PT_SECURITY_VERIFICATION_FAILURE|Ocorreu um problema de autorização no serviço.|
|**0x80cf0438**|OM_E_PT_ENDPOINT_UNREACHABLE|Não existe rota ou conectividade de rede para o ponto final.|
|**0x80cf0439**|OM_E_PT_INVALID_FORMAT|Os dados recebidos não correspondem às expectativas do contrato de dados.|
|**0x80cf043A**|OM_E_PT_INVALID_URL|O URL não é válido.|
|**0x80cf043B**|OM_E_PT_NWS_NOT_LOADED|Não é possível carregar o tempo de execução do NWS.|
|**0x80cf043C**|OM_E_PT_PROXY_AUTH_SCHEME_NOT_SUPPORTED|O esquema de autenticação de proxy não é suportado.|
|**0x80cf043D**|OM_E_SERVICEPROP_NOTAVAIL|A propriedade do serviço pedida não está disponível.|
|**0x80cf043E**|OM_E_PT_ENDPOINT_REFRESH_REQUIRED|O plug-in do fornecedor do ponto final necessita de uma atualização online.|
|**0x80cf043F**|OM_E_PT_ENDPOINTURL_NOTAVAIL|Não está disponível um URL para o ponto final do serviço pedido.|
|**0x80cf0440**|OM_E_PT_ENDPOINT_DISCONNECTED|A ligação ao ponto final do serviço foi terminada.|
|**0x80cf0441**|OM_E_PT_INVALID_OPERATION|A operação não é válida porque o locutor do protocolo está num estado inadequado.|
|**0x80cf0FFF**|OM_E_UNEXPECTED|Uma operação falhou por motivos que não são explicados por outro código de erro.|
|**0x80cf1001**|OM_E_MSI_WRONG_VERSION|Algumas atualizações podem não ter sido incluídas na pesquisa porque o Windows Installer é de uma versão anterior à versão 3.1.|
|**0x80cf1002**|OM_E_MSI_NOT_CONFIGURED|Algumas atualizações podem não ter sido incluídas na pesquisa porque o Windows Installer não está configurado.|
|**0x80cf1003**|OM_E_MSP_DISABLED|Algumas atualizações podem não ter sido incluídas na pesquisa porque uma política desativou a aplicação de patches do Windows Installer.|
|**0x80cf1004**|OM_E_MSI_WRONG_APP_CONTEXT|Não foi possível aplicar uma atualização porque a aplicação é instalada por utilizador.|
|**0x80cf2000**|OM_E_UH_REMOTEUNAVAILABLE|Não foi possível concluir um pedido a um processador de atualizações remoto porque não está disponível nenhum processo remoto.|
|**0x80cf2001**|OM_E_UH_LOCALONLY|Não foi possível concluir um pedido de processador de atualizações remoto porque o processador é apenas local.|
|**0x80cf2003**|OM_E_UH_REMOTEALREADYACTIVE|Não foi possível criar um processador de atualizações remoto porque já existe um.|
|**0x80cf2004**|OM_E_UH_DOESNOTSUPPORTACTION|Não foi possível concluir um pedido enviado ao processador para instalar (desinstalar) uma atualização porque a atualização não suporta a instalação (desinstalação).|
|**0x80cf2005**|OM_E_UH_WRONGHANDLER|Não foi possível concluir uma operação porque foi especificado um processador incorreto.|
|**0x80cf2006**|OM_E_UH_INVALIDMETADATA|Não foi possível concluir uma operação do processador porque a atualização contém metadados que não são válidos.|
|**0x80cf2007**|OM_E_UH_INSTALLERHUNG|Não foi possível concluir uma operação porque o instalador excedeu o limite de tempo. Verifique se foi aprovada para implementação alguma atualização que necessite de interação do utilizador. Neste caso, tem de rever os parâmetros de instalação da atualização para que possa ser efetuada uma instalação automática.|
|**0x80cf2008**|OM_E_UH_OPERATIONCANCELLED|Foi cancelada uma operação que estava a ser realizada pelo processador de atualizações.|
|**0x80cf2009**|OM_E_UH_BADHANDLERXML|Não foi possível concluir uma operação porque os metadados específicos do processador não são válidos.|
|**0x80cf200B**|OM_E_UH_INSTALLERFAILURE|O instalador falhou ao instalar (desinstalar) uma ou mais atualizações.|
|**0x80cf200D**|OM_E_UH_NEEDANOTHERDOWNLOAD|O processador de atualizações não instalou a atualização porque esta tem de ser transferida novamente.|
|**0x80cf200E**|OM_E_UH_NOTIFYFAILURE|O processador de atualizações não conseguiu enviar a notificação do estado da operação de instalação (desinstalação).|
|**0x80cf2014**|OM_E_UH_POSTREBOOTSTILLPENDING|A operação pós-reinício da atualização ainda está em curso.|
|**0x80cf2015**|OM_E_UH_POSTREBOOTRESULTUNKNOWN|Não foi possível determinar o resultado da operação pós-reinício da atualização.|
|**0x80cf2016**|OM_E_UH_POSTREBOOTUNEXPECTEDSTATE|O estado da atualização após a conclusão da operação pós-reinício é inesperado.|
|**0x80cf2017**|OM_E_UH_NEW_SERVICING_STACK_REQUIRED|A pilha de serviço do sistema operativo tem de ser atualizada antes de transferir ou instalar esta atualização.|
|**0x80cf2018**|OM_E_UH_CALLED_BACK_FAILURE|Um instalador de chamada de retorno devolveu a chamada com um erro.|
|**0x80cf2019**|OM_E_UH_CUSTOMINSTALLER_INVALID_SIGNATURE|A assinatura personalizada do instalador não correspondeu à assinatura exigida pela atualização.|
|**0x80cf201A**|OM_E_UH_UNSUPPORTED_INSTALLCONTEXT|O instalador não suporta a configuração da instalação.|
|**0x80cf201B**|OM_E_UH_INVALID_TARGETSESSION|A sessão visada para a instalação não é válida.|
|**0x80cf2FFF**|OM_E_UH_UNEXPECTED|Um erro do processador de atualizações não é abrangido por outro código OM_E_UH_&#42;.|
|**0x80cf3FFD**|OM_E_NON_UI_MODE|Não é possível mostrar a IU no modo não IU. Os módulos de IU do cliente do Windows Update poderão não estar instalados.|
|**0x80cf3FFE**|OM_E_WUCLTUI_UNSUPPORTED_VERSION|Esta versão das funções de IU exportadas do cliente WU não é suportada.|
|**0x80cf3FFF**|OM_E_AUCLIENT_UNEXPECTED|Ocorreu um erro de interface de utilizador que não é abrangido por outro código de erro OM_E_AUCLIENT_&#42;.|
|**0x80cf4007**|OM_E_PT_SOAPCLIENT_SOAPFAULT|O mesmo que **SOAPCLIENT_SOAPFAULT**. O cliente SOAP falhou porque ocorreu uma falha SOAP do tipo de código de erro **OM_E_PT_SOAP_&#42;**.|
|**0x80cf4008**|OM_E_PT_SOAPCLIENT_PARSEFAULT|O mesmo que **SOAPCLIENT_PARSEFAULT_ERROR**.  O cliente SOAP não analisou um erro de falha SOAP.|
|**0x80cf400A**|OM_E_PT_SOAPCLIENT_PARSE|O mesmo que **SOAPCLIENT_PARSE_ERROR**.  O cliente SOAP não analisou a resposta do servidor.|
|**0x80cf400B**|OM_E_PT_SOAP_VERSION|O mesmo que **SOAP_E_VERSION_MISMATCH**. O cliente SOAP detetou um espaço de nomes irreconhecível no envelope SOAP.|
|**0x80cf400C**|OM_E_PT_SOAP_MUST_UNDERSTAND|O mesmo que **SOAP_E_MUST_UNDERSTAND**. O cliente SOAP não conseguiu interpretar um cabeçalho.|
|**0x80cf400D**|OM_E_PT_SOAP_CLIENT|O mesmo que **SOAP_E_CLIENT**. O cliente SOAP detetou que a mensagem estava com um formato incorreto. Corrija antes de reenviar.|
|**0x80cf400E**|OM_E_PT_SOAP_SERVER|O mesmo que **SOAP_E_SERVER**. Não foi possível processar a mensagem SOAP devido a um erro no servidor. Reenvie mais tarde.|
|**0x80cf4010**|OM_E_PT_EXCEEDED_MAX_SERVER_TRIPS|O número de ações de ida e volta ao servidor excedeu o limite máximo.|
|**0x80cf4012**|OM_E_PT_DOUBLE_INITIALIZATION|A inicialização falhou porque o objeto já tinha sido inicializado.|
|**0x80cf4013**|OM_E_PT_INVALID_COMPUTER_NAME|Não foi possível determinar o nome do computador.|
|**0x80cf4015**|OM_E_PT_REFRESH_CACHE_REQUIRED|A resposta do servidor indica que o servidor foi alterado ou que o cookie era inválido. Atualize a cache interna e tente novamente.|
|**0x80cf4016**|OM_E_PT_HTTP_STATUS_BAD_REQUEST|O mesmo que **Estado HTTP 400**. O servidor não conseguiu processar o pedido porque a sintaxe não é válida.|
|**0x80cf4017**|OM_E_PT_HTTP_STATUS_DENIED|O mesmo que **Estado HTTP 401**. O recurso pedido requer autenticação do utilizador.|
|**0x80cf4018**|OM_E_PT_HTTP_STATUS_FORBIDDEN|O mesmo que **Estado HTTP 403**. O servidor compreendeu o pedido, mas recusou-se a executá-lo.|
|**0x80cf4019**|OM_E_PT_HTTP_STATUS_NOT_FOUND|O mesmo que **Estado HTTP 404**. O servidor não consegue localizar o URI (Uniform Resource Identifier) pedido.|
|**0x80cf401A**|OM_E_PT_HTTP_STATUS_BAD_METHOD|O mesmo que **Estado HTTP 405**. O método HTTP não é permitido.|
|**0x80cf401B**|OM_E_PT_HTTP_STATUS_PROXY_AUTH_REQ|O mesmo que **Estado HTTP 407**. É necessária autenticação de proxy.|
|**0x80cf401C**|OM_E_PT_HTTP_STATUS_REQUEST_TIMEOUT|O mesmo que **Estado HTTP 408**. O servidor excedeu o limite de tempo ao aguardar pelo pedido.|
|**0x80cf401D**|OM_E_PT_HTTP_STATUS_CONFLICT|O mesmo que **Estado HTTP 409**. O pedido não foi concluído devido a um conflito com o estado atual do recurso.|
|**0x80cf401E**|OM_E_PT_HTTP_STATUS_GONE|O mesmo que **Estado HTTP 410**. O recurso pedido já não está disponível no servidor.|
|**0x80cf401F**|OM_E_PT_HTTP_STATUS_SERVER_ERROR|O mesmo que **Estado HTTP 500**. Um erro interno do servidor impediu a execução do pedido.|
|**0x80cf4020**|OM_E_PT_HTTP_STATUS_NOT_SUPPORTED|O mesmo que **Estado HTTP 500**. O servidor não suporta a funcionalidade que é necessária para satisfazer o pedido.|
|**0x80cf4021**|OM_E_PT_HTTP_STATUS_BAD_GATEWAY|O mesmo que **Estado HTTP 502**. O servidor recebeu uma resposta inválida do servidor a montante ao qual acedeu para tentar satisfazer o pedido, enquanto funcionava como gateway ou proxy.|
|**0x80cf4022**|OM_E_PT_HTTP_STATUS_SERVICE_UNAVAIL|O mesmo que **Estado HTTP 503**. O serviço está temporariamente sobrecarregado.|
|**0x80cf4023**|OM_E_PT_HTTP_STATUS_GATEWAY_TIMEOUT|O mesmo que **Estado HTTP 503**. O pedido excedeu o limite de tempo ao aguardar por um gateway.|
|**0x80cf4024**|OM_E_PT_HTTP_STATUS_VERSION_NOT_SUP|O mesmo que **Estado HTTP 505**. O servidor não suporta a versão do protocolo HTTP que foi utilizada no pedido.|
|**0x80cf4025**|OM_E_PT_FILE_LOCATIONS_CHANGED|A operação falhou devido à alteração da localização de um ficheiro. Atualize o estado interno e reenvie.|
|**0x80cf4027**|OM_E_PT_NO_AUTH_PLUGINS_REQUESTED|O servidor devolveu uma lista de informações de autenticação vazia.|
|**0x80cf4028**|OM_E_PT_NO_AUTH_COOKIES_CREATED|O agente não conseguiu criar nenhum cookie de autenticação válido.|
|**0x80cf4029**|OM_E_PT_INVALID_CONFIG_PROP|Um valor de propriedade de configuração estava incorreto.|
|**0x80cf402A**|OM_E_PT_CONFIG_PROP_MISSING|Um valor de propriedade de configuração estava em falta.|
|**0x80cf402B**|OM_E_PT_HTTP_STATUS_NOT_MAPPED|Não foi possível concluir o pedido HTTP e o motivo não correspondeu a nenhum dos códigos de erro **OM_E_PT_HTTP_&#42;**.|
|**0x80cf402C**|OM_E_PT_WINHTTP_NAME_NOT_RESOLVED|O mesmo que **ERROR_WINHTTP_NAME_NOT_RESOLVED**. Não é possível resolver o servidor proxy ou o nome do servidor de destino.|
|**0x80cf402F**|OM_E_PT_ECP_SUCCEEDED_WITH_ERRORS|O processamento do ficheiro .cab externo foi concluído com alguns erros.|
|**0x80cf4030**|OM_E_PT_ECP_INIT_FAILED|A inicialização do processador de ficheiros .cab externos não foi concluída.|
|**0x80cf4031**|OM_E_PT_ECP_INVALID_FILE_FORMAT|O formato de um ficheiro de metadados não é válido.|
|**0x80cf4032**|OM_E_PT_ECP_INVALID_METADATA|O processador de ficheiros .cab externos detetou metadados que não são válidos.|
|**0x80cf4033**|OM_E_PT_ECP_FAILURE_TO_EXTRACT_DIGEST|Não foi possível extrair o resumo de ficheiro de um ficheiro .cab externo.|
|**0x80cf4034**|OM_E_PT_ECP_FAILURE_TO_DECOMPRESS_CAB_FILE|Não foi possível descomprimir um ficheiro .cab externo.|
|**0x80cf4035**|OM_E_PT_ECP_FILE_LOCATION_ERROR|O processador de ficheiros .cab externos não conseguiu obter a localização dos ficheiros.|
|**0x80cf4FFF**|OM_E_PT_UNEXPECTED|Ocorreu um erro de comunicação que não é abrangido por outro código de erro **OM_E_PT_&#42;**.|
|**0x80cf6001**|OM_E_DM_URLNOTAVAILABLE|Não foi possível concluir uma operação do gestor de transferências porque o ficheiro pedido não tem um URL.|
|**0x80cf6002**|OM_E_DM_INCORRECTFILEHASH|Não foi possível concluir uma operação do gestor de transferências porque o resumo do ficheiro não foi reconhecido.|
|**0x80cf6003**|OM_E_DM_UNKNOWNALGORITHM|Não foi possível concluir uma operação do gestor de transferências porque os metadados do ficheiro pediram um algoritmo hash não reconhecido.|
|**0x80cf6005**|OM_E_DM_NONETWORK|Não foi possível concluir uma operação do gestor de transferências porque a ligação de rede não estava disponível.|
|**0x80cf6007**|OM_E_DM_NOTDOWNLOADED|A atualização não foi transferida.|
|**0x80cf6008**|OM_E_DM_FAILTOCONNECTTOBITS|Uma operação do gestor de transferências falhou porque o gestor de transferências não conseguiu ligar o Serviço de Transferência Inteligente em Segundo Plano (BITS).|
|**0x80cf6009**|OM_E_DM_BITSTRANSFERERROR|Uma operação do gestor de transferências falhou porque ocorreu um erro não especificado numa transferência do Serviço de Transferência Inteligente em Segundo Plano (BITS).|
|**0x80cf600a**|OM_E_DM_DOWNLOADLOCATIONCHANGED|É necessário reiniciar uma transferência porque a localização da origem da transferência foi alterada.|
|**0x80cf600B**|OM_E_DM_CONTENTCHANGED|É necessário reiniciar uma transferência porque o conteúdo da atualização foi alterado numa nova revisão.|
|**0x80cf6FFF**|OM_E_DM_UNEXPECTED|Ocorreu um erro do gestor de transferências que não é abrangido por outro código de erro **OM_E_DM_&#42;**.|
|**0x80cf7003**|OM_E_INVALID_EVENT_PAYLOAD|Foi especificada uma payload do evento que não é válida.|
|**0x80cf7004**|OM_E_INVALID_EVENT_PAYLOADSIZE|O tamanho da payload do evento submetido não é válido.|
|**0x80cf7005**|OM_E_SERVICE_NOT_REGISTERED|O serviço não está registado.|
|**0x80cf8000**|OM_E_DS_SHUTDOWN|Uma operação falhou porque o agente está a ser encerrado.|
|**0x80cf8001**|OM_E_DS_INUSE|Uma operação falhou porque o arquivo de dados estava em utilização.|
|**0x80cf8002**|OM_E_DS_INVALID|Os estados atual e esperado do arquivo de dados não correspondem.|
|**0x80cf8003**|OM_E_DS_TABLEMISSING|Existe uma tabela em falta no arquivo de dados.|
|**0x80cf8004**|OM_E_DS_TABLEINCORRECT|O arquivo de dados contém uma tabela com colunas inesperadas.|
|**0x80cf8005**|OM_E_DS_INVALIDTABLENAME|Não foi possível abrir uma tabela porque a tabela não se encontra no arquivo de dados.|
|**0x80cf8006**|OM_E_DS_BADVERSION|As versões atual e esperada do arquivo de dados não correspondem.|
|**0x80cf8007**|OM_E_DS_NODATA|As informações pedidas não se encontram no arquivo de dados.|
|**0x80cf8008**|OM_E_DS_MISSINGDATA|O arquivo de dados não dispõe de informações necessárias ou contém um valor nulo numa coluna de tabela que necessita de um valor não nulo.|
|**0x80cf8009**|OM_E_DS_MISSINGREF|O arquivo de dados não dispõe de informações necessárias ou contém uma referência a termos de licenciamento, ficheiro, propriedade localizada ou linha interligada em falta.|
|**0x80cf800A**|OM_E_DS_UNKNOWNHANDLER|A atualização não foi processada porque o respetivo processador não foi reconhecido.|
|**0x80cf800B**|OM_E_DS_CANTDELETE|A atualização não foi eliminada porque ainda é referenciada por um ou mais serviços.|
|**0x80cf800C**|OM_E_DS_LOCKTIMEOUTEXPIRED|Não foi possível bloquear a secção do arquivo de dados dentro do prazo atribuído.|
|**0x80cf800E**|OM_E_DS_ROWEXISTS|A linha não foi adicionada porque já existe uma linha com a mesma chave primária.|
|**0x80cf800F**|OM_E_DS_STOREFILELOCKED|Não foi possível inicializar o arquivo de dados porque foi bloqueado por outro processo.|
|**0x80cf8010**|OM_E_DS_CANNOTREGISTER|O arquivo de dados não pode ser registado no processo atual através de COM.|
|**0x80cf8011**|OM_E_DS_UNABLETOSTART|Uma operação não conseguiu criar um objeto de arquivo de dados noutro processo.|
|**0x80cf8013**|OM_E_DS_DUPLICATEUPDATEID|O servidor enviou a mesma atualização ao cliente com dois IDs de revisão diferentes.|
|**0x80cf8014**|OM_E_DS_UNKNOWNSERVICE|Não foi possível concluir uma operação porque o serviço não se encontra no arquivo de dados.|
|**0x80cf8015**|OM_E_DS_SERVICEEXPIRED|Não foi possível concluir uma operação porque o registo do serviço expirou.|
|**0x80cf8016**|OM_E_DS_DECLINENOTALLOWED|Foi recusado um pedido para ocultar uma atualização porque se trata de uma atualização obrigatória ou porque esta foi implementada com um prazo.|
|**0x80cf8017**|OM_E_DS_TABLESESSIONMISMATCH|Uma tabela não foi fechada porque não está associada à sessão.|
|**0x80cf8018**|OM_E_DS_SESSIONLOCKMISMATCH|Uma tabela não foi fechada porque não está associada à sessão.|
|**0x80cf8019**|OM_E_DS_NEEDWINDOWSSERVICE|O pedido para remover ou anular o registo do serviço foi recusado porque se trata de um serviço incorporado ou porque as Atualizações Automáticas não podem reverter para outro serviço.|
|**0x80cf801A**|OM_E_DS_INVALIDOPERATION|O pedido foi recusado porque a operação não é permitida.|
|**0x80cf801B**|OM_E_DS_SCHEMAMISMATCH|O esquema do arquivo de dados atual e o esquema de uma tabela num documento XML de cópia de segurança não correspondem.|
|**0x80cf801C**|OM_E_DS_RESETREQUIRED|É necessário repor a sessão do arquivo de dados. Liberte a sessão e tente novamente com uma nova sessão.|
|**0x80cf801D**|OM_E_DS_IMPERSONATED|Não foi possível concluir uma operação do arquivo de dados porque foi pedida com uma identidade representada.|
|**0x80cf8FFF**|OM_E_DS_UNEXPECTED|Ocorreu um erro do arquivo de dados que não é abrangido por outro código **OM_E_DS_&#42;**.|
|**0x80cfA000**|OM_E_AU_NOSERVICE|As Atualizações Automáticas não conseguiram dar resposta aos pedidos recebidos.|
|**0x80cfA004**|OM_E_AU_PAUSED|As Atualizações Automáticas não conseguiram processar os pedidos recebidos porque estavam em pausa.|
|**0x80cfA005**|OM_E_AU_NO_REGISTERED_SERVICE|Não está registado nenhum serviço não gerido nas Atualizações Automáticas.|
|**0x80cfA006**|OM_E_AU_DETECT_SVCID_MISMATCH|O serviço predefinido registado nas Atualizações Automáticas foi alterado durante a pesquisa.|
|**0x80cfA007**|OM_E_AU_ALREADY_PROMPTING_FOR_REBOOT|As Atualizações Automáticas já estão a pedir ao utilizador para reiniciar.|
|**0x80cfAFFF**|OM_E_AU_UNEXPECTED|Ocorreu um erro das Atualizações Automáticas que não é abrangido por outro código **OM_E_AU &#42;**.|
|**0x80cfE001**|OM_E_EE_UNKNOWN_EXPRESSION|Não foi possível concluir uma operação do avaliador de expressões porque uma expressão não foi reconhecida.|
|**0x80cfE002**|OM_E_EE_INVALID_EXPRESSION|Não foi possível concluir uma operação do avaliador de expressões porque uma expressão não era válida.|
|**0x80cfE003**|OM_E_EE_MISSING_METADATA|Não foi possível concluir uma operação do avaliador de expressões porque uma expressão contém um número incorreto de nós de metadados.|
|**0x80cfE004**|OM_E_EE_INVALID_VERSION|Não foi possível concluir uma operação do avaliador de expressões porque a versão dos dados de expressão serializados não é válida.|
|**0x80cfE005**|OM_E_EE_NOT_INITIALIZED|Não foi possível inicializar o avaliador de expressões.|
|**0x80cfE006**|OM_E_EE_INVALID_ATTRIBUTEDATA|Não foi possível concluir uma operação do avaliador de expressões porque um atributo não é válido.|
|**0x80cfE007**|OM_E_EE_CLUSTER_ERROR|Não foi possível concluir uma operação do avaliador de expressões porque não foi possível determinar o estado cluster do computador.|
|**0x80cfEFFF**|OM_E_EE_UNEXPECTED|Ocorreu um erro do avaliador de expressões que não é abrangido por outro código de erro **OM_E_EE_&#42;**.|
|**0x80cfF001**|OM_E_REPORTER_EVENTCACHECORRUPT|O ficheiro de cache de eventos estava danificado.|
|**0x80cfF002**|OM_E_REPORTER_EVENTNAMESPACEPARSEFAILED|Não foi possível analisar o XML no descritor do espaço de nomes do evento.|
|**0x80cfF003**|OM_E_INVALID_EVENT|O XML no descritor do espaço de nomes do evento não é válido.|
|**0x80cfF004**|OM_E_SERVER_BUSY|O servidor rejeitou um evento porque o servidor estava demasiado ocupado.|
|**0x80cfFFFF**|OM_E_REPORTER_UNEXPECTED|Ocorreu um erro de relatório que não é abrangido por outro código de erro.|
|**0x80af0005**|OMC_E_INSTALL_NOT_ALLOWED_REBOOT_REQUIRED|A instalação falhou porque existe um reinício obrigatório pendente.|
|**0x80af0006**|OMC_E_DOWNLOAD_CANCELLED|A transferência foi cancelada.|

## <a name="windows-7-based-computers-with-lots-of-superseded-updates-stop-reporting-to-the-microsoft-intune-console"></a>Computadores baseados no Windows 7 com muitas atualizações substituídas deixam de reportar na consola do Microsoft Intune
**Problema**: poderá encontrar uma situação em que os clientes do Microsoft Intune se deparam com um ou mais dos seguintes sintomas:
- Param subitamente de reportar na consola de administração do Microsoft Intune.  
- Registam uma elevada utilização da CPU.
- As aplicações são instaladas lentamente quando são instaladas através do portal do Intune.
- O Microsoft Intune Center aciona o seguinte erro: *Ocorreu um erro ao atualizar o seu computador. Erro encontrado: código 0x800705b4*.
- O campo de estado na Consola de Administração do Intune > Grupos > Todos os Dispositivos apresenta: *Um ou mais agentes instalados neste computador têm erros. As informações para este computador podem não ser exatas ou atualizadas*.

Este problema pode ocorrer se as atualizações substituídas (atualizações que foram substituídas por outra atualização) não foram recusadas durante um período prolongado. Durante determinados processos, como a instalação de uma aplicação, o Windows verifica todas as atualizações substituídas em sequência, para que as atualizações e as respetivas sucessoras possam ser mapeadas corretamente. Se a lista de atualizações substituídas ficar demasiado grande, esta tarefa de verificação pode causar uma elevada utilização da CPU devido à carga de processamento e ao tempo necessário. Este problema afeta principalmente os clientes com o Windows 7 devido ao elevado número de atualizações substituídas que estão disponíveis para o Windows 7. O Windows 8 e os sistemas operativos posteriores não têm tantas atualizações substituídas disponíveis e, por conseguinte, não estão tão suscetíveis a este problema.

**Resolução**: para resolver este problema, siga estes passos:
1. Inicie sessão na [consola de administração do Intune](https://manage.microsoft.com).
2. Selecione **Atualizações** > **Todas as Atualizações**.
3. Utilize a opção de filtro na barra de ferramentas superior para filtrar as atualizações substituídas.
4. Rejeite todas as atualizações substituídas que possam ser aplicadas ao Windows 7 ou a aplicações (por exemplo, o Microsoft Office) que foram instaladas nos clientes afetados.
5. Reinicie os clientes afetados.

Além disso, se estiver a executar o Windows 7, certifique-se de que tem a seguinte atualização instalada:[3050265 Cliente do Windows Update para o Windows 7: junho de 2015](https://support.microsoft.com/kb/3050265).

### <a name="next-steps"></a>Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

