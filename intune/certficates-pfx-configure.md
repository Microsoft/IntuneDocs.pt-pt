---
title: Configurar e gerir certificados PKCS com o Intune
titleSuffix: Intune on Azure
description: Crie e atribua certificados PKCS com o Intune."
keywords: 
author: MicrosoftGuyJFlo
ms.author: joflore
manager: angrobe
ms.date: 12/09/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 
ms.reviewer: 
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: a51d260718e0d0c3984966fab69e202b854c1847
ms.sourcegitcommit: b2467a653ffd36c2248a30b69cb88e3dc7cca2ed
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 12/14/2017
---
# <a name="configure-and-manage-pkcs-certificates-with-intune"></a>Configurar e gerir certificados PKCS com o Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

## <a name="requirements"></a>Requisitos

Para utilizar certificados PKCS com o Intune, tem de ter a seguinte infraestrutura:

* Um domínio do Active Directory Domain Services (AD DS) existente configurado.
 
  Se precisar de mais informações sobre como instalar e configurar o AD DS, veja o artigo [AD DS Design and Planning (Design e Planeamento do AD DS)](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

* Uma Autoridade de Certificação (AC) Empresarial existente configurada.

  Se precisar de mais informações sobre como instalar e configurar os Serviços de Certificados do Active Directory (AD CS), veja o artigo [Active Directory Certificate Services Step-by-Step Guide (Guia Passo a Passo dos Serviços de Certificados do Active Directory)](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > O Intune requer a execução do AD CS com uma Autoridade de Certificação (AC) Empresarial e não uma AC Autónoma.

* Um cliente que tenha conetividade com a AC Empresarial.
* Uma cópia exportada do certificado de raiz da AC Empresarial.
* O Microsoft Intune Certificate Connector (NDESConnectorSetup.exe) transferido a partir do Portal do Intune.
* Um Windows Server disponível para alojar o Microsoft Intune Certificate Connector (NDESConnectorSetup.exe).

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportar o certificado de raiz da AC Empresarial

Precisa de um certificado da AC intermediária ou de raiz para a autenticação com a VPN, Wi-Fi e outros recursos. Os passos seguintes explicam como obter o certificado necessário a partir da AC Empresarial.

1. Inicie sessão na AC Empresarial com uma conta que tenha privilégios administrativos.
2. Abra uma linha de comandos como administrador.
3. Exporte o Certificado da AC de Raiz para uma localização onde possa aceder ao certificado mais tarde.

   Por exemplo:

4.  Após o assistente ser concluído, mas antes de o fechar, clique em **Iniciar a IU do Certificate Connector**.

   `certutil -ca.cert certnew.cer`

   Para obter mais informações, veja [Tarefas do certutil para gerir certificados](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configurar modelos de certificado na autoridade de certificação

1. Inicie sessão na AC Empresarial com uma conta que tenha privilégios administrativos.
2. Abra a consola **Autoridade de Certificação**.
3. Clique com botão direito do rato em **Modelos de Certificado** e escolha **Gerir**.
4. Localize o modelo de certificado de **Utilizador**, clique com o botão direito do rato nele e escolha **Duplicar Modelo**. Será apresentada a janela **Propriedades de Novo Modelo**.
5. No separador **Compatibilidade**
   * Defina **Autoridade de Certificação** como **Windows Server 2008 R2**
   * Defina **Destinatário do certificado** como **Windows 7/Server 2008 R2**
6. No separador **Geral**:
   * Defina **Nome a apresentar do modelo** para algo significativo para si.

   > [!WARNING]
   > Por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo** *sem espaços*. Tome nota do nome de modelo para utilização posterior.

7. Clique no separador **Processamento de Pedidos** e selecione a caixa **Permitir que a chave privada seja exportada**.
8. No separador **Criptografia**, confirme se o **Tamanho mínimo da chave** está definido como 2048.
9. No separador **Nome do Requerente**, escolha o botão de opção **Fornecer no pedido**.
10. No separador **Extensões**, confirme se vê o Sistema de Encriptação de Ficheiros, Proteger o E-mail e Autenticação de Cliente em **Políticas de Aplicações**.
    
      > [!IMPORTANT]
      > Para os modelos de certificado iOS e macOS, no separador **Extensões**, edite **Utilização de Chave** e confirme que a opção **A assinatura é uma prova de origem** não está selecionada.

11. No separador **Segurança**, adicione a Conta de Computador do servidor no local onde vai instalar o Microsoft Intune Certificate Connector.
    * Conceda a esta conta as permissões **Ler** e **Inscrever**.
12. Clique em **Aplicar** e em **OK** para guardar o modelo de certificado.
13. Feche a **Consola de Modelos de Certificado**.
14. Na consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado**, **Novo**, **Modelo de Certificado a Emitir**.
    * Escolha o modelo criado nos passos anteriores e clique em **OK**.
15. Para o servidor gerir os certificados em nome dos utilizadores e dos dispositivos inscritos no Intune, siga estes passos:

    a. Clique com o botão direito do rato na Autoridade de Certificação e escolha **Propriedades**.

    b. No separador de segurança, adicione a Conta de computador do servidor onde executa o Microsoft Intune Certificate Connector.
      * Conceda as permissões **Emitir e Gerir Certificados** e **Pedir Certificados** à conta de computador.
16. Termine a sessão na AC Empresarial.

## <a name="download-install-and-configure-the-microsoft-intune-certificate-connector"></a>Transferir, instalar e configurar o Microsoft Intune Certificate Connector

![ConnectorDownload][ConnectorDownload]

1. No portal do Azure, selecione **Mais Serviços** > **Monitorização + Gestão** > **Intune**.
2. No painel do **Intune**, selecione **Configuração do Dispositivo**. 
3. No painel **Configuração do Dispositivo**, selecione **Autoridade de Certificação**. 
4. Clique em **Adicionar** e selecione **Transferir o ficheiro de Conector**. Guarde a transferência numa localização a que possa aceder a partir do servidor onde irá instalá-la. 
5.  Inicie sessão no servidor onde vai instalar o Microsoft Intune Certificate Connector.
6.  Execute o instalador e aceite a localização predefinida. Instala o conector em C:\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe.
    1. Na página Opções do Instalador, escolha **PFX Distribution** e clique em **Seguinte**.
    2. Clique em **Instalar** e aguarde pela conclusão da instalação.
    3. Na página de conclusão, selecione a caixa com a etiqueta **Iniciar o Conector do Intune** e clique em **Concluir**.
7.  Agora a janela do Conector do NDES deve abrir no separador **Inscrição**. Para ativar a ligação ao Intune, clique em **Iniciar sessão** e indique uma conta com permissões administrativas.
8.  No separador **Avançadas**, pode deixar o botão de opção **Utilizar a conta SYSTEM deste computador (predefinição)** selecionada.
9.  Clique em **Aplicar** e em **Fechar**.
10. Agora volte ao portal do Azure. Após alguns minutos, deverá ver uma marca de verificação verde e a palavra **Ativo**, em **Estado da ligação**, em **Intune** > **Configuração do Dispositivo** > **Autoridade de Certificação**. Esta confirmação permite-lhe saber que o servidor do conector consegue comunicar com o Intune.


## <a name="create-a-device-configuration-profile"></a>Criar um perfil de configuração de dispositivos

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Navegue para **Intune**, **Configuração do dispositivo**, **Perfis** e clique em **Criar perfil**.

   ![NavigateIntune][NavigateIntune]

3. Introduza as seguintes informações:
   * O **Nome** do perfil
   * Opcionalmente, defina uma descrição
   * A **Plataforma** na qual vai implementar o perfil
   * Defina o **Tipo de perfil** como **Certificado fidedigno**
4. Navegue para **Definições** e carregue o ficheiro .cer do Certificado da AC de Raiz exportado anteriormente.

   > [!NOTE]
   > Consoante a plataforma que selecionou no **Passo 3**, poderá ter ou não uma opção para escolher o **Armazenamento de destino** do certificado.

   ![ProfileSettings][ProfileSettings]

5. Clique em **OK** e em **Criar** para guardar o perfil.
6. Para atribuir o novo perfil a um ou mais dispositivos, veja [Como atribuir perfis de dispositivo do Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Criar um perfil de Certificado PKCS

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Navegue para **Intune**, **Configuração do dispositivo**, **Perfis** e clique em **Criar perfil**.
3. Introduza as seguintes informações:
   * O **Nome** do perfil
   * Opcionalmente, defina uma descrição
   * A **Plataforma** na qual vai implementar o perfil
   * Defina o **Tipo de perfil** como **Certificado PKCS**
4. Navegue para **Definições** e indique as seguintes informações:
   * **Limiar de renovação (%)** – recomenda-se 20%.
   * **Período de validade do certificado** – se não tiver alterado o modelo de certificado, esta opção deverá ser definida como um ano.
   * **Autoridade de certificação** – esta opção é o nome de domínio completamente qualificado (FQDN) interno da AC Empresarial.
   * **Nome da autoridade de certificação** – esta opção é o nome da AC Empresarial e poderá ser diferente do item anterior.
   * **Nome do modelo de certificado** – esta opção é o nome do modelo criado anteriormente. Nota: por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo** *sem espaços*.
   * **Formato do nome do requerente** – defina esta opção como **Nome comum**, exceto se for exigido de outra forma.
   * **Nome alternativo do requerente** – defina esta opção como **Nome principal de utilizador (UPN)**, exceto se for exigido de outra forma.
   * **Utilização alargada da chave** – desde que tenha utilizado as predefinições no Passo 10 da secção anterior **Configurar modelos de certificado na autoridade de certificação**, poderá adicionar os seguintes **Valores predefinidos** na caixa de seleção:
      * **Qualquer Objetivo**
      * **Autenticação de Cliente**
      * **Proteger o E-mail**
   * **Certificado de Raiz** – (para perfis Android) esta opção é o ficheiro .cer exportado no Passo 3 da secção anterior [Exportar o certificado de raiz da AC Empresarial](#export-the-root-certificate-from-the-enterprise-ca).

5. Clique em **OK** e em **Criar** para guardar o perfil.
6. Para atribuir o novo perfil a um ou mais dispositivos, veja o artigo [Como atribuir perfis de dispositivo do Microsoft Intune](device-profile-assign.md).


[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navegar para o Intune no portal do Azure e criar um novo perfil para um certificado fidedigno"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Criar um perfil e carregar um certificado fidedigno"
[ConnectorDownload]: ./media/certificates-download-connector.png "Transferir o certificate connector a partir do portal do Azure"  
