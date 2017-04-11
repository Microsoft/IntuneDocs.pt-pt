---
title: "Resolver problemas de configuração do cliente | Documentos da Microsoft"
description: "Resolva problemas comuns de configuração do cliente."
keywords: 
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.date: 02/22/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: e46d292b-1d16-46db-a87f-d53eefa4d22a
ms.reviewer: tscott
ms.suite: ems
ms.custom: intune-classic
translationtype: Human Translation
ms.sourcegitcommit: e7beff3bf4579d9fb79f0c3f2fb8fbf9bb1ea160
ms.openlocfilehash: 9de1c3f8c3dbb7a5e00c5384cc7321aedfa5b9b5
ms.lasthandoff: 02/22/2017


---

# <a name="troubleshoot-client-setup-in-microsoft-intune"></a>Resolver problemas de configuração do cliente no Microsoft Intune

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

Utilize as seguintes informações para o ajudar a resolver problemas comuns de configuração de clientes. Se estas informações não resolverem o problema, veja [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md) para ver mais formas de obter ajuda.

## <a name="client-installation-fails"></a>Falha na instalação do cliente

-   Se não for apresentado nenhum alerta de implementação do software de cliente na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), verifique a conectividade à Internet e a configuração de proxy do computador e certifique-se de que este consegue comunicar com o URL do serviço, [https://manage.microsoft.com](https://manage.microsoft.com/). Em seguida, tente instalar o software de cliente novamente.

-   Pode configurar um e-mail para ser enviado a determinados destinatários em caso de alerta de falha de implementação do software de cliente, ao configurar uma regra de notificação na área de trabalho **Admin** . Para obter mais informações, veja [Ser notificado através de alertas do Microsoft Intune](/intune/deploy-use/get-notified-by-alerts).

-   O Intune apresenta o alerta crítico **Client Software Deployment Failure (Falha na Implementação do Software de Cliente)**, se a implementação do software de cliente falhar. Este será apresentado nas páginas **System Overview (Descrição Geral do Sistema)** e **Alerts (Alertas)** da [consola de administração do Microsoft Intune](https://manage.microsoft.com/). Eis como verificar a existência de alertas:

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com/), escolha **Alerts (Alertas)** &gt; **Overview (Descrição Geral)**.

2.  Na página **Alerts overview (Descrição geral dos alertas)**, poderá rever as seguintes informações:

    -   Os três alertas principais, que podem ser ordenados por data, categoria ou gravidade

    -   O número total de alertas ativos

3.  Escolha **All Alerts (Todos os Alertas)** para apresentar as seguintes informações na página **Alerts (Alertas)**. Os alertas críticos são apresentados primeiro:

    -   **Name (Nome)** – o nome do tipo de alerta que gerou o alerta.

    -   **Source (Origem)** – uma ligação para a origem do alerta.  Se o limiar de apresentação do tipo de alerta estiver definido como **All (Todos)**, esta ligação apresentará um único dispositivo afetado.  Se o limiar de apresentação do tipo de alerta estiver definido com um valor, esta ligação apresentará uma lista de todos os dispositivos afetados por este alerta.

    -   **Last Updated (Última Atualização)** – indica a hora em que o alerta foi modificado pela última vez. Se um alerta estiver fechado, será apresentada a hora em que o alerta foi fechado.

    -   **Severity (Gravidade)** – indica a gravidade do alerta.

## <a name="computer-enrollment-package-doesnt-download"></a>O pacote de inscrição do computador não é transferido
**Issue (Problema):** ao tentar inscrever um computador, ocorre o seguinte:
-  O pacote de inscrição não é transferido
-  A caixa de diálogo de transferência é apresentada, mas excede o tempo limite

**Resolution (Resolução):** no browser que estiver a utilizar para a transferência, para o período em ocorre a transferência, certifique-se de que as transferências estão ativadas e que os ficheiros encriptados podem ser guardados no disco local.

## <a name="client-installation-hangs-with-error-code-0x80040154"></a>A instalação do cliente bloqueia com o código de erro 0x80040154
**Problema:**

-  A instalação do cliente durante a inscrição bloqueia

-  Não é possível inscrever o dispositivo

-  Erro 0x80040154 em WindowsUpdate.log

Isto pode ser causado pela ausência de atualizações de software críticas no PC.

**Resolution (Resolução)**: certifique-se de que a política de atualização de software permite a instalação de atualizações críticas, conforme descrito em [Manter os PCs Windows atualizados com as atualizações de software no Microsoft Intune](/intune/deploy-use/keep-windows-pcs-up-to-date-with-software-updates-in-microsoft-intune)


## <a name="microsoft-intune-policy-related-errors-in-policyplatformlog"></a>Erros relacionados com políticas do Microsoft Intune no policyplatform.log
Nos dispositivos Windows sem MDM, os erros de políticas no ficheiro policyplatform.log podem ser o resultado das definições não predefinidas no Controlo de Conta de Utilizador no Windows (UAC) no dispositivo. Algumas definições de UAC não predefinidas podem afetar as instalações de cliente do Microsoft Intune e a execução de políticas.

### <a name="to-resolve-uac-issues"></a>Para resolver problemas de UAC

1.  Extinga o computador, conforme descrito em [Extinguir dispositivos e dados a partir da gestão do Microsoft Intune](/intune/deploy-use/retire-devices-from-microsoft-intune-management).

2.  Aguarde 20 minutos para que o software de cliente seja removido.

    > [!NOTE]
    > Não tente remover o cliente nos Programas e Funcionalidades.

3.  No menu Iniciar, escreva **UAC** para abrir as definições de Controlo de Conta de Utilizador.

4.  Mova o controlo de deslize de notificações para a predefinição.

## <a name="what-to-do-if-the-client-will-not-uninstall-from-the-microsoft-intune-administrator-console"></a>O que fazer se não conseguir desinstalar o cliente a partir da consola do administrador do Microsoft Intune

### <a name="to-remove-the-client-software-by-using-the-microsoft-intune-command-line-tool"></a>Para remover o software de cliente através da ferramenta de linha de comandos do Microsoft Intune

1.  Abra uma linha de comandos em modo de administrador.

2.  Aceda à pasta *%programfiles%\Microsoft\OnlineManagement\Common*

3.  Execute o seguinte comando ``ProvisioningUtil.exe /UninstallAgents /MicrosoftIntune``

## <a name="client-installation-error-codes"></a>Códigos de erro de instalação do cliente
A seguinte tabela descreve os códigos de erro que são apresentados em **Alerts (Alertas)** se a instalação do software de cliente falhar. Inclui sugestões para resolver o problema que é representado por cada código de erro.

|Código de erro|Possível problema|Resolução sugerida|
|--------------|--------------------|------------------------|
|**0x80CF0437**|O relógio no computador cliente não está definido com a hora correta.|Certifique-se de que o relógio e o fuso horário no computador cliente estão definidos com a hora e fuso horário corretos.|
|**0x80240438**, **0x80CF0438**, **0x80CF401B**|Não é possível ligar ao serviço Intune. Verifique as definições de proxy do cliente.|Verifique se a configuração de proxy no computador cliente é suportada pelo Intune e se o computador cliente tem acesso à Internet. Para obter mais informações sobre configurações de proxy suportadas, veja [Ajudar a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**0x80CF402C**|Não é possível ligar ao serviço Intune. Verifique a conectividade da rede.|Verifique que o computador tem conectividade de rede. Certifique-se de que o cabo de rede está ligado ou que a rede sem fios está ativada.|
|**0x80240438, 0x80CF0438**|As definições de proxy no Internet Explorer e no Sistema Local não estão configuradas.|Verifique as definições de proxy do cliente e confirme se a configuração de proxy no computador cliente é suportada pelo Intune e se o computador cliente tem acesso à Internet. Para obter mais informações sobre configurações de proxy suportadas, veja [Ajudar a proteger os PCs Windows com o Endpoint Protection para o Microsoft Intune](/intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune).|
|**0x80043001**|O pacote de inscrição está desatualizado.|Transfira e instale o pacote de software de cliente atual a partir da área de trabalho **Admin** . Para obter instruções, consulte o tópico [Instalar o cliente do PC Windows com o Microsoft Intune](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune).|
|**0x80043004**|A subscrição não existe ou está desativada.|Verifique se a sua conta e subscrição do Intune ainda estão ativas. Para ver as definições da sua conta, inicie sessão na mesma no [Centro de administração do Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043002**|A conta está em modo de manutenção.|Não pode inscrever novos computadores cliente quando a conta estiver em modo de manutenção. Para ver as definições da sua conta, inicie sessão na mesma no [Centro de administração do Office 365](http://go.microsoft.com/fwlink/?LinkId=698854%20).|
|**0x80043003**|A conta foi eliminada.|Verifique se a sua conta e subscrição do Intune ainda estão ativas. Para ver as definições da sua conta, inicie sessão na conta.|
|**0x80043005**|O computador cliente foi extinguido.|Aguarde algumas horas, remova todas as antigas versões do software de cliente do computador e, em seguida, tente instalar o software de cliente novamente. Para obter instruções, consulte **O que fazer se não conseguir desinstalar o cliente a partir da consola do administrador do Microsoft Intune** acima.|
|**0x80043006**|Foi atingido o número máximo de licenças permitido na conta.|A sua organização tem de comprar licenças adicionais para que possa inscrever mais computadores cliente no serviço.|
|**0x80043007**|Não foi possível localizar o ficheiro de certificado na mesma pasta que o programa do instalador.|Extraia todos os ficheiros antes de iniciar a instalação. Não mude o nome ou a localização de nenhum dos ficheiros extraídos; todos os ficheiros têm de estar na mesma pasta ou a instalação irá falhar. Para mais informações, consulte [Instalar o cliente do PC Windows com o Microsoft Intune](/intune/deploy-use/install-the-windows-pc-client-with-microsoft-intune).|
|**0x8024D015**, **0x00240005**, **0x80070BC2**, **0x80070BC9**, **0x80CFD015**|O software não pode ser instalado porque existe um reinício pendente do computador cliente.|Reinicie o computador e, em seguida, tente instalar o software de cliente novamente.|
|**0x80070032**|Um ou mais pré-requisitos para a instalação do software de cliente não foram encontrados no computador cliente.|Certifique-se de que todas as atualizações necessárias estão instaladas no computador cliente e, em seguida, tente instalar o software de cliente novamente. Para mais informações sobre os pré-requisitos para instalar o software cliente, consulte [Requisitos de infraestrutura de rede do Microsoft Intune ](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune).|
|**0x80043008**|Não foi possível iniciar o serviço Atualizações do Microsoft Online Management.|Contacte o Suporte, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).|
|**0x80043009**|O computador cliente já está inscrito no serviço.|Tem de extinguir o computador cliente para o poder inscrever novamente no serviço. Para instruções, consulte [Extinguir dispositivos a partir da gestão do Microsoft Intune](/intune/deploy-use/retire-devices-from-microsoft-intune-management).|
|**0x8004300A**|(Fase 21) O erro ocorre quando o pacote de inscrição é implementado no GPO para ser instalado no âmbito do utilizador e não no âmbito do computador. |Certifique-se de que o GPO é visado corretamente através de GPSI no âmbito do computador. Para ver mensagens sobre este assunto num fórum, veja este [Fórum da TechNet](https://social.technet.microsoft.com/Forums/en-US/bb9fa71c-c132-4954-abb0-70be8acbd925/failed-to-install-windows-intune?forum=microsoftintuneprod).|
|**0x8004300B**|Não é possível executar o pacote de instalação do software de cliente porque a versão do Windows que está a ser executada no cliente não é suportada.|O Intune não suporta a versão do Windows que está a ser executada no computador cliente. Para obter uma lista dos sistemas operativos suportados, consulte [Requisitos de infraestrutura de rede do Microsoft Intune](/intune/get-started/network-infrastructure-requirements-for-microsoft-intune).|
|**0xAB2**|O Windows Installer não conseguiu aceder ao tempo de execução de VBScript de uma ação personalizada.|Este erro é causado por uma ação personalizada baseada em DLLs (Dynamic-Link Libraries). Ao resolver problemas com o DLL, pode ter de utilizar as ferramentas descritas em [KB198038 do Suporte da Microsoft: Ferramentas Úteis para Problemas de Empacotamento e Implementação](http://go.microsoft.com/fwlink/?LinkID=234255).|
|**0x8004300f**|O software não pode ser instalado porque o cliente do System Center Configuration Manager já está instalado.|Remova o cliente do Configuration Manager e, em seguida, tente instalar o software de cliente novamente.|
|**0x80043010**|O software não pode ser instalado porque o cliente do Device Management da Open Mobile Alliance (OMADM) já está instalado.|Anule a inscrição do cliente do OMADM e, em seguida, tente instalar o software de cliente novamente.|
Se os problemas de instalação persistirem, contacte o Suporte, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md). Tenha o registo de inscrição do computador cliente (localizado em %*programfiles*%\Microsoft\OnlineManagement\Logs\Enrollment.log e em %*userprofile*%\AppData\Local\Microsoft\OnlineManagement\Logs\Enrollement.log) e o registo do Windows Update (%*windir*%\windowsupdate.log) disponíveis para mostrar aos engenheiros de suporte.

## <a name="what-to-do-if-endpoint-protection-is-not-uninstalled-when-you-uninstall-the-client"></a>O que fazer se o Endpoint Protection não for desinstalado quando desinstalar o cliente

Por vezes, o agente de Proteção do Anfitrião (Endpoint Protection) pode continuar instalado depois de executar os comandos acima. Se isto acontecer, execute este comando a partir de uma linha de comandos elevada:

    ```
    "C:\Program Files\Managed Defender\Setup.exe" /x /q /s
    ```


### <a name="next-steps"></a>Passos seguintes
Se estas informações de resolução de problemas não o ajudaram, contacte o Suporte da Microsoft, conforme descrito em [Como obter suporte para o Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

