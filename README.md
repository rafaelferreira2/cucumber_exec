# cucumber_exec
Certamente você já precisou executar um determinado cenário, uma única linha de m um data table com algumas muitas linhas. E oque era preciso? 
Comentar todas as linhas, exceto a do cenário que deseja executar, e realizar a execução pela tag cucumber -t @sua_tag -p seu_profile

Através das configurações apresentadas abaixo, desejo te ajudar a realizar a execução dos seus testes através do VScode de forma mais fácil!

O primeiro passo é instalar a extensão [multi-command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command)
img_1

Após instalada, acesse as configurações do VScode, selecione a opção de editar JSON e adicione o seguinte bloco de código:
img_2
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
img_3

