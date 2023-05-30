# Упражнение 0: python.exe и виртуальные окружения

## A. Мучаем python.exe

Команда python -c "import pandas" используется для запуска Python-кода из командной строки. Флаг -c означает, что следующий за ним аргумент будет содержать код на языке Python, который нужно выполнить. В данном случае, мы импортируем библиотеку pandas. Когда команда выполняется, интерпретатор Python запускается, код импортирует pandas и завершается. Если библиотека не установлена, будет вызвано исключение ModuleNotFoundError


## B. Ищем пути к файлам

1.
   - `which` на Linux
   - `where` на Windows

2. Какой путь на вашей машине к `python.exe` (`which python` или `where python`)? 
   -  C:\Users\mrale>where python
   -  C:\Users\mrale\anaconda3\python.exe
   -  C:\Users\mrale\AppData\Local\Microsoft\WindowsApps\python.exe
   
   Какой путь к `pip` (`which pip` или `where pip`)? Относятся ли эти пути к одной папке?
   - C:\Users\mrale>where pip
   - C:\Users\mrale\pip
   - C:\Users\mrale\anaconda3\Scripts\pip.exe


### Что такое pip и pip3?

`pip` и `pip3` - это утилиты для управления пакетами в Python. `pip` обычно используется для Python 2, а `pip3` - для Python 3.

`pip` позволяет устанавливать, обновлять и удалять пакеты из репозитория PyPI (Python Package Index). PyPI является крупнейшим репозиторием пакетов Python и содержит более 300 000 пакетов.

`pip` и `pip3` также поддерживают установку пакетов из локальных директорий или файлов, а также управление зависимостями между пакетами.

Команда `pip` вызывается без указания версии Python, что может привести к проблемам совместимости при использовании Python 2 и Python 3. Поэтому, для управления пакетами в Python 3 рекомендуется использовать `pip3`.


3. Покажите, в какой папке находится исходный код пакета `pandas` (если он установлен).
   - C:\Users\mrale>pip3 show pandas | findstr "Location"
   
     Location: c:\users\mrale\anaconda3\lib\site-packages

   - C:\Users\mrale>pip show pandas | findstr "Location"
   
     Location: c:\users\mrale\anaconda3\lib\site-packages
    

4. Укажите версию установаленного пакета `pandas`.
  - C:\Users\mrale>pip show pandas | findstr "Version"

    Version: 1.4.4


## С. Первое виртуальное окружение

1. Создаем новое виртуальное окружение и активируем его
- python3 -m venv my_env
- activate my_env

2. Попытаемся выйти из виртуального окружения
- deactivate

3. Войдем в виртуальное окружение снова
- activate my_env

4. Проверяем, на каком шаге возникает проблема (если возникает)
- python -c "import pandas"
- pip install pandas

5. Показываем установленные пакеты и сохраняем их в requirements.txt
- pip freeze > requirements.txt
- pip list

## D. Сравниваем глобальное окружение и `my_env`

1. Чем отличается пути к `python.exe` в глобальном и в виртуальном окружении `my_env`?

1. C:\Users\mrale>where python
- C:\Users\mrale\anaconda3\python.exe
- C:\Users\mrale\AppData\Local\Microsoft\WindowsApps\python.exe

2. (my_env) C:\Users\mrale>where python
- C:\Users\mrale\anaconda3\python.exe
- C:\Users\mrale\AppData\Local\Microsoft\WindowsApps\python.exe

2. Найдите, где находится код `pandas` в глобальном и в виртуальном окружении.
   Покажите, что это разные директории.
   - C:\Users\mrale>pip3 show pandas | findstr "Location"
  
     Location: c:\users\mrale\anaconda3\lib\site-packages

   - (my_env) C:\Users\mrale>pip3 show pandas | findstr "Location"
   
     Location: c:\users\mrale\anaconda3\lib\site-packages


3. В глобальном и локальном окружении стоит `pandas` одной или разных версий?

-C:\Users\mrale>pip3 show pandas | findstr "Version"

Version: 1.4.4


- (my_env) C:\Users\mrale>pip3 show pandas | findstr "Version"

Version: 1.4.4

4. Если версии одинаковые, измените версию `pandas` в локальном окружении на другую, например,
   более низкую. Приведите пример, зачем это может быть нужно в реальной работе?

## Q. Дополнительные вопросы

1. С какими библиотеками будет установлен Python с Python.org?
- https://docs.python.org/3/library/
- Например collections, datetime, json
2. Что такое сборка Anaconda, зачем она нужна?
- Anaconda - это пакетный менеджер и среда программирования для работы с Python, предназначенная для анализа данных и научных вычислений. Она объединяет в себе язык программирования Python, необходимые библиотеки и инструменты, облегчая установку и использование для работы с данными.
3. Какие еще сборки Python бывают?

4. Что такое и чем отличаются `pip` и `conda`?
- `pip` - стандартный способ библиотек на python из Python Package Index (PyPI) - центрального репозитория пакетов Python. Conda - нечто похожее, только позволяет устанавливать пакеты из различных источников, включая Anaconda Repository, PyPI и Conda Forge, также в Conda есть функционал для создания изолированных средств. 
5. Папка, в которой установлен python
- ?
6. Всегда ли `which python` будет выдавать один и тот же результат? От чего это зависит. 
- Нет, если активировано виртуальное окружение, результат может меняться.
## N. Заметки - чему мы научились и каким выводам пришли

- ЕП: ...
- YG: Я встретился с небольшими проблемами с командной строкой, мне не хватало списка команд, которые надо знать (https://lab.karpov.courses/learning/102/module/1276/lesson/12126/35055/171606/ - хороший пример) + я не понял в чем суть пятого доп. вопроса. 
- другие: ...
