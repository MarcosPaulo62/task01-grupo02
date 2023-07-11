
## Comando GIT SQUASH

Comando "git squash" é usado para combinar vários commits relacionados em um único commit. Ele permite simplificar o histórico de commits, reduzindo o número de commits e tornando o histórico mais limpo e fácil de entender.

#### Funcionamento

O comando "git squash" utiliza o recurso de rebase do Git para fundir commits. Quando você executa o comando, o Git permite que você interaja com uma lista de commits selecionados e especifique a ação a ser realizada para cada um deles. Ao combinar os commits, o Git aplica as alterações de cada commit sequencialmente em relação ao commit anterior, criando um novo commit consolidado.

#### Sintaxe

A sintaxe básica do comando "git squash" é a seguinte:

```
git rebase -i HEAD~<número-de-commits>
```
Substitua <número-de-commits> pelo número de commits consecutivos que você deseja combinar. Por exemplo, se você deseja combinar os últimos três commits, use HEAD~3.

#### Aplicação

O comando "git squash" é útil em várias situações, incluindo:

Organização do histórico de commits: Ao combinar commits relacionados em um único commit, você pode simplificar o histórico e torná-lo mais legível para outros colaboradores do projeto.

Revisão de código: Antes de enviar um pull request ou uma solicitação de mesclagem, você pode usar "git squash" para agrupar commits de uma mesma funcionalidade ou correção de bugs. Isso facilita a revisão do código por outros desenvolvedores.

Correção de commits desnecessários: Se você cometeu commits desnecessários ou fez commits intermediários durante o desenvolvimento de uma funcionalidade, o "git squash" permite que você os combine em um único commit antes de enviar o código para revisão.

#### Nota

É importante ter em mente que o uso do comando "git squash" altera o histórico de commits, portanto, deve ser usado com cautela em repositórios compartilhados ou em branches principais. Recomenda-se criar um branch separado e experimentar o comando antes de aplicá-lo em um ambiente de produção. Além disso, se você já enviou os commits para um repositório remoto, pode ser necessário forçar um push para atualizar o histórico remoto.