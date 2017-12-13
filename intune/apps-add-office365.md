---
title: "Instalar aplicações do Office 365 em dispositivos móveis com o Intune"
titlesuffix: Azure portal
description: "Saiba como pode utilizar o Intune para facilitar a instalação das aplicações do Office 365 em dispositivos Windows 10."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 08/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 7f1958e4a0fb5aeba3225ee7ea5fae1e7fb39db3
ms.sourcegitcommit: 520eb7712625e129b781e2f2b9fe16f9b9f3d08a
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-assign-office-365-proplus-2016-apps-to-windows-10-devices-with-microsoft-intune"></a>Como atribuir aplicações do Office 365 ProPlus 2016 a dispositivos Windows 10 com o Microsoft Intune

Este tipo de aplicação faz com que seja mais fácil atribuir aplicações do Office 365 ProPlus 2016 aos dispositivos que gere que executem o Windows 10. Também pode instalar as aplicações do cliente de ambiente de trabalho do Microsoft Project Online e do Microsoft Visio Pro para Office 365, se tiver licenças para os mesmos. As aplicações que pretende são apresentadas como uma única entrada na lista de aplicações na consola do Intune.


## <a name="before-you-start"></a>Antes de começar

>[!IMPORTANT]
>Este método de instalação do Office só é suportado se não existirem outras versões do Microsoft Office instaladas no dispositivo.

- Os dispositivos em que pretende implementar estas aplicações têm de ter a Atualização para Criativos do Windows 10 ou posterior.
- O Intune só suporta a adição de aplicações do Office que pertençam ao conjunto de aplicações Office 365 ProPlus 2016.
- Se estiverem abertas aplicações do Office quando o Intune instalar o conjunto de aplicações, os utilizadores finais poderão perder os dados dos ficheiros não guardados.
- Este método de instalação não é suportado em dispositivos com o Windows 10.
- O Intune não suporta a instalação de aplicações de ambiente de trabalho do Office 365 da Microsoft Store (denominadas aplicações Office Centennial) num dispositivo em que já implementou aplicações do Office 365 com o Intune. Se instalar esta configuração, poderá causar perda ou danos em dados.


## <a name="get-started"></a>Introdução

1.  Inicie sessão no portal do Azure.
2.  Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3.  No painel **Intune**, escolha **Aplicações móveis**.
4.  Na carga de trabalho **Aplicações móveis**, escolha **Gerir** > **Aplicações**.
5.  Acima da lista de aplicações, escolha **Adicionar**.
6.  No painel **Adicionar Aplicação**, selecione **Conjunto de Aplicações Office 365 ProPlus (Windows 10)**.

## <a name="configure-the-app-suite"></a>Configurar o conjunto de aplicações

Neste passo, selecione as aplicações do Office que pretende atribuir aos dispositivos.

1.  No painel **Adicionar Aplicação**, selecione **Configurar Conjunto de Aplicações**.
2.  No painel **Configurar Conjunto de Aplicações**, selecione as aplicações padrão do Office que pretende atribuir aos dispositivos. Além disso, pode instalar aplicações do cliente de ambiente de trabalho do Microsoft Project Online e do Microsoft Visio Pro para Office 365 se tiver licenças para os mesmos.
3.  Quando tiver terminado, clique em **OK**.

>[!IMPORTANT]
> Depois de ter criado o conjunto de aplicações, não poderá editar as respetivas propriedades. Para configurar propriedades diferentes, elimine o conjunto de aplicações e crie um novo.

## <a name="configure-app-information"></a>Configurar as informações da aplicação

Neste passo, forneça informações acerca do conjunto de aplicações. Estas informações ajudam-no a identificar o conjunto no Intune e também ajudam os utilizadores a encontrá-lo na aplicação Portal da Empresa.

1.  No painel **Adicionar Aplicação**, selecione **Informações do Conjunto de Aplicações**.
2.  No painel **Informações do Conjunto de Aplicações**, especifique as seguintes informações: 
    - **Nome do Conjunto** – introduza o nome do conjunto de aplicações tal como será apresentado no portal da empresa. Certifique-se de que todos os nomes de conjuntos de aplicações que utiliza são exclusivos. Se o nome de um conjunto de aplicações existir em duplicado, apenas uma das aplicações será apresentada aos utilizadores no portal da empresa.
    - **Descrição do Conjunto** – introduza uma descrição para o conjunto de aplicações. Por exemplo, pode listar as aplicações que selecionou para inclusão.
    - **Publicador** – introduza o nome do publicador da aplicação.
    - **Categoria** – em alternativa, selecione uma ou mais categorias de aplicações incorporadas ou uma categoria criada por si. Isto irá permitir que os utilizadores encontrem o conjunto de aplicações mais facilmente quando procurarem no portal da empresa.
    - **Apresentar como aplicação em destaque no Portal da Empresa** – apresente o conjunto de aplicações em destaque na página principal do portal da empresa quando os utilizadores procurarem aplicações.
    - **URL de Informações** – opcionalmente, introduza o URL de um site que contenha informações sobre esta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **URL de Privacidade** – opcionalmente, introduza um URL para um site que contenha informações sobre a privacidade desta aplicação. O URL é apresentado aos utilizadores no portal da empresa.
    - **Programador** – opcionalmente, introduza o nome do programador da aplicação.
    - **Proprietário** – opcionalmente, introduza um nome para o proprietário desta aplicação, por exemplo, **Departamento de RH**.
    - **Notas** – introduza quaisquer notas que pretenda associar esta aplicação.
    - **Carregar Ícone** – carregue um ícone que será apresentado para a aplicação quando os utilizadores procurarem no portal da empresa.
3.  Quando tiver terminado, clique em **OK**.

## <a name="configure-app-settings"></a>Configurar as definições da aplicação

Neste passo, configure as opções de instalação do conjunto de aplicações. As definições aplicam-se a todas as aplicações que adicionou ao conjunto.

1.  No painel **Adicionar Aplicação**, selecione **Definições do Conjunto de Aplicações**.
2.  No painel **Definições do Conjunto de Aplicações**, especifique as seguintes informações: 
    - **Versão do Office** – selecione se quer atribuir a versão de 32 bits ou de 64 bits do Office. Pode instalar a versão de 32 bits em dispositivos de 32 e de 64s bits, mas só pode instalar a versão de 64 bits em dispositivos de 64 bits.
    - **Atualizar Canal** – selecione a forma como o Office é atualizado nos dispositivos. Para obter informações sobre os diferentes canais de atualização, veja a Descrição geral dos canais de atualização do Office 365 ProPlus. Escolha entre: 
        - **Atual**
        - **Diferido**
        - **Canal Atual de Lançamento Inicial**
        - **Canal Diferido de Lançamento Inicial**
    - **Aceitar automaticamente o contrato de licença do utilizador final** – selecione esta opção se não precisar que os utilizadores finais aceitem o contrato de licença. O Intune irá aceitar automaticamente o contrato.
    - **Utilizar a ativação de computadores partilhados** – a ativação de computadores partilhados é utilizada quando existem múltiplos utilizadores a partilhar um computador. Para obter mais informações, veja a Descrição geral da ativação de computadores partilhados para o Office 365 ProPlus.
    - **Idiomas** – o Office é instalado automaticamente nos idiomas suportados que vierem instalados com o Windows no dispositivo dos utilizadores finais. Selecione esta opção se quiser instalar idiomas adicionais no conjunto de aplicações.

>[!IMPORTANT]
> Depois de ter criado o conjunto de aplicações, não poderá editar as respetivas propriedades. Para configurar propriedades diferentes, elimine o conjunto de aplicações e crie um novo.

## <a name="finish-up"></a>Concluir

Quando terminar, no painel **Adicionar Aplicação**, escolha **Guardar**. A aplicação que criou é apresentada na lista de aplicações.

## <a name="error-codes-when-installing-the-app-suite"></a>Códigos de erro ao instalar o conjunto de aplicações

A seguinte tabela lista códigos de erro comuns que poderá encontrar e o respetivo significado.

### <a name="status-for-office-csp"></a>Estado do CSP do Office: 

||||
|-|-|-|
|Estado|Fase|Descrição|
|1460 (ERROR_TIMEOUT)|Transferência|Falha ao transferir a Ferramenta de Implementação do Office|    
|13 (ERROR_INVALID_DATA)|-|Não foi possível verificar a assinatura da Ferramenta de Implementação do Office transferida| 
|Código de erro de CertVerifyCertificateChainPolicy|-|Falha na verificação de certificação da Ferramenta de Implementação do Office transferida|    
|997|WIP|A instalar| 
|0|Após a instalação|Instalação concluída com êxito|    
|1603 (ERROR_INSTALL_FAILURE)|-|Falha numa verificação de pré-requisitos, como:<br>- SxS (tentativa de instalação quando o MSI do Office 2016 se encontra instalado)<br>- Erro de correspondência de versão<br>- Etc.|     
|0x8000ffff (E_UNEXPECTED)|-|Tentativa de desinstalação quando a tecnologia Clique-e-Use do Office não existe no computador.|    
|17002|-|Falha ao concluir o cenário (instalação). Motivos possíveis:<br>- A instalação foi cancelada pelo utilizador<br>- A instalação foi cancelada por outra instalação<br>- Falta de espaço em disco durante a instalação<br>- ID de idioma desconhecido| 
|17004|-|SKUs desconhecidos|   


### <a name="office-deployment-tool-error-codes"></a>Códigos de Erro da Ferramenta de Implementação do Office

|||||
|-|-|-|-|
|Cenário|Código de retorno|IU|Nota| 
|Tentativa de desinstalação quando não existe nenhuma instalação Clique-e-Use ativa|-2147418113, 0x8000ffff ou 2147549183|Código de Erro: 30088-1008<br>Código de Erro: 30125-1011 (404)|Ferramenta de Implementação do Office| 
|Instalação quando já existe uma versão MSI instalada|1603|-|Ferramenta de Implementação do Office| 
|Instalação cancelada pelo utilizador ou por outra instalação|17002|-|Clique-e-Use| 
|Tentativa de instalação da versão de 64 bits num dispositivo com a versão de 32 bits instalada.|1603|-|Código de retorno da Ferramenta de Implementação do Office| 
|Tentativa de instalação de um SKU desconhecido (trata-se de um caso de utilização ilegítima do CSP do Office, visto que devemos passar apenas SKUs válidos)|17004|-|Clique-e-Use| 
|Falta de espaço|17002|-|Clique-e-Use| 
|O cliente da tecnologia clique-e-use falhou ao iniciar (inesperado)|17000|-|Clique-e-Use| 
|O cliente da tecnologia clique-e-use falhou ao colocar o cenário em fila (inesperado)|17001|-|Clique-e-Use| 

## <a name="next-steps"></a>Próximos passos

Agora pode atribuir as aplicações aos grupos que escolher. Para obter ajuda, veja [Como atribuir aplicações a grupos](/intune-azure/manage-apps/deploy-apps).