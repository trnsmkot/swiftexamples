# Типы данных 
<br/>

1. Какие из строк кода будут успешно выполнены, не вызвав ошибок (сперва подумать, потом проверить):

```swift
Var myVar = 132
let myName = "Angel"
var myGrilfriend
var countOfMyDogs = 4.96
let name of city = "Cherepovets"
let country = Russia
var age: UInt8 = 5.5
```
<details><summary>Ответ</summary>
Нужно проверить в xcode
</details>
<br/>

2. Вам даны две переменные. Первая дробного типа хранит в себе расстояние в километрах. Вторая целочисленная хранит в себе время в секундах, за которое преодолели данное расстояние:

<details><summary>Ответ</summary>

```swift
// расстояние
var lengthOfPath = Double(52)
// время
var seconds = Int(360)
// вычисление скорости в метрах в минуту
var v = (lengthOfPath*1000) / (Double(seconds)/60)
```
</details>
<br/>

3. Даны два целочисленных трехзначных числа. Найти шестизначное, образованное слиянием данных чисел в одно. К примеру из чисел 111 и 222 должно получиться 111222:

<details><summary>Ответ</summary>

```swift
var a = 166
var b = 556
var c = Int("\(a)\(b)")
```
</details>
<br/>
