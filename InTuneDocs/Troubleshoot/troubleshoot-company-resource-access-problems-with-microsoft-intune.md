---
title: "Resolução de problemas de acesso aos recursos da empresa | Microsoft Intune"
description: 
keywords: 
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 40622ced-6029-4abf-873e-b51d2b51934c
ms.reviewer: jeffgilb
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c22ddd554928b394e14742b8ba7d583d390d1c44
ms.openlocfilehash: ed14e92d48a2604d16ceee8b844ae5cc0c45f051


---

# Resolução de problemas de acesso aos recursos da empresa com o Microsoft Intune
Utilize os códigos de estado e de erro deste tópico para obter ajuda para resolver problemas se uma ação do Microsoft Intune devolver um código de erro.

Se estas informações não resolverem o problema, veja [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md) para ver mais formas de ajuda.

## Códigos de estado para dispositivos Windows geridos por MDM

|Código de estado|Mensagem de erro|O que fazer|
|---------------|-----------------|--------------|
|10 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Instalação em curso||
|20 (APP_CI_ENFORCEMENT_IN_PROGRESS_WAITING_CONTENT)|A aguardar conteúdo||
|30 (APP_CI_ENFORCEMENT_ERROR_RETRIEVING_CONTENT)|A obter conteúdo|Motivo Provável: o estado de tarefa 30 indica que a transferência de uma aplicação do utilizador falhou.<br /><br />As causas prováveis para tal podem ser:<br /><br />O dispositivo perdeu a conectividade à Internet enquanto a transferência estava em curso.<br /><br />O certificado emitido para o dispositivo no momento da inscrição pode ter expirado.<br /><br />Mitigação:<br /><br />Inicie a aplicação Aplicações da Empresa a partir do Painel de Controlo do dispositivo para confirmar que o certificado do dispositivo não expirou; caso tenha expirado, terá de reinscrevê-lo.<br /><br />Confirme se o dispositivo está ligado à Internet e tente pedir novamente a aplicação.|
|40 (APP_CI_ENFORCEMENT_IN_PROGRESS_CONTENT_DOWNLOADED)|Transferência de conteúdo concluída||
|50 (APP_CI_ENFORCEMENT_IN_PROGRESS_INSTALLING)|Instalação em curso||
|60 (APP_CI_ENFORCEMENT_ERROR_INSTALLING)|Instalação Ocorreu um erro|A instalação da aplicação falhou após a transferência.<br /><br />O certificado com assinatura de código com o qual a aplicação foi assinada não está presente no dispositivo.<br /><br />Uma dependência da arquitetura da qual a aplicação depende não está instalada no dispositivo.<br /><br />Verifique se o certificado com assinatura de código com o qual a aplicação foi assinada está presente no dispositivo e confirme junto do administrador se esse certificado foi direcionado para todos os dispositivos Windows RT inscritos na empresa.<br /><br />No caso de a falha da instalação se dever a uma dependência de arquitetura em falta, o administrador terá de publicar novamente a aplicação ao empacotar a arquitetura juntamente com o pacote de aplicações.<br /><br />O pacote de aplicações transferido não é um pacote válido, pode ter sido danificado ou pode não ser compatível com a versão do SO no dispositivo.|
|70 (APP_CI_ENFORCEMENT_SUCCEEDED)|Instalação Com Êxito||
|80 (APP_CI_ENFORCEMENT_IN_PROGRESS)|Desinstalação em curso||
|90 (APP_CI_ENFORCEMENT_ERROR)|Ocorreu um erro de desinstalação||
|100 (APP_CI_ENFORCEMENT_SUCCEEDED)|Desinstalação Com Êxito||
|110 (APP_CI_ENFORCEMENT_ERROR)|Erro de correspondência do hash de conteúdo||
|120 (APP_CI_ENFORCEMENT_ERROR)|SLK/sideload não ativado||
|130 (APP_CI_ENFORCEMENT_ERROR)|Falha na instalação da licença MSADP||
|Sem estado (APP_CI_ENFORCEMENT_UNKNOWN)|n/d|O estado é atualmente desconhecido.|

## Acesso a recursos da empresa (erros comuns)

|Código de estado|Código de erro hexadecimal|Mensagem de erro|
|---------------|--------------------------|-----------------|
|-2016281101|0x87D1FDF3|Pedido de CRP de MDM não encontrado|
|-2016281102|0x87D1FDF2|URL de NDES não encontrado|
|-2016281103|0x87D1FDF1|Informações do certificado de CRP de MDM não encontradas|
|-2016281104|0x87D1FDF0|Informações do certificado de CI de MDM não encontradas|
|-2016281105|0x87D1FDEF|Falha ao avaliar a Regra|
|-2016281106|0x87D1FDEE|Não aplicável porque perdeu na resolução de conflito|
|-2016281107|0x87D1FDED|Definição de origem de deteção não suportada|
|-2016281108|0x87D1FDEC|Definição referenciada não localizada no CI|
|-2016281109|0x87D1FDEB|Falha ao concluir a conversão do tipo de dados|
|-2016281110|0x87D1FDEA|  Parâmetro inválido na definição de CIM|
|-2016281111|0x87D1FDE9|Não aplicável a este dispositivo|
|-2016281112|0x87D1FDE8|Falha na remediação|
|-2016330905|0x87D13B67|O estado da aplicação é desconhecido|
|-2016330906|0x87D13B66|A aplicação é gerida, mas foi removida pelo utilizador|
|-2016330907|0x87D13B65|O dispositivo está a resgatar o código de resgate|
|-2016330908|0x87D13B64|A instalação da aplicação falhou|
|-2016330909|0x87D13B63|O utilizador rejeitou a oferta para atualizar a aplicação|
|-2016330910|0x87D13B62|O utilizador rejeitou a oferta para instalar a aplicação|
|-2016330911|0x87D13B61|O utilizador instalou a aplicação antes de a instalação da aplicação gerida ter ocorrido|
|-2016330912|0x87D13B60|A aplicação está agendada para instalação, mas precisa de um código de resgate para concluir a transação|
|-2016341109|0x87D1138B|O dispositivo iOS devolveu um erro|
|-2016341110|0x87D1138A|O dispositivo iOS rejeitou o comando devido a um formato incorreto|
|-2016341111|0x87D11389|O dispositivo iOS devolveu um estado de inatividade inesperado|
|-2016341112|0x87D11388|O dispositivo iOS está ocupado neste momento|

## Erros devolvidos por dispositivos iOS

|Código de estado|Código de erro hexadecimal|Mensagem de erro|
|---------------|--------------------------|-----------------|
|-2016299111|0x87D1B799|Erro interno|
|-2016299112|0x87D1B798|Erro interno|
|-2016300111|0x87D1B3B1|36001: (erro interno)|
|-2016300112|0x87D1B3B0|36000: telemóvel já configurado|
|-2016301110|0x87D1AFCA|35002: vários tipos de letra num único payload|
|-2016301111|0x87D1AFC9|35001: falha ao instalar o tipo de letra|
|-2016301112|0x87D1AFC8|35000: dados de tipo de letra inválidos|
|-2016302109|0x87D1ABE3|34003: nome principal Kerberos inválido|
|-2016302110|0x87D1ABE2|34002: nome principal Kerberos em falta|
|-2016302111|0x87D1ABE1|34001: padrão de correspondência de URL inválido|
|-2016302112|0x87D1ABE0|34000: padrão de correspondência de identificador de aplicação inválido|
|-2016304112|0x87D1A410|32000: demasiadas aplicações|
|-2016305111|0x87D1A029|31001: não é possível aplicar as definições|
|-2016305112|0x87D1A028|31000: não é possível aplicar a credencial|
|-2016306111|0x87D19C41|30001: limite de tempo excedido|
|-2016306112|0x87D19C40|30000: falha na autenticação|
|-2016307109|0x87D1985B|29003: dados de certificado incorretos|
|-2016307110|0x87D1985A|29002:|
|-2016307111|0x87D19859|29001:|
|-2016307112|0x87D19858|29000: dispositivo não supervisionado|
|-2016308110|0x87D19472|28002: não é possível definir imagem de fundo|
|-2016308111|0x87D19471|28001: imagem de fundo incorreta|
|-2016308112|0x87D19470|28000: item desconhecido|
|-2016310111|0x87D18CA1|26001: encriptação de nível de ficheiro não suportada|
|-2016310112|0x87D18CA0|26000: encriptação de nível de bloco não suportada|
|-2016311110|0x87D188BA|25002: não é possível remover|
|-2016311111|0x87D188B9|25001: não é possível instalar|
|-2016311112|0x87D188B8|25000: perfil incorreto|
|-2016312109|0x87D184D3|24003: perfil final incorreto|
|-2016312110|0x87D184D2|24002: payload de identidade incorreto|
|-2016312111|0x87D184D1|24001: não é possível assinar dicionário de atributos|
|-2016312112|0x87D184D0|24000: não é possível criar dicionário de atributos|
|-2016313110|0x87D180EA|23002: certificado de servidor inválido|
|-2016313111|0x87D180E9|23001: resposta de servidor incorreta|
|-2016313112|0x87D180E8|23000: identidade incorreta|
|-2016314099|0x87D17D0D|22013: resposta PKIOperation inválida|
|-2016314100|0x87D17D0C|22012: não é possível armazenar CACertificate|
|-2016314101|0x87D17D0B|22011: não é possível gerar CSR|
|-2016314102|0x87D17D0A|22010: não é possível armazenar identidade temporária|
|-2016314103|0x87D17D09|22009: não é possível criar identidade temporária|
|-2016314104|0x87D17D08|22009: não é possível criar identidade temporária|
|-2016314105|0x87D17D07|22007: certificado assinado inválido|
|-2016314106|0x87D17D06|22006: CACaps Insuficiente|
|-2016314107|0x87D17D05|22005: erro de rede|
|-2016314108|0x87D17D04|22004: configuração de certificado não suportada|
|-2016314109|0x87D17D03|22003: RAResponse inválida|
|-2016314110|0x87D17D02|22003: CAResponse inválida|
|-2016314111|0x87D17D01|22001: não é possível gerar par de chaves|
|-2016314112|0x87D17D00|22000: utilização de chave inválida|
|-2016315105|0x87D1791F|21007: não é possível verificar conta|
|-2016315106|0x87D1791E|21006: não é possível desencriptar certificado|
|-2016315107|0x87D1791D|21005: conta não exclusiva|
|-2016315108|0x87D1791C|21004: não é possível criar conta|
|-2016315109|0x87D1791B|21003: nenhum nome de anfitrião|
|-2016315110|0x87D1791A|21002: não é possível cumprir a política de encriptação do servidor|
|-2016315111|0x87D17919|21001: não é possível cumprir a política do servidor|
|-2016315112|0x87D17918|21000: não é possível obter política do servidor|
|-2016316110|0x87D17532|20002: conta não exclusiva|
|-2016316111|0x87D17531|20001: nenhum nome de anfitrião|
|-2016316112|0x87D17530|20000: não é possível criar conta|
|-2016317110|0x87D1714A|19002: conta não exclusiva|
|-2016317111|0x87D17149|19001: nenhum nome de anfitrião|
|-2016317112|0x87D17148|19000: não é possível criar conta|
|-2016318110|0x87D16D62|18002: credenciais inválidas|
|-2016318111|0x87D16D61|18001: anfitrião inacessível|
|-2016318112|0x87D16D60|18000: erro desconhecido|
|-2016319110|0x87D1697A|17002: conta não exclusiva|
|-2016319111|0x87D16979|17001: nenhum nome de anfitrião|
|-2016319112|0x87D16978|17000: não é possível criar conta|
|-2016320110|0x87D16592|16002: conta não exclusiva|
|-2016320111|0x87D16591|16001: nenhum nome de anfitrião|
|-2016320112|0x87D16590|16000: não é possível criar subscrição|
|-2016321109|0x87D161AB|15003: certificado inválido|
|-2016321110|0x87D161AA|15002: não é possível bloquear configuração de rede|
|-2016321111|0x87D161A9|15001: não é possível remover VPN|
|-2016321112|0x87D161A8|15000: não é possível instalar VPN|
|-2016322110|0x87D15DC2|14002: a configuração de nuvem já existe|
|-2016322111|0x87D15DC1|14001: dispositivo bloqueado|
|-2016322112|0x87D15DC0|14000: campo inválido|
|-2016323107|0x87D159DD|13005: não é possível configurar proxy|
|-2016323108|0x87D159DC|13004: não é possível configurar EAP|
|-2016323109|0x87D159DB|13003: não é possível criar configuração Wi-Fi|
|-2016323110|0x87D159DA|13002: palavra-passe necessária|
|-2016323111|0x87D159D9|13001: nome de utilizador necessário|
|-2016323112|0x87D159D8|13000: não é possível instalar|
|-2016324070|0x87D1561A|12042: código de região desconhecido|
|-2016324071|0x87D15619|12041: código de idioma desconhecido|
|-2016324072|0x87D15618|12040: início de sessão na loja iTunes necessário|
|-2016324073|0x87D15617|12039: (não utilizado)|
|-2016324074|0x87D15616|12038: aplicação não gerida|
|-2016324075|0x87D15615|12037: código de resgate inválido|
|-2016324076|0x87D15614|12036: não é possível remover a aplicação no estado atual|
|-2016324077|0x87D15613|12035: não é possível comprar a aplicação|
|-2016324078|0x87D15612|12034: URL não é HTTPS|
|-2016324079|0x87D15611|12033: manifesto inválido|
|-2016324080|0x87D15610|12032: demasiadas aplicações no manifesto|
|-2016324081|0x87D1560F|12031: instalação de aplicações desativada|
|-2016324082|0x87D1560E|12030: URL inválido|
|-2016324083|0x87D1560D|12029: aplicação não gerida|
|-2016324084|0x87D1560C|12028: não aguardar pelo resgate|
|-2016324085|0x87D1560B|12027: não é uma aplicação|
|-2016324086|0x87D1560A|12026: aplicação já em fila de espera|
|-2016324087|0x87D15609|12025: aplicação já instalada|
|-2016324088|0x87D15608|12024: não foi possível validar o manifesto da aplicação|
|-2016324089|0x87D15607|12023: não foi possível validar ID da aplicação|
|-2016324090|0x87D15606|12022: tópico inválido|
|-2016324091|0x87D15605|12021: tipo de pedido inválido|
|-2016324092|0x87D15604|12020: não autorizado pelo servidor|
|-2016324093|0x87D15603|12019: não é possível copiar segredo de caução|
|-2016324094|0x87D15602|12018: não é possível copiar dados keybag de caução|
|-2016324095|0x87D15601|12017: não é possível criar keybag de caução|
|-2016324096|0x87D15600|12016: identidade em falta|
|-2016324097|0x87D155FF|12015: não é possível obter token push|
|-2016324098|0x87D155FE|12014: perfil de aprovisionamento não gerido|
|-2016324099|0x87D155FD|12013: perfil não gerido|
|-2016324100|0x87D155FC|12012: erro de correspondência de substituição de MDM|
|-2016324101|0x87D155FB|12011: configuração de MDM inválida|
|-2016324102|0x87D155FA|12010: erro de inconsistência interno|
|-2016324103|0x87D155F9|12009: perfil de substituição inválido|
|-2016324104|0x87D155F8|12008: formato de pedido incorreto|
|-2016324105|0x87D155F7|12007: não autorizado|
|-2016324106|0x87D155F6|12006: redirecionamento recusado|
|-2016324107|0x87D155F5|12005: não é possível encontrar certificado|
|-2016324108|0x87D155F4|12004: certificado push inválido|
|-2016324109|0x87D155F3|12003: resposta de desafio inválida|
|-2016324110|0x87D155F2|12002: não é possível dar entrada|
|-2016324111|0x87D155F1|12001: várias instâncias MDM|
|-2016324112|0x87D155F0|12000: direitos de acesso inválidos|
|-2016325111|0x87D15209|11001: APN personalizado já instalado|
|-2016325112|0x87D15208|11000: não é possível instalar APN|
|-2016326111|0x87D14E21|10001: signatário inválido|
|-2016326112|0x87D14E20|10000: não é possível instalar predefinições|
|-2016327106|0x87D14A3E|9006: certificado não é uma identidade|
|-2016327107|0x87D14A3D|9005: formato de certificado incorreto|
|-2016327108|0x87D14A3C|9004: não é possível armazenar certificado de raiz|
|-2016327109|0x87D14A3B|9003: não é possível armazenar dados WAPI|
|-2016327110|0x87D14A3A|9002: não é possível armazenar certificado|
|-2016327111|0x87D14A39|9001: demasiados certificados num payload|
|-2016327112|0x87D14A38|9000: palavra-passe inválida|
|-2016328112|0x87D14650|8000: não é possível instalar Web Clip|
|-2016329105|0x87D1426F|7007: conta SMTP configurada incorretamente|
|-2016329106|0x87D1426E|7006: conta POP configurada incorretamente|
|-2016329107|0x87D1426D|7005: conta IMAP configurada incorretamente|
|-2016329108|0x87D1426C|7004: certificado SMIME incorreto|
|-2016329109|0x87D1426B|7003: certificado SMIME não encontrado|
|-2016329110|0x87D1426A|7002: ocorreu um erro desconhecido durante a validação|
|-2016329111|0x87D14269|7001: credenciais inválidas|
|-2016329112|0x87D14268|7000: anfitrião inacessível|
|-2016330110|0x87D13E82|6002: não é possível criar consulta|
|-2016330111|0x87D13E81|6001: cadeia de carateres vazia|
|-2016330112|0x87D13E80|6000: erro de sistema de Keychain|
|-2016331097|0x87D13AA7|5015: não é possível definir período de tolerância|
|-2016331098|0x87D13AA6|5014: não é possível definir código de acesso|
|-2016331099|0x87D13AA5|5013: não é possível limpar o código de acesso|
|-2016331100|0x87D13AA4|5012: (não utilizado)|
|-2016331101||5011: código de acesso incorreto|
|-2016331102||5010: dispositivo bloqueado|
|-2016331103|0x87D13AA4|5009: (não utilizado)|
|-2016331104|0x87D13AA0|5008: código de acesso demasiado recente|
|-2016331105|0x87D13A9F|5007: código de acesso expirado|
|-2016331106|0x87D13AA3|5006: código de acesso necessita de carateres alfabéticos|
|-2016331107|0x87D13A9D|5005: código de acesso necessita de número|
|-2016331108|0x87D13A9C|5004: código de acesso com carateres ascendentes/descendentes|
|-2016331109|0x87D13A9B|5003: código de acesso com carateres repetidos|
|-2016331110|0x87D13A9A|5002: número insuficiente de carateres complexos|
|-2016331111|0x87D13A99|5001: número insuficiente de carateres exclusivos|
|-2016331112|0x87D13A98|5000: código de acesso demasiado curto|
|-2016332093|0x87D136C3|4019: múltiplos payloads de Bloqueio de Aplicação|
|-2016332094|0x87D136C2|4018: múltiplos payloads APN ou Móvel|
|-2016332095|0x87D136C1|4017: múltiplos payloads HTTPProxy globais|
|-2016332096|0x87D136C0|4016: (erro interno)|
|-2016332097|0x87D136BF|4015: perfil de substituição não contém um payload MDM|
|-2016332098|0x87D136BE|4014: nenhuma identidade de dispositivo disponível|
|-2016332099|0x87D136BD|4013: falha na atualização|
|-2016332100|0x87D136BC|4012: perfil não atualizável|
|-2016332101|0x87D136BB|4011: perfil final não é um perfil de configuração|
|-2016332102|0x87D136BA|4010: perfil atualizado não tem o mesmo identificador|
|-2016332103|0x87D136B9|4009: dispositivo bloqueado|
|-2016332104|0x87D136B8|4008: certificados sem correspondência|
|-2016332105|0x87D136B7|4007: formato de ficheiro não reconhecido|
|-2016332106|0x87D136B6|4006: data de remoção do perfil está no passado|
|-2016332107|0x87D136B5|4005: código de acesso não está em conformidade|
|-2016332108|0x87D136B4|4004: utilizador cancelou instalação|
|-2016332109|0x87D136B3|4003: perfil não colocado em fila de espera para instalação|
|-2016332110|0x87D136B2|4002: UUID duplicado|
|-2016332111|0x87D136B1|4001: falha na instalação|
|-2016332112|0x87D136B0|4000: não é possível analisar perfil|
|-2016333111|0x87D132C9|3001: deteção de comparação de valor inconsistente (erro interno)|
|-2016333112|0x87D132C8|3000: deteção de restrição inconsistente (erro interno)|
|-2016334108|0x87D12EE4|2004: valor de campo não suportado|
|-2016334109|0x87D12EE3|2003: tipo de dados incorreto no campo|
|-2016334110|0x87D12EE2|2002: campo obrigatório em falta|
|-2016334111|0x87D12EE1|2001: versão de payload não suportada|
|-2016334112|0x87D12EE0|2000: formato de Payload incorreto|
|-2016335102|0x87D12B02|1010: valor de campo não suportado|
|-2016335103|0x87D12B01|1009: falha na instalação do perfil|
|-2016335104|0x87D12B00|1008: identificadores de payload não exclusivos|
|-2016335105|0x87D12AFF|1007: UUIDs não exclusivos|
|-2016335106|0x87D12AFE|1006: não é possível desencriptar|
|-2016335107|0x87D12AFD|1005: perfil vazio|
|-2016335108|0x87D12AFC|1004: assinatura incorreta|
|-2016335109|0x87D12AFB|1003: tipo de dados incorreto no campo|
|-2016335110|0x87D12AFA|1002: campo obrigatório em falta|
|-2016335111|0x87D12AF9|1001: versão de perfil não suportada|
|-2016335112|0x87D12AF8|1000: formato de perfil incorreto|

## Códigos de resposta OMA

|Código de estado|Código de erro hexadecimal|Mensagem de erro|
|---------------|--------------------------|-----------------|
|-2016344008|0x87D10838|(1404): Acesso negado ao certificado|
|-2016344009|0x87D10837|(1403): Certificado não encontrado|
|-2016344010|0x87D10836|DCMO(1402): A operação falhou|
|-2016344011|0x87D10835|DCMO(1401): O Utilizador optou por não aceitar a operação quando solicitado|
|-2016344012|0x87D10834|DCMO(1400): Erro do cliente|
|-2016344108|0x87D107D4|DCMO(1204): A Capacidade de Dispositivo está desativada e o Utilizador está autorizado a reativá-la|
|-2016344109|0x87D107D3|DCMO(1203): A Capacidade de Dispositivo está desativada e o Utilizador não está autorizado a reativá-la|
|-2016344110|0x87D107D2|DCMO(1202): A operação de ativação é executada com êxito, mas a Capacidade de Dispositivo está atualmente desligada|
|-2016344111|0xF3FB4D95|DCMO(1201): A operação de ativação é executada com êxito e a Capacidade de Dispositivo está atualmente ligada|
|-2016344112|0x87D107D0|DCMO(1200): A operação foi efetuada com êxito|
|-2016345595|0x87D10205|Syncml(517): A resposta a um comando atómico era demasiado extensa para caber numa única mensagem.|
|-2016345596|0x87D10204|Syncml(516): O comando encontrava-se num elemento Atómico e ocorreu uma falha no elemento Atómico. Este comando não foi revertido com êxito.|
|-2016345598|0x87D10202|Syncml(514): O comando SyncML não foi concluído com êxito, uma vez que a operação já tinha sido cancelada antes do processamento do comando.|
|-2016345599|0x87D10201|Syncml(513): O destinatário não suporta ou recusa-se a suportar a versão especificada do Protocolo de Sincronização de SyncML utilizada na Mensagem de pedido de SyncML.|
|-2016345600|0x87D10200|Syncml(512): Ocorreu um erro da aplicação durante a sessão de sincronização.|
|-2016345601|0x87D101FF|Syncml(511): Ocorreu um erro grave no servidor durante o processamento do pedido.|
|-2016345602|0x87D101FE|Syncml(510): Ocorreu um erro ao processar o pedido. O erro está relacionado com uma falha no arquivo de dados do destinatário.|
|-2016345603|0x87D101FD|Syncml(509): Reservado para utilização futura.|
|-2016345604|0x87D101FC|Syncml(508): Ocorreu um erro que exige uma atualização do estado de sincronização atual do cliente com o servidor.|
|-2016345605|0x87D101FB|Syncml(507): O erro causou a falha de todos os comandos SyncML num tipo de elemento Atómico.|
|-2016345606|0x87D101FA|Syncml(506): Ocorreu um erro da aplicação durante o processamento do pedido.|
|-2016345607|0x87D101F9|Syncml(505): O destinatário não suporta ou recusa-se a suportar a versão especificada do DTD de SyncML utilizada na Mensagem de pedido de SyncML.|
|-2016345608|=0x87D101F8|Syncml(504): O destinatário, ao atuar como gateway ou proxy, não recebeu uma resposta atempada do destinatário a montante especificado pelo URI (por exemplo, HTTP, FTP, LDAP) ou de qualquer outro destinatário auxiliar (por exemplo, DNS) ao qual necessitava de aceder para tentar satisfazer o pedido.|
|-2016345609|0x87D101F7|Syncml(503): O destinatário não consegue processar o pedido neste momento devido a uma sobrecarga temporária ou a manutenção do destinatário.|
|-2016345610|0x87D101F6|Syncml(502): O destinatário, ao atuar como gateway ou proxy, recebeu uma resposta inválida do destinatário a montante ao qual acedeu na tentativa de satisfazer o pedido.|
|-2016345611|0x87D101F5|Syncml(501): O destinatário não suporta o comando necessário para satisfazer o pedido.|
|-2016345612|0x87D101F4|Syncml(500): O destinatário detetou uma condição inesperada que o impediu de satisfazer o pedido|
|-2016345684|0x87D101AC|Syncml(428): Falha ao mover|
|-2016345685|0x87D101AB|Syncml(427): Não é possível eliminar o elemento principal porque contém elementos subordinados.|
|-2016345686|0x87D101AA|Syncml(426): Item parcial não aceite.|
|-2016345687|0x87D101A9|Syncml(425): Falha ao executar o comando solicitado porque o remetente não tem permissões de controlo de acesso (ACL, Access Control Permissions) adequadas em relação ao destinatário.|
|-2016345688|0x87D101A8|Syncml(424): O objeto em segmentos foi recebido, mas o tamanho do objeto recebido não correspondeu ao tamanho declarado no primeiro segmento.|
|-2016345689|0x87D101A7|Syncml(423): Falha ao executar o comando solicitado porque o item " Eliminado de Forma Recuperável" foi " Eliminado de Forma Definitiva" no servidor anteriormente.|
|-2016345690|0x87D101A6|Syncml(422): Falha ao executar o comando solicitado no servidor porque o scripting CGI no LocURI estava formado incorretamente.|
|-2016345691|0x87D101A5|Syncml(421): Falha ao executar o comando solicitado no servidor porque a gramática de pesquisa especificada era desconhecida.|
|-2016345692|0x87D101A4|Syncml(420): O destinatário não dispõe de mais espaço de armazenamento para os dados de sincronização restantes.|
|-2016345693|0x87D101A3|Syncml(419): O pedido do cliente criou um conflito que foi resolvido pelo comando prevalecente do servidor.|
|-2016345694|0x87D101A2|Syncml(418): Falha ao executar o comando Put ou Add solicitado porque o destino já existe.|
|-2016345695|0x87D101A1|Syncml(417): Falha momentânea ao executar o pedido; o originador deverá repetir o pedido mais tarde.|
|-2016345696|0x87D101A0|Syncml(416): Falha ao executar o pedido porque o tamanho especificado em bytes era demasiado grande.|
|-2016345697|0x87D1019F|Syncml(415): Tipo de suporte de dados ou formato não suportados.|
|-2016345698|0x87D1019E|Syncml(414): Falha ao executar o comando solicitado porque o URI de destino é demasiado extenso para a capacidade ou disponibilidade de processamento do destinatário.|
|-2016345699|0x87D1019D|Syncml(413): O destinatário está a recusar a execução do comando solicitado porque o item pedido excede a capacidade ou disponibilidade de processamento do destinatário.|
|-2016345700|0x87D1019C|Syncml(412): Falha ao executar o comando solicitado no destinatário porque estava incompleto ou formado incorretamente.|
|-2016345701|0x87D1019B|Syncml(411): O comando solicitado tem de ser acompanhado do tamanho em bytes ou da informação de comprimento no tipo de elemento Meta.|
|-2016345702|0x87D1019A|Syncml(410): O destino solicitado já não se encontra no destinatário e não é conhecido nenhum URI de reencaminhamento.|
|-2016345703|0x87D10199|Syncml(409): Falha ao executar o pedido devido a um conflito de atualização entre as versões dos dados no cliente e no servidor.|
|-2016345704|0x87D10198|Syncml(408): Não foi recebida uma mensagem esperada dentro do prazo atribuído.|
|-2016345705|0x87D10197|Syncml(407): Falha ao executar o comando solicitado porque o originador tem de disponibilizar a autenticação correta.|
|-2016345706|0x87D10196|Syncml(406): Falha ao executar o comando solicitado porque não era suportada uma funcionalidade opcional do pedido.|
|-2016345707|0x87D10195|Syncml(405): O comando solicitado não é permitido no destino.|
|-2016345708|0x87D10194|Syncml(404): O destino solicitado não foi localizado.|
|-2016345709|0x87D10193|Syncml(403): Falha ao executar o comando solicitado, mas o destinatário compreendeu o comando pretendido.|
|-2016345710|0x87D10192|Syncml(402): Falha ao executar o comando solicitado porque é necessário o pagamento adequado.|
|-2016345711|0x87D10191|Syncml(401): Falha ao executar o comando solicitado porque o requerente tem de disponibilizar a autenticação adequada.|
|-2016345712|0x87D10190|Syncml(400): Não foi possível executar o comando solicitado devido a sintaxe formada incorretamente no comando.|
|-2016345807|0x87D10131|Syncml(305): O destino solicitado tem de ser acedido através do URI de proxy especificado.|
|-2016345808|0x87D10130|Syncml(304): o comando SyncML solicitado não foi executado no destino.|
|-2016345809|0x87D1012F|Syncml(303): O destino solicitado pode estar localizado noutro URI.|
|-2016345810|0x87D1012E|Syncml(302): O destino solicitado foi movido temporariamente para outro URI.|
|-2016345811|0x87D1012D|Syncml(301): O destino solicitado tem um novo URI.|
|-2016345812|0x87D1012C|Syncml(300): O destino solicitado é uma das várias alternativas de destino solicitadas.|
|-2016345896|0x87D100D8|Syncml(216): O comando encontrava-se num elemento Atómico e ocorreu uma falha no elemento Atómico. Este comando foi revertido com êxito.|
|-2016345897|0x87D100D7|Syncml(215): Não foi executado um comando, como resultado da interação do utilizador, o qual optou por não aceitar a escolha.|
|-2016345898|0x87D100D6|Syncml(214): A operação foi cancelada. O comando SyncML foi concluído com êxito, mas não serão processados mais comandos na sessão.|
|-2016345899|0x87D100D5|Syncml(213): O item segmentado foi aceite e colocado na memória intermédia|
|-2016345900|0x87D100D4|Syncml(212): A autenticação foi aceite. Não é preciso realizar outras autenticações durante o restante período da sessão de sincronização. Este código de resposta só pode ser utilizado em resposta a um pedido no qual tenham sido fornecidas credenciais.|
|-2016345901|0x87D100D3|Syncml(211): O item não foi eliminado. O item solicitado não foi encontrado. Poderá ter sido eliminado anteriormente.|
|-2016345902|0x87D100D2|Syncml(210): Eliminar sem arquivar. A resposta indica que os dados solicitados foram eliminados com êxito, mas não foram arquivados antes da eliminação porque esta funcionalidade OPCIONAL não era suportada pela implementação.|
|-2016345903|0x87D100D1|Conflito resolvido com duplicação. A resposta indica que o pedido criou um conflito de atualização, que foi resolvido com a criação de uma duplicação dos dados do cliente na base de dados do servidor. A resposta inclui o URI de destino dos dados duplicados no Item do Estado. Além disso, na eventualidade de uma sincronização bidirecional, é devolvido um comando Adicionar com a definição dos dados duplicados.|
|-2016345904|0x87D100D0|Conflito resolvido com o comando "prevalecente" do cliente. A resposta indica ter havido um conflito de atualização, resolvido pelo comando prevalecente do cliente.|
|-2016345905|0x87D100CF|Conflito resolvido com a intercalação. A resposta indica que o pedido criou um conflito, resolvido com uma intercalação das instâncias de dados do cliente e do servidor. A resposta inclui os URLs de Destino e de Origem no Item do Estado. Além disso, é devolvido um comando Substituir com os dados intercalados.|
|-2016345906|0x87D100CE|A resposta indica que apenas uma parte do comando foi concluída. Se for possível concluir a restante parte do comando mais tarde, quando tal acontecer DEVERÁ ser criado outro código de estado de pedido de conclusão adequado.|
|-2016345907|0x87D100CD|O conteúdo de origem DEVE ser atualizado. O originador do pedido está a receber a indicação de que o seu conteúdo DEVE ser sincronizado a fim de obter uma versão atualizada.|
|-2016345908|0x87D100CC|O pedido foi concluído com êxito, mas não estão a ser devolvidos dados. O código de resposta também é devolvido em resposta a uma ação Obter quando não existe conteúdo no destino.|
|-2016345909|0x87D100CB|Resposta não autoritativa. A resposta ao pedido está a ser emitida por outra entidade sem ser a visada. A resposta só deve ser devolvida quando o pedido resultar num código de resposta 200 proveniente do destino autoritativo.|
|-2016345910|0x87D100CA|Aceite para processamento. O pedido para executar uma execução remota de uma aplicação ou para alertar um utilizador ou aplicação foi efetuado com êxito.|
|-2016345911|0x87D100C9|O item solicitado foi adicionado.|
|-2016345912|0x87D100C8|O comando SyncML foi concluído com êxito.|
|-2016346011|0x87D10065|O comando SyncML especificado está a ser executado, mas ainda não foi concluído.|

### Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Jun16_HO4-->


