---
title: Integrar o Jamf Pro com o Microsoft Intune para conformidade
titleSuffix: Microsoft Intune
description: Utilize as políticas de conformidade da Microsoft Intune com o Azure Ative Directory Conditional Access para ajudar a integrar e proteger dispositivos geridos pelo Jamf.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 02/18/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 4b6dcbcc-4661-4463-9a36-698d673502c6
ms.reviewer: jinyoon
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9dab1025e283ed1591c22b03ed4e3a61d40a20c3
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515089"
---
# <a name="integrate-jamf-pro-with-intune-for-compliance"></a>Integrar o Jamf Pro com o Intune para conformidade

Quando a sua organização utiliza o [Jamf Pro](https://www.jamf.com) para gerir dispositivos macOS, pode utilizar as políticas de conformidade do Microsoft Intune com o Azure Ative Directory (Azure AD) Conditional Access para garantir que os dispositivos da sua organização estão em conformidade antes de poderem aceder aos recursos da empresa. Este artigo irá ajudá-lo a configurar a integração do Jamf com o Intune.

Quando o Jamf Pro se integrar com o Intune, pode sincronizar os dados de inventário dos dispositivos macOS com o Intune, através do Azure AD. O motor de conformidade da Intune analisa então os dados do inventário para gerar um relatório. A análise de Intune é combinada com inteligência sobre a identidade Azure AD do utilizador do dispositivo para impulsionar a aplicação através do Acesso Condicional. Os dispositivos conformes com as políticas de Acesso Condicional podem ter acesso aos recursos da empresa protegidos.

Depois de configurar a integração, configurará então a Jamf e a [Intune para impor o cumprimento do Acesso Condicional](conditional-access-assign-jamf.md) em dispositivos geridos pela Jamf.

## <a name="prerequisites"></a>Pré-requisitos

### <a name="products-and-services"></a>Produtos e serviços

É necessário configurar o Acesso Condicional com o Jamf Pro:

- Jamf Pro 10.1.0 ou posterior
- [Aplicação Portal da Empresa para macOS](https://aka.ms/macoscompanyportal)
- dispositivos macOS com OS X 10.12 Yosemite ou posteriormente

### <a name="network-ports"></a>Portas de rede

<!-- source: https://support.microsoft.com/en-us/help/4519171/troubleshoot-problems-when-integrating-jamf-with-microsoft-intune -->
As seguintes portas devem ser acessíveis à Jamf e ao Intune para integrar corretamente:

- **Insinton :** Porto 443
- **Apple**: Portos 2195, 2196 e 5223 (notificações push to Intune)
- **Jamf**: Portas 80 e 5223

Para permitir que a APNS funcione corretamente na rede, também deve ativar as ligações de saída e redirecionar a partir de:

- o bloco Apple 17.0.0.0.0/8 sobre as portas TCP 5223 e 443 de todas as redes de clientes.
- portas 2195 e 2196 dos servidores Jamf Pro.  

Para obter mais informações sobre estes portos, consulte os seguintes artigos:

- [Requisitos de configuração de rede intonantes e largura de banda.](../fundamentals/network-bandwidth-use.md)
- Portas de [rede utilizadas pelo Jamf Pro](https://www.jamf.com/jamf-nation/articles/34/network-ports-used-by-jamf-pro) na jamf.com.
- [Portas TCP e UDP utilizadas por produtos de software da Apple](https://support.apple.com/HT202944) em support.apple.com

## <a name="connect-intune-to-jamf-pro"></a>Conecte Intune ao Jamf Pro

Para ligar intune com o Jamf Pro:

1. Crie uma nova aplicação no Azure.
2. Enable Intune para integrar com jamf Pro.
3. Configure o acesso condicional no Jamf Pro.

### <a name="create-an-application-in-azure-active-directory"></a>Criar uma aplicação no Diretório Ativo azure

1. No [portal Azure,](https://portal.azure.com)vá ao **Azure Ative Directory** > Registos de **Aplicações,** e depois selecione **Nova inscrição.**

2. No **Registo de uma** página de candidatura, especifique os seguintes detalhes:

   - Na secção **Nome,** introduza um nome de aplicação significativo, por **exemplo, acesso condicional jamf**.
   - Para a secção de tipos de **conta suportada,** selecione **Contas em qualquer diretório organizacional**.
   - Para **redirecionar uri,** deixe o padrão da Web e, em seguida, especifique o URL para a sua instância Jamf Pro.

3. Selecione **Register** para criar a aplicação e para abrir a página **'Visão Geral'** para a nova aplicação.

4. Na página de **visão geral** da aplicação, copie o valor de ID **da Aplicação (cliente)** e grave-o para posterior utilização. Vai precisar deste valor em procedimentos posteriores.

5. Selecione **Certificados e segredos** em **Gerir**. Selecione o botão secreto do **novo cliente.** Introduza um valor em **Descrição,** selecione qualquer opção para **Expirar** e escolha **Adicionar**.

   > [!IMPORTANT]
   > Antes de sair desta página, copie o valor para o segredo do cliente e grave-o para posterior utilização. Necessitará deste valor em procedimentos posteriores. Este valor não está novamente disponível, sem recriar o registo da aplicação.

6. Selecione **permissões API** em **'Gerir**. 

7. Na página de permissões da API, remova todas as permissões desta aplicação selecionando o **...** ícone ao lado de cada permissão existente. Note que isto é necessário; a integração não terá sucesso se houver permissões extra inesperadas no registo desta aplicação.

8. Em seguida, adicionaremos permissões para atualizar os atributos do dispositivo. Na parte superior à esquerda da página de **permissões DaPI,** selecione **Adicionar uma permissão** para adicionar uma nova permissão. 

9. Na página de **permissões Solicitar API,** selecione **Intune**, e, em seguida, selecione **permissões**de Pedido . Selecione apenas a caixa de verificação para **update_device_attributes** e guarde a nova permissão.

10. Em seguida, conceda o consentimento da administração para esta app, selecionando o **consentimento do administrador grant para\<seu _inquilino>_**  no topo esquerdo da página de **permissões da API.** Poderá ter de reautenticar a sua conta na nova janela e conceder o acesso ao pedido seguindo as instruções.  

11. Refresque a página clicando no botão **Refresh** na parte superior da página. Confirme que **o** consentimento da administração foi concedido para a update_device_attributes permissão. 

12. Após a registo da aplicação com sucesso, as permissões da API devem conter apenas uma permissão chamada **update_device_attributes** e devem aparecer da seguinte forma:

   ![Permissões bem sucedidas](./media/conditional-access-integrate-jamf/sucessfull-app-registration.png)

   O processo de registo da aplicação em Azure AD está completo.

    > [!NOTE]
    > Se o segredo do cliente expirar, terá de criar um novo segredo de cliente no Azure e, em seguida, atualizar os dados de Acesso Condicional no Jamf Pro. O Azure permite-lhe ter o segredo antigo e a nova chave ativa para evitar interrupções no serviço.

### <a name="enable-intune-to-integrate-with-jamf-pro"></a>Integrar o Intune com o Jamf Pro

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **a administração do Inquilino** > **Conectores e fichas** > gestão de **dispositivos parceiros.**

3. Ative o *Conector* de Conformidade para o Jamf colando o ID de aplicação que guardou durante o procedimento anterior no **Especifique o ID** da aplicação de diretório ativo Azure para o campo Jamf.

4. Selecione **Guardar**.

### <a name="configure-microsoft-intune-integration-in-jamf-pro"></a>Configurar a Integração do Microsoft Intune no Jamf Pro

1. Ativar a ligação na consola Jamf Pro:

   1. Abra a consola Jamf Pro e navegue para **a Global Management** > Acesso **Condicional.** Clique no botão **Editar** no separador **macOS Intune Integration.**
   2. Selecione a caixa de verificação para ativar a **integração intune para macOS**.
   3. Forneça as informações necessárias sobre o seu inquilino Azure, incluindo **Localização,** Nome de **Domínio,** id **de aplicação,** e o valor para o segredo do *cliente* que guardou quando criou a app em Azure AD.
   4. Selecione **Guardar**. O Jamf Pro testa as suas definições e verifica o seu sucesso.

   Volte à página de gestão de **dispositivos parceiros** em Intune para completar a configuração.

2. Intune, vá à página de gestão de **dispositivos parceiro.** Em configurações de **conectores** configure grupos para atribuição:

   - Selecione **Incluir** e especificar quais os grupos de utilizador que pretende atingir para a inscrição do macOS com o Jamf.
   - Utilize **o Excluir** para selecionar grupos de Utilizadores que não se matriculem com o Jamf e, em vez disso, matricularão os seus Macs diretamente com o Intune.

   *Excluir* substituições *Inclua*, o que significa que qualquer dispositivo que esteja em ambos os grupos é excluído do Jamf e direcionado para se inscrever na Intune.

   >[!NOTE]
   > Este método de inclusão e exclusão de grupos de utilizadores afeta a experiência de inscrição do utilizador. Qualquer utilizador com um Mac já matriculado no Jamf ou no Intune que depois seja direcionado para se inscrever com o outro MDM deve desinscrever o seu dispositivo e depois reinseri-lo com o novo MDM antes que a gestão do dispositivo funcione corretamente.

3. Selecione **Avaliar** para determinar quantos dispositivos serão matriculados com o Jamf, com base nas configurações do seu grupo.

4. Selecione **Guardar** quando estiver pronto para aplicar a configuração.

5. Para prosseguir, terá de utilizar [o Jamf para implementar o Portal da Empresa para o Mac,](conditional-access-assign-jamf.md#deploy-the-company-portal-app-for-macos-in-jamf-pro) para que os utilizadores possam registar os seus dispositivos para insintonização.

## <a name="set-up-compliance-policies-and-register-devices"></a>Definir as políticas de conformidade e registar dispositivos

Depois de configurar a integração entre intune e Jamf, tem de aplicar políticas de [conformidade a dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md).

## <a name="disconnect-jamf-pro-and-intune"></a>Desligar Jamf Pro e Intune

Se já não utilizar o Jamf Pro para gerir os Macs na sua organização e pretender que os utilizadores sejam geridos pela Intune, tem de remover a ligação entre o Jamf Pro e o Intune. Retire a ligação utilizando a consola Jamf Pro.

1. No Jamf Pro, vá à **Global Management** > **Acesso Condicional.** No separador **macOS Intune Integração,** selecione **Editar**.

2. Limpe a **Integração Enable Intune para a** caixa de verificação macOS.

3. Selecione **Guardar**. O Jamf Pro envia a sua configuração para Intune e a integração será terminada.

4. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

5. Selecione **a administração** do Inquilino > **Conectores e fichas** > **gestão** do dispositivo partner para verificar se o estado está agora **terminado**.

   > [!NOTE]
   > Os dispositivos Mac da sua organização serão removidos na data (3 meses) mostrada na sua consola.

## <a name="next-steps"></a>Próximos passos

- [Aplicar políticas de conformidade a dispositivos geridos pelo Jamf](conditional-access-assign-jamf.md)
- [Data Jamf envia para Intune](data-jamf-sends-to-intune.md)
