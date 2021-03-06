# Операторы перехода break, continue, return

## Оператор break

С оператором  **break** мы познакомились [в шестом уроке](006-Java-switch-case.md) во время знакомства с оператором выбора Switch. С помощью **break** мы выходим из вариантов выбора.

### Прерывание цикла

С помощью **break** можно выходить из цикла.

```Java
public static void searchFor () {
    for (int i = 0; i <= 20; i++) {
        if (i == 4) {
        break; // выйти из цикла при i равной 4.
        }
        System.out.println("Значение i: " + i);
    }
    System.out.println("Цикл завершен.");
}
```

Я могу себе представить такой вариант выхода из бесконечных методов или рекурсивных, где через оператор **break** мы указываем условия выхода.

```Java
// Использование break для выхода из while-цикла.
import java.util.Scanner;

class UserInputSum {
   public static void main(String[] args) {

      double number, sum = 0.0;
      Scanner input = new Scanner(System.in);
      
      while (true) {
         System.out.print("Enter a number: ");
         number = input.nextDouble();
         
         if (number < 0.0) {
            break;
         }
         
         sum += number;
      }
      System.out.println("Sum = " + sum);
   }
}
```

В языках постарше Java был оператор **goto** - перейти к определённой строчке. Break не должен и не может заменить оператор, который в Java не внесли создатели. Но зоны видимости и **break** позволяют делать интересные вещи:

```Java
public class Break {
	static void quarantine(Boolean quarantine) {
		quarantineZone:
		{
			if (quarantine) {
				break quarantineZone; // выход из зоны карантина
			}
			System.out.println("Мы в картантине");
		}
	}
}
```

![Эскиз](./res/025-java-break-statement-works.jpg "break")

Но я буду согласен с вами, если вы скажите, что решить вопрос с карантином можно было бы и через **if-else**.

## Оператор continue

```Java
// Демонстрирует continue.
public class Continue {

  public static void main(String[] args) {
    for (int i = 0; i < 10; i++) {
      System.out.print(i + " ");
      if (i % 2 == 0) {
        continue;
      }
      System.out.println("");
    }
  }
}
/* Вывод в терминале
0 1
2 3
4 5
6 7
8 9
*/
```

## Оператор return

Return мы знаем из [урока номер 12](013-Java-methods-void-return.md) про методы.
Оператор return используют для выполнения явного выхода из метода. Оператор можно использовать в любом месте метода для возврата управления тому объекту, который вызвал данный метод. Таким образом, return прекращает выполнение метода, в котором он находится.

```Java
// Демонстрирует return.
public class Return {
	static void quarantine(Boolean quarantine) {
		quarantineZone:
		{
			if (quarantine) {
				return; // выход из программы
			}
			System.out.println("Мы в картантине");
		}
	}
}
```

Как мы видим return можно использовать и в исполняем методе, а не только в возвратном. Не уверен, что эти операторы с завтрашнего дня надо активно использовать, но знать их надо.

## Дополнительные ссылки

Операции с метками, branching statements - https://docs.oracle.com/javase/tutorial/java/nutsandbolts/branch.html

## Домашнее задание

Напишите программу, которая выводит на консоль простые числа в промежутке от [2, 100].
Используйте для решения этой задачи оператор "%" (остаток от деления) и циклы. Используйте циклы с метками:
