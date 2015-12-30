Quick reference for Swift syntax
----
I found it exceptionally necessary to have a syntax ref due to my bad memory,
so I compiled this in one big markdown file.  Most of the snippet here are copied from apple's swift documentation site.
Be aware that this is not a quick reference served as a quick reminder
for those who already had programming experience on swift or other languages.

For more thorough information on Swift language itself I recommend going to apple's swift documentation site.
If you are looking for quick guides with more detailed descriptions, there are a couple of cheatsheet repositories out there that did a great job and I myself also benefit a lot from them.

## Variable and Constant

```
var a = "Hello world"  // Variable
let b = 2              // Constant
```

## Operators

### Arithmetic Operators

```
var a = 6 + 6
var b = 5 - 2
var c = a * b
var d = 8 / 8
var e = 9 % 3

//Increment and decrement
i++
i--

//Comparison
a == b  //equal
a != b
a === b //identical
a !== b //not identical
a > b
a < b
a >= b
a <= b

// ternary
a ? b : c
```


### Logical Operators
```
!a
a && b //Logical and
a || b //Logical or
```

### Bitwise Operators
```
~   // bitwise not
&   // bitwise and
|   // bitwise or
^   // bitwise xor
<<  // left shift
>>  // right shift
```

### Range Operators

```
//Closed range
a...b

//Half-Open range
a ..< b
```

### Others
```
//Nil coalescing
a ?? b
```

## Collection types
### Array
```
// Declaration
var array1 = [Int]()
var array2 : [Int] = []
var array3 : Array<String> = ["Apple", "Strawberry"]

// Addition
var array4 = array1 + array2
array3.append("Grape")

// Removal
array3.removeAtIndex(1)

// Retrieval
let item = array3[0]

// Update
array3[0] = "Pear"

// Iteration
for item in array3 {
  print(item)
}

for (index, value) in array3 {
  print("\(index) is \(value) ")
}
```

### Dictionary
```
// Declaration
var dict1 = Dictionary<Int, String>()
var dict2 = [String:String]()
var dict3 = ["key1": "value1", "key2": "value2"]

// Insertion
dict3["key3"] = "value3"

// Modification
dict3["key1"] = "new value 1"

// Removal
dict3.removeValueForKey("key2")

// Iteration
for (key, value) in dict3 {
  print(key, value)
}

for key in dict3.keys.sort() {
  if let value = dict3[key] {
        print(value)
  }
}
```

### Set
```
// Declaration
var set1 = Set<String>()
var set2 : Set<String> = ["String1", String2]
set1 = [] // empty set

// Insertion
set2.insert("String3")

// Removal
set2.remoe("String1")

// Retrieval
var item = set2[set2.startIndex.advancedBy(1)]

// Iteration
for item in set2 {
  print(item)
}
```


## Control structure

```
// If-else
if a < b {
  //Do something
} else if a == b {
  //Do something
} else {
  //Do something
}

// For loop
for item in array {
  //Do something
}

for index in 1...5 {
  //Do something
}

for var i = 0; i < 5; i++ {
  //Do something
}

// While loop
while a == b {
  //Do something
}

repeat {
  //Do something
} while a == b



// Switch case, Swift has no implicit fall through of case values so no need to break
switch letter {
  case "A", "B":
    //Do something
  case "C":
    //Do something
  default:
    //Do something
}

// Guard
func test(name: String){
  guard let name = name else {
    return
  }

  // Do something
}

```

## Classes
```
// Declaration
class AClass {
  var a = 0
  var b : String?
  let c = "string"

}

struct AStructure {
  var width = 0
  var height = 0
  var depth : Int?
  // structure definition goes here
}

// Instantiation
var a = AClass()
var b = AStructure()
// All structure have auto-generated memberwise initializer
var b2 = AStructure(width: 1, height: 2, depth: 3)
```

## Enumerations
```
// Declaration
enum LogType {
  case Info
  case Warning
  case Error
  case Debug
}

enum OperationMode {
  case Create, Read, Update, Delete
}

enum OperationMode2 : String {
  case Create, Read, Update, Delete
}

// Use
var operation = OperationMode.Read
let mode = OperationMode2.Create.rawValue // mode is "Create"
```

## Protocols
```
// Declaration
protocol SomeProtocol {
}

protocol SomeProtocol {
    var mustBeSettable: Int { get set }
    var doesNotNeedToBeSettable: Int { get }
}

```

## Functions
```

// Declaration
func sayHello(personName:String) -> String {
  return "Hello \(personName)!"
}

func sayHello2(firstName:String, lastName:String) -> String {
  return "Hello \(firstName) \(lastName)!"
}

func sayHelloWorld() {
  print("Hello World")
}

func minMax(array:[Int]) -> (min:Int, max:Int)? {
  var currentMin = array[0]
  var currentMax = array[array.count - 1]
  //Do something ...
  return (currentMin, currentMax)
}

print(sayHello("Foobar")) // print "Hello Foobar!"
print(sayHello2("Chris", lastName:"Jeter")) // print "Hello Chris Jeter!"
sayHelloWorld() // print "Hello World"

// External name and internal name
func someFunction(firstParam: Int, secondParam: Int) {
}
someFunction(1, secondParam: 2)               

func someFunction(externalParam localParam: Int) {
    print(localParam)
}
someFunction(externalParam:3) // print 3

func someFunction(firstParameterName: Int, _ secondParameterName: Int) {
}
someFunction(1, 2)

func someFunction(firstParam : Int = 6) {
  print(firstParam)
}
someFunction() // print 6


func arithmeticMean(numbers: Double...) -> Double {
    var total: Double = 0
    for number in numbers {
        total += number
    }
    return total / Double(numbers.count)
}

func swapTwoInts(inout a: Int, inout _ b: Int) {
    let temporaryA = a
    a = b
    b = temporaryA
}
var someInt = 2
var anotherInt = 4
swapTwoInts(&someInt, &anotherInt)

func takeTwoInt(a:Int, _ b:Int)->Int {}
var mathFunction : (Int, Int) -> Int = takeTwoInt

func chooseStepFunction(backwards: Bool) -> (Int) -> Int {
    // Do something...
}


```

## Closure

## Error handling
```
enum VendingMachineError: ErrorType {
    case InvalidSelection
    case InsufficientFunds(coinsNeeded: Int)
    case OutOfStock
}
throw VendingMachineError.InvalidSelection

func functionThrowError() throws -> String {
  throw VendingMachineError.OutOfStock
}

// Do catch
var vendingMachine = VendingMachine()
vendingMachine.coinsDeposited = 8
do {
    try buyFavoriteSnack("Alice", vendingMachine: vendingMachine)
} catch VendingMachineError.InvalidSelection {
    print("Invalid Selection.")
} catch VendingMachineError.OutOfStock {
    print("Out of Stock.")
} catch VendingMachineError.InsufficientFunds(let coinsNeeded) {
    print("Insufficient funds. Please insert an additional \(coinsNeeded) coins.")
}


let x = try? someThrowingFunction()
let photo = try! loadImage("./Resources/John Appleseed.jpg")

```

## Type Casting

is  //Check type
as? //Downcast
as! //Downcast
as  //Match is switch case


## Access Control
public
internal
private

```
public class SomePublicClass {}
internal class SomeInternalClass {}
private class SomePrivateClass {}

public var somePublicVariable = 0
internal let someInternalConstant = 0
private func somePrivateFunction() {}
```

## Generics


## Extensions
```
extension SomeType {
}

extension SomeType: SomeProtocol, AnotherProtocol {
}

extension Double {
    var km: Double { return self * 1_000.0 }
    var m: Double { return self }
    var cm: Double { return self / 100.0 }
    var mm: Double { return self / 1_000.0 }
    var ft: Double { return self / 3.28084 }
}
let oneInch = 25.4.mm

/** Add initializer in extension **/
extension Rect {
    init(center: Point, size: Size) {
        let originX = center.x - (size.width / 2)
        let originY = center.y - (size.height / 2)
        self.init(origin: Point(x: originX, y: originY), size: size)
    }
}

/** Add new method in extension **/
extension Int {
    func repetitions(task: () -> Void) {
        for _ in 0..<self {
            task()
        }
    }
}

/** Mutating **/
extension Int {
    mutating func square() {
        self = self * self
    }
}

```

## Optionals
```swift

```
