---
title: O dispositivo Android parece estar encriptado | Microsoft Docs
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 661ddaa2b6b100ccf1b1b890a2c39556723a5cc9
ms.sourcegitcommit: 9bd6278d129fa29f184b2d850138f8f65f3674ea
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/09/2018
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>O seu dispositivo Android parece estar encriptado, mas o Portal da Empresa diz o contrário

Ao encriptar um dispositivo, está a codificar informações no mesmo através de uma chave secreta que só você conhece. Isto impede o acesso ao dispositivo por parte de pessoas não autorizadas. Muitas organizações exigem que os utilizadores encriptem os respetivos dispositivos Android antes de poderem aceder aos ficheiros, e-mails ou dados da empresa.

## <a name="common-issues"></a>Problemas comuns

As versões mais recentes do Android, em particular a partir da versão 7.0, exigem um código de acesso de arranque para garantir que o dispositivo está totalmente encriptado. Os diferentes fabricantes de dispositivos têm descrições e locais distintos para o código de acesso de arranque. Esta definição é normalmente denominada "Arranque Seguro". 

## <a name="solutions"></a>Soluções

### <a name="add-a-startup-pin"></a>Adicionar um PIN de arranque

Determinados dispositivos Android exigem que crie um PIN de arranque para garantir que o dispositivo está seguro. Existem muitas versões do Android de muitos fabricantes diferentes. Pode tentar corrigir este problema ao encontrar um local na aplicação de definições para ativar esta opção. Por exemplo, no Galaxy S7 da Samsung, ativa o Arranque Seguro ao aceder a **Definições** > **Ecrã de Bloqueio e Segurança** > **Início Seguro**.  

### <a name="encrypt-the-entire-device"></a>Encriptar todo o dispositivo

Alguns dispositivos permitem-lhe optar por encriptar todo o dispositivo ou apenas o espaço utilizado do mesmo. Selecione a opção para encriptar todo o dispositivo em vez de "apenas o espaço utilizado". Se já encriptou apenas o espaço utilizado:

1. [Remova este dispositivo do Portal da Empresa](unenroll-your-device-from-intune-android.md)
2. Desencripte o espaço utilizado
3. Encriptar todo o dispositivo
4. Volte a inscrever o dispositivo

### <a name="downgrade-your-version-of-android"></a>Mudar a versão do Android para uma versão anterior

Se o seu dispositivo permitir mudar para a versão anterior Android 6.0+, faça-o. Existe um risco de perda de dados se tentar mudar o seu dispositivo para uma versão anterior. Em alternativa, recomendamos que contacte o suporte da empresa para resolver este problema. Pode obter as informações de contacto do suporte da empresa no [site do Portal da Empresa](https://portal.manage.microsoft.com#HelpDeskDialog).

## <a name="specific-manufacturer-issues"></a>Problemas de um fabricante específico

Alguns dispositivos Android com a versão 7.0 e superior encriptam os dados de forma inconsistente com determinadas normas da plataforma Android. Estes dispositivos poderão parecer encriptados mesmo quando são novos. O Intune reconhece que os métodos de encriptação destes dispositivos colocam as informações do mesmo em risco. Este risco está principalmente associado a utilizadores mal intencionados que têm acesso físico ao dispositivo.

> [!Note]
> A Microsoft trabalha com os fabricantes para abordar quaisquer problemas encontrados durante os testes ou comunicados pelos utilizadores. Atualizaremos este artigo sempre que estiverem disponíveis novas informações. 

## <a name="known-devices"></a>Dispositivos conhecidos

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Dispositivos conhecidos que podem ser atualizados para corrigir este problema

Caso tenha um dos seguintes dispositivos, pode ter este problema se não tiver atualizado o dispositivo para a versão mais recente do Android. Pode instalar as atualizações para estes dispositivos ao aceder a **Definições** > **Atualização**. 

- [Huawei Honor 8](https://consumer.huawei.com/us/support/phones/honor-8/)
- [Huawei P9](http://consumer.huawei.com/en/phones/p9/)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Dispositivos conhecidos que não podem ser atualmente atualizados para corrigir este problema

Pode resolver este problema para os dispositivos abaixo. Poderá ter de usar um dispositivo diferente para aceder aos recursos da empresa. 

- [Huawei Mate 8](https://consumer.huawei.com/en/mobile-phones/mate8/index.htm)
- [Dispositivos OPPO](http://www.oppo.com/en/smartphones)
- [Dispositivos Vivo](https://www.vivo.co.in)
- [Smartphones Xiaomi Mi](https://xiaomi-mi.com/mi-smartphones/)
