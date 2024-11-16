# Учебное приложение по автомойке
Интеграция Информационных Систем <br>

## Estimates (Примерные показатели):
  <table>
  <tr>
    <td>Регион</td>
    <td>Сахалинская область</td>
  </tr>
  <tr>
    <td>Численность региона</td>
    <td>500К человек</td>
  </tr>
  <tr>
    <td>DAU</td>
    <td>15% от 500К = 75К </td>
  </tr>
  <tr>
    <td>RPS</td>
    <td>75K/24/3600 ~= 1</td>
  </tr>
</table>


## Функциональные требования:
 ![User Case](https://github.com/Tissing/IIS/blob/main/UserCases.png)
### Сценарии использования
#### UC1: Найти автомойку
 <table>
  <tr>
    <td>Участники</td>
    <td>Пользователь приложения</td>
  </tr>
  <tr>
    <td>Предусловия</td>
    <td> Пользователь зарегистрирован и авторизован</td>
  </tr>
  <tr>
    <td>Условия для срабатывания</td>
    <td>Пользователь нажимает кнопку "Найти мойку"</td>
  </tr>
  <tr>
    <td>Признак успешности</td>
    <td>Пользователь выбрал автомойку</td>
  </tr>
</table>

##### Базовый сценарий:
1. Система проверяет, что клиент передал свою геолокацию.<br>
ЕСЛИ: Геолокации нет,<br>
ТО: Система переходит к базовому сценарию 3.
2. Система ищет ближайшие к позиции клиента мойки. ([AL01]())
3. Формируется список моек.
4. Система отображает "Экран с картой и списком моек". ([UI_01]())
5. Система ожидает выбора мойки клиентом.
6. Система переходит к [UC4]().
7. Сценарий завершен.

##### Базовый сценарий 2:
1. Система выводит сообщение клиенту с просьбой разрешить передачу геолокации.
2. ЕСЛИ: клиент разрешил передачу геолокации.<br>
ТО: Система переходит в "Базовый сценарий шаг 2".<br>
ИНАЧЕ: Система переходит в "Базовый сценарий 3".

##### Базовый сценарий 3:
1. Система отображает поле для ввода адреса.
2. Система ожидает от пользователя ввод адреса.
3. Система переходит в "Базовый сценарий шаг 2.



<!-- ///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////// -->



#### UC2: Выбрать дату и время

<table>
  <tr>
    <td>Участники</td>
    <td>Пользователь приложения</td>
  </tr>
  <tr>
    <td>Предусловия</td>
    <td> Пользователь зарегистрирован и авторизован</td>
  </tr>
  <tr>
    <td>Условия для срабатывания</td>
    <td>Пользователь нажимает кнопку "Выбрать дату"</td>
  </tr>
  <tr>
    <td>Признак успешности</td>
    <td>Пользователь выбрал дату и время</td>
  </tr>
</table>

##### Базовый сценарий:
1. Система проверяет, выбрал ли пользователь автомойку.
ЕСЛИ: Автомойка не выбрана.
ТО: Направляет в [UC1]().
2. Система проверяет, наличие выбранных услуг.
ЕСЛИ: Хотя бы 1 услуга не выбрана.
ТО: Направляет в [UC4]().
3. Система запрашивает доступное время на мойке из БД.
4. Система оценивает время исходя из выбранных услуг.
5. Система формирует периоды времени, в которые пользователь может быть обслужен.
6. Система отображает "Экран с доступным временем". ([UI_02]())
7. Система ожидает выбора мойки клиентом.
8. Система резервирует выбранное время в БД.
9. Система переходит к [UC3]().
10. Сценарий завершен.



<!-- ///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////// -->

#### UC3: Оплатить

<table>
  <tr>
    <td>Участники</td>
    <td>Пользователь приложения</td>
  </tr>
  <tr>
    <td>Предусловия</td>
    <td> Пользователь зарегистрирован и авторизован</td>
  </tr>
  <tr>
    <td>Условия для срабатывания</td>
    <td>Пользователь нажимает кнопку "Оплатить" и выберет способ оплаты</td>
  </tr>
  <tr>
    <td>Признак успешности</td>
    <td>Оплата прошла успешна</td>
  </tr>
</table>

##### Базовый сценарий:
1. Система проверяет наличие выбранных пунктов "Автомойка", "Услуги" и "Дата и время".
2. Система формирует итоговый вариант заказа пользователя.
3. Система отображает экран "Итоговый заказ". ([UI_3]())
4. Система ожидает выбора способа оплаты.
ЕСЛИ: Способ оплаты - "Онлайн оплата".
ТО:  Работа с API платежной системы.
6. Формируется номер заказа.
7. Заказа помещается в БД и в очередь автомойки.
8. Отображение сообщения о том, что заказ сформирован.
9. Сценарий завершен.


<!-- ///////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////// -->

#### UC4: Выбрать услугу

<table>
  <tr>
    <td>Участники</td>
    <td>Пользователь приложения</td>
  </tr>
  <tr>
    <td>Предусловия</td>
    <td> Пользователь зарегистрирован и авторизован</td>
  </tr>
  <tr>
    <td>Условия для срабатывания</td>
    <td>Пользователь нажимает кнопку "Выбрать дату"</td>
  </tr>
  <tr>
    <td>Признак успешности</td>
    <td>Пользователь выбрал дату и время</td>
  </tr>
</table>

##### Базовый сценарий:



##### Альтернативные сценарии:








#### UC5: Отменить запись

<table>
  <tr>
    <td>Участники</td>
    <td>Пользователь приложения</td>
  </tr>
  <tr>
    <td>Предусловия</td>
    <td> Пользователь зарегистрирован и авторизован</td>
  </tr>
  <tr>
    <td>Условия для срабатывания</td>
    <td>Пользователь нажимает кнопку "Выбрать дату"</td>
  </tr>
  <tr>
    <td>Признак успешности</td>
    <td>Пользователь выбрал дату и время</td>
  </tr>
</table>

##### Базовый сценарий:



##### Альтернативные сценарии:








#### UC6: Техническая поддержка

<table>
  <tr>
    <td>Участники</td>
    <td>Пользователь приложения</td>
  </tr>
  <tr>
    <td>Предусловия</td>
    <td> Пользователь зарегистрирован и авторизован</td>
  </tr>
  <tr>
    <td>Условия для срабатывания</td>
    <td>Пользователь нажимает кнопку "Выбрать дату"</td>
  </tr>
  <tr>
    <td>Признак успешности</td>
    <td>Пользователь выбрал дату и время</td>
  </tr>
</table>

##### Базовый сценарий:



##### Альтернативные сценарии:






##### Альтернативные сценарии:
AC_1. Некорректный запрос пользователя. <br>
АС_2. Обрыв соединения приложения с Интернетом\ Отсутствует подключение к серверу. <br>
АС_3. Упала БД<br>
AC_4. Попытка двух пользователей записаться на одно время.


## Нефункциональные требования:

### AL01 Алгоритм поиска моек по адресу или геолокации
1. Система формирует запрос в БД
2. ...
3. ...
4. Система возвращает список моек сценарию, который вызвал алгоритм

## Интерфейсы:

### UI_1 "Экран с картой и списком моек"
![]()

### UI_2 "Экран с доступным временем"
![]()










