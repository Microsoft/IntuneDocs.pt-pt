---
title: Resolver problemas com políticas no Microsoft Intune – Azure | Microsoft Docs
description: Veja como usar a funcionalidade de resolução de problemas incorporada, e leia sobre problemas ou problemas comuns e suas resoluções ao usar políticas de conformidade e perfis de configuração no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 02/18/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: configuration
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9acb934cdf67aae9c18091a0340f27de635b5399
ms.sourcegitcommit: c780e9988341a20f94fdeb8672bd13e0b302da93
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77511022"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>Políticas e perfis de resolução de problemas e em Intune

O Microsoft Intune inclui algumas funcionalidades de resolução de problemas incorporadas. Utilize estas funcionalidades para ajudar a resolver as políticas de conformidade e perfis de configuração no seu ambiente.

Este artigo lista algumas técnicas comuns de resolução de problemas, e descreve alguns problemas que pode experimentar.

## <a name="check-tenant-status"></a>Verifique o estado do inquilino

Verifique o [Estado do Inquilino](../fundamentals/tenant-status.md) e confirme que a subscrição está Ativa. Também pode visualizar detalhes para incidentes ativos e avisos que possam afetar a sua política ou implementação de perfis.

## <a name="use-built-in-troubleshooting"></a>Use resolução de problemas incorporado

1. No centro de administração do [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)selecione **Troubleshooting + suporte**:

    ![Intune, vá para Ajuda e Suporte, e selecione Troubleshoot](./media/troubleshoot-policies-in-microsoft-intune/help-and-support-troubleshoot.png)

2. Escolha **Selecione Selecione Utilizador** > selecione o utilizador com um problema > **Selecione**.
3. Confirme que a **Licença Intune** e **o Status da Conta** mostram ambos cheques verdes:

    ![Intune, selecione o utilizador e confirme o estado da conta e a licença Intune mostrar marcas de verificações verdes para o estado](./media/troubleshoot-policies-in-microsoft-intune/account-status-intune-license-show-green.png)

    **Links úteis:**

    - [Atribuir licenças para que os utilizadores possam inscrever dispositivos](../fundamentals/licenses-assign.md)
    - [Adicionar utilizadores ao Intune](../fundamentals/users-add.md)

4. No âmbito **do Dispositivo,** encontre o dispositivo com problemas. Reveja as diferentes colunas:

    - **Gerido**: Para que um dispositivo receba políticas de conformidade ou configuração, esta propriedade deve mostrar **MDM** ou **EAS/MDM**.

        - Se **managed** não está definido para **MDM** ou **EAS/MDM,** então o dispositivo não está matriculado. Não recebe políticas de conformidade ou configuração até estar matriculada.

        - As políticas de proteção de aplicações (gestão de aplicações móveis) não requerem que os dispositivos sejam matriculados. Para mais informações, consulte criar e atribuir políticas de proteção de [aplicações.](../apps/app-protection-policies.md)

    - **Tipo de adesão do Azure AD:** Deve ser definido para **o local** de trabalho ou **azureAd**.
 
        - Se esta coluna não estiver **registada,** pode haver um problema com a inscrição. Normalmente, não inscrever e reinscrever o dispositivo resolve este estado.

    - **Intune compliant**: Deve ser **Sim**. Se **não** for mostrado, pode haver um problema com as políticas de conformidade, ou o dispositivo não está ligado ao serviço Intune. Por exemplo, o dispositivo pode ser desligado ou pode não ter uma ligação de rede. Eventualmente, o dispositivo torna-se incompatível, possivelmente após 30 dias.

        Para mais informações, consulte iniciar as [políticas de conformidade do dispositivo.](../protect/device-compliance-get-started.md)

    - Conformidade com a **AD Azure:** Deve ser **Sim**. Se **não** for mostrado, pode haver um problema com as políticas de conformidade, ou o dispositivo não está ligado ao serviço Intune. Por exemplo, o dispositivo pode ser desligado ou pode não ter uma ligação de rede. Eventualmente, o dispositivo torna-se incompatível, possivelmente após 30 dias.

        Para mais informações, consulte iniciar as [políticas de conformidade do dispositivo.](../protect/device-compliance-get-started.md)

    - **Última verificação**: Deve ser uma hora e data recentes. Por predefinição, os dispositivos Intune check-in a cada 8 horas.

        - Se **o último check-in** for superior a 24 horas, pode haver um problema com o dispositivo. Um dispositivo que não pode fazer o check-in não pode receber as suas políticas de Intune.

        - Para forçar o check-in:
            - No dispositivo Android, abra a app Portal da Empresa > **Dispositivos** > Escolha o dispositivo a partir da lista > **Verifique as definições**do dispositivo .
            - No dispositivo iOS/iPadOS, abra a aplicação portal da Empresa > **Dispositivos** > Escolha o dispositivo a partir da lista > **Verifique as definições**.

        - Num dispositivo Windows, abra **Definições** > **Contas** > Trabalho de **Acesso ou Escola** > Selecione a conta ou inscrição de MDM > **Info** > **Sync**.

    - Selecione o dispositivo para ver informações específicas da política.

        **A Conformidade do Dispositivo** mostra os estados das políticas de conformidade atribuídas ao dispositivo.

        **A configuração** do dispositivo mostra os estados das políticas de configuração atribuídas ao dispositivo.

        Se as políticas esperadas não forem mostradas no âmbito da conformidade do **dispositivo** ou **da configuração**do dispositivo, então as políticas não são corretamente direcionadas. Abra a apólice e atribua a política a este utilizador ou dispositivo.

        **Os estados políticos:**

        - **Não Aplicável**: Esta política não é suportada nesta plataforma. Por exemplo, as políticas iOS/iPadOS não funcionam no Android. As políticas da Samsung KNOX não funcionam em dispositivos Windows.
        - **Conflito**: Existe uma configuração existente no dispositivo que Intune não pode sobrepor. Ou implementou duas políticas com a mesma configuração usando valores diferentes.
        - **Pendente**: O dispositivo não fez check-in em Intune para obter a apólice. Ou o dispositivo recebeu a apólice, mas não comunicou o estado ao Intune.
        - **Erros**: Procure erros e possíveis resoluções em problemas de [acesso a recursos da empresa Troubleshoot](../fundamentals/troubleshoot-company-resource-access-problems.md).

        **Links úteis:** 

        - [Formas de implementar políticas de conformidade de dispositivos](../protect/device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
        - [Monitorizar as políticas de conformidade de dispositivos](../protect/compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>Não tem a certeza se um perfil é corretamente aplicado

1. Inscreva-se no centro de administração do [Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **Dispositivos** > **Todos os dispositivos** > selecione a **configuração**do dispositivo > dispositivo . 

    Todos os dispositivos listam os seus perfis. Cada perfil tem um **Status**. O estado aplica-se quando todos os perfis atribuídos, incluindo restrições e requisitos de hardware e SO, são considerados em conjunto. Os estatutos possíveis incluem:

    - **Conformidades**: O dispositivo recebeu o perfil e informa ao Intune que está em conformidade com a definição.

    - **Não aplicável**: A definição de perfil não é aplicável. Por exemplo, as definições de e-mail para dispositivos iOS/iPadOS não se aplicam a um dispositivo Android.

    - **Pendente**: O perfil é enviado para o dispositivo, mas não reportou o estado a Intune. Por exemplo, a encriptação no Android requer que o utilizador final ative a encriptação e, por isso, poderá estar pendente.

**Link útil**: [Monitor de configuração perfis de dispositivos](../configuration/device-profile-monitor.md)

> [!NOTE]
> Quando duas políticas com diferentes níveis de restrição se aplicam ao mesmo dispositivo ou utilizador, é aplicada a política mais restrita.

## <a name="policy-troubleshooting-resources"></a>Recursos de resolução de problemas políticos

- Políticas de [resolução de problemas iOS/iPadOS ou Android que não se aplicam a dispositivos](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-tip-Troubleshooting-iOS-or-Android-policies-not-applying/ba-p/280154) (abre outro site da Microsoft)
- [Resolução de problemas Windows 10 Falhas políticas intune](https://blogs.technet.microsoft.com/configmgrdogs/2018/08/09/troubleshooting-windows-10-intune-policy-failures/) (abre um blog)
- [Definições personalizadas de CSP de resolução de problemas para windows 10](https://support.microsoft.com/en-us/help/4055338/troubleshoot-csp-setting-windows-10-computer-intune) (abre outro site da Microsoft)
- [Política de Grupo Windows 10 vs Intune MDM (abre](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/) outro site da Microsoft)

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Alerta: Falha ao Guardar as Regras de Acesso no Exchange

**Problema**: Recebe o alerta **Falha ao Guardar as Regras de Acesso no Exchange**  na consola de administração.

Se criar políticas no espaço de trabalho da Política Exchange On-Premises (consola Admin), mas estiver a utilizar o Office 365, então as definições de política configuradas não são aplicadas pela Intune. No alerta, note a fonte política. No âmbito do espaço de trabalho de política exchange on-local, apague as regras do legado. As regras do legado são as regras da Global Exchange no Intune para a Exchange no local, e não são relevantes para o Office 365. Depois, crie uma nova política para o Office 365.

[Problemas de resolução do conector intune on-premises Exchange](../protect/troubleshoot-exchange-connector.md) pode ser um bom recurso.

## <a name="cant-change-security-policies-for-enrolled-devices"></a>Não pode mudar as políticas de segurança para dispositivos matriculados

Os dispositivos Windows Phone não permitem que as políticas de segurança definidas utilizando MDM ou EAS sejam reduzidas em segurança depois de as configurar. Por exemplo, você define um **número mínimo de senha de caracteres** para 8, e depois tenta reduzi-lo para 4. A política mais restritiva é aplicada ao dispositivo.

Os dispositivos Windows 10 não podem remover as políticas de segurança quando desalestá a apólice (parar a implementação). Pode ter de deixar a apólice atribuída e, em seguida, alterar as definições de segurança de volta para os valores predefinidos.

Dependendo da plataforma do dispositivo, se quiser alterar a apólice para um valor menos seguro, poderá ter de redefinir as políticas de segurança.

Por exemplo, no Windows 8.1, no ambiente de trabalho, passe pela direita para abrir a barra **de Charms.** Escolha **definições** > **Painel de Controlo** > Contas de **utilizador**. No lado esquerdo, selecione a ligação **Repor Políticas de Segurança** e escolha **Repor Políticas**.

Outras plataformas, como o Android, iOS/iPadOS e Windows Phone 8.1, poderão ter de ser reformadas e reinscritas para aplicar uma política menos restritiva.

[A inscrição do dispositivo de resolução de problemas](../enrollment/troubleshoot-device-enrollment-in-intune.md) pode ser um bom recurso.

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>PCs usando o cliente de software Intune - portal clássico

> [!NOTE]
> Esta secção aplica-se ao portal clássico. 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Erros relacionados com a política do Microsoft Intune no policyplatform.log

No caso dos PCs do Windows geridos com o cliente do software Intune, os erros de política no ficheiro `policyplatform.log` podem ser provenientes de definições não predefinidas no Controlo de Conta do Utilizador do Windows (UAC) no dispositivo. Algumas definições de UAC não predefinidas podem afetar as instalações de cliente do Microsoft Intune e a execução de políticas.

#### <a name="resolve-uac-issues"></a>Resolver problemas de UAC

1. Extinga o computador. Veja [Remover dispositivos](../remote-actions/devices-wipe.md).

2. Aguarde 20 minutos para que o software de cliente seja removido.

    > [!NOTE]
    > Não tente remover o cliente nos Programas e Funcionalidades.

3. No menu inicial, digite **uAC** para abrir as definições de Controlo de Conta do Utilizador.

4. Desloque o slider de notificação para a definição predefinida.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>ERRO: Não é possível obter o valor do computador, 0x80041013

Ocorre se a hora no sistema local estiver dessincronizada em cinco minutos ou mais. Se o tempo no computador local estiver dessincronizado, as transações seguras falham porque os selos de tempo são inválidos.

Para resolver esta questão, coloque o tempo do sistema local o mais próximo possível do tempo de Internet. Ou, definir para o tempo nos controladores de domínio na rede.

## <a name="next-steps"></a>Próximos passos

[Questões e resoluções comuns com perfis de e-mail](../configuration/troubleshoot-email-profiles-in-microsoft-intune.md)

Obtenha [ajuda de suporte da Microsoft](../fundamentals/get-support.md), ou use os [fóruns comunitários](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
