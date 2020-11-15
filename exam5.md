# Функции (func)
<br/>

1. Будет ли корректно выполняться данный код? Если нет, то укажите почему и по-возможности исправьте ошибки

```swift
func mult(_ a: Double, _ b: Double) -> Double {
 a * b
}
```
<details><summary>Ответ</summary>
Функция написана корректно. Оператор return не обязательно должен быть в коде, когда тело функции состоит из одного выражения.
</details>
<br/>

2. Разработайте функцию, которая принимает на вход значение типа Bool, преобразует его в строку и возвращает. То есть передав true типа Bool должно вернуться "true" типа String, то же самое и для false.

<details><summary>Ответ</summary>

```swift
func booleanToString(_ b: Bool) -> String {
   return String(b)
}

Возможно вы решили данную задачу с помощью оператора ветвления. Ваш вариант так же будет верным.
```
</details>
<br/>

3. Напишите функцию, которая принимает на вход массив с элементами типа Int, а возвращает целое число – сумму всех положительных элементов переданного массива.<br/>
К примеру для массива [1,-2,3,4,-5] должно быть возвращено 1+3+4 = 8

<details><summary>Ответ</summary>

```swift
func sumOfPositives(_ a: [Int] ) -> Int{
    var result = 0
    for i in a {
        // тернарная форма оператора ветвления позволяет сократить код
        // вы оожете использовать сокращенный или стандартный синтаксис
        result += i>0 ? i : 0
    }
    return result
}
//внутри цикла for применяется терная
sumOfPositives([1,-2,3,4,-5]) //8
```
</details>
<br/>

4. Напишите функцию, которая принимает на вход массив типа [Int] и, в случае, если количество элементов > 0, то возвращает целое число – произведение всех элементов переданной коллекции. Если количество элементов = 0, то возвращается 0.<br/>
Пример: [1,2,3,4] -> 1 * 2 * 3 * 4 = 24

<details><summary>Ответ</summary>

```swift
func grow(_ a: [Int]) -> Int {
    var result = 0
    if a.count > 0 {
        result = 1
        for i in a {
            result *= i
        }
    }
    return result
}
grow([1,2,3,4]) //24
grow([]) //0
```
</details>
<br/>

5. Используя перегрузку (overloading) создайте две одноименные функции, которые могут принимать два однотипных параметра (Int или Double) и возвращают их произведение<br/>
Пример:<br/>
(4, 5) -> 4 * 5 = 20<br/>
(4.1, 5.2) -> 4.1 * 5.2 = 21.32

<details><summary>Ответ</summary>

```swift
func multi(_ a: Int, _ b: Int) -> Int {
    return a*b
}
func multi(_ a: Double, _ b: Double) -> Double {
    return a*b
}
multi(4.1, 5.2) //21.32
multi(4, 5) //20
```
</details>
<br/>

6. Напишите функцию, которая принимает на вход целое число и возвращает обратное ему целое число<br/>
Пример: -12 -> 12, 32 -> -32

<details><summary>Ответ</summary>

```swift
func opposite(_ a: Int) -> Int {
    return -a
}
opposite(-12) //12
opposite(32) //-32
```
</details>
<br/>

7. Напишите функцию, которая производит подсчет стоимости аренды квартиры с учетом следующих условий:<br/>
1- Один день аренды стоит 850 рублей<br/>
2- При аренде от 3 дней вы получаете скидку в размере 550 рублей от общей суммы<br/>
3- При аренде от 7 дней вы получаете скидку в размере 1620 рублей от общей суммы<br/>
Функция должна принимать на вход количество дней, а возвращать итоговую сумму.<br/>
Пример: (5) -> 3700, (9) -> 6030

<details><summary>Ответ</summary>

```swift
func rent(_ days: Int) -> Int {
    let dayPrice = 850;
    var result = dayPrice * days
    if days >= 7 {
        result -= 1620
    }else if days >= 3 {
        result -= 550
    }
    return result
}
rent(5) // 3700
rent(9) // 6030
```
</details>
<br/>

8. Напишите функцию, которая принимает на вход массив типа [Int] и значение Int, проверяет содержится ли целочисленный элемент в массиве и возвращает true или false в зависимости от результата проверки<br/>
Покажите не менее двух способов решения данной задачи<br/>
Пример: ([1,2,3], 4) -> false, ([2,3,4], 3) -> true

<details><summary>Ответ</summary>

```swift
//Вы можете реализовать данную задачу с помощью перебора или используя встроенный метод contains(_:). Ниже показаны оба варианты решения
//Вариант 1. Перебор
func check1(_ arr: [Int], _ el: Int) -> Bool {
    for i in arr {
        if i == el {
            return true
        }
    }
    return false
}
check1([1,2,3], 4) //false
check1([2,3,4], 3) //true
//Вариант 2. Метод contains(_:)
func check2(_ arr: [Int], _ el: Int) -> Bool {
    return arr.contains(el)
}
check2([1,2,3], 4) //false
check2([2,3,4], 3) //true
```
</details>
<br/>

9. Напишите функцию, которая повторяет заданную строку N раз.<br/>
Функция принимает на вход значение типа String (строку для повторений) и значение типа Int (количество повторений) и возвращает полученный результат.<br/>
Пример: ("Swift", 2) -> "SwiftSwift", ("Xcode", 0) -> ""

<details><summary>Ответ</summary>

```swift
//Вариант 1
func repeatStr1(_ str: String, _ n: Int) -> String {
    return String(repeating: str, count: n)
}
repeatStr1("Swift", 2) //
repeatStr1("Xcode", 0) //
//Вариант 2
func repeatStr2(_ str: String, _ n: Int) -> String {
    var result = ""
    for _ in 0..<n {
        result += str
        //так же допустим вариант с
        //result.append(str)
    }
    return result
}
repeatStr2("Swift", 2) // "Swift"
repeatStr2("Xcode", 0) // ""
```
</details>
<br/>

10. Напишите функцию, которая принимает параметр типа String, а возвращает true (типа Bool) если в строке есть только уникальные символы, и false, если в ней есть хотя бы один повторяющийся символ.

<details><summary>Ответ</summary>

```swift
//Решение 1
func checkUniqueSymbols1(text: String) -> Bool {
    // массив, который будет хранить просмотренные символы
    var usedSymbols = [Character]()
    //перебор всех символов
    for symbol in text {
        if usedSymbols.contains(symbol) {
            return false
        }
        usedSymbols.append(symbol)
    }
    return true
}

//Решение 2
//Преобразовать строку в множество (набор, сет)
//После чего сравнить количество символов с исходной строкой
func checkUniqueSymbols2(text: String) -> Bool {
    return Set(text).count == text.count
}
// уникальные символы (буквы S имею различный регистр)
checkUniqueSymbols1(text: "Unique Symbols") //true
checkUniqueSymbols2(text: "Unique Symbols") //true
// неуникальные символы (повторение буквы "о")
checkUniqueSymbols1(text: "Not Unique Symbols") //false
checkUniqueSymbols2(text: "Not Unique Symbols") //false
```
</details>
<br/>

11. Напишите функцию, которая определяет, состоят ли две переданные в нее строки из одних и тех же символов.<br/>
Пример: checkSameSymbols(in: "abc", and: "bca") // true, checkSameSymbols(in: "abc", and: "bcaa") // false

<details><summary>Ответ</summary>

```swift
//Будем брать каждый символ из первой строки и удалять его первое вхождение из второй. В конце проверим, остались ли символы в
func checkSameSymbols(in stringOne: String, and stringTwo: String) -> Bool {
    var mutableStringTwo = stringTwo
    for symbol in stringOne {
        if let firstIndex = mutableStringTwo.firstIndex(of: symbol) {
            mutableStringTwo.remove(at: firstIndex)
        } else {
            return false
        }
    }
    return mutableStringTwo.count == 0
}
checkSameSymbols(in: "abc", and: "bca")
```
</details>
<br/>

12. Реализуйте функцию pow(Int,Int), которая принимает два целочисленных элемента. Первый указывает на степень второго числа. Результат функции – второй аргумент функции, возведенный в степень (первый аргумент функции).<br/>
Предполагается, что аргументы могут быть только целыми положительными числами.

<details><summary>Ответ</summary>

```swift
func pow(_ power: Int, _ b: Int) -> Int {
    guard power > 0 else {
        return 1
    }
    var result = 1
    for _ in 1...power {
        result *= b
    }
    return result
}
pow(2, 2) //4
pow(0, 5) //1
pow(8, 4) //65536
```
</details>
<br/>
