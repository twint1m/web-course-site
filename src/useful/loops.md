---
title: "JS. Начало #3. Циклы"
description: "Про циклы и их разновидности"
date: "2025-04-01"
---

_Автор: Чердаков Анатолий Сергеевич, Нерсисян Артем Сосович_

### Введение

Циклы встречаются в работе большинства программистов практически на всех языках программирования. Они есть в Java, JavaScript, PHP, Python, C++ — везде. Циклов в привычном виде нет разве что в очень низкоуровневых языках, близких к «железу», таких как ассемблер.

## Что такое циклы?

Цикл в программировании — это управляющая конструкция, которая заставляет какой-то блок кода выполняться несколько раз. Циклы есть в большинстве языков программирования. Чаще всего их объявляют командами for, while или repeat.

Циклы выполняют блок кода до тех пор, пока выполняется условие. С помощью условия можно управлять тем, сколько раз выполнять код, который называется телом цикла. Например, выполнять код до тех пор, пока все сообщения не будут напечатаны.

Цикл завершается, когда условие перестаёт выполняться. Такого может и не произойти и цикл будет работать бесконечно. Обычно бесконечный цикл — результат ошибки программиста. Программа зависает, так как тело цикла будет выполняться вечно.

Опишем работу цикла словами.

1. Проверь, выполняется ли условие.
2. Если условие выполняется, выполни тело цикла. Затем вернись в пункт 1.
3. Если условие не выполняется, цикл завершён.

Цикл удобно представлять в виде схемы:

![](/web-course-site/loops/image1.png)

**Зачем нужны циклы и какие задачи они решают?**

Циклами пользуются для задач, в рамках которых нужно повторить одно и то же действие несколько раз. Таких задач в разработке много. Например:

- построчно посчитать данные из файла;
- обработать каждый элемент структуры данных по очереди;
- видоизменить целый ряд данных;
- решить математическую задачу;
- обновить экран.
- решить математическую задачу;
- обновить экран.

Некоторые алгоритмы итеративные, то есть работают с несколькими итерациями — повторениями. Чтобы их реализовать, обычно нужны циклы.

Частичной альтернативой циклам в программировании можно назвать некоторые встроенные функции высшего порядка. Они могут выполнять несколько действий, например с массивом. Но такие функции есть не во всех языках и подходят не для всего. Циклы универсальнее.

**Типы циклов в JavaScript**

Первый тип цикла который мы рассмотрим - это стандартный цикл for с заданным количеством итераций.Он имеет следующий синтаксис:

```javascript

for (начало; условие; шаг) {
    // тело цикла
}

```

Вот пример:

```javascript

for (let i = 0; i < 3; i++) {
    console.log(i);
}

```

Внутри нашего цикла переменная счетчик i будет увеличивать свое значение на каждой итерации, конкретно в этом цикле она примет три значения, которые и будут выведены в консоль, 0, 1, 2, далее уже не будет соответствия условию i < 3 и тело цикла выполнено не будет. В качестве шага не обязательно использовать инкременту, а можно изменять переменную-счетчик на свое усмотрение (например, сделать шаг в 2). Любую из частей этого цикла можно пропустить, например, пропустив все части, мы создадим вечный цикл:
```javascript

for (;;) {
    // тело цикла
}

```

При этом точки запятой следует писать, иначе будет допущена ошибка синтаксиса.

Следующий тип циклов это while. Он имеет следующий синтаксис:

```javascript
while (условие) {
    // тело цикла
}
```

Пример:

```javascript
let i = 0;

while (i < 3) {
    console.log(i);
    i++;
}
```

В нашем примере так же будет выполнено три итерации, в которых в консоль будет выведено 0, 1, 2. По итогу выполнения цикла переменная i будет доступна вне цикла, а её значение будет равно трем. В нашем конкретном примере очень важно не забыть изменять значение переменной i, иначе мы можем попасть в вечный цикл, ведь, если мы не изменяли бы значение i, то оно бы никогда не стало большим или равным трем, чтобы выполнение цикла прекратилось.

Любое выражение или переменная может быть условием цикла, а не только сравнение: условие while вычисляется и преобразуется в логическое значение. Важно отметить, что может быть например такая ситуация:

```javascript

let i = 10;

while (i < 5) {
    console.log(i);
    i++;
}

```

В таком случае тело цикла не выполнится ни разу, ведь условие изначально неверно.

И последний тип цикла, который мы рассмотрим, это do..while. Он гарантирует то, что независимо от условия тело цикла будет выполнено **ХОТЯ БЫ 1 РАЗ**. Его синтаксис:

```javascript

do {

// тело цикла

} while (условие);

```

Рассмотрим предыдущий пример. В нём у нас тело цикла ни разу не выполнится, но, если мы перепишем код в цикле do..while

```javascript

let i = 10;

do {
    
console.log(i);

i++;

} while (i < 5);

```

Теперь же тело цикла выполнится ровно 1 раз, а потом только будет проверена истинность условия, и т.к оно ложно, то цикл прекратит своё выполнение.

**Перебор массивов и объектов**

Первый способ перебора массивов и других перечисляемых объектов это при помощи for..of. Он имеет следующий синтаксис:

```javascript

let fruits = ["Яблоко", "Апельсин", "Слива"];

for (let fruit of fruits) {
    console.log( fruit );
}

```

Мы при помощи данного цикла может проходиться по значениям, таким образом в консоль будут выведены значения Яблоко, Апельсин и Слива. Также цикл for..of можно использовать для перебора строки по символам:

```javascript

let word = "Hello";

for (let char of word) {
    console.log(char);
}

```

Есть еще 1 цикл for..in, используется он для перебора всех свойств объекта и имеет такой синтаксис:

```javascript

for (key in object) {

    // тело цикла выполняется для каждого свойства объекта

}

```

Например, у нас есть объект user, выведем его свойства:

```javascript

let user = {
    name: "John",
    age: 30,
    isAdmin: true
};

for (let key in user) {
    // ключи
    console.log( key ); // name, age, isAdmin
    
    // значения ключей
    console.log( user[key] ); // John, 30, true
}

```

Если же мы попробуем пройтись циклом for..in по массиву, то нам будут выведены не значения, а именно свойства, которые есть у массива, например, индексы элементов, или какие-либо другие свойства, по типу length (в браузере есть объекты, называемые “псевдомассивы”, они выглядят как массивы, но имеют дополнительные методы и свойства,которые цикл тоже выведет):

```javascript

let arr = [1, 2, 3]

for (let prop in arr) {

    console.log(prop) // 0, 1, 2

}

```

Важно отметить, что использовать for..in для массивов не стоит, ведь этот цикл придумывался для произвольных объектов и в 100 раз медленнее.

Рассмотрим еще такую тему, как “Методы массивов forEach, map, filter, reduce как альтернатива циклам**”.** Все эти методы (кроме forEach) не являются мутирующими, то есть не изменяют изначальный массив, а возвращают новый. forEach ничего не изменяет, и ничего не возвращает, а просто применяет какую-то функцию к каждому из элементов, но внутри метода forEach возможно изменять изначальный массив.

Метод forEach позволяет перебрать все элементы массива и применить к каждому из них переданную функцию. Он имеет такой синтаксис:

```javascript

array.forEach(function(element, index, array) {

    // тело функции

});

Пример:

let numbers = [1, 2, 3];

numbers.forEach(function(number) {
    console.log(number);
});

```

Метод map создает новый массив, в котором каждый элемент получается путём применения функции к элементу исходного массива. Он имеет такой синтаксис:

```javascript

let newArray = array.map(
    
    function(element, index, array) {
        
        // возвращаемое значение попадёт в новый массив
        
});

```

Пример:

```javascript

let numbers = [1, 2, 3];

let squared = numbers.map(function(number) {

    return number ** 2;

});

console.log(squared); // [1, 4, 9]

```

####

Метод filter используется для фильтрации массива на основе условия, возвращая только те элементы, которые удовлетворяют этому условию. Он имеет такой синтаксис:

```javascript

let filteredArray = array.filter(
    
    function(element, index, array) {
        
        // возвращаем true для элементов, которые должны попасть в новый массив
        
});

```

Пример:

```javascript

let numbers = [1, 2, 3, 4, 5];

let even = numbers.filter(function(number) {

return number % 2 === 0; // только чётные

});

console.log(even); // [2, 4]

```

Метод reduce используется для последовательной обработки каждого элемента массива с сохранением промежуточного результата. Итоговое значение возвращается после завершения работы метода. Он имеет такой синтаксис:

```javascript

let result = array.reduce(
    
    function(accumulator, element, index, array) {

        // тело функции

}, initialValue);

```

Пример:

```javascript

let numbers = [1, 2, 3, 4, 5];

let sum = numbers.reduce(function(accumulator, number) {

return accumulator + number;

}, 0);

console.log(sum); // 15

```

Метод reduce проходит по всему массиву и накапливает результат, который возвращается в конце работы.

**Управление циклом**

Прерывание цикла: «break»

Обычно цикл завершается при вычислении условия в false.

Но мы можем выйти из цикла в любой момент с помощью специальной директивы break.

Например, следующий код подсчитывает сумму вводимых чисел до тех пор, пока посетитель их вводит, а затем – выдаёт:

![](/web-course-site/loops/image2.png)

Директива break в строке (\*) полностью прекращает выполнение цикла и передаёт управление на строку за его телом, то есть на alert.

Вообще, сочетание «бесконечный цикл + break» – отличная штука для тех ситуаций, когда условие, по которому нужно прерваться, находится не в начале или конце цикла, а посередине или даже в нескольких местах его тела.

**Переход к следующей итерации: continue**

Директива continue – «облегчённая версия» break. При её выполнении цикл не прерывается, а переходит к следующей итерации (если условие все ещё равно true).

Её используют, если понятно, что на текущем повторе цикла делать больше нечего.

Например, цикл ниже использует continue, чтобы выводить только нечётные значения:

![](/web-course-site/loops/image3.png)

Для чётных значений i, директива continue прекращает выполнение тела цикла и передаёт управление на следующую итерацию for (со следующим числом). Таким образом alert вызывается только для нечётных значений.

**Бесконечные циклы**

Если условие цикла написано так, что оно никогда не станет ложным, цикл будет выполняться бесконечно.

![](/web-course-site/loops/image4.png)

Такой цикл занимает все выделенные ресурсы компьютера. В итоге вкладка браузера или целая программа зависает.

К бесконечному циклу могут привести две ошибки:

- неверное условие;
- условие написано верно, но в теле цикла никак не изменяются переменные, которые используются в условии.

Для того чтобы избежать бесконечного цикла:

1. Используйте правильные циклы(for - когда известно количество итераций, while - когда неизвестно.
2. Будьте аккуратно с добавлением/удалением элементов в массиве внутри цикла, это может сломать логику.
3. Проверяйте переменные счётчики
4. Используйте инструменты отладки(console.log)

Самые частые ошибки - это выход за границу массива и бесконечный цикл.

**Оптимизация кода с циклами.**

| **Название**     | **Что делает**                                             | **Производительность**                                      |
|------------------|------------------------------------------------------------|------------------------------------------------------------|
| **for**          | Полный контроль над индексами, прерывание (break), оптимизация для больших данных. | Высокая. Подходит для больших данных, позволяет оптимизировать итерации. |
| **while**        | Циклы с неизвестным количеством итераций или условием выхода внутри. | Зависит от условия. Может быть бесконечным, если условие не обновляется. |
| **do...while**   | Выполняется хотя бы один раз перед проверкой условия.     | Аналогичен while, но гарантирует минимум одну итерацию.     |
| **forEach**      | Простой перебор массива без изменения элементов (не поддерживает break). | Умеренная. Не создает новый массив, но нельзя прервать.    |
| **map**          | Создает новый массив, преобразуя элементы исходного.      | O(n). Создает новый массив, требует памяти.                |
| **filter**       | Создает новый массив с элементами, прошедшими проверку.   | O(n). Аналогично map, но с фильтрацией.                    |
| **reduce**       | Агрегирует данные (сумма, группировка) в единое значение. | O(n). Удобен для свертки, но требует аккумулятора.          |
| **some**         | Проверяет, удовлетворяет ли хотя бы один элемент условию. | O(n). Прерывается при нахождении элемента (лучше forEach для проверок). |
| **every**        | Проверяет, удовлетворяют ли все элементы условию.         | O(n). Аналогично some, но для всех элементов.              |
| **for...of**     | Перебор итерируемых объектов (массивы, строки) с возможностью break. | Высокая. Удобен для массивов, поддерживает прерывание.     |
| **find**         | Возвращает первый элемент, удовлетворяющий условию.       | O(n). Аналогичен some, но возвращает элемент вместо boolean.|
| **findIndex**    | Возвращает индекс первого элемента, удовлетворяющего условию. | O(n). Как find, но для индексов.                           |
| **includes**     | Проверяет наличие элемента в массиве.                     | O(n). Для примитивов, строгая проверка (как ===).          |
| **indexOf**      | Возвращает индекс первого вхождения элемента.             | O(n). Работает с примитивами, как includes, но возвращает индекс. |
| **sort**         | Сортирует элементы массива **на месте** (изменяет исходный массив). | O(n log n) в большинстве реализаций. Может быть нестабильным. |
| **splice**       | Изменяет массив, добавляя/удаляя элементы.                 | O(n). Изменяет исходный массив, может быть затратным из-за сдвига элементов. |
| **slice**        | Создает новый массив с подмассивом элементов.              | O(k), где k — длина подмассива. Не изменяет исходный массив.|
| **join**         | Объединяет элементы массива в строку.                      | O(n). Эффективен для преобразования массива в строку.      |
| **concat**       | Создает новый массив путем объединения существующих массивов. | O(n). Не изменяет исходные массивы, но требует памяти.     |
| **for...in**     | Перебор перечисляемых свойств объекта (включая индексы массива). | Не рекомендуется для массивов (перебирает все свойства, включая унаследованные). |

**Правило раннего выхода (early exit)** в контексте циклов в JavaScript — это подход, при котором ты выходишь из цикла как можно раньше, как только достигаешь нужного условия. Это позволяет избежать ненужных итераций, повысить производительность и сделать код более читаемым.

```javascript

let numbers = [1, 3, 5, 7, 9, 10, 15];

for (let i = 0; i < numbers.length; i++) {

    if (numbers[i] === 10) {
        
        console.log('Нашёл число 10!');
        
        break; // ранний выход из цикла

    }
}

```

**Как писать читабельный и эффективный код**

1. Осмысленные имена

Используйте понятные названия переменных, функций и классов. Например:

- Плохо: let b = 5;
- Хорошо: let numberOfUsers = 5;

Совет:

- Переменные — существительные (userAge).
- Функции — глаголы (calculateTotal()).
- Классы — существительные в единственном числе (User).

2. Принцип единственной ответственности (SRP)

Каждая функция должна решать одну задачу.

- Плохо: Функция, которая считает сумму и создает объект.
- Хорошо: Разделите на calculateTotal() и createCalculationRecord().

3. Минимум комментариев

Пишите код так, чтобы он был понятен без комментариев. Используйте их только для сложной логики.

- Хорошо: let userAge = 25;
- Плохо: let a;

4. Читаемый код

Используйте отступы и пробелы. Пример:

```javascript

if (isLoggedIn) {

    console.log("Welcome!");

} else {

    console.log("Please log in.");

}

```

Инструменты: Prettier, ESLint для автоматического форматирования.

5. Юнит-тесты

Тестируйте каждую функцию отдельно. Пример для класса Calculator:

```javascript

// Проверка сложения

console.assert(calculator.add(2, 3) === 5, 'Тест не пройден');

// Проверка деления на ноль

try {

calculator.divide(1, 0);

} catch (e) {

console.assert(e.message === "Cannot divide by zero");

}

```

6. Управление зависимостями

Не злоупотребляйте сторонними библиотеками. Пример с Nodemailer:

- Ограничивайте количество зависимостей: Подключайте только те библиотеки или модули, которые действительно необходимы для проекта.
- Обновляйте версии: Используйте актуальные версии библиотек, чтобы избежать уязвимостей в безопасности.
- Разделяйте логику: Создавайте основные функции самостоятельно, где это возможно. Это позволит вам удалить зависимость, если потребуется, не ломая остальной код.

7. Структура проекта

Организуйте код по папкам:

myProject/

├── src/

│ ├── components/ **UI-элементы**

│ ├── services/  **Бизнес-логика**

│ └── utils/ **Вспомогательные функции**

└── tests/ **Тесты**

8. Единый стиль кода

Соблюдайте одинаковые отступы, названия и структуру. Используйте автоматические форматеры.

9. Избегайте хардкода

Храните значения в константах или конфигурационных файлах:

Плохо: 
```javascript
if (users >= 100) {...}
```


Хорошо:
```javascript
const MAX_USERS = 100; if (users >= MAX_USERS) {...}
```

10. Короткие функции

Оптимальная длина — 20–30 строк. Пример:

Разбейте функцию updateCart() на addItemToCart(), calculateTotal(), logTransaction().

**Как избежать зависаний и долгих циклов в JavaScript**

- Разбивайте задачи на части

Используйте setTimeout, requestIdleCallback или асинхронные функции, чтобы делить тяжелые операции на мелкие блоки. Это не блокирует основной поток.

- Оптимизируйте алгоритмы

Избегайте вложенных циклов (O(n²)).

Кешируйте повторяющиеся значения (например, длину массива).

Используйте Set/Map для быстрого поиска.

- Не блокируйте поток синхронными операциями

Заменяйте синхронные запросы (HTTP, файлы) на асинхронные с async/await.

- Используйте методы с прерыванием

some(), every(), find() останавливают выполнение при достижении условия. Эффективнее, чем forEach/map.

- Контролируйте анимации

Для обновлений интерфейса применяйте requestAnimationFrame, чтобы синхронизировать циклы с частотой кадров.

- Профилируйте код

Используйте Chrome DevTools (Performance и Memory вкладки) для поиска узких мест и утечек памяти.
