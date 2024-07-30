##### [<-- back to Types data](../types_data/types_data.md)

## Типы с плавающей точкой

|  Тип   | Описание                       | Размер (бит) | Диапазон                | По умолчанию |
|:------:|--------------------------------|:------------:|-------------------------|:------------:|
| float  | Длинные дробные числа          |    32 бит    | от 1.4e-45f до 3.4e+38f |     0,0f     |
| double | Дробные числа двойной точности |    64 бит    | от 4.9e-324 до 1.7e+308 |     0,0d     |

* Стандарт [IEEE754](https://ru.wikipedia.org/wiki/IEEE_754-2008)
* Побитовые операции не поддерживаются.

Литералы:

* Обычная запись: `-1.234`
* Экспоненциальная запись: `-123.4e-2` (−123.4 * 10−2)
* Шестнадцатеричная запись: `0xFFFFpFF` (FFFF * 2 FF)
* С суффиксом типа: `38f`, `3e19d`, `123.4e-2f`, `444.444d`

Особые случаи:

* Деление положительного числа на 0 дает +∞
* Деление отрицательного числа на 0 дает −∞
* Деление 0 на 0 дает NaN
* Переполнение дает +∞ или −∞, в зависимости от направления.
* NaN != NaN

Ключевое слово strictfp:

* Java использует FPU для вычислений с плавающей точкой, но регистры FPU могут быть шире 64 бит, в результате вычисления могут отличаться.
* Модификатор strictfp включает режим строгой совместимости, результаты будут идентичны на любом процессоре.