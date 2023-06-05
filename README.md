<<<<<<< HEAD
# laba-4etverka
Сейчас вам требуется настроить систему непрерывной интеграции для библиотек и приложений, с которыми вы работали в прошлый раз. Настройте сборочные процедуры на различных платформах:

# Task 1
Используйте GitHub Actions для сборки на операционной системе Linux с использованием компиляторов gcc и clang

# Копируем репозиторий из предыдущей ЛР:
```sh
(kali㉿kali)-[~]
└─$ cd HECCYLLIujTbmy/workspace/projects && mkdir laba-4etverka && cd laba-4etverka
$ git clone https://github.com/HECCYLLIujTbmy/lab03                    
Cloning into 'lab03'...
remote: Enumerating objects: 121, done.
remote: Counting objects: 100% (50/50), done.
remote: Compressing objects: 100% (19/19), done.
remote: Total 121 (delta 42), reused 31 (delta 31), pack-reused 71
Receiving objects: 100% (121/121), 1.03 MiB | 1.31 MiB/s, done.
Resolving deltas: 100% (60/60), done.
```

```sh
kali㉿kali)-[~/HECCYLLIujTbmy/workspace/projects/laba-4etverka]
└─$ git init                                         
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint:   git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint:   git branch -m <name>
Initialized empty Git repository in /home/kali/HECCYLLIujTbmy/workspace/projects/laba-4etverka/.git/
```
```sh
cat>> Linux.yml<<EOF
name: CMake
on:
push:
branches: [master]
pull_request:
branches: [master]
jobs:
build_Linux:
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v3
- name: Configure Solver
run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build
- name: Build Solver
run: cmake --build ${{github.workspace}}/solver_application/build
- name: Configure HelloWorld
run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build
- name: Build HelloWorld
run: cmake --build ${{github.workspace}}/hello_world_application/build
EOF
```
```sh
(kali㉿kali)-[~/HECCYLLIujTbmy/workspace/projects/laba-4etverka]
└─$ git status                                       
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Linux.yml
        lab03/

nothing added to commit but untracked files present (use "git add" to track)
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/HECCYLLIujTbmy/workspace/projects/laba-4etverka]
└─$ git add Linux.yml
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/HECCYLLIujTbmy/workspace/projects/laba-4etverka]
└─$ git commit -m"Linux.yml - 1"                     
[master (root-commit) 6d8cfb9] Linux.yml - 1
 1 file changed, 27 insertions(+)
 create mode 100644 Linux.yml
 ```
 ```sh
 $ git push origin master
Username for 'https://github.com': HECCYLLIujTbmy
Password for 'https://HECCYLLIujTbmy@github.com': 
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Delta compression using up to 2 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 467 bytes | 467.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/HECCYLLIujTbmy/laba-4etverka
 * [new branch]      master -> master
 ```

# Task II 

```sh
(kali㉿kali)-[~/HECCYLLIujTbmy/workspace/projects/laba-4etverka]
└─$ cat >> Windows.yml <<EOF
name: CMake

on:
 push:
  branches: [master]
 pull_request:
  branches: [master]

jobs: 
 build_Windows:

  runs-on: windows-latest

  steps:
  - uses: actions/checkout@v3

  - name: Configure Solver
    run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build

  - name: Build Solver
    run: cmake --build ${{github.workspace}}/solver_application/build

  - name: Configure HelloWorld
    run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build

  - name: Build HelloWorld
    run: cmake --build ${{github.workspace}}/hello_world_application/build

EOF
```
```sh
git status            
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Windows.yml
        lab03/
 nothing added to commit but untracked files present (use "git add" to track)
```
```sh
(kali㉿kali)-[~/HECCYLLIujTbmy/workspace/projects/laba-4etverka]
└─$ git commit -m"Windows.yml - 1"
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Windows.yml
        lab03/
```

```sh
(kali㉿kali)-[~/HECCYLLIujTbmy/workspace/projects/laba-4etverka]
└─$ git pull origin master         
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 2.16 KiB | 2.16 MiB/s, done.
From https://github.com/HECCYLLIujTbmy/laba-4etverka
 * branch            master     -> FETCH_HEAD
   6d8cfb9..3d18e38  master     -> origin/master
Updating 6d8cfb9..3d18e38
Fast-forward
 README.md | 94 ++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
 1 file changed, 94 insertions(+)
 create mode 100644 README.md
```

```sh
(kali㉿kali)-[~/HECCYLLIujTbmy/workspace/projects/laba-4etverka]
└─$ git commit -m"Windows.yml - 1" 
[master 21d77bd] Windows.yml - 1
 1 file changed, 27 insertions(+)
 create mode 100644 Windows.yml
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/HECCYLLIujTbmy/workspace/projects/laba-4etverka]
└─$ git push origin master        
Username for 'https://github.com': HECCYLLIujTbmy
Password for 'https://HECCYLLIujTbmy@github.com': 
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 2 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 569 bytes | 569.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To https://github.com/HECCYLLIujTbmy/laba-4etverka
   3d18e38..21d77bd  master -> master
                                        
=======
## Laboratory work III

Данная лабораторная работа посвещена изучению систем автоматизации сборки проекта на примере **CMake**

```sh
$ open https://cmake.org/
```

## Tasks

- [ ] 1. Создать публичный репозиторий с названием **lab03** на сервисе **GitHub**
- [ ] 2. Ознакомиться со ссылками учебного материала
- [ ] 3. Выполнить инструкцию учебного материала
- [ ] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

```sh
$ export GITHUB_USERNAME=<имя_пользователя>
```

```sh
$ cd ${GITHUB_USERNAME}/workspace
$ pushd .
$ source scripts/activate
```

```sh
$ git clone https://github.com/${GITHUB_USERNAME}/lab02.git projects/lab03
$ cd projects/lab03
$ git remote remove origin
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03.git
```

```sh
$ g++ -std=c++11 -I./include -c sources/print.cpp
$ ls print.o
$ nm print.o | grep print
$ ar rvs print.a print.o
$ file print.a
$ g++ -std=c++11 -I./include -c examples/example1.cpp
$ ls example1.o
$ g++ example1.o print.a -o example1
$ ./example1 && echo
```

```sh
$ g++ -std=c++11 -I./include -c examples/example2.cpp
$ nm example2.o
$ g++ example2.o print.a -o example2
$ ./example2
$ cat log.txt && echo
```

```sh
$ rm -rf example1.o example2.o print.o
$ rm -rf print.a
$ rm -rf example1 example2
$ rm -rf log.txt
```

```sh
$ cat > CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.4)
project(print)
EOF
```

```sh
$ cat >> CMakeLists.txt <<EOF
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
EOF
```

```sh
$ cat >> CMakeLists.txt <<EOF
add_library(print STATIC \${CMAKE_CURRENT_SOURCE_DIR}/sources/print.cpp)
EOF
```

```sh
$ cat >> CMakeLists.txt <<EOF
include_directories(\${CMAKE_CURRENT_SOURCE_DIR}/include)
EOF
```

```sh
$ cmake -H. -B_build
$ cmake --build _build
```

```sh
$ cat >> CMakeLists.txt <<EOF

add_executable(example1 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example1.cpp)
add_executable(example2 \${CMAKE_CURRENT_SOURCE_DIR}/examples/example2.cpp)
EOF
```

```sh
$ cat >> CMakeLists.txt <<EOF

target_link_libraries(example1 print)
target_link_libraries(example2 print)
EOF
```

```sh
$ cmake --build _build
$ cmake --build _build --target print
$ cmake --build _build --target example1
$ cmake --build _build --target example2
```

```sh
$ ls -la _build/libprint.a
$ _build/example1 && echo
hello
$ _build/example2
$ cat log.txt && echo
hello
$ rm -rf log.txt
```

```sh
$ git clone https://github.com/tp-labs/lab03 tmp
$ mv -f tmp/CMakeLists.txt .
$ rm -rf tmp
```

```sh
$ cat CMakeLists.txt
$ cmake -H. -B_build -DCMAKE_INSTALL_PREFIX=_install
$ cmake --build _build --target install
$ tree _install
```

```sh
$ git add CMakeLists.txt
$ git commit -m"added CMakeLists.txt"
$ git push origin master
```

## Report

```sh
$ popd
$ export LAB_NUMBER=03
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER}
$ edit REPORT.md
$ gist REPORT.md
```

## Homework

Представьте, что вы стажер в компании "Formatter Inc.".
### Задание 1
Вам поручили перейти на систему автоматизированной сборки **CMake**.
Исходные файлы находятся в директории [formatter_lib](formatter_lib).
В этой директории находятся файлы для статической библиотеки *formatter*.
Создайте `CMakeList.txt` в директории [formatter_lib](formatter_lib),
с помощью которого можно будет собирать статическую библиотеку *formatter*.

```sh 
cd /home/kali/HECCYLLIujTbmy/workspace/projects/lab02/lab3_x3/lab03/formatter_lib/
```


```sh                                                            
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/formatter_lib]
└─$ cat > CMakeLists.txt
cmake_minimum_required(VERSION 3.4)^[[3~
^Z
zsh: suspended  cat > CMakeLists.txt
```                                                                                                                                                             

```sh                                                                       
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/formatter_lib]
└─$ cat > CMakeLists.txt               
cmake_minimum_required(VERSION 3.4)
project(formatter_lib)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_library(formatter_lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter.cpp)
^Z
zsh: suspended  cat > CMakeLists.txt
```                                                                                                                                                             ```sh                                                                      
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/formatter_lib]
└─$ cmake -B build
-- The C compiler identification is GNU 12.2.0
-- The CXX compiler identification is GNU 12.2.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/kali/HECCYLLIujTbmy/workspace/projects/lab02/lab3_x3/lab03/formatter_lib/build
```

```sh
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/formatter_lib]
└─$ cmake -B build
-- Configuring done
-- Generating done
-- Build files have been written to: /home/kali/HECCYLLIujTbmy/workspace/projects/lab02/lab3_x3/lab03/formatter_lib/build
```

```sh                                      
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/formatter_lib]
└─$ cmake --build build
[ 50%] Building CXX object CMakeFiles/formatter_lib.dir/formatter.cpp.o
[100%] Linking CXX static library libformatter_lib.a
[100%] Built target formatter_lib
                                   
```
### Задание 2
У компании "Formatter Inc." есть перспективная библиотека,
которая является расширением предыдущей библиотеки. Т.к. вы уже овладели
навыком созданием `CMakeList.txt` для статической библиотеки *formatter*, ваш 
руководитель поручает заняться созданием `CMakeList.txt` для библиотеки 
*formatter_ex*, которая в свою очередь использует библиотеку *formatter*.

```sh
$ cd formatter_ex_lib
```                                                                                                                                                             ```sh                                                                              
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/formatter_ex_lib]
└─$ cat > CMakeLists.txt
cmake_minimum_required(VERSION 3.4)
project(formatter_ex_lib)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib formatter_lib_dir)
add_library(formatter_ex_lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter_ex.cpp)
target_include_directories(formatter_ex_lib PUBLIC
${CMAKE_CURRENT_SOURCE_DIR}/../formatter_lib
)
target_link_libraries(formatter_ex_lib formatter_lib)
^Z
zsh: suspended  cat > CMakeLists.txt
```                                                                                                                                                             ```sh                                                                              
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/formatter_ex_lib]
└─$ cmake -B build
-- The C compiler identification is GNU 12.2.0
-- The CXX compiler identification is GNU 12.2.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/kali/HECCYLLIujTbmy/workspace/projects/lab02/lab3_x3/lab03/formatter_ex_lib/build
```
```sh
$ cmake --build build
[ 16%] Building CXX object formatter_ex_lib_dir/formatter_lib_dir/CMakeFiles/formatter_lib.dir/formatter.cpp.o
[ 33%] Linking CXX static library libformatter_lib.a
[ 33%] Built target formatter_lib
[ 50%] Building CXX object formatter_ex_lib_dir/CMakeFiles/formatter_ex_lib.dir/formatter_ex.cpp.o
[ 66%] Linking CXX static library libformatter_ex_lib.a
[ 66%] Built target formatter_ex_lib
[ 83%] Building CXX object CMakeFiles/hello_world.dir/hello_world.cpp.o
[100%] Linking CXX executable hello_world
[100%] Built target hello_world
```
### Задание 3
Конечно же ваша компания предоставляет примеры использования своих библиотек.
Чтобы продемонстрировать как работать с библиотекой *formatter_ex*,
вам необходимо создать два `CMakeList.txt` для двух простых приложений:
* *hello_world*, которое использует библиотеку *formatter_ex*;


```sh
(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/hello_world_application]
└─$ cat > CMakeLists.txt
cmake_minimum_required(VERSION 3.4)
project(hello_world)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex_lib_dir)
add_executable(hello_world ${CMAKE_CURRENT_SOURCE_DIR}/hello_world.cpp)
target_include_directories(hello_world PUBLIC
${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib
)    
^Z
zsh: suspended  cat > CMakeLists.txt
```                                                                                                                                                             ```sh                                                                             
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/hello_world_application]
└─$ cmake -B build
-- The C compiler identification is GNU 12.2.0
-- The CXX compiler identification is GNU 12.2.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/kali/HECCYLLIujTbmy/workspace/projects/lab02/lab3_x3/lab03/hello_world_application/build
```

```sh
kali㉿kali)-[~/…/lab02/lab3_x3/lab03/hello_world_application]
└─$ build/hello_world
-------------------------
hello, world!
-------------------------
```
* *solver*, приложение которое испольует статические библиотеки *formatter_ex* и *solver_lib*.

```sh
(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/solver_lib]
└─$ cat > CMakeLists.txt                                                           
cmake_minimum_required(VERSION 3.4)
project(solver)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex_lib_dir)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib solver_lib_dir)
add_executable(solver ${CMAKE_CURRENT_SOURCE_DIR}/equation.cpp)
target_include_directories(formatter_ex_lib PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib)
target_link_libraries(solver formatter_ex_lib solver_lib)
^Z
zsh: suspended  cat > CMakeLists.txt
```                                                                                                                                                                     ```sh                                                                       
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/solver_lib]
└─$ cd ..                                                                          
```                                                                                                                                                                     

```sh                                                                     
┌──(kali㉿kali)-[~/…/projects/lab02/lab3_x3/lab03]
└─$ cd solver_application
```                                                                                                                                                                    

```sh                                                                     
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/solver_application]
└─$ cat > CMakeLists.txt 
cmake_minimum_required(VERSION 3.4)
project(solver)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib formatter_ex_lib_dir)
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib solver_lib_dir)
add_executable(solver ${CMAKE_CURRENT_SOURCE_DIR}/equation.cpp)
target_include_directories(formatter_ex_lib PUBLIC
${CMAKE_CURRENT_SOURCE_DIR}/../formatter_ex_lib
${CMAKE_CURRENT_SOURCE_DIR}/../solver_lib
)
target_link_libraries(solver formatter_ex_lib solver_lib)
^Z
zsh: suspended  cat > CMakeLists.txt
```                                                                                                                                                                     ```sh                                                                     
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/solver_application]
└─$ cmake -B build      
-- The C compiler identification is GNU 12.2.0
-- The CXX compiler identification is GNU 12.2.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working C compiler: /usr/bin/cc - skipped
-- Detecting C compile features
-- Detecting C compile features - done
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++ - skipped
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Configuring done
-- Generating done
-- Build files have been written to: /home/kali/HECCYLLIujTbmy/workspace/projects/lab02/lab3_x3/lab03/solver_application/build/
```

```sh
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/solver_application]
$ cmake --build build
[ 12%] Building CXX object solver_lib_dir/CMakeFiles/solver_lib.dir/solver.cpp.o
[ 25%] Linking CXX static library libsolver_lib.a
[ 25%] Built target solver_lib
[ 37%] Building CXX object formatter_ex_lib_dir/formatter_lib_dir/CMakeFiles/formatter_lib.dir/formatter.cpp.o
[ 50%] Linking CXX static library libformatter_lib.a
[ 50%] Built target formatter_lib
[ 62%] Building CXX object formatter_ex_lib_dir/CMakeFiles/formatter_ex_lib.dir/formatter_ex.cpp.o
[ 75%] Linking CXX static library libformatter_ex_lib.a
[ 75%] Built target formatter_ex_lib
[ 87%] Building CXX object CMakeFiles/solver.dir/equation.cpp.o
[100%] Linking CXX executable solver
[100%] Built target solver
```

```sh
┌──(kali㉿kali)-[~/…/lab02/lab3_x3/lab03/solver_application] 
$ build/solver
2 4 6
-------------------------
error: discriminant < 0
-------------------------
```
**Удачной стажировки!**

## Links
- [Основы сборки проектов на С/C++ при помощи CMake](https://eax.me/cmake/)
- [CMake Tutorial](http://neerc.ifmo.ru/wiki/index.php?title=CMake_Tutorial)
- [C++ Tutorial - make & CMake](https://www.bogotobogo.com/cplusplus/make.php)
- [Autotools](http://www.gnu.org/software/automake/manual/html_node/Autotools-Introduction.html)
- [CMake](https://cgold.readthedocs.io/en/latest/index.html)

```
Copyright (c) 2015-2021 The ISC Authors
```
>>>>>>> 318fa3d (second push)
