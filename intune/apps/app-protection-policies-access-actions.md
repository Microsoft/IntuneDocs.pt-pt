---
title: Apagar dados usando as ações de inicialização condicional da política de proteção de aplicativo
titleSuffix: Microsoft Intune
description: Saiba como apagar dados seletivamente usando ações de inicialização condicional da política de proteção de aplicativo no Microsoft Intune.
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
ms.openlocfilehash: a0440e2d6f5890b20ccf020c40bb1037bcfcae38
ms.sourcegitcommit: ebf72b038219904d6e7d20024b107f4aa68f57e6
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74564129"
---
# <a name="selectively-wipe-data-using-app-protection-policy-conditional-launch-actions-in-intune"></a>Apagar dados seletivamente usando as ações de inicialização condicional da política de proteção de aplicativo no Intune

Ao utilizar as políticas de proteção de aplicações do Intune, pode configurar definições para impedir que os utilizadores finais acedam a uma conta ou aplicação empresarial. Estas definições destinam-se aos requisitos de acesso e relocalização de dados definidos pela sua organização em casos de, por exemplo, dispositivos desbloqueados por jailbreak e versões de SO mínimas.
 
Com estas definições, pode eliminar dados da empresa explicitamente do dispositivo do utilizador final como uma ação a ser realizada em caso de não conformidade. Em algumas definições, será possível configurar múltiplas ações, como impedir o acesso e eliminar os dados com base em diferentes valores especificados.

## <a name="create-an-app-protection-policy-using-conditional-launch-actions"></a>Criar uma política de proteção de aplicativo usando ações de inicialização condicionais

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **aplicativos** > **políticas de proteção de aplicativo**.
3. Clique em **criar política** e selecione a plataforma do dispositivo para a política. 
4. Clique em **Configurar definições obrigatórias** para ver a lista de definições disponíveis a configurar para a política. 
5. Rolando para baixo no painel configurações, você verá uma seção intitulada **inicialização condicional** com uma tabela editável.

    ![Captura de ecrã a mostrar as ações de acesso de proteção de aplicações do Intune](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions01.png)

6. Selecione uma **Definição** e introduza o **Valor** que os utilizadores têm de cumprir para iniciar sessão na sua aplicação da empresa. 
7. Selecione a **Ação** a realizar se os utilizadores não cumprirem os seus requisitos. Em alguns casos, é possível configurar múltiplas ações para uma única definição. Para obter mais informações, veja [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md).

## <a name="policy-settings"></a>Definições de política 

A tabela das definições de políticas de proteção de aplicações apresenta colunas para a **Definição**, o **Valor** e a **Ação**.

### <a name="ios-policy-settings"></a>Definições de política para iOS
Para iOS, poderá configurar ações para as seguintes definições a partir da lista pendente **Definição**:
- Máximo de tentativas de PIN
- Período de tolerância offline
- Dispositivos com jailbreak/rooting
- Versão mínima do SO
- Versão mínima da aplicação
- Versão mínima do SDK
- Modelos de dispositivos
- Nível máximo de ameaça do dispositivo permitido

Para utilizar a definição **Modelos de dispositivos**, introduza uma lista de identificadores de modelos de iOS separados por ponto e vírgula. Estes valores não são sensíveis a maiúsculas e minúsculas. Além dos relatórios do Intune para a entrada de ' modelo (s) de dispositivo ', você pode encontrar um identificador de modelo do iOS na coluna tipo de dispositivo na [documentação de suporte do HockeyApp](https://support.hockeyapp.net/kb/client-integration-ios-mac-os-x-tvos/ios-device-types) ou no [repositório GitHub de terceiros](https://gist.github.com/adamawolf/3048717).<br>
Entrada de exemplo: *iPhone5,2;iPhone5,3*

Nos dispositivos dos utilizadores finais, o cliente do Intune toma medidas com base numa única correspondência de cadeias do modelo de dispositivo especificadas no Intune para as Políticas de Proteção de Aplicações. A correspondência depende inteiramente do que é comunicado pelo dispositivo. Recomendamos-lhe (ao administrador de TI) que se certifique de que o comportamento previsto está a ocorrer ao testar esta definição com base numa variedade de fabricantes e modelos de dispositivos e direcionado para um pequeno grupo de utilizadores. O valor predefinido é **Não configurado**.<br>
Defina uma das seguintes ações: 
- Permitir especificados (Bloquear não especificados)
- Permitir especificados (Apagar não especificados)

**O que acontece se o administrador de TI introduzir uma lista diferente de identificadores de modelos de iOS entre as políticas direcionadas às mesmas aplicações para o mesmo utilizador do Intune?**<br>
Quando existem conflitos entre duas políticas de proteção de aplicações em relação a valores configurados, o Intune normalmente opta pela abordagem mais restritiva. Por isso, a política resultante enviada para a aplicação-alvo a ser aberta pelo utilizador-alvo do Intune será uma intersecção dos identificadores de modelos de iOS listados na *Política A* e na *Política B* direcionados para a mesma combinação aplicação/utilizador. Por exemplo: se a *Política A* especificar "iPhone5,2;iPhone5,3" e a *Política B* especificar "iPhone5,3", a política resultante para o utilizador do Intune visado pela *Política A* e pela *Política B* será "iPhone5,3". 

### <a name="android-policy-settings"></a>Definições de políticas para Android

Para Android, poderá configurar ações para as seguintes definições a partir da lista pendente **Definição**:
- Máximo de tentativas de PIN
- Período de tolerância offline
- Dispositivos com jailbreak/rooting
- Versão mínima do SO
- Versão mínima da aplicação
- Versão mínima da correção
- Fabricantes de dispositivos
- Atestado de dispositivo SafetyNet
- Exigir verificação de ameaças em aplicativos
- Versão mínima do Portal da Empresa
- Nível máximo de ameaça do dispositivo permitido

Usando a **versão mín portal da empresa**, você pode especificar uma versão específica definida mínima do portal da empresa que é imposta em um dispositivo de usuário final. Essa configuração de inicialização condicional permite definir valores para **bloquear o acesso**, **apagar dados**e **avisar** como ações possíveis quando cada valor não é atendido. Os formatos possíveis para esse valor seguem o padrão *[Major]. [ Minor]* , *[principal]. [ Secundária]. [Build]* ou *[Major]. [ Secundária]. [Build]. [Revisão]* . Considerando que alguns usuários finais podem não preferir uma atualização forçada de aplicativos no local, a opção ' WARN ' pode ser ideal ao definir essa configuração. O Google Play Store faz um bom trabalho de enviar apenas os bytes Delta para atualizações do aplicativo, mas isso ainda pode ser uma grande quantidade de dados que o usuário talvez não queira utilizar se eles estiverem em dados no momento da atualização. Forçar uma atualização e, portanto, baixar um aplicativo atualizado pode resultar em encargos de dados inesperados no momento da atualização. A configuração de **versão mín portal da empresa** , se configurada, afetará qualquer usuário final que obtém a versão 5.0.4560.0 do portal da empresa e quaisquer versões futuras do portal da empresa. Essa configuração não terá nenhum efeito sobre os usuários que usam uma versão do Portal da Empresa mais antiga do que a versão com a qual esse recurso é lançado. Os usuários finais que usam as atualizações automáticas do aplicativo em seu dispositivo provavelmente não verão nenhuma caixa de diálogo desse recurso, Considerando que eles provavelmente estarão na versão mais recente do Portal da Empresa. Essa configuração é Android somente com proteção de aplicativo para dispositivos registrados e não registrados.

Para utilizar a definição **Fabricantes de dispositivos**, introduza uma lista de fabricantes de dispositivos Android separados por ponto e vírgula. Estes valores não são sensíveis a maiúsculas e minúsculas. Além dos relatórios do Intune, você pode encontrar o fabricante do Android de um dispositivo nas configurações do dispositivo. <br>
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

![Captura de tela de ações de acesso de proteção do aplicativo – versão mínima do so](./media/app-protection-policies-access-actions/apps-selective-wipe-access-actions05.png)

Depois de ter configurado totalmente uma definição, a linha será apresentada numa vista só de leitura e estará disponível para editar em qualquer altura. A linha também parecerá ter uma lista pendente disponível para seleção na coluna **Definição**. As definições que já tenham sido configuradas e que não permitam múltiplas ações não estarão disponíveis para seleção na lista pendente.

## <a name="next-steps"></a>Próximos passos

Para obter mais informações sobre as políticas de proteção de aplicações do Intune, veja:
- [Como criar e atribuir políticas de proteção de aplicações](app-protection-policies.md)
- [Definições de políticas de proteção de aplicações iOS](app-protection-policy-settings-ios.md)
- [Definições de políticas de proteção de aplicações Android no Microsoft Intune](app-protection-policy-settings-android.md) 
