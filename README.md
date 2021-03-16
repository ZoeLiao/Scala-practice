# Scala-practice

- [Doc](https://www.scala-lang.org/)

## Practice
- [Hello World](https://github.com/ZoeLiao/Scala-practice/tree/main/hellow-world)

## The Scala REPL 
The Scala REPL (“Read-Evaluate-Print-Loop”) is a command-line interpreter that you use as a “playground” area to test your Scala code.

## Type
- 2 types of variables:
    - val: immutable variable, like `final` in Java, it should be preferred. 
    - var: mutable variabl, and should only be used when there is a specific reason to use it.
- Declaring variable types:
```scala
val x = 1
val s = "a string"
val p = new Person("Amy")
```

## Control Structures
- if/else
    - 1.
        ```scala
        if (a) {
          doA()
        } else if (b){
          doB()
        } else {
          doC()
        }
        ```
    - 2.
        ```scala
        val x = if (a < b) a else b 
        ```
- match
    - 1. 
        ```scala
        var result = i match {
            case 1 => "one"
            case 2 => "two"
            case _ => "not 1 or 2"
        }
        ```
    - 2. 
        ```scala
        def getClassAsString(x: Any):String = x match {
            case s: String => s + " is a String"
            case i: Int => "Int"
            case f:Float => "Float"
            case l:List[_] => "List"
            case p:Person => "Person"
            case _ => "Unknown"
        }
        ```
- try/catch
    ```scala
    try {
        writeToFile(text)
    } catch {
        case fnfe: FileNotFoundException => println(fnfe)
        case ioe: IOException => println(ioe)
    }
    ```
- for loops and expressions
    - 1.
        ```scala
        for (arg <- args) println(arg)
        for (i <- 0 to 5) println(i)
        for (i <- 0 to 10 by 2) println(i)
        ```
    - 2. with `yield`
        ```scala
        val x = for (i <- i to 5) yield i * 2
        ```
    - 3.
        ```scala
        val fruit = List("apple", "banana", "lime", "orange")
        
        val fruitLengths = for {
            f <- fruits
            if f.length > 4
        } yield f.length
        ```
- while and do/while
    ```scala
    // while loop
    while(condition) {
        statement(a)
        statement(b)
    }

    // do-while
    dp {
        statement(a)
        statement(b)
    }
    while(condition)
    ```

## Classes
- No get, set method 
- Support to set default
- No need to assign return type 
- Example:
    ```scala
    class Pizza (
      var crustSize: CrustSize,
      var crustType: CrustType,
      var toppings: ArrayBuffer[Topping],
    ) {
      def addTopping(t: Topping): Unit = toppings += t
      def removeTopping(t: Topping): Unit = toppings -= t
      def removeAllTopping(t: Topping): Unit = toppings.clear()
    }
    ```

## Traits
- Let you break your code down into small, modular units 
- 單一繼承
- 不能有類的參數
- Example:
    ```scala
    trait Speaker {
      def speak(): String
    }

    trait TrailWagger {
      def startTail(): Unit = println("tail is wagging")
      def stopTail(): Unit = println("tail is stopped")
    }

    trait Runner {
      def startRunning(): Unit = println("I'm running")
      def stopRunning(): Unit = println("Stopped running")
    }

    // 繼承
    class Dog(name: String) extends Speaker with TailWagger with Runner {
      def speak(): String = "Woof!"
    }

    // 繼承多個 Trait
    class Cat extends Speaker with TailWagger with Runner {
      def speak(): String = "Meow"
      override def startRunning(): Unit = println("Yeah ... I don’t run")
      override def stopRunning(): Unit = println("No need to stop")
    }
    ```
