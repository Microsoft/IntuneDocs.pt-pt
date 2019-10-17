---
title: Dicas de solução de problemas para políticas do BitLocker no Microsoft Intune
titleSuffix: Microsoft Intune
description: Descreve como habilitar a criptografia BitLocker em um dispositivo usando a política do Intune e como verificar se a política foi implantada com êxito em um dispositivo.
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 10/02/2019
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
ms.openlocfilehash: 440eb2d457783ac71b905d064a6d83abaa966cfe
ms.sourcegitcommit: 9013f7442bbface78feecde2922e8e546a622c16
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72503885"
---
# <a name="troubleshoot-bitlocker-policies-in-microsoft-intune"></a>Solucionar problemas de políticas do BitLocker no Microsoft Intune

Este artigo pode ajudar os administradores do Intune a entender como os dispositivos Windows 10 configuram o BitLocker com base na política do Intune. Este artigo também fornece orientação sobre como solucionar problemas com as configurações do BitLocker nos dispositivos gerenciados com o Intune.  

## <a name="understanding-bitlocker"></a>Noções básicas sobre o BitLocker

A criptografia de unidade de disco BitLocker é um serviço oferecido pelos sistemas operacionais Microsoft Windows que permite aos usuários criptografar dados em seus discos rígidos. O BitLocker dá suporte à criptografia para unidades do sistema operacional, unidades de mídia removíveis e unidades de dados fixas. O BitLocker também dá suporte ao uso de criptografia de 256 bits para melhor proteção de dados confidenciais.  

Com o Microsoft Intune, você tem os seguintes métodos para gerenciar o BitLocker em dispositivos Windows 10:

- **Políticas de configuração de dispositivo** – determinadas opções de política internas estão disponíveis no console de administração do Intune em **configuração do dispositivo** >  Endpoint Protection**política de criptografia do Windows** > . Você pode encontrar todos os recursos e opções disponíveis aqui: [criptografia do Windows](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption).

- **Linhas de base de segurança** - [linhas de base de segurança](security-baselines.md) são grupos conhecidos de configurações e valores padrão que são recomendados pela equipe de segurança relevante para ajudar a proteger dispositivos Windows. Fontes de linha de base diferentes, como a linha de base de *segurança do MDM* ou a linha de *base do Microsoft defender ATP* , podem gerenciar as mesmas configurações, bem como configurações diferentes. Eles também podem gerenciar as mesmas configurações que você gerencia com as políticas de configuração de dispositivo. 

Além do Intune, é possível que as configurações do BitLocker sejam gerenciadas por outros meios como Política de Grupo ou definidas manualmente por um usuário do dispositivo.

Não importa como as configurações são aplicadas a um dispositivo, as políticas do BitLocker usam o [CSP do BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) para configurar a criptografia no dispositivo. O CSP do BitLocker é integrado ao Windows e quando o Intune implanta uma política do BitLocker em um dispositivo atribuído, é o CSP do BitLocker no dispositivo que grava os valores apropriados no registro do Windows para que as configurações da política possam entrar em vigor.

Se você quiser saber mais sobre o BitLocker, consulte os recursos abaixo.

- [Pelo](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Perguntas frequentes sobre requisitos e visão geral do BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)

Agora que você tem uma compreensão geral do que essas políticas fazem e como elas funcionam, veja como você pode verificar se as configurações do BitLocker se aplicam com êxito a um cliente do Windows.

## <a name="verify-the-source-of-bitlocker-settings"></a>Verificar a origem das configurações do BitLocker

Quando você investiga um problema do BitLocker em um dispositivo Windows 10, é importante primeiro determinar se o problema está relacionado ao Intune ou ao Windows. Depois que a origem provável de falha for conhecida, você poderá concentrar seus esforços de solução de problemas no lugar certo e, se necessário, obter suporte da equipe correta.  

Como uma primeira etapa, determine se a política do Intune foi implantada com êxito no dispositivo de destino. No exemplo a seguir, você tem uma política de configuração de dispositivo que implanta as configurações de criptografia do Windows (BitLocker), conforme mostrado: 

![Política de configuração do dispositivo de criptografia do Windows com as configurações](./media/troubleshooting-bitlocker-policies/settings.png)

Como você confirma que as configurações foram aplicadas ao dispositivo de destino? Veja a seguir algumas maneiras de fazer isso.

### <a name="device-configuration-policy-device-status"></a>Status do dispositivo da política de configuração do dispositivo  

Ao usar a política de configuração de dispositivo para configurar o BitLocker, você pode verificar o status da política no portal do Intune. No portal, acesse **configuração do dispositivo** > **perfis** > selecione o perfil que contém as configurações do BitLocker e, em seguida, selecione **status do dispositivo**. Os dispositivos atribuídos ao perfil são listados e a coluna *status do dispositivo* indica se um dispositivo implantou o perfil com êxito. 

Lembre-se, pode haver um atraso entre um dispositivo que recebe uma política do BitLocker e a unidade que está sendo totalmente criptografada.  

 
### <a name="use-control-panel-on-the-client"></a>Usar o painel de controle no cliente  

Em um dispositivo que habilitou o BitLocker e criptografou uma unidade, você pode exibir o status do BitLocker em um painel de controle de dispositivos. No dispositivo, abra o **painel de controle** > **sistema e segurança** > **criptografia de unidade de disco BitLocker**. A confirmação aparece como mostrado na imagem a seguir.  

![O BitLocker está ativado no painel de controle](./media/troubleshooting-bitlocker-policies/control-panel.png)

### <a name="use-a-command-prompt"></a>Usar um prompt de comando  

Em um dispositivo que habilitou o BitLocker e criptografou uma unidade, inicie o prompt de comando com credenciais de administrador e execute `manage-bde -status`. Os resultados devem ser semelhantes ao exemplo a seguir:  
![A o resultado do comando de status @ no__t-1

No exemplo: 
- A **proteção do BitLocker** está **ativada**,  
- O **percentual criptografado** é de **100%**  
- O **método de criptografia** é **XTS-AES 256**.  

Você também pode verificar **protetores de chave** executando o seguinte comando:

```cmd
Manage-bde -protectors -get c:
```

Ou com o PowerShell:

```powershell
Confirm-SecureBootUEFI
```

### <a name="review-the-devices-registry-key-configuration"></a>Examinar a configuração da chave do registro de dispositivos   

Depois que a política do BitLocker for implantada com êxito em um dispositivo, exiba a seguinte chave do registro no dispositivo em que você pode examinar a configuração das configurações do BitLocker: *HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\PolicyManager\current\device\BitLocker* . Segue-se um exemplo:

![Chave do registro do BitLocker](./media/troubleshooting-bitlocker-policies/registry.png)

Esses valores são configurados pelo CSP do BitLocker. Verifique se os valores das chaves correspondem às configurações especificadas na origem da sua política de criptografia do Windows do Intune. Para obter mais informações sobre cada uma dessas configurações, consulte [CSP do BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp).

> [!NOTE]
> O Windows Visualizador de Eventos também conterá várias informações relacionadas ao BitLocker. Há muitos para listar aqui, mas a pesquisa pela **API do BitLocker** fornecerá muitas informações úteis.

### <a name="check-the-mdm-diagnostics-report"></a>Verificar o relatório de diagnóstico de MDM  

Em um dispositivo que habilitou o BitLocker, você pode gerar e exibir um relatório de diagnóstico de MDM do dispositivo de destino para confirmar se a política do BitLocker está presente. Se você puder ver as configurações de política no relatório, será outra indicação de que a política foi implantada com êxito. O vídeo *ajuda da Microsoft* no seguinte link explica como capturar um relatório de diagnóstico do MDM de um dispositivo Windows. 

> [!VIDEO https://www.youtube.com/embed/WKxlcjV4TNE]

Quando você analisa o relatório de diagnóstico do MDM, o conteúdo pode parecer um pouco confuso a princípio. Veja a seguir um exemplo que mostra como correlacionar o que há no relatório com as configurações em uma política:

![Exemplo de relatório de diagnóstico do MDM](./media/troubleshooting-bitlocker-policies/report.png)

O resultado da saída mostra os valores que correspondem aos valores de sua política do BitLocker:

![Resultado da saída mostra os valores ](./media/troubleshooting-bitlocker-policies/output.png)

Resultados de saída do diagnóstico de MDM:

```asciidoc
EncryptionMethodWithXtsOsDropDown: 7 (The value 7 refers to the 256 bit encryption)
EncryptionMethodWithXtsFdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
EncryptionMethodWithXtsRdvDropDown: 6 (The value 6 refers to the 128 bit encryption)
```

Você pode fazer referência à [documentação do CSP do BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) para ver o que significa cada valor. Para este exemplo, um trecho de código é compartilhado na imagem a seguir.

![Fins de valores](./media/troubleshooting-bitlocker-policies/shared-example.png)

 Da mesma forma, você pode ver todos os valores e verificá-los no link do CSP do BitLocker.

> [!TIP]
> A principal finalidade do relatório de diagnóstico do MDM é ajudar a Suporte da Microsoft ao solucionar problemas. Se você abrir um caso de suporte para o Intune e o problema envolver clientes Windows, é sempre uma boa ideia coletar esse relatório e incluí-lo em sua solicitação de suporte.

## <a name="troubleshooting-bitlocker-policy"></a>Solucionando problemas de política do BitLocker

Agora você deve ter uma boa ideia de como confirmar se a política do BitLocker foi implantada com êxito pelo Intune, que desligou a configuração do BitLocker para o CSP do BitLocker no WIndows.  

A **política não consegue acessar o dispositivo** -quando sua política do Intune não está presente em nenhuma capacidade:  
- **O dispositivo está registrado corretamente no Microsoft Intune?** Caso contrário, você precisará abordar isso antes de solucionar qualquer coisa específica à política. A ajuda para solucionar problemas de registro do Windows pode ser encontrada [aqui](../enrollment/troubleshoot-windows-enrollment-errors.md).  
- **Há uma conexão de rede ativa no dispositivo?** Se o dispositivo estiver no modo avião ou desativado, ou se o usuário tiver o dispositivo em um local sem serviço, a política não será entregue ou aplicada até que a conectividade de rede seja restaurada.  
- **A política do BitLocker foi implantada no usuário ou grupo de dispositivos correto?** Verifique se o usuário ou o dispositivo correto é membro dos grupos que você tem como destino.  

A **política está presente, mas nem todas as configurações foram configuradas com êxito** -quando sua política do Intune atinge o dispositivo, mas nem todas as configurações estão definidas:  
- **A implantação de toda a política falha ou é apenas determinadas configurações que não se aplicam?** Se você estiver enfrentando um cenário em que apenas algumas configurações de política não se aplicam, verifique as seguintes considerações:

  1. **Nem todas as configurações do BitLocker têm suporte em todas as versões do Windows**.  
  A política se resume a um dispositivo como uma única unidade, portanto, se algumas configurações se aplicarem e outras não, você poderá ter certeza de que a própria política será recebida. Nesse cenário, é possível que a versão do Windows no dispositivo não dê suporte às configurações problemáticas. Consulte [CSP do BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp) na documentação do Windows para obter detalhes sobre os requisitos de versão para cada configuração.  

  1. O **BitLocker não tem suporte em todos os hardwares**.  
  Mesmo que você tenha a versão correta do Windows, é possível que o hardware do dispositivo subjacente não atenda aos requisitos de criptografia do BitLocker. Você pode encontrar os [requisitos do sistema para o BitLocker (https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements) na documentação do Windows, mas os principais itens a serem verificados são que o dispositivo tem um chip TPM compatível (1,2 ou posterior) e um firmware ou BIOS compatível com TCG (Trusted Computing Group).

**Investigação de exemplo** – você implanta uma política do BitLocker em um dispositivo Windows 10 e a configuração **criptografar dispositivos** mostra um status de **erro** no Portal.

- Como o nome sugere, essa configuração permite que um administrador exija que a criptografia seja ativada usando o *BitLocker > criptografia de dispositivo*. Usando as dicas de solução de problemas mencionadas anteriormente, primeiro você verifica o relatório de diagnóstico do MDM. O relatório confirma que a política correta foi implantada no dispositivo:

  ![O relatório confirma que a política correta está implantada no dispositivo](./media/troubleshooting-bitlocker-policies/mdm-report.png)

- Você também verifica o sucesso no registro:

  ![O valor do registro RequiredDeviceEncryption mostra 1](./media/troubleshooting-bitlocker-policies/registry-confirm.png)

- Em seguida, você verifica o status do TPM usando o PowerShell e descobre que o TPM não está disponível no dispositivo:

  ![Status do TPM verificado usando o PowerShell](./media/troubleshooting-bitlocker-policies/tpm-command.png)

- Como o BitLocker depende do TPM, você pode concluir que o BitLocker não falha devido a um problema com o Intune ou com a política, mas porque o próprio dispositivo não tem um chip TPM ou o TPM está desabilitado no BIOS.

  Como uma dica adicional, você pode confirmar o mesmo no Windows Visualizador de Eventos em **aplicativos e serviços log** > **API do BitLocker**do**Windows** > . No log de eventos da **API do BitLocker** , você encontrará uma ID de evento 853 que significa que o TPM não está disponível:

  ![ID do evento 853](./media/troubleshooting-bitlocker-policies/event-error.png)

  > [!NOTE]
  > Você também pode verificar o status do TPM executando **TPM. msc** no dispositivo.



## <a name="summary"></a>Resumo

Quando você soluciona problemas de política do BitLocker com o Intune e pode confirmar que a política atinge o dispositivo pretendido, é seguro supor que o problema não está diretamente relacionado ao Intune. O problema é mais provável de um problema com o sistema operacional Windows ou o hardware. Nesse caso, comece a procurar outras áreas, como a configuração do TPM, a UEFI e a inicialização segura).

<!-- Unable to Verify this: 
You can try to isolate the issue by enabling BitLocker manually. If you can turn on BitLocker manually, Intune won't be able to turn it on through policy. Also, the Windows Recovery Environment (WinRE) must be enabled on the client for BitLocker to work. When organizations use using custom images, WinRE is a common cause that is often overlooked. 
-->

## <a name="next-steps"></a>Próximos passos  

Veja a seguir mais recursos que podem ajudar quando você trabalha com o BitLocker:

- [Documentação do produto BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Requisitos de sistema do BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview#system-requirements)
- [Perguntas frequentes sobre o BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-frequently-asked-questions)
- [Documentação do CSP do BitLocker](https://docs.microsoft.com/windows/client-management/mdm/bitlocker-csp)
- [Configurações de política de criptografia do Windows Intune](https://docs.microsoft.com/intune/endpoint-protection-windows-10#windows-encryption)
- [Criptografia BitLocker automática independente de hardware usando AAD/MDM](https://blogs.technet.microsoft.com/home_is_where_i_lay_my_head/2017/06/07/hardware-independent-automatic-bitlocker-encryption-using-aadmdm/)
- [Política de CSP para criptografia BitLocker em dispositivos de piloto automático](https://techcommunity.microsoft.com/t5/Windows-10-security/CSP-policy-for-bitLocker-encryption-on-autopilot-devices/m-p/284537)
- [Walkthrough criando e implantando a política do BitLocker com o Intune](https://blogs.technet.microsoft.com/cbernier/2017/07/11/windows-10-intune-windows-bitlocker-management-yes/)