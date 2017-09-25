## Laboratory work III

Данная лабораторная работа посвещена изучению систем контроля версий на примере **Git**.

```bash
$ open https://git-scm.com
```

## Tasks

- [X] 1. Создать публичный репозиторий с названием **lab03** и с лиценцией **MIT**
- [X] 2. Ознакомиться со ссылками учебного материала
- [X] 3. Выполнить инструкцию учебного материала
- [X] 4. Составить отчет и отправить ссылку личным сообщением в **Slack**

## Tutorial

Установим значения `GITHUB_USERNAME` и `GITHUB_EMAIL`, потом настраиваем текстовый редактор.

```ShellSession
$ export GITHUB_USERNAME=nex-7 
$ export GITHUB_EMAIL=alex.malinovski205430@gmail.ru 
$ alias edit=vim 
```

Создаем папку lab03, конфигурацию гита, README.md и загружаем на гит.

```ShellSession
$ mkdir lab03 && cd lab03 
$ git init 
$ git config --global user.name ${GITHUB_USERNAME}
$ git config --global user.email ${GITHUB_EMAIL} 
$ git config -e --global 
$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab03 
$ git pull origin master 
$ touch README.md 
$ git status 
$ git add README.md 
$ git commit -m"added README.md" 
$ git push origin master 
```

Добавить на сервисе **GitHub** в репозитории **lab03** файл **.gitignore**
со следующем содержимом:

```ShellSession
*build*/
*install*/
*.swp
```

Проверяем, все ли правильно сделали с .gitignore
```ShellSession
$ git pull origin master
$ git log 
```

Создаем 3 папки, 4 файла.

```ShellSession
$ mkdir sources 
$ mkdir include 
$ mkdir examples 
$ cat > sources/print.cpp <<EOF
#include <print.hpp>

void print(const std::string& text, std::ostream& out) {
  out << text;
}

void print(const std::string& text, std::ofstream& out) {
  out << text;
}
EOF 
```

```ShellSession
$ cat > include/print.hpp <<EOF
#include <string>
#include <fstream>
#include <iostream>

void print(const std::string& text, std::ostream& out = std::cout);
void print(const std::string& text, std::ofstream& out);
EOF # Заполнение файла print.hpp
```

```ShellSession
$ cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv) {
  print("hello");
}
EOF 
```

```ShellSession
$ cat > examples/example2.cpp <<EOF
#include <fstream>
#include <print.hpp>

int main(int argc, char** argv) {
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF 
```

Редактируем файл README.md.

```ShellSession
$ edit README.md 
```

Копируем все содержимое в папке lab03, загружаем на гит.

```ShellSession
$ git status 
$ git add . 
$ git commit -m"added sources" 
$ git push origin master 
```

## Report

```ShellSession
$ cd ~/workspace/labs/
$ export LAB_NUMBER=03 
$ git clone https://github.com/tp-labs/lab${LAB_NUMBER} tasks/lab${LAB_NUMBER}
$ mkdir reports/lab${LAB_NUMBER}
$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
$ cd reports/lab${LAB_NUMBER} 
$ edit REPORT.md 
$ gistup -m "lab${LAB_NUMBER}"
```

## Links

- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)

```
Copyright (c) 2017 Братья Вершинины
```