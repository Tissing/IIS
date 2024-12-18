# ERD для БД Автомойки
# Схема
![erd](/materials/ERD1.png)

# Скрипт
```
Автомойки {
	id integer pk increments unique
	Долгота float
	Широта float
	Услуги set
}

Клиенты {
	id integer pk increments unique
	ФИО integer
	Номер_телефона varchar
	Марка_машины varchar
	Гос_номер varchar
}

Услуги {
	id integer pk increments unique
	Название varchar
	Цена integer
}

Записи {
	id integer pk increments unique
	Клиент_id integer *> Клиенты.id
	Автомойка_id integer *> Автомойки.id
	Услуга_id integer *> Услуги.id
	Стоимость integer
	Дата_Время datetime
	Оплачено bool
	Завершено bool
}
```
