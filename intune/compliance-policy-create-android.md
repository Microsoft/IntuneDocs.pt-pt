---
title: Criar uma política de conformidade de dispositivos Android no Microsoft Intune – Azure | Microsoft Docs
description: Criar ou configurar uma política de conformidade de dispositivos do Microsoft Intune para dispositivos Android. Opte por permitir dispositivos com jailbreak, defina o nível de ameaça aceitável, verifique o Google Play, introduza a versão do sistema operativo mínima e máxima, escolha os seus requisitos de palavra-passe e permita aplicações de sideload.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 10/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: e1258fe4-0b5c-4485-8bd1-152090df6345
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cb5fc7256e68b8ea10ba1b3ddd7cfe6ed44bd544
ms.sourcegitcommit: 51b763e131917fccd255c346286fa515fcee33f0
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52180617"
---
# <a name="add-a-device-compliance-policy-for-android-devices-in-intune"></a>Adicionar uma política de conformidade de dispositivos Android no Intune

Uma política de conformidade de dispositivos do Intune para Android especifica as regras e definições que os dispositivos Android têm de cumprir para serem considerados como estando em conformidade. Pode utilizar estas políticas com [acesso condicional](conditional-access.md) para permitir ou bloquear o acesso a recursos da organização. Também pode obter relatórios de dispositivos e agir relativamente a situações de não conformidade. 

Para saber mais sobre as políticas de conformidade, veja [Introdução à conformidade de dispositivos](device-compliance-get-started.md).

Este tópico indica as definições que pode utilizar numa política de conformidade para dispositivos Android.

## <a name="non-compliance-and-conditional-access"></a>Não conformidade e acesso condicional

A seguinte tabela descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

--------------------

|**Definição de política**| **Android 4.0 e posterior, Samsung Knox Standard 4.0 e posterior** |
| --- | ----|
| **Configuração do PIN ou da palavra-passe** |  Em quarentena |
| **Encriptação do dispositivo** | Em quarentena |
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | Em quarentena (não é uma definição) |
| **perfil de e-mail** | Não aplicável |
| **Versão mínima do SO** | Em quarentena |
| **Versão máxima do SO** |   Em quarentena |
| **Atestado do estado de funcionamento do Windows** | Não aplicável |

--------------------------

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. Por exemplo, forçar o utilizador a definir um PIN.

**Em quarentena** = O sistema operativo do dispositivo não impõe a conformidade. Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo. Quando o dispositivo não é conforme, são efetuadas as seguintes ações:

  - O dispositivo é bloqueado se uma política de acesso condicional se aplicar ao utilizador.
  - O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Em **Plataforma**, selecione **Android**. 
5. Selecione **Configurar Definições**. Introduza as definições **Estado de Funcionamento do Dispositivo**, **Propriedades do Dispositivo** e **Segurança do Sistema**, conforme descrito neste artigo.

## <a name="device-health"></a>Device health

- **Dispositivos com rooting**: selecione **Bloquear** para marcar dispositivos com rooting (com jailbreak) como não conformes. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Exigir que o dispositivo esteja ao Nível de Ameaça do Dispositivo ou abaixo do mesmo**: utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição de conformidade. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Para utilizar esta definição, selecione o nível de ameaça permitido:
  - **Protegido**: esta opção é a mais segura, uma vez que o dispositivo não pode ter qualquer ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixo**: o dispositivo é avaliado como em conformidade se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: o dispositivo será avaliado como estando em conformidade se as ameaças existentes forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Elevado**: esta opção é a menos segura e permite todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
- **Os Serviços do Google Play estão configurados**: **exige** que a aplicação de Serviços do Google Play esteja instalada e ativada. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Fornecedor de segurança atualizado**: **exige** que um fornecedor de segurança atualizado proteja um dispositivo contra vulnerabilidades conhecidas. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Análise de ameaça nas aplicações**: **exige** que a funcionalidade **Verificar Aplicações** do Android esteja ativada. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  > [!NOTE]
  > Na plataforma Android legada, esta funcionalidade é uma definição de conformidade. O Intune só consegue verificar se esta definição está ativada ao nível do dispositivo.

- **Atestado de dispositivo SafetyNet**: introduza o nível de [Atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que tem de ser cumprido. As opções são:
  - **Não configurado** (predefinição): a definição não é avaliada quanto à conformidade ou não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

## <a name="device-property-settings"></a>Definições de propriedade do dispositivo

- **Versão do SO mínima**: quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não estando em conformidade. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo e, em seguida, obter acesso aos recursos da empresa.
- **Versão do SO máxima**: quando um dispositivo utiliza uma versão do SO posterior à versão especificada na regra, o acesso aos recursos da empresa é bloqueado. É pedido ao utilizador para contactar o administrador de TI. Até uma regra ser alterada para permitir a versão do SO, este dispositivo não poderá aceder aos recursos da empresa.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear os dispositivos móveis**: **exige** que os utilizadores introduzam uma palavra-passe para poderem aceder aos dispositivos. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Comprimento mínimo da palavra-passe**: introduza o número mínimo de dígitos ou carateres que a palavra-passe do utilizador tem de ter.
- **Tipo de palavra-passe necessária**: escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e de outros carateres. As opções são:
  - **Dispositivo Predefinido**
  - **Biométrica de segurança baixa**
  - **Pelo menos, numérico** (predefinição)
  - **Complexo numérico**: os números repetidos ou consecutivos, tal como `1111` ou `1234`, não são permitidos.
  - **Pelo menos alfabética** 
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**

- **Máximo de minutos de inatividade antes de ser exigida a palavra-passe**: introduza o tempo de inatividade antes de o utilizador ter de reintroduzir a palavra-passe. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Expiração da palavra-passe (dias)**: selecione o número de dias antes de a palavra-passe expirar e de o utilizador ter de criar uma nova.
- **Número de palavras-passe anteriores para impedir a reutilização**: introduza o número de palavras-passe recentes que não podem ser utilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados num dispositivo** (Android 4.0 e superior ou KNOX 4.0 e superior): escolha **Exigir** a encriptação do armazenamento de dados nos dispositivos. Os dispositivos são encriptados quando seleciona a definição **Palavra-passe obrigatória para desbloquear os dispositivos móveis**. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: opte por **bloquear** os dispositivos que tenham a opção "Segurança > Origens Desconhecidas" ativada (Suportado pelo Android 4.0 – Android 7.X. Não suportado pelo Android 8.0 e posterior). Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, defina esta funcionalidade como **Bloquear** para ativar esta política de conformidade. 

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

- **Integridade de tempo de execução de aplicações do portal da empresa**: selecione **Exigir** para confirmar que a aplicação Portal da Empresa cumpre os seguintes requisitos:

  - Tem o ambiente de tempo de execução predefinido instalado
  - Está corretamente assinada
  - Não está no modo de depuração
  - Foi instalada a partir de uma origem conhecida

  Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

- **Bloquear a depuração de USB no dispositivo** (Android 4.2 ou posterior): selecione **Bloquear** para impedir que os dispositivos utilizem a funcionalidade de depuração USB. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Nível de correção de segurança mínimo** (Android 6.0 ou posterior): selecione o nível de correção de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data tem de ser introduzida no formato `YYYY-MM-DD`.
- **Aplicações restritas**: introduza o **Nome da aplicação** e o **ID do pacote de aplicação** para aplicações que devem ser restringidas. Selecione **Adicionar**. Um dispositivo com pelo menos uma aplicação restrita instalada é marcado como não conforme.

Quando terminar, selecione **OK** > **OK** para guardar as suas alterações.

## <a name="locations"></a>localizações

Na sua política, escolha uma das localizações existentes. Ainda não tem uma localização? [Utilizar Localizações (barreira de rede) no Intune](use-network-locations.md) fornece algumas orientações.

1. Selecione **Localizações**.
2. Na lista, verifique a sua localização e escolha **Selecionar**.
3. **Guarde** a política.

## <a name="actions-for-noncompliance"></a>Ações de não conformidade

Selecione **Ações para não conformidade**. A ação predefinida marca imediatamente o dispositivo como não conforme.

Pode alterar a agenda quando o dispositivo for marcado como não conforme, tal como após um dia. Também pode configurar uma segunda ação que envia um e-mail para o utilizador quando o dispositivo não estiver em conformidade.

O artigo [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) fornece mais informações, incluindo como criar um e-mail de notificação para os seus utilizadores.

Por exemplo, está a utilizar a funcionalidade Localizações e adiciona uma localização numa política de conformidade. A ação predefinida de não conformidade aplica-se quando selecionar pelo menos uma localização. Se o dispositivo não estiver ligado às localizações selecionadas, será imediatamente considerado não conforme. Pode dar aos seus utilizadores um período de tolerância, por exemplo um dia.

## <a name="scope-tags"></a>Scope tags (Etiquetas de âmbito)

As etiquetas de âmbito são uma ótima forma de atribuir políticas a grupos específicos, tal como Vendas, Engenharia, RH e assim sucessivamente. Pode adicionar etiquetas de âmbito a políticas de conformidade. Veja [Utilizar etiquetas de âmbito para filtrar políticas](scope-tags.md). 

## <a name="assign-user-groups"></a>Atribuir grupos de utilizadores

Depois de criar uma política, esta não fará nada até ser atribuída. Para atribuir a política: 

1. Escolha uma política configurada por si. As políticas existentes encontram-se em **Conformidade do dispositivo** > **Políticas**.
2. Escolha a política e, em seguida, **Atribuições**. Pode incluir ou excluir grupos de segurança do Azure Active Directory (AD).
3. Escolha **Grupos selecionados** para ver os grupos de segurança do Azure AD. Selecione os grupos de utilizadores aos quais pretende aplicar esta política e escolha **Guardar** para implementar a política aos utilizadores.

Aplicou a política aos utilizadores. Os dispositivos utilizados pelos utilizadores abrangidos pela política são avaliados quanto à conformidade.

## <a name="next-steps"></a>Passos Seguintes
[Automatizar o e-mail e adicionar ações para dispositivos não conformes](actions-for-noncompliance.md)  
[Monitorizar as políticas de conformidade do Dispositivo do Intune](compliance-policy-monitor.md)  
[Definições de política de conformidade para Android Enterprise](compliance-policy-create-android-for-work.md)
