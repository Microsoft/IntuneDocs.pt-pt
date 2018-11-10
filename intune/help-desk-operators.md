---
title: Portal de resolução de problemas de suporte técnico
titlesuffix: Microsoft Intune
description: O pessoal de suporte técnico utiliza o portal de resolução de problemas para resolver problemas técnicos dos utilizadores.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 10/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 1f39c02a-8d8a-4911-b4e1-e8d014dbce95
ms.reviewer: sumitp
ms.custom: intune-azure
ms.openlocfilehash: 90756da72ecdcbd049b14b45014433bb5843a5ed
ms.sourcegitcommit: 5c2a70180cb69049c73c9e55d36a51e9d6619049
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236667"
---
# <a name="use-the-troubleshooting-portal-to-help-users-at-your-company"></a>Utilizar o portal de resolução de problemas para ajudar os utilizadores na sua empresa

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

O portal de resolução de problemas permite que os operadores de suporte técnico e os administradores do Intune vejam as informações de utilizador para resolverem pedidos de ajuda dos utilizadores. As organizações que incluem um suporte técnico podem atribuir o **Operador de suporte técnico** a um grupo de utilizadores. A função de operador de suporte técnico pode utilizar o painel **Resolução de problemas**.

O painel **Resolução de Problemas** também apresenta problemas de inscrição de utilizadores. Os detalhes acerca do problema e os passos de remediação sugeridos podem ajudar os administradores e os operadores de suporte técnico a resolver problemas. Existem determinados problemas de inscrição que não são detetados e é possível que não existam sugestões de remediação para alguns erros.

Para obter passos sobre como adicionar uma função de operador de suporte técnico, veja [Controlo de administração baseada em funções (RBAC) com o Intune](/intune/role-based-access-control)

Quando um utilizador contacta o suporte acerca de um problema técnico com o Intune, o operador de suporte técnico introduz o nome do utilizador. O Intune mostra dados úteis que podem ajudar a resolver vários problemas de nível 1, incluindo:

- Estado de utilizador
- Atribuições
- Resolver problemas de compatibilidade
- O dispositivo não responde
- O dispositivo não consegue aceder às definições de VPN ou Wi-Fi
- Falha na instalação da aplicação

## <a name="to-review-troubleshooting-details"></a>Para rever os detalhes da resolução de problemas

No painel Resolução de Problemas, selecione **Utilizador selecionado** para ver as informações do utilizador. As informações dos utilizadores podem ajudá-lo a compreender o estado atual dos utilizadores e dos dispositivos deles.  

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços** > **Intune**. O Intune encontra-se na secção **Monitorização + Gestão**.
3. No painel **Intune**, selecione **Resolução de problemas**.
4. Clique em **Selecionar** para selecionar um utilizador para o qual pretende executar a resolução de problemas.
5. Selecione um utilizador ao escrever o nome ou endereço de e-mail. Clique em **Selecionar**. As informações de resolução de problemas do utilizador são apresentadas no painel Resolução de problemas. A seguinte tabela explica as informações.

> [!Note]  
> Também pode aceder ao painel **Resolução de problemas** ao apontar o seu browser para: [https://aka.ms/intunetroubleshooting](https://aka.ms/intunetroubleshooting).

## <a name="areas-of-troubleshooting-dashboard"></a>Áreas do dashboard de resolução de problemas

Pode utilizar o painel **Resolução de problemas** para analisar as informações de utilizador.

![](/intune/media/troubleshooting-dash.png)

| Área | Nome | Descrição |
| ---  | ---  | ---         |
| 1.   | Estado da conta  | Mostra o estado do inquilino do Intune atual como **Ativo** ou **Inativo**.       |
| 2.   | Seleção do utilizador  | O nome do utilizador atualmente selecionado. Clique em **Alterar utilizador** para selecionar um novo utilizador.       |
| 3.   | Estado de utilizador  | Apresenta o estado da licença do Intune do utilizador, número de dispositivos, conformidade de cada dispositivo, número de aplicações e conformidade das aplicações.       |
| 4.   | Informações do utilizador  | Utilize a lista para selecionar os detalhes a consultar no painel. <br>Pode selecionar: <ul><li>Aplicações do cliente<li>Políticas de conformidade<li> Políticas de configuração<li>Políticas de proteção de aplicações <li>Restrições de inscrição</ul>      |
| 5.   | Associação a grupos  | Mostra os grupos atuais dos quais o utilizador selecionado é membro.       |

## <a name="client-apps-reference"></a>Referência de aplicações do cliente

As aplicações que estão em execução em dispositivos
- Geridos pelo Intune e pelo Azure Active Directory (AD) 
- Pertencentes a utilizadores geridos pelo Intune e pelo Azure Active Directory (AD).

### <a name="properties"></a>Propriedades

As propriedades das aplicações do cliente.

| Propriedade      | Descrição                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Nome          | O nome da aplicação.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| SO            | O sistema operativo instalado no dispositivo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Tipo          | Pode escolher um tipo de atribuição para cada aplicação.  <br> **Disponível** – Os utilizadores instalam a aplicação a partir do site ou da aplicação Portal da Empresa.  <br> **Não Aplicável** – A aplicação não é instalada nem apresentada no Portal da Empresa. <br> **Desinstalar** – A aplicação é desinstalada dos dispositivos nos grupos selecionados.  <br> **Disponível com ou sem inscrição** – Atribua esta aplicação a grupos de utilizadores cujos dispositivos não estão inscritos no Intune. |
| Última Modificação | O nome do tipo de dispositivo.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### <a name="devices"></a>Dispositivos

Dispositivos geridos pelo Intune ou por utilizadores geridos pelo Intune ou Azure AD.

| Propriedade           | Descrição                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome do dispositivo        | O nome do tipo de dispositivo.                                                                                                     |
| Gerido por         | O carimbo de data/hora em que a política foi modificada.                                                                                              |
| Tipo de associação Azure AD | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| Propriedade          | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**).                                               |
| Em conformidade com o Intune   | O nome do tipo de dispositivo.                                                                                                     |
| Em conformidade com o Azure AD | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| Instalação da aplicação | Indica se a instalação da aplicação falhou ou teve êxito em cada dispositivo. |
| SO                 | O sistema operativo instalado no dispositivo.                                                                                       |
| Versão do SO         | O número da versão do Sistema Operativo do dispositivo.                                                                                  |
| Último registo      | O nome do tipo de dispositivo.                                                                                                     |

### <a name="app-protection-status"></a>Estado da proteção de aplicações

Encontra-se disponível uma política de proteção de aplicações para aplicações móveis que integrem as tecnologias de Enterprise Mobility + Security (EMS). Estas políticas proporcionam uma linha base de proteção para os seus dados empresariais quando são transferidos para aplicações móveis, incluindo as aplicações móveis do Office. 

| Propriedade    | Descrição                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Estado      | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**). |
| Nome da aplicação    | O nome da aplicação                                                           |
| Nome do dispositivo | O nome do tipo de dispositivo.                                                       |
| Tipo de dispositivo | O nome do tipo de dispositivo.                                                       |
| Políticas    | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**). |
| Última sincronização   | O carimbo de data/hora da última vez que o dispositivo sincronizou com o Intune.                   |

## <a name="app-protection-policies-reference"></a>Referência de políticas de proteção de aplicações

As políticas de proteção de aplicações estão disponíveis para aplicações móveis que integram tecnologias de EMS. Estas políticas proporcionam uma linha base de proteção para os seus dados empresariais quando são transferidos para aplicações móveis, incluindo as aplicações móveis do Office. 

### <a name="properties"></a>Propriedades

A tabela resume o estado das políticas de proteção de aplicações para dispositivos geridos pelo Intune.

| Propriedade    | Descrição                                                                                                                                |
|-------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome        | O nome da aplicação.                                                                                                        |
| Implementado    | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| Platform    | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**).                                               |
| Inscrição  | O nome do tipo de dispositivo.                                                                                                     |
| Última Atualização | O carimbo de data/hora em que a política foi modificada.                                                                                              |

### <a name="devices"></a>Dispositivos

Dispositivos geridos pelo Intune ou por utilizadores geridos pelo Intune ou Azure AD.

| Propriedade           | Texto                                                                                                                                |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome do Dispositivo        | O nome do tipo de dispositivo.                                                                                                     |
| Gerido Por         | O carimbo de data/hora em que a política foi modificada.                                                                                              |
| Tipo de associação Azure AD | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| Propriedade          | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**).                                               |
| Em conformidade com o Intune   | O nome do tipo de dispositivo.                                                                                                     |
| Em conformidade com o Azure AD | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| Em conformidade com o Azure AD | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| SO                 | O sistema operativo instalado no dispositivo.                                                                                       |
| Versão do SO         | O número da versão do Sistema Operativo do dispositivo.                                                                                  |
| Último Registo      | O nome do tipo de dispositivo.                                                                                                     |

## <a name="compliance-policies-reference"></a>Referência de políticas de conformidade

Assegura que os dispositivos utilizados para aceder às aplicações e aos dados da empresa estão em conformidade com determinadas regras, como a utilização de um PIN para aceder ao dispositivo e a encriptação dos dados armazenados no dispositivo.

### <a name="properties"></a>Propriedades

As propriedades das políticas de conformidade.

| Propriedade      | Descrição                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Atribuição    | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| Nome          | O nome da aplicação.                                                                                                        |
| SO            | O sistema operativo instalado no dispositivo.                                                                                       |
| Tipo de Política   | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** e **Desconhecido**).                                               |
| Última Modificação | O nome do tipo de dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivos

Dispositivos geridos pelo Intune ou por utilizadores geridos pelo Intune ou Azure AD.

| Propriedade           | Descrição                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome do dispositivo        | O nome do tipo de dispositivo.                                                                                                     |
| Gerido por         | O carimbo de data/hora em que a política foi modificada.                                                                                              |
| Tipo de associação Azure AD | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| Propriedade          | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** e **Desconhecido**).                                               |
| Em conformidade com o Intune   | O nome do tipo de dispositivo.                                                                                                     |
| Em conformidade com o Azure AD | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| SO                 | O sistema operativo instalado no dispositivo.                                                                                       |
| Versão do SO         | O número da versão do Sistema Operativo do dispositivo.                                                                                  |
| Último registo      | O nome do tipo de dispositivo.                                                                                                     |

### <a name="app-protection-policies"></a>Políticas de proteção de aplicações

Encontra-se disponível uma política de proteção de aplicações para aplicações móveis que integrem tecnologias de EMS. Estas políticas proporcionam uma linha base de proteção para os seus dados empresariais quando são transferidos para aplicações móveis, incluindo as aplicações móveis do Office. 

| Propriedade    | Descrição                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Estado      | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**). |
| Nome da aplicação    | O nome da aplicação                                                           |
| Nome do dispositivo | O nome do tipo de dispositivo.                                                       |
| Tipo de dispositivo | O nome do tipo de dispositivo.                                                       |
| Políticas    | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**). |
| Última sincronização   | O carimbo de data/hora da última vez que o dispositivo sincronizou com o Intune.                   |

## <a name="configuration-policies-reference"></a>Referência de políticas de configuração

Uma política de configuração de aplicações está disponível para aplicações móveis com configurações específicas do fornecedor. 

### <a name="properties"></a>Propriedades

As propriedades das políticas de configuração.

| Propriedade      | Descrição                                                                                                                         |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Atribuição    | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| Nome          | O nome da aplicação.                                                                                                        |
| SO            | O sistema operativo instalado no dispositivo.                                                                                       |
| Tipo de Política   | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**).                                               |
| Última Modificação | O nome do tipo de dispositivo.                                                                                                     |

### <a name="devices"></a>Dispositivos

Dispositivos geridos pelo Intune ou por utilizadores geridos pelo Intune ou Azure AD.

| Propriedade           | Descrição                                                                                                                         |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Nome do dispositivo        | O nome do tipo de dispositivo.                                                                                                     |
| Gerido por         | O carimbo de data/hora em que a política foi modificada.                                                                                              |
| Tipo de associação Azure AD | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| Propriedade          | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**).                                               |
| Em conformidade com o Intune   | O nome do tipo de dispositivo.                                                                                                     |
| Em conformidade com o Azure AD | O estado de cada uma das aplicações de proteção dos utilizadores. Os estados possíveis para as aplicações são **Verificado** e **Não verificado**. |
| SO                 | O sistema operativo instalado no dispositivo.                                                                                       |
| Versão do SO         | O número da versão do Sistema Operativo do dispositivo.                                                                                  |
| Último registo      | O nome do tipo de dispositivo.                                                                                                     |


### <a name="app-protection-policies"></a>Políticas de proteção de aplicações

Encontra-se disponível uma política de proteção de aplicações para aplicações móveis que integrem tecnologias de EMS. Estas políticas proporcionam uma linha base de proteção para os seus dados empresariais quando são transferidos para aplicações móveis, incluindo as aplicações móveis do Office. 

| Propriedade    | Descrição                                                                           |
|-------------|---------------------------------------------------------------------------------------|
| Estado      | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**). |
| Nome da aplicação    | O nome da aplicação                                                           |
| Nome do dispositivo | O nome do tipo de dispositivo.                                                       |
| Tipo de dispositivo | O nome do tipo de dispositivo.                                                       |
| Políticas    | O tipo de propriedade do dispositivo (**Empresa**, **Pessoal** ou **Desconhecido**). |
| Última sincronização   | O carimbo de data/hora da última vez que o dispositivo sincronizou com o Intune.                   |

## <a name="enrollment-failure-reference"></a>Referência de falha de inscrição

A tabela Falhas de Inscrição lista as tentativas de inscrição que falharam. Um dispositivo listado na tabela abaixo pode ter sido inscrito posteriormente com êxito durante outra tentativa. É possível que algumas tentativas falhadas não sejam listadas. As informações de mitigação não estão disponíveis para todas as falhas.

| Coluna de tabela | Descrição |
|-------------|----------|
| Início da inscrição | A hora de início em que o utilizador começou a inscrição. |
| SO | O sistema operativo do dispositivo. |
| Versão do SO | A versão do sistema operativo do dispositivo. |
| Falha | O motivo da falha. |

### <a name="failure-details"></a>Detalhes da falha

Ao selecionar uma linha de falha, são fornecidos mais detalhes.

| Secção | Descrição |
|-------------|----------|
| Detalhes da falha | Uma explicação em maior detalhe sobre a falha. |
| Potenciais remediações | Passos sugeridos para resolver o erro. Poderão não existir remediações para determinadas falhas. |
| Recursos (Opcional) | Ligações para leituras adicionais ou para determinada área no portal para efetuar uma ação. |

### <a name="enrollment-errors"></a>Erros de inscrição

| Error | Detalhes |
|-------------|----------|
| Tempo limite ou Falha de dispositivos iOS | Exceder do tempo limite entre o dispositivo e o Intune devido ao utilizador demorar demasiado tempo a concluir a inscrição. |
| Utilizador não encontrado ou licenciado | O utilizador não possui uma licença ou foi removido do serviço. |
| O dispositivo já está inscrito | Uma pessoa tentou inscrever um dispositivo ao utilizar o Portal da Empresa num dispositivo que ainda está inscrito por outro utilizador. |
| Não incluído no Intune | Houve uma tentativa de inscrição enquanto a autoridade de gestão de dispositivos móveis (MDM) do Intune ainda não estava configurada. |
| Falha na autorização da inscrição | Houve uma tentativa de inscrição através de uma versão antiga do portal da empresa. |
| Dispositivo não suportado | O dispositivo não cumpre os requisitos mínimos de inscrição no Intune. |
| As restrições de inscrição não correspondem | A inscrição foi bloqueada devido a uma restrição de inscrição configurada pelo administrador. |
| Máximo de dispositivos atingido | A inscrição foi bloqueada devido a uma restrição de limite de dispositivos configurada pelo administrador. |
| Inclusão da Apple | A inscrição de todos os dispositivos iOS foi bloqueada até ao momento devido a um certificado push de MDM da Apple expirado ou em falta no Intune. |
| O dispositivo não foi pré-registado | O dispositivo não foi pré-registado como dispositivo empresarial e todas as inscrições pessoais foram bloqueadas por um administrador. |
| Funcionalidade não suportada | O utilizador procedeu a uma provável tentativa de inscrição através de um método incompatível com a sua configuração do Intune. |

## <a name="collect-available-data-from-mobile-device"></a>Recolher dados disponíveis de dispositivos móveis

Utilize os seguintes recursos para ajudar a recolher dados de dispositivos ao resolver problemas de dispositivos:
  - [Enviar erros de inscrição de dispositivos iOS para o seu administrador de TI](/intune-user-help/send-errors-to-your-it-admin-ios)
  - [Help your company support fix device issues with verbose logging](/intune-user-help/use-verbose-logging-to-help-your-it-administrator-fix-device-issues-android) (Ajudar o suporte da empresa a corrigir problemas de dispositivos com o registo verboso)
  - [Enviar registos Android ao suporte da empresa por cabo USB](/intune-user-help/send-diagnostic-data-logs-to-your-it-administrator-using-a-usb-cable-android)
  - [Enviar registos de dados de diagnóstico para o seu administrador de TI através de e-mail](/intune-user-help/send-logs-to-your-it-admin-by-email-android)
  - [Enviar erros de inscrição de dispositivos Android para o seu administrador de TI](/intune-user-help/send-enrollment-errors-to-your-it-administrator-android)

## <a name="next-steps"></a>Próximos passos

Pode saber mais sobre o Controlo de administração baseada em funções (RBAC) para definir funções no seu dispositivo organizacional, gestão de aplicações móveis e tarefas de proteção de dados. Para obter mais informações, veja [Controlo de administração baseada em funções (RBAC) com o Intune](/intune/role-based-access-control).

Saiba mais sobre os problemas conhecidos no Microsoft Intune. Para obter mais informações, veja [Problemas conhecidos no Microsoft Intune](/intune/known-issues).

Saiba como criar um pedido de suporte e obter ajuda quando precisar. [Obter suporte](/intune/get-support).
