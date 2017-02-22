---
title: "Configurar um serviço de gestão de despesas de telecomunicações | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: configurar o serviço de gestão de despesas de telecomunicações Saaswedo a integrar com o Intune."
keywords: Saaswedo
author: staciebarker
ms.author: stabar
manager: angrobe
ms.date: 01/24/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: b7bf5802-4b65-4aeb-ac99-8e639dd89c2a
ms.reviewer: sumitp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 915d61344a3c1d388305dd51b1e2463bd2e32770
ms.openlocfilehash: 8d94fec099e1dc8918077062fb73b94a5973ea96

---

# <a name="set-up-a-telecom-expense-management-service-in-intune-azure-preview"></a>Configurar um serviço de gestão de despesas de telecomunicações na pré-visualização do Azure no Intune
[!INCLUDE[azure_preview](../includes/azure_preview.md)]

O Intune integrou-se com a solução de gestão de despesas de telecomunicações Datalert, do programador de software de terceiros Saaswedo. O Datalert é um software de gestão de despesas de telecomunicações em tempo real que lhe permite gerir a utilização de dados de telecomunicações e evitar excessos dispendiosos e inesperados de dados e roaming nos seus dispositivos geridos pelo Intune. A integração do Intune com o Datalert permite-lhe configurar, monitorizar e impor centralmente limites de utilização de dados nacionais e de roaming através de alertas automatizados quando os limites excedem os limiares definidos. Pode configurar o serviço para aplicar medidas diferentes a indivíduos ou grupos de utilizadores finais, incluindo a desativação do roaming, quando excedem o limiar. Na consola de gestão Datalert poderá encontrar relatórios que disponibilizam informações de monitorização e de utilização de dados.

Para poder utilizar o serviço Datalert com o Intune, tem de configurar as definições na consola Datalert e no Intune. A ligação tem de ser ativada para o serviço Datalert e para o Intune. Se o lado da ligação do Datalert estiver ativado, mas o lado do Intune não, o Intune recebe a comunicação, mas ignora-a.

>[!NOTE]
>Para ativar esta funcionalidade no inquilino de avaliação, [contacte o suporte da Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune) para a ativação e o suporte do Datalert para obter as licenças de software obrigatórias.

## <a name="supported-platforms"></a>Plataformas suportadas

- Samsung Knox
- iOS 8.0 e posterior

## <a name="prerequisites"></a>Pré-requisitos

- Uma subscrição do Microsoft Intune
- Uma subscrição do serviço de gestão de despesas de telecomunicações Datalert

## <a name="list-of-telecom-expense-management-providers"></a>Lista de fornecedores de gestão de despesas de telecomunicações

Atualmente, o Intune integra-se com os seguintes fornecedores de gestão de despesas de telecomunicações:

[Serviço de gestão de despesas de telecomunicações Datalert da Saaswedo](http://www.datalert.biz/)

## <a name="configure-intune-to-work-with-the-datalert-service"></a>Configurar o Intune para funcionar com o serviço Datalert

 

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Outros** > **Intune**.
3. No painel **Intune**, escolha **Configurar dispositivos**.
2. No painel **Configuração do Dispositivo**, escolha **Configuração** > **Gestão de Despesas de Telecomunicações**.
2. Em **Gestão de Despesas de Telecomunicações**, selecione **Estado da ligação**.

3. Selecione **Lista de fornecedores de serviços TEM** e, em seguida, selecione o seu fornecedor na lista apresentada. É apresentada uma página específica do seu fornecedor. Para a Saaswedo, é apresentada a página do Datalert. Terá de trabalhar com o Datalert da Saaswedo para comprar uma subscrição.

4. Na consola de gestão **Datalert**:

    a. Aceda ao separador **Definições** e, em seguida, à secção **Configuração de MDM**.

    b. Selecione **Desbloquear** para poder introduzir as definições na página.

    c. Para **Servidor de MDM**, selecione **Microsoft Intune**.

    d. Para **ID do Inquilino**, introduza o seu ID de inquilino do Intune e selecione o botão **Ligação**. Selecionar **Ligação** faz com que o Datalert consulte o Intune para garantir que não existem ligações prévias do Datalert com o Intune. Alguns segundos depois, aparece a página de início de sessão da Microsoft, seguida da autenticação do Datalert no Azure.

    e. Na página de autenticação da Microsoft, selecione **Aceitar**. É redirecionado para uma página de “Obrigado” do Datalert, que se fecha alguns segundos depois. O Datalert valida a ligação e apresenta marcas de verificação verdes junto a uma lista de itens que validou. Se a validação falhar, verá uma mensagem em vermelho. Se tal acontecer, contacte o Suporte do Datalert para obter ajuda.

5. Aguarde alguns minutos e, em seguida, aceda ao portal do Azure para verificar se o estado da Ligação aparece como **Ativo**. 

    >[!NOTE]
    >Para ativar esta funcionalidade no seu inquilino de avaliação, [contacte o suporte da Microsoft](https://docs.microsoft.com/intune/troubleshoot/how-to-get-support-for-microsoft-intune).

6. Volte à consola de gestão Datalert e configure as linhas de dados:

    a. Aceda ao separador **Definições**.

    b. Aceda ao assistente de **Configuração** e siga os passos.



O serviço Datalert está ativo e começa a monitorizar a utilização de dados e a desativar os dados de roaming e via rede móvel nos dispositivos que excedem os limites de utilização configurados.

## <a name="turning-off-the-datalert-service"></a>Desativar o serviço Datalert

Se desativar o serviço Datalert no portal do Azure:

- Todas as medidas que foram aplicadas aos dispositivos, devido a violações anteriores dos limites de utilização, serão anuladas.
- Os utilizadores deixam de estar bloqueados em relação ao acesso a dados e roaming.
- O Intune continua a receber sinais provenientes do serviço, mas ignora-os.

**Para desativar o serviço**

1. No painel **Gestão de Despesas de Telecomunicações** do portal do Azure, selecione **Desativar**.

2. Selecione **Guardar**.

## <a name="viewing-data-usage-and-roaming-reports"></a>Ver relatórios de utilização de dados e de roaming

Neste momento, os relatórios de utilização de dados só estão disponíveis na consola de gestão do Datalert da Saaswedo.



<!--HONumber=Feb17_HO2-->


