---
title: "Resolver problemas de políticas | Microsoft Intune"
description: "Resolva problemas de configuração de políticas."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ms.reviewer: tscott
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e95db6d0ccbe350984f11ce08749b700c2f5ad01
ms.openlocfilehash: fbc18b12c00a4b61f7419731c6b4306b583638cc


---

# Resolver problemas de políticas no Microsoft Intune

Se estiver a ter problemas de implementação e gestão de políticas com o Intune, comece por aqui. Este tópico contém alguns problemas comuns que poderá encontrar juntamente com as soluções.

## Problemas Gerais

### Foi aplicada uma política implementada ao dispositivo?
**Problema:** não tem a certeza se uma política foi corretamente aplicada.

Na consola de administração do Intune, todos os dispositivos têm um separador de política em **Propriedades do Dispositivo**. Cada política tem um **Valor Pretendido** e um **Estado**. O valor pretendido é o que esperava obter com a atribuição da política. O estado é o que é realmente aplicado quando todas as políticas aplicáveis ao dispositivo, bem como as restrições e os requisitos de hardware e do sistema operativo, são consideradas em conjunto. Estados possíveis:

-   **Em conformidade**: o dispositivo recebeu a política e comunica ao serviço que está em conformidade com a definição.

-   **Não aplicável**: a definição de política não é aplicável. Por exemplo, as definições de e-mail para dispositivos iOS não seriam aplicadas a um dispositivo Android.

-   **Pendente**: a política foi enviada para o dispositivo, mas ainda não comunicou o estado ao serviço. Por exemplo, a encriptação no Android requer que o utilizador final ative a encriptação e, por isso, poderá estar pendente.

Na captura de ecrã abaixo, pode ver dois exemplos claros:

-   A opção**Permitir palavras-passe simples** está definida como **Sim**, conforme apresentado na coluna **Valor Pretendido**, mas o **Estado** está definido como **Não aplicável**. Isto ocorre porque os dispositivos Android não suportam as palavras-passe simples.

-   Da mesma forma, o item de política expandida **Definições de e-mail para dispositivos iOS** não se aplica a este dispositivo, uma vez que é um dispositivo Android.

![Política de dispositivo do Intune](../media/Intune-Device-Policy-v.2.jpg)

> [!NOTE]
> Lembre-se de que quando duas políticas com diferentes níveis de restrição se aplicam ao mesmo dispositivo ou utilizador, na prática, é aplicada a política mais restrita.


## Problemas com dispositivos inscritos

### Alerta: Falha ao Guardar as Regras de Acesso no Exchange
**Problema**: Recebe o alerta **Falha ao Guardar as Regras de Acesso no Exchange**  na consola de administração.

Se tiver criado políticas na área de trabalho Política do Exchange No Local na Consola de Administração, mas estiver a utilizar o Office 365, as definições de política configuradas não são impostas pelo Intune. Tenha em atenção a origem da política do alerta.  Na área de trabalho Política do Exchange No Local, elimine as regras legadas, uma vez que estas são regras globais do Exchange no Intune para o Exchange no local e não são relevantes para o Office 365. Em seguida, crie a nova política para o Office 365.

### Não é possível alterar a política de segurança de vários dispositivos inscritos
Os dispositivos Windows Phone não permitem que as políticas de segurança definidas através de MDM ou EAS sejam reduzidas em termos de segurança depois de serem configuradas. Por exemplo, defina um **Número mínimo de carateres de palavra-passe** para 8 e, em seguida, tente reduzir para 4. A política mais restritiva já foi aplicada ao dispositivo.

Consoante a plataforma de dispositivo, se pretender alterar a política para um valor menos seguro, poderá ter de repor as políticas de segurança.
Por exemplo, no ambiente de trabalho do Windows, percorra a partir da direita para abrir a barra **Atalhos** e selecione **Definições** &gt; **Painel de Controlo**.  Selecione a miniaplicação **Contas de Utilizador** .
No menu de navegação esquerdo, existe uma ligação **Repor Políticas de Segurança** na parte inferior. Escolha a mesma e, em seguida, escolha o botão **Repor Políticas**.
Outros dispositivos MDM, tal como Android, Windows Phone 8.1 e posterior e iOS, poderão ter de ser extintos e reinscritos no serviço para que possa aplicar uma política menos restritiva.

## Problemas com PCs que executam o cliente de software do Intune

### Erros relacionados com políticas do Microsoft Intune no policyplatform.log
Nos PCs Windows geridos sem o cliente de software do Intune, os erros de políticas no ficheiro policyplatform.log podem ser o resultado das definições não predefinidas no Controlo de Conta de Utilizador no Windows (UAC) no dispositivo. Algumas definições de UAC não predefinidas podem afetar as instalações de cliente do Microsoft Intune e a execução de políticas.

#### Para resolver problemas de UAC

1.  Extinga o computador, conforme descrito em [Extinguir dispositivos da gestão do Microsoft Intune](/intune/deploy-use/retire-devices-from-microsoft-intune-management).

2.  Aguarde 20 minutos para que o software de cliente seja removido.

    > [!NOTE]
    > Não tente remover o cliente nos Programas e Funcionalidades.

3.  No menu Iniciar, escreva **UAC** para abrir as definições de Controlo de Conta de Utilizador.

4.  Mova o controlo de deslize de notificações para a predefinição.

### ERRO: Não é possível obter o valor do computador, 0x80041013
Isto pode ocorrer se a hora no sistema local estiver dessincronizada em cinco minutos ou mais. Se a hora no computador local estiver dessincronizada, as transações seguras irão falhar porque os carimbos de data/hora serão inválidos.

Para resolver este problema, defina a hora do sistema local para o mais próximo possível da hora da Internet ou da hora definida nos controladores de domínio na rede.








### Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).



<!--HONumber=Oct16_HO2-->


