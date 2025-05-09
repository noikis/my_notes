Нужно разработать микросервис для счетчиков статистики. Сервис должен уметь взаимодействовать с клиентом при помощи REST API или JSON RPC запросов. Также нужно реализовать валидацию входных данных.

**API методы:**

* Метод сохранения статистики.  
* Метод показа статистики.  
* Метод сброса статистики.  
* Метод сохранения статистики.

**Принимает на вход:**

* date \- дата события.  
* views \- количество показов.  
* clicks \- количество кликов.  
* cost \- стоимость кликов (в рублях с точностью до копеек).

Поля views, clicks и cost \- опциональные. Статистика агрегируется по дате.

**Принимает на вход:**

* from \- дата начала периода (включительно).  
* to \- дата окончания периода (включительно).

Отвечает статистикой, отсортированной по дате. 

**В ответе должны быть поля:**

* date \- дата события.  
* views \- количество показов.  
* clicks \- количество кликов.  
* cost \- стоимость кликов.  
* cpc \= cost/clicks (средняя стоимость клика).  
* cpm \= cost/views \* 1000 (средняя стоимость 1000 показов).

**Метод сброса статистики**

* Удаляет всю сохраненную статистику.

**Критерии приемки:**

* язык программирования: Go/PHP/Python.  
* можно использовать любое хранилище(PostgreSQL, MySQl, Redis и т.д.).  
* или обойтись без него (in-memory). При использовании СУБД нужен файл с запросами на создание \- \- всех необходимых таблиц.  
* формат даты YYYY-MM-DD.  
* стоимость указывается в рублях с точностью до копеек.  
* простая инструкция для запуска (в идеале — с возможностью запустить в docker).

**Усложнения:**

* в методе показа статистики можно выбрать сортировку по любому из полей ответа.  
* покрытие unit-тестами.  
* документация (достаточно структурированного описания методов, примеров их вызова в README.md).

**Автор: [https://link.sergeyfilichkin.ru/tg\_t](https://link.sergeyfilichkin.ru/tg_t)**