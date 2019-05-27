---
title: Adicionar aplicações para PCs Windows que executam o cliente de software do Intune
titleSuffix: Microsoft Intune
description: Utilize as informações deste tópico para saber como adicionar aplicações para PCs Windows ao Intune antes de implementá-las.
keywords: ''
author: dougeby
ms.author: dougeby
manager: dougeby
ms.date: 08/29/2018
ms.topic: archived
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic-keep
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86cbea29233d792006bce68fcd2a36fb1a7ec0a6
ms.sourcegitcommit: 916fed64f3d173498a2905c7ed8d2d6416e34061
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 05/23/2019
ms.locfileid: "66050204"
---
# <a name="add-apps-for-windows-pcs-that-run-the-intune-software-client"></a>Adicionar aplicações para PCs Windows que executam o cliente de software do Intune

[!INCLUDE [classic-portal](includes/classic-portal.md)]

Utilize as informações deste tópico para saber como adicionar aplicações ao Intune antes de implementá-las.

> [!IMPORTANT]
> As informações neste tópico ajudam-no a adicionar aplicações para PCs Windows que gere ao utilizar o cliente de software do Intune. Se quiser adicionar aplicações para PC com Windows inscritos e outros dispositivos móveis, veja [Adicionar aplicações ao Microsoft Intune](apps-add.md).

Para instalar aplicações em PCs, elas têm de ter a capacidade de ser instaladas automaticamente, sem a interação do utilizador. Se este não for o caso, a instalação falhará.

## <a name="additional-security-settings-for-windows-installer"></a>Definições de segurança adicionais para o Windows installer
Pode permitir que os utilizadores controlem a instalação de aplicações. Se estiver ativada, esta definição permite continuar as instalações que, caso contrário, seriam interrompidas devido a uma violação de segurança. Pode configurar o Windows Installer para utilizar permissões elevadas ao instalar programas num sistema. Além disso, pode ativar os itens do Windows Information Protection (WIP) para serem indexados e os metadados acerca dos mesmos para serem armazenados numa localização não encriptada. Quando a política está desativada, os itens protegidos pelo WIP não são indexados e não são apresentados nos resultados na Cortana ou no explorador de ficheiros. A funcionalidade destas opções está desativada por predefinição. 

## <a name="add-the-app"></a>Adicionar a aplicação
Utilize o Intune Software Publisher para configurar as propriedades da aplicação e carregá-la para o seu espaço de armazenamento na cloud através do seguinte procedimento:

1. Na [consola do administrador do Microsoft Intune](https://manage.microsoft.com), selecione **Aplicações** &gt; **Adicionar Aplicações** para iniciar o Intune Software Publisher.

   > [!TIP]
   > Poderá ter de introduzir o seu nome de utilizador e palavra-passe do Intune para que o publicador seja iniciado.

2. Na página **Configuração de software** do publicador, em **Selecionar de que forma este software é disponibilizado nos dispositivos**, escolha **Instalador de software** e, em seguida, especifique:

   - **Selecionar o tipo de ficheiro de instalador de software**. Esta definição indica o tipo de software que pretende implementar. Para um PC com Windows, escolha **Windows Installer**.
   - **Especificar a localização dos ficheiros de configuração do software**. Introduza a localização dos ficheiros de instalação ou escolha **Procurar** para selecionar a localização numa lista.
   - **Incluir ficheiros e subpastas adicionais da mesma pasta**. Algum software que utiliza o Windows Installer requer ficheiros de suporte. Estes têm de estar localizados na mesma pasta que o ficheiro de instalação. Selecione esta opção se pretender também implementar estes ficheiros de suporte.

   Por exemplo, se pretender publicar uma aplicação com o nome Application.msi no Intune, a página teria o seguinte aspeto: ![Página de configuração de software do publicador](media/publisher-for-pc.png)

   Este tipo de instalação utiliza algum do seu espaço de armazenamento na cloud.

3. Na página **Descrição do software**, configure o seguinte.

   > [!NOTE]
   > Dependendo do ficheiro do instalador que está a utilizar, alguns destes valores podem ter sido introduzidos automaticamente ou podem não aparecer.

   - **Publicador**. Introduza o nome do publicador da aplicação.
   - **Nome**. Introduza o nome da aplicação tal como será apresentado no portal da empresa.<br />Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se existir o mesmo nome duas vezes, só é apresentada uma das aplicações aos utilizadores no portal da empresa.
   - **Descrição**. Introduza uma descrição para a aplicação. A descrição será apresentada aos utilizadores no portal da empresa.
   - **URL para informações de software** (opcional). Introduza o URL de um site que contenha informações sobre esta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
   - **URL de privacidade** (opcional). Introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
   - **Categoria** (opcional). Selecione uma das categorias de aplicações incorporadas. Isto irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
   - **Ícone** (opcional). Carregue um ícone que será associado à aplicação. Este é o ícone que será apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.

4. Na página **Requisitos**, selecione os requisitos que têm de ser cumpridos antes de ser possível instalar a aplicação. Escolha entre:

   - **Arquitetura**. Selecione se esta aplicação pode ser instalada em sistemas operativos de 32 bits, 64 bits ou ambos.
   - **Sistema Operativo**. Selecione o sistema operativo mínimo no qual esta aplicação pode ser instalada.

5. Na página **Regras de deteção**, pode configurar regras para detetar se a aplicação que está a configurar já está instalada num PC. Em alternativa, pode utilizar as regras de deteção predefinidas para substituir automaticamente todas as versões instaladas anteriormente da aplicação. Esta opção é para o Windows Installer (apenas ficheiros .exe).

   As regras que pode configurar são:
   - **O ficheiro existe**. Especifique o caminho para o ficheiro que pretende detetar. Pode procurar em **%ProgramFiles%** (que procura **Program Files**\&lt;path&gt; e **Program Files (x86)**\&lt;path&gt;) no PC ou **%SystemDrive%** (que procura na unidade raiz do PC, normalmente a unidade C).
   - **O código de produto MSI existe**. Selecione **Procurar** para escolher o ficheiro do Windows Installer (.msi) que pretende detetar.
   - <strong>A chave do registo existe</strong>. Especifique uma chave de registo que comece com <strong>HKEY_LOCAL_MACHINE\<. São procurados ambos os caminhos de registo de 32 bits e 64 bits. Se a chave que especificou existir em ambos os locais, a regra de deteção é satisfeita.

   Se a aplicação satisfizer qualquer uma das regras que tiver configurado, esta não será instalada.

6. Para o **Windows Installer** apenas de tipo (. msi e .exe) de ficheiros: Sobre o **argumentos de linha de comandos** página, selecione se pretende fornecer argumentos de linha de comandos opcionais para o instalador.
   Os parâmetros seguintes são adicionados automaticamente pelo Intune:
   - Para ficheiros .exe, é adicionado **/install**.
   - Para ficheiros .msi, é adicionado **/quiet**.
   Tenha em atenção que estas opções só funcionarão se o criador do pacote de aplicações tiver ativado as respetivas funcionalidades.

7. Para o **Windows Installer** apenas de tipo (apenas .exe) de ficheiros: Sobre o **códigos de retorno** página, pode adicionar novos códigos de erro que o Intune interpreta quando a aplicação é instalada num PC Windows gerido.

   Por predefinição, o Intune utiliza códigos de retorno de norma da indústria para comunicar a falha ou êxito de uma instalação do pacote de aplicação: **0** (êxito) ou **3010** (êxito ao reiniciar). Também pode adicionar os seus códigos de retorno a esta lista. Se especificar uma lista de códigos de retorno e a instalação da aplicação devolver um código que não esteja na lista, será interpretado como uma falha.

8. Na página **Resumo**, reveja as informações que especificou. Quando estiver pronto, selecione **Carregar**.

9. Selecione **Fechar** para concluir.

A aplicação é apresentada no nó **Aplicações** da área de trabalho **Aplicações**.

## <a name="next-steps"></a>Passos Seguintes

Depois de criar uma aplicação, o passo seguinte é implementá-la. Para saber mais, veja [Atribuir aplicações a grupos com o Microsoft Intune](apps-deploy.md).

Se quiser ler mais informações sobre sugestões e truques para implementar software em Windows PCs, consulte a mensagem de blogue [sugestão de suporte: Melhores práticas para distribuição de Software do Intune para PC](https://blogs.technet.microsoft.com/intunesupport/2016/06/13/support-tip-best-practices-for-intune-software-distribution-to-pcs/).
