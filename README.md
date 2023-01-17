<h2>Дипломный проект курса "Тестировщик ПО"</h2>

<h2>О проекте</h2>
<p>Приложение представляет из себя веб-сервис.</p>
<p><a href="https://github.com/netology-code/qa-diploma/raw/master/pic/service.png"><img src="https://github.com/netology-code/qa-diploma/raw/master/pic/service.png" alt="image"></a></p>
<p>Приложение предлагает купить тур по определённой цене с помощью двух способов:</p>
<ul>
    <li>Обычная оплата по дебетовой карте</li>
    <li>Уникальная технология: выдача кредита по данным банковской карты</li>
</ul>
<p>Приложение предлагает купить тур по определённой цене с помощью двух способов:</p>
<ul>
    <li>Обычная оплата по дебетовой карте</li>
    <li>Уникальная технология: выдача кредита по данным банковской карты</li>
</ul>
<p>Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:</p>
<ul>
    <li>сервису платежей (далее - Payment Gate)</li>
    <li>кредитному сервису (далее - Credit Gate)</li>
</ul>
<p>Сервис может взаимодействоватьс СУБД MySql и PostgreSql</p>
<p>База данных хранит информацию о заказах, платежах, статусах карт, способах оплаты.</p>
<h2>Цели проекта</h2>
<p>В рамках проекта необходимо автоматизировать тестирование комплексного сервиса покупки тура, взаимодействующего с СУБД и API Банка.</p>
<h2>Подготовка к запуску тестов</h2>
<h3>Предусловия</h3>
<p>Если необходимое ПО уже установлено, то в предусловиях достаточно только открыть проект в IDEA.</p>
<ul>
    <li>Склонировать себе данный репозиторий командой git clone</li>
    <li>Установить и запустить Docker Desktop. Скачать программу можно с официального сайта по <a href="https://docs.docker.com/desktop/install/windows-install/">ссылке</a>. Порядок установки можно прочитать <a href="https://github.com/netology-code/aqa-homeworks/blob/master/docker/installation.md">здесь</a></li>
    <li>Установить IntelliJ IDEA (Communicate или Ultimate) версию. Скачать можно по <a href="https://www.jetbrains.com/ru-ru/idea/download/#section=windows">ссылке</a> с официального сайта</li>
    <li>Открыть склонированный проект в IDEA</li>
</ul>
<h2>Запуск контейнеров и SUT</h2>
<ol>
    <li>Запустить контейнеры докера, поднимающие БД MySQL, PostgreSql и сервис платежей payment-gate на node.js. Для этого в терминале IDEA ввести команду <code>docker-compose up -d</code></li>
    <li>Запустить SUT в зависимости нужного подключения к БД. Для этого:</li>
</ol>
<ul>
    <li>Для подключения к БД MySql в терминале IDEA ввести команду: <code>java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar ./artifacts/aqa-shop.jar</code></li>
    <li>Для подключения к БД PostgresSql в терминале IDEA ввести команду: <code>java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app" -jar ./artifacts/aqa-shop.jar</code></li>
    
</ul>
<ol dir="auto" start="3">
    <li>Проверить успешность запуска SUT по адресу <a href="http://localhost:8080/">http://localhost:8080/</a></li>
</ol>

<h2 dir="auto">Запуск тестов и генерация отчета Allure</h2>
<ol dir="auto">
    <li>В зависимости от подключенной БД в терминале IDEA в новой вкладке выполнить команду:</li>
</ol>
<ul dir="auto">
    <li>При подключенной БД MySql:&nbsp;<code>./gradlew clean test -D db.url=jdbc:mysql://localhost:3306/app</code></li>
    <li>При подключенной БД PostgreSql:&nbsp;<code>./gradlew clean test -D db.url=jdbc:postgresql://localhost:5432/app</code></li>
</ul>
<ol dir="auto" start="2">
    <li>Сгенерировать отчет Allure, выполнив команду в терминале IDEA:&nbsp;<code>./gradlew allureServe</code></li>
</ol>
<ul dir="auto">
    <li>Если отчет не открывается автоматически в браузере, то выполнить команду:&nbsp;<code>./gradlew allureReport</code> и открыть отчет вручную (файл index.html) по адресу:&nbsp;<code>.\build\reports\allure-report\allureReport</code></li>
</ul>
<ol dir="auto" start="3">
    <li>При необходимости изменить подключение к другой БД, необходимо остановить подключения в терминалах черех Ctrl + C в окне терминала</li>
</ol>
