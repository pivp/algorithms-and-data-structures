#### <div align="center"> [Задача 1296. Гиперпереход](https://acm.timus.ru/problem.aspx?space=1&num=1296) </div>

>Ограничение времени: 1.0 секунды
>Ограничение памяти: 64 МБ

###### Условие:

> Гиперпереход, открытый ещё в начале XXI-го века, и сейчас остаётся основным способом перемещения на расстояния до сотен тысяч парсеков. Но совсем недавно физиками открыто новое явление. Оказывается, длительностью альфа-фазы перехода можно легко управлять. Корабль, находящийся в альфа-фазе перехода, накапливает гравитационный потенциал. Чем больше накопленный гравитационный потенциал корабля, тем меньше энергии потребуется ему на прыжок сквозь пространство. Ваша цель — написать программу, которая позволит кораблю за счёт выбора времени начала альфа-фазы и её длительности накопить максимальный гравитационный потенциал.
>
> В самой грубой модели грави-интенсивность — это последовательность целых чисел *pi*. Будем считать, что если альфа-фаза началась в момент *i* и закончилась в момент *j*, то накопленный в течение альфа-фазы потенциал — это сумма всех чисел, стоящих в последовательности на местах от *i* до *j*.

###### Исходные данные:

> В первой строке входа записано целое число *N* — длина последовательности, отвечающей за грави-интенсивность (0 ≤ *N* ≤ 60000). Далее идут *N* строк, в каждой записано целое число *pi* (−30000 ≤ *pi* ≤ 30000).

###### Результат:

> Максимальный гравитационный потенциал, который может накопить корабль в альфа-фазе прыжка. Считается, что потенциал корабля в начальный момент времени равен нулю.

| Исходные данные                         | Результат |
| --------------------------------------- | --------- |
| `10 31 -41 59 26 -53 58 97 -93 -23 84 ` | `187`     |
| `3 -1 -5 -6 `                           | `0`       |

###### Описание алгоритма:

> Задача на поиск максимальной положительной последовательности, необходимо вывести максимальное значение последовательности. Суммируем последовательность, если сумма больше чем прошлый результат, обновляем результат, если последовательность становится нулевой или меньше нуля, то сбрасываем последовательность до нуля.

###### Реализация:

```cpp
#include <iostream>

int main() {

    //input of the number of elements
    int n;
    std::cin >> n;

    int sequence = 0; // sum of the elements
    int potential = 0; // result value

    for (int i = 0; i < n; i++) // read the element and examine the sequence
    {
        // input element
        int input;
        std::cin >> input;

        sequence += input;

        if (sequence > potential) potential = sequence; // if the sequence grows, then we increase the value of the possible potential
        if (sequence < 0) sequence = 0; // if the sequence is less than 0, then it has no meaning
    }

    // result output
    std::cout << potential << std::endl;

    return 0;
}
```

###### Подтверждение выполнения:
![image](https://user-images.githubusercontent.com/75897943/157522717-7353568a-0f0f-4ec7-a2b0-077ec3c2fa1a.png)
