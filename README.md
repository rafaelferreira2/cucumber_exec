# FACILITANDO A EXECUÇÃO DE TESTES COM CUCUMBER + VSCODE
Certamente você já precisou executar um determinado cenário ou uma única linha de um data table com algumas muitas linhas. E oque era preciso? 
Comentar todas as linhas, exceto a do cenário que deseja executar, para realizar a execução pela tag ```cucumber -t @sua_tag -p seu_profile```

Através das configurações apresentadas abaixo, desejo te ajudar a realizar a execução dos seus testes através do VScode de forma mais fácil!

## CONFIGURAÇÃO
O primeiro passo é instalar a extensão [multi-command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command)


![multi command](https://user-images.githubusercontent.com/32469229/155770845-419582d0-1080-4f13-a854-20646f06d414.png)<br/><br/>

Após instalada, acesse as configurações do VScode, selecione a opção de editar JSON e adicione o seguinte bloco de código:<br/><br/>
![config_1](https://user-images.githubusercontent.com/32469229/155771311-c9588340-f2f6-4013-9d2a-dfde963106e6.png)
![config_2](https://user-images.githubusercontent.com/32469229/155771324-a7b90b91-5123-4e72-93e9-05068c5e50e0.png)


```
    "multiCommand.commands": [
        {
            "command": "multiCommand.executarTag",
            "sequence": [
                {
                    "command" : "workbench.action.terminal.sendSequence",
                    "args" : {"text" : "bundle exec cucumber -t '@${selectedText}' -p seu_profile\u000D"}
                },
                "workbench.action.terminal.focus"
            ]
        },
        {
            "command": "multiCommand.executarLinha",
            "sequence": [
                {
                    "command" : "workbench.action.terminal.sendSequence",
                    "args" : {"text" : "bundle exec cucumber -p seu_profile ${relativeFile}:${lineNumber}\u000D"}
                },
                "workbench.action.terminal.focus"
            ]
          }
    ],
```
Agora é hora de vincular o comando á um atalho!
Acesse as configurações de atalhos de teclado e busque por ```multiCommand.executarTag``` ou ```multiCommand.executarLinha``` e defina o atalho de teclado de sua preferência.
No exemplo abaixo utilizando Mac, configurei como Command + u d

![atalhos](https://user-images.githubusercontent.com/32469229/155771640-92c9634a-c00f-4ead-91a7-aca509f54e82.png)


# UTILIZAÇÃO
Após as configurações realizadas, basta abrir o arquivo .feature que deseja executar e abrir também o terminal integrado do VScode.

## Execução por tag
Para a execução por tag, selecione o texto que deseja executar como tag e pressione o atalho de teclado configurado anteriormente para a execução por tag.

![tag](https://user-images.githubusercontent.com/32469229/155774493-e859ec50-70f0-4849-a680-a85ea7c0d972.png)


## Execução por linha
Para a execução pela linha, clique na linha do data table que deseja executar e pressione o atalho de teclado configurado anteriormente para a execução por linha.

![line](https://user-images.githubusercontent.com/32469229/155774764-f132d383-90b6-4d90-83d6-5dfa7df34e87.png)
