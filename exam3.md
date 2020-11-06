# Операторы управления
<br/>

1. Напишите код, который будет выводить на консоль персонализированное приветствие пользователю в зависимости от его имени.
Пусть в константе name хранится имя пользователя. Используя операторы управления (условия if и ветвления switch) реализуйте различный вывод на консоль в зависимости от значения в константе name<br/>
Покажите варианты решения с использованием switch и if. Определите вывод на консоль для трех произвольных имен, а так же в блоке “во всех остальных случаях” (default и else).

<details><summary>Ответ</summary>

```swift
//Вариант 1
let name = "Vasiliy"
switch name {
case "Vasiliy":
    print("Привет, Василий")
    break;
case "Alex":
    print("Привет, Алексей")
    break;
case "Helga":
    print("Привет, Ольга")
    break;
default:
    print("Привет, пользователь")
    break;
}
//Вариант 2
if name == "Vasiliy"{
    print("Привет, Василий")
}else if name == "Alex" {
    print("Привет, Алексей")
}else if name == "Helga"{
    print("Привет, Ольга")
}else{
    print("Привет, пользователь")
}
```
</details>
<br/>

2. У вас есть логическая переменная open, которая может принять одно из двух доступных значений (true или false)<br/>
var open = true<br/>

Вам необходимо создать новую переменную типа String и инициализировать ей строковое значение:<br/>
– если open равно true, то инициализировать “открыто”<br/>
– если open равно false, то инициализировать “закрыто”

<details><summary>Ответ</summary>

```swift
//Наиболее очевидным вариантом станет использование оператора условия if, а точнее его тернарной формы
var message = open ? "открыто" : "закрыто"
//Конечно же вы можете реализовать данную задачу и через стандартную форму оператора if
//в этом случае переменную нужно создать вне оператора if, т.к. в ином случае она будет локальной и недоступной вне его тела
var message2 = ""
if open {
    message2 = "открыто"
}else{
    message2 = "закрыто"
}
```
</details>
<br/>

3. Вам даны три переменные var1, var2 и var3 целочисленного типа Int<br>
Составьте программу, в конце которой в константе result будет находиться наибольшее из трех целочисленных значений.

<details><summary>Ответ</summary>

```swift
var var1 = 2
var var2 = 23
var var3 = 16
// Способ 1
//временная переменная
var tmp = 0
//двумя условиями проверим, какое из чисел самое больше
//сперва найдем наиболее из первых двух
//потом сравним его с третьим
tmp = var1 > var2 ? var1 : var2
tmp = tmp > var3 ? tmp : var3
let result = tmp
// Способ 2
// использовать полную форму оператора условия
var tmp2 = 0
// мы можем задать самые разные варианты условий
// или даже использовать вложенные условия
if var1 > var2 && var1 > var3 {
    tmp2 = var1
}else if var2 > var1 && var2 > var3 {
    tmp2 = var2
}else{
    tmp2 = var3
}
let result2 = tmp2
// Способ 3 (от Vlados)
var tmp3 = [var1, var2, var3]
let result3 = tmp3.max()
```
</details>
<br/>

4. Вы имеете три переменные-кортежа, содержащие координаты точек<br>
Напишите программу, которая определяет, может ли существовать треугольник с заданными координатами вершин.<br>
(Треугольник существует только тогда, когда сумма длин любых двух его сторон больше длины третьей.)

<details><summary>Ответ</summary>

```swift
// Способ 1 (от Vlados и disconnect)
// Координаты
var (a, b, c): ((Double,Double), (Double,Double), (Double, Double)) = ((1, 1), (1, 3), (3, 1))
// Вычислим длины сторон
let aB = sqrt ((pow(b.0-a.0, 2)) + (pow(b.1-a.1, 2)))
let aC = sqrt ((pow(c.0-a.0, 2)) + (pow(c.1-a.1, 2)))
let bC = sqrt ((pow(c.0-b.0, 2)) + (pow(c.1-b.1, 2)))
// Сравниваем грани
var faceBc = (aB + aC) > bC
var faceAc = (aB + bC) > aC
var faceAb = (aC + bC) > aB
// Треугольник существует только тогда, когда сумма длин любых двух его сторон больше длины третьей
if faceBc && faceAc && faceAb {
    print("True triangle")
} else {
    print("False triangle")
}
// Способ 2
//переменные с координатами
var point1 = (-100,1)
var point2 = (10,2)
var point3 = (6,12)
//определяем длину отрезков
var line1 = sqrt(
    pow(Double(point2.0 - point1.0), 2) +
    pow(Double(point2.1 - point1.1), 2)
)
var line2 = sqrt(
    pow(Double(point2.0 - point3.0), 2) +
    pow(Double(point2.1 - point3.1), 2)
)
var line3 = sqrt(
    pow(Double(point1.0 - point3.0), 2) +
    pow(Double(point1.1 - point3.1), 2)
)
if line1+line2>line3 {
    print("Такой треугольник существует")
}else{
    print("Такой треугольник не существует")
}
```
</details>
<br/>

5. Переменная lang может принимать 2 значения: 'ru', 'en'. Если она имеет значение 'ru', то в переменную days запишите массив дней недели на русском языке, а если имеет значение 'en' – то на английском<br>
Покажите решение задачи через конструкцию switch-case

<details><summary>Ответ</summary>

```swift
var lang = "ru"
var days: [String] = []
switch lang {
   case "ru":
       days = ["пн", "вт", "ср", "чт", "пт", "сб", "вс"];
   case "en":
       days = ["mn", "ts", "wd", "th", "fr", "st", "sn"];
   default:
       break;
}
days // ["пн", "вт", "ср", "чт", "пт", "сб", "вс"]
```
</details>
<br/>

6. Основано на предыдущем задании<br/>
У вас появилась дополнительная переменная chars, которая может принять два значения "up" и "down"<br/>
Доработайте конструкцию switch-case таким образом, чтобы в зависимости от значения chars массив заполнялся большими или маленькими символами

<details><summary>Ответ</summary>

```swift
var lang = "ru"
var chars = "up"
var days: [String] = []
switch lang {
   case "ru" where chars == "down":
     days = ["пн", "вт", "ср", "чт", "пт", "сб", "вс"];
     break;
   case "ru" where chars == "up":
     days = ["ПН", "ВТ", "СР", "ЧТ", "ПТ", "СБ", "ВС"];
     break;
   case "en" where chars == "down":
     days = ["mn", "ts", "wd", "th", "fr", "st", "sn"];
     break;
   case "en" where chars == "up":
     days = ["MN", "TS", "WD", "TH", "FR", "ST", "SN"];
     break;
   default:
     break;
}
days // ["ПН", "ВТ", "СР", "ЧТ", "ПТ", "СБ", "ВС"]
```
</details>
<br/>

7. 
- Определите псевдоним Operation типу кортежа, содержащему три элемента со следующими именами: operandOne, operandTwo, operation.
Первые два – это числа с плавающей точкой. Они будут содержать операнды для выполнения операции.
Третий элемент – строковое значение типа Character. Оно будет содержать указатель на проводимую операцию. Всего может быть четыре вида операций: +, -, *, /.<br/>
- Создайте константу типа Operation и инициализируйте ей произвольное значение, к примеру (3.1, 33, “+”)<br/>
- Используя конструкцию switch-case вычислите значение операции, указанной в элементе для операндов operandOne и operandTwo. Оператор switch должен корректно отрабатывать любую из четырех операций.<br/>
- Проверьте правильность работы конструкции по для следующих операций:<br/>
– (3.1, 33, “+”) -><br/>
– (24.9, 22.32, “*”) -><br/>
– (11.3, 5, “/”) -><br/>
– (5, 2.5, “-“) -> 2.5<br/>

<details><summary>Ответ</summary>

```swift
//1
typealias Operation = (operandOne: Double, operandTwo: Double, operation: Character)
//2
let oper: Operation = (operandOne: 3.1, operandTwo: 33, operation: "+")
//3
var resultOper: Double = 0
switch oper {
   case (let a, let b, "+"):
     resultOper = a + b
   case (let a, let b, "-"):
     resultOper = a - b
   case (let a, let b, "/"):
     resultOper = a / b
   case (let a, let b, "*"):
     resultOper = a * b
   default:
     break
}
```
</details>
<br/>
