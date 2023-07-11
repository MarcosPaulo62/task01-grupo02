
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




## NOME REVERT

git-revert - Reverte alguns commits existentes

## RESUMO

```
git revert [--[no-]edit] [-n] [-m parent-number] [-s] [-S[<keyid>]] <commit>…
git revert (--continue | --skip | --abort | --quit)
```

## DESCRIÇÃO

Dado um ou mais commits já existentes, reverta as alterações introduzidas pelos patches relacionados e registre alguns novos commits que registram neles. Isso requer que a sua árvore de trabalho esteja limpa (nenhuma alteração a partir do commit `HEAD`).

Nota: *git revert* é utilizado para registrar alguns commits novos para reverter o efeito de alguns commits anteriores (geralmente apenas um com problema). Caso queira descartar todos os commits das alterações que não foram aplicados no seu diretório de trabalho, você deve consultar [git-reset[1\]](https://git-scm.com/docs/git-reset/pt_BR), em particular a opção `--hard`. Caso queira extrair arquivos específicos da maneira que eles estavam em um outro commit, você deve consutar [git-restore[1\]](https://git-scm.com/docs/git-restore/pt_BR), principalmente a opção `--source`. Tenha cuidado com ambas alternativas pois elas descartam qualquer modificação não aplicada no seu diretório de trabalho.

Para as diferenças entre os três comandos consulte "Redefinir, restaurar e reverter" em [git[1\]](https://git-scm.com/docs/git/pt_BR).

## OPÇÕES

- <commit>…

  Commits que serão revertidos. Para obter uma lista mais completa das maneiras de como soletrar os nomes dos commits, consulte [gitrevisions[7\]](https://git-scm.com/docs/gitrevisions/pt_BR) Um conjunto de commits também podem ser informados porém nenhuma travessia é feita por padrão, consulte [git-rev-list[1\]](https://git-scm.com/docs/git-rev-list/pt_BR) e a sua opção `--no-walk`.

- -e

- --edit

  Com esta opção, o comando *git revert* permitirá a edição da mensagem do commit antes de fazer a reversão do commit. Esta é a predefinição caso execute o comando em um terminal.

- -m parent-number

- --mainline parent-number

  Geralmente, você não pode reverter uma mesclagem porque não sabe qual o lado da mesclagem deve ser considerado a linha principal. Esta opção determina o número do pai (começando em 1) da linha principal e permite que a reversão reverta a alteração em relação ao pai informado.A reversão da mesclagem de um commit declara que você nunca vai querer que as alterações na árvore sejam trazidas pela mesclagem. Como resultado, as mesclagens posteriores trarão apenas as alterações na árvore introduzidas pelos commits que não sejam os ancestrais da mesclagem revertida anteriormente. Isso pode ou não ser o que você queira.Consulte o [Como fazer um *revert-a-faulty-merge*](https://git-scm.com/docs/howto/revert-a-faulty-merge/pt_BR) para mais detalhes.

- --no-edit

  Com esta opção, o comando *git revert* não iniciará o editor das mensagens do commit.

- --cleanup=<modo>

  Essa opção define como a mensagem de commit sera limpa antes de ser encaminhada para o maquinário de commit. Para mais detalhes consulte [git-commit[1\]](https://git-scm.com/docs/git-commit/pt_BR). Em particular, caso o valor *<mode>* tenha um valor de tesoura `scissors`, a tesoura será anexada a `MERGE_MSG` antes de ser repassada no caso de um conflito.

- -n

- --no-commit

  Geralmente, o comando cria automaticamente alguns commits com mensagens no registro log informando quais commits foram revertidos. Esta opção aplica as alterações necessárias para reverter os commits informados para a sua árvore de trabalho e o índice, mas não faz os commits. Além disso, quando esta opção é utilizada, o seu índice não precisa coincidir ao HEAD do commit. A reversão é feita na condição inicial do seu índice.Isso é útil durante ao reverter o efeito de um ou mais commits no seu índice, em uma linha.

- -S[<keyid>]

- --gpg-sign[=<keyid>]

- --no-gpg-sign

  Commits assinados com o GPG O argumento `keyid` é opcional e a predefinição retorna para a identidade de quem fez o commit; caso seja utilizado, deve estar anexado a opção e sem espaço. A opção `--no-gpg-sign` é útil para revogar a variável de configuração `commit.gpgSign` e a anterior `--gpg-sign`.

- -s

- --signoff

  Adicione uma linha de assinatura no final da mensagem do commit. Para mais informações, consulte a opção *signoff* em [git-commit[1\]](https://git-scm.com/docs/git-commit/pt_BR).

- --strategy=<estratégia>

  Use a estratégia de mesclagem fornecida. Deve ser usado apenas uma vez. Veja a seção MERGE STRATEGIES em [git-merge[1\]](https://git-scm.com/docs/git-merge/pt_BR) para detalhes.

- -X<opção>

- --strategy-option=<opção>

  Encaminhe a um opção específica até a estratégia de mesclagem. Para mais detalhes, consulte [git-merge[1\]](https://git-scm.com/docs/git-merge/pt_BR).

- --rerere-autoupdate

- --no-rerere-autoupdate

  Permita que o mecanismo "rerere" atualize o índice com o resultado da resolução automática de conflitos, caso seja possível.

## SEQUENCER SUBCOMANDOS

- --continue

  Continue a operação em andamento utilizando as informações existentes em `.git/sequencer`. Pode ser utilizado para continuar após a resolução dos conflitos em uma falha na seleção ou reversão da escolha seletiva.

- --skip

  Ignore o commit atual e continue com o restante da sequência.

- --quit

  Esqueça a operação atual em andamento. Pode ser utilizado para limpar a condição do sequenciador após uma falha na seleção ou reversão de uma escolha seletiva.

- --abort

  Cancele a operação e retorne a condição pré-sequência.

## EXEMPLOS

- `git revert HEAD~3`

  Reverta as alterações informadas pelo quarto último commit no HEAD e crie um novo commit com as alterações revertidas.

- `git revert -n master~5..master~2`

  Reverta as alterações feitas pelos commits do quinto último commit no master (incluso) para o terceiro último commit no master (incluso), porém não crie nenhum commit com as alterações revertidas. A reversão altera apenas a árvore de trabalho e o índice.