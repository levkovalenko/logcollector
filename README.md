# LogCollecotor

## platforms
Данный проект нацелен на платформы Linux. 
Его развертка проводилась на:
- debian 9 - stretch
- debian 9 - testing
- ...

## dependencies
**python3-venv**

Виртуальное окружение python3.
Позволяет изолировать окружение проекта и использовать библиотеки описанные в requirements.txt 

Для установки: `apt-get install python3-venv`


**postgresql**

Реляционная база данных. Запуск производился на версиях: 10.5, 9.6

Для установки: [Инструкция](https://linuxize.com/post/how-to-install-postgresql-on-debian-9/)


**requirements.txt**

Для установки: 
    
    `pip install -r requirements.txt`

## pre run
В этом разделе описываются действия необходимые для успешного запуска проекта.

**Установка переменных среды:**

    $ export USER_NAME=postgres
    $ export BASE_NAME=logcollector
    $ export BASE_HOST=127.0.0.1
    $ export BASE_PORT=5432
    $ export BASE_URL=http://127.0.0.1:8000
    $ export BASE_PASSWORD=[secure]

**Запуск внешней инфраструктуры:**

    sudo systemctl postgresql start
**Генерация настроек:**

_Стоит отметить, что настройки генерируются из переменных среды._

    python gen_settings.py
    
Для генерации случайных значений можно использовать команду: `python gen_settings.py -ag SECRET_KEY -l 34 -i True`


## run
После **pre run** можно инициализировать запуск проекта
- `python manage.py runserver ` для запуска сервера, основной точки входа в систему.
