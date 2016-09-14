---
title: "Ligações Wi-Fi | Microsoft Intune"
description: "Utilize perfis Wi-Fi para ajudar os utilizadores a ligar às suas redes Wi-Fi."
keywords: 
author: Nbigman
manager: angrobe
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 0b1b86ed-2e80-474d-8437-17dd4bc07b55
ms.reviewer: karanda
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 310a1160d105a80623742ce4e2dc046c670bc167
ms.openlocfilehash: d597cd13bd2254a9303769e2f5d5519c739f0aaf


---

# Configurar dispositivos para ligar às suas redes Wi-Fi empresariais

Utilize os perfis de Wi-Fi do Microsoft Intune para implementar definições de rede sem fios para utilizadores e dispositivos na sua organização. Quando implementa um perfil Wi-Fi, os seus utilizadores terão acesso ao seu Wi-Fi empresarial sem ser necessário serem eles a configurá-lo.

Por exemplo, instala uma nova rede Wi-Fi chamada **Contoso Wi-Fi** e pretende configurar todos os dispositivos iOS para ligarem a esta rede. Eis o processo:

![Resumo do processo de perfil Wi-Fi](..\media\wi-fi-process-diagram.png) 

1.   Crie um perfil de Wi-Fi que contenha as definições necessárias para ligar à rede sem fios **Contoso Wi-Fi**.

2. Implemente o perfil no grupo de utilizadores com dispositivos iOS.

3.   Os utilizadores encontrarão a rede nova **Contoso Wi-Fi** na lista de redes sem fios e conseguirão ligar-se facilmente à mesma.


## Como criar um perfil de Wi-Fi

Pode implementar perfis de Wi-Fi nas seguintes plataformas:

-   Android 4.0 e posterior

-   iOS 7.1 e posterior

-   Mac OS X 10.9 e posterior

Para dispositivos com Windows 8.1 ou Windows 10 Desktop ou Mobile, pode importar um perfil de configuração de Wi-Fi que tenha sido exportado anteriormente para um ficheiro. Para mais detalhes, veja [Exportar ou Importar um perfil de configuração de Wi-Fi para dispositivos Windows](#export-or-import-a-wi-fi-configuration-profile-for-windows-devices).

1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** &gt; ** Adicionar Política**.

2.  Selecione um dos seguintes tipos de política e, em seguida, clique em **Criar Política**:

    -   Perfil de Wi-Fi (Android 4 e posterior)

    -   Perfil de Wi-Fi (iOS 7.1 e posterior)

    -   Perfil de Wi-Fi (Mac OS X 10.9 e posterior)

    Não existem definições recomendadas para este tipo de política. Tem de criar uma política personalizada.

3.  Forneça o nome e uma descrição para o perfil.

4. Especifique os valores de **Ligações de Rede**.
 - **SSID (Service Set Identifier)**: os utilizadores veem o nome da rede, não o SSID.
 - **Ligar mesmo que a rede não esteja a difundir o nome (SSID)**: selecione esta opção para permitir que os dispositivos liguem à rede quando esta não está visível na lista de redes (por estar oculta e sem difundir o respetivo nome).
 
5. Configure as **Definições de Segurança** da plataforma selecionada. As definições disponíveis dependerão dos tipos de segurança que selecionar, e estão descritas em [Definições de segurança](#security-settings).

6. (Apenas iOS e MAC OS X) Configurar **Definições de Proxy**

    |Nome da definição|Mais informações|Utilize se:|
    |----------------|-------------------|-------------|
    |**Definições de proxy desta ligação Wi-Fi**|Selecione o tipo de definições de proxy:<br /><br />-   **Nenhum** (predefinição)<br />-   **Manual** -   Especifique manualmente o URL e o número de porta do servidor proxy.<br />-   **Automático** – Utilize um ficheiro de configuração para configurar o servidor proxy.|Sempre|
    |**Endereço do servidor proxy** e **Número de porta**|Especifique o URL e o número de porta do servidor proxy.|A opção **Definições de proxy desta ligação Wi-Fi** estiver definida como **Manual**|
    |**URL do Servidor Proxy**|Especifique o URL do ficheiro que contém as definições do servidor proxy.|A opção **Definições de proxy desta ligação Wi-Fi** estiver definida como **Automático**|

7.  guardar o perfil de Wi-Fi

A nova política é apresentada no nó **Políticas de Configuração** da área de trabalho **Política**. Consulte **Passos seguintes** para obter informações sobre a implementação do perfil.

## Exportar ou Importar um perfil de configuração de Wi-Fi para dispositivos Windows
 
Para dispositivos com Windows 8.1 ou Windows 10 Desktop ou Mobile, pode importar um perfil de configuração de Wi-Fi que tenha sido exportado anteriormente para um ficheiro. 

### Exportar um perfil de Wi-Fi
No Windows, pode utilizar o utilitário **netsh wlan** para exportar um perfil de Wi-Fi existente para um ficheiro XML, que pode ser lido pelo Intune. Num computador Windows que já tenha o perfil de Wi-Fi necessário instalado, siga este procedimento.

1.  Crie uma pasta local para os perfis Wi-Fi exportados, como c:\WiFi

2.  Abra uma Linha de Comandos como Administrador.

3.  Execute o comando `netsh wlan show profiles` e tome nota do nome do perfil que quer exportar.  Neste exemplo, o nome do perfil é *WiFiName*.

4.  Execute o comando `netsh wlan export profile name="ProfileName" folder=c:\Wifi`. Esta ação irá criar um ficheiro do perfil Wi-Fi com o nome "Wi-Fi-WiFiName.xml na sua pasta de destino".

### Importar um perfil de Wi-Fi
Utilize a **Política de Importação de Wi-Fi do Windows** para importar um conjunto de definições de Wi-Fi que poderá implementar consoante necessário nos grupos de utilizadores ou de dispositivos.


1.  Na [consola de administração do Microsoft Intune](https://manage.microsoft.com), clique em **Política** &gt; ** Adicionar Política**.

2.  Configure uma política do tipo **Windows** &gt; **Política de Importação Wi-Fi (Windows 8.1 e posterior)**.

    Esta política pode ser aplicada a dispositivos Windows 8.1 e Windows 10 Desktop e Mobile.

    Só pode criar e implementar uma política de importação de Wi-Fi do Windows *personalizada*. As definições recomendadas não estão disponíveis.

3.  Especifique os seguintes valores gerais para a Política de Importação de Wi-Fi do Windows:

    |Nome da definição|Mais informações|
    |----------------|--------------------|
    |**Nome**|Introduza um nome exclusivo para o perfil de Wi-Fi para o identificar na consola do Intune.|
    |**Descrição**|Forneça uma descrição do perfil de Wi-Fi e outras informações relevantes que ajudem a localizá-lo.|

4.  Especifique os seguintes valores no cabeçalho **Perfil de Wi-Fi Personalizado**:

    |Nome da definição|Mais informações|
    |----------------|--------------------|
    |**Ficheiro de perfil de configuração**|Clique em **Importar** para selecionar o ficheiro XML que contém as definições de perfil de Wi-Fi a importar para o Intune.|
    |**Nome do perfil de configuração personalizado (apresentado aos utilizadores)**|Mostra o nome do perfil de configuração de Wi-Fi conforme será apresentado aos utilizadores nos respetivos dispositivos.|
    |**Detalhes do perfil de configuração**|Apresenta o código XML do perfil de configuração que selecionou.|

5.  Quando terminar, clique em **Guardar Política**.

6.  A nova política é apresentada no nó **Políticas de Configuração** da área de trabalho **Política** .

## Implementar o perfil

Um perfil é um tipo de política, por isso, utilize a área de trabalho Política para implementá-lo.

1.  Na área de trabalho **Política** , selecione a política que pretende implementar e, em seguida, clique em **Gerir Implementação**.

2.  Na caixa de diálogo **Gerir a Implementação** , para:

    -   **Para implementar a política** - selecione um ou mais grupos nos quais pretende implementar a política e, em seguida, clique em **Adicionar** &gt; **OK**.

    -   **Fechar a caixa de diálogo sem implementar a política** - clique em **Cancelar**.


Um resumo do estado e alertas na página **Descrição Geral** da área de trabalho **Política** identificam problemas com a política que necessitam da sua atenção. Para além disso, é apresentado um resumo de estado na área de trabalho Dashboard.

## Definições de segurança
Estas tabelas incluem os detalhes para as definições de segurança que estão disponíveis para perfis Wi-Fi Android, iOS e Mac OS X. 

### Definições de segurança para dispositivos Android

  |Nome da definição|Mais informações|Utilize se:|
|----------------|--------------------|-------------|
|**Tipo de segurança**|Selecione o protocolo de segurança da rede sem fios:<br /><br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **Sem autenticação (Aberto)** se a rede não for protegida.|Sempre|
|**Tipo EAP**|Selecione o tipo EAP (Protocolo de Autenticação Extensível) utilizado para autenticar as ligações sem fios protegidas:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TTLS**|Tiver selecionado o tipo de segurança **WPA-Enterprise/WPA2-Enterprise**.|
|**Selecionar certificados de raiz para a validação do servidor**|Clique em **Selecionar**e, em seguida, selecione o perfil de certificado de raiz fidedigna utilizado para autenticar a ligação. **Importante:** para criar o perfil de certificado de raiz fidedigna, consulte [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md).|Estiver selecionado qualquer **Tipo EAP** .|
|**Método de autenticação**|Selecione o método de autenticação da ligação:<br /><br />-   **Certificados** para especificar o certificado de cliente<br />-   **Nome de utilizador e Palavra-passe** para especificar um método de autenticação diferente|O **Tipo EAP** é **PEAP** ou **EAP-TTLS**.|
|**Selecionar um método de autenticação não EAP (Identidade interior)**|Selecione a forma como irá autenticar a ligação:<br /><br />-   **Nenhum**<br />-   **Palavra-passe não encriptada (PAP)**<br />-   **CHAP (Challenge Handshake Authentication Protocol)**<br />-   **Microsoft CHAP (MS-CHAP)**<br />-   **Microsoft CHAP Versão 2 (MS-CHAP v2)**<br /><br />As opções disponíveis dependerão do tipo EAP que selecionou.|O **Método de autenticação** for **Nome de Utilizador e Palavra-passe**.|
|**Ativar a privacidade de identidade (Identidade Externa)**|Especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.|O **Tipo EAP** é **PEAP** ou **EAP-TTLS**.|
|**Selecione um certificado de cliente para autenticação de cliente (Certificado de Identidade)**|Clique em **Selecionar**e, em seguida, selecione o perfil de certificado SCEP utilizado para autenticar a ligação. **Importante:** para criar um perfil de certificado SCEP, consulte [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md).|O tipo de segurança for **WPA-Enterprise/WPA2-Enterprise** e estiver selecionado qualquer **Tipo EAP**.|

### Definições de segurança para dispositivos iOS e Mac OS X

  |Nome da definição|Mais informações|Utilize se:|
|----------------|--------------------|-------------|
|**Tipo de segurança**|Selecione o protocolo de segurança da rede sem fios:<br /><br />-   **WPA-Pessoal/WPA2-Pessoal**<br />-   **WPA-Enterprise/WPA2-Enterprise**<br />-   **WEP**<br />-   **Sem autenticação (Aberto)** se a rede não for protegida.|Sempre|
|**Tipo EAP**|Selecione o tipo EAP (Protocolo de Autenticação Extensível) utilizado para autenticar as ligações sem fios protegidas:<br /><br />-   **EAP-TLS**<br />-   **PEAP**<br />-   **EAP-TLS**<br />-   **EAP-AST**<br />-   **LEAP**<br />-   **EAP-SIM**|Tiver selecionado um tipo de segurança **WPA-Enterprise/WPA2-Enterprise**.|
|**Nomes de certificado de servidor fidedigno**|Selecione o perfil de certificado de raiz fidedigna utilizado para autenticar a ligação. **Importante:** para criar o perfil de certificado de raiz fidedigna, consulte [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md).|Tiver selecionado um tipo EAP de **EAP-TLS**, **PEAP**, **EAP-TTLS** ou **EAP-FAST**.|
|**Utilizar PAC (Credencial de Acesso Protegido)**|Selecione para utilizar credenciais de acesso protegido para estabelecer um túnel autenticado entre o cliente e o servidor de autenticação. Se já existir um ficheiro PAC, este será utilizado.|O **Tipo EAP** é **EAP-FAST**.|
|**Aprovisionar PAC**|Aprovisiona os ficheiros PAC para os seus dispositivos.<br /><br />Quando utilizado, também pode selecionar **Aprovisionar PAC Anonimamente** para assegurar que o ficheiro PAC é aprovisionado sem autenticar o servidor.|A opção**Utilizar PAC (Credencial de Acesso Protegido)** estiver selecionada.|
|**Método de autenticação**|Selecione o método de autenticação utilizado na ligação:<br /><br /><ul><li>**Certificados** para especificar o certificado de cliente</li><li>**Nome de Utilizador e Palavra-passe** para especificar um dos seguintes métodos de autenticação não EAP (também conhecido como Identidade interna):<br /><br /><ul><li>**Nenhum**</li><li>**Palavra-passe não encriptada (PAP)**</li><li>**CHAP (Challenge Handshake Authentication Protocol)**</li><li>**Microsoft CHAP (MS-CHAP)**</li><li>**Microsoft CHAP Versão 2 (MS-CHAP v2)**</li><li>**EAP-TLS**</li></ul></li></ul>|O **Tipo EAP** é **PEAP** ou **EAP-TTLS**.|
|**Selecione um certificado de cliente para autenticação de cliente (Certificado de Identidade)**|Selecione o perfil de certificado SCEP utilizado para autenticar a ligação. **Importante:** para criar um perfil de certificado SCEP, consulte [Proteger o acesso a recursos com perfis de certificado](secure-resource-access-with-certificate-profiles.md).|O tipo de segurança for **WPA-Enterprise/WPA2-Enterprise** e o **Tipo EAP** for **EAP-TLS**, **PEAP** ou **EAP-TTLS**.|
|**Ativar a privacidade de identidade (Identidade Externa)**|Especifique o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor.<br /><br />Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.|Se o **Tipo EAP** estiver definido como **PEAP**, **EAP-TTLS** ou **EAP-FAST**.|


### Consulte também
Saiba como criar um perfil Wi-Fi com uma chave pré-partilhada em [Perfil Wi-Fi com chave pré-partilhada](pre-shared-key-wi-fi-profile.md)



<!--HONumber=Sep16_HO1-->


