# lab02
# Tutorial
Part I
1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.
```sh
$ echo "# lab02" >> README.md
$ git init
$ git add README.md
$ git commit -m "first commit"
$ git branch -M main
$ git remote add origin https://github.com/egornedelin/lab02.git
$ git push -u origin main
```
```sh
Reinitialized existing Git repository in /home/vboxuser/.git/
[main 825c8cd] first commit
 Committer: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly. Run the
following command and follow the instructions in your editor to edit
your configuration file:

    git config --global --edit

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author

 1 file changed, 3 deletions(-)
error: remote origin already exists.

Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Writing objects: 100% (3/3), 260 bytes | 260.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/egornedelin/lab02.git
   fd76c46..825c8cd  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```
```sh
$ git clone https://github.com/egornedelin/lab02.git
```
```sh
Cloning into 'lab02'...
remote: Enumerating objects: 13, done.
remote: Counting objects: 100% (13/13), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 13 (delta 1), reused 13 (delta 1), pack-reused 0
Receiving objects: 100% (13/13), done.
Resolving deltas: 100% (1/1), done.
```
3. Создайте файл hello_world.cpp в локальной копии репозитория . Реализуйте программу Hello world на языке C++ используя плохой стиль кода.
```sh
$ cd lab02
$ touch hello_ world.cpp
```
Hello world.cpp
```sh
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello world!" << endl;
    return 0;
}
```
4. Добавьте этот файл в локальную копию репозитория.
```sh
$ git add hello_world.cpp
```
5. Закоммитьте изменения с осмысленным сообщением.
```sh
$ git commit -m "Added initial version of Hello world program with bad code style"
```
```sh
[main def2934] Added initial version of Hello world program with bad code style
 1 file changed, 8 insertions(+)
 create mode 100644 hello_world.cpp
```
7. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.
```sh
#include <iostream>
#include <string>
using namespace std; 
int main()
{
  string name;
  cout << "Enter your name: ";
  cin >> name;
  cout << "Hello world from " << name << endl;
  return 0;
}
```sh
Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?
```
```sh


