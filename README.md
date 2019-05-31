Скребков Александр ИУ8-22
# Homework
## Задание 1
Вам поручили перейти на систему автоматизированной сборки CMake. Исходные файлы находятся в директории formatter_lib. В этой директории находятся файлы для статической библиотеки formatter. Создайте CMakeList.txt в директории formatter_lib, с помощью которого можно будет собирать статическую библиотеку formatter.

```ShellSession
$ cd formatter
$ cat >> CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.4)
project(formatter)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_library(formatter_lib1 STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter.cpp)
add_executable(formatter ${CMAKE_CURRENT_SOURCE_DIR}/formatter.cpp)
target_link_libraries(formatter formatter_lib1)
EOF
```
Проверка работы

```ShellSession
$ cmake .
$ make
```
Библиотека создается. Удаляем созданное при проверке. Commit, push.

```ShellSession
$ cd ..
$ git add .
$ git commit -m "Создание библиотеки formatter_lib1"
$ git push origin master
```
