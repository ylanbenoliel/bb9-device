# Projeto BB-9 (Robô)

## Dependências
- Tinygo 0.35.0
- Go 1.23.5 (Precisa ser compatível com o tinygo)

**Opcionais:**
- VsCode (Plugin Tinygo)

## Configuração do projeto

O Tinygo necessita de alterar as variáveis de ambiente *GOROOT* e *GOPATH* para seu funcionamento. 

*GOROOT* fica com o retorno da linha *cached GOROOT* do comando:
```shell
tinygo info <placa>
``` 
onde \<placa> é o nome da placa a ser enviada o código.

*GOPATH* fica:
```shell
"$GOPATH:$(which tinygo)"
```

**Obs:** Com o plugin tinygo no code, apertar `ctrl+shift+p`, selecionar tinygo target e procurar pela placa que o plugin faz a alteração das variáveis em `.vscode/settings.json`

## Compilação
```shell
tinygo flash -target=pico -port=/dev/ttyACM0 main.go
```

**Obs:** Caso ocorra um erro de `failed to reset port /dev/ttyACM0: opening port: Permission denied,`, execute um 
```shell
ls -l /dev/ttyACM0
```
Terá uma saída parecida com: `crw-rw---- 1 root grupo 166, 0 Fev 1 16:00 /dev/ttyACM0
`.
Se adicione ao grupo informado no shell. Remova a placa e recarregue o shell. Ao executar o comando anterior novamente, aparecerá `crw-rw-rw-` no início do retorno

