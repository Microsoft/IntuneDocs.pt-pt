---
title: "Controlo de acesso baseado em funções (RBAC) para o Microsoft Intune | Pré-visualização do Azure no Intune | Documentos da Microsoft"
description: "Pré-visualização do Azure no Intune: saiba como o RBAC lhe permite controlar quem pode realizar ações e fazer alterações."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 12/18/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ca3de752-3caa-46a4-b4ed-ee9012ccae8e
ms.reviewer: 
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1024d2a33d843c628ffbb68f7b01a5d511191e7e
ms.openlocfilehash: db0f88db8eee33781ccf3ef54e34089a25118726


---

# <a name="role-based-access-control-rbac-for-microsoft-intune"></a>Controlo de acesso baseado em funções (RBAC) para o Microsoft Intune

[!INCLUDE[azure_preview](../includes/azure_preview.md)]

Em palavras simples, as **funções** (ou RBAC) do Intune ajudam a controlar quem pode realizar várias ações do Intune e a quem se aplicam essas ações. Pode utilizar as funções incorporadas que abrangem alguns cenários comuns do Intune ou pode criar as suas próprias funções.

Uma função é definida por:

- **Definição** – O nome de uma função e as permissões que configura.
- **Membros** – O utilizador ou grupo de utilizadores a quem estas permissões são concedidas.
- **Âmbito** – Os utilizadores ou dispositivos que uma pessoa específica (o membro) pode gerir.
- **Atribuição** – Quando a definição, os membros e o âmbito tenham sido configurados, a função é atribuída.

## <a name="built-in-roles"></a>Funções incorporadas

As seguintes funções estão incorporadas no Intune e pode personalizar estas funções ou atribuí-las a grupos sem qualquer configuração adicional.

- **Administrador do Intune** – Tem todas as permissões para todas as operações do Intune.
- **Gestor da Aplicação** – Gere e implementa aplicações e perfis.
- **Gestor de Políticas de Configuração** – Gere e implementa definições e perfis de configuração.
- **Operador de Assistência Técnica** – Realiza tarefas remotas e vê informações sobre o utilizador e o dispositivo.
- **Operador Só de Leitura** – Vê informações no portal do Intune sem a capacidade de realizar alterações.


## <a name="custom-roles"></a>Funções personalizadas

Se nenhuma das funções incorporadas der resposta às suas necessidades, pode criar a sua própria função ao selecionar as definições que abrangem muitas das funcionalidades do Intune. Pode ver uma lista das definições disponíveis mais adiante neste tópico.

### <a name="example"></a>Exemplo

Contrata um administrador de TI novo que vai ser responsável pela implementação e gestão de aplicações dos utilizadores no seu escritório em Londres. Os utilizadores estão num grupo do Azure AD com o nome **Londres**. Quer garantir que o administrador de TI não consegue implementar aplicações aos utilizadores de mais nenhum escritório. Deve tomar uma das seguintes medidas:

- Atribuir a função **Gestor de Aplicação** incorporada com as seguintes propriedades:
    - **Membros** – Selecione um grupo que inclua o administrador de TI que vai implementar as aplicações
    - **Âmbito** – Selecione o grupo do Azure AD **Londres**.

    >[!IMPORTANT]
    >Para criar, editar ou atribuir funções, a sua conta tem de ter uma das seguintes permissões no Azure AD:
    >- **Administrador Global do AAD**
    >- **Administrador do Serviço do Intune**

### <a name="how-to-create-a-custom-role"></a>Como criar uma função personalizada

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Controlo de acesso**.
![Carga de trabalho Controlo de acesso](./media/axxess-control.png)
1. No painel **Funções** da carga de trabalho **Controlo de acesso**, escolha **Adicionar personalizado**.
2. No painel **Adicionar Função Personalizada**, introduza um nome e uma descrição para a nova função e, em seguida, clique em **Permissões**.
3. No painel **Permissões**, escolha as permissões que quer utilizar com esta função. Utilize a lista de referência de definições de funções personalizadas que está mais adiante neste tópico para ajudá-lo.
4. Quando tiver terminado, clique em **OK**.
5. No painel **Adicionar Função Personalizada**, clique em **Criar**.

A nova função é apresentada na lista no painel **Funções**.

## <a name="how-to-assign-a-role"></a>Como atribuir uma função

1. No painel **Funções** da carga de trabalho **Controlo de acesso**, escolha a função incorporada ou personalizada que pretende atribuir.
2. No painel <*nome da função*> – **Propriedades**, escolha **Gerir** > **Atribuições**.
    >[!TIP]
    >Neste painel, também pode editar ou eliminar funções existentes.
3. No painel seguinte, escolha **Atribuir**.
4. No painel **Atribuições de Função**, introduza um **Nome** e uma **Descrição** opcional para a atribuição e, em seguida, escolha o seguinte:
    - **Membros** – Selecione um grupo que inclua o utilizador ao qual pretende conceder as permissões.
    - **Âmbito** – Selecione um grupo que inclua os utilizadores que o membro acima terá permissão para gerir.
5. Quando tiver terminado, clique em **OK**.

A nova atribuição é apresentada na lista de atribuições.

## <a name="custom-role-settings-reference"></a>Referência para definições de função personalizada

Quando cria uma função personalizada, pode configurar uma ou mais das seguintes definições:

### <a name="device-configurations"></a>Configurações de dispositivo

|||
|-|-|
|**Atribuir**|Atribua perfis de dispositivo a grupos.|
|**Criar**|Crie perfis de dispositivo.|
|**Eliminar**|Elimine perfis de dispositivo.|
|**Ler**|Leia perfis de dispositivo e as respetivas propriedades.|
|**Atualizar**|Atualize os perfis de dispositivo existentes.|

### <a name="managed-apps"></a>Aplicações geridas

|||
|-|-|
|**Atribuir**|Atribua aplicações geridas a grupos.|
|**Criar**|Adicione novas aplicações geridas ao Intune.|
|**Eliminar**|Elimine aplicações geridas.|
|**Ler**|Leia aplicações geridas e as respetivas propriedades.|
|**Atualizar**|Atualize as aplicações geridas existentes.|
|**Eliminação**|Elimine aplicações geridas dos dispositivos.|

### <a name="managed-devices"></a>Dispositivos geridos

|||
|-|-|
|**Eliminar**|Elimine dispositivos geridos do Intune.|
|**Ler**|Veja informações sobre dispositivos geridos no portal do Intune.|
|**Atualizar**|Atualize informações sobre dispositivos geridos.|

### <a name="mobile-apps"></a>Aplicações móveis

|||
|-|-|
|**Atribuir**|Atribua aplicações móveis a grupos.|
|**Criar**|Adicione novas aplicações móveis ao Intune.|
|**Eliminar**|Elimine aplicações móveis.|
|**Ler**|Leia aplicações móveis e as respetivas propriedades.|
|**Atualizar**|Atualize aplicações móveis existentes.|

### <a name="organization"></a>Organização

|||
|-|-|
|**Ler**|Leia definições de inquilinos.|
|**Atualizar**|Atualize definições de inquilinos.|

### <a name="remote-tasks"></a>Tarefas remotas

|||
|-|-|
|**Ignorar Bloqueio de Ativação**|Remova o bloqueio de ativação de um dispositivo iOS sem o Apple ID e a palavra-passe do utilizador. |
|**Desativar o Modo Perdido**|Desative o Modo Perdido. O modo perdido permite-lhe especificar uma mensagem e um número de telefone que serão apresentados no ecrã de bloqueio do dispositivo.|
|**Ativar o Modo Perdido**|Ative o Modo Perdido. O modo perdido permite-lhe especificar uma mensagem e um número de telefone que serão apresentados no ecrã de bloqueio do dispositivo.|
|**Localizar Dispositivo**|-|
|**Reiniciar Agora**|Faz com que o dispositivo seja reiniciado.|
|**Bloqueio Remoto**|Bloqueia um dispositivo. O proprietário do dispositivo tem de utilizar o código de acesso para desbloqueá-lo.|
|**Repor Código de acesso**|Gera um novo código de acesso para o dispositivo, que será apresentado no painel <device name> Descrição Geral.|
|**Extinguir**|Remove apenas os dados da empresa geridos pelo Intune. Não remove os dados pessoais do dispositivo.|
|**Eliminação**|Repõe as predefinições do dispositivo.|



### <a name="telecom-expenses"></a>Despesas de telecomunicações

|||
|-|-|
|**Ler**|Leia as definições da Gestão de Despesas de Telecomunicações (TEM).|
|**Atualizar**|Atualize as definições da Gestão de Despesas de Telecomunicações (TEM).|

### <a name="terms-and-conditions"></a>Termos e condições

|||
|-|-|
|**Atribuir**|Atribua termos e condições a grupos.|
|**Criar**|Crie definições dos termos e condições.|
|**Eliminar**|Elimine definições dos termos e condições.|
|**Ler**|Leia definições dos termos e condições no portal do Intune.|
|**Atualizar**|Atualize as definições dos termos e condições existentes.|


<!--HONumber=Feb17_HO1-->


