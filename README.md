# devops-netology

Первое редактирование файла п.8
Вывод команд после клонирования репозитория 
```bash
root@git-km ~/devops-netology (main) # git config --list --show-origin                                 file:/root/.gitconfig   user.name=Kirill Gilels
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
