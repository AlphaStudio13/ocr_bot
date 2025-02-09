# Скрипт [OCR] анализ данных

[//]: # Этот скрипт представляет собой автоматизированную систему для обработки файлов в указанной папке, 
извлечения данных из изображений с помощью оптического распознавания символов (OCR), 
анализа извлеченных данных на предмет наличия телефонных номеров, адресов электронной почты и имен, 
фильтрации файлов по дате и отправки результатов обработки в Telegram. # :[//]

## Содержание

┌── **Файловая структура**: Полное отображение файловой структуры скрипта, а так же описание файловой структуры.
├──. **Установка зависимостей**: Инструкция по установке всех необходимых зависимостей для работы скрипта.
├──. **Настройка и запуск на Linux**: Инструкции для настройки и запуска скрипта на `Linux` с использованием `systemd`.
├── **Настройка и запуск на Windows**: Инструкции для настройки и запуска скрипта на `Windows` с использованием `Task Scheduler`.
├── **Установка и настройка Python**: Информация о необходимости установки `Python` на `Windows`.
├── **Настройка конфигурации**: Примеры настройки конфигурационного файла `config.py`.
├── **Запуск скрипта**: Как запустить скрипт и описание его работы.
├── **Особенности**: Краткое описание особенностей скрипта, таких как экстренная остановка и уведомления.
├── **Работа на различных ОС**: Инструкции для запуска скрипта на `Linux` и `Windows`.
└── **Служба или автозапуск**: Рекомендации по настройке службы или задачи для автоматического запуска скрипта.


## Файловая структура

📁 OCR_BOT [Скрипт разработан - dev_oop_studio] (https://t.me/dev_oop_studio)
  ├── 📄 ocr_bot.py			# Основной скрипт для запуска процесса сканирования и обработки изображений
  ├── 📄 config.py			# Конфигурационный файл с настройками скрипта
  ├── 📄 requirements.txt	# Файл с зависимостями Python для установки необходимых пакетов
  ├── 📄 script_runner.bat	# Сценарий для автозапуска скрипта на Windows
  ├── 📄 readme.md			# Файл с описанием проекта, инструкциями по установке и использованию
  ├── 📁 logs				# Папка для хранения логов работы скрипта
  │   └── 📄 log.txt		# Файл с логами работы скрипта
  └── 📁 scripts			# Папка с дополнительными скриптами и модулями
      └── 📄 ocr_script.py 	# Скрипт для выполнения оптического распознавания символов (OCR)


### Описание файловой структуры

- **`ocr_bot.py`**: Основной скрипт вашего проекта, который выполняет сканирование папки и вызывает другие функции.
  
- **`config.py`**: Конфигурационный файл, где хранятся переменные и настройки для вашего скрипта.

- **`requirements.txt`**: Файл, содержащий список всех зависимостей Python, необходимых для работы проекта.

- **`script_runner.bat`**: Файл для автозапуска и перезапуска скрипта на Windows.

- **`readme.md`**: Файл Markdown с описанием проекта, инструкциями по установке и использованию.

- **`logs/log.txt`**: Папка и файл для хранения логов работы скрипта.

- **`scripts/ocr_script.py`**: Файл, который содержит основной функционал оптического распознавания символов (OCR).

- [//]: # Это основная структура, которая может быть адаптирована в зависимости от конкретных потребностей проекта.


## Установка

### Установите необходимые сурсы и зависимости

1. **Откройте **: ***`Windows`*** *CMD.exe or PowerShell* | ***`Linux `*** *SHELL, Tunel SSH, CMD or PuTTy * 

	- *** Для работы скрипта требуется ***: *Python 3.6* *** и  выше. ***
		- ** Установите ** *Python* **следуя инструкциям для вашей операционной системы ** :
			- ***`Linux `***:
				```bash
					sudo apt update
					sudo apt install python3.
				```
			- ***` Windows `***:
				- Скачайте установщик *Python* с [официального сайта python.org](https://www.python.org/downloads/) и выполните установку.
			-
		-
	-

2. **Установка зависимостей **

	- **Перед запуском скрипта необходимо установить зависимости, указанные в файле ** *requirements.txt*
		- *** Запуск от имени Администратора Windows*** *CMD.exe or PowerShell*  *** Выполните следующую команду ***:
			```bash sh
				pip install -r requirements.txt
			```
		- *** Для *** *Linux* *** Запуск из под*** *ROOT'а SHELL, Tunel_SSH, PowerShell or PuTTy * *** Выполните следующую команду ***:
			```bash sh
				sudo pip install -r requirements.txt
			```
		-
	-


3. **Настройка конфигурации**
	
	- **Скопируйте файл** *config.example.py* **в** *config.py* **и настройте переменные в соответствии с вашими данными.**
		- ***Пример конфигурации***:
			```Python
				TELEGRAM_TOKEN = 'YOUR_TELEGRAM_BOT_TOKEN'
				CHAT_ID = 'YOUR_CHAT_ID'
				SOURCE_FOLDER = '/path/to/source/folder'
				CUSTOMERS_FOLDER = '/path/to/Customers_and_Clients_Files'
				DATE_FILTER_START = datetime(2023, 1, 1)
				DATE_FILTER_END = datetime(2024, 12, 31)
				MAX_EXECUTION_TIME_MINUTES = 30
			```
		- 
	- 

## Использование

### Для запуска скрипта на вашей ОС:
	
	- **`Выполните команду:`**
		- *** Linux ***:
			```bash sh
				sudo python ocr_bot.py
			```
		- *** Windows ***:
			```bash sh
				python ocr_bot.py
			```
		-
	-

### Настройка Для Linux (используя systemd)

    - ***Создайте файл службы*** `/etc/systemd/system/main_script.service` ***со следующим содержимым***:
        ```code
			[Unit]
			Description=Main Script Service
			After=network.target

			[Service]
			User=root
			ExecStart=/usr/bin/python3 /path/to/ocr_bot.py
			Restart=always

			[Install]
			WantedBy=multi-user.target
        ```
    - *** Включите службу и запустите её ***:
		```bash sh
			sudo systemctl daemon-reload
		```
		```bash sh
			sudo systemctl enable main_script.service
		```
		```bash sh
			sudo systemctl start main_script.service
		```
	-

### Настройка Для Windows (используя Task Scheduler)

1. **`Откройте Планировщик задач (Task Scheduler)`**:
	- Запустите Планировщик задач из меню Пуск или через поиск в Windows.

2. **`Создайте новую задачу`**:
	- В меню Планировщика задач выберите "Создать задачу" из действий в правой части окна.

3. **`Настройте выполнение задачи`**:
	
	- ***Общие***:
    	- Укажите имя задачи и описание.
    	- Установите опции для запуска задачи: "Запускать с наибольшими правами" и "Запускать для текущего пользователя".
   
	- ***Триггеры***:
		- Нажмите "Новый", чтобы создать новый триггер запуска задачи.
		- Выберите расписание запуска (например, "Ежедневно" или "По расписанию").
   
	- ***Действия***:
		- Нажмите "Новое", чтобы добавить действие.
		- Укажите путь к `script_runner.bat` в поле "Программа или сценарий".
   
	- ***Условия***:
		- Установите условия выполнения задачи, такие как "Запускать задачу только при наличии подключения к сети".
	
	- ***`Сохраните задачу`**:
		- Нажмите "ОК", чтобы сохранить задачу в Планировщике задач.
		- Задача будет выполнена согласно настроенному расписанию.
	-

## Особенности

	- **`Экстренная остановка`**: Скрипт поддерживает экстренную остановку по команде ***Ctrl+C*** или по истечении времени выполнения, заданного в конфигурации.

	- **`Уведомления Telegram`**: При экстренной остановке или других событиях скрипт отправляет уведомления в Telegram.

	- **`Автоматический перезапуск`**: Для обеспечения непрерывной работы предусмотрен автоматический перезапуск скрипта в случае его непредвиденной остановки.

	- **`Работа на различных ОС`**:
		- ***Linux***: Скрипт может быть запущен на любом современном дистрибутиве Linux с установленным Python 3.
		- ***Windows Server и Windows 10+ ***: На Windows убедитесь, что у вас установлен Python 3 и выполните установку зависимостей через pip. Запускайте скрипт через командную строку.
	
	- **`Служба или автозапуск`**: Для постоянного выполнения скрипта на сервере рекомендуется настроить службу или задачу планировщика задач, чтобы скрипт запускался автоматически при загрузке системы или по расписанию.



