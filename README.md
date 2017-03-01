# Criando Ambiente no Vagrant utilizando provisionamento Ansible

Este é um exemplo para realizar a configuração de um ambiente de testes para wordpress. Utilizei as ferramentas Vagrant e Ansible para a criação deste ambiente.

# Para iniciar os testes em uma máquina UBUNTU realize os seguintes comandos


**1** - sudo apt-get install virtualbox

**2** - sudo apt-get install vagrant

**3** - sudo apt-get install virtualbox-dkms

**4** - sudo apt-get install software-properties-common

**5** - sudo apt-add-repository ppa:ansible/ansible

**6** - sudo apt-get update

**7** - sudo apt-get install ansible


Ir para a pasta do projeto (onde está o arquivo Vagrantfile)


**8** - mkdir vars

**9** - cd vars

**10** - vim mysql.yml (Ao invés do vim pode utilizar o editor que preferir)

Copie o conteúdo abaixo e coloque no arquivo mysql.yml alterando as entradas que desejar:

  mysql_root_password: **senha de root**
	
  mysql_wp_user: **usuário mysql para wordpress**
	
  mysql_wp_password: **senha do usuário mysql para wordpress**
	
  wordpress_db_name: **nome da database do mysql**  
  
**11** - vim wordpress.yml (Ao invés do vim pode utilizar o editor que preferir)

Copie o conteúdo abaixo e coloque no arquivo wordpress.yml alterando as entradas que desejar: *Obs. A variável url é a mesma que está no arquivo Vagrantfile, portanto caso altere o ip, deve ser alterado tambem a variável url*.

  dir_wordpress: **diretório onde irá ser instalado o wordpress**  
	
  url: 192.168.33.10  
	
  titulo_wordpress: **título do site**  
	
  admin_wordpress: **usuário admin do painel do wordpress**  
	
  admin_pass_wordpress: **senha do usuário admin do painel do wordpress** 
	
  admin_email_wordpress: **email do usuário admin do painel do wordpress**
  
**12** - Vagrant up
 
 
Após isso seu site wordpress poderá ser acessado localmente pelo IP 192.168.33.10

*Obs: Caso deseje outro ip altere nos arquivos Vagrantfile e vars/wordpress*
