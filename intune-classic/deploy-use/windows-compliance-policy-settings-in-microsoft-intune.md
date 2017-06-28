---
title: "Definições de política de conformidade para dispositivos Windows"
description: "Este tópico descreve as regras e definições que pode configurar numa política de conformidade para dispositivos Windows."
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 12/15/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: f996842c-e9a4-4819-acb4-ee66e8fb35b8
ms.reviewer: chrisgre
ms.suite: ems
ms.custom: intune-classic
ms.translationtype: Human Translation
ms.sourcegitcommit: df3c42d8b52d1a01ddab82727e707639d5f77c16
ms.openlocfilehash: 67810c51c7a7b2ec1e1ff33c11a27a8757b2bcbd
ms.contentlocale: pt-pt
ms.lasthandoff: 06/08/2017


---

# <a name="compliance-policy-settings-for-windows-devices-in-microsoft-intune"></a>Definições de política de conformidade para dispositivos Windows no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

As definições de política descritas neste tópico aplicam-se a dispositivos com o sistema operativo Windows. As secções seguintes descrevem as versões do Windows suportadas.

Se estiver à procura de informações sobre outras plataformas, selecione uma das seguintes opções:
> [!div class="op_single_selector"]
- [Definições de política de conformidade para dispositivos iOS](ios-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para dispositivos Android](android-compliance-policy-settings-in-microsoft-intune.md)
- [Definições de política de conformidade para Android for Work](afw-compliance-policy-settings-in-microsoft-intune.md)

## <a name="compliance-policy-settings-for-windows-phone-devices"></a>Definições de política de conformidade para dispositivos Windows Phone
As definições apresentadas nesta secção são suportadas no Windows Phone 8.1 e posterior.

### <a name="system-security-settings"></a>Definições de segurança do sistema
#### <a name="password"></a>Palavra-passe
- **Exigir uma palavra-passe para desbloquear dispositivos móveis:** defina esta opção como **Sim** para exigir que o utilizador introduza uma palavra-passe para que possa aceder ao respetivo dispositivo.

- **Permitir palavras-passe simples**: defina esta opção para **Sim** para permitir que o utilizador crie uma palavra-passe simples, como **1234** ou **1111**.

-  **Comprimento mínimo da palavra-passe**: especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.
- **Solicitar tipo de palavra-passe:** especifique se o utilizador tem de criar uma palavra-passe **Alfanumérica** ou **Numérica**.

  Nos dispositivos com Windows cujo acesso é feito com uma conta Microsoft, a política de conformidade não conseguirá avaliar corretamente se o comprimento mínimo da palavra-passe for superior a oito carateres ou se o número mínimo dos conjuntos de carateres for superior a dois.

- **Número mínimo de conjuntos de carateres**: se o **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especifica o número mínimo de conjuntos de carateres que a palavra-passe tem de conter. Os quatro conjuntos de carateres são:
  -   Letras minúsculas
  -   Letras maiúsculas
  -   Símbolos
  -   Números

  Definir um número mais elevado aqui irá exigir que o utilizador crie uma palavra-passe mais complexa. Nos dispositivos com Windows cujo acesso é feito com uma conta Microsoft, a política de conformidade não conseguirá avaliar corretamente se o comprimento mínimo da palavra-passe for superior a oito carateres ou se o número mínimo dos conjuntos de carateres for superior a dois.

- **Minutos de inatividade antes de a palavra-passe ser exigida**: esta definição especifica o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe do utilizador expirar e ser necessário criar uma nova.

- **Memorizar histórico de palavras-passe:** utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.

- **Impedir a reutilização de palavras-passe anteriores**: se a opção **Memorizar histórico de palavras-passe** estiver selecionada, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.
- **Exigir uma palavra-passe quando o dispositivo regressa de um estado inativo**: utilize esta definição em conjunto com a definição **Minutos de inatividade antes de a palavra-passe ser exigida**. Será pedido ao utilizador que introduza uma palavra-passe para aceder a dispositivos que tenham estado inativos durante o período de tempo especificado na definição **Minutos de inatividade antes de a palavra-passe ser exigida**.

  > [!NOTE]
  > Esta definição aplica-se apenas a dispositivos com o Windows 10 Mobile.

#### <a name="encryption"></a>Encriptação
- **Exigir encriptação no dispositivo móvel**: defina esta opção como **Sim** para exigir que os dispositivos sejam encriptados para poder ligar aos recursos.

### <a name="device-health-settings"></a>Definições de estado de funcionamento do dispositivo
- **Exigir que os dispositivos sejam comunicados como estando em bom estado de funcionamento**: pode definir uma regra para exigir que os dispositivos com o **Windows 10 Mobile** sejam comunicados como estando em bom estado de funcionamento nas políticas de conformidade novas ou existentes.  Se esta definição estiver ativada, os dispositivos com o Windows 10 são avaliados através do Serviço de Atestado de Estado de Funcionamento (HAS) quanto aos seguintes pontos de dados:
  -  **BitLocker está ativado**: se o BitLocker estiver ativado, o dispositivo poderá ajudar a proteger os dados que são armazenados na unidade contra acesso não autorizado, quando o sistema é desligado ou entra em hibernação. A Encriptação de Unidade BitLocker do Windows encripta todos os dados armazenados no volume do sistema operativo Windows. O BitLocker utiliza o TPM para ajudar a proteger o sistema operativo Windows e os dados de utilizador. O BitLocker também ajuda a garantir que os computadores não são adulterados, mesmo que não estejam a ser vigiados, sejam roubados ou se percam. Se os computadores estiverem equipados com um TPM compatível, o BitLocker utiliza o TPM para bloquear as chaves de encriptação que ajudam a proteger os dados. Como resultado, as chaves não podem ser acedidas até o TPM ter verificado o estado dos computadores.
  -  **A integridade do código está ativada**: a integridade do código é uma funcionalidade que valida a integridade de um ficheiro de controlador ou de sistema sempre que é carregado para a memória. A integridade do código deteta se um ficheiro de controlador ou de sistema não assinado está a ser carregado para o kernel. Também deteta se um ficheiro de sistema foi modificado por software malicioso que está a ser executado por uma conta de utilizador com privilégios administrativos.
  - **O Arranque Seguro está ativado**: se o Arranque Seguro estiver ativado, o sistema é forçado a fazer o arranque para um estado de fábrica fidedigno. Além disso, com o Arranque Seguro ativado, os componentes do núcleo utilizados para arrancar o computador têm de ter assinaturas criptográficas corretas e que sejam consideradas fidedignas pela organização que fabricou o dispositivo. O firmware UEFI verifica isto antes de permitir que o computador seja iniciado. Se um ficheiro tiver sido adulterado, danificando a respetiva assinatura, o sistema não arrancará.

  > [!IMPORTANT]
  > Os dispositivos Windows não suportam software **Antimalware de Arranque de Início Antecipado** (ELAM) de terceiros instalado como parte do atestado de estado de funcionamento do dispositivo.

  Para obter informações sobre como funciona o serviço HAS, veja [Health Attestation CSP (CSP de Atestado de Estado de Funcionamento)](https://msdn.microsoft.com/library/dn934876.aspx).
###  <a name="device-property-settings"></a>Definições de propriedade do dispositivo
- **SO mínimo necessário:** quando um dispositivo não cumpre o requisito de versão mínima do SO, será reportado como não conforme.
    É apresentada uma ligação com informações sobre como atualizar. O utilizador pode optar por atualizar o dispositivo para, em seguida, poder aceder aos recursos da empresa.

- **Versão do SO máxima permitida**: quando um dispositivo utiliza uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.


## <a name="compliance-policy-settings-for-windows-pcs"></a>Definições de política de conformidade para dispositivos PCs Windows
As definições apresentadas nesta secção são suportadas em PCs Windows.
### <a name="system-security-settings"></a>Definições de segurança do sistema
#### <a name="password"></a>Palavra-passe
- **Comprimento mínimo da palavra-passe**: suportado no Windows 8.1.

  Especifique o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de conter.

  Nos dispositivos acedidos com uma conta Microsoft, a política de conformidade não conseguirá avaliar corretamente se o **Comprimento mínimo da palavra-passe** for superior a oito carateres ou se o **Número mínimo de conjuntos de carateres** corresponder a mais de dois carateres.

- **Tipo obrigatório de palavra-passe**: suportado no Windows RT, Windows RT 8.1 e Windows 8.1.

  Especifique se o utilizador tem de criar uma palavra-passe **Alfanumérica** ou **Numérica**.

- **Número mínimo de conjuntos de carateres**: suportado no Windows RT, Windows RT 8.1 e Windows 8.1.

  Se o **Tipo obrigatório de palavra-passe** estiver definido como **Alfanumérico**, esta definição especifica o número mínimo de conjuntos de carateres que a palavra-passe tem de conter. Os quatro conjuntos de carateres são:
  -   Letras minúsculas
  -   Letras maiúsculas
  -   Símbolos
  -   Números     

  Definir um número mais elevado aqui irá exigir que o utilizador crie uma palavra-passe mais complexa. Nos dispositivos acedidos com uma conta Microsoft, a política de conformidade não conseguirá avaliar corretamente se o **Comprimento mínimo da palavra-passe** for superior a oito carateres ou se o **Número mínimo de conjuntos de carateres** corresponder a mais de dois carateres.

- **Minutos de inatividade antes de a palavra-passe ser exigida**: suportado no Windows RT, Windows RT 8.1 e Windows 8.1.

  Especifique o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe.

- **Expiração da palavra-passe (dias)**: suportado no Windows RT, Windows RT 8.1 e Windows 8.1.

  Selecione o número de dias antes de a palavra-passe do utilizador expirar e ser necessário criar uma nova.

- **Memorizar histórico de palavras-passe**: suportado no Windows RT, Windows RT 8.1 e Windows 8.1.

  Utilize esta definição juntamente com **Impedir a reutilização de palavras-passe anteriores** para impedir o utilizador de criar palavras-passe utilizadas anteriormente.

- **Impedir a reutilização de palavras-passe anteriores**: suportado no Windows RT, Windows RT 8.1 e Windows 8.1.

  Se a opção **Memorizar histórico de palavras-passe** estiver selecionada, especifique o número de palavras-passe utilizadas anteriormente que não podem ser reutilizadas.

### <a name="device-health-settings"></a>Definições de estado de funcionamento do dispositivo
- **Exigir que os dispositivos sejam comunicados como estando em bom estado de funcionamento**: suportado nos dispositivos com o Windows 10.
Pode definir uma regra para exigir que os dispositivos com o Windows 10 sejam comunicados como estando em bom estado de funcionamento nas políticas de conformidade novas ou existentes. Se esta definição estiver ativada, os dispositivos com o Windows 10 são avaliados através do Serviço de Atestado de Estado de Funcionamento (HAS) quanto aos seguintes pontos de dados:
  -  **BitLocker está ativado**: se o BitLocker estiver ativado, o dispositivo poderá ajudar a proteger os dados que são armazenados na unidade contra acesso não autorizado, quando o sistema é desligado ou entra em hibernação. A Encriptação de Unidade BitLocker do Windows encripta todos os dados armazenados no volume do sistema operativo Windows. O BitLocker utiliza o TPM para ajudar a proteger o sistema operativo Windows e os dados de utilizador. O BitLocker também ajuda a garantir que os computadores não são adulterados, mesmo que não estejam a ser vigiados, sejam roubados ou se percam. Se os computadores estiverem equipados com um TPM compatível, o BitLocker utiliza o TPM para bloquear as chaves de encriptação que ajudam a proteger os dados. Como resultado, as chaves não podem ser acedidas até o TPM ter verificado o estado dos computadores.
  -  **A integridade do código está ativada**: a integridade do código é uma funcionalidade que valida a integridade de um ficheiro de controlador ou de sistema sempre que é carregado para a memória. A integridade do código deteta se um ficheiro de controlador ou de sistema não assinado está a ser carregado para o kernel. Também deteta se um ficheiro de sistema foi modificado por software malicioso que está a ser executado por uma conta de utilizador com privilégios administrativos.
  - **O Arranque Seguro está ativado**: se o Arranque Seguro estiver ativado, o sistema é forçado a fazer o arranque para um estado de fábrica fidedigno. Além disso, com o Arranque Seguro ativado, os componentes do núcleo utilizados para arrancar o computador têm de ter assinaturas criptográficas corretas e que sejam consideradas fidedignas pela organização que fabricou o dispositivo. O firmware UEFI verifica isto antes de permitir que o computador seja iniciado. Se um ficheiro tiver sido adulterado, danificando a respetiva assinatura, o sistema não arrancará.
  - **O antimalware de início antecipado está ativado**: o antimalware de arranque de início antecipado (ELAM) assegura proteção para os computadores da sua rede quando são iniciados e antes de os controladores de terceiros serem inicializados.

  Para obter informações sobre como funciona o serviço HAS, veja [Health Attestation CSP (CSP de Atestado de Estado de Funcionamento)](https://msdn.microsoft.com/library/dn934876.aspx).

### <a name="device-property-settings"></a>Definições de propriedade do dispositivo
- **SO mínimo obrigatório**: suportado no Windows 8.1 e Windows 10.

  Especifique o número major.minor.build aqui. O número da versão tem de corresponder à versão devolvida pelo comando **winver**.

  Quando um dispositivo tem uma versão anterior à versão de SO especificada, é comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador pode optar por atualizar o dispositivo para, em seguida, poder aceder aos recursos da empresa.

- **Versão máxima de SO permitida**: suportado no Windows 8.1 e Windows 10.

  Quando um dispositivo está a utilizar uma versão do SO posterior à especificada na regra, o acesso aos recursos da empresa é bloqueado e é pedido ao utilizador que contacte o administrador de TI. Até a regra ser alterada para permitir a versão do SO, este dispositivo não pode ser utilizado no acesso aos recursos da empresa.

Para localizar a versão de SO a utilizar nas definições **SO mínimo obrigatório** e **Versão máxima de SO permitida**, execute o comando **winver** a partir da linha de comandos. O comando **winver** devolve a versão comunicada do SO.

- Os PCs Windows 8.1 devolvem a versão **6.3**. Se a regra de versão de SO estiver definida como Windows 8.1 para o Windows, o dispositivo é comunicado como não conforme, mesmo que tenha o sistema operativo Windows 8.1.

- Nos PCs com o Windows 10, a versão deve ser definida como **10.0** mais o número de compilação do SO devolvido pelo comando **winver**. Por exemplo, pode ser semelhante a 10.0.10586.
> ![Versão de compilação do SO realçada na caixa de diálogo "Acerca do Windows"](./media/ca_win10-os-version.png)

