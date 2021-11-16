# Criando seu pr�prio <i>�GitHub�</i> usando o Git

### Requisitos m�nimos para instala��o:

>> Sistema operacional Linux (Ubuntu 20.04.2 LTS)  <br/>Mem�ria RAM de 4GB ou mais  <br/>Vers�o mais recente do Git

O Git � um software de versionamento de c�digo como muitos outros que existem, mas gra�as ao GitHub que � uma plataforma web de distribui��o c�digos e que usa por traz o c�digo do Git tornou essa ferramenta muito famosa na comunidade de desenvolvimento. O que muita gente n�o sabe que � poss�vel criar seu pr�prio <i>�GitHub�</i>, mas sem interface gr�fica, onde voc� ficar� respons�vel por administrar toda infraestrutura e os report�rios, existem outras varia��es no mercado como o GitLab que � uma varia��o do GitHub muito usado em ambientes corporativos.

Encare essa minha abordagem de maneira mais conceitual, pois sabemos que a utiliza��o do GitHub e de sua interface facilita muito a vida de quem utiliza a plataforma para desenvolvimento, mas sempre � v�lido entender o funcionamento de ferramentas que est�o no nosso dia a dia.

Como eu disse, � poss�vel criar seu reposit�rio de c�digos utilizando uma VPN ou uma m�quina virtual hospedada em qualquer um dos principais fornecedores de Cloud como AWS, Azure, GCP entre outros e instalando nessa m�quina o Git na sua vers�o mais recente j� � poss�vel criar seus reposit�rios e administrar sua rotina de desenvolvimento ou de sua equipe. 

### Aqui � a representa��o gr�fica de como ficaria sua infraestrutura:

![Servidor Git](https://drive.google.com/uc?export=view&id=1DqSfEgnI15rY6IbfghbhESm4UKhiE85Q)

Nesse exemplo aqui vou utilizar uma m�quina virtual local, mas esses mesmos passos podem ser replicados em uma VPN ou Cloud.

## 1� Passo - Instalando o Git

- Atualize o ambiente antes de iniciar o processo com os seguintes comandos:

````
sudo apt update && sudo apt upgrade -y
````

- Execute o seguinte comando:

````
sudo apt install git -y
````

![Instala��o do Git](https://drive.google.com/uc?export=view&id=1EBgO94ijhqrLTj1pd_3SPLvPr0wkS6z6)

Instalado com sucesso.

## 2� Passo - Criando o reposit�rio central

Agora vamos criar um diret�rio no nosso servidor e vamos utilizar ele como reposit�rio central.

- Criando um diret�rio:

````
mkdir -p repo_central.git
````

- Acessando o diret�rio:

````
cd repo_central.git
````

- Iniciando o diret�rio como um reposit�rio central:

````
git init --bare
````

![Criando Repo Central](https://drive.google.com/uc?export=view&id=1ECBLX7rV7uAPuv4BqmetkaM5R10a6BHW)

## 3� Passo - Vinculando uma pasta qualquer ao reposit�rio (local)

Agora vamos escolher um suposto diret�rio onde ter�amos um projeto ou v�rios para vincul�-lo ao reposit�rio central e assim poder movimentar c�digos entre eles.  

````
$ cd projetos/
$ git init .
$ git remote add origin /home/ubuntu/repo_central.git
````

![Remote Add git](https://drive.google.com/uc?export=view&id=1ENcu9DWpalNOeLvb8Py9wEP_HU_hr5U4)

## 4� Passo - Clonando o reposit�rio central (remoto)

Clonar � mais uma forma de criar esse v�nculo, entre uma determinada pasta preferencialmente em uma m�quina que vai ser utilizada para desenvolvimento e vinculada ao reposit�rio central do Git.

**Sintaxe:** ````git clone <usu�rio>@<servidor>:<Local do reposit�rio central> <diret�rio que vai receber o clone>````

````
$ cd projetos2/
$ git clone ubuntu@localhost:/home/ubuntu/repo_central.git arquivos_clonados
````

![Clonando Repo Central](https://drive.google.com/uc?export=view&id=1EPEbjqk1iOHBQTNh49u46YgmmhZwePRN)

>> **Observa��o:** apareceu uma notifica��o de <i>warning</i>, pois como o reposit�rio do Git est� vazio aparece essa mensagem, caso contr�rio n�o apareceria outro ponto importante � que no <i>clone</i> feito conforme sintaxe acima � necess�rio que o servidor onde est� o Git e a m�quina cliente tenham o <i>SSH</i> instalado, como em nosso exemplo o servidor e o cliente s�o **a mesma m�quina** s� � necess�ria uma �nica configura��o <i>SSH</i>.

Pronto, tudo instalado e configurado a partir de agora voc� pode utilizar esse ambiente para versionar seus c�digos, al�m de poder distribuir o acesso a quem voc� queria que tenha esse acesso e aos c�digos.

Em breve eu volto para ensinar como utilizar os principais comandos do Git que podem ser utilizados, tanto no Git como no GitHub ou GitLab.

**At�.**

**Refer�ncias:**  <br/><font size="1">Wikip�dia, **Git.** Dispon�vel em:<https://pt.wikipedia.org/wiki/Git>. Acesso em: 16 nov. 2021.  <br/> Git-scm.com, **Git --fast-version-control.** Dispon�vel em: <https://git-scm.com/docs/git/pt_BR>. Acesso em: 16 nov. 2021.  <br/> Wikip�dia, **GitHub.** Dispon�vel em:<https://pt.wikipedia.org/wiki/GitHub>. Acesso em: 16 nov. 2021.  <br/> Wikip�dia, **GitLab.** Dispon�vel em:< https://pt.wikipedia.org/wiki/GitLab>. Acesso em: 16 nov. 2021.  <br/></font>

