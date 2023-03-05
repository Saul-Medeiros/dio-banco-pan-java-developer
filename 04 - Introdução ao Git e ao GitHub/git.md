![logo-git](./img/1024px-Git-logo.svg.png)

---

## Conceitos GIT

**GUI** - Graphic User Interface

**CLI** - Command Line Interface (base do GIT)

**Git Bash** - Usado em sistemas Unix (Linux e derivados)

**Git CMD/Shell** - Usado no sistema Windows

---

## Comandos no Git Bash

`dir` - lista os diretórios do windows (pastas) no caminho atual

`ls` - lista os diretórios do linux (git bash) no caminho atual

`cd /` - volta para a raíz do Linux

`cd _nomepasta_` - acessa a pasta/diretório do Linux

`cd ..` - volta para a pasta anterior

`clear` ou `ctrl+l` - limpa o conteúdo da tela

`mkdir` - cria uma pasta (no Linux será preciso da permissão de administrador, para obter basta executar o comando `sudo su` e uma senha caso tenha)

`echo _texto_ > arquivo.txt` - o sistema redireciona o fluxo (`>`) para um arquivo (caso o arquivo não exista, ele vai automaticamente criar)

`rm -rf _pasta_/` - "remove" apaga a pasta e todo o conteúdo dentro dela (o parâmetro r vem de recursive, ele remove todas as pastas que estiverem dentro uma da outra, dentro da pasta selecionada; e o parâmetro f vm de force, evita solicitação de confirmação do para deletar a pasta)

---

## Comandos no Git CMD

`cd/` - volta para a pasta raiz do Windows

`cd _nomepasta_` - acessa a pasta/diretório do Windows

`cd ..` - volta para a pasta anterior

`cls` - "clear screen" limpa o conteúdo da tela

`tab` - completa o nome da pasta que está sendo digitada

`mkdir` - "make directory" cria uma pasta/diretório

`echo _texto_` - o sistema retorna a informação digitada pelo usuário

`echo _texto_ > arquivo.txt` - o sistema redireciona o fluxo (>) para um arquivo (caso o arquivo não exista, ele vai automaticamente criar)

`del _pasta_` - apaga todos os arquivos da pasta, mas o diretório continua existindo

`rmdir _pasta_ /S /Q` - "remove directory" apaga a pasta existente e todo o conteúdo dentro dela

---

## Security Hash Algorithm

SHA1 - A sigla SHA significa Secure Hash Algorithm (Algoritmo de Hash Seguro), é um conjunto de funções hash criptográficas projetadas pela NSA (Agência de Segurança Nacional dos EUA). ELe pega um arquivo e "embaralha" e a encriptação gera conjunto de characteres indentificador de 40 dígitos. É uma forma curta de representar um arquivo. O arquivo quando sofre uma pequena alteração, o seu SHA sofre uma alteração nos dígitos, essa é uma forma do GIT indentificar alterações de código, e quando o conteúdo for alterado pra sua forma anterior novamente, o SHA vai ser o mesmo.

`echo "ola mundo" | openssl sha1` - gera o código SHA de 40 dígitos do arquivo selecionado dentro do GIT bash.

---

## Objetos do Git

Objetos fundamentais - blobs, trees, commits

**Blob** "bolha" - Os arquivos ficam guardados dentro do objeto Blob, que contém metadados. O objeto blob vai ter o tipo do objeto, no caso Blob, o tamanho da string, o \0 e o conteúdo do arquivo.

```bash
echo 'conteudo' | git hash-object --stdin
> fc31e91b26cf85a55e072476de7f263c89260eb1

echo -e 'conteudo' | openssl sha1
> 65b0d0dda479cc03cce59528e28961e498155f5c

echo -e 'blob 9\0conteudo' | openssl sha1
> fc31e91b26cf85a55e072476de7f263c89260eb1
```

**Tree** "árvore" - As trees armazenam blobs, o blob sendo o bloco básico de composição, a tree apontando e armazenando tipos de blobs diferentes. A tree contém metadados, que contém o \0, o tipo de blob, o sha e o nome do arquivo. Ela pode apontar para blobs e também para trees, assim como uma pasta pode levar para outra pasta, por exemplo. Quando se altera uma vírgula em um arquivo, o sha1 do blob vai ter mudado, e por consequência o sha1 do tree também vai ter mudado, sendo que uma coisa está relacionada com a outra.

**Commit** - É o objeto que vai juntar tudo, o commit aponta para uma tree, aponta para um parente (último commit realizado antes dele), para um autor (a pessoa que fez o commit), para uma mensagem (o commit pode armazenar uma mensagem que dê signficado a sua existência, aos arquivos dentro das pastas) e possui um timestamp (carimbo de tempo). O commit também possui um sha1, que basicamente é a junção de todos os metadados existentes nele, ou seja, qualquer mínima alteração em uma blob por exemplo, vai alterar o sha1 de uma tree que aponta para ela, e por sua vez vai alterar o sha1 do commit. Um commit não pode ser alterado depois de feito, apenas substituído.

---

## Sistema Distribuído

Um sistema distribuído é uma coleção de programas de computador que utilizam recursos computacionais em vários pontos centrais de computação diferentes para atingir um objetivo comum e compartilhado. Os sistemas distribuídos visam remover gargalos ou pontos centrais de falha de um sistema.

---

## Chaves SSH

É uma forma de estabelecer uma conexão segura e encriptada entre duas máquinas. Sendo essa conexão a da máquina do usuário e o GitHub.
Segue a lista de comandos para criar as duas chaves SSH no seu computador (deve usar o Git Bash em Windows ou no Linux):

```bash
ssh-keygen -t ed25519 -C seuemail@mail.com
```

>após o comando acima, ele vai gerar uma chave ssh e vai indicar o caminho em que ela se encontra:

```bash
Enter file in which to save the key (/c/Users/_nomeusuário_/.ssh/id_ed25519):
```

>após teclar enter, ele vai pedir uma senha para acesso do arquivo, caso não queira inserir uma senha, basta digitar enter e após isso será gerado um SHA256 e uma key randomart asim como está na imagem abaixo:

![ssh-exemplo](./img/Captura%20de%20Tela%20(411).png)

>Para acessar a pasta criada no Git Bash, basta digitar o seguinte comando (caso o nome de usuário tenha espaços, o nome pode ser inserido com aspas simples ['nome usuário'] ou com tabulações [nome\ usuário]):

```bash
cd /c/Users/_nomeusuário_/.ssh/
```

>Para acessar o conteúdo do arquivo, basta digitar o comando cat e o nome do arquivo logo em seguida (lembrando que, a chave SSH que vai ser compartilhada no GitHub deve ser a chave pública, para identificá-la, o arquivo público terá a extensão .pub, o arquivo privado é o outro que foi gerado e consequentemente ele não tem a extensão .pub).

```bash
cat id_ed25519.pub
```

>Após isso, ele mostrará a chave SSH pública, após isso, basta inseri-la no GitHub, nas opções de Chaves SSH.

`pwd` mostra o caminho completo até a pasta atual no Git Bash

>Após todo este processo, é preciso ativar o ssh agent, que é o que vai gerenciar as chaves ssh geradas. Para isso, basta digitar o seguinte comando:

```bash
eval $(ssh-agent -s)
```

>Após digitar o comando acima, ele vai gerar um agent pid com um número aleatório, para inserir a chave nesse agent, basta digitar o seguinte comando (lembrando que no agent é inserido a chave SSH privada, para ele monitorar qualquer alteração feita). Caso você já esteja na pasta da chave SSH, basta inserir o nome dela ao invés do caminho do arquivo:

```bash
ssh-add _caminho_do_arquivo_
```

>Quando uma chave SSH é configurada na máquina, não é possível clonar um repositório do GitHub por link HTTPs, mas logo, é possivel clonar por SSH, que é uma das opções que o GitHub dá, basta copiar o link e usar no seguinte comando:

```bash
git clone _linkcopiado_
```

>A primeira vista, não vai parecer que funcionou, mas basta aparecer a seguinte mensagem `Are you sure you want to continue connecting (yes/no/[fingerprint])?` e digitar yes, que, o repositório irá ser clonado com sucesso.

---

## Tokens de acesso pessoal

O token funciona de forma similar a chave SSH, mas sem muita linha de comandos e apenas usando um tipo de token. No GitHub, nas configurações, na opção "Developer Settings", existe uma opção para ser gerado um token, após o mesmo ser gerado, ele deve ser guardado em um local seguro, em um arquivo de segurança e pode-se personalizar o mesmo, qual a "data de validade" dele, e após o token ser gerado, caso seja perdido, deve-se gerar outro token de acesso. O token, resumidamente, lhe permite clonar um repositório do GitHub por HTTPS e colocá-lo em uma pasta com chave SSH, com o mesmo comando `git clone`, só que agora com o link https, ele vai abrir um popup do GitHub pedindo o email e o token de confirmação, após ser inserido e o passo ser finalizado, o repositório vai ser clonado normalmente na sua pasta.

---

## Iniciando e configurando um repositório no Git

`git init` - inicia o git dentro da pasta ou repositório atual

`ls -a` - comando para mostrar arquivos ocultos no git bash (`.arquivo`)

>a pasta objects dentro do .git armazena os objetos

`git config --global user.email ""` - configuração para definir o email de usuário do git com a flag `--global`, que configura para todo o git, onde o que está em aspas vai ser colocado o email do autor

`git config --global user.name name` - configuração para definir o nome de usuário do git com a flag `--global`, que configura para todo o git, onde no lugar de name deve ser colocado o nome que desejar.

`git add *` - após um arquivo de qualquer tipo ser inserido na pasta onde está localizado o .git, é possível inseri-lo ao git usando este comando (o símbolo `*` é uma abrangência, significa que todos os arquivos novos da pasta serão adicionados ao git)

`git commit -m "commit inicial"` - depois do arquivo ser adicionado, ele pode ser commitado (`-m` é uma flag para commit), após isso, ele retornará informações do commit (em qual branch foi commitado, o sha1 e sua mensagem, que está entre aspas), assim como está na imagem abaixo:

![git-commit](./img/Captura%20de%20Tela%20(413).png)

`git status` - mostra o status do seu repositório local

`mv arquivo.txt ./pasta/` - move o arquivo para a pasta indicada (./indica o repositório atual)

`git config --list` - mostra uma lista de todas as configurações feitas no git (para sair dessa lista, basta apertar `q`)

`git config --global --unset user.name` - desfaz a alteração global que foi aplicada a user.name para poder modificá-lo novamente (com o uso da flag `--unset`), sendo esse comando aplicável a outros tipos da lista do git config

`git remote add origin _link github repository_` - vincula o repositório remoto (GitHub) ao repositório local, com o nome origin sendo um alias(pseudônimo) ao link

`git remote -v` - exibe as informações do repositório remoto

`git push origin master` - após os arquivos serem commitados localmente, eles podem ser adicionados ao repositório remoto através deste comando, tendo em vista que pedirá uma confirmação para envio, assim como mostra na imagem abaixo:

![git-push](./img/Captura%20de%20Tela%20(421).png)

---

## Ambiente de Desenvolvimento e Servidor

![git-add](./img/Captura%20de%20Tela%20(417).png)

![git-commit](./img/Captura%20de%20Tela%20(418).png)

> Working Directory -> Staging Area: `git add`

> Staging Area -> Local Repository: `git commit -m`

> Local Repository -> Remote Repository: `git push origin`

> Remote Repository -> Local Repository: `git pull origin`

**Untracked** - arquivo que o git não tem ciência de sua existência

**Tracked** {Unmodified, Modified, Staged} - ao contrário do exemplo anterior, o git já possui conhecimento do arquivo (o arquivo foi adicionado ao git)

**Unmodified** - Não foi alterado após adicionado ao git e commitado (um arquivo unmodified que for retirado do repositório, passará a ser untracked, pois o arquivo não sofreu alterações desde seu último commit)

**Modified** - Arquivo modificado (o git compara as versões o sha1 para indentificar alterações), para ser modified, ele deve ter sido adicionado e commitado no git

**Staged** - Arquivo preparado para um commit (pode ser um arquivo não adicionado ao git ou modificado)

**Merge** - Arquivo que sofreu alteração na mesma linha por 2 ambientes de desenvolvimento (geralmente ocorre quando o arquivo que está no servidor sofreu alterações e o seu arquivo local não foi atualizado, para isto, basta fazer um `pull origin` para comparar as alterações e modificar de acordo com seus critérios). Veja exemplo abaixo:

![merge-conflict](./img/Captura%20de%20Tela%20(423).png)

![merge-solution](./img/Captura%20de%20Tela%20(424).png)
