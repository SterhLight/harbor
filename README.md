# HARBOR

## Harbor install


## Предварительные требования

1. Установленный Ansible
2. Клонировать репозиторий
```bash
git clone git@github.com:SterhLight/harbor.git
```
3. Необходимо настроить доступ к целевому хосту с хоста с Ansible по ssh-ключу.  
Для этого на целевом хосте должен существовать одноименный пользователь с sudo-правами.  
В файл '$HOME/.ssh/authorized_keys' целевого хоста дописывается свой публичный ключ.  
На хосте с Ansible создается или редактируется файл '$HOME/.ssh/config'  
В нем необходимо указать DNS-имя целевого хоста и приватный ключ, посредством  
которого будет происходить подключение. Например:
```bash
Host harbor-test45.lab.local
  IdentityFile ~/.ssh/myserf
```
Данная запись должна находиться выши часных и общих, которые могут перекрывать собой эту.  
Проверка доступности хостов:
```bash
ansible -i hosts.ini -m ping all
```
Запуск установки Harbor  
Потребуется ввести пароль от root и пароль для Ansible-vault
```bash
ansible-playbook -i hosts.ini all.yml --ask-vault-pass -K
```
