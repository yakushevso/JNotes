##### [<-- back to Types data](../types_data/types_data.md)

## Целочисленные типы

|  Тип  | Описание               | Размер (бит) | Диапазон                                               | По умолчанию |
|:-----:|------------------------|:------------:|--------------------------------------------------------|:------------:|
| byte  | Наименьшие целые числа |    8 бит     | от -128 до 127                                         |      0       |
| short | Короткие целые числа   |    16 бит    | от -32768 до 32767                                     |      0       |
| char  | Символы                |    16 бит    | беззнаковое целое число, символ UTF-16 (буквы и цифры) |    \u0000    |
|  int  | Целые числа            |    32 бит    | от -2147483648 до 2147483647                           |      0       |
| long  | Длинные дробные числа  |    64 бит    | от -9223372036854775808L до 9223372036854775807L       |      0L      |

Литералы:

* Десятичное число (_Decimal_): `123`
* Восьмеричное число (_Octal_): `0123`
* Шестнадцатеричное число (_Hex_): `0x123`
* Двоичное число (_Binary_): `0b101` (с Java 7)
* С подчеркиванием: `123_456_789` (с Java 7)
* С суффиксом L для long: `123456789L`