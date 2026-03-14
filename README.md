# devops-netology

Первое редактирование файла п.8

Вывод команд после клонирования репозитория 
```bash
root@git-km ~/devops-netology (main) # git config --list --show-origin
file:/root/.gitconfig   user.name=Kirill Gilels
file:/root/.gitconfig   user.email=arekan@mail.ru
file:/root/.gitconfig   core.editor=mcedit
file:.git/config        core.repositoryformatversion=0
file:.git/config        core.filemode=true
file:.git/config        core.bare=false
file:.git/config        core.logallrefupdates=true
file:.git/config        remote.origin.url=https://github.com/olerakon/devops-netology.git
file:.git/config        remote.origin.fetch=+refs/heads/*:refs/remotes/origin/*
file:.git/config        branch.main.remote=origin
file:.git/config        branch.main.merge=refs/heads/main
root@git-km ~/devops-netology (main) # git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

`git diff` и `git diff --staged` показывают разные типы изменений в Git.

`git diff` показывает изменения которые еще не были добавлены с помощью `git add`.

`git diff --staged` "ступенчатая разница" показывает измения в файле подготовленном к коммиту.

В созданной директрии `terraform` был склонирован файл `.gitignore` который позволяет гиту пропускать следующее:

## terraform .gitignore :

1. `.terraform/`


   Игнорируются все файлы в директории `.terraform/`

3. `*.tfstate` и `*.tfstate.*`

   Игнорируются все файлы оканчивающся на .tfstate вида <что_угодно>.tfstate

   Игнорируются все файлы вида <что_угодно>.tfstate.<что_угодно>

4. `crash.log` и `crash.*.log`

   Игнорируется конкретный файл: crash.log

   Игнорируются все файлы вида crash.<что_угодно>.log

5. `*.tfvars` и `*.tfvars.json`

   Игнорируются все файлы оканчивающся на .tfvars вида <что_угодно>.tfvars

   Игнорируются все файлы оканчивающся на .tfvars.json вида <что_угодно>..tfvars.json

6. `override.tf`, `override.tf.json`, `*_override.tf`, `*_override.tf.json`

   Игнорируется конкретные файлы: override.tf и override.tf.json

   Игнорируются все файлы оканчивающся на _override.tf вида <что_угодно>_override.tf
 
   Игнорируются все файлы оканчивающся на _override.tf.json вида <что_угодно>_override.tf.json

7. `.terraform.tfstate.lock.info`, `.terraformrc`, `terraform.rc`

   Игнорируется конкретные файлы:

   .terraform.tfstate.lock.info

   .terraformrc

   terraform.rc
