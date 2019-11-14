---
title: Resolver problemas com políticas no Microsoft Intune – Azure | Microsoft Docs
description: Veja como usar o recurso interno de solução de problemas e leia sobre problemas comuns ou problemas e suas resoluções ao usar políticas de conformidade e perfis de configuração no Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/05/2019
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
ms.openlocfilehash: a8768022872d32116add0ed4ea4caf1f8fcb800f
ms.sourcegitcommit: 78cebd3571fed72a3a99e9d33770ef3d932ae8ca
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 11/13/2019
ms.locfileid: "74059277"
---
# <a name="troubleshoot-policies-and-profiles-and-in-intune"></a>Solucionar problemas de políticas e perfis e no Intune

Microsoft Intune inclui alguns recursos internos de solução de problemas. Use esses recursos para ajudar a solucionar problemas de políticas de conformidade e perfis de configuração em seu ambiente.

Este artigo lista algumas técnicas comuns de solução de problemas e descreve alguns problemas que podem ocorrer.

## <a name="check-tenant-status"></a>Verificar status do locatário

Verifique o [status do locatário](../fundamentals/tenant-status.md) e confirme se a assinatura está ativa. Você também pode exibir detalhes de incidentes e avisos ativos que podem afetar sua política ou implantação de perfil.

## <a name="use-built-in-troubleshooting"></a>Usar a solução de problemas interna

1. No [centro de administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selecione **solução de problemas + suporte**:

    ![No Intune, acesse ajuda e suporte e selecione solucionar problemas](./media/troubleshoot-policies-in-microsoft-intune/help-and-support-troubleshoot.png)

2. Escolha **Selecionar usuário** > selecione o usuário que está tendo um problema > **selecione**.
3. Confirme se o status da **conta** e da **licença do Intune** mostram verificações verdes:

    ![No Intune, selecione o usuário e confirme o status da conta e a licença do Intune Mostrar marcas de verificações verdes para o status](./media/troubleshoot-policies-in-microsoft-intune/account-status-intune-license-show-green.png)

    **Links úteis**:

    - [Atribuir licenças para que os usuários possam registrar dispositivos](../fundamentals/licenses-assign.md)
    - [Adicionar utilizadores ao Intune](../fundamentals/users-add.md)

4. Em **dispositivos**, encontre o dispositivo com um problema. Examine as diferentes colunas:

    - **Gerenciado**: para um dispositivo receber políticas de conformidade ou configuração, essa propriedade deve mostrar **MDM** ou **EAS/MDM**.

        - Se **gerenciado** não estiver definido como **MDM** ou **EAS/MDM**, o dispositivo não será registrado. Ele não recebe políticas de conformidade ou configuração até que ele seja registrado.

        - As políticas de proteção de aplicativo (gerenciamento de aplicativo móvel) não exigem que os dispositivos sejam registrados. Para obter mais informações, consulte [criar e atribuir políticas de proteção de aplicativo](../apps/app-protection-policies.md).

    - **Tipo de junção do Azure ad**: deve ser definido como **Workplace** ou **AzureAD**.
 
        - Se essa coluna **não estiver registrada**, pode haver um problema com o registro. Normalmente, o cancelamento do registro e o reregistro do dispositivo resolve esse estado.

    - **Compatível com o Intune**: deve ser **Sim**. Se **não** for mostrado, pode haver um problema com as políticas de conformidade ou o dispositivo não está se conectando ao serviço do Intune. Por exemplo, o dispositivo pode estar desligado ou pode não ter uma conexão de rede. Eventualmente, o dispositivo torna-se não compatível, possivelmente após 30 dias.

        Para obter mais informações, consulte Introdução [às políticas de conformidade do dispositivo](../protect/device-compliance-get-started.md).

    - **Compatível com o Azure ad**: deve ser **Sim**. Se **não** for mostrado, pode haver um problema com as políticas de conformidade ou o dispositivo não está se conectando ao serviço do Intune. Por exemplo, o dispositivo pode estar desligado ou pode não ter uma conexão de rede. Eventualmente, o dispositivo torna-se não compatível, possivelmente após 30 dias.

        Para obter mais informações, consulte Introdução [às políticas de conformidade do dispositivo](../protect/device-compliance-get-started.md).

    - **Último check-in**: deve ser uma data e hora recentes. Por padrão, os dispositivos do Intune verificam a cada 8 horas.

        - Se o **último check-in** tiver mais de 24 horas, pode haver um problema com o dispositivo. Um dispositivo que não pode fazer check-in não pode receber suas políticas do Intune.

        - Para forçar o check-in:
            - No dispositivo Android, abra o aplicativo Portal da Empresa > **dispositivos** > escolha o dispositivo na lista > **Verifique as configurações do dispositivo**.
            - No dispositivo iOS, abra o aplicativo do portal da empresa > **dispositivos** > escolha o dispositivo na lista > **Verifique as configurações**.

        - Em um dispositivo Windows, abra **configurações** > **contas** > **acessar o trabalho ou a escola** > selecione a conta ou o registro do MDM > **informações** > **sincronização**.

    - Selecione o dispositivo para ver informações específicas da política.

        **Conformidade do dispositivo** mostra os Estados das políticas de conformidade atribuídas ao dispositivo.

        **Configuração de dispositivo** mostra os Estados das políticas de configuração atribuídas ao dispositivo.

        Se as políticas esperadas não forem mostradas em **conformidade do dispositivo** ou **configuração do dispositivo**, as políticas não serão destinadas corretamente. Abra a política e atribua a política a este usuário ou dispositivo.

        **Estados de política**:

        - **Não aplicável**: essa política não tem suporte nesta plataforma. Por exemplo, as políticas do iOS não funcionam no Android. As políticas do Samsung KNOX não funcionam em dispositivos Windows.
        - **Conflito**: há uma configuração existente no dispositivo que o Intune não pode substituir. Ou, você implantou duas políticas com a mesma configuração usando valores diferentes.
        - **Pendente**: o dispositivo não fez check-in no Intune para obter a política. Ou, o dispositivo recebeu a política, mas não relatou o status para o Intune.
        - **Erros**: Pesquise erros e possíveis resoluções em [solucionar problemas de acesso aos recursos da empresa](../fundamentals/troubleshoot-company-resource-access-problems.md).

        **Links úteis**: 

        - [Maneiras de implantar políticas de conformidade do dispositivo](../protect/device-compliance-get-started.md#ways-to-deploy-device-compliance-policies)
        - [Monitorizar as políticas de conformidade de dispositivos](../protect/compliance-policy-monitor.md)

## <a name="youre-unsure-if-a-profile-is-correctly-applied"></a>Você não tem certeza se um perfil é aplicado corretamente

1. Entre no centro de [Administração do Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Selecione **dispositivos** > **todos os dispositivos** > selecione o dispositivo > **configuração do dispositivo**. 

    Cada dispositivo lista seus perfis. Cada perfil tem um **status**. O status se aplica quando todos os perfis atribuídos, incluindo restrições e requisitos de hardware e de so, são considerados juntos. Os status possíveis incluem:

    - **Compatível**: o dispositivo recebeu o perfil e os relatórios para o Intune de que está de acordo com a configuração.

    - **Não aplicável**: a configuração de perfil não é aplicável. Por exemplo, as configurações de email para dispositivos iOS não se aplicam a um dispositivo Android.

    - **Pendente**: o perfil é enviado para o dispositivo, mas não relatou o status para o Intune. Por exemplo, a encriptação no Android requer que o utilizador final ative a encriptação e, por isso, poderá estar pendente.

**Link útil**: [monitorar perfis de dispositivo de configuração](../configuration/device-profile-monitor.md)

> [!NOTE]
> Quando duas políticas com diferentes níveis de restrição se aplicam ao mesmo dispositivo ou utilizador, é aplicada a política mais restrita.

## <a name="policy-troubleshooting-resources"></a>Recursos de solução de problemas de política

- [Solução de problemas de políticas do Ios ou Android que não se aplicam a dispositivos](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Support-tip-Troubleshooting-iOS-or-Android-policies-not-applying/ba-p/280154) (abre outro site da Microsoft)
- [Solucionando problemas de falhas de política do Windows 10 Intune](https://blogs.technet.microsoft.com/configmgrdogs/2018/08/09/troubleshooting-windows-10-intune-policy-failures/) (abre um blog)
- [Solucionar problemas de configurações personalizadas do CSP para Windows 10](https://support.microsoft.com/en-us/help/4055338/troubleshoot-csp-setting-windows-10-computer-intune) (abre outro site da Microsoft)
- [Política de MDM do Windows 10 política de grupo vs Intune](https://blogs.technet.microsoft.com/cbernier/2018/04/02/windows-10-group-policy-vs-intune-mdm-policy-who-wins/) (abre outro site da Microsoft)

## <a name="alert-saving-of-access-rules-to-exchange-has-failed"></a>Alerta: Falha ao Guardar as Regras de Acesso no Exchange

**Problema**: Recebe o alerta **Falha ao Guardar as Regras de Acesso no Exchange**  na consola de administração.

Se você criar políticas no espaço de trabalho política do Exchange local (console de administração), mas estiver usando o Office 365, as configurações de política definidas não serão impostas pelo Intune. No alerta, observe a origem da política. No espaço de trabalho política do Exchange local, exclua as regras herdadas. As regras herdadas são regras globais do Exchange no Intune para o Exchange local e não são relevantes para o Office 365. Em seguida, crie uma nova política para o Office 365.

[Solucionar problemas do Exchange Connector local do Intune](../protect/troubleshoot-exchange-connector.md) pode ser um bom recurso.

## <a name="cant-change-security-policies-for-enrolled-devices"></a>Não é possível alterar políticas de segurança para dispositivos registrados

Windows Phone dispositivos não permitem que as políticas de segurança definidas usando MDM ou EAS sejam reduzidas em segurança depois de serem definidas. Por exemplo, você define um **número mínimo de caracteres de senha** como 8 e, em seguida, tenta reduzi-lo para 4. A política mais restritiva é aplicada ao dispositivo.

Dispositivos Windows 10 não podem remover políticas de segurança quando você não atribui a política (parar a implantação). Talvez seja necessário deixar a política atribuída e, em seguida, alterar as configurações de segurança de volta para os valores padrão.

Dependendo da plataforma do dispositivo, se você quiser alterar a política para um valor menos seguro, talvez seja necessário redefinir as políticas de segurança.

Por exemplo, no Windows 8.1, na área de trabalho, passe o dedo da direita para abrir **a barra de** botões. Escolha **configurações** > **painel de controle** > **contas de usuário**. No lado esquerdo, selecione a ligação **Repor Políticas de Segurança** e escolha **Repor Políticas**.

Outras plataformas, como Android, iOS e Windows Phone 8,1, talvez precisem ser desativadas e inscritas novamente para aplicar uma política menos restritiva.

[Solucionar problemas de registro de dispositivo](../enrollment/troubleshoot-device-enrollment-in-intune.md) pode ser um bom recurso.

## <a name="pcs-using-the-intune-software-client---classic-portal"></a>PCs usando o portal clássico do cliente de software do Intune

> [!NOTE]
> Esta seção se aplica ao portal clássico. 

### <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Erros relacionados com políticas do Microsoft Intune no policyplatform.log

Para computadores Windows gerenciados com o cliente de software do Intune, os erros de política no arquivo `policyplatform.log` podem ser de configurações não padrão no UAC (controle de conta de usuário) do Windows no dispositivo. Algumas definições de UAC não predefinidas podem afetar as instalações de cliente do Microsoft Intune e a execução de políticas.

#### <a name="resolve-uac-issues"></a>Resolver problemas de UAC

1. Extinga o computador. Veja [Remover dispositivos](../remote-actions/devices-wipe.md).

2. Aguarde 20 minutos para que o software de cliente seja removido.

    > [!NOTE]
    > Não tente remover o cliente nos Programas e Funcionalidades.

3. No menu Iniciar, digite **UAC** para abrir as configurações de controle de conta de usuário.

4. Mova o controle deslizante de notificação para a configuração padrão.

### <a name="error-cannot-obtain-the-value-from-the-computer-0x80041013"></a>ERRO: Não é possível obter o valor do computador, 0x80041013

Ocorre se a hora no sistema local estiver dessincronizada em cinco minutos ou mais. Se o horário no computador local estiver fora de sincronia, as transações seguras falharão porque os carimbos de data/hora são inválidos.

Para resolver esse problema, defina a hora do sistema local o mais próximo possível do horário da Internet. Ou defina-o como a hora nos controladores de domínio na rede.

## <a name="next-steps"></a>Próximos passos

[Problemas comuns e resoluções com perfis de email](../configuration/troubleshoot-email-profiles-in-microsoft-intune.md)

Obtenha [ajuda de suporte da Microsoft](../fundamentals/get-support.md)ou use os [fóruns da Comunidade](https://social.technet.microsoft.com/Forums/en-US/home?category=microsoftintune).
