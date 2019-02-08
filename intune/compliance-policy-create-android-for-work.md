---
title: Criar uma política de conformidade do Android Enterprise no Microsoft Intune – Azure | Microsoft Docs
description: Crie ou configure uma política de conformidade de dispositivos do Microsoft Intune para dispositivos Android Enterprise ou com perfil de trabalho. Opte por permitir dispositivos com jailbreak, defina o nível de ameaça aceitável, verifique o Google Play, introduza a versão do sistema operativo mínima e máxima, escolha os seus requisitos de palavra-passe e permita aplicações de sideload.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 12/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: 9da89713-6306-4468-b211-57cfb4b51cc6
ms.reviewer: muhosabe
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1d29399b4aaecbee06118e2331c1f0911d7c8caa
ms.sourcegitcommit: 727c3ae7659ad79ea162250d234d7730f840c731
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/07/2019
ms.locfileid: "55842478"
---
# <a name="add-a-device-compliance-policy-for-android-enterprise-devices-in-intune"></a>Adicionar uma política de conformidade para dispositivos Android Enterprise no Intune

As políticas de conformidade de dispositivos são um elemento fundamental ao utilizar o Intune para proteger os recursos da sua organização. No Intune, pode criar regras e definições que os dispositivos têm de cumprir para serem considerados como estando em conformidade, como o comprimento da palavra-passe. Se o dispositivo não estiver em conformidade, pode bloquear o acesso aos dados e recursos através do [acesso condicional](conditional-access.md). 

Também pode obter relatórios de dispositivo e tomar medidas quanto à não conformidade, tais como enviar um e-mail de notificação para o utilizador. Para saber mais sobre as políticas de conformidade, veja [Introdução à conformidade de dispositivos](device-compliance-get-started.md).

Este artigo indica as definições que pode utilizar numa política de conformidade para dispositivos Android Enterprise.

## <a name="non-compliance-and-conditional-access"></a>Não conformidade e acesso condicional

A seguinte tabela descreve como as definições não conformes são geridas quando uma política de conformidade é utilizada com uma política de acesso condicional.

--------------------------

|**definição de política**| **Perfil do Android Enterprise** |
| --- | --- |
| **Configuração do PIN ou da palavra-passe** |  Em quarentena |
| **Encriptação do dispositivo** |  Em quarentena |
| **Dispositivo desbloqueado por jailbreak ou obtenção de controlo de raiz** | Em quarentena (não é uma definição) |
| **perfil de e-mail** | Não aplicável |
| **Versão mínima do SO** | Em quarentena |
| **Versão máxima do SO** | Em quarentena |
| **Atestado do estado de funcionamento do Windows** |Não aplicável |

**Remediado** = O sistema operativo do dispositivo impõe a conformidade. Por exemplo, forçar o utilizador a definir um PIN.

**Em quarentena** = O sistema operativo do dispositivo não impõe a conformidade. Por exemplo, os dispositivos Android não forçam o utilizador a encriptar o dispositivo. Quando o dispositivo não é conforme, são realizadas as seguintes ações:

  - Se uma política de acesso condicional se aplicar ao utilizador, o dispositivo é bloqueado.
  - O portal da empresa notifica o utilizador sobre eventuais problemas de conformidade.

## <a name="create-a-device-compliance-policy"></a>Criar uma política de conformidade de dispositivo

[!INCLUDE [new-device-compliance-policy](./includes/new-device-compliance-policy.md)]
4. Em **Plataforma**, selecione **Android Enterprise**. 
5. Selecione **Configurar Definições**. Introduza as definições **Estado de Funcionamento do Dispositivo**, **Propriedades do Dispositivo** e **Segurança do Sistema**, conforme descrito neste artigo.

## <a name="device-health"></a>Device health

- **Dispositivos com jailbreak**: Escolher **bloco** para marcar os dispositivos com root (com jailbreak) como não conforme. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Exigir o dispositivo esteja ao nível ou abaixo do nível de ameaça do dispositivo**: Utilize esta definição para assumir a avaliação de riscos da solução Lookout MTP como uma condição para conformidade. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Para utilizar esta definição, selecione o nível de ameaça permitido:
  - **Protegido**: Esta opção é a mais segura e significa que o dispositivo não pode ter qualquer ameaça. Se forem detetadas ameaças de qualquer nível no dispositivo, o mesmo será avaliado como não conforme.
  - **Baixa**: O dispositivo é avaliado como conforme se só estiverem presentes ameaças de nível baixo. Qualquer nível mais alto coloca o dispositivo num estado de não conforme.
  - **Médio**: O dispositivo é avaliado como conforme se as ameaças que estão presentes no dispositivo forem de nível baixo ou médio. Se forem detetadas ameaças de nível alto no dispositivo, este será determinado como não conforme.
  - **Alta**: Esta opção é menos segura, já que permite a todos os níveis de ameaça. Poderá ser útil se utilizar esta solução apenas para fins de relatórios.
- **Serviços do Google Play está configurado**: **Exigir** que o Google Play dos serviços de aplicação é instalada e ativada. Os serviços do Google Play permitem realizar atualizações de segurança, que são uma dependência de nível base de várias funcionalidades de segurança dos dispositivos Google certificados. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Fornecedor de segurança atualizado**: **Exigir** que um fornecedor de segurança atualizado Proteja um dispositivo contra vulnerabilidades conhecidas. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Dispositivo safetynet**: Introduza o nível de [atestado de SafetyNet](https://developer.android.com/training/safetynet/attestation.html) que têm de ser cumpridos. As opções são:
  - **Não configurado** (predefinição): Não é avaliada a definição de conformidade ou de não conformidade.
  - **Verificação de integridade básica**
  - **Verificação de integridade básica e de dispositivos certificados**

#### <a name="threat-scan-on-apps"></a>Análise de ameaças nas aplicações

Em dispositivos Android Enterprise, a definição **Análise de ameaça em aplicações** é uma política de configuração. Veja [Definições de restrição de dispositivos Android Enterprise](device-restrictions-android-for-work.md).

## <a name="device-properties-settings"></a>Definições de propriedades do dispositivo

- **Versão mínima do SO**: Quando um dispositivo não cumpre o requisito de versão mínima do SO, será comunicado como não conforme. É apresentada uma ligação com informações sobre como atualizar. O utilizador final pode optar por atualizar o dispositivo para, em seguida, poder aceder aos recursos da empresa.
- **Versão do SO máxima**: Quando um dispositivo utiliza uma versão do SO posterior à versão na regra, o acesso aos recursos da empresa é bloqueado. Além disso, é pedido ao utilizador para contactar o administrador de TI. Até uma regra ser alterada para permitir a versão do SO, este dispositivo não poderá aceder aos recursos da empresa.

## <a name="system-security-settings"></a>Definições de segurança do sistema

### <a name="password"></a>Palavra-passe

- **Exigir uma palavra-passe para desbloquear dispositivos móveis**: **Exigir** que os utilizadores introduzam uma palavra-passe antes de poderem aceder ao respetivo dispositivo. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. Esta definição é aplicada ao nível do dispositivo. Se só precisa de exigir uma palavra-passe no nível de perfil de trabalho, em seguida, utilize uma política de configuração. Ver [definições de configuração de dispositivos Android Enterprise](device-restrictions-android-for-work.md).
- **Comprimento mínimo da palavra-passe**: Introduza o número mínimo de dígitos ou carateres de que palavra-passe do utilizador tem de ter.
- **Tipo de palavra-passe obrigatório**: Escolha se uma palavra-passe deve incluir apenas carateres numéricos ou uma combinação de números e outros caracteres. As opções são:
  - **Dispositivo Predefinido**
  - **Biométrica de segurança baixa**
  - **Pelo menos, numérico** (predefinição)
  - **Complexo numérico**
  - **Pelo menos alfabética**
  - **Pelo menos alfanumérica**
  - **Pelo menos alfanumérica com símbolos**

- **Máximo de minutos de inatividade antes da palavra-passe é necessária**: Introduza o tempo de inatividade antes do utilizador ter de reintroduzir a palavra-passe. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.
- **Expiração de palavra-passe (dias)**: Selecione o número de dias antes da palavra-passe expirar e ser necessário criar um novo.
- **Número de palavras-passe anteriores cuja reutilização está**: Introduza o número de palavras-passe recentes que não podem ser reutilizadas. Utilize esta definição para impedir o utilizador final de criar palavras-passe utilizadas anteriormente.

### <a name="encryption"></a>Encriptação

- **Encriptação do armazenamento de dados no dispositivo de**: Escolher **requerem** para encriptar o armazenamento de dados nos seus dispositivos. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade. 

  Uma vez que os dispositivos com perfil de trabalho do Android impõem a encriptação, não tem de configurar esta definição.

### <a name="device-security"></a>Segurança do Dispositivo

- **Bloquear aplicações de origens desconhecidas**: Optar por **bloco** dispositivos com o "Segurança > origens desconhecidas" ativada origens (suportadas no Android 4.0 – Android 7.x; não suportadas pelo Android 8.0 e posteriores). Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Para aplicações de sideload, as origens desconhecidas têm de ser permitidas. Se não tiver aplicações Android de sideload, defina esta funcionalidade como **Bloquear** para ativar esta política de conformidade. 

  > [!IMPORTANT]
  > As aplicações de sideload requerem a ativação da definição **Bloquear aplicações de origens desconhecidas**. Aplique esta política de conformidade apenas se não tiver aplicações Android de sideload nos dispositivos.

  Uma vez que os dispositivos com perfil de trabalho do Android restringem sempre a instalação de origens desconhecidas, não tem de configurar esta definição.

- **Integridade de tempo de execução da aplicação do portal da empresa**: Escolher **requerem** para confirmar o Portal da empresa a aplicação cumpre os seguintes requisitos:

  - Tem o ambiente de tempo de execução predefinido instalado
  - Está corretamente assinada
  - Não está no modo de depuração
  - Foi instalada a partir de uma origem conhecida

  Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

- **Depuração de USB de bloco no dispositivo**: Escolher **bloco** para impedir que os dispositivos a utilizar a funcionalidade de depuração de USB. Quando seleciona **Não configurado** (predefinição), esta definição não é avaliada quanto à conformidade ou não conformidade.

  Uma vez que a depuração USB já está desativada em dispositivos com perfil de trabalho do Android, não tem de configurar esta definição.

- **Nível de patch de segurança mínimo**: Selecione o nível de patch de segurança mais antigo que um dispositivo pode ter. Os dispositivos que não tiverem pelo menos este nível de correção serão considerados como não conformes. A data tem de ser introduzida no formato *AAAA-MM-DD*.

Quando terminar, selecione **OK** > **OK** para guardar as suas alterações.

## <a name="actions-for-noncompliance"></a>Ações de não conformidade

Selecione **Ações para não conformidade**. A ação predefinida marca imediatamente o dispositivo como não conforme.

Pode alterar a agenda quando o dispositivo for marcado como não conforme, tal como após um dia. Também pode configurar uma segunda ação que envia um e-mail para o utilizador quando o dispositivo não estiver em conformidade.

O artigo [Adicionar ações para dispositivos não conformes](actions-for-noncompliance.md) fornece mais informações, incluindo como criar um e-mail de notificação para os seus utilizadores.

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
[Definições de políticas de conformidade para Android](compliance-policy-create-android.md)
