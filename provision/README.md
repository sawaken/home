provision
=========

### Vagrantでclient-local-mainのVMを立てる
```
# client-local-main01のVMを起動する (provisionはまだ流さない)
PS> vagrant up client-local-main01 --no-provision
# VM内の/etc/pass/vault_pass.txtにvault-passを格納する
PS> vagrant ssh client-local-main01 -c "sudo mkdir /etc/ansible && sudo vi /etc/ansible/vault_pass.txt"
# VMにansibleを流す
PS> vagrant provision client-local-main01
```

## client-local-mainからwindows-local-mainを構築する
```
# windows-local-main01においてWinRMを有効化する
PS> winrm quickconfig
# client-local-main01からwindows-local-main01にansibleを流す
PS> vagrant ssh client-local-main01 -c "sudo su - owner"
$ cd /var/data/home/provision && ansible-playbook -i inventory/hosts.yml playbooks/construct.yml -l windows-local-main01
# windows-local-main01からowner@client-local-main01にSSH接続できるようになっているはず
PS> ssh owner@client-local-main01
```
