---
title: Limpe os dados utilizando ações de lançamento condicional da política de proteção de aplicações
titleSuffix: Microsoft Intune
description: Aprenda a limpar seletivamente dados usando ações de lançamento condicional da política de proteção de aplicações no Microsoft Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 11/26/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: apps
ms.localizationpriority: high
ms.technology: ''
ms.assetid: f5ca557e-a8e1-4720-b06e-837c4f0bc3ca
ms.reviewer: aanavath
ms.suite: ems
search.appverid: MET150
ms.custom: seodec18
ms.collection: M365-identity-device-management
ms.openlocfilehash: 64faf797c69302e2a5cdbdde090330ab99fcc2e4
ms.sourcegitcommit: ecaff388038fb800f2e646f8efcf8f3b1e2fd1b1
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/18/2020
ms.locfileid: "77437890"
---
# <a name="selectively-wipe-data-using-app-protection-policy-conditional-launch-actions-in-intune"></a>Limpe seletivamente os dados utilizando ações de lançamento condicional da política de proteção de aplicações em Intune

Ao utilizar as políticas de proteção de aplicações do Intune, pode configurar definições para impedir que os utilizadores finais acedam a uma conta ou aplicação empresarial. Estas definições destinam-se aos requisitos de acesso e relocalização de dados definidos pela sua organização em casos de, por exemplo, dispositivos desbloqueados por jailbreak e versões de SO mínimas.
 
Com estas definições, pode eliminar dados da empresa explicitamente do dispositivo do utilizador final como uma ação a ser realizada em caso de não conformidade. Em algumas definições, será possível configurar múltiplas ações, como impedir o acesso e eliminar os dados com base em diferentes valores especificados.

## <a name="create-an-app-protection-policy-using-conditional-launch-actions"></a>Criar uma política de proteção de aplicações utilizando ações de lançamento condicional

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Apps** > Políticas de proteção de **aplicações**.
3. Clique na **política Criar** e selecione a plataforma do dispositivo para a sua apólice. 
4. Clique em **Configurar definições obrigatórias** para ver a lista de definições disponíveis a configurar para a política. 
5. Ao deslocar-se para baixo no painel Definições, verá uma secção intitulada **Lançamento Condicional** com uma tabela editável.

    ![Captura de ecrã a mostrar as ações de acesso de proteção de aplicações do Intune](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions01.png)

6. Selecione uma **Definição** e introduza o **Valor** que os utilizadores têm de cumprir para iniciar sessão na sua aplicação da empresa. 
7. Selecione a **Ação** a realizar se os utilizadores não cumprirem os seus requisitos. Em alguns casos, é possível configurar múltiplas ações para uma única definição. Para obter mais informações, veja [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md).

## <a name="policy-settings"></a>Definições de política 

A tabela das definições de políticas de proteção de aplicações apresenta colunas para a **Definição**, o **Valor** e a **Ação**.

### <a name="ios-policy-settings"></a>Definições de política para iOS
Para iOS/iPadOS, poderá configurar as ações para as seguintes definições utilizando a **definição** de dropdown:
- Máximo de tentativas de PIN
- Período de tolerância offline
- Dispositivos com jailbreak/rooting
- Versão mínima do SO
- Versão mínima da aplicação
- Versão mínima do SDK
- Modelos de dispositivos
- Max permitiu o nível de ameaça do dispositivo

Para utilizar a definição **do modelo do Dispositivo,** insera uma lista separada do modelo iOS/iPadOS. Estes valores não são sensíveis aos casos. Além de intune Reporting para a entrada 'Dispositivo modelo(s)', pode encontrar um identificador de modelo iOS/iPadOS sob a coluna Tipo dispositivo na [documentação de suporte do HockeyApp](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types) ou neste [repositório GitHub de 3ª parte.](https://gist.github.com/adamawolf/3048717)<br>
Entrada de exemplo: *iPhone5,2;iPhone5,3*

Nos dispositivos dos utilizadores finais, o cliente do Intune toma medidas com base numa única correspondência de cadeias do modelo de dispositivo especificadas no Intune para as Políticas de Proteção de Aplicações. A correspondência depende inteiramente do que é comunicado pelo dispositivo. Recomendamos-lhe (ao administrador de TI) que se certifique de que o comportamento previsto está a ocorrer ao testar esta definição com base numa variedade de fabricantes e modelos de dispositivos e direcionado para um pequeno grupo de utilizadores. O valor predefinido é **Não configurado**.<br>
Defina uma das seguintes ações: 
- Permitir especificados (Bloquear não especificados)
- Permitir especificados (Apagar não especificados)

**O que acontece se o administrador de TI inserir uma lista diferente de identificadores de modelos iOS/iPadOS entre políticas direcionadas para as mesmas apps para o mesmo utilizador Intune?**<br>
Quando existem conflitos entre duas políticas de proteção de aplicações em relação a valores configurados, o Intune normalmente opta pela abordagem mais restritiva. Assim, a política resultante enviada para a aplicação visada que está a ser aberta pelo utilizador intune visado seria uma intersecção do(s) identificador(s) do modelo iOS/iPadOS listado na *Política A* e *Política B* direcionado para a mesma combinação app/utilizador. Por exemplo: se a *Política A* especificar "iPhone5,2;iPhone5,3" e a *Política B* especificar "iPhone5,3", a política resultante para o utilizador do Intune visado pela *Política A* e pela *Política B* será "iPhone5,3". 

### <a name="android-policy-settings"></a>Definições de políticas para Android

Para Android, poderá configurar ações para as seguintes definições a partir da lista pendente **Definição**:
- Máximo de tentativas de PIN
- Período de tolerância offline
- Dispositivos com jailbreak/rooting
- Versão mínima do SO
- Versão mínima da aplicação
- Versão mínima da correção
- Fabricantes de dispositivos
- Atestação do dispositivo SafetyNet
- Exigir uma varredura de ameaças em apps
- Versão Min Company Portal
- Max permitiu o nível de ameaça do dispositivo

Utilizando a **versão Min Company Portal,** pode especificar uma versão definida específica do Portal da Empresa que é aplicada num dispositivo de utilizador final. Esta definição de lançamento condicional permite-lhe definir valores para **bloquear o acesso,** **eliminar dados**e **alertar** como possíveis ações quando cada valor não for atingido. Os possíveis formatos para este valor seguem o padrão *[Major]. Menor,* *[Major].[ Menor]. [Construir]* ou *[Major].[ Menor]. [Construir]. [Revisão]* . Dado que alguns utilizadores finais podem não preferir uma atualização forçada de aplicações no local, a opção 'warn' pode ser a ideal para configurar esta definição. A Google Play Store faz um bom trabalho ao enviar apenas os bytes delta para atualizações de aplicações, mas esta ainda pode ser uma grande quantidade de dados que o utilizador pode não querer utilizar se estiverem em dados no momento da atualização. Forçar uma atualização e, assim, descarregar uma aplicação atualizada pode resultar em cargas de dados inesperadas no momento da atualização. A definição da **versão Min Company Portal,** se configurada, afetará qualquer utilizador final que obtenha a versão 5.0.4560.0 do Portal da Empresa e quaisquer futuras versões do Portal da Empresa. Esta definição não terá qualquer efeito sobre os utilizadores utilizando uma versão do Portal da Empresa que seja mais antiga do que a versão com a que esta funcionalidade é lançada. Os utilizadores finais que utilizam as atualizações automáticas da aplicação no seu dispositivo provavelmente não verão quaisquer diálogos desta funcionalidade, dado que provavelmente estarão na versão mais recente do Portal da Empresa. Esta definição é Android apenas com proteção de aplicativos para dispositivos matriculados e não matriculados.

Para utilizar a definição **Fabricantes de dispositivos**, introduza uma lista de fabricantes de dispositivos Android separados por ponto e vírgula. Estes valores não são sensíveis aos casos. Além do Intune Reporting, pode encontrar o fabricante Android de um dispositivo sob as definições do dispositivo. <br>
Entrada de exemplo: *Fabricante A;Fabricante B* 

>[!NOTE]
> Estes são alguns fabricantes comuns, comunicados por dispositivos que utilizam o Intune, que podem ser utilizados como entrada: Asus;Blackberry;Bq;Gionee;Google;Hmd global;Htc;Huawei;Infinix;Kyocera;Lemobile;Lenovo;Lge;Motorola;Oneplus;Oppo;Samsung;Sharp;Sony;Tecno;Vivo;Vodafone;Xiaomi;Zte;Zuk

Nos dispositivos dos utilizadores finais, o cliente do Intune toma medidas com base numa única correspondência de cadeias do modelo de dispositivo especificadas no Intune para as Políticas de Proteção de Aplicações. A correspondência depende inteiramente do que é comunicado pelo dispositivo. Recomendamos-lhe (ao administrador de TI) que se certifique de que o comportamento previsto está a ocorrer ao testar esta definição com base numa variedade de fabricantes e modelos de dispositivos e direcionado para um pequeno grupo de utilizadores. O valor predefinido é **Não configurado**.<br>
Defina uma das seguintes ações: 
- Permitir especificados (Bloquear não especificados)
- Permitir especificados (Apagar não especificados)

**O que acontece se o administrador de TI introduzir uma lista diferente de fabricantes de dispositivos Android entre as políticas direcionadas às mesmas aplicações para o mesmo utilizador do Intune?**<br>
Quando existem conflitos entre duas políticas de proteção de aplicações em relação a valores configurados, o Intune normalmente opta pela abordagem mais restritiva. Por isso, a política resultante enviada para a aplicação-alvo a ser aberta pelo utilizador-alvo do Intune será uma intersecção dos fabricantes de dispositivos Android listados na *Política A* e na *Política B* direcionados para a mesma combinação aplicação/utilizador. Por exemplo: se a *Política A* especificar "Google;Samsung" e a *Política B* especificar "Google", a política resultante para o utilizador do Intune visado pela *Política A* e pela *Política B* será "Google". 

### <a name="additional-settings-and-actions"></a>Definições e ações adicionais 

Por predefinição, a tabela terá linhas povoadas como definições configuradas para **Período de tolerância offline** e **Máximo de tentativas de PIN**, se a definição **Requerer PIN para acesso** estiver definida como **Sim**.
 
Para configurar uma definição, selecione uma definição na lista pendente da coluna **Definição**. Depois de selecionar uma definição, a caixa de texto editável ficará ativa na coluna **Valor** da mesma linha, se for necessário definir um valor. Além disso, a lista pendente ficará ativa na coluna **Ação** com o conjunto de ações de iniciação condicional aplicáveis à definição. 

A seguinte lista apresenta as ações comuns:
- **Bloquear acesso** – impedir o utilizador final de aceder à aplicação da empresa.
- **Apagar dados** – apagar os dados da empresa do dispositivo do utilizador final.
- **Avisar** – apresentar uma caixa de diálogo com uma mensagem de aviso para o utilizador final.

Em alguns casos, como a definição **Versão mínima do SO**, pode configurar a definição para realizar todas as ações aplicáveis com base em números de versão diferentes. 

![Screenshot das ações de acesso à proteção de aplicativos - versão Min OS](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions05.png)

Depois de ter configurado totalmente uma definição, a linha será apresentada numa vista só de leitura e estará disponível para editar em qualquer altura. A linha também parecerá ter uma lista pendente disponível para seleção na coluna **Definição**. As definições que já tenham sido configuradas e que não permitam múltiplas ações não estarão disponíveis para seleção na lista pendente.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre as políticas de proteção de aplicações do Intune, veja:
- [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md)
- [Definições de políticas de proteção de aplicações iOS](app-protection-policy-settings-ios.md)
- [Definições de políticas de proteção de aplicações Android no Microsoft Intune](app-protection-policy-settings-android.md) 
