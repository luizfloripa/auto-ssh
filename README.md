# auto-ssh
## 💻 Pré-requisitos

Antes de começar, verifique se você atendeu aos seguintes requisitos:
* Você instalou o ansible
* Você tem uma máquina `Linux`.
* Você já tomou ☕ hoje =).
## ☕ Usando auto-ssh

Seguem alguns exemplo_de_uso:

```
ansible-playbook -i <inventory> -b _deploy/<allow|deny>/deploy.yml --tags <url|file&production|staging> -ekey_path='<key_path>'
```
Adicionando uma chave a partir de uma url no ambiente staging
```
ansible-playbook -i inventory/staging -b _deploy/allow/deploy.yml --tags url,staging -ekey_path='https://github.com/luizfloripa.keys'
```

Adicionando uma chave a partir de um arquivo no ambiente staging
```
ansible-playbook -i inventory/staging -b _deploy/allow/deploy.yml --tags file,staging -ekey_path='/home/luiz/.ssh/id_rsa.pub'
```

Removendo uma chave a partir de uma url no ambiente produção
```
ansible-playbook -i inventory/production -b _deploy/deny/deploy.yml --tags url,production -ekey_path='https://github.com/luizfloripa.keys'
```

Adicionando uma chave no localhost
```
ansible-playbook -i inventory -b _deploy/allow/deploy.yml --tags url -ekey_path='https://github.com/luizfloripa.keys' -edev_user=xpto -edev_groups=sudo
```

## 📫 Algumas melhorias possíveis

1. Usar o ansible-vault encrypt para as variáveis.
2. Criar uma imagem docker para rodar o ansible.
