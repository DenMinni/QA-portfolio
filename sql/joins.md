# SQL JOIN — примеры

## Получение студентов и их классов

SELECT Class.name, Student.first_name
FROM Class
INNER JOIN Student_in_class
    ON Class.id = Student_in_class.class
INNER JOIN Student
    ON Student_in_class.student = Student.id;

Запрос связывает классы, таблицу связей и студентов, чтобы получить имя класса и имя ученика.

## Количество пассажиров на каждом рейсе

SELECT Trip.id, COUNT(Pass_in_trip.passenger) AS count
FROM Trip
LEFT JOIN Pass_in_trip
    ON Trip.id = Pass_in_trip.trip
GROUP BY Trip.id;

Используется LEFT JOIN, чтобы в результате отображались даже рейсы без пассажиров.

## Компании, выполняющие рейсы на Boeing

SELECT DISTINCT Company.name
FROM Company
INNER JOIN Trip
    ON Company.id = Trip.company
WHERE Trip.plane LIKE 'Boeing%';

DISTINCT используется, чтобы каждая компания отображалась только один раз.
