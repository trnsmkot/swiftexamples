# Опциональные типы данных
<br/>

1. Какое значение у каждой из приведенных переменных? В чем отличие переменных easy и medium из предыдущего задания?

```swift
var easy: String?
var medium: String!
var hard: String
```
<details><summary>Ответ</summary>
Переменные easy и medium не имеют значения (nil).<br/>
Выражение с переменной hard вызовет ошибку, т.к. оно не опционального типа и не имеет значения.<br/>
В переменной medium используется косвенное извлечение значения, т.е. в момент обращения у нему оно не должно иметь nil в качестве значения, т.к. будет автоматически извлечено.
</details>
<br/>

2. Будет ли корректно выполнен следующий программный код? Если в нем присутствуют ошибки, то по-возможности исправьте их.

```swift
easy = "1"
medium = "contra"
hard = "play game"
easy = medium
hard = medium
easy = hard!
easy = hard
var gameTuple = (easy, Optional(hard))
var gameText: String = gameTuple.0
```
<details><summary>Ответ</summary>
Строка 6 вызовет ошибку, т.к. происходит попытка извлечения неопционального значения<br/>
Строка 8 вызовет ошибку, т.к. неопционалу присваивается опциональное значения без принудительного извлечения
</details>
<br/>

3. Покажите не менее трех способов (с помощью разных синтаксических конструкций) создания переменной типа String?

<details><summary>Ответ</summary>

```swift
var one: String? = "Способ 1"
var two = Optional("Способ 2")
var three = String(3.14)
```
</details>
<br/>

4. Корректно ли будет выполнен следующий код?

```swift
var point = nil
```
<details><summary>Ответ</summary>
Данный код вызовет ошибку, так как при присвоении nil параметру без конкретного указания опционального типа Swift не может определить его автоматически (что это: String?, Int?, Bool? или что-то другое?).
</details>
<br/>

5. 1- Создайте псевдоним типа String с именем Text<br/>
2- Объявите три константы типа Text. Значения дух констант должны состоять только из цифр, а третьей – из букв и цифр<br/>
3- С помощью оператора условия определите те константы, которые состоят только из цифр и выведите из на консоль

```swift
Для преобразования строки в число (для проверки того, из чего она состоит) можно использовать функцию Int(_:)
```
<details><summary>Ответ</summary>

```swift
//1
typealias Text = String
//2
let let1: Text = "22"
let let2: Text = "97"
let let3: Text = "swift5"
//3
if let unwrap1 = Int(let1) {
    print(unwrap1)
}
if let unwrap2 = Int(let2) {
    print(unwrap2)
}
if let unwrap3 = Int(let3) {
    print(unwrap3)
}
```
</details>
<br/>

6. В задании используются результаты предыдущего задания<br/>
1- Создайте псевдоним типа (numberOne: Text?, numberTwo: Text?) с именем TupleType.<br/>
2- Создайте три переменные типа TupleType, содержащие следующие значения: ("190", "67"), ("100", nil), ("-65", "70").<br/>
3- С помощью конструкции switch-case определите, какие из кортежей не содержат nil в своем составе и выведите значения их элементов на консоль

<details><summary>Ответ</summary>

```swift
//1
typealias TupleType = (numberOne: Text?, numberTwo: Text?)
//2
var var1: TupleType = ("190", "67")
var var2: TupleType = ("100", nil)
var var3: TupleType = ("-65", "70")
//3
switch var1 {
case (let a, let b) where a != nil && b != nil:
    print("\(a!) \(b!)")
default:
    break;
}
switch var2 {
case (let a, let b) where a != nil && b != nil:
    print("\(a!) \(b!)")
default:
    break;
}
switch var3 {
case (let a, let b) where a != nil && b != nil:
    print("\(a!) \(b!)")
default:
    break;
}
```
</details>
<br/>

7. 1- Создайте псевдоним Coordinates для типа кортежа (alpha: Character?, num: Int?). Данный тип будет описывать координаты шахматной фигуры на игровом поле. Если вместо элементов кортежа стоит nil, значит фигура не находится на игровом поле.<br/>
2- Создайте псевдоним Chessman для типа словаря [String:Coordinates?]. Данный тип описывает шахматную фигуру на игровом поле. В ключе словаря должно хранится имя фигуры, например "White King", а в значении – кортеж, указывающий на координаты фигуры на игровом поле.<br/>
3- Создайте переменный словарь figures типа Chessman и добавьте в него три произвольные фигуры, одна из которых не должна иметь координат.<br/>
4- Создайте цикл, которая обходит всех элементы словаря (все фигуры), и проверяет, убита ли очередная фигура (элемент словаря figures), далее выводит на консоль информацию либо о координатах фигуры, либо о ее отсутствии на игровом поле.

<details><summary>Ответ</summary>

```swift
//1
typealias Coordinates = (alpha: Character?, num: Int?)
//2
typealias Chessman = [String:Coordinates]
//3
var figures:Chessman = [:]
figures["White King"] = (alpha: "B", num: 1)
figures["White Queen"] = (alpha: nil, num: nil)
figures["Black King"] = (alpha: "F", num: 6)
//4
for oneFigure in figures {
    if oneFigure.value.0 != nil && oneFigure.value.1 != nil {
        print("Фигура на поле")
    }else{
        print("Фигура не на поле")
    }
}
```
</details>
<br/>
