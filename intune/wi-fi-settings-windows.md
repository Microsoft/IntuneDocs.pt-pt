---
title: Definições de Wi-Fi para dispositivos com o Windows 10 no Microsoft Intune – Azure | Microsoft Docs
description: Adicione ou crie um perfil de configuração de Wi-Fi com as definições de Wi-Fi para dispositivos com o Windows 10 ou posterior no Microsoft Intune. Pode configurar as Definições básicas ou as definições de nível empresarial.
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 11/8/2018
ms.topic: reference
ms.prod: ''
ms.service: microsoft-intune
ms.localizationpriority: medium
ms.reviewer: tycast
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 880a81b49a78e7afd83aca510f85133e91416cf4
ms.sourcegitcommit: 143dade9125e7b5173ca2a3a902bcd6f4b14067f
ms.translationtype: MT
ms.contentlocale: pt-PT
ms.lasthandoff: 04/23/2019
ms.locfileid: "61514774"
---
# <a name="add-wi-fi-settings-for-windows-10-and-later-devices-in-intune"></a>Adicionar definições de Wi-Fi para dispositivos Windows 10 e posteriores no Intune

Pode criar um perfil com definições de Wi-Fi específicas e, em seguida, implementar este perfil nos seus dispositivos com o Windows 10 e posterior. O Microsoft Intune oferece muitas funcionalidades, incluindo a autenticação na rede, a utilização de uma chave pré-partilhada e mais.

Este artigo descreve estas definições.

## <a name="before-you-begin"></a>Antes de começar

[Crie um perfil de dispositivo](device-profile-create.md).

## <a name="basic-profile"></a>Perfil básico

- **Tipo de Wi-Fi**: Selecione **Básico**. 

- **Nome do Wi-Fi (SSID)**: Identificador do conjunto de abreviação de serviço. Este valor é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores só veem o **Nome da ligação** configurado por si quando selecionam a ligação.

- **Nome da ligação**: Introduza um nome amigável para esta ligação Wi-Fi. O texto que introduziu é o nome que os utilizadores veem quando procuram as ligações disponíveis no respetivo dispositivo.

- **Ligar automaticamente quando está no intervalo**: Quando **Sim**, dispositivos ligarem automaticamente quando estiverem no intervalo desta rede. Se **Não**, os dispositivos não ligam automaticamente.

  - **Ligar à rede mais preferida, se disponível**: Se os dispositivos estão no intervalo de uma rede mais preferida, em seguida, escolha **Sim** para utilizar a rede preferencial. Selecione **Não** para utilizar a rede Wi-Fi neste perfil de configuração.

    Por exemplo, cria uma rede Wi-Fi **ContosoCorp** e utiliza a **ContosoCorp** neste perfil de configuração. Também tem uma rede Wi-Fi **ContosoGuest** ao alcance. Quando os seus dispositivos empresariais estiverem ao alcance, pretende que os mesmos liguem automaticamente à **ContosoCorp**. Neste cenário, defina a propriedade **Ligar à rede mais preferida, se estiver disponível** para **Não**.

  - **Ligar a esta rede, mesmo quando ele não esteja a difundir o respetivo SSID**: Escolher **Sim** para o perfil de configuração ligar automaticamente à sua rede, mesmo quando a rede está oculta (ou seja, respetivo SSID não estiver a difundir publicamente). Selecione **Não** se não quiser que este perfil de configuração se ligue à sua rede oculta.

- **Limitados de limite de ligações**: Um administrador pode escolher como o tráfego da rede é limitado. Com base nesta definição, as aplicações podem ajustar o respetivo comportamento de tráfego de rede. As opções são:

  - **Sem restrições**: Predefinição. A ligação não é limitada e não há restrições sobre o tráfego.
  - **Foi corrigido**: Utilize esta opção se a rede é configurada com um limite fixo para o tráfego de rede. Uma vez atingido este limite, o acesso à rede será proibido.
  - **Variável**: Utilizar esta opção se o tráfego de rede é cobrado por byte (custo por byte).

- **Tipo de segurança de conexão sem fio**: Introduza o protocolo de segurança utilizado para autenticar dispositivos na sua rede. As opções são:
  - **Abrir (sem autenticação)**: Utilize esta opção apenas se a rede não for protegida.
  - **WPA/WPA2-Personal**: Um mais seguro opção e é geralmente utilizado para conectividade de Wi-Fi. Para obter mais segurança, também pode introduzir uma chave pré-partilhada, palavra-passe ou chave de rede. 

    - **Chave pré-partilhada** (PSK): Opcional. Apresentado quando seleciona **WPA/WPA2-Personal** como o tipo de segurança. Quando a rede da sua organização é configurada, uma chave de rede ou palavra-passe também é configurada. Introduza esta chave de rede ou palavra-passe para o valor PSK. Introduza uma cadeia de carateres que tenha entre 8 e 64 carateres. Se a sua palavra-passe ou chave de rede tiver 64 carateres, introduza os carateres hexadecimais.
    
      > [!NOTE]
      > Ao guardar o perfil Wi-Fi, o valor PSK que introduziu não é apresentado por motivos de segurança. A marca d'água da chave pré-partilhada continua a mostrar a indicação **Não configurado**, apesar de o PSK estar guardado no perfil. Para alterar o PSK, introduza uma nova chave e guarde o perfil. Se guardar o PSK, edite a política, deixe o PSK em branco e o PSK existente continuará a ser utilizado.

- **Definições de Proxy de empresa**: Opte por utilizar as definições de proxy na sua organização. As opções são:
  - **Nenhum**: Não existem definições de proxy estão configuradas.
  - **Configurar manualmente**: Introduza o **o servidor de Proxy IPaddress** e a respetiva **número de porta**.
  - **Configurar automaticamente**: Introduza o URL que aponta para um script de configuração automática (PAC) de proxy. Por exemplo, introduza `http://proxy.contoso.com/proxy.pac`.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e é apresentado na lista de perfis.

## <a name="enterprise-profile"></a>Perfil empresarial

- **Tipo de Wi-Fi**: Escolher **Enterprise**. 

- **Nome do Wi-Fi (SSID)**: Identificador do conjunto de abreviação de serviço. Este valor é o nome real da rede sem fios à qual os dispositivos se ligam. No entanto, os utilizadores só veem o **Nome da ligação** configurado por si quando selecionam a ligação.

- **Nome da ligação**: Introduza um nome amigável para esta ligação Wi-Fi. O texto que introduziu é o nome que os utilizadores veem quando procuram as ligações disponíveis no respetivo dispositivo.

- **Ligar automaticamente quando está no intervalo**: Quando **Sim**, dispositivos ligarem automaticamente quando estiverem no intervalo desta rede. Se **Não**, os dispositivos não ligam automaticamente.
  - **Ligar à rede mais preferida, se disponível**: Se os dispositivos estão no intervalo de uma rede mais preferida, em seguida, escolha **Sim** para utilizar a rede preferencial. Selecione **Não** para utilizar a rede Wi-Fi neste perfil de configuração.

    Por exemplo, cria uma rede Wi-Fi **ContosoCorp** e utiliza a **ContosoCorp** neste perfil de configuração. Também tem uma rede Wi-Fi **ContosoGuest** ao alcance. Quando os seus dispositivos empresariais estiverem ao alcance, pretende que os mesmos liguem automaticamente à **ContosoCorp**. Neste cenário, defina a propriedade **Ligar à rede mais preferida, se estiver disponível** para **Não**.

  - **Ligar a esta rede, mesmo quando ele não esteja a difundir o respetivo SSID**: Escolher **Sim** para o perfil de configuração ligar automaticamente à sua rede, mesmo quando a rede está oculta (ou seja, respetivo SSID não estiver a difundir publicamente). Selecione **Não** se não quiser que este perfil de configuração se ligue à sua rede oculta.

- **Limitados de limite de ligações**: Um administrador pode escolher como o tráfego da rede é limitado. Com base nesta definição, as aplicações podem ajustar o respetivo comportamento de tráfego de rede. As opções são:

  - **Sem restrições**: Predefinição. A ligação não é limitada e não há restrições sobre o tráfego.
  - **Foi corrigido**: Utilize esta opção se a rede é configurada com um limite fixo para o tráfego de rede. Uma vez atingido este limite, o acesso à rede será proibido.
  - **Variável**: Utilizar esta opção se o tráfego de rede é costed por byte.

- **Início de sessão único (SSO)**: Permite-lhe configurar o início de sessão único (SSO), onde as credenciais são partilhadas para o computador e início de sessão de rede Wi-Fi. As opções são:
  - **Desativar**: Desativa o comportamento SSO. O utilizador tem de efetuar a autenticação na rede separadamente.
  - **Ativar antes de utilizador inicia sessão no dispositivo**: Utilize SSO para autenticar para a rede apenas antes do processo de início de sessão do usuário.
  - **Ativar após o utilizador inicia sessão no dispositivo**: Utilize SSO para autenticar-se à rede imediatamente após a conclusão do processo de início de sessão do usuário.
  - **Tempo máximo para autenticar antes do tempo limite**: Introduza o número máximo de segundos a aguardar antes da autenticação para a rede de 1-120 segundos.
  - **Permitir que o Windows para solicitar ao utilizador as credenciais de autenticação adicional**: Escolher **Sim** permite que o sistema do Windows solicitar ao utilizador credenciais adicionais se o método de autenticação exigir. Selecione **Não** para ocultar estes pedidos.

- **Ativar a colocação em cache pairwise master key (PMK)**: Selecione **Sim** para colocar em cache PMK utilizado na autenticação. Geralmente, esta colocação em cache permite autenticar a rede de forma a concluir mais rapidamente. Selecione **Não** para forçar o handshake de autenticação sempre que ligar à rede Wi-Fi.

  - **Tempo máximo de um PMK é armazenado na cache**: Introduza o número de minutos que uma chave mestra pairwise (PMK) é armazenada na cache, de 5-1440 minutos.
  - **Número máximo de PMKs armazenados na cache**: Introduza o número de chaves armazenadas em cache, a partir de 1 a 255.

- **Ativar pré-autenticação**: Pré-autenticação permite que o perfil autenticar a todos os pontos de acesso para a rede no perfil antes de se ligar. Ao deslocar-se entre pontos de acesso, a pré-autenticação volta a ligar o utilizador ou os dispositivos mais rapidamente. Selecione **Sim** para o perfil autenticar todos os pontos de acesso desta rede que estejam ao alcance. Selecione **Não** para exigir que o utilizador ou dispositivo autentique cada ponto de acesso separadamente.

  - **Máximo de tentativas de pré-autenticação**: Introduza o número de tentativas para preauthenticate, a partir de 1-16.

- **Tipo de EAP**: Escolha o tipo de protocolo de autenticação extensível (EAP) para autenticar as ligações sem fios protegidas. As opções são:

  - **EAP-SIM**
  - **EAP-TLS**
  - **EAP-TTLS**
  - **PEAP Protegido** (PEAP)

    **Definições adicionais de EAP-TLS, EAP-TTLS e PEAP**:
    
    > [!NOTE]
    > Atualmente, apenas os perfis de certificado SCEP são suportados quando utiliza um tipo de EAP. Os perfis de certificado PKCS não são suportados. Sempre que for pedido a um utilizador para introduzir um certificado, certifique-se de que seleciona um certificado SCEP.

      - **Fidedignidade do Servidor**  

        **Nomes de servidor de certificado**: Utilizar com o **EAP-TLS**, **EAP-TTLS**, ou **PEAP** tipos de EAP. Introduza um ou mais nomes comuns utilizados em certificados emitidos pela sua autoridade de certificação (AC) confiável. Se introduzir estas informações, pode ignorar a caixa de diálogo de confiança dinâmica apresentada nos dispositivos dos utilizadores quando estes se ligam a esta rede Wi-Fi.  

        **Certificado de raiz para validação do servidor**: Utilizar com o **EAP-TLS**, **EAP-TTLS**, ou **PEAP** tipos de EAP. Escolha o perfil de certificado de raiz fidedigna que serve para autenticar a ligação.  

        **Privacidade de identidade (identidade externa)**: Utilizar com o **PEAP** tipo EAP. Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.  

      - **Autenticação de Cliente**

        **Certificado de cliente para autenticação de cliente (certificado de identidade)**: Utilizar com o **EAP-TLS** tipo EAP. Selecione o perfil de certificado utilizado para autenticar a ligação.

        **Método de autenticação**: Utilizar com o **EAP-TTLS** tipo EAP. Selecione o método de autenticação da ligação:  

          - **Certificados**: Selecione o certificado de cliente que é o certificado de identidade apresentado para o servidor.
          - **Nome de utilizador e palavra-passe**: Introduza um **método não EAP (identidade interna)** método de autenticação. As opções são:

            - **Palavra-passe não encriptada (PAP)**
            - **Protocolo CHAP (Challenge Handshake)**
            - **Microsoft CHAP (MS-CHAP)**
            - **Microsoft CHAP Versão 2 (MS-CHAP v2)**

        **Privacidade de identidade (identidade externa)**: Utilizar com o **EAP-TTLS** tipo EAP. Introduza o texto enviado em resposta a um pedido de identidade EAP. Este texto pode ser qualquer valor. Durante a autenticação, esta identidade anónima é inicialmente enviada, seguida pela identificação verdadeira enviada num túnel seguro.

- **Definições de Proxy de empresa**: Opte por utilizar as definições de proxy na sua organização. As opções são:
  - **Nenhum**: Não existem definições de proxy estão configuradas.
  - **Configurar manualmente**: Introduza o **o servidor de Proxy IPaddress** e a respetiva **número de porta**.
  - **Configurar automaticamente**: Introduza o URL que aponta para um script de configuração automática (PAC) de proxy. Por exemplo, introduza `http://proxy.contoso.com/proxy.pac`.

- **Forçar o perfil de Wi-Fi para estar em conformidade com as Federal Information Processing Standard (FIPS)**: Escolher **Sim** ao validar contra o FIPS 140-2 padrão. Esta norma é necessária para todas as agências governamentais federais dos EUA que utilizem sistemas de segurança baseados em criptografia para proteger informações confidenciais, mas não classificadas, armazenadas digitalmente. Selecione **Não** se não pretender a conformidade com a norma FIPS.

Selecione **OK** > **Criar** para guardar as alterações. O perfil é criado e é apresentado na lista de perfis.

## <a name="use-an-imported-settings-file"></a>Utilizar um ficheiro de definições importadas

Para as definições não disponíveis no Intune, pode exportar definições de Wi-Fi de outro dispositivo com Windows. Esta exportação cria um ficheiro XML com todas as definições. Em seguida, importe este ficheiro para o Intune e utilize-o como o perfil de Wi-Fi. Veja [Exportar e importar definições de Wi-Fi para dispositivos com Windows](wi-fi-settings-import-windows-8-1.md).

## <a name="next-steps"></a>Passos Seguintes

O perfil é criado, mas não faz nada. Em seguida, [atribua este perfil](device-profile-assign.md).

## <a name="more-resources"></a>Mais recursos

- Veja as definições disponíveis para o [Windows 8.1](wi-fi-settings-import-windows-8-1.md).
- [Descrição geral das definições de Wi-Fi](wi-fi-settings-configure.md), incluindo outras plataformas
