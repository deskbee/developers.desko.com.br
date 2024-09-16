# Slack

## Comandos e Operações

1. No **App** **Desko Slack** existem dois conceitos básicos que precisamos entender:
   1. **Comandos:** São os básicos de uso do slack, todos os aplicativos no slack possuem ao menos um comando para o usuário interagir, é através dos comandos que será possível realizar ações no **App Desko Slack;**
   2. **Operações:** São através delas que você poderá solicitar o que deseja fazer, as **operações** são como **argumentos** e normalmente estarão em conjunto com os comandos.
2. A estrutura base de uso do slack é **/comando operação**, um exemplo disto é quando queremos reservar uma estação de trabalho e para isso basta digitar: **/book mesa ou /book estação de trabalho**.
3. Existem alguns feedbacks que o **App Desko Slack** retorna ao usuário e um deles é quando tenta realizar alguma operação que não existe, como por exemplo, **/book uma operação qualquer,** se você copiar este trecho e colar em seu canal **(após realizar a integração)** provavelmente você receberá um retorno de que esta operação não existe, conforme as imagens abaixo.

![](<../.gitbook/assets/2 (2).png>)

1. Outra observação que devemos considerar é a **multilinguagem**, os comandos por padrão serão sempre em inglês já as operações podem ser na língua que o usuário escolher, ou seja, se o idioma escolhido no painel **(vide a seção Ajuste de Idioma)** for inglês, e no app digitarmos o comando **/book estação de trabalho**, você irá receber o retorno de que esta operação não existe pois está esperando que escreva a operação em inglês, **/book workspace**.
2. No **App Desko Slack** existe um comando que pode ser usado como **Helper** quando não se sabe os comandos/operações disponíveis, estas informações podem ser encontradas na **Página Inicial do App Desko Slack,** como pode ver na imagem abaixo, porém existe também o comando **/desko** que quando usado sem a operação, pode retornar uma mensagem de boas vindas sugerindo algumas ações, e se usado juntamente com a operação **lista de comandos (em portugues)** vai retornar a lista de comandos e operações disponíveis.

![](<../.gitbook/assets/3 (2).png>)

##

## Acessando o Painel

1. Acesse o painel do Desko com um usuário **Admin** ou **Master.**
2. Navegue até **Integrações -> Comunicação** no menu lateral e verá a tela abaixo.

![](<../.gitbook/assets/4 (2).png>)

## Iniciando a Integração:

1. Primeiro habilite a integração no botão **Toggle** que está no canto direito da tela.
2. Logo após, pressione o botão iniciar a integração e você será redirecionado para a tela de permissões do Slack.

![](<../.gitbook/assets/5 (2).png>)

## Testando a Integração:

1. Após aceitar (ou cancelar) as permissões vai abrir uma tela de sucesso (ou uma mensagem informando o cancelamento) da integração.
2. Após isto você pode abrir seu Slack e visualizar que o Aplicativo foi adicionado e um atalho estará disponível

![](<../.gitbook/assets/6 (2).png>)

1. Dentro do seu workspace, navegue até o aplicativo e acesse sua **página inicial** e verá a seguinte imagem:

![](<../.gitbook/assets/7 (2).png>)

1. Repare que na lista de **Apps** no canto esquerdo da tela está o atalho do **Desko** selecionado, isto acontece pois ao finalizar a integração automaticamente ele será adicionado lá, **com exceção nos casos em que um administrador não permite o atalho automático ou a lista de aplicativos está cheia, porém você poderá acessar o atalho do Desko também pela lista de aplicativos, como mostra a imagem abaixo:**

![](<../.gitbook/assets/8 (2).png>)

1. E com a integração feita você pode usá-lo em seus **canais públicos, privados, conversa um-a-um ou na própria home do aplicativo.**

![](<../.gitbook/assets/9 (2).png>)

## Ajuste de Idioma:

1. O aplicativo do **Desko Slack** possui ajuste de **linguagem** de acordo com a conta do **Desko Painel**, ou seja, se precisar trocar o idioma do **Desko Slack** isto pode ser facilmente feito pelo **Painel,** para isto vá até **Configurações -> Aplicativo -> Idioma e Região Padrão** e selecione o idioma.

![](<../.gitbook/assets/10 (2).png>)

1. O painel está configurado para **Portugues** e o **App no Slack está em Portugues.**

![](<../.gitbook/assets/11 (2).png>)

## Ativar/Desativar Integração:

1. Também é possível desativar uma **integração** já feita no painel, isto faz com que a integração fique em estado **“desativada”** ou **“ativada”** mas sem perder o fluxo de integração em si.
2. **Integração Desativada:**

![](<../.gitbook/assets/12 (2).png>)

![](<../.gitbook/assets/13 (2).png>)

![](<../.gitbook/assets/14 (2).png>)

1. **Integração Ativada:**

![](<../.gitbook/assets/15 (1).png>)

**Seja Feliz :)**

## Versionamento

| **Versão** | **Author**   | **Data**   |
| ---------- | ------------ | ---------- |
| v1.0       | Jean Nícolas | 14/07/2021 |
