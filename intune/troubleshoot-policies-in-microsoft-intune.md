---
title: Resolver problemas com políticas no Microsoft Intune – Azure | Microsoft Docs
description: Problemas comuns e resoluções quando utilizar políticas no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/14/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.openlocfilehash: bb55ddc283ce4633b5057d5b96ae2ed6973dcf8a
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52181773"
---
# <a name="troubleshoot-policies-in-intune"></a>Resolver políticas no Intune

Se estiver a ter problemas ao implementar e gerir políticas do Intune, comece por aqui. Este artigo descreve alguns problemas comuns que podem ocorrer e possíveis soluções.

## <a name="general-issues"></a>Problemas Gerais

### <a name="was-a-deployed-policy-applied-to-the-device"></a>Foi aplicada uma política implementada ao dispositivo?
**Problema:** não tem a certeza se uma política foi corretamente aplicada.

No Intune > **Dispositivos** > **Todos os dispositivos** > selecione o dispositivo > **Configuração do dispositivo**, todos os dispositivos indicam as respetivas políticas. Cada política tem um **Estado**. O estado é aplicado quando todas as políticas aplicáveis ao dispositivo, incluindo as restrições e os requisitos de hardware e do sistema operativo, são consideradas em conjunto. Estados possíveis:

- **Em conformidade**: o dispositivo recebeu a política e comunica ao serviço que está em conformidade com a definição.

- **Não aplicável**: a definição de política não é aplicável. Por exemplo, as definições de e-mail para dispositivos iOS não seriam aplicadas a um dispositivo Android.

- **Pendente**: a política foi enviada para o dispositivo, mas ainda não comunicou o estado ao serviço. Por exemplo, a encriptação no Android requer que o utilizador final ative a encriptação e, por isso, poderá estar pendente.

> [!NOTE]
> Quando duas políticas com diferentes níveis de restrição se aplicam ao mesmo dispositivo ou utilizador, é aplicada a política mais restrita.

## <a name="issues-with-enrolled-devices"></a>Problemas com dispositivos inscritos

### <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Alerta: Falha ao Guardar as Regras de Acesso no Exchange
**Problema**: Recebe o alerta **Falha ao Guardar as Regras de Acesso no Exchange**  na consola de administração.

Se tiver criado políticas na área de trabalho Política do Exchange No Local na Consola de Administração, mas estiver a utilizar o O365, as definições de política configuradas não são impostas pelo Intune. Tenha em atenção a origem da política do alerta.  Na área de trabalho Política do Exchange No Local, elimine as regras legadas. As regras legadas são regras globais do Exchange no Intune para o Exchange no local e não são relevantes para o O365. Em seguida, crie a nova política para o Office 365.

### <a name="cannot-change-security-policy-for-various-enrolled-devices"></a>Não é possível alterar a política de segurança de vários dispositivos inscritos
Os dispositivos Windows Phone não permitem que as políticas de segurança definidas através de MDM ou EAS sejam reduzidas em termos de segurança depois de serem configuradas. Por exemplo, defina um **Número mínimo de carateres de palavra-passe** para 8 e, em seguida, tente reduzir para 4. A política mais restritiva já foi aplicada ao dispositivo.

Consoante a plataforma de dispositivo, se pretender alterar a política para um valor menos seguro, poderá ter de repor as políticas de segurança.

Por exemplo, no ambiente de trabalho do Windows, percorra a partir da direita para abrir a barra **Atalhos**. Escolha **Definições** > **Painel de Controlo**e selecione **Contas de Utilizador**. No lado esquerdo, selecione a ligação **Repor Políticas de Segurança** e escolha **Repor Políticas**.

Outros dispositivos MDM, como Android, Windows Phone 8.1 e posterior, e iOS, poderão ter de ser extintos e reinscritos no serviço para aplicar uma política menos restritiva.

## <a name="issues-with-pcs-that-run-the-intune-software-client"></a>Problemas com PCs que executam o cliente de software do Intune

Aplica-se ao portal clássico.

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Erros relacionados com políticas do Microsoft Intune no policyplatform.log
Nos PCs Windows geridos sem o cliente de software do Intune, os erros de políticas no ficheiro policyplatform.log podem ser o resultado das definições não predefinidas no Controlo de Conta de Utilizador no Windows (UAC) no dispositivo. Algumas definições de UAC não predefinidas podem afetar as instalações de cliente do Microsoft Intune e a execução de políticas.

#### <a name="resolve-uac-issues"></a>Resolver problemas de UAC

1. Extinga o computador. Veja [Remover dispositivos](devices-wipe.md).

2. Aguarde 20 minutos para que o software de cliente seja removido.

    > [!NOTE]
    > Não tente remover o cliente nos Programas e Funcionalidades.

3. No menu Iniciar, escreva **UAC** para abrir as definições de Controlo de Conta de Utilizador.

4. Mova o controlo de deslize de notificações para a predefinição.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>ERRO: Não é possível obter o valor do computador, 0x80041013
Ocorre se a hora no sistema local estiver dessincronizada em cinco minutos ou mais. Se a hora no computador local estiver dessincronizada, as transações seguras irão falhar porque os carimbos de data/hora serão inválidos.

Para resolver este problema, defina a hora do sistema local para o mais próximo possível da hora da Internet ou da hora definida nos controladores de domínio na rede.

### <a name="next-steps"></a>Passos Seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [obter suporte para o Microsoft Intune](get-support.md).
