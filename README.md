# Como usar sua conta do YouTube Premium para não ver anúncios nos Embeds do Discord

Nos últimos meses, os anúncios nos Embeds do YouTube se tornaram cada vez mais frequentes e incômodos. Felizmente, existe uma maneira fácil e eficaz de conectar sua conta do YouTube Premium ao Discord para bloquear todos esses anúncios. Com isso, você pode curtir seus vídeos sem interrupções, tanto nos chats quanto no Watch Together com seus amigos, garantindo uma experiência mais tranquila e divertida.

Falando tecnicamente, achei uma forma de configurar o Discord para abrir qualquer site na janela do aplicativo, usando um parâmetro chamado `"WEBAPP_ENDPOINT"`. Assim podemos acessar a página de login do YouTube e linkar a conta do Discord com o YouTube Premium.

Veja o vídeo caso o texto não tenha ficado claro: https://youtu.be/iQ7GatyWfpg

## 1. Pegar o link de login do YouTube

Como a janela do Discord tem algumas limitações, você não consegue clicar diretamente em links. Por isso, vamos usar um link direto para facilitar o processo e garantir que tudo funcione. e, por isso, precisa do link que te leve diretamente para a página de login do Google.

1. Abra uma aba anônima no seu navegador favorito *(No Google Chrome e Edge, você pode utilizar o atalho CTRL+SHIFT+N)*;
2. Digite o endereço `youtube.com` e aperte "Enter";
3. Clique sobre o *botão de Login* localizado no canto superior direito da tela;
4. Será aberta a tela de login do Google. Copie o URL da barra de endereços;
5. Feche o navegador; não precisaremos mais dele.

## 2. Editar o arquivo de configurações do Discord

Agora que temos o link de login, precisamos configurar o parâmetro `"WEBAPP_ENDPOINT"` dentro do arquivo de configurações do Discord, localizado na pasta `C:\Users\nome\AppData\Roaming\discord\`.

*Se você estiver utilizando o Discord PTB ou o Canary, haverá pastas com os respectivos nomes dentro do diretório Roaming.*

O jeito mais fácil de acessar o diretório de configuração é digitar `%appdata%` na barra de busca do Windows e apertar Enter. A partir daí, navegue até a pasta do Discord.&#x20;

1. Aperte a tecla "Windows" no seu teclado;
2. Digite `%appdata%` e aperte Enter.

## 3. Editar o arquivo *settings.json*

Chegou a hora de configurar o parâmetro dentro do arquivo de configurações do Discord. Você encontrará este arquivo na pasta que acabou de acessar, com o nome `settings.json`. Você pode usar qualquer editor de texto; eu recomendo o *Bloco de Notas do Windows*.

> Antes de continuar, garanta que o Discord está com a janela maximizada, ocupando o máximo do seu monitor. Em seguida, feche-o clicando no "X". Verifique na bandeja do sistema se ele ainda está aberto. Se estiver, clique com o botão direito do mouse no ícone e escolha `Quit Discord`.

1. Localize o arquivo `settings.json`, clique com o botão direito do mouse sobre ele e selecione para editar no Bloco de Notas;
2. Adicione uma vírgula na última linha antes do fechamento das chaves `}`;
3. Adicione uma nova linha antes do fechamento das chaves `}` com o texto `"WEBAPP_ENDPOINT": "URL_QUE_VOCE_COPIOU"`;
4. Substitua *URL\_QUE\_VOCE\_COPIOU* pelo texto que você copiou da barra de endereços do navegador;

> Atenção à formatação para evitar corromper o arquivo. Não esqueça das aspas duplas no nome do parâmetro e no URL que você substituiu. Também não esqueça da vírgula na linha acima.

5. Salve o arquivo em `Arquivo > Salvar` ou usando o atalho `CTRL+S`;
6. Feche o Bloco de Notas.

O arquivo deve ficar parecido com este exemplo abaixo:

```
{
  "BACKGROUND_COLOR": "#202225",
  "IS_MAXIMIZED": false,
  "IS_MINIMIZED": true,
  "WINDOW_BOUNDS": {
    "x": 160,
    "y": 78,
    "width": 1130,
    "height": 692
  },
  "OPEN_ON_STARTUP": false,
  "MINIMIZE_TO_TRAY": true,
  "chromiumSwitches": {},
  "audioSubsystem": "experimental",
  "useLegacyAudioDevice": false,
  "WEBAPP_ENDPOINT": "https://accounts.google.com/v3/signin/identifier..."
}
```

## 4. Realizar login com sua conta do Google

Ao abrir o Discord, você verá o login do Google - estamos quase lá! Faça login com a conta que possui a assinatura do YouTube Premium.

Este passo envolve apenas digitar seu e-mail e senha, realizar a verificação em duas etapas e torcer para dar certo.

Após o login, você será redirecionado para o YouTube. Caso tenha mais de um canal, será exibida a janela para selecionar o canal que armazenará o histórico de visualização dos vídeos.

Selecione a opção para não perguntar novamente qual canal utilizar e dê dois cliques no nome do canal desejado.

> Devido à limitação mencionada anteriormente sobre links, ao clicar no nome do canal nada parecerá acontecer, mas a configuração ficará salva. 

Para fechar o a janela é preciso recorrer ao icone na bandeja do sistema, clique com o botão direito do mouse no ícone e escolha \`Quit Discord\`.

## 5. Desfazer modificação no arquivo de configurações

Agora que você fez login com sucesso no YouTube, é necessário remover o parâmetro `WEBAPP_ENDPOINT` da configuração do Discord.

1. Reabra o arquivo `settings.json`, clicando com o botão direito do mouse sobre ele e selecionando para editar no Bloco de Notas;
2. Apague tudo que você adicionou anteriormente. Certifique-se de remover a vírgula na linha anterior ao `WEBAPP_ENDPOINT`;
3. Salve o arquivo indo em `Arquivo > Salvar` ou usando o atalho `CTRL+S`;
4. Feche o Bloco de Notas.

O arquivo deve voltar a ser igual ao exemplo abaixo. Você pode copiá-lo se preferir:

```
{
  "BACKGROUND_COLOR": "#202225",
  "IS_MAXIMIZED": false,
  "IS_MINIMIZED": true,
  "WINDOW_BOUNDS": {
    "x": 160,
    "y": 78,
    "width": 1130,
    "height": 692
  },
  "OPEN_ON_STARTUP": false,
  "MINIMIZE_TO_TRAY": true,
  "chromiumSwitches": {},
  "audioSubsystem": "experimental",
  "useLegacyAudioDevice": false
}
```

## 6. Abrir o Discord novamente

Pronto! Agora, ao abrir o Discord, você pode aproveitar uma experiência muito mais fluida, sem os incômodos dos anúncios nos vídeos. Divirta-se assistindo e interagindo sem interrupções!

Essa solução tem funcionado perfeitamente por meses. Imagino que eventualmente será preciso fazer o processo de login novamente.

Ainda não testei no Linux, mas há grandes chances de funcionar se você localizar o arquivo correspondente.&#x20;

