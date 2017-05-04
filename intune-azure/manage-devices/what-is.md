---
title: Gerir dispositivos com o Intune
titleSuffix: Intune Azure preview
description: "Pré-visualização do Azure no Intune: saiba como ver os dispositivos que gere com o Intune e como desempenhar várias operações neles."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 04/13/2017
ms.topic: get-started-article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.suite: ems
ms.custom: intune-azure
translationtype: Human Translation
ms.sourcegitcommit: e5dd7cb5b320df7f443b52a1b502027fa3c4acaf
ms.openlocfilehash: 25a46754f6c7e44b3f4fef7e8eef015cf559e31f
ms.lasthandoff: 04/19/2017


---

# <a name="what-is-microsoft-intune-device-management"></a>O que é a gestão de dispositivos do Microsoft Intune?


[!INCLUDE[azure_preview](../includes/azure_preview.md)]

A carga de trabalho **Dispositivos** dá-lhe informações aprofundadas sobre os dispositivos que gere e permite-lhe realizar tarefas remotas nesses dispositivos. Para aceder à carga de trabalho:

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Dispositivos**.

Agora, escolha uma das seguintes opções:

- **Descrição geral** – Obtenha informações sobre os dispositivos que inscreveu e os sistemas operativos executados em cada dispositivo.
- **Gerir** – Escolha **Todos os Dispositivos** para ver uma lista de todos os dispositivos que gere.
    Selecione um desses dispositivos na lista para abrir o painel <*nome do dispositivo*> **Descrição Geral**, onde pode selecionar uma das opções:
    - **Descrição Geral** – Veja as informações gerais do dispositivo, incluindo informações sobre o nome, o proprietário, se é um dispositivo BYOD, quando foi registado pela última vez e muito mais.

    - **Hardware** – Veja informações mais detalhadas sobre o dispositivo, incluindo o espaço de armazenamento livre, o modelo e fabricante, entre outros.
    ![Inventário do hardware do dispositivo gerido](./media/hardware-inventory.png)
    - **Aplicações Detetadas** – Apresenta uma lista de todas as aplicações que o Intune encontrou instaladas no dispositivo.
    ![Nó de aplicações detetadas](./media/detected-applications.png)
- **Monitorizar** – Escolha **Ações do Dispositivo** para ver uma lista das ações do dispositivo que foram realizadas nos dispositivos que gere e o estado atual dessas ações.
![Monitorizar ações de dispositivos](./media/monitor-device-actions.png)
- **Ajuda e Suporte** – apresenta ligações para a documentação de suporte e de resolução de problemas.

## <a name="available-device-actions"></a>Ações do dispositivo disponíveis

Além disso, pode realizar as seguintes ações remotas no dispositivo (nem todas as ações são suportadas por todas as plataformas de dispositivos):

### <a name="remove-company-data"></a>**Remover dados da empresa**
Remove apenas os dados da empresa geridos pelo Intune. Não remove os dados pessoais do dispositivo. O dispositivo deixará de ser gerido pelo Intune e já não poderá aceder aos recursos da empresa (não suportado para dispositivos Windows que estejam associados ao Azure Active Directory).

### <a name="factory-reset"></a>**Reposição de fábrica**
Repõe as predefinições do dispositivo. O dispositivo deixará de ser gerido pelo Intune e os dados pessoais e da empresa são removidos. Não pode anular esta ação.

### <a name="remote-lock"></a>**Bloqueio remoto**
Bloqueia o dispositivo. O proprietário do dispositivo tem de utilizar o código de acesso para desbloqueá-lo. Só pode bloquear remotamente um dispositivo que tenha um PIN ou uma palavra-passe definida.

### <a name="reset-passcode"></a>**Repor código de acesso**
Gera um novo código de acesso para o dispositivo, que será apresentado no painel <*nome do dispositivo*> **Descrição Geral**.

### <a name="bypass-activation-lock"></a>**Ignorar Bloqueio de Ativação**
Esta ação remove o bloqueio de ativação de um dispositivo iOS sem o ID Apple e a palavra-passe do utilizador. Depois de ignorar o bloqueio de ativação, o dispositivo ativa novamente o bloqueio de ativação quando a aplicação Encontrar o Meu iPhone é iniciada. Ignore o bloqueio de ativação apenas se tiver acesso físico ao dispositivo.

### <a name="fresh-start"></a>**Fresh Start**

Remove todas as aplicações que foram instaladas nos PCs a executar a Atualização para Criativos do Windows 10 e, em seguida, atualiza automaticamente os PCs para a versão mais recente do Windows.
Esta ação pode ajudar a remover aplicações (OEM) que vêm frequentemente pré-instaladas em PCs novos. Pode configurar se os dados de utilizador são retidos ao efetuar esta ação. Neste caso, as aplicações e as definições são removidas, mas o conteúdo da pasta Raiz dos utilizadores é mantido.


### <a name="lost-mode"></a>**Modo perdido**
Se um dispositivo iOS for perdido ou tiver sido roubado, poderá ativar o modo perdido. Esta opção permite-lhe especificar uma mensagem e um número de telefone que serão apresentados no ecrã de bloqueio do dispositivo. Para efetuar este procedimento:
1.    No painel de propriedades de um dispositivo iOS, escolha **Mais** > **Modo perdido**.
2.    No painel **Modo perdido**, ative o modo perdido, introduza a mensagem que será apresentada e, opcionalmente, um número de telefone de contacto.
3.    Clique em **OK**.
Quando ativar o modo perdido, bloqueia qualquer utilização do dispositivo. O utilizador final não pode aceder ao dispositivo até desativar o modo perdido. Quando o modo perdido está ativado, pode utilizar a ação **Localizar dispositivo** para saber onde este se encontra.
Para utilizar o modo perdido, o dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado.

### <a name="locate-device"></a>**Localizar dispositivo**
Utilize esta ação remota para apresentar a localização de um dispositivo iOS perdido ou roubado num mapa. O dispositivo tem de ser um dispositivo iOS pertencente à empresa, inscrito através do DEP, que esteja no modo supervisionado. Para utilizar esta ação, o dispositivo tem de ter o modo perdido ativado.
1.    No painel de propriedades de um dispositivo iOS, escolha **Mais** > **Localizar dispositivo**.
2.    Depois de o dispositivo ser localizado, é apresentada a sua localização no painel **Localizar dispositivo**.
    ![Painel Localizar dispositivo](./media/locate-device.png)

>[!NOTE]
>Por motivos de privacidade, a ampliação do mapa é limitada.

### <a name="restart"></a>**Reiniciar**
Faz com que o dispositivo seja reiniciado. O proprietário do dispositivo não é automaticamente notificado relativamente ao reinício, por isso, poderá perder trabalho.


## <a name="security-and-privacy-information-for-the-lost-mode-and-locate-device-actions"></a>Informações de segurança e de privacidade das ações localizar dispositivo e modo perdido
- Nenhuma informação de localização do dispositivo é enviada para o Intune até ativar esta ação.
- Quando utiliza a ação localizar dispositivo, as coordenadas de latitude e longitude do dispositivo são enviadas para o Intune e apresentadas no portal do Azure.
- Os dados são armazenados durante 24 horas e, em seguida, são removidos. Não pode remover manualmente os dados de localização.
- Os dados de localização são encriptados quando são armazenados e, igualmente, quando estão a ser transmitidos.
- Ao configurar o modo perdido, recomendamos que a mensagem que introduzir e que é apresentada no ecrã de bloqueio inclua informações que indiquem que a localização do dispositivo pode ser determinada.

