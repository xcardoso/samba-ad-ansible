# SAMBA4 Ansible Installer Free

Este projeto tem como intuíto facilitar a vida de **SysAdmins**, esta é uma versão **simplicada** e disponibilizada **gratuitamente**


## Comercialização

**O compartilhamento e edição desta versão é permitido desde que se mantenha os direitos autorais**

**Comercializo uma versão completa** á qual é disponibilizada DCs adicionais com sysvol em cluster, FileServer, Upgrades de Versão homologadas mantendo sempre o seu ambiente atualizado.

Para maiores informações entre em contato pelo e-mail yuri.bucci@outlook.com


## Requerimentos
#
+ [Ansible](https://docs.ansible.com/ansible/latest/index.html)

## Como Usar
#
## Tags Disponíveis
```
init - Instala os pacotes necessários para compilação

install - Instala o Samba4

provision - Provisiona o Domínio

configure - Configura requerimentos para funcionamento

all - Executa todos os passos anteriores
```

## 1.Passo

```
Edite o arquivo samba-ad-ansible/env/1-master/group_vars/all/master_configuration.yml com os campos pedidos
```

## 2.Passo

```
Edite o arquivo samba-ad-ansible/env/1-master/hosts o servidor
```

## 3.Passo

```
cd samba-ad-ansible
ansible-playbook -i env/1-master/ --tags=all
```


## Dicas de uso:
#

## CRIACAO DE PASTAS

* CRIE NOVAS PASTAS UTILIZANDO O COMANDO 'mkdir folder/'

* SEMPRE ALTERE AS PERMISSÕES COM O COMANDO 'chown root.'Domain Admins' folder/ -R' (ASPAS DUPLAS EM DOMAIN ADMINS)

#
## BACKUP

* UTILIZE O VEEAMBACKUP ATRAVES DO COMANDO 'veeamconfig ui'

* SEMPRE UTILIZE O BACKUP A NIVEL DE PARTICAO E/OU LVM PARA QUE AS PERMISSOES EXTENDIDAS FUNCIONEM

* ADICIONE OS SCRIPTS NA CRIAÇÃO DO BACKUP: /etc/veeam/scripts/pre.sh (REALIZA O BACKUP DO SAMBA4) E /etc/veeam/scripts/email.sh (ENVIA O E-MAIL)
#
## COMANDOS UTEIS

* samba-tool ntacl sysvolreset - RESETA AS PERMISSÕES DAS PASTAS SYSVOL E GPOS

* samba-tool dbcheck --cross-ncs --fix --yes (VERIFICA O BANCO DE DADOS DO SAMBA E REPARA O MESMO)

* samba-tool dbcheck --reindex (REINDEXA O BANCO DE DADOS)

* samba_dnsupdate --all-names --verbose (ATUALIZA O DNS BIND)
#

## ADMINISTRACAO DO DOMINIO

* ADICIONE UMA MAQUINA WINDOWS NO DOMINIO E INSTALE O RSAT PARA ADMINISTRACAO DO SEU DOMINIO

* CONFIGURE O DNS REVERSO

* DESABILITE A EXPIRACAO DE SENHA DO ADMINISTRATOR