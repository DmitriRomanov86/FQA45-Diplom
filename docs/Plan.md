<h2>План работ</h2>

<h3>Этапы тестирования сервиса</h3>

<p>Целевой сервис: aqa-shop.jar</p>

<ol>
    <li>Ознакомление с сервисом и настройка рабочего пространства</li>
    <li>Определение плана работ</li>
    <li>Определение и реализация позитивных сценариев</li>
    <li>Определение и реализация негативных сценариев</li>
    <li>Оформление баг-репортов</li>
    <li>Подготовка отчетных документов и сдача проекта на проверку</li>
</ol>

<h2>Тестовые сценарии</h2>

<h3>Тестирование формы оплаты тура по карте</h3>

<h3>Предусловия</h3>
<ul>
    <li>На главной странице нажать кнопку "Купить"</li>
    <li>Валидный номер активированной карты 4444 4444 4444 4441</li>
    <li>Валидный номер заблокированной карты 4444 4444 4444 4442</li>
</ul>

<h3>Позитивные сценарии</h3>

<h3>1. Успешная оплата тура по активной карте</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Всплывающее окно с сообщением "Успешно! Операция одобрена банком." В БД есть запись APPROVED</p>

<h3>2. Отклонение оплаты тура по заблокированной карте</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение заблокированной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Всплывающее окно с сообщением "Ошибка! Банк отказал в проведении операции." В БД есть запись DECLINED</p>

<h3>Негативные сценарии</h3>

<h3>Тестирование поля "Номер карты"</h3>

<h3>3. Отклонение оплаты тура по несуществующей карте</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение несуществующей карты 4444 4444 4444 4443</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Всплывающее окно с сообщением "Ошибка! Банк отказал в проведении операции." В БД нет новой записи</p>

<h3>4. Отклонение оплаты тура по некорректному номеру карты</h3>
<ol>
    <li>В поле "Номер карты" ввести невалидное значение карты 4444 4444 4444 44</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Номер карты" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>5. Заполнение заявки на оплату картой с пустым полем "Номер карты"</h3>
<ol>
    <li>Поле "Номер карты" оставить пустым</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Номер карты" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>6. Отклонение оплаты тура по несуществующей карте (нули в номере)</h3>
<ol>
    <li>В поле "Номер карты" ввести значение 0000 0000 0000 0000</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Всплывающее окно с сообщением "Ошибка! Банк отказал в проведении операции." В БД нет новой записи</p>
<h3>Тестирование поля "Месяц"</h3>

<h3>7. Заполнение заявки с невалидной датой(истекший срок действия карты)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести прошлый месяц</li>
    <li>В поле "Год" ввести значение текущего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Месяц" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>8. Заполнение заявки с невалидной датой(месяц)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести значение 13</li>
    <li>В поле "Год" ввести значение текущего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Месяц" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>9. Заполнение заявки с невалидной датой(месяц)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести значение 00</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Месяц" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>10. Заполнение заявки с пустым полем "месяц"</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>Поле "Месяц" оставить пустым</li>
    <li>В поле "Год" ввести значение текущего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Месяц" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>
<h3>Тестирование поля "Год"</h3>

<h3>11. Заполнение заявки с невалидной датой(истекший срок действия карты)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение предыдущего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Год" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>12. Заполнение заявки с пустым полем "Год"</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>Поле "Год" оставить пустым</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Год" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>13. Заполнение заявки с невалидной датой(нули в дате)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В роле "Год" ввести значение 00</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Год" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>Тестирование поля "Владелец"</h3>

<h3>14. Заполнение заявки с невалидным именем(русская раскладка имя и фамилия)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести невалидное значение русскими буквами (имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Владелец" подсвечивает сообщение: "недопустимые символы" В БД нет новой записи</p>

<h3>15. Заполнение заявки с невалидным именем(только имя)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести невалидное значение на латинице (только имя)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Владелец" подсвечивает сообщение: "введите полное имя и фамилию" В БД нет новой записи</p>

<h3>16. Заполнение заявки с пустым полем "Владелец"</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>Поле "Владелец" оставить пустым</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Владелец" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>Тестирование поля "CVC/CVV"</h3>

<h3>17. Заполнение заявки с невалидным CVC/CVV</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение на латинице (имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести невалидное значение из двух цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "CVC/CVV" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>18. Заполнение заявки с пустым полем "CVC/CVV"</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение на латинице (имя и фамилию)</li>
    <li>Поле "CVC/CVV" оставить пустым</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "CVC/CVV" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>19. Заполнение заявки с невалидным CVC/CVV (нули в поле)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение на латинице (имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести невалидное значение 000</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "CVC/CVV" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>Тестирование формы оплаты тура в кредит</h3>

<h3>Предусловия</h3>
<ul>
    <li>На главной странице нажать кнопку "Купить в кредит"</li>
    <li>Валидный номер активированной карты 4444 4444 4444 4441</li>
    <li>Валидный номер заблокированной карты 4444 4444 4444 4442</li>
</ul>

<h3>Позитивные сценарии</h3>

<h3>20. Успешная оплата тура по активной карте</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Всплывающее окно с сообщением "Успешно! Операция одобрена банком." В БД есть запись APPROVED</p>

<h3>21. Отклонение оплаты тура по заблокированной карте</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение заблокированной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Всплывающее окно с сообщением "Ошибка! Банк отказал в проведении операции." В БД есть запись DECLINED</p>

<h3>Негативные сценарии</h3>

<h3>Тестирование поля "Номер карты"</h3>

<h3>22. Отклонение оплаты тура по несуществующей карте</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение несуществующей карты 4444 4444 4444 4443</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Всплывающее окно с сообщением "Ошибка! Банк отказал в проведении операции." В БД нет новой записи</p>

<h3>23. Отклонение оплаты тура по невалидному номеру карты</h3>
<ol>
    <li>В поле "Номер карты" ввести невалидное значение карты 4444 4444 4444 44</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Всплывающее окно с сообщением "Ошибка! Банк отказал в проведении операции." В БД нет новой записи</p>

<h3>24. Заполнение заявки с пустым полем "Номер карты"</h3>
<ol>
    <li>Поле "Номер карты" оставить пустым</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Номер карты" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>25. Отклонение оплаты тура по невалидному номеру карты (нули в поле)</h3>
<ol>
    <li>В поле "Номер карты" ввести невалидное значение карты 0000 0000 0000 0000</li>
    <li>В поле "Месяц" ввести текущую дату</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Всплывающее окно с сообщением "Ошибка! Банк отказал в проведении операции." В БД нет новой записи</p>

<h3>Тестирование поля "Месяц"</h3>

<h3>26. Заполнение заявки с невалидной датой(истекший срок действия карты)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести прошлый месяц</li>
    <li>В поле "Год" ввести значение текущего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Месяц" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>27. Заполнение заявки с невалидной датой(месяц)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести значение 13</li>
    <li>В поле "Год" ввести значение текущего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Месяц" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>28. Заполнение заявки с невалидной датой(месяц)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести значение 00</li>
    <li>В поле "Год" ввести значение текущего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Месяц" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>29. Заполнение заявки с пустым полем "месяц"</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>Поле "Месяц" оставить пустым</li>
    <li>В поле "Год" ввести значение текущего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Месяц" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>Тестирование поля "Год"</h3>

<h3>30. Заполнение заявки с невалидной датой(истекший срок действия карты)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение предыдущего года</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Год" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>31. Заполнение заявки с пустым полем "Год"</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>Поле "Год" оставить пустым</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Год" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>32. Заполнение заявки с невалидной датой(нули в дате)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение 00</li>
    <li>В поле "Владелец" ввести валидное значение (латиницей имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Год" подсвечивает сообщение: "Неверно указан срок действия карты" В БД нет новой записи</p>

<h3>Тестирование поля "Владелец"</h3>

<h3>33. Заполнение заявки с невалидным именем(русская раскладка имя и фамилия)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести невалидное значение русскими буквами (имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Владелец" подсвечивает сообщение: "недопустимые символы" В БД нет новой записи</p>

<h3>34. Заполнение заявки с невалидным именем(только имя)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести невалидное значение на латиницу (только имя)</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Владелец" подсвечивает сообщение: "введите полное имя и фамилию" В БД нет новой записи</p>

<h3>35. Заполнение заявки с пустым полем "Владелец"</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>Поле "Владелец" оставить пустым</li>
    <li>В поле "CVC/CVV" ввести валидное значение из трех цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "Владелец" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>Тестирование поля "CVC/CVV"</h3>

<h3>36. Заполнение заявки с невалидным CVC/CVV</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение на латинице (имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести невалидное значение из двух цифр</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "CVC/CVV" подсвечивает сообщение: "Значение поля должно состоять из трех цифр" В БД нет новой записи</p>

<h3>37. Заполнение заявки с пустым полем "CVC/CVV"</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение на латинице (имя и фамилию)</li>
    <li>Поле "CVC/CVV" оставить пустым</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "CVC/CVV" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h3>38. Заполнение заявки с невалидным CVC/CVV (нули в поле)</h3>
<ol>
    <li>В поле "Номер карты" ввести валидное значение активной карты (см. предусловия)</li>
    <li>В поле "Месяц" ввести валидное значение текущего месяца</li>
    <li>В поле "Год" ввести значение следующего года</li>
    <li>В поле "Владелец" ввести валидное значение на латинице (имя и фамилию)</li>
    <li>В поле "CVC/CVV" ввести значение 000</li>
    <li>Нажать кнопку "Продолжить"</li>
</ol>
<p><strong>Ожидаемый результат:</strong> Поле "CVC/CVV" подсвечивает сообщение: "Поле обязательно для заполнения" В БД нет новой записи</p>

<h2>Используемые инструменты</h2>
<ul>
    <li><strong>IntelliJ IDEA Ultimate</strong> - интегрированная среда разработки программного обеспечения для многих языков программирования, в частности Java, JavaScript, Python.</li>
    <li><strong>Gradle</strong> система автоматической сборки и управления зависимостями.</li>
    <li><strong>Java 11</strong> - 11 версия строго типизированного объектно-ориентированного языка программирования общего назначения.</li>
    <li><strong>JUnit 5</strong> - одна из самых популярных платформ модульного тестирования в экосистеме Java.</li>
    <li><strong>Selenide</strong> - это один из фреймворков для автоматизированного тестирования веб-приложений.</li>
    <li><strong>Lombok</strong> - это плагин компилятора, который добавляет в Java новые «ключевые слова» и превращает аннотации в Java-код.</li>
    <li><strong>JavaFaker</strong> - это библиотека, которая позволяет генерировать случайные данные.</li>
    <li><strong>Allure</strong> - это фреймворк для сбора данных и построения отчетов о тестировании кода.</li>
    <li><strong>Docker</strong> - приложение для создания и запуска контейнерных приложений.</li>
    <li><strong>MySql/PostgresSql</strong> - Заявлена поддержка данных СУБД</li>
    <li><strong>NodeJs</strong> - Среда исполнения</li>
    <li><strong>Google Chrome </strong>108.0.5359.126 - самый популярный и удобный браузер.</li>
    <li><strong>GitHub</strong> - веб-сервис для хостинга IT-проектов и их совместной разработки, основанный на системе контроля Git.</li>
</ul>

<h2>Возможные риски</h2>
<ol>
    <li>Отсутствие ТЗ, документации. Непонятно, какое поведение ожидать от SUT</li>
    <li>Если отсутствуют css селекторы (test-id), это осложнит тестирование. При обновлении верстки возможно падение тестов</li>
    <li>Заявлено поддержка 2х СУБД (PostgresSql и MySql), возможны сложности с поведением тестов на разных СУБД</li>
    <li>Данные кард захардкожены, поведение может отличаться от реальной системы. Бывают карты с длиной номера отличной от того, что предоставлено</li>
</ol>

<h2 style="margin-left:0px;">Интервальная оценка с учётом рисков (в часах)</h2>
<p>Планируемое время – 80 - 90 часов по итогам всех этапов от планирования до подготовки отчётных документов.</p>

<h2>План сдачи работ</h2>
<p>Подготовка автотестов и результаты прогона автотестов планируется выполнить в течение 2-3 недель.</p>