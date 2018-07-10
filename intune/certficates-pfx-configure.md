---
title: Utilizar certificados PKCS com o Microsoft Intune – Azure | Microsoft Docs
description: Adicionar ou criar certificados Public Key Cryptography Standard com o Microsoft Intune, incluindo os passos para exportar um certificado de raiz, configurar o modelo de certificado, transferir e instalar o Microsoft Intune Certificate Connector (NDES), criar um perfil de configuração de dispositivo, criar um perfil de Certificado PKCS no Azure e Autoridade de Certificação.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 06/20/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ''
ms.reviewer: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3b3bfe76173eff76a3175952bef5c6e23ad5e429
ms.sourcegitcommit: afda8a0fc0f615e976b18ddddf81d56d7ae3566e
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271546"
---
# <a name="configure-and-use-pkcs-certificates-with-intune"></a>Configurar e utilizar certificados PKCS com o Intune

[!INCLUDE [azure_portal](./includes/azure_portal.md)]

Os certificados são utilizados para autenticar e proteger o acesso aos seus recursos empresariais, tal como uma VPN ou rede Wi-Fi. Este artigo mostra-lhe como exportar um certificado PKCS e, em seguida, adicioná-lo a um perfil do Intune. 

## <a name="requirements"></a>Requisitos

Para utilizar certificados PKCS com o Intune, certifique-se de que tem a seguinte infraestrutura:

- **Domínio do Active Directory**: todos os servidores indicados nesta secção têm de ser associados ao seu domínio do Active Directory.

  Para obter mais informações sobre como instalar e configurar o AD DS, veja [Design e Planeamento do AD DS](https://docs.microsoft.com/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).

- **Autoridade de Certificação** (AC): uma Autoridade de Certificação (AC) Empresarial

  Para obter mais informações sobre como instalar e configurar os Serviços de Certificados do Active Directory (AD CS), veja [Active Directory Certificate Services Step-by-Step Guide (Guia Passo a Passo dos Serviços de Certificados do Active Directory)](https://technet.microsoft.com/library/cc772393).

  > [!WARNING]
  > O Intune requer a execução do AD CS com uma Autoridade de Certificação (AC) Empresarial e não uma AC Autónoma.

- **Um cliente**: para ligar à AC Empresarial

- **Certificado de raiz**: uma cópia exportada do certificado de raiz da AC Empresarial

- **Microsoft Intune Certificate Connector**: utilize o portal do Azure para transferir o instalador do **Certificate Connector** (**NDESConnectorSetup.exe**). 

  O Certificate Connector do NDES também suporta o modo Federal Information Processing Standard (FIPS). O FIPS não é obrigatório, mas pode emitir e revogar certificados quando está ativado.

- **Windows Server**: aloja o Microsoft Intune Certificate Connector (NDESConnectorSetup.exe)

## <a name="export-the-root-certificate-from-the-enterprise-ca"></a>Exportar o certificado de raiz da AC Empresarial

Para autenticar com VPN, Wi-Fi e outros recursos, é necessário um certificado de AC intermédio ou de raiz em cada dispositivo. Os passos seguintes explicam como obter o certificado necessário a partir da AC Empresarial.

1. Inicie sessão na AC Empresarial com uma conta que tenha privilégios administrativos.
2. Abra uma linha de comandos como administrador.
3. Exporte o Certificado da AC de Raiz (.cer) para uma localização onde possa aceder ao mesmo mais tarde.

   Por exemplo:

4. Após o assistente ser concluído, mas antes de o fechar, clique em **Iniciar a IU do Certificate Connector**.

   `certutil -ca.cert certnew.cer`

   Para obter mais informações, veja [Tarefas do certutil para gerir certificados](https://technet.microsoft.com/library/cc772898.aspx#BKMK_ret_sign).

## <a name="configure-certificate-templates-on-the-certification-authority"></a>Configurar modelos de certificado na autoridade de certificação

1. Inicie sessão na AC Empresarial com uma conta que tenha privilégios administrativos.
2. Abra a consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado** e selecione **Gerir**.
3. Localize o modelo de certificado de **Utilizador**, clique com o botão direito do rato no mesmo e selecione **Duplicar Modelo**. As **Propriedades de Novo Modelo** são abertas.
4. No separador **Compatibilidade**:

  - Defina **Autoridade de Certificação** como **Windows Server 2008 R2**
  - Defina **Destinatário do certificado** como **Windows 7/Server 2008 R2**

5. No separador **Geral**, defina o **Nome a apresentar do modelo** para algo que seja relevante para si.

   > [!WARNING]
   > Por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo** *sem espaços*. Anote o nome do modelo, irá precisar dele mais tarde.

6. Em **Processamento de Pedidos**, selecione **Permitir que a chave privada seja exportada**.
7. Em **Criptografia**, confirme se o **Tamanho mínimo da chave** está definido como 2048.
8. Em **Nome do Requerente**, selecione **Fornecer no pedido**.
9. Em **Extensões**, confirme se vê o Sistema de Encriptação de Ficheiros, Proteger o E-mail e Autenticação de Cliente em **Políticas de Aplicações**.

    > [!IMPORTANT]
    > Para os modelos de certificado iOS, aceda ao separador **Extensões**, atualize a **Utilização de Chaves** e confirme que a opção **A assinatura é uma prova de origem** não está selecionada.

10. Em **Segurança**, adicione a Conta de Computador do servidor no local onde irá instalar o Microsoft Intune Certificate Connector. Conceda a esta conta as permissões **Ler** e **Inscrever**.
11. Selecione **Aplicar** e, em seguida, **OK** para guardar o modelo de certificado.
12. Feche a **Consola de Modelos de Certificado**.
13. Na consola **Autoridade de Certificação**, clique com o botão direito do rato em **Modelos de Certificado**, **Novo**, **Modelo de Certificado a Emitir**. Selecione o modelo criado nos passos anteriores e selecione **OK**.
14. Para o servidor gerir os certificados em nome dos utilizadores e dos dispositivos inscritos no Intune, siga estes passos:

    1. Clique com o botão direito do rato na Autoridade de Certificação e escolha **Propriedades**.
    2. No separador de segurança, adicione a Conta de computador do servidor onde executa o Microsoft Intune Certificate Connector. Conceda as permissões **Emitir e Gerir Certificados** e **Pedir Certificados** à conta de computador.

15. Termine a sessão na AC Empresarial.

## <a name="download-install-and-configure-the-certificate-connector"></a>Transferir, instalar e configurar o Certificate Connector

![ConnectorDownload][ConnectorDownload]

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Selecione **Todos os serviços**, filtre por **Intune** e selecione **Microsoft Intune**.
3. Selecione **Configuração do dispositivo** e, em seguida, selecione **Autoridade de Certificação**.
4. Selecione **Adicionar** e **Transferir o ficheiro de Conector**. Guarde a transferência numa localização a que possa aceder a partir do servidor onde irá instalá-la.
5. Após a transferência ser concluída, inicie sessão no servidor. Em seguida:

    1. Certifique-se de que o .NET 4.5 Framework está instalado, pois o Certificate Connector do NDES precisa dele. O .NET 4.5 Framework vem incluído automaticamente com o Windows Server 2012 R2 e versões mais recentes.
    2. Execute o instalador (NDESConnectorSetup.exe) e aceite a localização predefinida. O conector é instalado em `\Program Files\Microsoft Intune\NDESConnectorUI\NDESConnectorUI.exe`. Nas Opções do Instalador, selecione **PFX Distribution** (Distribuição PFX). Continue para concluir a instalação.

6. O Conector do NDES é aberto no separador **Enrollment** (Inscrição). Para ativar a ligação ao Intune, selecione **Sign In** (Iniciar Sessão) e introduza uma conta com permissões administrativas globais.
7. No separador **Avançadas**, deixe a opção **Utilizar a conta SYSTEM deste computador (predefinição)** selecionada.
8. Clique em **Aplicar** e, em seguida, em **Fechar**.
9. Aceda novamente ao portal do Azure (**Intune** > **Configuração do Dispositivo** > **Autoridade de Certificação**). Alguns momentos depois, é apresentada uma marca de verificação verde e o **Connection status** (Estado da ligação) muda para **Active** (Ativo). Agora o servidor do conector pode comunicar com o Intune.

> [!NOTE]
> É incluído suporte para o TLS 1.2 com o Certificate Connector do NDES. Assim, se o servidor com o Certificate Connector do NDES instalado suportar o TLS 1.2, será utilizado o TLS 1.2. Se o servidor não suportar o TLS 1.2, será utilizado o TLS 1.1. Atualmente, é utilizado o TLS 1.1 para a autenticação entre os dispositivos e o servidor.

## <a name="create-a-device-configuration-profile"></a>Criar um perfil de configuração de dispositivos

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Aceda a **Intune** > **Configuração do Dispositivo** > **Perfis** > **Criar perfil**.

   ![NavigateIntune][NavigateIntune]

3. Introduza as seguintes propriedades:

  - O **Nome** do perfil
  - Opcionalmente, defina uma descrição
  - A **Plataforma** na qual vai implementar o perfil
  - Defina o **Tipo de perfil** como **Certificado fidedigno**

4. Aceda às **Definições** e introduza o ficheiro .cer do Certificado da AC de Raiz que exportou anteriormente.

   > [!NOTE]
   > Consoante a plataforma que selecionou no **Passo 3**, poderá ter ou não uma opção para escolher o **Arquivo de destino** do certificado.

   ![ProfileSettings][ProfileSettings]

5. Selecione **OK** e **Criar** para guardar o seu perfil.
6. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](device-profile-assign.md).

## <a name="create-a-pkcs-certificate-profile"></a>Criar um perfil de Certificado PKCS

1. Inicie sessão no [portal do Azure](https://portal.azure.com).
2. Aceda a **Intune** > **Configuração do Dispositivo** > **Perfis** > **Criar perfil**.
3. Introduza as seguintes propriedades:

  - O **Nome** do perfil
  - Opcionalmente, defina uma descrição
  - A **Plataforma** na qual vai implementar o perfil
  - Defina o **Tipo de perfil** como **Certificado PKCS**

4. Aceda a **Definições** e introduza as seguintes propriedades:

  - **Limiar de renovação (%)** – recomenda-se 20%.
  - **Período de validade do certificado** – se não tiver alterado o modelo de certificado, esta opção poderá estar definida como um ano.
  - **Autoridade de certificação** – apresenta o nome de domínio completamente qualificado (FQDN) interno da AC Empresarial.
  - **Nome da autoridade de certificação** – indica o nome da AC Empresarial e pode ser diferente do item anterior.
  - **Nome do modelo de certificado** – o nome do modelo criado anteriormente. Nota: por predefinição, o **Nome do modelo** é igual ao **Nome a apresentar do modelo** *sem espaços*.
  - **Formato do nome do requerente** – defina esta opção como **Nome comum**, exceto se for exigido de outra forma.
  - **Nome alternativo do requerente** – defina esta opção como **Nome principal de utilizador (UPN)**, exceto se for exigido de outra forma.
  - **Utilização de chave alargada** – desde que tenha utilizado as predefinições no Passo 10 da secção [Configurar modelos de certificado na autoridade de certificação](#configure-certificate-templates-on-the-certification-authority) (neste artigo), poderá adicionar os seguintes **Valores predefinidos** na caixa de seleção:
    - **Qualquer Objetivo**
    - **Autenticação de Cliente**
    - **Proteger o E-mail**
  - **Certificado de Raiz** – (para perfis Android) indica o ficheiro .cer exportado no Passo 3 da secção [Exportar o certificado de raiz da AC Empresarial](#export-the-root-certificate-from-the-enterprise-ca) (neste artigo).

5. Selecione **OK** e **Criar** para guardar o seu perfil.
6. Para atribuir o novo perfil a um ou mais dispositivos, veja [Atribuir perfis de dispositivo no Microsoft Intune](device-profile-assign.md).

## <a name="next-steps"></a>Próximos passos
[Utilizar certificados SCEP](certificates-scep-configure.md) ou [emitir certificados PKCS de um serviço Web de gestão de PKI da Symantec](certificates-symantec-configure.md).

[NavigateIntune]: ./media/certificates-pfx-configure-profile-new.png "Navegar para o Intune no portal do Azure e criar um novo perfil para um certificado fidedigno"
[ProfileSettings]: ./media/certificates-pfx-configure-profile-fill.png "Criar um perfil e carregar um certificado fidedigno"
[ConnectorDownload]: ./media/certificates-download-connector.png "Transferir o certificate connector a partir do portal do Azure"  
