---
title: Utilizar linhas de base de segurança no Microsoft Intune – Azure | Documentos da Microsoft
description: Adicione ou configure as definições de segurança do windows recomendadas para proteger dados em dispositivos com o Microsoft Intune para gestão de dispositivos móveis e de utilizador. Ativar o BitLocker, configurar a proteção de ameaças avançada do Microsoft Defender, controlam o Internet Explorer, utilizar Smart Screen, definir políticas de segurança local, exigir uma palavra-passe, bloquear transferências de internet e muito mais.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 06/20/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: ''
ms.reviewer: joglocke
ms.suite: ems
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9a1a48f132d199ad7b1b3e112915acd8f073cf21
ms.sourcegitcommit: 256952cac44bc6289156489b6622fdc1a3c9c889
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/26/2019
ms.locfileid: "67403592"
---
# <a name="use-security-baselines-to-configure-windows-10-devices-in-intune"></a>Utilizar linhas de base de segurança para configurar dispositivos Windows 10 no Intune

Utilize linhas de base do Intune para ajudar a proteger e proteger os seus utilizadores e dispositivos. Linhas de base de segurança são previamente configurados grupos de definições que o ajudam a aplicam-se um grupo conhecido de definições e valores predefinidos que são recomendados pelas equipes de segurança relevantes do Windows. Ao criar um perfil de linha de base de segurança no Intune, está criando um *configuração do dispositivo* perfil.

Esta funcionalidade aplica-se a:

- Windows 10 versão 1809 e posterior

Implementar linhas de base de segurança para grupos de utilizadores ou dispositivos no Intune e as definições são aplicadas aos dispositivos que executam o Windows 10 ou posterior. Por exemplo, o *linha de base de segurança de MDM* automaticamente ativa o BitLocker para unidades amovíveis, automaticamente requer uma palavra-passe para desbloquear um dispositivo, Desabilita automaticamente a autenticação básica e muito mais. Quando um valor predefinido não funciona para o seu ambiente, personalize a linha de base para aplicar as definições que precisa.  

Tipos de linha de base separado podem incluir as mesmas definições, mas usar valores padrão diferente para essas definições. É importante para compreender os padrões nas linhas de base optar por utilizar, e, em seguida, modificar cada linha de base de acordo com sua organização precisa.  

> [!NOTE]
> A Microsoft não recomenda utilizar versões de pré-visualização das linhas de base de segurança num ambiente de produção. As definições numa linha de base de pré-visualização podem ser alteradas no decorrer da pré-visualização. 

O objetivo de utilizar linhas de base de segurança é ter um fluxo de trabalho seguro do ponto-a-ponto, ao trabalhar com o Microsoft 365. Alguns dos benefícios incluem:

- Uma linha de base de segurança inclui as melhores práticas e recomendações sobre as definições que afetam a segurança. Parceiros do Intune com a equipe de segurança mesmo do Windows que cria as linhas de base de segurança de política de grupo. Estas recomendações baseiam-se nas orientações e ampla experiência.
- Se estiver familiarizado com o Intune e não tem a certeza onde começar, em seguida, linhas de base de segurança dá-lhe uma vantagem. Pode, rapidamente, criar e implementar um perfil de seguro, sabendo que está ajudando a proteger os dados e recursos da sua organização.
- Se utilizar atualmente a política de grupo, a migração para o Intune para gestão é muito mais fácil com essas linhas de base. Essas linhas de base estão nativamente incorporadas Intune e incluem uma experiência de gestão moderna.



[Linhas de base de segurança de Windows](https://docs.microsoft.com/windows/security/threat-protection/windows-security-baselines) é um ótimo recurso para obter mais informações sobre esta funcionalidade. [Gestão de dispositivos móveis](https://docs.microsoft.com/windows/client-management/mdm/) (MDM) é um ótimo recurso sobre MDM e o que pode fazer em dispositivos Windows.

## <a name="security-baseline-versions-and-instances"></a>Versões de linha de base de segurança e instâncias
Periodicamente, novas atualizações para uma linha de base fiquem disponíveis. Cada nova instância de versão de uma linha de base pode adicionar ou remover definições ou introduzir outras alterações. Por exemplo, como as novas definições do Windows 10 são disponibilizadas com novas versões do Windows 10, a linha de base de segurança de MDM pode receber uma nova instância de versão, que inclui as definições mais recentes.  

Na consola do Intune, pode ver quais linhas de base de segurança estão disponíveis e informações sobre eles. Informações disponíveis incluem escreva Quantos perfis tiver que usar essa linha de base, quantas instâncias separadas do tipo de linha de base estão disponíveis e, quando a última instância mais recente foi feita disponíveis ou publicado.  O exemplo seguinte mostra o mosaico para uma linha de base de segurança bem utilizados do MDM:  

![Mosaico de linha de base](./media/security-baselines/baseline-tile.png)

Para ver informações sobre as versões de linha de base que utiliza, selecione uma linha de base e, em seguida, selecione **versões**. Intune apresenta detalhes sobre as versões em utilização por seus perfis. No painel de versões, pode selecionar uma única versão para ver mais detalhes sobre os perfis que utilizam essa versão. Pode também selecionar duas versões diferentes e, em seguida, escolha **comparar as linhas de base** para transferir um ficheiro CSV que detalha essas diferenças.  

![Comparar as linhas de base](./media/security-baselines/compare-baselines.png)

Quando cria uma linha de base de segurança *perfil*, o perfil utiliza automaticamente a instância de linha de base de segurança lançada recentemente.  Pode continuar a utilizar e editar perfis que criou anteriormente e utilizam uma instância de versão de linha de base anterior, incluindo linhas de base criadas com uma versão de pré-visualização. 

Suporte de perfis de linha de base de segurança uma [mudar da versão](#change-the-baseline-instance-for-a-profile) da linha de base que está a ser utilizado. Isso significa que quando sai de uma nova versão, não precisa de criar um novo perfil de linha de base para aproveitá-la. Em vez disso, quando estiver pronto, pode selecionar um perfil de linha de base e, em seguida, utilize a opção incorporada para alterar a versão de instância para o perfil.  

## <a name="available-security-baselines"></a>Linhas de base de segurança disponíveis 

As instâncias de linha de base de segurança seguintes estão disponíveis para utilização com o Intune. Utilize as ligações para ver as definições para a instância mais recente de cada linha de base. 

- **Linha de base de segurança MDM**
  - [Linha de base de segurança MDM para o Spring 2019 (1 de 19 horas)](security-baseline-settings-windows.md)
  - Pré-visualização: Linha de base de segurança MDM de Outubro de 2018

- **Linha de base do Windows Defender ATP**  
  *(Para usar esta linha de base seu ambiente tem de cumprir os pré-requisitos de utilização [a proteção de ameaças avançada do Microsoft Defender](advanced-threat-protection.md#prerequisites))* .
  - [Pré-visualização: Linha de base do Windows Defender ATP](security-baseline-settings-defender-atp.md)  

Pode continuar a utilizar e editar perfis que criou anteriormente com base num modelo de pré-visualização, mesmo quando esse modelo de pré-visualização já não está disponível para a criação de novos perfis. 

## <a name="prerequisites"></a>Pré-requisitos
- Para gerir linhas de base no Intune, sua conta tem de ter o [Gerenciador de perfis de política e](role-based-access-control.md#built-in-roles) função incorporada.

- Utilização de algumas linhas de base pode exigir que tenha uma subscrição ativa para serviços adicionais, como Microsoft Defender ATP.  

## <a name="co-managed-devices"></a>Dispositivos cogeridos

Linhas de base de segurança nos dispositivos geridos pelo Intune são semelhantes aos dispositivos cogeridos com o Configuration Manager. Dispositivos cogeridos utilizam o System Center Configuration Manager e o Microsoft Intune para gerir os dispositivos Windows 10 em simultâneo. Permite-lhe na cloud-anexar o investimento existente do Configuration Manager para os benefícios do Intune. [Descrição geral de cogestão](https://docs.microsoft.com/sccm/comanage/overview) é um ótimo recurso, se utilizar o Configuration Manager e também desejam obter os benefícios da cloud.

Ao utilizar dispositivos cogeridos, tem de mudar a **configuração do dispositivo** carga de trabalho (suas configurações) para o Intune. [Cargas de trabalho de configuração de dispositivo](https://docs.microsoft.com/sccm/comanage/workloads#device-configuration) fornece mais informações.

## <a name="create-the-profile"></a>Criar o perfil

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e, em seguida, selecione **segurança do dispositivo** > **linhas de base de segurança** para ver a lista de linhas de base disponíveis.


    ![Selecione uma linha de base de segurança para configurar](./media/security-baselines/available-baselines.png)

2. Selecione a linha de base que pretende utilizar e, em seguida, selecione **criar perfil**.  

3. Sobre o **Noções básicas** separador, especifique as seguintes propriedades:

    - **Nome**: Introduza um nome para o seu perfil de linhas de base de segurança. Por exemplo, introduza *perfil padrão para Defender ATP*.

    - **Descrição**: Introduza algum texto que descreve o que faz esta linha de base. A descrição é que digitar qualquer texto que pretende. É opcional mas recomendado.  

   Selecione **seguinte** para ir para o separador seguinte. Após avançada para um novo separador, pode selecionar o nome do separador para retornar a uma guia visualizada anteriormente.  

4. No separador de definições de configuração, ver os grupos dos **definições** que estão disponíveis na linha de base que selecionou. Pode expandir um grupo para ver as definições desse grupo e os valores predefinidos para essas definições na linha de base. Para localizar as definições específicas:
   - Selecione um grupo para expandir e reveja as definições disponíveis.  
   - Utilize o *pesquisa* barra e especifique palavras-chave que filtrar a vista para apresentar apenas aos grupos que contêm os critérios de procura.  
 
   Cada configuração numa linha de base tem uma configuração predefinida para essa versão de linha de base. Reconfigure as predefinições para atender às necessidades da sua empresa. Linhas de base diferentes podem conter a mesma definição e usar valores padrão diferente para a definição, dependendo da intenção da linha de base. 

    ![Expandir um grupo para ver as definições para esse grupo](./media/security-baselines/sample-list-of-settings.png)

5. Sobre o **etiquetas de âmbito** separador, selecione **selecionar etiquetas de âmbito** para abrir o *selecionar etiquetas* painel para atribuir etiquetas de âmbito para o perfil. 

6. Sobre o **atribuições** separador, selecione **selecionar grupos para incluir** e, em seguida, atribua a linha de base para um ou mais grupos. Uso **selecionar grupos para excluir** para ajustar a atribuição.  

   ![Atribuir um perfil](./media/security-baselines/assignments.png)
  
7. Quando estiver pronto para implementar a linha de base, avance para o **rever + criar** separador e reveja os detalhes da linha de base. Selecione **criar** para guardar e implementar o perfil.  

   Assim que criar o perfil, são emitidos via push para o grupo atribuído e podem ser aplicadas imediatamente.

   > [!TIP]  
   > Se salvar um perfil sem primeiro atribui-la a grupos, pode editar o perfil para fazê-lo mais tarde.  

   ![Reveja a linha de base](./media/security-baselines/review.png) 

  
8. Depois de criar um perfil, editá-lo acedendo a **segurança de dispositivos** > **linhas de base de segurança**, selecione o tipo de linha de base que configurou e, em seguida, selecione **perfis**.  Selecione o perfil na lista de perfis disponíveis e, em seguida, selecione **propriedades**. Pode editar as definições de todos os guias de configuração disponíveis e selecionar **revisão + guardar** para consolidar as alterações.  

## <a name="change-the-baseline-instance-for-a-profile"></a>Alterar a instância de linha de base para um perfil
Perfis de linha de base suportam uma alteração da instância de linha de base que utiliza o perfil. Pode selecionar uma instância mais antiga ou, mais geralmente, uma instância mais recente da mesma linha de base.  Não é possível alterar entre duas diferentes linhas de base, tal como alterar um perfil de utilizar uma linha de base para Defender ATP para utilizar a linha de base de segurança MDM. 

Ao configurar uma alteração da versão de linha de base, terá a opção para transferir um ficheiro CSV que indica as alterações entre as versões de linha de duas base envolvidas. Também está dada a opção manter todas as suas personalizações na versão de linha de base original e aplicá-las para a nova versão ou implementar todos os padrões encontrados na nova versão de linha de base que selecionou. 

Depois de guardar, após a conversão for concluída, a linha de base é imediatamente reimplementada grupos atribuídos.  

**Durante a conversão**:
- Novas definições que não estavam na versão original que estava a utilizar são adicionadas e definidas para utilizar os valores predefinidos.  

- As definições que não estão na nova versão de linha de base que selecionar são removidas e já não são aplicadas por este perfil de linha de base de segurança.  

  Quando uma definição já não é gerida por um perfil de linha de base, essa definição não for redefinida no dispositivo. Em vez disso, a definição do dispositivo permanece definido para a sua última configuração até que outro processo gerencia a definição de alterá-la. Exemplos de processos que podem alterar uma configuração depois de interromper a gerenciá-lo incluem um perfil de linha de base diferentes, uma definição de política de grupo ou configuração manual, que é efetuada no dispositivo. 

### <a name="to-change-the-instance-for-a-baseline"></a>Para alterar a instância para uma linha de base  

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973) e, em seguida, selecione **segurança do dispositivo** > **linhas de base de segurança**e, em seguida, selecione o mosaico para o tipo de linha de base que tenha o perfil que pretende Para alterar.  

2. Em seguida, selecione **perfis**e, em seguida, selecione a caixa de verificação para o perfil que pretende editar e, em seguida, selecione **alterar versão**.  

   ![Selecione uma linha de base](./media/security-baselines/select-baseline.png)  

3. Sobre o **alterar versão do** painel, utilize o **Selecione uma linha de base de segurança para atualizar para** lista pendente e selecione a instância de versão que pretende utilizar.  

   ![Selecionar uma versão](./media/security-baselines/select-instance.png)  
 
4. Selecione **atualização de revisão** para transferir um ficheiro CSV que mostra a diferença entre a versão de instância atual de perfis e a nova versão que selecionou. Consulte este ficheiro, para que entenda quais configurações são adicionadas, removidas, e quais são os valores predefinidos para estas definições no perfil atualizado.  

   Quando estiver pronto, avance para o passo seguinte.  

5. Escolha uma das duas opções para **selecionar um método para atualizar o perfil**: 
   - **Aceitar as alterações de linha de base, mas manter a minha definição personalizações existente** -esta opção mantém as personalizações que efetuou para o perfil de linha de base e aplica-se para a nova versão que selecionou para utilizar.
   - **Aceitar as alterações de linha de base e descartar existente definição personalizações** -esta opção substitui o seu perfil original completamente. O perfil atualizado irá utilizar os valores predefinidos para todas as definições.  

6. Selecione **submeter**. As atualizações de perfil para a versão de linha de base selecionada e após a conversão for concluída, a linha de base reimplementa imediatamente para grupos atribuídos.

## <a name="remove-a-security-baseline-assignment"></a>Remover uma atribuição de linha de base de segurança
Quando a definição de linha de base de segurança já não se aplica a um dispositivo, ou as definições de numa linha de base são definidas para *não configurado*, essas definições num dispositivo não reverter para uma configuração de pré-gerenciada. Em vez disso, as definições anteriormente geridas no dispositivo mantenha suas últimas configurações uma vez recebido da linha de base até que outro processo atualiza essas definições no dispositivo.  

Outros processos que mais tarde poderão alterar as definições do dispositivo incluem uma linha de base de segurança novo ou diferente, perfil de configuração do dispositivo, as configurações da política de grupo ou a edição manual da definição no dispositivo.  





## <a name="q--a"></a>Perguntas e Respostas

#### <a name="why-these-settings"></a>Por que estas definições?

A equipa de segurança da Microsoft tem anos de experiência trabalhando diretamente com os desenvolvedores do Windows e da Comunidade de segurança para criar estas recomendações. As definições nesta linha de base são consideradas as opções de configuração relacionadas com segurança mais relevantes. Em cada nova compilação do Windows, a equipe ajusta as recomendações com base nos recursos recentemente publicados.

#### <a name="is-there-a-difference-in-the-recommendations-for-windows-security-baselines-for-group-policy-vs-intune"></a>Existe uma diferença nas recomendações para linhas base de segurança do Windows para o vs de política de grupo. Intune?

Da mesma equipe de segurança da Microsoft escolheu e organizados as definições para cada linha de base. O Intune inclui todas as configurações relevantes na linha de base de segurança do Intune. Existem algumas definições na linha de base de política de grupo que são específicas para um controlador de domínio no local. Estas definições são excluídas da recomendações do Intune. Todas as outras definições são os mesmos.

#### <a name="are-the-intune-security-baselines-cis-or-nsit-compliant"></a>São as Intune segurança linhas de base de itens de configuração ou NSIT em conformidade?

Estritamente em termos, não. A equipe de segurança da Microsoft consulta organizações, como itens de configuração, para compilar suas recomendações. No entanto, não existe um mapeamento entre "CIS e compatível com" linhas de base da Microsoft.

#### <a name="what-certifications-does-microsofts-security-baselines-have"></a>As certificações tem linhas de base da Microsoft? 

- A Microsoft continua a publicar linhas de base de segurança para as políticas de grupo (GPOs) e o [Kit de ferramentas de compatibilidade de segurança](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10), porque tem por muitos anos. Essas linhas de base são usadas por muitas organizações. As recomendações apresentadas nessas linhas de base são de envolvimento da equipe de segurança da Microsoft com clientes corporativos e órgãos externos, incluindo o departamento de defesa (DoD), instituto nacional de normas e tecnologia (NIST) e muito mais. Compartilhamos nosso recomendações e linhas de base com essas organizações. Essas organizações também têm suas próprias recomendações que espelham estreitamente recomendações da Microsoft. Como a gestão de dispositivos móveis (MDM) continua a crescer para a cloud, a Microsoft criou equivalentes recomendações de MDM dessas linhas de base de política de grupo. Essas linhas de base adicionais incorporadas no Microsoft Intune e incluem relatórios de conformidade em utilizadores, grupos e dispositivos que sigam (ou não siga) a linha de base.

- Muitos clientes estão a utilizar as recomendações de linha de base do Intune como um ponto de partida e, em seguida, personalizá-la para atender às suas IT e solicitações de segurança. Windows 10 RS5 do Microsoft **linha de base de segurança de MDM** é a primeira linha de base para libertar. Esta linha de base foi concebida como uma infraestrutura genérica que permite aos clientes, eventualmente, importar outras linhas de base de segurança com base nos itens de configuração, NIST e outros padrões. Atualmente, ele está disponível para Windows e, eventualmente, irá incluir o iOS e Android.

- Migrar de políticas de grupo do Active Directory no local para uma solução de cloud pura através do Azure Active Directory (AD) com o Microsoft Intune é uma jornada. Para ajudar a, existem modelos incluídos de diretiva de grupo a [Kit de ferramentas de compatibilidade de segurança](https://docs.microsoft.com/windows/security/threat-protection/security-compliance-toolkit-10) que podem ajudar a gerir o AD híbrido e de dispositivos associados ao AD Azure. Estes dispositivos podem obter as definições de MDM da cloud (Intune) e as definições de política de grupo de controladores de domínio no local, conforme necessário.

## <a name="next-steps"></a>Passos Seguintes
- Ver as definições nas versões mais recentes das linhas de base disponíveis:  
  - [Linha de base de segurança MDM](security-baseline-settings-windows.md)  
  - [Linha de base do Windows Defender ATP](security-baseline-settings-defender-atp.md)  

- Verifique o estado e o monitor a [linha de base e perfil](security-baselines-monitor.md).
