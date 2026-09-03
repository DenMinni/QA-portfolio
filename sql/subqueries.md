# SQL подзапросы — примеры

## Самая дорогая комната и её владелец

SELECT Users.*
FROM Users
INNER JOIN Rooms
    ON Users.id = Rooms.owner_id
WHERE Rooms.price = (
    SELECT MAX(price)
    FROM Rooms
);

Запрос находит максимальную цену комнаты и выводит пользователей, которые являются владельцами комнат с такой ценой.

## Самая дорогая покупка каждого члена семьи

SELECT
    FamilyMembers.member_name,
    (
        SELECT MAX(Payments.unit_price)
        FROM Payments
        WHERE Payments.family_member = FamilyMembers.member_id
    ) AS good_price
FROM FamilyMembers;

Коррелированный подзапрос для каждого члена семьи находит максимальную стоимость его покупки.
