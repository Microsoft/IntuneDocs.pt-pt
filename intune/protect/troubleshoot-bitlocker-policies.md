---
title: Dicas de resolução de problemas para as políticas bitLocker no Microsoft Intune
titleSuffix: Microsoft Intune
description: Descreve como ativar a encriptação bitLocker num dispositivo utilizando a política Intune e como verificar se a sua política foi implementada com sucesso num dispositivo.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 01/29/2020
ms.topic: troubleshooting
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: medium
ms.technology: ''
ms.assetid: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: f3b32268d0b04dee84a737b9a1c768bc4fab7202
ms.sourcegitcommit: 3964e6697b4d43e2c69a15e97c8d16f8c838645b
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 02/21/2020
ms.locfileid: "77556504"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Problemas bitLocker políticas no Microsoft Intune

Este artigo pode ajudar os administradores da Intune a entender como os dispositivos do Windows 10 configuram o BitLocker com base na política intune. Este artigo também fornece orientações sobre como resolver problemas com as definições do BitLocker nos dispositivos que gere com o Intune.  

## <a name="understanding-bitlocker"></a>Compreender bitLocker

A encriptação de unidade BitLocker é um serviço oferecido pelos sistemas operativos Microsoft Windows que permite aos utilizadores encriptar dados nos seus discos rígidos. O BitLocker suporta encriptação para unidades de sistema operativo, unidades de mídia amovíveis e unidades de dados fixas. O BitLocker também suporta a utilização de encriptação de 256 bits para uma melhor proteção de dados sensíveis.  

Com o Microsoft Intune, tem os seguintes métodos para gerir o BitLocker nos dispositivos Windows 10:

- Políticas de **configuração** do dispositivo - Certas opções de política incorporadas estão disponíveis no Intune quando cria um perfil de configuração do dispositivo para gerir a proteção de pontos finais. Para encontrar estas opções, crie um perfil de dispositivo para proteção de [pontos finais,](endpoint-protection-configure.md#create-a-device-profile-containing-endpoint-protection-settings)selecione o Windows **10 e mais tarde** para a *Plataforma,* e, em seguida, selecione a categoria de **Encriptação do Windows** para *Definições*. 

   Pode ler sobre as opções e funcionalidades disponíveis aqui: [Encriptação do Windows](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **As linhas** de base de segurança - As linhas de [base de segurança](security-baselines.md) são grupos conhecidos de definições e valores predefinidos que são recomendados pela equipa de segurança relevante para ajudar a proteger os dispositivos windows. Diferentes fontes de base, como a *Base de Base* de Segurança do MDM ou o Microsoft Defender *ATP Baseline* podem gerir as mesmas configurações bem diferentes das outras. Também podem gerir as mesmas definições que gere com as políticas de configuração do dispositivo. 

Além de Intune, para hardware que esteja em conformidade com o Modern Standby e o HSTI, quando utilizar qualquer uma destas funcionalidades, a Encriptação do Dispositivo BitLocker é automaticamente ligada sempre que o utilizador se une a um dispositivo ao Azure AD. A Azure AD fornece um portal onde as chaves de recuperação também estão apoiadas, para que os utilizadores possam recuperar a sua própria chave de recuperação para autosserviço, se necessário.

Também é possível que as definições bitLocker sejam geridas por outros meios como a Política de Grupo, ou manualmente definidas por um utilizador do dispositivo.

Independentemente da forma como as definições são aplicadas a um dispositivo, as políticas bitLocker fazem uso do [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) para configurar a encriptação no dispositivo. O BitLocker CSP é incorporado no Windows e quando o Intune implementa uma política BitLocker para um dispositivo atribuído, é o BitLocker CSP no dispositivo que escreve os valores apropriados para o registo do Windows para que as definições da apólice possam produzir efeitos.

Se quiser saber mais sobre o BitLocker, consulte os seguintes recursos:

- [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [BitLocker Visão geral e requisitos FAQ](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Agora que tem uma compreensão geral do que estas políticas fazem e como funcionam, veja como pode verificar se as definições do BitLocker se aplicam com sucesso a um cliente Windows.

## <a name="verify-the-source-of-bitlocker-settings"></a>Verifique a origem das definições do BitLocker

Quando investiga um problema do BitLocker num dispositivo Windows 10, é importante primeiro determinar se o problema está relacionado com Intune ou relacionado com o Windows. Depois de conhecida a provável fonte de falha, pode então concentrar os seus esforços de resolução de problemas no local certo e, se necessário, obter apoio da equipa correta.  

Como primeiro passo, determine se a política intune foi implementada com sucesso para o dispositivo-alvo. No exemplo seguinte, tem uma política de configuração do dispositivo que implementa as definições de Encriptação do Windows (BitLocker), como mostrado:

![Política de configuração do dispositivo de encriptação do Windows com as definições](./media/troubleshooting-bitlocker-policies/settings.png)

Como confirma que as definições foram aplicadas ao dispositivo-alvo? Seguem-se algumas formas de o fazer.

### <a name="device-configuration-policy-device-status"></a>Estado do dispositivo de configuração do dispositivo  

Quando utilizar a política de configuração do dispositivo para configurar o BitLocker, pode verificar o estado da apólice no portal Intune.

1. Inscreva-se no [Microsoft Endpoint Manager Admin Center](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Selecione **Dispositivos** > Perfis de **Configuração** e, em seguida, selecione o perfil que contém definições bitLocker.

3. Depois de selecionar o perfil que pretende visualizar, selecione **O Estado do Dispositivo**. Os dispositivos atribuídos ao perfil estão listados e a coluna de estado do *Dispositivo* indica se um dispositivo implementou com sucesso o perfil.

Lembre-se, pode haver um atraso entre um dispositivo que recebe uma política bitLocker, e a unidade está totalmente encriptada.  

### <a name="use-control-panel-on-the-client"></a>Use painel de controlo no cliente  

Num dispositivo que ativou o BitLocker e encriptou uma unidade, pode ver o estado BitLocker a partir de um Painel de Controlo de Dispositivos. No dispositivo, abra o Painel de **Controlo** > **Sistema e segurança** > **encriptação de unidade BitLocker**. A confirmação aparece como visto na seguinte imagem.  

![BitLocker é ligado no Painel de Controlo](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Use um pedido de comando  

Num dispositivo que ativou o BitLocker e encriptou uma unidade, inicie o Comando Prompt com credenciais de administração e, em seguida, execute `manage-bde -status`. Os resultados devem assemelhar-se ao seguinte exemplo:  
![Um resultado do comando de estado](./media/troubleshooting-bitlocker-policies/command.png)

No exemplo:

- **A proteção BitLocker** está **on**
- **Percentagem Encriptada** é **100%**
- **Método de encriptação** é **XTS-AES 256**

Também pode verificar **os Protetores chave** executando o seguinte comando:

```cmd
Manage-bde -protectors -get c:
```

Ou com a PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Reveja a configuração da chave de registo dos dispositivos

Depois de a política bitLocker ser implementada com sucesso para um dispositivo, veja a seguinte chave de registo no dispositivo onde pode rever a configuração das definições bitLocker: *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker*. Segue-se um exemplo:

![Chave de registo BitLocker](./media/troubleshooting-bitlocker-policies/registry.png)

Estes valores são configurados pelo BitLocker CSP. Verifique se os valores das teclas correspondem às definições especificadas na fonte da sua política de encriptação intune Windows. Para obter mais informações sobre cada uma destas definições, consulte [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> O Windows Event Viewer também irá conter várias informações relacionadas com o Bitlocker. Há muitos para listar aqui, mas procurar a **API Bitlocker** irá fornecer-lhe muitas informações úteis.

### <a name="check-the-mdm-diagnostics-report"></a>Consulte o relatório de diagnóstico do MDM

Num dispositivo que ativou o BitLocker, pode gerar e visualizar um relatório de diagnóstico do MDM a partir do dispositivo-alvo para confirmar que a política do BitLocker está presente. Se conseguir ver as definições políticas do relatório, é outra indicação de que a política foi implementada com sucesso. O *Microsoft Ajuda* o vídeo no seguinte link explica como capturar um relatório de diagnóstico do MDM a partir de um dispositivo Windows.

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Quando analisa o relatório de diagnóstico do MDM, o conteúdo pode parecer um pouco confuso no início. Segue-se um exemplo que mostra como relacionar o que está no relatório com as definições de uma política:

![Exemplo de relatório de diagnóstico do MDM](./media/troubleshooting-bitlocker-policies/report.png)

O resultado da saída mostra os valores que correspondem aos valores da sua política BitLocker:

![Resultado da saída mostra os valores ](./media/troubleshooting-bitlocker-policies/output.png)

Resultados da saída de diagnóstico sMD:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Pode fazer referência à [documentação do BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) para ver o que cada valor significa. Para este exemplo, um corte é partilhado na imagem seguinte.

![Finalidades dos valores](./media/troubleshooting-bitlocker-policies/shared-example.png)

Da mesma forma, pode ver todos os valores e comprová-los a partir da ligação BitLocker CSP.

> [!TIP]
> O principal objetivo do relatório de diagnóstico do MDM é ajudar o Microsoft Support a resolver problemas. Se abrir um caso de suporte para o Intune e o problema envolver clientes windows, é sempre uma boa ideia reunir este relatório e incluí-lo no seu pedido de suporte.

## <a name="troubleshooting-bitlocker-policy"></a>Política bitLocker de resolução de problemas

Deve agora ter uma boa ideia de como confirmar que a política bitLocker implementada com sucesso pela Intune, que entrega a configuração do BitLocker ao BitLocker CSP em WIndows.

**A política não chega ao dispositivo** - Quando a sua política Intune não está presente em nenhuma capacidade:

- **O dispositivo está devidamente matriculado no Microsoft Intune?** Caso contrário, terá de resolver isso antes de resolver algo específico da apólice. A ajuda na resolução de problemas problemas com os problemas de inscrição do Windows pode ser encontrada [aqui](../enrollment/troubleshoot-windows-enrollment-errors.md).

- **Existe uma ligação de rede ativa no dispositivo?** Se o dispositivo estiver em modo avião ou desligado, ou se o utilizador tiver o dispositivo num local sem serviço, a apólice não será entregue ou aplicada até que a conectividade da rede seja restaurada.

- **A política BitLocker foi implementada para o utilizador ou grupo de dispositivos corretos?** Verifique se o utilizador ou dispositivo correto é membro dos grupos visados.

**A política está presente, mas nem todas as configurações configuradas com sucesso** - Quando a sua política Intune chega ao dispositivo, mas nem todas as configurações são definidas:

- **A implementação de toda a política falha, ou são apenas certas configurações que não se aplicam?** Se se encontrar confrontado com um cenário em que apenas algumas definições de política não se aplicam, verifique as seguintes considerações:

  1. **Nem todas as definições bitLocker são suportadas em todas as versões do Windows**.
     A política resume-se a um dispositivo como uma única unidade, por isso, se algumas definições se aplicarem e outras não o fizerem, pode estar confiante de que a apólice em si é recebida. Neste cenário, é possível que a versão do Windows no dispositivo não suporte as definições problemáticas. Consulte o [BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) na documentação do Windows para obter detalhes sobre os requisitos da versão para cada definição.

  2. **O BitLocker não é suportado em todo o hardware.**
     Mesmo que tenha a versão certa do Windows, é possível que o hardware do dispositivo subjacente não cumpra os requisitos para a encriptação BitLocker. Pode encontrar os requisitos do sistema para o [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) na documentação do Windows, mas as principais coisas a verificar são que o dispositivo tem um chip TPM compatível (1.2 ou mais tarde) e um BIOS compatível com o Fidedigno (TCG) compatível com BIOS ou firmware UEFI.
     
**A encriptação bitlocker não é executada silenciosamente** - Configurauma política de proteção de ponto final com a definição "Aviso para outra encriptação de disco" definida para bloquear e o assistente de encriptação ainda aparece:

- **Confirme que a versão do Windows suporta encriptação silenciosa** Isto requer um mínimo de versão 1803. Se o utilizador não for um administator no dispositivo do que requer uma versão mínima de 1809. Adicionalmente, 1809 suporte adicional para dispositivos que não suportam Suporte Moderno

**O dispositivo encriptado Bitlocker mostra como não conforme para as políticas** de conformidade intune - O problema ocorre quando a encriptação BitLocker não está terminada. Com base em fatores como o tamanho do disco, número de ficheiros e definições bitLocker, a encriptação BitLocker pode demorar muito tempo. Após a encriptação estar completa, o dispositivo será mostrado como Conforme. Os dispositivos também podem tornar-se temporariamente incompatíveis imediatamente após uma recente instalação de Atualizações WIndows.

**Os dispositivos são encriptados usando 128 bits algorithim quando a política especifica 256 bits** -- Por padrão, o Windows 10 irá encriptar uma unidade com encriptação xTS-AES de 128 bits. Consulte este guia para [configurar encriptação de 256 bits para BitLocker durante o Autopilot](https://techcommunity.microsoft.com/t5/intune-customer-success/setting-256-bit-encryption-for-bitlocker-during-autopilot-with/ba-p/323791#).


**Investigação de exemplo**

- Implementa uma política BitLocker para um dispositivo Windows 10 e a definição de **dispositivos Encrypt** mostra um estado de **Erro** no portal.

- Como o nome sugere, esta definição permite que um administrador exija que a encriptação seja ativada utilizando *a Encriptação BitLocker > Device*. Utilizando as dicas de resolução de problemas mencionadas anteriormente, consulte primeiro o relatório de Diagnóstico do MDM. O relatório confirma que a política correta foi implementada no dispositivo:

  ![Relatório confirma que a política correta é implementada no dispositivo](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Também verifica o sucesso no registo:

  ![Valor de registo de encriptação de Dispositivos obrigatórios mostra 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Em seguida, verifique o estado do TPM usando powerShell e descubra que o TPM não está disponível no dispositivo:

  ![Verificado estado tPM usando PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Como o BitLocker depende do TPM, pode concluir que o BitLocker não falha devido a um problema com o Intune ou a apólice, mas sim porque o dispositivo em si não tem um chip TPM ou TPM é desativado no BIOS.

  Como dica adicional, pode confirmar o mesmo no Windows Event Viewer no âmbito do registo de **Aplicações e Serviços** > **Microsoft** > **Windows** > **BitLocker API**. No registo de eventos **bitLocker API,** você encontrará um Id de evento 853 que significa que TPM não está disponível:

  ![Id do evento 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > Também pode verificar o estado do TPM executando **tpm.msc** no dispositivo.

## <a name="summary"></a>Resumo

Quando se despede dos problemas de política do BitLocker com o Intune e pode confirmar que a política atinge o dispositivo pretendido, é seguro assumir que o problema não está diretamente relacionado com o Intune. O problema é mais provável que seja um problema com o Windows OS ou com o hardware. Neste caso, comece a procurar noutras áreas como a configuração TPM ou UEFI e secure boot).

## <a name="next-steps"></a>Próximos passos  

Seguem-se mais recursos que podem ajudar quando trabalha com o BitLocker:

- [Documentação do produto BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Requisitos do sistema BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [BitLocker frequentemente fez perguntas](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Documentação do BitLocker CSP](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Intune Windows Crypton definições políticas](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Encriptação automática independente de hardware BitLocker usando AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Política do CSP para encriptação BitLocker em dispositivos piloto automático](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Walkthrough criando e implementando a política bitLocker com Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)
