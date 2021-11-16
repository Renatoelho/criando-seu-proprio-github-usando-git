# Criando seu próprio <i>‘GitHub’</i> usando o Git

### Requisitos mínimos para instalação:

>> Sistema operacional Linux (Ubuntu 20.04.2 LTS)  <br/>Memória RAM de 4GB ou mais  <br/>Versão mais recente do Git

O Git é um software de versionamento de código como muitos outros que existem, mas graças ao GitHub que é uma plataforma web de distribuição códigos e que usa por traz o código do Git tornou essa ferramenta muito famosa na comunidade de desenvolvimento. O que muita gente não sabe que é possível criar seu próprio <i>‘GitHub’</i>, mas sem interface gráfica, onde você ficará responsável por administrar toda infraestrutura e os reportórios, existem outras variações no mercado como o GitLab que é uma variação do GitHub muito usado em ambientes corporativos.

Encare essa minha abordagem de maneira mais conceitual, pois sabemos que a utilização do GitHub e de sua interface facilita muito a vida de quem utiliza a plataforma para desenvolvimento, mas sempre é válido entender o funcionamento de ferramentas que estão no nosso dia a dia.

Como eu disse, é possível criar seu repositório de códigos utilizando uma VPN ou uma máquina virtual hospedada em qualquer um dos principais fornecedores de Cloud como AWS, Azure, GCP entre outros e instalando nessa máquina o Git na sua versão mais recente já é possível criar seus repositórios e administrar sua rotina de desenvolvimento ou de sua equipe. 

### Aqui é a representação gráfica de como ficaria sua infraestrutura:

![Servidor Git](https://drive.google.com/uc?export=view&id=1DqSfEgnI15rY6IbfghbhESm4UKhiE85Q)

Nesse exemplo aqui vou utilizar uma máquina virtual local, mas esses mesmos passos podem ser replicados em uma VPN ou Cloud.

## 1º Passo - Instalando o Git

- Atualize o ambiente antes de iniciar o processo com os seguintes comandos:

````
sudo apt update && sudo apt upgrade -y
````

- Execute o seguinte comando:

````
sudo apt install git -y
````

![Instalação do Git](https://drive.google.com/uc?export=view&id=1EBgO94ijhqrLTj1pd_3SPLvPr0wkS6z6)

Instalado com sucesso.

## 2º Passo - Criando o repositório central

Agora vamos criar um diretório no nosso servidor e vamos utilizar ele como repositório central.

- Criando um diretório:

````
mkdir -p repo_central.git
````

- Acessando o diretório:

````
cd repo_central.git
````

- Iniciando o diretório como um repositório central:

````
git init --bare
````

![Criando Repo Central](https://drive.google.com/uc?export=view&id=1ECBLX7rV7uAPuv4BqmetkaM5R10a6BHW)

## 3º Passo - Vinculando uma pasta qualquer ao repositório (local)

Agora vamos escolher um suposto diretório onde teríamos um projeto ou vários para vinculá-lo ao repositório central e assim poder movimentar códigos entre eles.  

````
$ cd projetos/
$ git init .
$ git remote add origin /home/ubuntu/repo_central.git
````

![Remote Add git](https://drive.google.com/uc?export=view&id=1ENcu9DWpalNOeLvb8Py9wEP_HU_hr5U4)

## 4º Passo - Clonando o repositório central (remoto)

Clonar é mais uma forma de criar esse vínculo, entre uma determinada pasta preferencialmente em uma máquina que vai ser utilizada para desenvolvimento e vinculada ao repositório central do Git.

**Sintaxe:** ````git clone <usuário>@<servidor>:<Local do repositório central> <diretório que vai receber o clone>````

````
$ cd projetos2/
$ git clone ubuntu@localhost:/home/ubuntu/repo_central.git arquivos_clonados
````

![Clonando Repo Central](https://drive.google.com/uc?export=view&id=1EPEbjqk1iOHBQTNh49u46YgmmhZwePRN)

>> **Observação:** apareceu uma notificação de <i>warning</i>, pois como o repositório do Git está vazio aparece essa mensagem, caso contrário não apareceria. Outro ponto importante é que no <i>clone</i> feito conforme sintaxe acima é necessário que o servidor onde está o Git e a máquina cliente tenham o <i>SSH</i> instalado, como em nosso exemplo o servidor e o cliente são **a mesma máquina** só é necessária uma única configuração <i>SSH</i>.

Pronto, tudo instalado e configurado a partir de agora você pode utilizar esse ambiente para versionar seus códigos, além de poder distribuir o acesso a quem você queria que tenha esse acesso.

Em breve eu volto para ensinar os principais comandos do Git que podem ser utilizados, tanto no Git como no GitHub ou GitLab.

**Até.**

**Referências:**  <br/><font size="1">Wikipédia, **Git.** Disponível em:<https://pt.wikipedia.org/wiki/Git>. Acesso em: 16 nov. 2021.  <br/> Git-scm.com, **Git --fast-version-control.** Disponível em: <https://git-scm.com/docs/git/pt_BR>. Acesso em: 16 nov. 2021.  <br/> Wikipédia, **GitHub.** Disponível em:<https://pt.wikipedia.org/wiki/GitHub>. Acesso em: 16 nov. 2021.  <br/> Wikipédia, **GitLab.** Disponível em:< https://pt.wikipedia.org/wiki/GitLab>. Acesso em: 16 nov. 2021.  <br/></font>

