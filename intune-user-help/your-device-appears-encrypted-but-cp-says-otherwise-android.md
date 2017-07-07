---
title: O dispositivo Android parece estar encriptado
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 269ad7968242f8f5ce7095c9c73347987675e846
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 07/01/2017
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>O seu dispositivo Android parece estar encriptado, mas o Portal da Empresa diz o contrário

Quando encripta um dispositivo, está a codificar as informações no mesmo com uma chave secreta que só você conhece, o que impede que pessoas não autorizadas acedam ao dispositivo. Para se certificar de que a sua informação está segura, a sua organização requer que encripte o seu dispositivo Android antes de poder aceder a ficheiros, e-mail ou dados da empresa.

## <a name="common-issues"></a>Problemas comuns

As versões mais recentes do Android, em particular a partir da versão 7.0, exigem um código de acesso de arranque para garantir que o dispositivo está totalmente encriptado. Os diferentes fabricantes de dispositivos têm descrições e locais distintos para o código de acesso de arranque. Na maioria das vezes, isso é conhecido como “Arranque Seguro”. 

## <a name="solutions"></a>Soluções

### <a name="add-a-startup-pin"></a>Adicionar um PIN de arranque

Determinados dispositivos Android exigirão que crie um PIN de arranque para garantir que o dispositivo está seguro. Existem muitas versões do Android de muitos fabricantes diferentes. Pode tentar corrigir este problema ao encontrar um local na aplicação de definições para ativar esta opção. Por exemplo, no Galaxy S7 da Samsung, ativa o Arranque Seguro ao aceder a **Definições** > **Ecrã de Bloqueio e Segurança** > **Início Seguro**.  

### <a name="downgrade-your-version-of-android"></a>Mudar a versão do Android para uma versão anterior
Se o seu dispositivo permitir mudar para a versão anterior Android 6.0+, faça-o. Existe um risco de perda de dados se tentar mudar o seu dispositivo para uma versão anterior. Em alternativa, recomendamos que contacte o seu administrador de TI para resolver este problema. Pode obter as informações de contacto do seu administrador de TI no [site do Portal da Empresa](http://portal.manage.microsoft.com).

## <a name="specific-manufacturer-issues"></a>Problemas de um fabricante específico

Alguns dispositivos Android com a versão 7.0+ encriptam os dados de forma inconsistente com determinadas normas da plataforma Android. Estes dispositivos podem parecer já vir encriptados de origem, mas o Intune considera que os métodos utilizados colocam as informações do dispositivo em risco de serem acedidos por utilizadores mal intencionados que tenham acesso físico ao dispositivo.

> [!Note]
> A Microsoft trabalha com os fabricantes para abordar quaisquer problemas encontrados durante os testes ou comunicados pelos utilizadores. Atualizaremos este artigo sempre que estejam disponíveis novas informações. 

## <a name="known-devices"></a>Dispositivos conhecidos

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Dispositivos conhecidos que podem ser atualizados para corrigir este problema

Caso tenha um dos seguintes dispositivos, pode ter este problema se não tiver atualizado o dispositivo para a versão mais recente do Android. Pode instalar as atualizações para estes dispositivos ao aceder a **Definições** > **Atualização**. 

- [Huawei Honor 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [Huawei P9](http://consumer.huawei.com/mobile-phones/p9/index.html)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Dispositivos conhecidos que não podem ser atualmente atualizados para corrigir este problema

- [Huawei Mate 8](http://consumer.huawei.com/en/mobile-phones/mate8/index.htm)
- [Smartphones Xiaomi Mi](https://xiaomi-mi.com/mi-smartphones/)
