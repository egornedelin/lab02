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
5. Закоммитьте изменения с *осмысленным* сообщением.
```sh
$ git commit -m "Added initial version of Hello world program with bad code style"
```
```sh
[main def2934] Added initial version of Hello world program with bad code style
 1 file changed, 8 insertions(+)
 create mode 100644 hello_world.cpp
```
6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение `Hello world from @name`, где `@name` имя пользователя.
   
**hello_world.cpp with greet user by name:**

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
```
7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно `git add`?
```sh
$ git commit -am "Modified program to greet user by name"
```
```
[main e2472be] Modified program to greet user by name

1 file changed, 7 insertions(+), 4 deletions(-)
```
```sh
Потому что при первом добавлении файла в Git, он уже отслеживается системой контроля версий, и при последующем коммите изменений в этом файле, Git автоматически учитывает его изменения.
```
8. Запуште изменения в удалёный репозиторий.
```sh
$ git push origin main
```
```sh
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 6 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 838 bytes | 838.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/egornedelin/lab02.git
   825c8cd..e2472be  main -> main
```
### Part II
**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. В локальной копии репозитория создайте локальную ветку `patch1`.
```sh
$ git checkout -b patch1
```
```sh
Switched to a new branch 'patch1'
```
2. Внесите изменения в ветке `patch1` по исправлению кода и избавления от `using namespace std;`.
**hello_world.cpp with greet user by name without `using namespace std;`:**
```sh
#include <iostream>
#include <string>

int main()
{
    std::string name;
    std::cout << "Enter your name: ";
    std::cin >> name;
    std::cout << "Hello world from " << name << std::endl;
    return 0;
}
```
```sh
$ git add .
$ git commit -m "Removed using namespace std;"
```
```sh
[patch1 5a2ecc2] Removed using namespace std;
1 file changed, 6 insertions(+), 6 deletions(-)
```
3. **commit**, **push** локальную ветку в удалённый репозиторий.
```sh
$ git push origin patch1
```
```sh
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 6 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 436 bytes | 436.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'patch1' on GitHub by visiting:
remote:      https://github.com/egornedelin/lab02/pull/new/patch1
remote: 
To https://github.com/egornedelin/lab02.git
 * [new branch]      patch1 -> patch1
```

4. В локальной копии в ветке `patch1` добавьте в исходный код комментарии.
**hello_world.cpp with greet user by name, without `using namespace std;`, with commentaries:**
```sh
#include <iostream>
#include <string>

int main()
{
  std::string name;
  std::cout << "Enter your name: ";
  std::cin >> name; // write here your name, please!
  std::cout << "Hello world from " << name << std::endl;
  return 0;
}
```
```sh
$ git add .
$ git commit -m "Added comments to the code"
$ git push origin patch1
```
```sh
[patch1 e782d75] Added comments to the code
 1 file changed, 5 insertions(+), 5 deletions(-)
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 6 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 443 bytes | 443.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/egornedelin/lab02.git
   5a2ecc2..e782d75  patch1 -> patch1
```
5. Локально выполните **pull**.
```sh
$ git checkout main  
$ git pull origin main 
```
```sh
Switched to branch 'main'
Your branch is up to date with 'origin/main'.
remote: Enumerating objects: 1, done.
remote: Counting objects: 100% (1/1), done.
remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (1/1), 906 bytes | 906.00 KiB/s, done.
From https://github.com/egornedelin/lab02
 * branch            main       -> FETCH_HEAD
   e2472be..352d9a0  main       -> origin/main
Updating e2472be..352d9a0
Fast-forward
 hello_world.cpp | 10 +++++-----
 1 file changed, 5 insertions(+), 5 deletions(-)
```
6. С помощью команды **git log** просмотрите историю в локальной версии ветки `master`.
```sh
$ git log
```
```sh
commit 352d9a047d8f60f42cf6faf7ca15b9fba01622f5 (HEAD -> main, origin/main, origin/HEAD)
Merge: e2472be e782d75
Author: egornedelin <145435742+egornedelin@users.noreply.github.com>
Date:   Thu Apr 4 11:35:02 2024 +0300

    Merge pull request #1 from egornedelin/patch1
    
    Removed using namespace std;

commit e782d752306a487d0654002aad8700168acea368 (origin/patch1, patch1)
Author: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Date:   Thu Apr 4 11:34:06 2024 +0300

    Added comments to the code

commit 5a2ecc2b9ea416859fec7357cb4f7bfd1cf8acd8
Author: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Date:   Thu Apr 4 11:29:51 2024 +0300

    Removed using namespace std;

commit e2472bed8c17217c2cf08c0b0711092099f040f9
Author: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Date:   Thu Apr 4 11:28:31 2024 +0300

    Modified program to greet user by name

commit def293450c4daeb95b22db80a00d74d448c62c2e
Author: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Date:   Thu Apr 4 11:27:58 2024 +0300

    Added initial version of Hello world program with bad code style

commit 825c8cd97e177a1f0654504c0c637195bf29e88d
Author: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Date:   Thu Apr 4 11:24:45 2024 +0300

    first commit

commit fd76c46438012d99b5728d25a6bced70da83dfc7
Author: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Date:   Thu Apr 4 11:22:00 2024 +0300

    first commit

commit 3d95044619d905efed0f99f17c8248b65fdca0a3
Author: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Date:   Thu Apr 4 11:19:12 2024 +0300

    first commit

commit 1c46836f4ad7064c35754e7c6b1786e0900ced78
Author: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Date:   Thu Apr 4 11:18:05 2024 +0300

    first commit

commit 6b82c363ec3c496e2bf918567a31fb43031419d0
Author: vboxuser <vboxuser@linux1.myguest.virtualbox.org>
Date:   Thu Apr 4 11:12:15 2024 +0300

    first commit

[1]+  Stopped                 git log
```
7. Удалите локальную ветку `patch1`.
```sh
$ git branch -d patch1
```
```sh
Deleted branch patch1 (was e782d75).
```

### Part III

**Note:** *Работать продолжайте с теми же репоззиториями, что и в первой части задания.*
1. Создайте новую локальную ветку `patch2`.
2. Измените *code style* с помощью утилиты [**clang-format**](http://clang.llvm.org/docs/ClangFormat.html). Например, используя опцию `-style=Mozilla`.
3. **commit**, **push**, создайте pull-request `patch2 -> master`.
```sh
$ clang-format -i -style=Mozilla hello_world.cpp
$ git checkout -b patch2
$ git add .
$ git commit -m "Changed code style using clang-format"
```
```sh
Switched to a new branch 'patch2'
nothing to commit, working tree clean
```
4. В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.

**hello_world.cpp with greet user by name, without `using namespace std;`, with new commentaries. Code style: clang-format:**
```sh
#include <iostream>
#include <string>

int main()
{
  std::string name;
  std::cout << "Enter your name: ";
  std::cin >> name; // напишите здесь свое имя!!!
  std::cout << "Hello world from " << name << std::endl;
  return 0;
}
```
```sh
$ git add .
$ git commit -m "Updated comments in the code"
```
```sh
[patch2 9555e1b] Updated comments in the code
 1 file changed, 1 insertion(+), 1 deletion(-)
```
```sh
git push origin patch2
```
```sh
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 6 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 386 bytes | 386.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'patch2' on GitHub by visiting:
remote:      https://github.com/egornedelin/lab02/pull/new/patch2
remote: 
To https://github.com/egornedelin/lab02.git
 * [new branch]      patch2 -> patch2

```
5. Для этого локально выполните **pull** + **rebase** (точную последовательность команд, следует узнать самостоятельно). **Исправьте конфликты**.
```sh
$ git checkout patch2
$ git pull --rebase origin main
$
```
```sh
Already on 'patch2'
From https://github.com/Adam-dunno/lab02
 * branch            main       -> FETCH_HEAD
Current branch patch2 is up to date.
```

**Исправьте конфликт**.


```sh
$ git add .
   git rebase --continue
```
```sh
fatal: No rebase in progress?
```
6. Сделайте *force push* в ветку `patch2`
```sh
$    git push origin patch2 --force
```
```sh
Everything up-to-date
```

**проверка запуска программы**:


```sh
$ gcc hello_world.cpp -o hello_world
```






```sh
/usr/bin/ld: /tmp/ccjnomep.o: warning: relocation against `_ZSt4cout' in read-only section `.text'
/usr/bin/ld: /tmp/ccjnomep.o: in function `main':
hello_world.cpp:(.text+0x24): undefined reference to `std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string()'
/usr/bin/ld: hello_world.cpp:(.text+0x35): undefined reference to `std::cout'
/usr/bin/ld: hello_world.cpp:(.text+0x3d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/usr/bin/ld: hello_world.cpp:(.text+0x4b): undefined reference to `std::cin'
/usr/bin/ld: hello_world.cpp:(.text+0x53): undefined reference to `std::basic_istream<char, std::char_traits<char> >& std::operator>><char, std::char_traits<char>, std::allocator<char> >(std::basic_istream<char, std::char_traits<char> >&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >&)'
/usr/bin/ld: hello_world.cpp:(.text+0x64): undefined reference to `std::cout'
/usr/bin/ld: hello_world.cpp:(.text+0x6c): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/usr/bin/ld: hello_world.cpp:(.text+0x7e): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <char, std::char_traits<char>, std::allocator<char> >(std::basic_ostream<char, std::char_traits<char> >&, std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
/usr/bin/ld: hello_world.cpp:(.text+0x85): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
/usr/bin/ld: hello_world.cpp:(.text+0x90): undefined reference to `std::ostream::operator<<(std::ostream& (*)(std::ostream&))'
/usr/bin/ld: hello_world.cpp:(.text+0xa1): undefined reference to `std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/usr/bin/ld: hello_world.cpp:(.text+0xc7): undefined reference to `std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> >::~basic_string()'
/usr/bin/ld: /tmp/ccjnomep.o: in function `__static_initialization_and_destruction_0(int, int)':
hello_world.cpp:(.text+0x10d): undefined reference to `std::ios_base::Init::Init()'
/usr/bin/ld: hello_world.cpp:(.text+0x128): undefined reference to `std::ios_base::Init::~Init()'
/usr/bin/ld: /tmp/ccjnomep.o:(.data.rel.local.DW.ref.__gxx_personality_v0[DW.ref.__gxx_personality_v0]+0x0): undefined reference to `__gxx_personality_v0'
/usr/bin/ld: warning: creating DT_TEXTREL in a PIE
collect2: error: ld returned 1 exit status
```


