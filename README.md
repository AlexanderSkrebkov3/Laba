
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
## Проверка работы

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
## Задание 3
```ShellSession

cd formatter   #переход в директорию в которой расположена библиотека
$ cat >> CMakeLists.txt <<EOF #редактирование файла CMakeLists.txt
cmake_minimum_required(VERSION 3.4)   #указание необходимой версии cmake
project(formatter_ex)    #название проекта
set(CMAKE_CXX_STANDARD 11)  #установка необходимых стандартов языка С++
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_library(formatter_ex STATIC ${CMAKE_CURRENT_SOURCE_DIR}/helloworld.cpp)  #создание библиотеки formatter_ex
add_executable(helloworld ${CMAKE_CURRENT_SOURCE_DIR}/helloworld.cpp)    #создание исполняемого файла helloworld
target_link_libraries(helloworld formatter_lib1)  #компоновка программы с библиотекой
EOF  #завершение работы с файлом

cd solver
$ cat >> CMakeLists.txt <<EOF
cmake_minimum_required(VERSION 3.4)
project(solver)
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
add_library(formatter_lib1 STATIC ${CMAKE_CURRENT_SOURCE_DIR}/formatter_lib1.cpp)
add_library(solver_lib STATIC ${CMAKE_CURRENT_SOURCE_DIR}/solver_lib.cpp)

add_executable(solver  solver.cpp )#Команда компилирует исполняемый файл с заданным именем из списка исходников. 

target_link_libraries(solver solver_lib formatter_lib1)#Команда компонует исполняемый файл solver с другими предоставляемыми библиотеками.


EOF
```

