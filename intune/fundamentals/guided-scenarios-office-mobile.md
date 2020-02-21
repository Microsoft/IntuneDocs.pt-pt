---
title: Cenário guiado - Aplicações móveis secure Microsoft Office
titleSuffix: Microsoft Intune
description: Saiba mais sobre o cenário orientado para implementar aplicações móveis seguras do Microsoft Office a partir do portal de Gestão de Dispositivos Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0232855773626693d848f77e561c51d281739215
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77514613"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>Cenário guiado - Aplicações móveis secure Microsoft Office 

Seguindo este cenário guiado no portal de Gestão de Dispositivos, pode ativar a proteção básica de aplicações Intune em dispositivos iOS/iPadOS e Android.

A proteção da aplicação que ativa irá impor as seguintes ações: 
- Encriptar ficheiros de trabalho.
- Requer um PIN para aceder a ficheiros de trabalho.
- Exija que o PIN seja reiniciado após cinco tentativas falhadas.
- Bloqueie ficheiros de trabalho de serem apoiados em serviços de backup iTunes, iCloud ou Android.  
- Exija que os ficheiros de trabalho sejam guardados apenas para oneDrive ou SharePoint.
- Evite que as aplicações protegidas carreguem ficheiros de trabalho em dispositivos encarcerados ou enraizados.
- Bloqueie o acesso aos ficheiros de trabalho se o dispositivo estiver offline durante 720 minutos.
- Remova os ficheiros de trabalho se o dispositivo estiver offline durante 90 dias. 

## <a name="background"></a>Fundo

As aplicações móveis do Office, bem como o Microsoft Edge para Mobile, suportam dupla identidade. A dupla identidade permite que as aplicações gerem ficheiros de trabalho separadamente de ficheiros pessoais. 

![Imagem de dados corporativos versus dados pessoais](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

[As políticas de proteção de aplicações intonantes](~/apps/app-protection-policy.md) ajudam a proteger os seus ficheiros de trabalho em dispositivos que estão inscritos no Intune. Também pode utilizar políticas de proteção de aplicações em dispositivos de funcionários que não estejam inscritos para gestão no Intune. Neste caso, mesmo que a sua empresa não gere o dispositivo, ainda precisa de se certificar de que os ficheiros e recursos de trabalho estão protegidos.

Pode utilizar as políticas de proteção da Aplicação para evitar que os utilizadores guardem ficheiros de trabalho em locais desprotegidos. Também pode restringir o movimento de dados para outras aplicações que não estão protegidas pelas Políticas de proteção de aplicações. As definições de políticas de proteção de aplicações incluem:
- Políticas de deslocalização de dados como **Guardar cópias de dados org**, e restringir **corte, cópia e pasta**.
- As definições de política de acesso para exigir um PIN simples para acesso e bloquear aplicações geridas de executar em dispositivos encadeçados ou enraizados.

O acesso condicional com base em aplicações e a gestão de aplicações cliente adicionam uma camada de segurança ao garantir que apenas as aplicações cliente que suportam políticas de proteção de aplicações do Intune podem aceder ao Exchange Online e a outros serviços do Office 365.

Pode bloquear as aplicações de correio incorporados no iOS/iPadOS e Android quando permite apenas que a aplicação Microsoft Outlook aceda ao Exchange Online. Além disso, pode bloquear o acesso ao SharePoint Online para as aplicações que não têm políticas de proteção de aplicações do Intune aplicadas.

Neste exemplo, o administrador tem políticas de proteção de aplicações aplicadas à aplicação Outlook seguidas de uma regra de acesso condicional que adiciona a aplicação Outlook a uma lista aprovada de aplicações que podem ser utilizadas ao aceder ao e-mail empresarial.

![Fluxo de processo de acesso condicional da aplicação outlook](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>Pré-requisitos

Vai precisar das permissões de administração intune seguintes:

   - Aplicações geridas lêem, criam, eliminam e atribuem permissões
   - Conjuntos de políticas ler, criar e atribuir permissões
   - Organização lê permissão

## <a name="step-1---introduction"></a>Passo 1 - Introdução

Ao seguir o cenário guiado pela **Intune App Protection,** evitará que os dados sejam partilhados ou vazados fora da sua organização. 

Os utilizadores designados de iOS/iPadOS e Android devem introduzir um PIN sempre que abrirem uma aplicação do Office. Após 5 tentativas pin falhadas, os utilizadores devem redefinir o PIN. Se já necessitar de um PIN do dispositivo, os utilizadores não serão afetados.

### <a name="what-you-will-need-to-continue"></a>O que precisa para continuar

Vamos perguntar-lhe sobre as aplicações de que os seus utilizadores precisam e sobre o que é necessário para aceder às mesmas. Certifique-se de que tem as seguintes informações à mão:
- Lista de aplicações do Office aprovadas para uso corporativo.
- Quaisquer requisitos PIN para o lançamento de aplicações aprovadas em dispositivos não geridos.

## <a name="step-2---basics"></a>Passo 2 - Básicos

Neste passo, deve introduzir um **Prefixo** e **Descrição** para a sua nova política de proteção de aplicações. À medida que adiciona o **Prefixo,** os detalhes relacionados com os recursos que o cenário guiado cria serão atualizados. Estes detalhes facilitarão a descoberta das suas políticas mais tarde se precisar de alterar as atribuições e configurações. 

> [!TIP]
> Considere tomar nota dos recursos que serão criados, para que possa encaminhá-los mais tarde.

## <a name="step-3---apps"></a>Passo 3 - Apps

Para ajudá-lo a começar, este cenário guiado pré-seleciona as seguintes aplicações móveis para proteger em dispositivos iOS/iPadOS e Android:
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

Este cenário guiado também configurará estas aplicações para abrir weblinks no Microsoft Edge para garantir que os sites de trabalho são abertos num navegador protegido.

Modifique a lista de aplicações geridas por políticas que pretende proteger. Adicione ou remova aplicações desta lista. 

Quando tiver selecionado as aplicações, clique em **Next**.

## <a name="step-4---configuration"></a>Passo 4 - Configuração

Neste passo, deve configurar os requisitos para aceder e partilhar os ficheiros corporativos e e-mails nestas aplicações. Por padrão, os utilizadores podem guardar dados para as contas OneDrive e SharePoint da sua organização.

| Definição | Description | Valor Predefinido |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| Tipo PIN | Os PINs numéricos são compostos por todos os números. As códigos de acesso são compostas por caracteres alfanuméricos e caracteres especiais.  No iOS/iPadOS, para configurar o tipo "Passcode", é necessário que a aplicação tenha a versão Intune SDK 7.1.12 ou superior. O tipo numérico não tem uma restrição de versão do SDK do Intune. | Numérica |
| Selecione comprimento pin mínimo | Especifique o número mínimo de dígitos numa sequência de PIN. | 6 |
| Volte a verificar os requisitos de acesso após (minutos de inatividade) | Se a aplicação gerida por políticas estiver inativa por mais tempo do que o número de minutos de inatividade especificados, a aplicação irá solicitar os requisitos de acesso (isto é, PIN, definições de lançamento condicional) a ser novamente verificada após o lançamento da aplicação. | 30 |
| Imprimir dados org | Se bloqueada, a aplicação não pode imprimir dados protegidos. | Bloqueio |
| Links de aplicativos geridos por políticas abertas em navegadores não geridos | Se bloqueados, as ligações de aplicações geridas por políticas devem ser abertas a um navegador gerido. | Bloqueio |
| Copiar dados para aplicações não geridas | Se bloqueados, os dados geridos permanecerão em aplicações geridas. | Permitir |

## <a name="step-5---assignments"></a>Passo 5 - Atribuições

Neste passo, pode escolher os grupos de utilizadores que pretende incluir para garantir que têm acesso aos seus dados corporativos. A proteção de aplicações é atribuída aos utilizadores e não aos dispositivos, pelo que os seus dados corporativos serão seguros independentemente do dispositivo utilizado e do seu estado de inscrição.

Os utilizadores sem políticas de proteção de aplicações e definições de acesso condicional atribuídas poderão guardar dados do seu perfil corporativo para aplicações pessoais e armazenamento local não manipulado nos seus dispositivos móveis. Também poderiam ligar-se a serviços de dados corporativos, como o Microsoft Exchange, com aplicações pessoais.

## <a name="step-6---review--create"></a>Passo 6 - Rever + criar

O passo final permite-lhe rever um resumo das definições configuradas. Depois de ter revisto as suas escolhas clique **em Criar** para completar o cenário guiado. Uma vez concluído o cenário guiado, é apresentada uma tabela de recursos. Pode editar estes recursos mais tarde, no entanto, uma vez que saia da vista sumária, a mesa não será salva.

> [!IMPORTANT]
> Uma vez concluído o cenário guiado, apresentará um resumo. Pode modificar os recursos listados no resumo mais tarde, no entanto a tabela que exibe estas resouces não será guardada.
## <a name="next-steps"></a>Próximos passos

- Melhorar a segurança dos ficheiros de trabalho, atribuindo aos utilizadores uma política de acesso condicional baseada em Aplicações para proteger os serviços na nuvem do envio de ficheiros de trabalho para aplicações desprotegidas. Para mais informações, consulte [Configurar as políticas de acesso condicional baseadas em aplicativos com](~/protect/app-based-conditional-access-intune-create.md)o Intune .

