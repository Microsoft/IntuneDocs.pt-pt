---
title: "Como criar uma política de conformidade para macOS"
titleSuffix: Azure portal
description: "Saiba como criar uma política de conformidade para dispositivos macOS."
keywords: 
author: andredm7
ms.author: andredm
manager: dougeby
ms.date: 2/13/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.reviewer: muhosabe
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a5f1caeddbd3d171092ef59cfb092404b31154f2
ms.sourcegitcommit: 754fcc31155b28d6910bba45419c6be745f8793e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/14/2018
---
# <a name="create-a-device-compliance-policy-for-macos-devices-with-intune"></a>Criar uma política de conformidade para dispositivos macOS com o Intune


[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="before-you-begin"></a>Antes de começar

Antes de criar e atribuir uma política de conformidade de dispositivos, reveja os conceitos relativos às políticas de conformidade de dispositivos do Intune.

- Para saber mais sobre as políticas de conformidade de dispositivos, veja [Introdução às políticas de conformidade de dispositivos](device-compliance.md).

> [!IMPORTANT]
> Tem de criar políticas de conformidade de dispositivos para cada plataforma. As definições das políticas de conformidade de dispositivos do Intune dependem de funcionalidades da plataforma que são definições acessíveis através do protocolo MDM.

A tabela seguinte descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional:


| Definição de política | macOS 10.11 e posterior |
| --- | --- |
| **Configuração do PIN ou da palavra-passe** | Corrigido |   
| **Encriptação do dispositivo** | Corrigido (ao definir um PIN) |
| **Perfil de e-mail** | Em quarentena |
|**Versão mínima do SO** | Em quarentena |
| **Versão máxima do SO** | Em quarentena |  


**Remediado** = O sistema operativo do dispositivo impõe a conformidade. (Por exemplo, forçar o utilizador a definir um PIN.)

**Em Quarentena** = O sistema operativo do dispositivo não impõe a conformidade. (Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo.) Quando o dispositivo não é conforme, são efetuadas as seguintes ações:

- O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
- O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="macos-compliance-policy-settings"></a>Definições de políticas de conformidade para MacOS

Ao criar uma nova conformidade do dispositivo com o Intune, terá várias categorias com definições diferentes à escolha:

- Estado de Funcionamento do Dispositivo

- Propriedades do Dispositivo

- Segurança do sistema

### <a name="device-health"></a>Estado de Funcionamento do Dispositivo

- **Exigir uma proteção da integridade do sistema** – defina como **Exigir** para que seja verificado se os seus dispositivos macOS têm a proteção da integridade do sistema ativada.

### <a name="device-properties"></a>Propriedades do dispositivo

- **Versão do SO mínima** – quando um dispositivo não cumprir o requisito de versão mínima do SO, será comunicado como não estando em conformidade. É apresentada uma hiperligação com informações sobre como atualizar. O utilizador pode optar por atualizar o dispositivo. Depois, pode aceder aos recursos da empresa.

- **Versão do SO máxima** – quando um dispositivo utiliza uma versão do SO superior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

### <a name="system-security-settings"></a>Definições de segurança do sistema

#### <a name="password"></a>Palavra-passe

- **Palavra-passe obrigatória para desbloquear dispositivos móveis** – defina como **Exigir** para que os utilizadores tenham de introduzir uma palavra-passe para poderem aceder aos dispositivos.

- **Palavras-passe simples** – defina como **Bloquear** para que o utilizador não possa criar uma palavra-passe simples, como **1234** ou **1111**.

- **Comprimento mínimo da palavra-passe** – especifique o número mínimo de dígitos ou carateres que a palavra-passe tem de ter.

- **Tipo de palavra-passe** – especifique se o utilizador tem de criar uma palavra-passe **Alfanumérica** ou **Numérica**.

- **Número de carateres não alfanuméricos na palavra-passe** – se definir o **Tipo obrigatório de palavra-passe** como **Alfanumérico**, utilize esta definição para especificar o número mínimo de conjuntos de carateres que a palavra-passe tem de ter. 

    > [!NOTE]
    > Definir um número mais relevado exige que o utilizador crie uma palavra-passe mais complexa.

    > [!IMPORTANT]
    > Para dispositivos macOS, esta definição refere-se ao número de carateres especiais (por exemplo, **!** , **#**, **&amp;**) que têm de ser incluídos na palavra-passe.

- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe** – especifique o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da palavra-passe (dias)** – selecione o número de dias (entre 1 e 250) antes de a palavra-passe expirar e ser necessário criar uma nova.

- **Número de palavras-passe anteriores cuja reutilização está bloqueada** –especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.

    > [!IMPORTANT]
    > As alterações ao requisito de palavra-passe num dispositivo macOS só têm efeito na próxima alteração de palavra-passe do utilizador. Por exemplo, se definir uma restrição de comprimento da palavra-passe para oito dígitos e o dispositivo macOS tiver atualmente uma palavra-passe de seis dígitos, o mesmo permanecerá em conformidade até à próxima vez que o utilizador atualizar a palavra-passe no dispositivo.

## <a name="to-create-a-device-compliance-policy"></a>Para criar uma política de conformidade do dispositivo

1. Aceda ao [portal do Azure](https://portal.azure.com) e inicie sessão com as credenciais do Intune.

2. Depois de iniciar sessão com êxito, poderá ver o **Dashboard do Azure**.

3. Selecione **Mais serviços** no menu à esquerda e, em seguida, escreva **Intune** no filtro da caixa de texto.

4. Selecione **Intune** e o **Dashboard do Intune** será apresentado.

5. Selecione **Conformidade do dispositivo** e, em seguida, selecione **Políticas** em **Gerir**.

6. Selecione **Criar Política**.

7. Escreva um nome, uma descrição e escolha a plataforma à qual pretende que esta política se aplique.

8. O painel **Política de conformidade de macOS** é aberto. Selecione as categorias de conformidade do dispositivo **Segurança**, **Estado de funcionamento do dispositivo** e **Propriedade do dispositivo** para especificar as suas definições.

10. Assim que terminar de escolher as suas definições, selecione **OK** em cada categoria de definições de conformidade do dispositivo.

11. Selecione **OK** e, em seguida, selecione **Criar**.

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

Para atribuir uma política de conformidade a utilizadores, escolha uma política que tenha configurado. As políticas existentes encontram-se no painel **Políticas de conformidade**.

1. Selecione a política de conformidade de dispositivos que pretende atribuir aos utilizadores e, em seguida, selecione **Tarefas**. Esta ação abre o painel onde pode selecionar **Grupos de segurança do Azure Active Directory** e atribuí-los à política.

2. Escolha **Selecionar grupos** para abrir o painel que apresenta os grupos de segurança do Azure AD.

3. Selecione **Selecionar** e, em seguida, **Guardar** para atribuir a política de conformidade de dispositivos a grupos de segurança do Azure AD.

4. Quando terminar de atribuir a política de conformidade de dispositivos aos seus grupos, pode fechar o painel **Tarefas**.

    > [!TIP]
    > Por predefinição, os dispositivos efetuam uma verificação de conformidade a cada oito horas. No entanto, os utilizadores podem impor este processo através da aplicação Portal da Empresa do Intune.

## <a name="next-steps"></a>Próximos passos

[Como monitorizar as políticas de conformidade de dispositivos](compliance-policy-monitor.md)
