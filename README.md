# Infraestrutura como código: preparando máquinas na AWS com Ansible e Terraform

Este é um projeto que utiliza Terraform e Ansible para criar uma instância EC2 na AWS e provisioná-la com uma aplicação web Flask simples.

## Configuração do ambiente

### Instalação do Terraform

Para instalar o Terraform, execute os seguintes comandos:

```bash
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform
```

### Instalação do Ansible
Para instalar o Ansible, execute os seguintes comandos:

```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt-get install ansible
```

###  Configuração do AWS CLI

Para configurar o AWS CLI, acesse a página da AWS CLI e siga os procedimentos para o seu sistema operacional. Depois de instalado, você pode configurar a AWS usando o comando `aws configure`, onde será solicitado a chave secreta (secret key) que pode ser criada na página de credenciais do AWS IAM.

###  Criação da instância na AWS

Para criar a instância na AWS, execute os seguintes comandos:

```bash
terraform init
terraform apply
```

### Configuração do Ansible
Altere o arquivo hosts.yml, colocando o host da instância criada na AWS.

### Execução do Ansible
Para executar o Ansible, execute o seguinte comando:

```bash
ansible-playbook playbook.yml -u ubuntu --private-key <chave.pem> -i hosts.yml
```
Substitua <chave.pem> pelo caminho para a chave gerada na AWS.


