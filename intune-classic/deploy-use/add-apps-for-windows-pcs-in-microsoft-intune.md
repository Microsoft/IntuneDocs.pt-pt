---
title: "Adicionar aplicações para PCs Windows que executam o cliente de software do Intune"
description: "Utilize as informações deste tópico para saber como adicionar aplicações para PCs Windows ao Intune antes de implementá-las."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 02/16/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bc8c8be9-7f4f-4891-9224-55fc40703f0b
ms.reviewer: owenyen
ms.suite: ems
ms.custom: intune-classic
ms.openlocfilehash: faf52c4166298d981532ee61c158f4a705c5a3da
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="add-apps-for-windows-pcs-that-run-the-intune-software-client"></a>Adicionar aplicações para PCs Windows que executam o cliente de software do Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize as informações deste tópico para saber como adicionar aplicações ao Intune antes de implementá-las.

> [!IMPORTANT]
> As informações neste tópico ajudam-no a adicionar aplicações para PCs Windows que gere ao utilizar o cliente de software do Intune. Se pretender adicionar aplicações para PC com Windows inscritos e outros dispositivos móveis, consulte [Adicionar aplicações para dispositivos móveis no Microsoft Intune](add-apps-for-mobile-devices-in-microsoft-intune.md).

Para instalar aplicações em PCs, elas têm de ter a capacidade de ser instaladas automaticamente, sem a interação do utilizador. Se este não for o caso, a instalação falhará.


## <a name="add-the-app"></a>Adicionar a aplicação
Utilize o Intune Software Publisher para configurar as propriedades da aplicação e carregá-la para o seu espaço de armazenamento na cloud através do seguinte procedimento:

1.  Na [consola do administrador do Microsoft Intune](https://manage.microsoft.com), selecione **Aplicações** &gt; **Adicionar Aplicações** para iniciar o Intune Software Publisher.

    > [!TIP]
    > Poderá ter de introduzir o seu nome de utilizador e palavra-passe do Intune para que o publicador seja iniciado.

2.  Na página **Configuração de software** do publicador, em **Selecionar de que forma este software é disponibilizado nos dispositivos**, escolha **Instalador de software** e, em seguida, especifique:

    - **Selecionar o tipo de ficheiro de instalador de software**. Esta definição indica o tipo de software que pretende implementar. Para um PC com Windows, escolha **Windows Installer**.
    - **Especificar a localização dos ficheiros de configuração do software**. Introduza a localização dos ficheiros de instalação ou escolha **Procurar** para selecionar a localização numa lista.
    - **Incluir ficheiros e subpastas adicionais da mesma pasta**. Algum software que utiliza o Windows Installer requer ficheiros de suporte. Estes têm de estar localizados na mesma pasta que o ficheiro de instalação. Selecione esta opção se pretender também implementar estes ficheiros de suporte.

    Por exemplo, se pretendesse publicar uma aplicação com o nome Application.msi no Intune, a página teria o seguinte aspeto: ![Página de configuração de software do publicador](./media/publisher-for-pc.png)

   Este tipo de instalação utiliza algum do seu espaço de armazenamento na cloud.

3.  Na página **Descrição do software**, configure o seguinte.

    > [!NOTE]
    > Dependendo do ficheiro do instalador que está a utilizar, alguns destes valores podem ter sido introduzidos automaticamente ou podem não aparecer.

    - **Publicador**. Introduza o nome do publicador da aplicação.
    - **Nome**. Introduza o nome da aplicação tal como será apresentado no portal da empresa.<br />Certifique-se de que todos os nomes de aplicações que utiliza são exclusivos. Se o mesmo nome de aplicação existir duas vezes, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição**. Introduza uma descrição para a aplicação. A descrição será apresentada aos utilizadores no portal da empresa.
    - **URL para informações de software** (opcional). Introduza o URL de um site que contenha informações sobre esta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **URL de privacidade** (opcional). Introduza o URL de um site que contenha informações sobre a privacidade desta aplicação. O URL será apresentado aos utilizadores no portal da empresa.
    - **Categoria** (opcional). Selecione uma das categorias de aplicações incorporadas. Isto irá permitir que os utilizadores encontrem a aplicação mais facilmente quando procurarem no portal da empresa.
    - **Ícone** (opcional). Carregue um ícone que será associado à aplicação. Este é o ícone que será apresentado com a aplicação quando os utilizadores procurarem no portal da empresa.

4.  Na página **Requisitos**, selecione os requisitos que têm de ser cumpridos antes de ser possível instalar a aplicação. Escolha entre:

    - **Arquitetura**. Selecione se esta aplicação pode ser instalada em sistemas operativos de 32 bits, 64 bits ou ambos.
    - **Sistema Operativo**. Selecione o sistema operativo mínimo no qual esta aplicação pode ser instalada.

5.  Na página **Regras de deteção**, pode configurar regras para detetar se a aplicação que está a configurar já está instalada num PC. Em alternativa, pode utilizar as regras de deteção predefinidas para substituir automaticamente todas as versões instaladas anteriormente da aplicação. Esta opção é para o Windows Installer (apenas ficheiros .exe).

    As regras que pode configurar são:
    - **O ficheiro existe**. Especifique o caminho para o ficheiro que pretende detetar. Pode procurar em **%ProgramFiles%** (que procura **Program Files**\&lt;path&gt; e **Program Files (x86)**\&lt;path&gt;) no PC ou **%SystemDrive%** (que procura na unidade raiz do PC, normalmente a unidade C).
    - **O código de produto MSI existe**. Selecione **Procurar** para escolher o ficheiro do Windows Installer (.msi) que pretende detetar.
    - **A chave do registo existe**. Especifique uma chave de registo que comece com **HKEY_LOCAL_MACHINE\**. São procurados ambos os caminhos de registo de 32 bits e 64 bits. Se a chave que especificou existir em ambos os locais, a regra de deteção é satisfeita.

    Se a aplicação satisfizer qualquer uma das regras que tiver configurado, esta não será instalada.

6.  Apenas para o tipo de ficheiro do **Windows Installer** (.msi e .exe): na página **Argumentos de linha de comandos**, escolha se pretende fornecer argumentos de linha de comandos opcionais para o instalador.
    Os parâmetros seguintes são adicionados automaticamente pelo Intune:
    - Para ficheiros .exe, é adicionado **/install**.
    - Para ficheiros .msi, é adicionado **/quiet**.
    Tenha em atenção que estas opções só funcionarão se o criador do pacote de aplicações tiver ativado as respetivas funcionalidades.

7.  Apenas para o tipo de ficheiro do **Windows Installer** (apenas .exe): na página **Códigos de retorno**, pode adicionar novos códigos de erro que o Intune interpreta quando a aplicação é instalada num PC Windows gerido.

    Por predefinição, o Intune utiliza códigos de retorno comuns da indústria para comunicar a instalação falhada ou com êxito de um pacote de aplicações: **0** (Êxito) ou **3010** (Êxito ao reiniciar). Também pode adicionar os seus códigos de retorno a esta lista. Se especificar uma lista de códigos de retorno e a instalação da aplicação devolver um código que não esteja na lista, será interpretado como uma falha.

8.  Na página **Resumo**, reveja as informações que especificou. Quando estiver pronto, selecione **Carregar**.

9. Selecione **Fechar** para concluir.

A aplicação é apresentada no nó **Aplicações** da área de trabalho **Aplicações**.

## <a name="next-steps"></a>Passos seguintes

Depois de criar uma aplicação, o passo seguinte é implementá-la. Para obter mais informações, veja [Implementar aplicações no Microsoft Intune](deploy-apps.md).

Se quiser ler mais informações sobre sugestões e truques para implementar software para PCs com Windows, veja a mensagem do blogue [Sugestão de Suporte: Melhores Práticas para Distribuição de Software do Intune para PCs](https://blogs.technet.microsoft.com/intunesupport/2016/06/13/support-tip-best-practices-for-intune-software-distribution-to-pcs/).
