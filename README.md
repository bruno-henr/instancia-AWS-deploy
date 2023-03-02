# instancia-AWS-deploy
# Criando instancia na EC2 AWS
Apenas um readme com o passa a passo para configurar EC2 na AWS

No painel da AWS, pesquisar por "EC2" -> instancias -> executar instancia -> *marcar box "Somente nivel gratuito" -> selecionar VM -> Proximo: configurar detalhes da instancia ->  next, next... -> verificar e ativar -> executar -> criar novo par de chaves (sera gerado um arquivo .pem) -> executar instancia.

apos essa sequencia de passos, sera criado e executado nossa instancia

Dentro da nossa instancia existe um botao "Conectar" que dispoem de algumas maneiras de se conectar a nossa instancia, como por exemplo o client SSH

# Configurando instancia

Conectado a VM da AWS, crie um usuario com o comando:

```sudo adduser app```

permissoes do usuário:

```sudo usermod -aG sudo app```

acessando o usuario: 

```sudo su - app```

criando pasta para salvar chave de acesso:

```
mkdir .ssh
chmod 700 .ssh/
cd .ssh/
touch authorized_keys
vi authorized_keys
```
ao utilizar o ultimo comando acima, ira abrir um editor de texto no proprio terminal e entao você inserir a sua chave SSH dentro do arquivo, para salvar e sair so basta inserir :wq! e enter

```
sudo su - app
cd .ssh/
chmod 600 authorized_keys

sudo apt update

instalar o node
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash - &&\
sudo apt-get install -y nodejs
instalar docker
-Uninstall old versions
 sudo apt-get remove docker docker-engine docker.io containerd runc
atualizar dependencias
```
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
    ```
- Add Docker’s official GPG key:
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
- Use the following command to set up the repository:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
-Install Docker Engine
```sudo apt-get update
sudo chmod a+r /etc/apt/keyrings/docker.gpg
sudo apt-get update
```
e por ultimo:
```sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin```
Docker instalado!!!

instalar docker compose agora:
```
curl -SL https://github.com/docker/compose/releases/download/v2.16.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose 
sudo apt install docker-compose
```
instalar YARN via npm:

```sudo npm install --global yarn```
```yarn -v```
yarn instalado!

# Clonando projeto na VM

```
mkdir app
cd app
git clone <link-do-projeto>
cd projeto
yarn 
yarn build 
```

Agora você deve configurar suas variaveis de sistemas necessarias para o projeto...

# Aplique permissoes ao docker
```
sudo groupadd docker
sudo usermod -aG docker $USER
```

Agora configure/crie seu container docker ou crie seu docker-compose para utilizar seu banco de dados desejado.
