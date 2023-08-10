# Дипломный проект по профессии «Тестировщик»

## Цели проекта

В рамках проекта необходимо автоматизировать тестирование комплексного сервиса покупки тура, взаимодействующего с СУБД и API Банка.

## О проекте
Приложение - веб-сервис.

Приложение предлагает купить тур по определённой цене с помощью двух способов:

* Обычная оплата по дебетовой карте
* Уникальная технология: выдача кредита по данным банковской карты

Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:

* сервису платежей (далее - Payment Gate)
* кредитному сервису (далее - Credit Gate)

Сервис может взаимодействоватьс СУБД  MySql и PostgreSql

## Документация

## Предварительные требования
Для запуска приложения необходимо следующее ПО:
* IntelliJ Idea.
* Docker Desktop - для запуска, установки и использования БД MySQL и PostgeSQL.
* Git.

## Запуск приложения

1. Клонировать репозиторий.
2. Запустить базы данных MySQL и PostgreSQL, а также эмулятор банковского сервиса. 
* в файле `docker-compose.yml` нажать на зеленый треугольник. </br>
или
* в терминале IntelliJ IDEA ввести команду:`docker compose up`, в новой вкладке терминала ввести следующие команды:
* `java -Dspring.datasource.url=jdbc:mysql://localhost:3306/app -jar ./artifacts/aqa-shop.jar` - для MySQL
* `java -Dspring.datasource.url=jdbc:postgresql://localhost:5432/app -jar ./artifacts/aqa-shop.jar` - для PostgreSQL
3. Проверить доступность веб-сервиса  по адресу: <http://localhost:8080/>

## Запуск автотестов

1. Для запуска автотестов с "MySQL",  необходимо открыть новую вкладку терминала и ввести:
* `./gradlew test -Dselenide.headless=true Ddb.url=jdbc:mysql://localhost:3306/app --info`
2. Для запуска автотестов с "PostgreSQL",  необходимо открыть новую вкладку терминала и ввести:
* `./gradlew test -Dselenide.headless=true -Ddb.url=jdbc:postgresql://localhost:5432/app --info`

## Запуск отчета тестирования

1. Для запуска и просмотра отчета по результатам тестирования, с помощью "Allure", выполнить по очереди команды:
* `gradlew allureReport`
* `gradlew allureServe`

## Завершения работы Sut

1. Для завершения работы SUT ввести команду в терминале:
* `Ctrl+C`

## Остановка контейнера
1. Для остановки работы контейнеров "Docker-Compose" ввести в терминал команду:

* `docker-compose down`
