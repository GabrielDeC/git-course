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
