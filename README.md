# HW1_Lapshova
### Инструкция по запуску кода 
**Для работы потребуются:** 
1)	Установленный Python (при создании была использована версия 3.7, однако более ранние версии должны подойти (желательно не раньше 3.4) https://www.python.org/downloads/) 

2)	Установленный Jupyter-Notebook  (https://jupyter.org/, либо встроенный в Anaconda (рекомендуется)  https://www.anaconda.com/download/). При установке Anaconda все дальнейшие действия с командной строкой (за исключением действий, предусматривающих применение командной строки MySQL Command Line Client) удобнее производить через Anaconda Prompt.
3)	Установленный MySQL (https://dev.mysql.com/downloads/mysql/, при установке отметить галочкой установку MySQL Connector/ Python, либо выбрать дефолтные параметры установки) 
4)	Обновление команды pip до последней версии (через командную строку с помощью команды python -m pip install --upgrade pip)
5)	Обновление пакета pandas до последней версии (через командную строку с помощью команды pip install --upgrade pandas)
6)	*Опционально, если при попытке подключиться к базе данных выскочит ошибка, возможно, установленная версия MySQL Connector/Python не соответствует установленной версии Python (установка последней версии возможна через командную строку с помощью команды pip install MySQL-connector-python)*	

**Далее выполните:**
1)	Создайте Базу Данных (БД):

    - Откройте командную строку MySQL Command Line Client, введите ваш пользовательский пароль для входа
    - Создайте новую БД командой: create database your_database_name;
  
2)	Загрузите архивы (2 шт.) с анкетами кредитных заявок и с данными о контрактах по ссылке https://drive.google.com/open?id=1VwgP8Vc_RCNAoZK5tWt6aUqdET6cS5vS

3)	Создайте на своём компьютере папку, присвойте ей какое-либо название на английском языке (далее в инструкции *my_folder_name*) и создайте внутри этой папки ещё две папки с названиями: **contracts** и **applications**. В папку **contracts** распакуйте архив с данными по контрактам, а в папку  **applications** распакуйте архив с данными по анкетам кредитных заявок. Важно, чтобы в папках **contracts** и **applications** не было никаких подпапок, а сразу находились только файлы с расширением .xlsx). Кроме указанных данных в папках **contracts** и **applications** не должно ничего находиться.
4)	Скачайте тетрадку HW1_Lapshova.ipynb по ссылке https://github.com/itlapshova/HW1_Lapshova.git и поместите её в созданную вами папку *my_folder_name*. 
5)	Откройте тетрадку HW1_Lapshova.ipynb при помощи Jupyter Notebook (в командной строке зайдите в папку, в которой содержатся папки applications и contracts с помощью команды cd *your_folder_path*, а затем введите команду jupyter-notebook (данный способ описан для работы через Anaconda Prompt))
6)	В начале документа внимательно прочитайте, какие переменные вы должны дать на вход. Понадобится замена пути папки, в которой расположены папки **applications** и **contracts**, а также ввод своих параметров созданной вами базы данных: имя базы данных, пароль для входа в MySQL, имя пользователя. Замените все указанные в первой ячейке поля на свои значения.
7)	Запустите весь код с помощью нажатия Cell -> Run All. Важно при запуске кода держать закрытыми все файлы из папок **contracts** и **applications**.

### Описание тетрадки HW1_Lapshova.ipynb
Третадка состоит из трёх частей, каждая часть соответствует пункту Домашнего задания №1.

1.	В первом пункте загружаются данные по контрактам и кредитным заявкам в виде таблиц в Python, таблицы предобрабатываются (корректируются форматы дат для дальнейшей загрузки в базу данных в единый формат даты, заменяются на NULL значения дат, превышающие лимиты Python, удаляются пустые по всем ID колонки, удаляются неотобранные для дальнейшей работы поля); создаются таблицы applications и contracts в базе данных, заполняются данными из таблиц Python. Таблицы связаны по полю id_number.

2.	Во втором пункте проверяются возможные ошибки в данных по разным типам переменных: 
    - отрицательные значения положительных по смыслу числовых переменных с заложенным исправлением
    - аномальные значения числовых переменных
    - ошибки в названиях категорий текстовых переменных с заложенным исправлением
    - ошибки в соотношении значений связанных по смыслу переменных (family, children)
    - ошибки в отображении дат с заложенным исправлением <br/><br/>
    Также создаётся поле возраста заёмщика и указывается, найдены ли заёмщики младше 18 лет. <br/>
    Все выводы и результаты проверок находятся внутри тетрадки
    
3.	В третьем пункте текстовые поля закодированы числами, для расшифровки кодов созданы и переданы в базу данных словари. Вид конечных таблиц и пример словарей для некоторых полей находятся внутри тетрадки.

### Результат выполнения кода

1.	В созданной базе данных появляются две таблицы: contracts (c данными по контрактам) и applications (с данными по анкетам).

2.	В поле position заменены значения <undefined> на NULL
3.	Создана переменная возраст (age) вместо даты рождения (date_of_birth)
4.	Все текстовые поля перекодированы в числа
5.	Для расшифровки кодов в базу данных переданы словари applications_dict, contracts_dict.

