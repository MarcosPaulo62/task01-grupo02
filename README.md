## NOME

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