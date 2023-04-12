# Выполнение первой части задания

1. **Используйте команды операционной системы Linux 
   и создайте две новых директории – «Игрушки для школьников» и «Игрушки для дошколят»**
```powershell

Welcome to Ubuntu 22.04.2 LTS (GNU/Linux 5.19.0-38-generic x86_64)

* Documentation:  https://help.ubuntu.com
* Management:     https://landscape.canonical.com
* Support:        https://ubuntu.com/advantage

* Introducing Expanded Security Maintenance for Applications.
  Receive updates to over 25,000 software packages with your
  Ubuntu Pro subscription. Free for personal use.

  https://ubuntu.com/pro

Расширенное поддержание безопасности (ESM) для Applications выключено.

0 обновлений может быть применено немедленно.

Включите ESM Apps для получения дополнительных будущих обновлений безопасности.
Смотрите https://ubuntu.com/esm или выполните: sudo pro status

Last login: Tue Apr 11 18:54:39 2023 from 10.0.3.2

pavel@gblinux:~/final_work$ mkdir Игрушки_для_дошколят
pavel@gblinux:~/final_work$ mkdir Игрушки_для_школьников
```
2. **Создайте в директории «Игрушки для школьников» текстовые файлы - 
    «Роботы», «Конструктор», «Настольные игры»**

```powershell

pavel@gblinux:~/final_work$ cd Игрушки_для_школьников
pavel@gblinux:~/final_work/Игрушки_для_школьников$ > Роботы
pavel@gblinux:~/final_work/Игрушки_для_школьников$ > Конструктор
pavel@gblinux:~/final_work/Игрушки_для_школьников$ > Настольные_Игры
```
3. **Создайте в директории «Игрушки для дошколят» текстовые файлы 
    «Мягкие игрушки», «Куклы», «Машинки»**

```powershell 
pavel@gblinux:~/final_work$ cd Игрушки_для_дошколят
pavel@gblinux:~/final_work/Игрушки_для_дошколят$ > Мягкие_игрушки
pavel@gblinux:~/final_work/Игрушки_для_дошколят$ > Куклы
pavel@gblinux:~/final_work/Игрушки_для_дошколят$ > Машинки
```
4. **Объединить 2 директории в одну «Имя Игрушки»**

```powershell
pavel@gblinux:~/final_work$ mv Игрушки_для_дошколят/ Игрушки_для_школьников/ Имя_игрушки/
pavel@gblinux:~/final_work$ cd Имя_игрушки
pavel@gblinux:~/final_work/Имя_игрушки$ tree
.
├── Игрушки_для_дошколят
│   ├── Куклы
│   ├── Машинки
│   └── Мягкие_игрушки
└── Игрушки_для_школьников
    ├── Конструктор
    ├── Настольные_Игры
    └── Роботы
```
5. **Переименовать директорию «Имя Игрушки» в «Игрушки»**
```powershell

pavel@gblinux:~/final_work$ mv Имя_игрушки/ Игрушки
pavel@gblinux:~/final_work$ cd Игрушки
pavel@gblinux:~/final_work/Игрушки$ ll
```

6. **Просмотреть содержимое каталога «Игрушки».**
```powershell
pavel@gblinux:~/final_work/Игрушки$ tree -g
.
├── [pavel   ]  Игрушки_для_дошколят
│   ├── [pavel   ]  Куклы
│   ├── [pavel   ]  Машинки
│   └── [pavel   ]  Мягкие_игрушки
└── [pavel   ]  Игрушки_для_школьников
    ├── [pavel   ]  Конструктор
    ├── [pavel   ]  Настольные_Игры
    └── [pavel   ]  Роботы

2 directories, 6 files
```
7. **Установить и удалить snap-пакет. (Любой, какой хотите)**
```powershell
pavel@gblinux:~/final_work$ sudo snap install tree
[sudo] пароль для pavel:
tree 1.8.0+pkg-3fd6 от 林博仁(Buo-ren, Lin) (brlin) установлен
pavel@gblinux:~/final_work/Игрушки$  sudo snap remove tree
tree удалён
```
8.**Добавить произвольную задачу для выполнения каждые 3 минуты  
(Например, запись в текстовый файл чего-то или копирование из каталога А в каталог Б).**
```powershell
pavel@gblinux:~/final_work$  sudo vi /usr/local/bin/script.sh
    #!/bin/bash
    echo $(date) >> /var/log/testcron.log
    :w!
    :q
pavel@gblinux:~/final_work$  sudo chmod ugo+x /usr/local/bin/script.sh
pavel@gblinux:~/final_work$  sudo crontab -e
    0/3 * * * * /usr/local/bin/script.sh
crontab: installing new crontab