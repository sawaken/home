provision
=========

## client-local-main
```
# client-local-main01のVMを起動する (初回起動時はansibleも流れる)
vagrant up client-local-main01
# ホストマシンからclinet-local-main01にansibleだけ流したい場合
vagrant provision client-local-main
# client-local-main01から自分自身にansibleを流したい場合
vagrant ssh client-local-main01
cd /mono/provision
ansible-playbook -i inventory/hosts.yml playbooks/construct.yml -l client-local-main01 -c local
```

## windows-local-main
```
# windows-local-main01でWinRMを有効化する
PS> winrm quickconfig
# client-local-main01からwindows-local-main01にansibleを流す
ansible-playbook -i inventory/hosts.yml playbooks/construct.yml -l windows-local-main01
# windows-local-main01からclient-local-main01にSSH接続したい場合
ssh client-local-main01
```
