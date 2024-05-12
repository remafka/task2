# task2 
## Часть №1 Тестирование

### Ввод данных 

Реализуем ввод даннных (чтобы ввод считывался через файл input.txt), а также создаём список list, который содержит все введенные элементы. Затем важна проверка, что файл найден и код сможет работать (ошибки пустого файла быть не может, так как по условию файл содержит хотя бы 1 элемент), в ином случае код выведен "Файл не найден". Вызовем функции _min; _max; _sum; _mult.

```cmd
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class n {

    public static void main(String[] args) {

        try {
            String path = "input.txt";
            File file = new File(path);
            Scanner scanner = new Scanner(file);
            String line = scanner.nextLine();
            String[] num = line.split(" ");

            long[] lists = new long[num.length];
            for (int i = 0; i < num.length; i++) {
                lists[i] = Long.parseLong(num[i]);
            }
            System.out.println("Минимальное число: " + _min(lists));
            System.out.println("Максимальное число: " + _max(lists));
            System.out.println("Сумма всех чисел: " + _sum(lists));
            System.out.println("Произведение всех чисел: " + _mult(lists));

        } catch (FileNotFoundException e) {
            System.out.println("Файл не найден.");
        }
    }
}
```

### _min
```cmd
public static long _min(long[] num) {
    long min = num[0];
    for (long i : num) {
        if (i < min) {
            min = i;
        }
    }
    return min;
}
```

### _max
```cmd
public static long _max(long[] num) {
    long max = num[0];
    for (long i : num) {
        if (i > max) {
            max = i;
        }
    }
    return max;
}
```
### _sum
```cmd
public static long _sum(long[] num) {
    long sum = 0;
    for (long i : num) {
        sum += i;
    }
    return sum;
}
```
### _mult
```cmd
public static long _mult(long[] num) {
    long mult = 1;
    for (long i : num) {
        mult *= i;
    }
    return mult;
}
```
## Полный код:

```cmd
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class n {

    public static void main(String[] args) {

        try {
            String path = "input.txt";
            File file = new File(path);
            Scanner scanner = new Scanner(file);
            String line = scanner.nextLine();
            String[] num = line.split(" ");

            long[] lists = new long[num.length];
            for (int i = 0; i < num.length; i++) {
                lists[i] = Long.parseLong(num[i]);
            }
            System.out.println("Минимальное число: " + _min(lists));
            System.out.println("Максимальное число: " + _max(lists));
            System.out.println("Сумма всех чисел: " + _sum(lists));
            System.out.println("Произведение всех чисел: " + _mult(lists));

        } catch (FileNotFoundException e) {
            System.out.println("Файл не найден.");
        }
    }

    public static long _min(long[] num) {
        long min = num[0];
        for (long i : num) {
            if (i < min) {
                min = i;
            }
        }
        return min;
    }

    public static long _max(long[] num) {
        long max = num[0];
        for (long i : num) {
            if (i > max) {
                max = i;
            }
        }
        return max;
    }

    public static long _sum(long[] num) {
        long sum = 0;
        for (long i : num) {
            sum += i;
        }
        return sum;
    }

    public static long _mult(long[] num) {
        long mult = 1;
        for (long i : num) {
            mult *= i;
        }
        return mult;
    }
}

```
## Тесты для проверки корректности:
Ввод:
```cmd
1 2 3 4 5 
```
Вывод:

Минимальное число: 1

Максимальное число: 5

Сумма всех чисел: 15

Произведение всех чисел: 120

Ввод: 
```cmd
0 9 6 5 4 8
```
Вывод:

Минимальное число: 0

Максимальное число: 9

Сумма всех чисел: 32

Произведение всех чисел: 0

Ввод:
```cmd
9 88 5 4 1 8
```
Вывод:

Минимальное число: 1

Максимальное число: 88

Сумма всех чисел: 115

Произведение всех чисел: 126720

Ввод:
```cmd
8 7 5 4 52 110000 9 0 8 6 9 5 3 3 3 3 33 3 33 3 4 4 4 5 8 0 90 90 90
```
Вывод:

Минимальное число: 0

Максимальное число: 110000

Сумма всех чисел: 110492

Произведение всех чисел: 0

## Создание теста с 1 млн элементов 
```cmd
import java.io.FileWriter;
import java.io.IOException;
import java.util.Random;

public class tests {

    public static void main(String[] args) {
        generate("input.txt", 1000000); 
    }

    public static void generate(String name, int amount) {
        Random r = new Random();
        try {
            FileWriter w = new FileWriter(name);
            for (int i = 0; i < amount; i++) {
                w.write(r.nextInt(1000000) + " ");
            }
            w.close();
            System.out.println("Файл " + name + " с " + amount + " числами создан.");
        } catch (IOException e) {
            System.out.println("Ошибка при создании файла.");
        }
    }
}
```
Полный файл, созданный с помощью кода выше находится в файле репозитория.

Ввод:
```cmd
858869 656798 928843 525413 513324 456604 ...
```
Вывод:

Минимальное число: 0

Максимальное число: 999997

Сумма всех чисел: 1688404761

Произведение всех чисел: 0

## Время выполнения программы
Будем использовать currentTimeMillis(), чтобы понять сколько времени выполняется код:

```cmd
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class n {

    public static void main(String[] args) {
        long startTime = System.currentTimeMillis();

        try {
            String path = "input.txt";
            File file = new File(path);
            Scanner scanner = new Scanner(file);
            String line = scanner.nextLine();
            String[] num = line.split(" ");

            long[] lists = new long[num.length];
            for (int i = 0; i < num.length; i++) {
                lists[i] = Long.parseLong(num[i]);
            }
            System.out.println("Минимальное число: " + _min(lists));
            System.out.println("Максимальное число: " + _max(lists));
            System.out.println("Сумма всех чисел: " + _sum(lists));
            System.out.println("Произведение всех чисел: " + _mult(lists));

        } catch (FileNotFoundException e) {
            System.out.println("Файл не найден.");
        }
        long endTime = System.currentTimeMillis();
        System.out.println("Время выполнения программы: " + (endTime - startTime) + " миллисекунд");
    }

    public static long _min(long[] num) {
        long min = num[0];
        for (long i : num) {
            if (i < min) {
                min = i;
            }
        }
        return min;
    }

    public static long _max(long[] num) {
        long max = num[0];
        for (long i : num) {
            if (i > max) {
                max = i;
            }
        }
        return max;
    }

    public static long _sum(long[] num) {
        long sum = 0;
        for (long i : num) {
            sum += i;
        }
        return sum;
    }

    public static long _mult(long[] num) {
        long mult = 1;
        for (long i : num) {
            mult *= i;
        }
        return mult;
    }
}

```
## График зависимости времени выполнения от кол-ва чисел в файле


![Иллюстрация к проекту](https://github.com/remafka/task2/blob/0a40dc1b74455d22cdb0013d6fa0f317e99e896d/grafic.png)
