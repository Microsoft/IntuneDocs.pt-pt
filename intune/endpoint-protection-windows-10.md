---
title: "Definições de proteção de ponto final do Intune para o Windows 10"
titlesuffix: Azure portal
description: "Saiba que definições do Intune pode utilizar para controlar as definições de proteção de ponto final, como o BitLocker, em dispositivos com o Windows 10."
keywords: 
author: arob98
ms.author: angrobe
manager: angrobe
ms.date: 08/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3af7c91b-8292-4c7e-8d25-8834fcf3517a
ms.reviewer: ilwu
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 19c20ac5dd73b45dc06d1df6a7d08cc6bac42982
ms.sourcegitcommit: 769db6599d5eb0e2cca537d0f60a5df9c9f05079
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 09/15/2017
---
# <a name="endpoint-protection-settings-for-windows-10-and-later-in-microsoft-intune"></a>Definições de proteção de ponto final para o Windows 10 e versões posteriores no Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

O perfil de proteção de ponto final permite-lhe controlar as funcionalidades de segurança em dispositivos com o Windows 10, como o BitLocker e o Windows Defender.

Utilize as informações neste tópico para saber como criar perfis de proteção de ponto final.

## <a name="create-an-endpoint-protection-profile"></a>Criar um perfil de proteção de ponto final

1. Inicie sessão no portal do Azure.
2. Escolha **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
3. No painel **Intune**, escolha **Configuração do dispositivo**.
2. No painel **Configuração do Dispositivo**, escolha **Gerir** > **Perfis**.
3. No painel de perfis, escolha **Criar Perfil**.
4. No painel **Criar Perfil**, introduza um **Nome** e uma **Descrição** para o perfil de funcionalidades de dispositivos.
5. Na lista pendente **Plataforma**, selecione **Windows 10 e posterior**.
6. Na lista pendente **Tipo de perfil**, selecione **Proteção de ponto final**.
7. No painel **Encriptação do Windows**, configure as definições que pretende. Utilize os detalhes neste tópico para o ajudar a compreender o que faz cada definição. Quando terminar, escolha **OK**.
8. Regresse ao painel **Criar Perfil** e selecione **Criar**.

O perfil é criado e apresentado no painel da lista de perfis.

## <a name="windows-defender-smartscreen-settings"></a>Definições do Windows Defender SmartScreen

- **SmartScreen para aplicações e ficheiros** – ative o Windows SmartScreen para a execução de ficheiros e aplicações em execução.
- **Execução de ficheiros não verificados** – não permita que o utilizador final execute ficheiros que não foram verificados pelo Windows SmartScreen.

## <a name="windows-encryption-settings"></a>Definições de encriptação do Windows

### <a name="windows-settings"></a>Definições do Windows

- **Exigir que os dispositivos sejam encriptados (apenas ambiente de trabalho)** – se ativada, é pedido aos utilizadores que ativem a encriptação de dispositivos. Adicionalmente, é-lhes pedido que confirmem que a encriptação de outro fornecedor não foi ativada. Se a encriptação do Windows for ativada enquanto outro método de encriptação estiver ativo, o dispositivo pode tornar-se instável.
- **Exigir que o Cartão de Armazenamento seja encriptado (móvel apenas)** – ative esta definição para encriptar todos os cartões de armazenamento removíveis utilizados pelo dispositivo.


### <a name="bitlocker-base-settings"></a>Definições base do BitLocker

- **Configurar métodos de encriptação** – ative esta definição para configurar algoritmos de encriptação para o sistema operativo, dados e unidades amovíveis.
    - **Encriptação para unidades de sistema operativo** – selecione o método de encriptação para as unidades de sistema operativo. Recomendamos que utilize o algoritmo XTS-AES.
    - **Encriptação para unidades de dados fixas** – selecione o método de encriptação para unidades de dados fixas (incorporadas). Recomendamos que utilize o algoritmo XTS-AES.
    - **Encriptação para unidades de dados removíveis** – selecione o método de encriptação para unidades de dados amovíveis. Se a unidade amovível for utilizada com dispositivos que não executam o Windows 10, recomendamos que utilize o algoritmo AES-CBC.


### <a name="bitlocker-os-drive-settings"></a>Definições de unidades de SO do BitLocker

- **Exigir a autenticação adicional no arranque** -
    - **BitLocker com chip do TPM não compatível** -
    - **Arranque do TPM** – configure se o chip de TPM é permitido, não permitido ou exigido.
    - **PIN de arranque do TPM** – configure se utilizar um PIN de arranque do TPM é permitido, não permitido ou exigido.
    - **Chave de arranque do TPM** – configure se utilizar uma chave de arranque do TPM é permitido, não permitido ou exigido.
    - **Chave e PIN de arranque do TPM** – configure se utilizar uma chave e PIN de arranque do TPM é permitido, não permitido ou exigido.
- **Comprimento Mínimo do PIN ** – ative esta definição para configurar um comprimento mínimo para o PIN de arranque do TPM.
    - **Carateres mínimos** – introduza o número de carateres necessários para o PIN de arranque de **4**-**20**.
- **Ativar a recuperação da unidade de SO** – ative esta definição para controlar a forma como as unidades de sistema operativo protegidas pelo BitLocker são recuperadas quando as informações de arranque necessárias não estão disponíveis.
    - **Agente de recuperação de dados baseada em certificados** – ative esta definição se quiser que os agentes de recuperação de dados possam ser utilizados com as unidades de sistema operativo protegidas pelo BitLocker.
    - **Criação de palavra-passe de recuperação pelo utilizador** – configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma palavra-passe de recuperação de 48 dígitos.
    - **Criação da chave de recuperação pelo utilizador** – configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma chave de recuperação de 256 bits.
    - **Ocultar opções de recuperação no assistente de configuração do BitLocker** – ative esta definição para impedir que os utilizadores vejam ou alterem opções de recuperação quando ativam o BitLocker.
    - **Guardar as informações de recuperação do BitLocker no AD DS** – permite o armazenamento das informações de recuperação do BitLocker no Active Directory.
    - **Configurar o armazenamento das informações de recuperação do BitLocker para AD DS** – configure que partes das informações de recuperação do BitLocker são armazenadas no Active Directory. Escolha entre:
        - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
        - **Apenas palavras-passe de recuperação de cópia de segurança**
    - **Requer que as informações de recuperação sejam armazenadas no AD DS antes de ativar o BitLocker** – ative esta definição para impedir os utilizadores de ativarem o BitLocker, a menos que o dispositivo esteja associado a um domínio e as informações de recuperação do BitLocker estejam armazenadas com êxito no Active Directory.
- **Ativar a mensagem de recuperação de pré-arranque e o URL** – ative esta definição para configurar a mensagem e o URL que são apresentados no ecrã de recuperação da chave de pré-arranque.
    - **Mensagem de recuperação de pré-arranque** – configure de que forma é que a mensagem de recuperação de pré-arranque é apresentada aos utilizadores. Escolha entre:
        - **Utilizar mensagem de recuperação predefinida e URL**
        - **Utilizar mensagem de recuperação vazia e URL**
        - **Utilizar mensagem de recuperação personalizada**
        - **Utilizador URL de recuperação personalizada**


### <a name="bitlocker-fixed-data-drive-settings"></a>Definições de unidades de dados fixas do BitLocker

- **Recusar o acesso de escrita para unidade de dados fixa não protegida pelo BitLocker** – se ativada, a proteção do BitLocker tem de ser ativada em todas as unidades de dados incorporadas ou fixas para que seja possível escrever nas mesmas.
- **Ativar recuperação de unidade fixa**– ative esta definição para controlar a forma como as unidades fixas protegidas pelo BitLocker são recuperadas quando as informações de arranque necessárias não estão disponíveis.
    - **Agente de recuperação de dados** – ative esta definição se quiser que os agentes de recuperação de dados sejam utilizados com as unidades fixas protegidas pelo BitLocker.
    - **Criação de palavra-passe de recuperação pelo utilizador** – configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma palavra-passe de recuperação de 48 dígitos.  
    - **Criação da chave de recuperação pelo utilizador** – configure se é permitido, não permitido ou exigido aos utilizadores gerarem uma chave de recuperação de 256 bits.
    - **Ocultar opções de recuperação no assistente de configuração do BitLocker** – ative esta definição para impedir que os utilizadores vejam ou alterem opções de recuperação quando ativam o BitLocker.
    - **Guardar as informações de recuperação do BitLocker no AD DS** – permite o armazenamento das informações de recuperação do BitLocker no Active Directory.
    - **Configurar o armazenamento das informações de recuperação do BitLocker para AD DS** – configure que partes das informações de recuperação do BitLocker são armazenadas no Active Directory. Escolha entre:
        - **Palavras-passe de recuperação de cópia de segurança e pacotes de chaves**
        - **Apenas palavras-passe de recuperação de cópia de segurança**
    - **Requer que as informações de recuperação sejam armazenadas no AD DS antes de ativar o BitLocker** – ative esta definição para impedir os utilizadores de ativarem o BitLocker, a menos que o dispositivo esteja associado a um domínio, e as informações de recuperação do BitLocker são armazenadas com êxito no Active Directory.


### <a name="bitlocker-removable-data-drive-settings"></a>Definições de unidades de dados removíveis do BitLocker

- **Recusar o acesso de escrita para a unidade de dados removível não protegida pelo BitLocker** – especifique se a encriptação do BitLocker é necessária para as unidades de armazenamento amovíveis.
    - **Bloquear o acesso de escrita a dispositivos configurados noutra organização** – especifique se é possível escrever nas unidades de dados amovíveis que pertencem a outra organização.



## <a name="next-steps"></a>Passos seguintes

Se quiser continuar e atribuir este perfil a grupos, veja [Como atribuir perfis de dispositivo](device-profile-assign.md).
