---
title: Cenário guiado – aplicativos móveis seguros Microsoft Office
titleSuffix: Microsoft Intune
description: Saiba mais sobre o cenário guiado para implantar aplicativos móveis seguros Microsoft Office do portal de gerenciamento de dispositivos Microsoft 365.
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
ms.openlocfilehash: 3399cf006543c0a3554c4c6ec812554462d74231
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691809"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>Cenário guiado – aplicativos móveis seguros Microsoft Office 

Seguindo esse cenário guiado no portal de gerenciamento de dispositivos, você pode habilitar a proteção básica de aplicativo do Intune em dispositivos iOS e Android.

A proteção do aplicativo que você habilitar irá impor as seguintes ações: 
- Criptografar arquivos de trabalho.
- Exigir um PIN para acessar os arquivos de trabalho.
- Exigir que o PIN seja redefinido após cinco tentativas com falha.
- Bloquear a realização de backup de arquivos de trabalho no iTunes, iCloud ou serviços de backup do Android.  
- Exigir que os arquivos de trabalho sejam salvos somente no OneDrive ou no SharePoint.
- Impedir que aplicativos protegidos carreguem arquivos de trabalho em dispositivos com jailbreak ou root.
- Bloquear o acesso a arquivos de trabalho se o dispositivo estiver offline por 720 minutos.
- Remova os arquivos de trabalho se o dispositivo estiver offline por 90 dias. 

## <a name="background"></a>Fundo

Os aplicativos móveis do Office, bem como o Microsoft Edge para dispositivos móveis, dão suporte a identidade dupla. A identidade dupla permite que os aplicativos gerenciem arquivos de trabalho separadamente de arquivos pessoais. 

![Imagem de dados corporativos versus dados pessoais](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

[As políticas de proteção de aplicativo do Intune](~/apps/app-protection-policy.md) ajudam a proteger seus arquivos de trabalho em dispositivos registrados no Intune. Também pode utilizar políticas de proteção de aplicações em dispositivos de funcionários que não estejam inscritos para gestão no Intune. Nesse caso, mesmo que sua empresa não gerencie o dispositivo, você ainda precisará certificar-se de que os arquivos de trabalho e os recursos estejam protegidos.

Você pode usar as políticas de proteção de aplicativo para impedir que os usuários salvem arquivos de trabalho em locais desprotegidos. Também pode restringir o movimento de dados para outras aplicações que não estão protegidas pelas Políticas de proteção de aplicações. As definições de políticas de proteção de aplicações incluem:
- Políticas de realocação **de dados como salvar cópias de dados da organização**e **restringir recortar, copiar e colar**.
- Configurações de política de acesso para exigir PIN simples para acesso e impedir que aplicativos gerenciados sejam executados em dispositivos com jailbreak ou com raiz.

O acesso condicional com base em aplicações e a gestão de aplicações cliente adicionam uma camada de segurança ao garantir que apenas as aplicações cliente que suportam políticas de proteção de aplicações do Intune podem aceder ao Exchange Online e a outros serviços do Office 365.

Pode bloquear as aplicações de e-mail incorporadas no iOS e Android quando permite apenas à aplicação Microsoft Outlook o acesso ao Exchange Online. Além disso, pode bloquear o acesso ao SharePoint Online para as aplicações que não têm políticas de proteção de aplicações do Intune aplicadas.

Neste exemplo, o administrador tem políticas de proteção de aplicações aplicadas à aplicação Outlook seguidas de uma regra de acesso condicional que adiciona a aplicação Outlook a uma lista aprovada de aplicações que podem ser utilizadas ao aceder ao e-mail empresarial.

![Fluxo do processo de acesso condicional do aplicativo Outlook](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>Pré-requisitos

Você precisará seguir as permissões de administrador do Intune:

   - Aplicativos gerenciados ler, criar, excluir e atribuir permissões
   - Política define permissões de leitura, criação e atribuição
   - Permissão de leitura da organização

## <a name="step-1---introduction"></a>Etapa 1-Introdução

Seguindo o cenário guiado **proteção de aplicativo do Intune** , você impedirá que os dados sejam compartilhados ou vazados fora da sua organização. 

Os usuários do iOS e Android atribuídos devem inserir um PIN sempre que abrirem um aplicativo do Office. Depois de 5 tentativas de PIN com falha, os usuários devem redefinir seu PIN. Se você já precisar de um PIN de dispositivo, os usuários não serão afetados.

### <a name="what-you-will-need-to-continue"></a>O que será necessário para continuar

Nós lhe perguntaremos sobre os aplicativos de que seus usuários precisam e o que é necessário para acessá-los. Verifique se você tem as seguintes informações à mão:
- Lista de aplicativos do Office aprovadas para uso corporativo.
- Quaisquer requisitos de PIN para iniciar aplicativos aprovados em dispositivos não gerenciados.

## <a name="step-2---basics"></a>Etapa 2-noções básicas

Nesta etapa, você deve inserir um **prefixo** e uma **Descrição** para sua nova política de proteção de aplicativo. À medida que você adiciona o **prefixo**, os detalhes relacionados aos recursos criados pelo cenário orientado serão atualizados. Esses detalhes facilitarão a localização de suas políticas posteriormente se você precisar alterar as atribuições e a configuração. 

> [!TIP]
> Considere anotar os recursos que serão criados para que você possa consultá-los mais tarde.

## <a name="step-3---apps"></a>Etapa 3-aplicativos

Para ajudá-lo a começar, este cenário guiado seleciona previamente os seguintes aplicativos móveis para proteger em dispositivos Android e iOS:
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

Esse cenário guiado também configurará esses aplicativos para abrir weblinks no Microsoft Edge para garantir que os sites de trabalho sejam abertos em um navegador protegido.

Modifique a lista de aplicativos gerenciados por política que você deseja proteger. Adicionar ou remover aplicativos desta lista. 

Quando você tiver selecionado os aplicativos, clique em **Avançar**.

## <a name="step-4---configuration"></a>Etapa 4-configuração

Nesta etapa, você deve configurar os requisitos para acessar e compartilhar os arquivos corporativos e emails nesses aplicativos. Por padrão, os usuários podem salvar dados nas contas do OneDrive e do SharePoint da sua organização.

| Definição | Description | Valor Predefinido |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| Tipo de PIN | Os PINs numéricos são compostos de todos os números. As senhas são constituídas de caracteres alfanuméricos e caracteres especiais.  No iOS/iPadOS, para configurar o tipo de "senha", é necessário que o aplicativo tenha o Intune SDK versão 7.1.12 ou superior. O tipo numérico não tem uma restrição de versão do SDK do Intune. | Numérica |
| Selecionar comprimento mínimo do PIN | Especifique o número mínimo de dígitos numa sequência de PIN. | 6 |
| Verificar novamente os requisitos de acesso após (minutos de inatividade) | Se o aplicativo gerenciado por política estiver inativo por mais tempo do que o número de minutos de inatividade especificado, o aplicativo solicitará os requisitos de acesso (ou seja, Fixe, configurações de inicialização condicional) a serem verificadas novamente após o aplicativo ser iniciado. | 30 |
| Imprimindo dados da organização | Se bloqueado, o aplicativo não poderá imprimir dados protegidos. | Bloqueio |
| Abrir política-links de aplicativos gerenciados em navegadores não gerenciados | Se bloqueado, os links de aplicativo gerenciados por política deverão ser abertos em um navegador gerenciado. | Bloqueio |
| Copiar dados para aplicativos não gerenciados | Se bloqueado, os dados gerenciados permanecerão em aplicativos gerenciados. | Permitir |

## <a name="step-5---assignments"></a>Etapa 5-atribuições

Nesta etapa, você pode escolher os grupos de usuários que deseja incluir para garantir que eles tenham acesso aos dados corporativos. A proteção do aplicativo é atribuída aos usuários e não aos dispositivos, de modo que seus dados corporativos serão protegidos, independentemente do dispositivo usado e do seu status de registro.

Os usuários sem políticas de proteção de aplicativo e configurações de acesso condicional atribuídas poderão salvar dados de seu perfil corporativo para aplicativos pessoais e armazenamento local não-gerenciada em seus dispositivos móveis. Eles também podem se conectar aos serviços de dados corporativos, como o Microsoft Exchange, com aplicativos pessoais.

## <a name="step-6---review--create"></a>Etapa 6-examinar + criar

A etapa final permite que você examine um resumo das configurações que você configurou. Depois de revisar suas escolhas, clique em **criar** para concluir o cenário guiado. Depois que o cenário guiado for concluído, uma tabela de recursos será exibida. Você pode editar esses recursos mais tarde, no entanto, depois de sair do modo de exibição de resumo, a tabela não será salva.

> [!IMPORTANT]
> Depois que o cenário guiado for concluído, ele exibirá um resumo. Você pode modificar os recursos listados no resumo posteriormente, no entanto, a tabela que está exibindo esses recurso não será salva.
## <a name="next-steps"></a>Próximos passos

- Aprimore a segurança dos arquivos de trabalho atribuindo aos usuários uma política de acesso condicional baseada em aplicativo para proteger os serviços de nuvem de enviar arquivos de trabalho para aplicativos desprotegidos. Para obter mais informações, consulte [Configurar políticas de acesso condicional com base no aplicativo com o Intune](~/protect/app-based-conditional-access-intune-create.md).

