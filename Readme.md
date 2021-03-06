# Отчёт о тестировании приложения "Money Transfer"

## Краткое описание

Тестирование перевода денежных средств показало, что есть техническое ограничение на максимальный баланс счетов у клиентов. Если итоговый баланс клиента выходит за границу максимально допустимых лимитов, то перевод не будет успешным.

## Описание тестов

Проводилось функциональное позитивное тестирование перевода денежных средств. Было выполнено санитарное тестирование функции перевода денежных средств.  
Исходные данные взяты из [Задачи 1 — Money Transfer](https://github.com/netology-code/javaqa-homeworks/tree/master/programming):  
* текущий баланс счёта клиента 2_000_000_000 (два миллиарда рублей)  
* сумма перевода 500_000_000 (пятьсот миллионов рублей)


Тестирование функции перевода денежных средств проводилось в IntelliJ IDEA.
```java
    public class Main {
    public static void main(String[] args) {  
        int balance = 2_000_000_000;
        int transfer = 500_000_000;
        int total = balance + transfer;
        System.out.println(total);
    }
````
 
Ожидаемый результат:
2500000000


## Результаты

1. 100% неуспешных тестов
2. [Неверный тип данных для баланса счета](https://github.com/elenkalee/MoneyTransfer/issues/1)

## Общие рекомендации

В зависимости от того, предполагает ли бизнес, что у клиентов может быть на счету больше 2 147 483 647 рублей или нет, рекомендуется применить одно из решений: 
1. Ввести уведомление для пользователя, что максимальный баланс на счету не может быть больше 2 147 483 647 рублей  

2. Изменить тип данных для баланса денежных средств на счету:
* Сейчас используется переменнмая `int` с ограничением до 2 147 483 647 рублей.  
* Чтобы избежать подобных ошибок в будущем необходимо изменить на `long`, где максимум может быть до 9 223 372 036 854 775 807 рублей.
