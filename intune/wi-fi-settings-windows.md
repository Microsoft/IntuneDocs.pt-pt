---
title: Definições de Wi-Fi para dispositivos com o Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou crie um perfil de configuração de Wi-Fi com as definições de Wi-Fi para dispositivos com o Windows 10 ou posterior no Microsoft Intune. Pode configurar as Definições básicas ou as definições de nível empresarial.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/30/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.reviewer: tycast
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: e15a7b034c9277fcd960e8c704f4318f0f5c1da2
ms.sourcegitcommit: e814cfbbefe818be3254ef6f859a7bf5f5b99123
ms.translationtype: HT
ms.contentlocale: pt-PT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43329652"
---
# <a name="wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Definições de Wi-Fi para dispositivos com o Windows 10 ou posterior no Intune

As definições de Wi-Fi são utilizadas num perfil de configuração que se aplica a dispositivos com o Windows 10 ou posterior. As suas opções são:

- Básico
- Enterprise

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

## <a name="settings-for-basic-and-enterprise-profiles"></a>Definições para perfis básicos e empresariais

- **Nome do Wi-Fi (SSID)**: sigla de Service Set Identifier (identificador do conjunto de serviço). Este valor é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores só veem o **Nome da ligação** configurado por si quando selecionam a ligação.
- **Nome da ligação**: introduza um nome simples para esta ligação Wi-Fi. O texto que introduziu é o nome que os utilizadores veem quando procuram as ligações disponíveis no respetivo dispositivo.
- **Ligar automaticamente quando estiver ao alcance**: se **Sim**, os dispositivos ligam automaticamente quando estão dentro do alcance desta rede. Se **Não**, os dispositivos não ligam automaticamente.
  - **Ligar à rede mais preferida, se estiver disponível**: se os dispositivos estiverem ao alcance de uma rede mais preferida, selecione **Sim** para utilizar a mesma. Selecione **Não** para utilizar a rede Wi-Fi neste perfil de configuração.

    Por exemplo, cria uma rede Wi-Fi **ContosoCorp** e utiliza a **ContosoCorp** neste perfil de configuração. Também tem uma rede Wi-Fi **ContosoGuest** ao alcance. Quando os seus dispositivos empresariais estiverem ao alcance, pretende que os mesmos liguem automaticamente à **ContosoCorp**. Neste cenário, defina a propriedade **Ligar à rede mais preferida, se estiver disponível** para **Não**.

  - **Ligar a esta rede, mesmo quando não estiver a difundir o seu SSID**: selecione **Sim** para que o perfil de configuração se ligue automaticamente à sua rede, mesmo quando esta estiver oculta (ou seja, o respetivo SSID não está a ser difundido publicamente). Selecione **Não** se não quiser que este perfil de configuração se ligue à sua rede oculta.

- **Definições de Proxy da empresa**: opte por utilizar as definições de proxy na sua organização. As opções são:
  - **Nenhuma**: não são configuradas definições de proxy.
  - **Configurar manualmente**: introduza o **endereço IP do servidor proxy** e o respetivo **Número de porta**.
  - **Configurar automaticamente**: introduza um URL que aponte para um script de configuração automática do proxy (PAC). Por exemplo, introduza `http://proxy.contoso.com/proxy.pac`.

## <a name="settings-for-basic-profiles-only"></a>Definições apenas para perfis básicos

- **Tipo de Segurança sem Fios**: introduza o protocolo de segurança utilizado para autenticar dispositivos na sua rede. As opções são:
  - **Abrir (sem autenticação)**: utilize esta opção apenas se a rede não estiver protegida.
  - **WPA/WPA2-Pessoal**

## <a name="settings-for-enterprise-profiles-only"></a>Definições apenas para perfis empresariais

- **Início de sessão único (SSO)**: permite-lhe configurar o início de sessão único (SSO), onde as credenciais são partilhadas para o início de sessão do computador e da rede Wi-Fi. As opções são:
  - **Desativar**: desativa o comportamento de SSO. O utilizador tem de efetuar a autenticação na rede separadamente.
  - **Ativar antes de o utilizador iniciar sessão no dispositivo**: utilize o SSO para efetuar a autenticação na rede antes do processo de início de sessão de utilizador.
  - **Ativar após o utilizador iniciar sessão no dispositivo**: utilize o SSO para efetuar a autenticação na rede imediatamente após a conclusão do processo de início de sessão de utilizador.
  - **Tempo máximo para autenticar antes do tempo limite**: introduza o número máximo de segundos de espera antes de autenticar na rede, de 1 a 120 segundos.
  - **Permitir que o Windows pergunte ao utilizador credenciais de autenticação adicional**: selecionar **Sim** permite que o sistema Windows peça ao utilizador credenciais adicionais caso o método de autenticação o exija. Selecione **Não** para ocultar estes pedidos.

- **Ativar colocação em cache de chave principal de pares (PMK)**: selecione **Sim** para colocar em cache a PMK utilizada na autenticação. Geralmente, esta colocação em cache permite autenticar a rede de forma a concluir mais rapidamente. Selecione **Não** para forçar o handshake de autenticação sempre que ligar à rede Wi-Fi.

  - **Tempo máximo que um PMK é armazenado na cache**: introduza o número de minutos que a chave principal de pares (PMK) está armazenada em cache, de 5 a 1440 minutos.
  - **Número máximo de PMKs armazenados na cache**: introduza o número de chaves armazenadas em cache, de 1 a 255.

- **Ativar pré-autenticação**: a pré-autenticação permite que o perfil autentique todos os pontos de acesso da rede no perfil antes da ligação. Ao deslocar-se entre pontos de acesso, a pré-autenticação volta a ligar o utilizador ou os dispositivos mais rapidamente. Selecione **Sim** para o perfil autenticar todos os pontos de acesso desta rede que estejam ao alcance. Selecione **Não** para exigir que o utilizador ou dispositivo autentique cada ponto de acesso separadamente.

  - **Máximo de tentativas antes de autenticação**: introduza o número de tentativas para pré-autenticar, de 1 a 16.

- **Tipo de EAP**: selecione o tipo de Protocolo de Autenticação Extensível (EAP) para autenticar as ligações sem fios protegidas. As opções são:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **PEAP Protegido** (PEAP)

    **Definições adicionais de EAP-TLS, EAP-TTLS e PEAP**:
    
    > [!NOTE]
    > Atualmente, apenas os perfis de certificado SCEP são suportados quando utiliza um tipo de EAP. Os perfis de certificado PKCS não são suportados. Sempre que for pedido a um utilizador para introduzir um certificado, certifique-se de que seleciona um certificado SCEP.

      - **Fidedignidade do Servidor**  

        **Nomes de servidores de certificados**: utilize com os tipos EAP **EAP-TLS**, **EAP-TTLS** ou **PEAP**. Introduza um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) confiável. Se introduzir estas informações, pode ignorar a caixa de diálogo de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.  

        **Certificado de raiz para validação do servidor**: utilize com os tipos EAP **EAP-TLS**, **EAP-TTLS** ou **PEAP**. Escolha o perfil de certificado de raiz fidedigna que serve para autenticar a ligação.  

        **Privacidade de identidade (identidade externa)**: utilize com o tipo EAP **PEAP**. Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.  

      - **Autenticação de Cliente**

        **Certificado de cliente para autenticação de cliente (Certificado de identidade)**: utilize com o tipo EAP **EAP-TLS**. Selecione o perfil de certificado utilizado para autenticar a ligação.

        **Método de autenticação**: utilize com o tipo EAP **EAP-TTLS**. Selecione o método de autenticação da ligação:  

          - **Certificados**: selecione o certificado de cliente, ou seja, o certificado de identidade apresentado ao servidor.
          - **Nome de Utilizador e Palavra-passe**: introduza o método de autenticação **Método não EAP (Identidade Interna)**. As opções são:

            - **Palavra-passe não encriptada (PAP)**
            - **Protocolo CHAP (Challenge Handshake)**
            - **Microsoft CHAP (MS-CHAP)**
            - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

        **Privacidade de identidade (identidade externa)**: utilize com o tipo EAP **EAP-TTLS**. Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

- **Forçar o perfil Wi-Fi para que esteja em conformidade com a norma FIPS (Federal Information Processing Standard)**: selecione **Sim** ao validar relativamente à norma FIPS 140-2. Esta norma é necessária para todas as agências governamentais federais dos EUA que utilizem sistemas de segurança baseados em criptografia para proteger informações confidenciais, mas não classificadas, armazenadas digitalmente. Selecione **Não** se não pretender a conformidade com a norma FIPS.

## <a name="use-an-imported-settings-file"></a>Utilizar um ficheiro de definições importadas

Para as definições não disponíveis no Intune, pode exportar definições de Wi-Fi de outro dispositivo com Windows. Esta exportação cria um ficheiro XML com todas as definições. Em seguida, importe este ficheiro para o Intune e utilize-o como o perfil de Wi-Fi. Veja [Exportar e importar definições de Wi-Fi para dispositivos com Windows](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Passos seguintes
[Configurar definições de Wi-Fi no Intune](wi-fi-settings-configure.md)
