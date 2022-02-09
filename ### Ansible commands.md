### Commandos e comentários sobre o Ansible

- ansible-playbook <file.yml> -u <user> -i <file hosts> --private-key <local key file>
- ansible-playbook provisioning.yml -u vagrant -i hosts --private-key ssh-keys/vagrant_id_rsa
<!-- Esse comando executa um arquivo playbook do Ansible que tem configurações para realizar na VM -->
<!-- | -u é o usuário | -i é o arquivo de inventário com os IPs das máquinas | --private-key é a chave ssh usada na conexão com a VM -->

- É possível abstrair o usuário e a private_key do comando, inserindo essas informações dentro do arquivo Hosts.
    Ficando assim:  <ip da VM> ansible_user=<nome do usuário> ansible_ssh_private_key_file=<caminho do arquivo da private_key>
    <!-- EX: 192.168.1.101 ansible_user=vagrant ansible_ssh_private_key_file="ssh-keys/vagrant_id_rsa" -->
    Dessa forma também é possível configurar o acesso para outras máquinas já passando suas credencias.
    Após isso o comando para rodar o playbook fica assim:
    - ansible-playbook <file playbook.yml> -i <file hosts>