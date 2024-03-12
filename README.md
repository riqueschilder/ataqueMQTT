## Perguntas - Roteiro

1. **O que acontece se você utilizar o mesmo ClientID em outra máquina ou sessão do browser? Algum pilar do CIA Triad é violado com isso?**

    **Resposta:** Quando um mesmo ClientID é utilizado em outra máquina ou sessão do navegador, o cliente é desconectado da sessão anterior e conectado à nova sessão. Essa ação viola o pilar da disponibilidade, uma vez que o cliente é desconectado sem aviso prévio, afetando a capacidade do sistema em estar disponível para os usuários.

2. **Com os parâmetros de recursos, algum pilar do CIA Triad pode ser facilmente violado?**

    **Resposta:** Sim, ao configurar os parâmetros de recursos, como na especificação fornecida, o pilar da disponibilidade pode ser facilmente violado. O container pode ser derrubado por falta de recursos em uma eventual sobrecarga de mensagens, comprometendo a disponibilidade do sistema. Além disso, a conexão sem TLS prejudica o pilar de confidencialidade, expondo o sistema a ataques como MitM (Man-in-the-Middle), spoofing e eavesdropping.

3. **Já tentou fazer o Subscribe no tópico #? (sim, apenas a hashtag). O que acontece?**

    **Resposta:** Ao realizar o Subscribe no tópico '#', está sendo utilizado um wildcard multi-level, que permite inscrever-se em todos os tópicos disponíveis. Isso pode ser perigoso, pois viola a confidencialidade das mensagens, expondo potencialmente informações sensíveis transmitidas nos tópicos.

4. **Sem autenticação (repare que a variável allow_anonymous está como true), como a parte de confidencialidade pode ser violada?**

    **Resposta:** A falta de autenticação permite que qualquer pessoa se conecte ao broker e leia mensagens de qualquer tópico, comprometendo assim a confidencialidade das mensagens. Além disso, a integridade também é violada, pois qualquer pessoa pode publicar mensagens em qualquer tópico, o que pode levar à adulteração dos dados transmitidos.

## Perguntas - Dev


1. **Como você faria para violar a confidencialidade?**

    **Resposta:** Para violar a confidencialidade, poderia-se inscrever em tópicos que transitam informações sensíveis, aproveitando a falta de uma lista de controle de acesso (ACL) para limitar o acesso a tópicos específicos. Obtendo credenciais de acesso, seria possível publicar e ler mensagens em tópicos restritos. A conexão sem TLS também poderia ser interceptada, expondo dados em tráfego e comprometendo o sistema.

2. **Como você faria para garantir a integridade do broker MQTT?**

    **Resposta:** Para garantir a integridade dos dados, além de credenciais de acesso, seria essencial implementar uma lista de controle de acesso (ACL) para tópicos específicos. Isso limitaria quem pode publicar mensagens em quais tópicos, protegendo a integridade dos dados contra adulteração não autorizada.

3. **Como você faria para violar o pilar de disponibilidade?**

    **Resposta:** Para violar o pilar de disponibilidade, poder-se-ia explorar a permissão de escrita nos arquivos de configuração do broker, permitindo alterações maliciosas. Isso incluiria sobrescrever arquivos de configuração para permitir acesso anônimo, realizar ataques de negação de serviço (DoS) enviando mensagens em massa, ou até mesmo apagar dados essenciais do sistema. Medidas de segurança, como limitar o acesso do container ao host e implementar perfis de segurança, seriam cruciais para mitigar esses riscos.

