# Домашнее задание к занятию «Инструменты Git»

## Задание

В клонированном репозитории:

1. Найдите полный хеш и комментарий коммита, хеш которого начинается на `aefea`.
```
root@git-km ~/terraform-analysis (main) # git log --oneline --all | grep "aefea"
aefead2207 Update CHANGELOG.md
root@git-km ~/terraform-analysis (main) # git show aefead2207
commit aefead2207ef7e2aa5dc81a34aedf0cad4c32545
Author: Alisdair McDiarmid <alisdair@users.noreply.github.com>
Date:   Thu Jun 18 10:29:58 2020 -0400

    Update CHANGELOG.md
```
2. Ответьте на вопросы.

* Какому тегу соответствует коммит `85024d3`?
```
root@git-km ~/terraform-analysis (main) # git describe --tags 85024d3
v0.12.23
root@git-km ~/terraform-analysis (main) # git show 85024d3
commit 85024d3100126de36331c6982bfaac02cdab9e76 (tag: v0.12.23)
Author: tf-release-bot <terraform@hashicorp.com>
Date:   Thu Mar 5 20:56:10 2020 +0000

    v0.12.23
```

* Сколько родителей у коммита `b8d720`? Напишите их хеши.
```
root@git-km ~/terraform-analysis (main) # git show --pretty=%P b8d720 | wc -w
2
root@git-km ~/terraform-analysis (main) # git show --pretty=%P b8d720
56cd7859e05c36c06b56d013b55a252d0bb7e158 9ea88f22fc6269854151c571162c5bcf958bee2b
```

* Перечислите хеши и комментарии всех коммитов, которые были сделаны между тегами  v0.12.23 и v0.12.24.
```
root@git-km ~/terraform-analysis (main) # git log v0.12.23..v0.12.24 --oneline --no-merges
33ff1c03bb (tag: v0.12.24) v0.12.24
b14b74c493 [Website] vmc provider links
3f235065b9 Update CHANGELOG.md
6ae64e247b registry: Fix panic when server is unreachable
5c619ca1ba website: Remove links to the getting started guide's old location
06275647e2 Update CHANGELOG.md
d5f9411f51 command: Fix bug when using terraform login on Windows
4b6d06cc5d Update CHANGELOG.md
dd01a35078 Update CHANGELOG.md
225466bc3e Cleanup after v0.12.23 release
```

* Найдите коммит, в котором была создана функция `func providerSource`, её определение в коде выглядит так: `func providerSource(...)` (вместо троеточия перечислены аргументы).
```
root@git-km ~/terraform-analysis (main) # git log -S "func providerSource(" --oneline
8c928e8358 main: Consult local directories as potential mirrors of providers
```

* Найдите все коммиты, в которых была изменена функция `globalPluginDirs`.
```
### 26.04.2026 git clone https://github.com/hashicorp/terraform.git terraform-analysis функцию `globalPluginDirs` не обнаружил, только `GlobalPluginDirs()`

root@git-km ~/terraform-analysis (main) # git grep 'func global'
internal/logging/logging.go:func globalLogLevel() (hclog.Level, bool) {
root@git-km ~/terraform-analysis (main) # git grep 'func Global'
internal/command/cliconfig/plugins.go:func GlobalPluginDirs() []string {
root@git-km ~/terraform-analysis (main) # git log -L :GlobalPluginDirs:internal/command/cliconfig/plugins.go --oneline -s
7c4aeac5f3 stacks: load credentials from config file on startup (#35952)
78b1220558 Remove config.go and update things using its aliases
52dbf94834 keep .terraform.d/plugins for discovery
41ab0aef7a Add missing OS_ARCH dir to global plugin paths
66ebff90cd move some more plugin search path logic to command
8364383c35 Push plugin discovery down into command package
root@git-km ~/terraform-analysis (main) # git log -S "globalPluginDirs" --oneline
7c4aeac5f3 stacks: load credentials from config file on startup (#35952)
65c4ba7363 Remove terraform binary
125eb51dc4 Remove accidentally-committed binary
22c121df86 Bump compatibility version to 1.3.0 for terraform core release (#30988)
7c7e5d8f0a Don't show data while input if sensitive
35a058fb3d main: configure credentials from the CLI config file
c0b1761096 prevent log output during init
8364383c35 Push plugin discovery down into command package
```

* Кто автор функции `synchronizedWriters`? 
```
root@git-km ~/terraform-analysis (main) # git log -S'func synchronizedWriters' --oneline
bdfea50cc8 remove unused
5ac311e2a9 main: synchronize writes to VT100-faker on Windows
root@git-km ~/terraform-analysis (main) # git checkout 5ac311e2a9
Note: switching to '5ac311e2a9'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at 5ac311e2a9 main: synchronize writes to VT100-faker on Windows
root@git-km ~/terraform-analysis ((HEAD detached at 5ac311e2a9)) # git blame -L 15,15 synchronized_writers.go
5ac311e2a91 (Martin Atkins 2017-05-03 16:25:41 -0700 15) func synchronizedWriters(targets ...io.Writer) []io.Writer {

```

*В качестве решения ответьте на вопросы и опишите, как были получены эти ответы.*
