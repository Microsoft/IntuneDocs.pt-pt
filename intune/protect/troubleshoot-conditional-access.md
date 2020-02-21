---
title: Resolver problemas de acesso condicional
titleSuffix: Microsoft Intune
description: O que fazer quando os seus utilizadores não têm acesso aos recursos através do Intune Conditional Access.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 07/23/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 5fa59501-5f33-46b7-a5f5-75eeae9f1209
ms.reviewer: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0d6dc10eca80a7d403d0ff44c25d3cfaed85fafa
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514205"
---
# <a name="troubleshoot-conditional-access"></a>Resolver problemas de acesso condicional
Este artigo descreve o que fazer quando os seus utilizadores não têm acesso a recursos protegidos com Acesso Condicional, ou quando os utilizadores podem aceder a recursos protegidos, mas devem ser bloqueados.

Com Acesso Intune e Condicional, pode proteger o acesso a serviços como:
- Office 365 serviços como Exchange Online, SharePoint Online e Skype para Business Online
- Exchange no local
- Vários outros serviços

Esta capacidade permite-lhe certificar-se de que apenas os dispositivos que estão inscritos no Intune e em conformidade com as regras de Acesso Condicional que definiu na consola de administração Intune ou no Diretório Ativo Azure têm acesso aos recursos da sua empresa. 

## <a name="requirements-for-conditional-access"></a>Requisitos para acesso condicional

Devem ser cumpridos os seguintes requisitos para o acesso condicional ao trabalho:

- O aparelho deve ser matriculado no MDM e gerido pela Intune.

- O utilizador e o dispositivo têm de estar em conformidade com as políticas de conformidade do Intune atribuídas.

- Por predefinição, tem de ser atribuída ao utilizador uma política de conformidade de dispositivos. Isto pode depender da configuração dos dispositivos de definição **Mark sem nenhuma política** de conformidade atribuída como que esteja em conformidade com o **dispositivo** > **Definições** de política de conformidade no portal de administração Intune.

- O Exchange ActiveSync tem de estar ativado no dispositivo se o utilizador estiver a utilizar o cliente de correio nativo do dispositivo em vez do Outlook. Isto acontece automaticamente para dispositivos iOS, Windows Phone e Android Knox.

- Para a troca no local, o conector de câmbio Intune deve estar devidamente configurado. Para mais informações, consulte [Troubleshooting the Exchange Connector in Microsoft Intune](troubleshoot-exchange-connector.md).

- Para o Skype no local, deve configurar a Autenticação Moderna Híbrida. Ver [visão geral do Auth Moderno Híbrido.](https://docs.microsoft.com/office365/enterprise/hybrid-modern-auth-overview)

Estas condições podem ser visualizadas para cada dispositivo no portal do Azure e no relatório de inventário do dispositivo.

## <a name="devices-appear-compliant-but-users-are-still-blocked"></a>Os dispositivos aparecem como estando em conformidade, mas o acesso dos utilizadores continua a ser bloqueado

- Certifique-se de que o utilizador tem uma licença Intune atribuída para uma avaliação de conformidade adequada.

- Os dispositivos Android não Knox não terão acesso até que o utilizador clique no link **Get Started Now** no e-mail de quarentena que recebem. Isto aplica-se mesmo que o utilizador já esteja inscrito no Intune. Se o utilizador não receber o e-mail com o link no seu telemóvel, pode utilizar um PC para aceder ao seu e-mail e encaminhar para uma conta de e-mail no seu dispositivo.

- Quando um dispositivo é inscrito pela primeira vez, pode demorar algum tempo até as informações de conformidade serem registadas num dispositivo. Aguarde alguns minutos e tente novamente.

- Para dispositivos iOS/iPadOS, um perfil de e-mail existente pode bloquear a implementação de um perfil de e-mail criado por administradores intune atribuído a esse utilizador, tornando o dispositivo incompatível. Neste cenário, a aplicação Portal da Empresa notificará o utilizador de que não está em conformidade devido ao seu perfil de email configurado manualmente, e leva o utilizador a remover esse perfil. Uma vez que o utilizador remova o perfil de e-mail existente, o perfil de e-mail Intune pode ser implementado com sucesso. Para evitar este problema, indique aos seus utilizadores para removerem qualquer perfil de e-mail existente no respetivo dispositivo antes de efetuarem a inscrição.

- Um dispositivo pode ficar preso num estado de verificação, impedindo o utilizador de iniciar outro check-in. Se tiver um dispositivo neste estado:
  - Certifique-se de que o dispositivo tem a versão mais recente da aplicação Portal da Empresa.
  - Reinicie o dispositivo.
  - Veja se o problema persiste em diferentes redes (por exemplo, celular, Wi-Fi, etc.).

  Se o problema persistir, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](../fundamentals/get-support.md).

- Alguns dispositivos Android podem parecer encriptados, no entanto a aplicação Portal da Empresa reconhece estes dispositivos como não encriptados e marca-os como não conformes. Neste cenário, o utilizador verá uma notificação na aplicação Portal da Empresa que lhe pede para definir um código de acesso para o dispositivo. Depois de tocar na notificação e confirmar a palavra-passe ou PIN existente, selecione a opção **Require PIN to start device**  (Exigir PIN para iniciar o dispositivo) no ecrã **Secure start-up** (Arranque seguro) e, em seguida, toque no botão **Check Compliance** (Verificar Conformidade) do dispositivo a partir da aplicação Portal da Empresa. O dispositivo deverá ser detetado como encriptado agora. 

  > [!NOTE]
  > Alguns fabricantes de dispositivos encriptam os seus dispositivos bu utilizando um PIN predefinido em vez de um PIN definido pelo utilizador. A encriptação intune vê que utiliza um PIN predefinido como inseguro e marca esses dispositivos como incompatíveis até que o utilizador crie um novo PIN não predefinido.

- Um dispositivo Android que esteja matriculado e em conformidade ainda pode ser bloqueado e receber um aviso de quarentena quando tentar aceder primeiro aos recursos corporativos. Se isso ocorrer, certifique-se de que a aplicação Do Portal da Empresa não está a funcionar e, em seguida, selecione o link **Get Started Now** no e-mail de quarentena para desencadear a avaliação. Este passo só terá de ser seguido ao ativar o acesso condicional pela primeira vez.

- Um dispositivo Android que esteja matriculado pode levar o utilizador com "Sem certificados encontrados" e não ter acesso aos recursos O365. O utilizador deve ativar a opção *Enable Browser Access* no dispositivo inscrito da seguinte forma:
  1. Abra a aplicação Portal da Empresa.
  2. Vá para a página Definições a partir dos pontos triplos (...) ou no botão do menu de hardware.
  3. Selecione o botão *'Enable Browser Access'.*
  4. No browser Chrome, termine a sessão no Office 365 e reinicie o Chrome.  


## <a name="devices-are-blocked-and-no-quarantine-email-is-received"></a>Os dispositivos estão bloqueados e não foi recebido qualquer e-mail de quarentena

- Verifique se o dispositivo está presente na consola de administração do Intune como um dispositivo do Exchange ActiveSync. Se não estiver, a deteção de dispositivos pode estar a falhar, provavelmente devido a um problema do Exchange Connector. Para mais informações, consulte [Troubleshoot o conector Intune on-premises Exchange](troubleshoot-exchange-connector.md).

- Antes do Exchange Connector bloquear um dispositivo, o mesmo envia um e-mail de ativação (quarentena). Se o dispositivo estiver offline, poderá não receber o e-mail de ativação. 

- Verifique se o cliente de e-mail no dispositivo está configurado para obter e-mails através de **Push** em vez de **Poll**. Se assim for, tal pode fazer com que o utilizador não receba o e-mail. Mude para **Poll** e verifique se o dispositivo recebe o e-mail.

## <a name="devices-are-noncompliant-but-users-are-not-blocked"></a>Os dispositivos estão classificados como não conformes, mas os utilizadores não são bloqueados

- Para computadores Windows, o Acesso Condicional bloqueia apenas a aplicação de e-mail nativa, Office 2013 com Autenticação Moderna, ou Office 2016. O bloqueio de versões anteriores do Outlook ou de todas as aplicações de correio eletrónico em PCs Windows requerem configurações de Registo de Dispositivos AAD e Serviços da Federação de Diretórios Ativos (AD FS) de acordo com [a Configuração SharePoint Online e Exchange Online para acesso condicional](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-no-modern-authentication)ao Diretório Ativo Azure.

- Se o dispositivo for apagado seletivamente ou extinto do Intune, poderá continuar a ter acesso durante várias horas após a extinção. Isto porque troca de caches direitos de acesso por seis horas. Considere outros meios de proteger dados em dispositivos extintos neste cenário.

- Os dispositivos Windows matriculados em Massa, Surface Hub, A granel e deM podem suportar o acesso condicional quando um utilizador a quem é atribuída uma licença para Intune é assinado. No entanto, deve implementar a política de conformidade para grupos de dispositivos (não grupos de utilizadores) para uma avaliação correta.

- Verifique as atribuições das suas políticas de conformidade e de acesso condicional. Se um utilizador não estiver no grupo que é atribuído às políticas, ou estiver num grupo excluído, o utilizador não está bloqueado. Apenas os dispositivos de utilizadores num grupo atribuído são verificados relativamente à conformidade.

## <a name="noncompliant-device-is-not-blocked"></a>O dispositivo não conforme não está bloqueado

Se um dispositivo não estiver em conformidade, mas continuar a ter acesso, tome as seguintes ações.

- Reveja os grupos de Destino e Exclusão. Se um utilizador não estiver no grupo de destino certo ou estiver no grupo de exclusão, não será bloqueado. Apenas os dispositivos de utilizadores num grupo de Destino são verificados relativamente à conformidade.

- Certifique-se de que o dispositivo está a ser detetado. O Exchange Connector está a apontar para um CAS do Exchange 2010 enquanto o utilizador está num servidor do Exchange 2013? Neste caso, se a regra do Exchange predefinida for Permitir, mesmo que o utilizador esteja no grupo de Destino, o Intune não pode ter conhecimento da ligação do dispositivo ao Exchange.

- Verifique o estado de Existência/Acesso do Dispositivo no Exchange:
  - Utilize este cmdlet PowerShell para obter uma lista de todos os dispositivos móveis para uma caixa de correio: 'Get-ActiveSyncDeviceStatistics -mailbox mbx'. Se o dispositivo não estiver listado, significa que não está a aceder ao Exchange.
  
  - Se o dispositivo estiver listado, utilize o 'Get-CASmailbox -identity:'upn'  Fl' cmdlet para obter informações detalhadas sobre o seu estado de acesso, e fornecer essa informação ao Microsoft Support.

## <a name="next-steps"></a>Próximos passos
Se estas informações não o ajudarem, também pode [obter suporte para o Microsoft Intune](../fundamentals/get-support.md).
