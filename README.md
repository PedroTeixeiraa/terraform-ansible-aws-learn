# Infraestrutura como código: preparando máquinas na AWS com Ansible e Terraform
Este repositório contém um projeto de infraestrutura como código para criar uma instância na AWS utilizando o Terraform para gerenciar a infraestrutura e o Ansible para provisionar a instância.

## Pré-requisitos
Antes de começar, você precisa instalar as seguintes ferramentas:

* Terraform
* Ansible
* AWS CLI


Para instalar o `Terraform`, você pode executar os seguintes comandos no terminal:

```bash
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform

```
Para instalar o `Ansible`, você pode executar os seguintes comandos no terminal:

```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt-get install ansible
```
Para instalar e configurar a AWS CLI, você pode seguir as instruções disponíveis na documentação oficial da AWS.

## Configuração
Antes de criar a instância na AWS, você precisa alterar a variável `key_name` do arquivo `main.tf` com o nome da chave gerada na AWS.

Depois de configurar a variável `key_name`, você pode criar a instância executando os seguintes comandos:

```bash
terraform init
terraform apply
```

Após a criação da instância, você precisa alterar o arquivo `hosts.yml`, colocando o endereço IP da instância criada na AWS.

Por fim, você pode executar o playbook do Ansible para provisionar a instância, executando o seguinte comando:

```bash
ansible-playbook playbook.yml -u ubuntu --private-key <chave.pem> -i hosts.yml
```

Lembre-se de substituir `<chave.pem>` pelo caminho para o arquivo `.pem` da chave gerada na AWS.