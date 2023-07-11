# task01-grupo02
Primeira task do Vem Ser DBC (git)

# GRUPO 02 
## Documentação do Git

[![Git](https://git-scm.com/images/logos/1color-orange-lightbg@2x.png)](https://git-scm.com/doc)


## Comando GIT REBASE

O comando git rebase é utilizado para integrar mudanças de um branch para outro, aplicando uma série de commits. Ele permite modificar o histórico de commits, movendo, combinando ou excluindo commits. O rebase é comumente usado para manter um histórico de commits limpo e linear ao trabalhar com branches de funcionalidades.

#### Funcionamento
O comando git rebase move os commits de um branch para outro, alterando a base desses commits. Isso significa que o branch de destino terá uma nova base, que é o commit mais recente do branch de origem. O rebase reaplica os commits do branch de origem no topo do branch de destino, um por um, mantendo a ordem cronológica dos commits.

Durante o rebase, o Git compara as alterações introduzidas por cada commit do branch de origem e tenta aplicá-las no branch de destino. Se houver conflitos, o Git pausa o processo de rebase para que o usuário possa resolvê-los manualmente.

#### Sintaxe
A sintaxe básica do comando **'git rebase'** é a seguinte:

```
git rebase [opções] <branch>
```
**[opções]**: São opções adicionais que podem ser especificadas, como **-i** para o modo interativo ou **--onto <new_base>** para definir uma nova base para o rebase.
**<branch>**: É o branch do qual você deseja integrar as mudanças.

#### Aplicação
Aqui estão os passos básicos para utilizar o comando git rebase:

Alterne para o branch de destino:

```
git checkout <branch>
```
Execute o comando de rebase, especificando o branch de origem:

```
git rebase <branch_origem>
```

Após executar esses passos, o Git irá aplicar os commits do branch de origem no branch de destino, um por um. Se houver conflitos, o Git irá pausar o rebase e você deverá resolvê-los manualmente.

#### Nota
É importante lembrar que o rebase modifica o histórico de commits e pode causar problemas se usado incorretamente. Portanto, é recomendado utilizá-lo com cautela e entender as possíveis consequências antes de executá-lo.
  
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