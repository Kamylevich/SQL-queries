# Примеры моих SQL запросов
## Задание: 20
Найдите производителей, выпускающих по меньшей мере три различных модели ПК. Вывести: Maker, число моделей ПК.

**Мое решение:**

*select maker, count(model) from product where type='pc' group by maker having count(model)>2*

## Задание: 25

Найдите производителей принтеров, которые производят ПК с наименьшим объемом RAM и с самым быстрым процессором среди всех ПК, имеющих наименьший объем RAM. Вывести: Maker

**Мое решение:**

*select distinct maker from product join pc on product.model=pc.model where maker in (select maker from product where type = 'printer') and speed in(select max(speed) from pc where ram in (select min(ram) from pc)) and ram in (select min(ram) from pc)*

## Задание: 28

Используя таблицу Product, определить количество производителей, выпускающих по одной модели.

**Мое решение:**

_Select count(maker) from ( select maker from product group by maker having count(*) =1 ) qty_

## Задание: 35

В таблице Product найти модели, которые состоят только из цифр или только из латинских букв (A-Z, без учета регистра).
Вывод: номер модели, тип модели.

**Мое решение:**

*select model, type from product where model not like '%[^0-9]%' or model not like '%[^A-Z]%'*


_Задачи взяты с сайта sql-ex.ru_
_На момент написания файла мною было решено 28 задач._
