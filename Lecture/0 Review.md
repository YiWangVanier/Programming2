# Review


## 1. Data type

Generally, Java data types can be separated into two groups:

1. **Primitive data type**: pre-defined and basic data type, the size of which is fixed.

    |Category|Type|Size|Comments|
    | - | - | - | - |
    |integral|byte<br />short<br />char<br />int<br />long|1<br />2<br />2<br />4<br />8|cannot be negative|
    |floating|float<br />double|4<br />8||
    |boolean|||true or false|

2. **Class**: user-defined, the size of which is not fixed.

## 2. Method

### 2.1 Overload method

**Overload methods** mean multiple methods in the same class have the same method name, but different parameter lists. Constructors are usually overloaded.

```java
// Example of overload methods
public static double max(double num1, double num2)
public static int max(int num1, int num2)
public static double max(double num1, double num2, double num3)
```

### 2.2 Pre-defined methods in classes

Some pre-defined classes:

#### 2.2.1 Math class

|Method/Value|Usage|Example|
|--|--|--|
|`Math.min(num1, num2)`| find the smaller number of two| `Math.min(1, 2)` returns 1 |
|`Math.max(num1, num2)`| find the larger number of two| `Math.max(1, 2)` returns 2 |
|`Math.sqrt(num)`| calculate the square root of a number | `Math.sqrt(4)` returns 2.0 |
|`Math.pow(num)`| calculate the power of a number| `Math.pow(3, 2)` returns 9 |
|`Math.round(num)`| round a number up or down| `Math.round(3.14)` returns 3<br />`Math.round(3.8)` returns 4 |
|`Math.ceil(num)`| round a number up | `Math.ceil(3.14)` returns 4 |
|`Math.floor(num)`| round a number down| `Math.floor(3.8)` returns 3 |
|`Math.random()`| generate a random number between `[0, 1)` | |
|`Math.PI`| value of π | |

#### 2.2.2 String class

The index of a string starts at `0`.

| Method/Value/Operator                                        | Usage                                                        | Example                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `str.length()`                                               | find the length of a string                                  | `"hello".length()` returns 5                                 |
| `str.charAt(idx)`                                            | find the character with a specific index in a string         | `"hello".charAt(1)` returns 'e'                              |
| `str.indexOf(chara)`                                         | find the index of a character in a string (first time appears), returns -1 if the character does not exist | `"hello".indexOf('l')` returns 2                             |
| `str.lastIndexOf(chara)`                                     | find the index of a character in a string (last time appears) | `"hello".lastIndexOf('l')` returns 3                         |
| `str.contains(str2)`                                         | check if a string contains a specific substring              | `"hello".contains("el")` returns true                        |
| `str.substring(startIdx, endIdx)`<br />`str.substring(startIdx)` | extract a substring from a string, with range `[startIdx, endIdx)`, or [startIdx, end of the string] | `"hello".substring(2, 4)` returns "ll"<br />`"hello".substring(1)` returns "ello" |
| `str.toUpperCase()`                                          | bring a string to uppercase                                  | `"hello!".toUpperCase()` returns "HELLO!"                    |
| `str.toLowerCase()`                                          | bring a string to lowercase                                  | `"HELLO!".toLowerCase()` returns "hello!"                    |
| `str.equals(str2)`                                           | compare two strings to check if they are the same            | `"hello".equals("hello")` returns true                       |
| `Stirng.format()`                                            | generate a string. See point 4.1 for further info                                            | `String.format("%s: %d", "Age", 18)` returns "Age: 18"       |
| `str1 + str2`                                                | join two strings as one                                      | `"hi " + "there"` returns "hi there"                         |

#### 2.2.3 Random

```java
// Example of using Random class
Random rand = new Random();
int num = rand.nextInt(3);    		// {0, 1, 2}
int num2 = rand.nextInt(6) + 1;		// dice {1, 2, 3, 4, 5, 6}
int num3 = rand.nextInt(5) + 3;		// {3, 4, 5, 6, 7}
int num4 = rand.nextInt(5) * 2 + 3;	// {3, 5, 7, 9, 11}
int num5 = rand.nextInt(5, 10);     // {5, 6, 7, 8, 9}

// General Pattern
// rand.nextInt(numOfChoice) * leapBetweenNums + startNum
```

#### 2.2.4 Scanner

```java
// Example of using Scanner class
Scanner console = new Scanner(System.in);
int num = console.nextInt();
double num2 = console.nextDouble();
String str = console.next();			// input stops at space or enter
String str2 = console.nextLine();		// input stops at enter only
```

#### 2.2.5 Character: 

| Method/Value | Usage | Example |
| ------------ | ----- | ------- |
| `Character.isUpperCase(chara)` | check if a character is an uppercase letter | `Character.isUpperCase('a')` returns `false` |
| `Character.isLowerCase(chara)` | check if a character is a lowercase letter | `Character.isLowerCase('a')` returns `true`  |
| `Character.isLetter(chara)`    | check if a character is a letter | `Character.isLetter('a')` returns `true`     |
| `Character.isDigit(chara)`     | check if a character is a digit  | `Character.isDigit('9')` returns `true`      |
| `Character.toUpperCase(chara)` | convert a character to uppercase | `Character.toUpperCase('a')` returns `'A'`   |
| `Character.toLowerCase(chara)` | convert a character to lowercase | `Character.toLowerCase('A')` returns `'a'`   |

```java
// Example of using Character class
/**
 * Checks if a password is valid or not, a valid password should contain uppercase letter, lowercase letter and digit
 * @param password the input password
 * @return if the password is valid or not
 */
public static boolean isPasswordValid(String password) {
    boolean upper = false;
    boolean lower = false;
    boolean digit = false;
    
    for (int i = 0; i < password.length(); i++) {
        char c = password.charAt(i);
        if (Character.isUpperCase(c)) {
            upper = true;
        }
        else if (Character.isLowerCase(c)) {
            lower = true;
        }
        else if (Character.isDigit(c)) {
            digit = true;
        }
    }
    
    return upper && lower && digit;
}
```

## 3. Control Structures

There are three control structures:

### 3.1  Sequence

Step by step, line by line, boring

### 3.2 Selection

Be able to skip part of the code

1. `if...(else if)...(else)`: supports all boolean operators, such as `<`, `>`, `>=`, `<=` etc.

    ```java
    // Example of using if...else
    if (age >= 18) {
        System.out.println("You can drive");
    }
    ```

2. Conditional operator `(condition) ? a : b`: is usually used to replace simple `if...else` statement.

    ```java
    // Example 1 of using conditional operator
    if (num1 >= num2) {
        return num1;
    }
    else {
        return num2;
    }
  
    // should be written as:
    return (num1 >= num2) ? num1 : num2;

    // ---------------------------------------

    // Example 2 of using conditional operator
    if (num1 >= num2) {
        max = num1;
    }
    else { 
        max = num2;
    }

    // should be written as:
    max = (num1 >= num2) ? num1 : num2;
    ```

3. **switch...case (break)**: **==** can only be used to compare primitive values

    ```java
    // Bad example of using switch...case, should use if...else instead
    switch (age) {
        case 1:
        case 2:
        case 3:
            ..
        case 17:
            System.out.println("You cannot drive");
            break;
        case 18:
        case 19:
            ...
            System.out.println("You can drive");
    }

    // Good example of using switch...case
    switch (oper) {
        case 1:
            withdraw();
            break;
        case 2:
            deposit();
            break;
        case 3:
            displayBalance();
            break;        
    }
    ```

* **switch expression** is an advanced way to write switch case.

    ```java 
    switch (oper) {
        case 1 -> withdraw();
        case 2 -> deposit();
        case 3 -> displayBalance();        
    }
    ```

### 3.3 Loop

Give programmers the ability to go back to the previous code

1. `for` loop: most frequently used, the initialization of the counter, the condition, and the counter updating are written in one place. If the number of iterations is predictable, then use the `for` loop.

    ```java
    // Example of using for loop
    /**
    * Prints characters in a string
    * @param str the input string
    */
    public static void printCharacters(String str) {
        for (int i = 0; i < str.length(); i++)
            System.out.print(str.charAt(i));
    }

    // for loop with special increament
    for (int i = 0; i < str.length(); i += 2)

    // for loop with no initialization
    for (; num < str.length(); i += 2)
        
    // for loop with two initialization
    for (int i = 0; num < str.length(); i += 2)
    ```

2. `while` loop: second.  If the number of iterations is not predictable, then use the `while` loop.

    ```java
    // Example of using while loop
    /**
    * Prints characters in a string
    * @param str the input string
    */
    public static void printCharacters(String str) {
        int i = 0;
        while (i < str.length())
            System.out.print(str.charAt(i++));
    }
    ```

3. `do...while` loop: If the first iteration of the loop should be executed with no condition, then use the `do...while` loop.

    ```java
    // Example of using do...while loop
    String pin = null;				// null is not "", you can use "".equals(), but not null.equals()
    do {
        System.out.println("Please input your pin:");
        pin = console.next();
    } while (!pin.equals(realPin));
    ```

## 4. OOP (Object-oriented Programming)

### 4.1 what is OOP

OOP is about 2 things:
* Class: takes no memory
    * data members (fields): the information of the object
    * methods: the behaviors of the object
        * constructor
            * **default constructor**: with no parameter

            ```Java
            // Example of default constructor
            public Clock() {
                this.hr = 0;
                this.mi = 0;
                this.se = 0;
            }
            ```

            * **constructor with data members**: with three parameters
            
            ```java
            // Example of constructor with data members
            public Clock(int hr, int mi, int se) {
                this.hr = hr;
                this.mi = mi;
                this.se = se;
            }
            ```

            * **copy constructor**: with one parameter with the same data type as the class
            
            ```Java
            // Example of copy constructor
            public Clock(Clock clock) {
                this.hr = clock.hr; 
                this.mi = clock.mi;
                this.se = clock.se;
            }
            ```
            
        * **toString()**: to generate a string to represent an object of that class
        
            ```java
            // Example of toString()
            @Override
            public String toString() {
                return String.format("%02d:%02d:%02d", hr, mi, se);
                // Example of output would be: 08:16:24
                // %d: integer
                // %f: floating
                // %c: char
                // %s: string
                // %%: %
                // %5d: the width of the place holder   123 -> "  123"
                // %05d: zero-padding  123 -> "00123"
                // %.2f: the length of the decimal part: 3.3333333 -> 3.33 
                // %5.2f: 3.3333333 -> " 3.33"
                // %-5.2f: 3.3333333 -> "3.33 "
            }
            ```
        
        * **equals()**: to compare two objects (*overload* version), we will learn the (*override* version) of this method this semester
        
        * **getter and setter**: to read or modify the data members of the class
* Object: takes memory

### 4.2 Access modifier
Access modifiers are used to define where the data member/method can be used. There are 4 access modifiers in total, and we have learned 2 of them:

| Access modifier | Accessibility                     |
| --------------- | --------------------------------- |
| private         | only the current class can use it |
| public          | every class can use it            |
| protected       |                                   |
| default         |                                   |

### 4.3 Shallow copy VS Deep copy
For each object, java will allocate two pieces of memory to it, one to store the real values based on the data member, while the other one to store the address of the first piece of memory.

* **Shallow copy**: copying the address of an object. Shallow copy does not create a new object, it only creates another name for an existing object. 

* **Deep copy**: copying the real values of an object. Deep copy creates another object.

### 4.4 Static VS Non-static
* **static** members: belong to the class, and should be called through the class when using it. A static method can ONLY visit static values and methods
  
    ```java
    // Example of calling a static method
    public static void main() {
        Clock.staticMethod();
    }
    ```
    
* **non-static**: belongs to the object, and should be called through an object when using it. A non-static method can visit both non-static and static values and methods
  
    ```java
    // Example of calling a non-static method
    public static void main() {
        Clock c1 = new Clock();
	    c1.nonStaticMethod();
    }
    ```

    ```java
    // Example of static and non-static variables and methods
    /**
     * A class of clock
     * @author Yi Wang
     */
    public class Clock {
        private int hr;              // non-static
        private int mi;
        private int se;
        private static String brand; // static 
    
        /*
         * A non-static method can visit non-static and static values and methods
         * non-static method should be called through an object
         * e.g.: c1.increaseHr()
         */
        public void increaseHr() {  
            hr++;
            if (hr == 24)
                hr = 0;
            System.out.println(brand);
        }
    
        /*
         * A static method can ONLY visit static values and methods
         * static method should be called through the class
         * e.g.: Clock.printBrand()
         * Math.max(1, 2)
        */
        public void printBrand() {
            System.out.println(brand);
        } 
    }
    ```
