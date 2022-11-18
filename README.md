# Local Docker Registry

Este projeto trata da implementação de um registry docker privado para testes dentro de uma infraestrutura local, foi criado para me auxiliar não só nos meus  estudos com o Docker mas também como um importante exercício para colocar os conhecimentos de outras ferramentas em prática. Todo o projeto foi feito utilizando as ferramentas Vagrant(com Virtualbox como hypervisor) e Ansible.

# Vagrant
O Vagrantfile realiza as definições comuns nesse tipo de projeto(alocação de recursos, configuração de ip, etc) porém no provisionamento eu utilizei algumas funcionalidades que precisam ser destacadas. Eu optei pelo provisioner ansible_local, com ele Vagrant tenta instalar e utilizar o Ansible dentro da VM ao invés de utilizar a instalação do Ansible presente no host, normalmente o Vagrant é capaz de fazer todo o processo de instalação porém eu gosto de instalar o Ansible do 'meu jeito' para isso eu fiz o uso desse [bash script](https://github.com/fermino-linux/bash-training/blob/main/ansible/install.sh) que havia desenvolvido antes.

# Ansible
Escrevi uma playbook de arquivo único ao invés de usar o esquema de roles, a minha playbook realiza as seguintes configurações:

* Prepara o yum
* Instalação de utilidades(coisas como o GIT, por exemplo).
* Adiciona o repositório do Docker e realiza a instalação
* Instala o Docker-SDK(necessário para usar o módulo community.docker)
* Cria o container do registry

# Executando
```
vagrant up
``` 





