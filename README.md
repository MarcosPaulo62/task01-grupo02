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



## Comando GIT CHERRY-PICK
git-cherry-pick - Aplique as alterações introduzidas por alguns commits existentes

#### RESUMO
git cherry-pick [--edit] [-n] [-m parent-number] [-s] [-x] [--ff]
		  [-S[<keyid>]] <commit>…​
git cherry-pick (--continue | --skip | --abort | --quit)

#### DESCRIÇÃO
Dado um ou mais commits existentes, aplique a alteração que cada um introduz, registrando um novo commit para cada um. Isso requer que a sua árvore de trabalho esteja limpa (nenhuma alteração a partir do commit HEAD).

Quando não é óbvio como aplicar uma alteração, acontece o seguinte:

O ramo atual e o ponteiro HEAD permanecem no último commit realizado com sucesso.

A referência CHERRY_PICK_HEAD é configurada para apontar para o commit que introduziu a mudança que é difícil de aplicar.

Caminhos nos quais a mudança aplicada corretamente são atualizados no arquivo de índice e na sua árvore de trabalho.

Para os caminhos conflitantes, o arquivo do índice registra até três versões, conforme descrito na seção "MESCLAGEM REAL" do git-merge[1]. Os arquivos da árvore de trabalho incluirão uma descrição do conflito entre os marcadores de conflito habituais <<<<<<< e >>>>>>>.

Nenhuma outra modificação é feita.

Veja git-merge[1] para algumas dicas sobre como resolver tais conflitos.

#### OPÇÕES
<commit>…​
Faz o commit na escolha seletiva. Para conhecer uma lista completa das diferentes maneiras de soletrar os nomes dos commits, consulte o comando gitrevisions[7] O conjunto dos commits também podem ser encaminhados porém é predefinido que nenhuma passagem seja feita, consulte o comando git-rev-list[1] assim como a sua opção --no-walk. Observe que ao definir um argumento para o intervalo, este irá alimentar todos os <commit>…​ percorrendo apenas uma revisão (mais adiante, consulte um exemplo que utiliza maint master..next).

-e
--edit
Com esta opção, o git cherry-pick permitirá que você edite a mensagem de commit antes de confirmar.

--cleanup=<modo>
Essa opção define como a mensagem de commit sera limpa antes de ser encaminhada para o maquinário de commit. Para mais detalhes consulte git-commit[1]. Em particular, caso o valor <mode> tenha um valor de tesoura scissors, a tesoura será anexada a MERGE_MSG antes de ser repassada no caso de um conflito.

-x
Ao gravar o commit, acrescente uma linha que diz "(cherry picked from commit …​)" na mensagem do commit original, indicando de onde a escolha seletiva da alteração deste commit foi feito. Isto é feito apenas para as escolhas seletivas sem conflitos. Não use esta opção caso esteja fazendo uma escolha seletiva do seu ramo privado porque a informação é inútil para o destinatário. No entanto, caso esteja fazendo uma escolha seletiva entre dois ramos publicamente visíveis (como por exemplo, fazendo a atualização retroativa de uma correção para um ramo de manutenção para uma versão de lançamento anterior de um ramo de desenvolvimento), pode ser útil adicionar esta informação.

-r
Costumava ser que o comando predefinia para fazer com a opção -x descrito acima, e a opção -r era para desativá-lo. Agora a predefinição é não utilizar a opção -x, então esta opção não é operacional.

-m parent-number
--mainline parent-number
Geralmente você não pode fazer uma escolha seletiva de uma mesclagem porque você não sabe qual o lado da mesclagem principal deve ser considerada. Esta opção determina o número da origem (a partir de 1) do principal e permite que a escolha seletiva repita a alteração em relação a origem informada.

-n
--no-commit
Normalmente, o comando cria automaticamente uma sequência de commits. Esta opção aplica as alterações necessárias para selecionar cada commit informada na sua árvore de trabalho e o índice, sem fazer qualquer commit. Além disso, quando esta opção é utilizada, o seu índice não precisa coincidir ao commit do HEAD. A escolha seletiva é feita contra a condição inicial do seu índice.

Isso é útil quando você seleciona mais de um efeito de commit para seu índice em uma linha.

-s
--signoff
Adicione uma linha de assinatura no final da mensagem do commit. Para mais informações, consulte a opção signoff em git-commit[1].

-S[<keyid>]
--gpg-sign[=<keyid>]
--no-gpg-sign
Commits assinados com o GPG O argumento keyid é opcional e a predefinição retorna para a identidade de quem fez o commit; caso seja utilizado, deve estar anexado a opção e sem espaço. A opção --no-gpg-sign é útil para revogar a variável de configuração commit.gpgSign e a anterior --gpg-sign.

--ff
Se o atual HEAD é o mesmo que o pai do commit cherry-pick’ed, então um avanço rápido para este commit será executado.

--allow-empty
É predefinido que a escolha seletiva de um commit vazio falhará, indicando que é necessário uma chamada explícita do comando git commit --allow-empty. Esta opção substitui este comportamento, permitindo que os commits vazios sejam preservados automaticamente em uma escolha seletiva. Observe que quando "--ff" estiver em vigor, os commits vazios que atendam ao requisito de "avanço rápido" serão mantidos mesmo sem esta opção. Observe também que o uso desta opção mantém apenas os commits inicialmente estão vazios (ou seja, o commit registrou a mesma árvore que o seu pai). Os commits que são tornados vazios devido a um commit anterior são descartados. Para impor a inclusão destes commits, utilize a opção --keke-redundant-commits.

--allow-empty-message
É predefinido que a escolha seletiva irá falhar quando houver um commit com uma mensagem sem nenhum conteúdo. Esta opção substitui este comportamento, permitindo que os commits com mensagens sem nenhum conteúdo possam ser usados.

--keep-redundant-commits
Caso um commit que esteja sendo escolhido seletivamente duplique um commit já no histórico atual, ele ficará vazio. É predefinido que estes commits redundantes façam com que a escolha seletiva cherry-pick pare para que o usuário possa examinar o commit. Esta opção substitui esse comportamento e cria um objeto commit vazio. implica no uso da opção --allow-empty.

--strategy=<estratégia>
Use a estratégia de mesclagem fornecida. Deve ser usado apenas uma vez. Veja a seção MERGE STRATEGIES em git-merge[1] para detalhes.

-X<opção>
--strategy-option=<opção>
Encaminhe a um opção específica até a estratégia de mesclagem. Para mais detalhes, consulte git-merge[1].

--rerere-autoupdate
--no-rerere-autoupdate
Permita que o mecanismo "rerere" atualize o índice com o resultado da resolução automática de conflitos, caso seja possível.

#### SEQUENCER SUBCOMANDOS
--continue
Continue a operação em andamento utilizando as informações existentes em .git/sequencer. Pode ser utilizado para continuar após a resolução dos conflitos em uma falha na seleção ou reversão da escolha seletiva.

--skip
Ignore o commit atual e continue com o restante da sequência.

--quit
Esqueça a operação atual em andamento. Pode ser utilizado para limpar a condição do sequenciador após uma falha na seleção ou reversão de uma escolha seletiva.

--abort
Cancele a operação e retorne a condição pré-sequência.

#### EXEMPLOS
git cherry-pick master
Aplique a mudança introduzida pelo commit na ponta do branch master e crie um novo commit com esta mudança.

git cherry-pick ..master
git cherry-pick ^HEAD master
Aplique as alterações introduzidas por todos os commits que são ancestrais do master, mas não do HEAD para produzir novos commits.

git cherry-pick maint próximo ^master
git cherry-pick maint master..próximo
Aplique as alterações introduzidas por todos os commits que sejam ancestrais do "maint" ou "next", porém não do "master" ou dos seus ancestrais. Note que o último não significa que maint e tudo entre master e next; especificamente, maint não será usado caso esteja incluso no master.

git cherry-pick master~4 master~2
Aplique as alterações introduzidas pelo quinto e terceiro últimos commits apontados pelo master e crie 2 novos commits com essas mudanças.

git cherry-pick -n master~1 next
Aplique as alterações na árvore de trabalho e no índice que foram introduzidos pelo segundo último commit apontada pelo "master" e pelo último commit apontada pelo próximo, porém não crie nenhum commit com estas alterações.

git cherry-pick --ff ..next
Caso o histórico seja linear e HEAD seja um ancestral do próximo, atualize a árvore de trabalho e avance o ponteiro HEAD para que coincida com o próximo. Caso contrário, aplique as alterações introduzidas pelos commits que estão na próxima, mas não o `HEAD`para o ramo atual, criando um novo commit para cada nova alteração.

git rev-list --reverse master -- README | git cherry-pick -n --stdin
Aplique as alterações introduzidas por todas as confirmações no ramo principal que tocaram no README para a árvore de trabalho e o índice, para que o resultado possa ser inspecionado e transformado em uma única nova confirmação, se adequado.

A seqüência a seguir tenta retroceder um patch, suspender porque o código ao qual o patch se aplica mudou muito e, em seguida, tenta novamente, desta vez exercendo mais cuidado com as linhas de contexto correspondentes.

$ git cherry-pick topic^             (1)
$ git diff                           (2)
$ git reset --merge ORIG_HEAD        (3)
$ git cherry-pick -Xpatience topic^  (4)
aplique a alteração que seria exibido através do comando git show topic^. Neste exemplo, o patch não se aplica de maneira limpa; portanto, as informações sobre os conflitos são gravadas no índice e na árvore de trabalho, sem nenhum resultado do novo commit.

resumir as alterações a serem reconciliadas

cancela a escolha seletiva. Em outras palavras, retorne a condição de escolha seletiva anterior, preservando as alterações locais que você teve na árvore de trabalho.

tente aplicar a mudança introduzida por topic^ novamente, gastando tempo extra para evitar erros baseados em linhas de contexto correspondentes incorretas.
  

  
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

