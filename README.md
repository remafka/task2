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
            String path = "numbers.txt";
            File file = new File(path);
            Scanner scanner = new Scanner(file);
            String line = scanner.nextLine();
            String[] num = line.split(" ");

            int[] lists = new int[num.length];
            for (int i = 0; i < num.length; i++) {
                lists[i] = Integer.parseInt(num[i]);
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

Добавим ещё подсчётчик времени выполнения программы. 

```cmd
import java.io.File;
import java.io.FileNotFoundException;
import java.util.Scanner;

public class n {

    public static void main(String[] args) {
        long m = System.currentTimeMillis();
        try {
            String path = "input.txt";
            File file = new File(path);
            Scanner scanner = new Scanner(file);
            String line = scanner.nextLine();
            String[] num = line.split(" ");

            int[] lists = new int[num.length];
            for (int i = 0; i < num.length; i++) {
                lists[i] = Integer.parseInt(num[i]);
            }
            System.out.println("Минимальное число: " + _min(lists));
            System.out.println("Максимальное число: " + _max(lists));
            System.out.println("Сумма всех чисел: " + _sum(lists));
            System.out.println("Произведение всех чисел: " + _mult(lists));

        } catch (FileNotFoundException e) {
            System.out.println("Файл не найден.");
        }
        System.out.println((double)(System.currentTimeMillis() - m));
    }
}
```

### _min
```cmd
public static int _min(int[] num) {
        int min = num[0];
        for (int i : num) {
            if (i < min) {
                min = i;
            }
        }
        return min;
    }
```

### _max
```cmd
public static int _max(int[] num) {
        int max = num[0];
        for (int i : num) {
            if (i > max) {
                max = i;
            }
        }
        return max;
    }
```
### _sum
```cmd
public static int _sum(int[] num) {
        int sum = 0;
        for (int i : num) {
            sum += i;
        }
        return sum;
    }
```
### _mult
```cmd
 public static int _mult(int[] num) {
        int mult = 1;
        for (int i : num) {
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
        long m = System.currentTimeMillis();
        try {
            String path = "input.txt";
            File file = new File(path);
            Scanner scanner = new Scanner(file);
            String line = scanner.nextLine();
            String[] num = line.split(" ");

            int[] lists = new int[num.length];
            for (int i = 0; i < num.length; i++) {
                lists[i] = Integer.parseInt(num[i]);
            }
            System.out.println("Минимальное число: " + _min(lists));
            System.out.println("Максимальное число: " + _max(lists));
            System.out.println("Сумма всех чисел: " + _sum(lists));
            System.out.println("Произведение всех чисел: " + _mult(lists));

        } catch (FileNotFoundException e) {
            System.out.println("Файл не найден.");
        }
        System.out.println((double)(System.currentTimeMillis() - m));
    }

    public static int _min(int[] num) {
        int min = num[0];
        for (int i : num) {
            if (i < min) {
                min = i;
            }
        }
        return min;
    }

    public static int _max(int[] num) {
        int max = num[0];
        for (int i : num) {
            if (i > max) {
                max = i;
            }
        }
        return max;
    }

    public static int _sum(int[] num) {
        int sum = 0;
        for (int i : num) {
            sum += i;
        }
        return sum;
    }

    public static int _mult(int[] num) {
        int mult = 1;
        for (int i : num) {
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

2111.0
```
```
```
```
```
```
```
```
```
```
```
```
```
```
