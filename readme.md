# Github

Aula inicial para utilização do git no Gituhub

git init -> Comando básico para iniciar a configuração 

Ciclo de Vida de um Arquivo no Git

Untracked --- Unmodified --- Modified --- Staged

O primeiro é o arquivo criado sem que o git ainda tenha conhecimento, quando adicionado se torna o segundo e ao editar o arquivo se torna o terceiro. O último se torna o momento em que serão salvos os arquivos modificado e ao realizar o comando Commit, todos os arquivos em Stage se tornam novamente Unmodified.

Para adicionar ao Staging - git add <arquivo.extensão>

Se necessário saber o que está em Modified disponível para Stage, utilizar git status
E para realizar o commit dos arquivos modificados git commit -m "modificação realizada"

Outros comandos importantes para visualização da sequência de versões,

git log --> visualiza todas as versões commitadas e as informações dos que alteraram detalhes de horário e data.
git log --author="" --> Mostra todas as alterações realizadas por uma pessoa
git show hashdocommit --> mostra a alteração realizada naquele commit
git log --graph --> mostra os grafos de alterações e interações entre os commits e as branchs
git shortlog --> mostra os autores e os commits realizadas com as quantidades totais de commits
git shortlog -sn --> mostra resumidade os autores e quantidades de commits

Outra área de comandos do git é verificar as alterações dos arquivos antes mesmo de gerar o commit para evitar erros

git diff --> vai mostrar todas as alterarções realizadas em todos os arquivos alterados
git diff --name-only --> vai mostrar apenas os arquivos alterados
git diff nomedoarquivo --> especifica o arquivo que se deseja validar as alterações

Adicionalmente, podemos dar um "undo" as alterações realizadas por meio dos comandos abaixo

git checkout nomedoarquivo --> comando que irá desfazer as alterações realizadas antes de entrar em staging
git restore --staged nomedoarquivo --> comando que irá retirar o arquivo do staging

          --soft hashanterior --> esse comando irá desfazer um commit deixando o arquivo alterado no commit em staging  
git reset --mixed hashanterior --> esse comando irá desfazer um commit deixando o arquivo alterado em modified
          --hard hashanterior --> esse comando irá desfazer um commit apagando todas as alterações realizadas

Para que seja adicionado um Repositório Remoto, deve-se criar um repositório no GitHub e seguir orientações colocadas no próprio site.

Para que seja possível realizar um commit dentro do repositório remoto, segue o comando

git push origin main

E se necessário clonar um repositório para a sua conta

git clone endereçoSSH

BRANCH

Branch é um ponteiro de commits, isso significa que posso abrir uma branch a parte da Master para realizar alterações específicas de um bug, sem que precise alterar o arquivo principal de funcionamento.

Exemplo, se há um bug na master, mas que só dá problema em uma parte do front de um site. Ao invés de alterar o que tem na branch master direto que pode afetar front e back end, eu abro uma branch a parte para tratar daquele ponto específico do código e quando commitar, vai alterar naquele "snapshot" que depois pode ser mergeado.

Quais as vantagens?

1.) Modificar o código sem alterar o local principal
2.) Fácil de desativar
3.) Múltiplas pessoas trabalhando ao mesmo tempo sem atrapalhar ninguém
4.) Evita conflitos de código, pois a branch está mexendo em uma linha de commits própria.

Para criar um branch, git checkout -b nomebranch. Para saber em qual branch está, git branch

Para mudar o branch, git checkout nomebranch. Para deletar um branch, git branch -D nomebranch


Como unir Branchs? Merge ou Rebase

Exemplo, em um branch com 3 commits e 2 Branchs (main e iss53). Se eu criar um commit no segundo branch, então, o main está 1 commit 'atrasado'. Se eu crio um novo commit no main, cria-se uma ramificação entre o main e o iss53. Se em seguida eu criar um novo commit em iss53, teríamos uma diferença de 2 commits com o main e 1 com o iss53.

Merge

Utilizando um Merge, seria criado o novo commit com a junção de todas as alterações de todas as branchs alteradas junto da main. Criando, assim, um ciclo 'diamante' que foi criado tirando a linearidade dos commits ao criar dois commits em iss53 e 1 na master, ao realizar o merge, o ciclo fecha.

Vantagens: Operação não destrutiva, pois cria um commit extra.
Desvantagem: Commit extra que teoricamente só junta alterações já realizadas, pode ser visto como sem sentido de armazenamento e polui o histórico.

Rebase

Utilizando o rebase, ao invés dele criar um novo commit juntando alterações. Ele pega o commit criado fora da main e colocar no commit a frente do último alterado na main do caminho da main.

Vantagem: Evita commit extra e mantém o histórico linear
Desvantagem: Perde ordem cronológica, pois apaga o commit feito apenas na branch iss53 e coloca na frente do último commit da main e isso altera histórico e se outra pessoa está alterando também pode causar conflito de histórico.

Geralmente Merge é utilizado no final de um grande projeto que usamos um Pull Request.



gitignore é um comando que traz algumas regras do git para ignorar alguns tipos de arquivos que não devem ser enviados ou commitados.

Para rodar, 

vim .gitignore

E assim, adiciona-se os arquivos necessários por meio da extensão ou do arquivo especifico:

Extensão: *.xlsx
Arquivo: nomedoarquivo.xlsx
*

Em uma situação que você está em uma branch que tem alterações para commit, mas precisará tratar outras tarefas em uma branch diferente, com o comando git stash irá salvar as alterações na branch atual e aí pode ser criado o branch e tratado o que for necessário nele.

Para retornar essas alterações que foram 'congeladas' basta realizar o comando git stash apply para retornar.

git stash list --> Lista de todos os stashs
git stash clear --> limpa todos os stashs salvos


No Unix, é possível criar um alias para comandos.

git config --global alias.s status --> Comando que cria um alias para status que poderia ser executado com o s.


git tag -a 1.0.0 -m "atualizacao" --> Comando para atualizar realises de tags/versões de software

git revert hashdocommit --> comando para revert o que foi alterado no commit sem apagar o commit.

git tag -D tagparadeletar --> Deletar tags no local
git push origin :tagparaapagar --> Apaga tags no repo remoto
