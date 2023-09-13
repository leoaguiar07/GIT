![capa](https://github.com/leoaguiar07/GIT/blob/main/git.jpg)

## Controle de Versão e Git

**Objetivo:**

- Aprender os conceitos básicos do Git.

O Git é uma parte importante da programação no dia a dia (especialmente se você estiver trabalhando em equipe) e é amplamente usado no setor de software.

Como existem muitos comandos que você pode utilizar, dominar o Git por completo leva tempo. Alguns comandos, no entanto, são usados com mais frequência (alguns, até, diariamente). 
Observação: para entender este artigo, você precisa conhecer o básico sobre o Git.

### 1. Git clone
Git clone é uma comando para baixar o código-fonte existente de um repositório remoto (como, por exemplo, o Github). Em outras palavras, git clone, basicamente, faz uma cópia idêntica da versão mais recente de um projeto em um repositório e a salva em seu computador.

Há algumas maneiras de baixar o código-fonte, mas, em geral, eu prefiro a maneira de clonar com https:

```python
git clone <https://link-com-o-nome-do-repositório>
```
Por exemplo, se eu quiser baixar um projeto do Github, tudo o que eu preciso fazer é clicar no botão verde (que diz "Clone or download"), copiar o URL da caixa logo abaixo e colá-lo após o comando git clone que mostrei logo acima.

![capa](https://www.freecodecamp.org/portuguese/news/content/images/2022/03/resim-4.png)

Exemplo com o código-fonte do Bootstrap no Github
Isso fará uma cópia do projeto no seu espaço de trabalho local para que você possa começar a trabalhar nessa cópia.

### 2. Git branch
Branches (algo como ramificações, em português) são altamente importantes no mundo do git. Usando as branches, vários desenvolvedores conseguem trabalhar em paralelo no mesmo projeto simultaneamente. Podemos usar o comando git branch para criar, listar e excluir as branches.

Como criar uma branch:

```python
git branch <nome-da-branch>
```
Esse comando criará uma branch em seu local de trabalho. Para fazer o push (algo como enviar) da nova branch para o repositório remoto, você precisa usar o comando a seguir:

```python
git push -u <local-remoto> <nome-da-branch>
```
Como ver as branches:

```python
git branch ou git branch --list
```
Como excluir uma branch:

```python
git branch -d <nome-da-branch>
```

### 3. Git checkout
Esse também é um dos comandos do Git mais usados. Para trabalhar em uma branch, primeiro, é preciso "entrar" nela. Usamos git checkout, na maioria dos casos, para trocar de uma branch para outra. Também podemos usar o comando para fazer o checkout de arquivos e commits.

```python
git checkout <nome-da-branch>
```
Existem alguns passos que você precisa seguir para trocar de branch com sucesso:

As alterações em sua branch atual devem estar em um commit ou em um stash antes de você fazer a troca
A branch na qual você quer fazer o checkout deve existir no seu espaço de trabalho local
Também existe um comando de atalho que permite criar e automaticamente trocar para a branch criada ao mesmo tempo:

```python
git checkout -b <nome-da-branch>
```
Esse comando cria a branch em seu espaço de trabalho local (a flag -b representa a branch) e faz o checkout na nova branch logo após sua criação.

### 4. Git status
O comando git status nos dá todas as informações necessárias sobre a branch atual.

```python
git status
```
Obtemos as seguintes informações:

Se a branch em que estamos no momento está atualizada
Se precisamos fazer o commit, push ou pull de algo
Se os arquivos estão em fase de stage, fora dessa fase ou se não estão sendo rastreados
Se arquivos foram criados, modificados ou excluídos

![capa](https://www.freecodecamp.org/portuguese/news/content/images/2022/03/resim-5.png)

Git status nos dá informações sobre a branch e os arquivos
### 5. Git add
Ao criarmos, modificarmos ou excluirmos um arquivo, essas alterações acontecerão em nosso espaço de trabalho local e não serão incluídas no próximo commit (a menos que alteremos as configurações).

Precisamos usar o comando git add para incluir as alterações de um ou vários arquivos em nosso próximo commit.

Para adicionar um único arquivo:
```python
git add <arquivo>
```
Para adicionar tudo ao mesmo tempo:


```python
git add -a
```
Ao ver a imagem acima, na 4ª seção, você verá que existem nomes de arquivo que estão em vermelho - isso significa que os arquivos ainda não estão em fase de stage. Esses arquivos não serão incluídos em seus commits.

Para incluí-los, precisamos usar git add:

![capa](https://www.freecodecamp.org/portuguese/news/content/images/2022/03/resim-6.png)

Os arquivos em verde agora estão em fase de stage com o git add
Importante: o comando git add não altera o repositório. As alterações não são salvas até que se use o git commit.


Ou para adicionar mais arquivos ao mesmo tempo,
```python
$ git add index.html estilo.css
```
Caso queira adicionar todos os arquivos de um diretório recursivamente; o que inclui seus subdiretórios e arquivos ou pastas ocultas,
```python
$ git add .
```
Para adicionar todos os arquivos de uma determinada extensão.
```python
$ git add *.txt
```

### 6. Git commit
Talvez esse seja o comando mais usado do Git. Quando chegamos a determinado ponto em desenvolvimento, queremos salvar nossas alterações (talvez após uma tarefa ou resolução de problema específica).

Git commit é como definir um ponto de verificação no processo de desenvolvimento. Você pode voltar a esse ponto mais tarde, se necessário.

Também precisamos escrever uma mensagem breve para explicar o que desenvolvemos ou alteramos no código-fonte.

```python
git commit -m "mensagem do commit"
```
Importante: git commit salva suas alterações no espaço de trabalho local.

### 7. Git push
Após fazer o commit de suas alterações, a próxima coisa a fazer é enviar suas alterações ao servidor remoto. Git push faz o upload dos seus commits no repositório remoto.

```python
 push <repositório-remoto> <nome-da-branch>
```
Entretanto, se a sua branch foi recém-criada, também é preciso fazer o upload da branch com o seguinte comando:

```python
git push --set-upstream <repositório-remoto> <nome-da-branch>
```
ou

```python
git push -u origin <nome-da-branch>
```
Importante: git push somente faz o upload das alterações que já estão em um commit.

### 8. Git pull
O comando git pull é usado para obter as atualizações de um repositório remoto. Esse comando é uma combinação de git fetch e git merge, o que significa que, quando usamos git pull, ele recebe as atualizações do repositório remoto (git fetch) e aplica imediatamente as alterações mais recentes em seu espaço de trabalho local (git merge).

```python
 pull <repositório-remoto>
```
Essa operação pode causar conflitos que você precisará resolver manualmente.

### 9. Git revert
Às vezes, precisamos desfazer as alterações que fizemos. Existem várias maneiras de se desfazer as alterações em nosso espaço de trabalho local ou remotamente (dependendo do que você necessita), mas devemos usar esses comandos com cuidado para evitar exclusões indesejadas.

Uma maneira segura de desfazer nossos commits é usando git revert. Para ver nosso histórico de commits, primeiro, precisamos usar git log -- oneline:

![capa](https://www.freecodecamp.org/portuguese/news/content/images/2022/03/resim.png)

Histórico de commits da minha branch master
Em seguida, precisamos apenas especificar o código hash ao lado do commit que desejamos desfazer:

```python
git revert 3321844
```
Depois disso, você verá uma tela igual ao que vemos abaixo - basta pressionar shift + q para sair:

![capa](https://www.freecodecamp.org/portuguese/news/content/images/2022/03/resim-2.png)

O comando git revert desfará o commit especificado, mas criará outro commit sem excluir o antigo:

![capa](https://www.freecodecamp.org/portuguese/news/content/images/2022/03/resim-3.png)

Novo commit do "revert"

A vantagem de se usar git revert é não tocar no histórico de commits. Isso significa que você ainda pode ver todos os commits do seu histórico, mesmo os revertidos.

Outra medida de segurança está no fato de que tudo acontece em nosso sistema local, a menos que façamos o push de tudo para o repositório remoto. É por isso que o uso de git revert é mais seguro e é a forma preferida de desfazer nossos commits.

### 10. Git merge
Quando você concluir o desenvolvimento em sua branch e quando tudo funcionar bem, a etapa final é fazer o merge (mesclar ou unir, em português) da branch com a branch pai (dev ou master/main, em geral). Isso é feito com o comando git merge.

Git merge, basicamente, integra sua branch com o recurso e todos os seus commits na branch de desenvolvimento (dev) ou na branch principal (master ou main). É importante lembrar que, primeiro, você precisa estar na branch específica na qual você quer fazer o merge de sua branch com o recurso.

Por exemplo, ao querer fazer o merge de sua branch do recurso na branch dev:

Primeiro, troque para a branch dev:

```python
git checkout dev
```
Antes do merge, atualize sua branch dev local:

```python
git fetch
```
Por fim, faça o merge da sua branch do recurso em dev:

```python
git merge <nome-da-branch-com-o-recurso>
```
Dica: certifique-se de que sua branch dev tem a versão mais recente antes de fazer o merge de suas branches de recurso. Do contrário, você pode ter que lidar com conflitos e outros problemas indesejados.

### 11. .gitignore

O arquivo .gitignore é um arquivo de texto que diz ao Git quais arquivos ou pastas ele deve ignorar em um projeto.

Um arquivo .gitignore local geralmente é colocado no diretório raiz de um projeto. Você também pode criar um arquivo .gitignore global e todas as entradas que estiverem naquele arquivo serão ignoradas em todos os seus repositórios do Git.

Para criar um arquivo .gitignore local, crie um arquivo de texto e dê a ele o nome de  .gitignore (lembre-se de incluir o . no começo). Em seguida, edite esse arquivo conforme necessário. Cada nova linha deve listar um arquivo ou pasta adicional que você quer que o Git ignore.

As entradas neste arquivo também podem seguir um padrão de correspondência.

* é usado para corresponder a um caractere curinga
/ é usado para ignorar nomes de caminhos relativos ao arquivo .gitignore
"#" é usado para adicionar comentários ao arquivo .gitignore

Aqui temos um exemplo de como pareceria um arquivo .gitignore:

Ignore todos os arquivos de texto<br>
*.txt

Ignore os arquivos de sistema do Mac<br>
.DS_store

Ignore a pasta node_modules<br>
node_modules

Ignore arquivos relacionados às chaves de API<br>
.env

Ignore arquivos de configuração de SASS<br>
.sass-cache

Para adicionar ou alterar seu arquivo .gitignore global, execute este comando:

```python
git config --global core.excludesfile ~/.gitignore_global
```

Isso criará o arquivo ~/.gitignore_global. Agora, você pode editar esse arquivo do mesmo modo que faz com um arquivo .gitignore local. Todos os seus repositórios do Git vão ignorar os arquivos e pastas listados no arquivo .gitignore global.

Como remover arquivos enviados anteriormente por commit a partir de um novo Gitignore
Para remover um único arquivo, ou seja, para parar de rastrear o arquivo, mas não excluir esse arquivo do sistema, use:

```python
git rm --cached filename
```

Para parar de rastrear todos os arquivos no .gitignore:

Primeiro, faça o commit de quaisquer alterações no código que estejam faltando. Depois, execute o comando:

```python
git rm -r --cached
```

Isso removerá todos os arquivos alterados do índice (área de staging). Logo depois, execute:

```python
git add .
```

Faça o commit:

```python
git commit -m ".gitignore agora está funcionando"
```

Para desfazer o git rm --cached filename, use git add filename


## Clonar um repositório
1. No GitHub.com, navegue até a página principal do repositório.

2. Acima da lista de arquivos, clique em  Código.

3. Copie a URL do repositório.

Para clonar o repositório usando HTTPS, em "HTTPS", clique em .

Para clonar o repositório usando uma chave SSH, incluindo um certificado emitido pela autoridade de certificação SSH da sua organização, clique em SSH e em .

Para clonar um repositório usando a GitHub CLI, clique em GitHub CLI e em .

Captura de tela do menu suspenso "Código". À direita da URL HTTPS do repositório, um ícone de cópia está contornado em laranja escuro.

4. Abra Git Bash.

5. Altere o diretório de trabalho atual para o local em que deseja ter o diretório clonado.

6. Digite git clone e cole a URL já copiada.

```python
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
```

7. Pressione ENTER para criar seu clone local.

```python
$ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
> Cloning into `Spoon-Knife`...
> remote: Counting objects: 10, done.
> remote: Compressing objects: 100% (8/8), done.
> remove: Total 10 (delta 1), reused 10 (delta 1)
> Unpacking objects: 100% (10/10), done.
```


## Adicionar um repositório local ao GitHub
1. Crie um repositório no GitHub.com. Para evitar erros, não inicialize o novo repositório com arquivos LEIAME, de licença ou gitignore. É possível adicionar esses arquivos após push do projeto no GitHub. Para obter mais informações, confira "Criar um repositório".

2. Na parte superior do repositório na página Configuração Rápida do GitHub.com, clique em  para copiar a URL do repositório remoto.

3. Abra Git Bash.

4. Altere o diretório de trabalho atual para seu projeto local.

5. No Prompt de comando, adicione a URL do repositório remoto em que o repositório local será enviado por push.

```python
$ git remote add origin <REMOTE_URL>
# Sets the new remote
$ git remote -v
# Verifies the new remote URL
```

6. Listar todos os arquivos novos ou modificados para serem commitados

```python
$ git status
```

7. Fazer o snapshot de um arquivo na preparação para versionamento
```python
git add [arquivo]
```
7. Fazer o snapshot de todos os arquivos na preparação para versionamento
```python
git add .
```

8. Grava o snapshot permanentemente do arquivo no histórico de versão

```python
$ git commit -m "[mensagem descritiva]"
```

9. Efetue push das alterações no repositório local para o GitHub.com
(git push [alias] [branch])

```python
$ git push origin main
```

<br><br>
Artigo original:

https://www.freecodecamp.org/news/10-important-git-commands-that-every-developer-should-know/

https://docs.github.com/pt
