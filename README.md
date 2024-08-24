# Проект по взаимодействию с API HH.ru и работой с базой данных PostgreSQL

## Описание проекта

Этот проект предназначен для сбора данных о компаниях и вакансиях с сайта https://hh.ru через API, сохранения этих данных в базу данных PostgreSQL, и выполнения различных запросов для анализа данных. 

Проект структурирован следующим образом:

- `api_hh`: Модуль для работы с API hh.ru.
- `database_postgresql`: Модуль для взаимодействия с базой данных PostgreSQL (создание таблиц, вставка данных).
- `db_manager`: Модуль для выполнения различных запросов к базе данных.
- `config.py`: Модуль для чтения конфигурационных параметров из файла database.ini.

## Установка и настройка проекта

### 1. Клонирование репозитория

```bash
git clone https://github.com/yourusername/yourproject.git
cd yourproject

2. Установка зависимостей
Зависимости проекта указаны в файле pyproject.toml. Убедитесь, что у вас установлен poetry, после чего выполните команду для установки всех зависимостей:
poetry install

3. Настройка базы данных
Перед запуском проекта необходимо настроить параметры подключения к базе данных. Это можно сделать через файл database.ini.

Пример файла database.ini:
[postgresql]
host=localhost
database=your_database_name
user=your_username
password=your_password
port=5432

4. Структура проекта
src/api_hh/api_hh.py: В этом файле реализованы классы и методы для работы с API hh.ru. Например, HeadHunterRuAPI позволяет получать данные о компаниях и вакансиях.
src/database_postgresql/database_postgresql.py: Этот модуль отвечает за взаимодействие с PostgreSQL, включая создание таблиц и добавление данных.
src/db_manager/db_manager.py: Этот модуль предоставляет методы для выполнения запросов к базе данных (например, получение списка компаний с количеством вакансий, вакансий с зарплатой выше средней и т.д.).
config.py: Этот модуль предназначен для чтения конфигурационных данных из database.ini. Функция config возвращает словарь с параметрами подключения к базе данных.
5. Запуск проекта
После настройки всех параметров вы можете запустить основной скрипт:
poetry run python main.py

6. Выполнение запросов к базе данных
После заполнения базы данных, DBManager предоставляет несколько методов для анализа данных:

get_companies_and_vacancies_count(): Возвращает список компаний и количество вакансий для каждой из них.
get_all_vacancies(): Возвращает все вакансии с указанием компании, зарплаты и ссылки на вакансию.
get_avg_salary(): Возвращает среднюю зарплату по всем вакансиям.
get_vacancies_with_higher_salary(): Возвращает вакансии с зарплатой выше средней.
get_vacancies_with_keyword(keyword): Возвращает вакансии, содержащие указанное ключевое слово в названии.
