---
# required metadata

title: Resolver problemas de políticas | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 05/26/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Resolver problemas de políticas no Microsoft Intune

Seguem-se alguns problemas que podem surgir na configuração de políticas do Microsoft Intune e as recomendações de resolução desses problemas.

Se estas informações não resolverem o problema, veja [How to get support for Microsoft Intune (Como obter suporte para o Microsoft Intune)](how-to-get-support-for-microsoft-intune.md) para ver mais formas de ajuda.


## A política é aplicada ao dispositivo?
**Problema:** Não é claro se uma determinada política está a ser aplicada a um dispositivo ou se um dispositivo está a ter um comportamento contrário ao indicado numa política.

Consulte as informações de política disponíveis para cada dispositivo para compreender como uma política afeta um dispositivo específico.

Na consola de administração do Intune, todos os dispositivos têm um separador de política em **Propriedades do Dispositivo**. Se não for o caso, o dispositivo ainda pode estar no processo de inscrição ou poderá não ter políticas aplicadas. Cada política tem um **Valor Pretendido** e um **Estado**. O valor pretendido é o que esperava obter com a atribuição da política. O estado é o que é realmente obtido quando todas as políticas que se aplicam ao dispositivo, bem como as restrições e os requisitos de hardware e do sistema operativo, são consideradas em conjunto. Estados possíveis:

-   **Em conformidade**: o dispositivo recebeu a política e comunica ao serviço que está em conformidade com a definição.

-   **Não aplicável**: a definição de política não é aplicável. Por exemplo, as definições de e-mail para dispositivos iOS não seriam aplicadas a um dispositivo Android.

-   **Pendente**: a política foi enviada para o dispositivo, mas ainda não comunicou o estado ao serviço. Por exemplo, a encriptação no Android requer que o utilizador final ative a encriptação e, por isso, poderá estar pendente.

Na captura de ecrã abaixo, pode ver dois exemplos claros:

-   A opção**Permitir palavras-passe simples** está definida como **Sim**, conforme apresentado na coluna **Valor Pretendido**, mas o **Estado** está definido como **Não aplicável**. Isto ocorre porque os dispositivos Android não suportam as palavras-passe simples.

-   Da mesma forma, o item de política expandida **Definições de e-mail para dispositivos iOS** não se aplica a este dispositivo, uma vez que é um dispositivo Android.

![Política de dispositivo do Intune](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE] Lembre-se de que quando duas políticas com diferentes níveis de restrição se aplicam ao mesmo dispositivo ou utilizador, na prática, é aplicada a política mais restrita.

## Política e intervalos de atualização
Tenha em atenção que as políticas são atualizadas em intervalos regulares. Em geral, as políticas devem ser registadas nos dispositivos num período de 15 minutos após efetuar uma alteração. Eis mais detalhes sobre os intervalos regulares de atualização de políticas:

-   **Dispositivos Windows inscritos na MDM**: é acionada através de uma tarefa agendada às 3:00 (hora local) no dispositivo e ocorre diariamente.

-   **Windows Phone**: a política é atualizada a cada oito horas. Pode ser forçada por uma atualização no Portal da Empresa, em **Definições**.

-   **iOS**: a política é atualizada uma vez por dia num intervalo de tempo aleatório. Também pode ser forçada ao abrir o Portal da Empresa, selecionar o dispositivo e escolher **Sincronizar**.

-   **Android**: a política é atualizada uma vez por dia num intervalo de tempo aleatório. Também pode ser forçada ao abrir o Portal da Empresa, selecionar o dispositivo e escolher **Sincronizar**.

## Erros relacionados com políticas do Microsoft Intune no policyplatform.log
Nos dispositivos Windows sem MDM, os erros de políticas no ficheiro policyplatform.log podem ser o resultado das definições não predefinidas no Controlo de Conta de Utilizador no Windows (UAC) no dispositivo. Algumas definições de UAC não predefinidas podem afetar as instalações de cliente do Microsoft Intune e a execução de políticas.

### Para resolver problemas de UAC

1.  Extinga o computador, conforme descrito em [Extinguir dispositivos da gestão do Microsoft Intune](/intune/deploy-use/retire-devices-from-microsoft-intune-management).

2.  Aguarde 20 minutos para que o software de cliente seja removido.

    > [!NOTE] Não tente remover o cliente dos Programas e Funcionalidades.

3.  No menu Iniciar, escreva **UAC** para abrir as definições de Controlo de Conta de Utilizador.

4.  Mova o controlo de deslize de notificações para a predefinição.

## Erro 0x87D1FDE8 para dispositivo KNOX
**Problema**: depois de criar e implementar um perfil de e-mail do Exchange Active Sync para Samsung KNOX em vários dispositivos Android, é comunicado o erro **0x87D1FDE8** ou **falha na remediação** no separador propriedades &gt; política do dispositivo.

Reveja a configuração do seu perfil EAS para Samsung KNOX e a política de origem. A opção de sincronização do Samsung Notes já não é suportada e não deve ser selecionada no seu perfil. Certifique-se de que os dispositivos têm tido tempo suficiente para processar a política, até 24 horas.

## Alerta: Falha ao Guardar as Regras de Acesso no Exchange
**Problema**: Recebe o alerta **Falha ao Guardar as Regras de Acesso no Exchange**  na consola de administração.

Se tiver criado políticas na área de trabalho Política do Exchange No Local na Consola de Administração, mas estiver a utilizar o Office 365, as definições de política configuradas não são impostas pelo Intune. Tenha em atenção a origem da política do alerta.  Na área de trabalho Política do Exchange No Local, elimine as regras legadas, uma vez que estas são regras globais do Exchange no Intune para o Exchange no local e não são relevantes para o Office 365. Em seguida, crie a nova política para o Office 365.

## ERRO: Não é possível obter o valor do computador, 0x80041013
Isto pode ocorrer se a hora no sistema local estiver dessincronizada em cinco minutos ou mais. Se a hora no computador local estiver dessincronizada, as transações seguras irão falhar porque os carimbos de data/hora serão inválidos.

Para resolver este problema, defina a hora do sistema local para o mais próximo possível da hora da Internet ou da hora definida nos controladores de domínio na rede.

## Não é possível alterar a política de segurança de vários dispositivos MDM
Os dispositivos Windows Phone e Windows RT não permitem que as políticas de segurança definidas através de MDM ou EAS sejam reduzidas em termos de segurança depois de serem configuradas. Por exemplo, defina um **Número mínimo de carateres de palavra-passe** para 8 e, em seguida, tente reduzir para 4. A política mais restritiva já foi aplicada ao dispositivo.

Consoante a plataforma de dispositivo, se pretender alterar a política para um valor menos seguro, poderá ter de repor as políticas de segurança.
Por exemplo, no ambiente de trabalho do Windows RT, percorra a partir da direita para abrir a barra **Atalhos** e escolha **Definições** &gt; **Painel de Controlo**.  Selecione a miniaplicação **Contas de Utilizador** .
No menu de navegação esquerdo, existe uma ligação **Repor Políticas de Segurança** na parte inferior. Escolha a mesma e, em seguida, escolha o botão **Repor Políticas**.
Outros dispositivos MDM, tal como Android, Windows Phone 8.1 e posterior, e iOS, poderão ter de ser extintos e reinscritos no serviço para que possa aplicar uma política menos restritiva.

## Os dispositivos Android não impõem Alterações de Política de Segurança sem Aceitação do utilizador final
O Android MDM não permite ao serviço impor alterações de política iniciais nos dispositivos, como permitem outras plataformas. Isto deve-se à funcionalidade Android e não está relacionado com o serviço Intune. Os dispositivos Android indicarão ao utilizador final através da janela de notificação a alteração de política relacionada (ou seja, Palavra-passe, Encriptação, etc.).  O utilizador final tem de responder ao pedido e, depois de aceite, a política deverá ser aplicada.

## Não é possível criar a política ou inscrever clientes se o nome da empresa incluir carateres especiais
**Problema:** não é possível criar a política ou inscrever clientes.

**Resolução:** No [centro de administração do Office 365](https://portal.office.com/), remova os carateres especiais do nome da empresa e guarde as informações da empresa.

### Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).


<!--HONumber=May16_HO4-->


