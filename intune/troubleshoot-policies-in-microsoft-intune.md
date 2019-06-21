---
title: Resolver problemas com políticas no Microsoft Intune – Azure | Microsoft Docs
description: Veja como utilizar a funcionalidade de resolução de problemas internos e leia sobre os problemas mais comuns ou problemas e resolução ao utilizar políticas de conformidade e perfis de configuração no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2019
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: 99fb6db6-21c5-46cd-980d-50f063ab8ab8
ROBOTS: ''
ms.reviewer: tscott
ms.suite: ems
search.appverid: MET150
ms.custom: intune-classic
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9314617640d0bfd7f3a7b0cd0ba572e99ede53f9
ms.sourcegitcommit: cd451ac487c7ace18ac9722a28b9facfba41f6d3
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298406"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>Resolver problemas de políticas e perfis e no Intune

O Microsoft Intune inclui alguns recursos internos de resolução de problemas. Utilize estas funcionalidades para ajudar a resolver problemas de políticas de conformidade e perfis de configuração no seu ambiente.

Este artigo apresenta uma lista de algumas técnicas de resolução de problemas comuns e descreve alguns problemas que poderá experienciar.

## <a name="check-tenant-status"></a>Verificar o estado do inquilino
Verifique os [estado do inquilino](tenant-status.md) e confirme a subscrição está ativa. Também pode ver detalhes de incidentes activos e aconselhamentos sobre o que pode afetar a implementação de políticas ou perfis.

## <a name="use-built-in-troubleshooting"></a>Utilizar a resolução de problemas interna

1. Na [Intune](https://go.microsoft.com/fwlink/?linkid=2090973), selecione **resolução de problemas**:

    ![No Intune, aceda a ajuda e suporte e selecione a resolução de problemas](./media/help-and-support-troubleshoot.png)

2. Escolher **selecionar utilizador** > selecione o utilizador tenha um problema > **selecione**.
3. Confirme que **licença do Intune** e **estado da conta** ambos mostram verificações verde:

    ![No Intune, selecione o utilizador e confirme o estado da conta e a licença do Intune mostram marcas de verificações de verde para o Estado](./media/account-status-intune-license-show-green.png)

    **Ligações úteis**:

    - [Atribuir licenças para que os utilizadores podem inscrever dispositivos](licenses-assign.md)
    - [Adicionar utilizadores ao Intune](users-add.md)

4. Sob **dispositivos**, localizá-lo a ter um problema. Reveja as colunas diferentes:

    - **Gerido**: Para o dispositivo receber políticas de conformidade ou de configuração, esta propriedade deve mostrar **MDM** ou **EAS/MDM**.

      - Se **gerida** não estiver definida como **MDM** ou **EAS/MDM**, em seguida, o dispositivo não estiver inscrito. Ele não recebe políticas de conformidade ou de configuração até estar inscrito.

      - Políticas de proteção de aplicações (gestão de aplicações móveis) não exigem que os dispositivos sejam inscritos. Para obter mais informações, consulte [criar e atribuir políticas de proteção de aplicações](app-protection-policies.md).

    - **Tipo de associação do Azure AD**: Deve ser definido como **à área de trabalho** ou **AzureAD**.
 
      - Se esta coluna é **não registado**, poderá existir um problema com a inscrição. Normalmente, anular a inscrição e reinscrição do dispositivo resolve esse Estado.

    - **Conformidade com o Intune**: Deve estar **Sim**. Se **não** seja apresentado, pode haver um problema com as políticas de conformidade ou o dispositivo não está a ligar ao serviço Intune. Por exemplo, o dispositivo pode ser desativado ou pode não ter uma ligação de rede. Eventualmente, o dispositivo ficará não conforme, possivelmente após 30 dias.

      Para obter mais informações, consulte [introdução às políticas de conformidade de dispositivo](device-compliance-get-started.md).

    - **O Azure AD em conformidade**: Deve estar **Sim**. Se **não** seja apresentado, pode haver um problema com as políticas de conformidade ou o dispositivo não está a ligar ao serviço Intune. Por exemplo, o dispositivo pode ser desativado ou pode não ter uma ligação de rede. Eventualmente, o dispositivo ficará não conforme, possivelmente após 30 dias.

      Para obter mais informações, consulte [introdução às políticas de conformidade de dispositivo](device-compliance-get-started.md).

    - **Última check-in**: Deve ser uma hora e data recentes. Por predefinição, a verificação de dispositivos do Intune a cada 8 horas.

      - Se **última check-in** é a mais de 24 horas, poderá existir um problema com o dispositivo. Um dispositivo que não é possível não consegue receber as políticas do Intune.

      - Para forçar a entrada:
        - No dispositivo Android, abra a aplicação Portal da empresa > **dispositivos** > selecione o dispositivo na lista > **verificar definições de dispositivo**.
        - No dispositivo iOS, abra a aplicação do portal da empresa > **dispositivos** > selecione o dispositivo na lista > **verificar definições**. 
        - Num dispositivo Windows, abra **configurações** > **contas** > **acesso profissional ou escolar** > selecione a conta ou a inscrição MDM >  **Info** > **sincronização**.

    - Selecione o dispositivo para ver informações específicas de política.

      **Conformidade do dispositivo** mostra os Estados de políticas de conformidade atribuídas ao dispositivo.

      **Configuração do dispositivo** mostra os Estados de políticas de configuração atribuídos ao dispositivo.

      Se as políticas esperadas não são apresentadas sob **conformidade do dispositivo** ou **configuração do dispositivo**, em seguida, as políticas não são visadas corretamente. Abra a política e atribuir a política para este utilizador ou dispositivo.

      **Estados da política de**:

      - **Não aplicável**: Esta política não é suportada nesta plataforma. Por exemplo, as políticas de iOS não funcionam no Android. As políticas do Samsung KNOX não funcionam em dispositivos Windows.
      - **Conflito**: Existe uma configuração existente no dispositivo que não é possível substituir o Intune. Em alternativa, implementou duas políticas com a mesma definição a utilizar valores diferentes.
      - **Pendente**: O dispositivo ainda não verificado no Intune para obter a política. Em alternativa, o dispositivo recebeu a política, mas ainda não comunicou o estado para o Intune.
      - **Erros**: Pesquisar erros e possíveis resoluções na [resolução de problemas de acesso de recursos da empresa](troubleshoot-company-resource-access-problems.md).

      **Ligações úteis**: 

      - [Formas de implementar políticas de conformidade do dispositivo](device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
      - [Monitorizar as políticas de conformidade de dispositivos](compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>Certeza se um perfil é aplicado corretamente

1. Inicie sessão no [Intune](https://go.microsoft.com/fwlink/?linkid=2090973).
2. Selecione **dispositivos** > **todos os dispositivos** > selecione o dispositivo > **configuração do dispositivo**. 

    Todos os dispositivos apresenta uma lista de seus perfis. Cada perfil tem um **estado**. O estado aplica-se quando todos os perfis atribuídos, incluindo requisitos de hardware e restrições do sistema operacional e, são considerados em conjunto. Estados possíveis incluem:

    - **Está em conformidade com**: O dispositivo recebeu o perfil e os relatórios para o Intune está em conformidade com a definição.

    - **Não aplicável**: A definição de perfil não é aplicável. Por exemplo, as definições de e-mail para dispositivos iOS não se aplicam num dispositivo Android.

    - **Pendente**: O perfil é enviado para o dispositivo, mas ainda não comunicou o estado para o Intune. Por exemplo, a encriptação no Android requer que o utilizador final ative a encriptação e, por isso, poderá estar pendente.

**Ligação útil**: [Monitorizar perfis de configuração de dispositivo](device-profile-monitor.md)

> [!NOTE]
> Quando duas políticas com diferentes níveis de restrição se aplicam ao mesmo dispositivo ou utilizador, é aplicada a política mais restrita.

## <a name="policy-troubleshooting-resources"></a>Recursos de resolução de problemas de política

- [Resolução de problemas do iOS ou Android políticas não aplicar a dispositivos](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-tip-Troubleshooting-iOS-or-Android-policies-not-applying/ba-p/280154) (abre o outro site da Microsoft)
- [Resolução de problemas de falhas de política do Intune do Windows 10](http://configmgrdogsarchive.com/2018/08/09/troubleshooting-windows-10-intune-policy-failures/) (abre um blog)
- [Resolver problemas relacionados com definições personalizadas do CSP para Windows 10](https://support.microsoft.com/en-us/help/4055338/troubleshoot-csp-setting-windows-10-computer-intune) (abre o outro site da Microsoft)
- [Política de grupo do Windows 10 vs MDM do Intune política](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/) (abre o outro site da Microsoft)

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Alerta: Falha ao guardar de regras de acesso ao Exchange

**Problema**: Recebe o alerta **Falha ao guardar as regras de acesso ao Exchange** na consola de administração.

Se criar políticas na área de trabalho de política do Exchange no local (Consola de administração), mas se estiver a utilizar o Office 365, em seguida, as definições de política configuradas não são impostas pelo Intune. No alerta, tenha em atenção a origem da política. Na área de trabalho política do Exchange no local, elimine as regras legadas. As regras legadas são regras globais do Exchange no Intune para o Exchange no local e não são relevantes para o Office 365. Em seguida, crie nova política para o Office 365.

[Resolver problemas relacionados com o Exchange connector do Intune no local](troubleshoot-exchange-connector.md) pode ser um bom recurso.

## <a name="cant-change-security-policies-for-enrolled-devices"></a>Não é possível alterar as políticas de segurança para dispositivos inscritos

Dispositivos Windows Phone não permitem políticas de segurança definidas através de MDM ou EAS sejam reduzidas em termos segurança assim que tiver configurado-los. Por exemplo, define um **número mínimo de palavra-passe de caráter** para 8 e, em seguida, tente reduzir para 4. A política mais restritiva é aplicada ao dispositivo.

Dispositivos Windows 10 não podem remover as políticas de segurança quando anular a atribuição de política (parar implementação). Poderá deixar a política atribuída e, em seguida, altere as definições de segurança para os valores predefinidos.

Consoante a plataforma de dispositivo, se pretender alterar a política para um valor menos seguro, poderá ter de repor as políticas de segurança.

Por exemplo, no Windows 8.1, na área de trabalho, percorra a partir da direita para abrir o **atalhos** barra. Escolher **configurações** > **painel de controlo** > **contas de utilizador**. No lado esquerdo, selecione a ligação **Repor Políticas de Segurança** e escolha **Repor Políticas**.

Outras plataformas, tal como Android, iOS e Windows Phone 8.1, poderão ter de ser extintos e reinscritos para aplicar uma política menos restritiva.

[Resolver problemas de inscrição de dispositivo](troubleshoot-device-enrollment-in-intune.md) pode ser um bom recurso.

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>PCs com o cliente de software do Intune - portal clássico

> [!NOTE]
> Esta secção aplica-se para o portal clássico. 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Erros relacionados com políticas do Microsoft Intune no policyplatform.log

Para PCs Windows geridos com o cliente de software do Intune, erros de políticas no `policyplatform.log` ficheiro poderá estar a partir das definições de não-padrão controle de conta de utilizador no Windows (UAC) no dispositivo. Algumas definições de UAC não predefinidas podem afetar as instalações de cliente do Microsoft Intune e a execução de políticas.

#### <a name="resolve-uac-issues"></a>Resolver problemas de UAC

1. Extinga o computador. Veja [Remover dispositivos](devices-wipe.md).

2. Aguarde 20 minutos para que o software de cliente seja removido.

    > [!NOTE]
    > Não tente remover o cliente nos Programas e Funcionalidades.

3. No menu Iniciar, escreva **UAC** para abrir as definições de controlo de conta de utilizador.

4. Mova o controlo de deslize de notificação para a configuração padrão.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>ERRO: Não é possível obter o valor do computador, 0x80041013

Ocorre se a hora no sistema local estiver dessincronizada em cinco minutos ou mais. Se a hora no computador local estiver dessincronizada, as transações seguras falharem porque os carimbos de data / hora é inválidos.

Para resolver este problema, defina a hora do sistema local mais próximo possível hora da Internet. Em alternativa, defina-o como o tempo nos controladores de domínio na rede.


## <a name="next-steps"></a>Passos Seguintes

[Problemas comuns e resoluções com perfis de e-mail](troubleshoot-email-profiles-in-microsoft-intune.md)

Obtenha [suportam a ajuda da Microsoft](get-support.md), ou utilize o [fóruns da Comunidade](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
