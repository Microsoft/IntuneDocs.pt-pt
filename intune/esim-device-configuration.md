---
title: Ativar ligações de dados eSIM no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou utilize o eSIM para obter acesso a dados e à Internet através de planos de dados diferentes. No Intune, adicione ou importe códigos de ativação e, em seguida, atribua estes códigos de ativação através de um perfil de configuração. Também pode monitorizar os perfis eSIM e verificar o estado dos dispositivos ativados para eSIM.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 7/31/2018
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: e241dc534427b97086013a12391f06bd2f342779
ms.sourcegitcommit: 7c251948811b8b817e9fe590b77f23aed95b2d4e
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/15/2019
ms.locfileid: "67883263"
---
# <a name="configure-esim-cellular-profiles-in-intune---public-preview"></a>Configurar perfis celulares eSIM no Intune – pré-visualização pública

> [!NOTE]
> A Microsoft quer saber a sua opinião. Envie perguntas ou inicie um debate ao enviar um e-mail para `eSIMonIntune@microsoft.com`.

## <a name="introduction"></a>Introdução

O eSIM é um chip SIM incorporado e permite-lhe ligar-se à Internet através de uma ligação de dados celular num dispositivo compatível com eSIM, como o [Surface Pro LTE](https://www.microsoft.com/surface/business/surface-pro). Com um eSIM, não precisa de obter um cartão SIM junto do seu operador de rede móvel. Enquanto viajante global, pode também alternar entre operadores de redes móveis e planos de dados para estar sempre ligado.

Por exemplo, poderá ter um plano de dados celular para o trabalho e outro plano de dados com uma operadora de rede móvel diferente para utilização pessoal. Quando viaja, pode aceder à Internet ao localizar operadoras de redes móveis com planos de dados numa determinada área.

No Intune, pode importar códigos de ativação de utilização única fornecidos pela sua operadora de rede móvel. Para configurar planos de dados celulares no módulo eSIM, implemente esses códigos de ativação nos seus dispositivos compatíveis com eSIM. Quando o Intune instalar o código de ativação, o módulo de hardware eSIM irá utilizar os dados no código de ativação para contactar a operadora de rede móvel. Quando a instalação for concluída, o perfil eSIM será transferido para o dispositivo e configurado para a ativação celular.

Para implementar o eSIM nos seus dispositivos com o Intune, é necessário o seguinte:

- **dispositivos compatíveis com o Esim**, como o LTE de superfície: Veja [se seu dispositivo dá suporte a Esim](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data). Em alternativa, veja uma lista com [alguns dos dispositivos compatíveis com eSIM conhecidos](#esim-capable-devices) (neste artigo).
- **Um PC com o Windows 10 Fall Creators Update** (compilação 1709 ou posterior) que esteja inscrito e gerido pela MDM no Intune.
- **Códigos de ativação** fornecidos pela sua operadora de rede móvel. Estes códigos de ativação de utilização única são adicionados ao Intune e implementados nos seus dispositivos compatíveis com eSIM. Contacte a sua operadora de rede móvel para adquirir códigos de ativação eSIM.

## <a name="deploy-esim-to-devices---overview"></a>Implementar o eSIM em dispositivos – descrição geral

Para implementar o eSIM em dispositivos, um Administrador tem de concluir as seguintes tarefas:

1. Importar códigos de ativação fornecidos pela sua operadora de rede móvel
2. Criar um grupo de dispositivos do Azure Active Directory (Azure AD) que inclua os seus dispositivos compatíveis com eSIM
3. Atribuir o grupo do Azure AD ao seu conjunto de subscrições importadas.
4. Monitorizar a implementação

Este artigo orienta-o ao longo destes passos.

## <a name="esim-capable-devices"></a>Dispositivos compatíveis com eSIM

Os seguintes dispositivos foram anunciados como sendo compatíveis com eSIM ou encontram-se no mercado atualmente. Além disso, verifique se [o seu dispositivo suporta o eSIM](https://support.microsoft.com/help/4020763/windows-10-use-esim-for-cellular-data).

- Acer Swift 7
- Asus NovaGo TP370QL
- Asus TP401
- Asus Transformer Mini T103
- HP EliteBook G5
- HP Envy x2
- HP ProBook G5
- Lenovo Miix 630
- Lenovo T480
- Samsung Galaxy Book
- Surface Pro LTE
- HP Spectre fólio 13
- C630 do Lenovo Yoga

## <a name="step-1-add-cellular-activation-codes"></a>Passo 1: Adicionar códigos de ativação de celular

Os códigos de ativação celulares são fornecidos pela sua operadora de rede móvel num ficheiro separado por vírgulas (CSV). Quando tiver este ficheiro, adicione-o ao Intune ao seguir os seguintes passos:

1. Inicie sessão no [portal do Azure](https://portal.azure.com/).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** > **Perfis celulares eSIM** > **Adicionar**.
4. Selecione o ficheiro CSV que contém os seus códigos de ativação.
5. Selecione **OK** para guardar as alterações.

#### <a name="csv-file-requirements"></a>Requisitos do ficheiro CSV

Ao trabalhar com o ficheiro CSV que contém os códigos de ativação, certifique-se de que você ou a sua operadora de rede móvel cumprem os seguintes requisitos:

- O ficheiro tem de estar no formato CSV (nomedeficheiro.csv).
- A estrutura do ficheiro tem de respeitar um formato rigoroso. Caso contrário, a importação irá falhar. O Intune verifica o ficheiro durante a importação, que irá falhar se forem encontrados erros.
- Os códigos de ativação são utilizados uma vez. Não recomendamos que importe códigos de ativação importados anteriormente, pois poderão causar problemas ao implementar no mesmo dispositivo ou num dispositivo diferente.
- Cada ficheiro deve ser específico a uma única operadora de rede móvel e todos os códigos de ativação devem ser específicos ao mesmo plano de faturação. O Intune distribui os códigos de ativação de forma aleatória para os dispositivos abrangidos. Não existem garantias de que dispositivo irá obter um determinado código de ativação.
- Pode ser importado um máximo de 1000 códigos de ativação num ficheiro CSV.

#### <a name="csv-file-example"></a>Exemplo de ficheiro CSV

1. A primeira linha e a primeira célula do ficheiro CSV contêm o URL do serviço de ativação eSIM da operadora de rede móvel, que é denominado SM-DP+ (servidor Subscription Manager Data Preparation). O URL deve ser um nome de domínio completamente qualificado (FQDN) sem vírgulas.
2. A partir da segunda linha, encontram-se os códigos de ativação de utilização única e exclusiva que incluem dois valores:

    1. Na primeira coluna, encontra-se o ICCID exclusivo (o identificador do chip SIM)
    2. Na segunda coluna, encontra-se o ID Correspondente, com apenas uma vírgula a separá-los (e nenhuma vírgula no final). Veja o seguinte exemplo:

        ![Ficheiro CSV de exemplo de códigos de ativação da operadora de rede móvel](./media/esim-device-configuration/url-activation-code-examples.png)

3. O nome do ficheiro CSV torna-se o nome do conjunto de subscrições celulares no portal do Azure. Na imagem anterior, o nome do ficheiro é `UnlimitedDataSkynet.csv`. Por isso, o Intune denomina o conjunto de subscrições `UnlimitedDataSkynet.csv`:

    ![O nome do ficheiro CSV de exemplo de códigos de ativação torna-se o nome do conjunto de subscrições celulares](./media/esim-device-configuration/subscription-pool-name-csv-file.png)

## <a name="step-2-create-an-azure-ad-device-group"></a>Passo 2: Criar um grupo de dispositivos do Azure AD

Crie um grupo de Dispositivos que inclua os dispositivos compatíveis com eSIM. Consulte os passos em [Adicionar grupos](groups-add.md).

> [!NOTE]
> - Apenas os dispositivos são abrangidos. Os utilizadores não são abrangidos.
> - Recomendamos que crie um grupo de dispositivos estático do Azure AD que inclua os seus dispositivos eSIM. Utilizar um grupo garante que abrange apenas dispositivos eSIM.

## <a name="step-3-assign-esim-activation-codes-to-devices"></a>Passo 3: Atribuir códigos de ativação do eSIM a dispositivos

Atribua o perfil ao grupo do Azure AD que inclui os seus dispositivos eSIM.

1. No [portal do Azure](https://portal.azure.com/), selecione **Todos os Serviços**, filtre o **Intune** e selecione **Microsoft Intune**.
2. Selecione **Configuração do dispositivo** > **Perfis celulares eSIM** > **Perfis**.
3. Na lista de perfis, selecione o conjunto de subscrições celulares eSIM que pretende atribuir e, em seguida, selecione **Atribuições**.
4. Opte por **Incluir** ou **Excluir** grupos e, em seguida, selecione os grupos.

    ![Incluir o grupo de dispositivos para atribuir o perfil](./media/esim-device-configuration/include-exclude-groups.png)

5. Ao selecionar os seus grupos, estará a escolher um grupo do Azure AD. Para selecionar múltiplos grupos, utilize a tecla **Ctrl** e selecione os grupos.
6. Quando terminar, selecione **Guardar** para guardar as suas alterações.

Os códigos de ativação eSIM são utilizados uma vez. Após o Intune instalar um código de ativação num dispositivo, o módulo eSIM contactará a operadora de rede móvel para transferir o perfil celular. Este contacto conclui o registo do dispositivo com a rede da operadora de rede móvel.

## <a name="step-4-monitor-deployment"></a>Passo 4: Monitorar a implantação

#### <a name="review-the-deployment-status"></a>Rever o estado de implementação

Após atribuir o perfil, pode monitorizar o estado da implementação de um conjunto de subscrições.

1. Inicie sessão no [portal do Azure](https://portal.azure.com/).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** > **Perfis celulares eSIM**. Estão listados todos os seus conjuntos de subscrições celulares eSIM.
4. Selecione uma subscrição e reveja o **Estado da Implementação**.

#### <a name="check-the-profile-status"></a>Verificar o estado do perfil
Depois de criar o perfil do dispositivo, o Intune disponibiliza gráficos. Estes gráficos apresentam o estado de um perfil, como a atribuição com êxito a dispositivos ou se o perfil mostra um conflito.

1. Selecione **Configuração do dispositivo** > **Perfis celulares eSIM** > Selecione uma subscrição existente.
2. No separador **Descrição Geral**, o gráfico geográfico na parte superior mostra o número de dispositivos atribuídos à implementação específica do conjunto de subscrições celulares eSIM.

    Também mostra o número de dispositivos de outras plataformas que são atribuídos ao mesmo perfil do dispositivo.

    O Intune mostra o estado da instalação e entrega do código de ativação direcionado aos dispositivos.

    - **Dispositivo não sincronizado**: O dispositivo de destino não contatou o Intune desde que a política de implantação do eSIM foi criada
    - **Ativação pendente**: Um estado transitório quando o Intune estiver instalando ativamente o código de ativação no dispositivo
    - **Ativo**: Instalação do código de ativação bem-sucedida
    - **Falha na ativação**: Falha na instalação do código de ativação – consulte o guia de solução de problemas.

#### <a name="view-the-detailed-device-status"></a>Ver o estado detalhado do dispositivo

Pode monitorizar e ver uma lista detalhada dos dispositivos em Estado do Dispositivo.**

1. Selecione **Configuração do dispositivo** > **Perfis celulares eSIM** > Selecione uma subscrição existente.
2. Selecione **Estado do Dispositivo**. O Intune mostra detalhes adicionais sobre o dispositivo:

    - **Nome do dispositivo**: Nome do dispositivo que está direcionado
    - **Usuário**: Usuário do dispositivo registrado
    - **ICCID**: O código exclusivo fornecido pelo Mobile opera no código de ativação instalado no dispositivo
    - **Status da ativação**: Status de entrega e instalação do Intune do código de ativação no dispositivo
    - **Status da rede celular**: Estado fornecido pela operadora móvel. Contacte a operadora de rede móvel para resolver problemas.
    - **Último check-in**: Data em que o dispositivo se comunica pela última vez com o Intune

#### <a name="monitor-esim-profile-details-on-the-actual-device"></a>Monitorizar os detalhes do perfil eSIM no dispositivo real

1. No seu dispositivo, abra as **Definições** > aceda a **Rede e Internet**.
2. Selecione **Rede Móvel** > **Gerir perfis de eSIM**
3. Os perfis eSIM estão listados:

    ![Ver os perfis eSIM nas definições do seu dispositivo](./media/esim-device-configuration/device-settings-cellular-profiles.png)

## <a name="remove-the-esim-profile-from-device"></a>Remover o perfil eSIM do dispositivo

Ao remover o dispositivo do grupo do Azure AD, o perfil eSIM também será removido. Certifique-se de que:

1. Confirma se está a utilizar o grupo do Azure AD dos dispositivos eSIM.
2. Acede ao grupo do Azure AD e remove o dispositivo do grupo.
3. Quando o dispositivo removido contactar o Intune, a política atualizada é avaliada e o perfil eSIM removido.

O perfil eSIM também será removido quando o dispositivo for [extinto](devices-wipe.md#retire) ou a inscrição do dispositivo for anulada pelo utilizador ou quando a [ação de reposição remota de dispositivos](devices-wipe.md#wipe) for executada no dispositivo.

> [!NOTE]
> Remover o perfil poderá não interromper o processo de faturação. Contacte a sua operadora de rede móvel para verificar o estado da faturação do seu dispositivo.

## <a name="best-practices--troubleshooting"></a>Melhores práticas e resolução de problemas

- Certifique-se de que o seu ficheiro CSV está formatado corretamente. Confirme se o ficheiro não inclui códigos duplicados, múltiplas operadoras de rede móvel ou planos de dados diferentes. Tenha em atenção que cada ficheiro tem de ser exclusivo de uma operadora de rede móvel e plano de dados celular.
- Crie um grupo estático de dispositivos do Azure AD que inclua apenas os dispositivos eSIM direcionados.
- Se ocorrer um problema com o estado da implementação, verifique o seguinte:
  - **Formato de arquivo não adequado**: Consulte **a etapa 1: Adicione códigos** de ativação de celular (neste artigo) sobre como formatar corretamente o arquivo.
  - **Falha de ativação de celular, contate a operadora móvel**: O código de ativação não pode ser ativado em sua rede. Também é possível que a ativação celular e a transferência do perfil tenham falhado.

## <a name="next-steps"></a>Passos Seguintes
[Configurar perfis de dispositivo](device-profiles.md)
