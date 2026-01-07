# 1. Классы языка Java и их синтаксис. Члены класса. Статические члены класса.Поля и методы класса. Главный метод приложения. Конструкторы класса. Цепочкиконструкторов. Блоки инициализации. Статические поля и методы классов.Инициализация статических полей класса

这是基于第一题  的详细拆解。

## 1.1 Классы языка Java и их синтаксис

**Java 语言的类及其语法**

```java
public class Student {
    // Тело класса
    // 类的主体
}

```

* **Объяснение (解释):**
Класс — это шаблон для создания объектов. Основной синтаксис включает ключевое слово `class`, имя класса и фигурные скобки.
类是创建对象的模板。基本语法包括关键字 `class`、类名和花括号。

---

## 2.2 Члены класса

**类的成员**

```java
public class Student {
    String name;          // Поле (成员变量)
    void study() { ... }  // Метод (成员方法)
}

```

* **Объяснение (解释):**
Члены класса — это основные элементы, из которых состоит класс. К ним относятся поля (переменные) и методы (функции).
类的成员是构成类的基本元素。它们包括字段（变量）和方法（函数）。

---

## 2.3 Статические члены класса

**类的静态成员**

```java
public class Student {
    static String university = "MSU"; // Статическое поле (静态字段)
    
    static void showUniversity() {    // Статический метод (静态方法)
        System.out.println(university);
    }
}

```

* **Объяснение (解释):**
Статические члены объявляются с ключевым словом `static`. Они принадлежат самому классу, а не экземплярам класса.
静态成员使用 `static` 关键字声明。它们属于类本身，而不是类的实例。

---

## 2.4 Поля и методы класса

**类的字段和方法**

```java
public class Student {
    int age; // Поле: хранит состояние (字段：存储状态)

    void grow() { // Метод: определяет поведение (方法：定义行为)
        age++;
    }
}

```

* **Объяснение (解释):**
Поля хранит данные или состояние объекта. Методы определяют поведение объекта и могут изменять его состояние.
字段存储对象的数据或状态。方法定义对象的行为，并可以修改其状态。

---

## 2.5 Главный метод приложения

**应用程序的主方法**

```java
public static void main(String[] args) {
    // Точка входа в программу
    // 程序的入口点
}

```

* **Объяснение (解释):**
Это точка входа для любого приложения Java. Он всегда должен быть `public`, `static`, `void` и принимать массив строк `String[]`.
这是任何 Java 应用程序的入口点。它必须始终是 `public`、`static`、`void`，并接收一个字符串数组 `String[]`。

---

## 2.6 Конструкторы класса

**类的构造器**

```java
public class Student {
    public Student() {
        // Код конструктора
        // 构造器代码
    }
}

```

* **Объяснение (解释):**
Конструктор — это специальный блок кода, который вызывается при создании нового объекта (с помощью `new`). Он используется для инициализации объекта.
构造器是一个特殊的代码块，在创建新对象（使用 `new`）时被调用。它用于初始化对象。

---

## 2.7 Цепочки конструкторов

**构造器链**

```java
public class Student {
    String name;

    public Student() {
        this("Unknown"); // Вызов другого конструктора (调用另一个构造器)
    }

    public Student(String name) {
        this.name = name;
    }
}

```
```java
class Person {
    String name;
    
    // Конструктор родителя
    // 父类构造器
    Person(String name) {
        this.name = name;
        System.out.println("1. Parent Constructor: " + name);
    }
}

class Student extends Person {
    int id;

    // Конструктор потомка
    // 子类构造器
    Student(String name, int id) {
        super(name); // Вызов конструктора родителя (обязательно первая строка!)
                     // 调用父类构造器（必须是第一行！）
        this.id = id;
        System.out.println("2. Student Constructor");
    }
}
```

* **Объяснение (解释):**
Это процесс, когда один конструктор вызывает другой конструктор того же класса (используя `this()`) или конструктор родительского класса (используя `super()`).
这是一个构造器调用同一个类的另一个构造器（使用 `this()`）或父类构造器（使用 `super()`）的过程。

---

## 2.8 Блоки инициализации

**初始化块**

```java
public class Student {
    {
        System.out.println("Instance Block"); // Блок инициализации экземпляра (实例初始化块)
    }

    static {
        System.out.println("Static Block"); // Статический блок инициализации (静态初始化块)
    }
}

```

* **Объяснение (解释):**
Это блоки кода в фигурных скобках внутри класса. Обычные блоки выполняются при создании каждого объекта, а статические — только один раз при загрузке класса.
这是类内部花括号中的代码块。普通块在每次创建对象时执行，而静态块在类加载时只执行一次。

---

## 2.9 Статические поля и методы классов

**类的静态字段和方法**

*(注：这部分内容在题目中与第3点有重叠，但在考试中可能要求再次强调具体用途)*

```java
Math.PI;         // Статическое поле (静态字段)
Math.abs(-5);    // Статический метод (静态方法)

```

* **Объяснение (解释):**
Эти элементы можно использовать, не создавая экземпляр класса. Обычно они используются для утилит или констант.
这些元素可以在不创建类实例的情况下使用。通常用于工具类或常量。

---

## 2.10 Инициализация статических полей класса

**静态类字段的初始化**

```java
public class Config {
    static int timeout;

    static {
        // Сложная логика инициализации
        // 复杂的初始化逻辑
        timeout = 1000 * 60; 
    }
}

```

* **Объяснение (解释):**
Статические поля инициализируются при загрузке класса. Это можно сделать напрямую при объявлении или внутри статического блока инициализации.
静态字段在类加载时初始化。这可以在声明时直接完成，也可以在静态初始化块内完成。
---

# 2. Пакеты классов и интерфейсов. Импорт классов и интерфейсов из другихпакетов. Разновидности видимости классов и интерфейсов. Соглашения обименовании пакетов, классов, директорий и файлов при программировании на Java.

## 2.1 Пакеты классов и интерфейсов

**类和接口的包**

```java
// Объявляем, что этот класс живет в пакете "ru.msu.utils"
// 声明该类位于 "ru.msu.utils" 包中
package ru.msu.utils;

public class MathTools {
    public void sayHello() {
        System.out.println("Привет из пакета utils! (来自 utils 包的问候！)");
    }
}
```
```java
package ru.msu.main;

// !!! Ключевой момент: Импорт (关键点：导入) !!!
// Мы говорим Java: "Найди класс MathTools в пакете ru.msu.utils"
// 我们告诉 Java：“去 ru.msu.utils 包里找 MathTools 这个类”
import ru.msu.utils.MathTools;

public class Application {
    public static void main(String[] args) {
        // Теперь мы можем использовать MathTools как обычно
        // 现在我们可以像往常一样使用 MathTools
        MathTools tools = new MathTools();
        tools.sayHello();
    }
}
```

* **Объяснение (解释):**
Пакет — это пространство имен, которое группирует связанные классы и интерфейсы для предотвращения конфликтов имен и управления доступом.
包是一个命名空间，它将相关的类和接口组合在一起，以防止命名冲突并控制访问权限。

---

## 2.2 Импорт классов и интерфейсов из других пакетов

**从其他包导入类和接口**

```java
package com.msu.exam;

import java.util.List;       // Импорт конкретного класса (导入具体类)
import java.util.Scanner;

public class Main {
    List<String> list;       // Можно использовать короткое имя (可以使用短名称)
}

```

* **Объяснение (解释):**
Ключевое слово `import` позволяет использовать классы из других пакетов по их коротким именам, не указывая полный путь каждый раз.
`import` 关键字允许按短名称使用其他包中的类，而无需每次都指定完整路径。

---

## 2.3 Разновидности видимости классов и интерфейсов

**类和接口的可见性类型**

```java
// 1. Public: Виден везде (随处可见)
public class PublicClass { ... }

// 2. Package-Private (default): Виден только внутри пакета (仅包内可见)
class DefaultClass { ... }

```

* **Объяснение (解释):**
У классов верхнего уровня есть только два уровня доступа: `public` (доступен из любого пакета) и пакетный (доступен только внутри своего пакета).
顶层类只有两个访问级别：`public`（可从任何包访问）和包级私有（仅在自己的包内可访问）。

---

## 2.4 Соглашения об именовании пакетов

**包的命名约定**

```java
// Правильно (正确):
package ru.msu.cmc.exam;

// Неправильно (错误):
package RU.MSU.CMC.Exam;

```

* **Объяснение (解释):**
Имена пакетов всегда записываются строчными (маленькими) буквами, чтобы избежать конфликтов с именами классов или интерфейсов.
包名总是用小写字母书写，以避免与类名或接口名冲突。

---

##  2.5 Соглашения об именовании классов

**类的命名约定**

```java
// UpperCamelCase (PascalCase)
public class ExamQuestion { ... }
public class StudentRecord { ... }

```

* **Объяснение (解释):**
Имена классов должны быть существительными и записываться в стиле UpperCamelCase (каждое слово с большой буквы).
类名应该是名词，并采用 UpperCamelCase 风格（每个单词首字母大写）书写。

---

## 2.6 Соглашения об именовании директорий и файлов

**目录和文件的命名约定**

```text
Файл (File): Student.java
|-- Класс (Class): public class Student { ... }

```

* **Объяснение (解释):**
Имя файла с исходным кодом должно в точности совпадать с именем публичного класса, который в нем находится (включая регистр букв).
源代码文件的名称必须与其中包含的公共类的名称完全匹配（包括大小写）。

---

# 3. Наследование полей и методов классов в языке Java. Перекрытие наследуемых методов. Использование конструкторов наследуемых классов. Разновидности видимости членов классов. Полиморфизм. Абстрактные классы. Конечные (final) классы.

## 3.1 Наследование полей и методов классов в языке Java

```java
class Parent {
    public void publicField = "Public Field"; // доступно везде
    protected void protectedField = "Protected Field"; // доступно в подклассах и в том же пакете
    void defaultField = "Default Field"; // package-private - только в этом пакете
    private void privateField = "Private Field"; // только в этом классе

    // Метод класса Parent
    public void PublicMethod() {}
    protected void ProtectedMethod() {}
    void DefaultMethod() {}
    private void PrivateMethod() {}
}

class Child extends Parent {
    public void test(){
        // Доступ к унаследованным полям и методам
        System.out.println(publicField); // Доступно
        System.out.println(protectedField); // Доступно
        System.out.println(defaultField); // Доступно (если в том же пакете)
        // System.out.println(privateField); // Ошибка: недоступно

        PublicMethod(); // Доступно
        ProtectedMethod(); // Доступно
        DefaultMethod(); // Доступно (если в том же пакете)
        // PrivateMethod(); // Ошибка: недоступно
    }
}

```

## 3.2 Перекрытие наследуемых методов

```java
class Aniaml {
    public void makeSound() {
        System.out.println("Animal sound");
    }

    public final void sleep() {
        System.out.println("Animal is sleeping");
    }
}

class Dog extends Aniaml {
    @Override
    public void makeSound() { // Перекрытие метода
        System.out.println("Dog Bark");
    }

    //можно вызвать родительский метод
    public void MakeSoundAndParentSound() {
        super.makeSound(); // Вызов метода родителя
        this.makeSound(); // Вызов перекрытого метода
    }

    // Ошибка: нельзя переопределить final метод
    // @Override
    // public void sleep() {
    //     System.out.println("Dog is sleeping");
    // }
}

## 3.3 Использование конструкторов наследуемых классов
```java
class Animal {
    private String name;
    private int age;

    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

class Dog extends Animal {
    private String breed;

    public Dog() {
        this.breed = "Unknown";
    }

    public Dog(String name, int age) {
        super(name, age); // Вызов конструктора родителя
        this.breed = "Unknown";
    }
    public Dog(String name, int age, String breed) {
        super(name, age); // Вызов конструктора родителя - должен быть первой строкой
        this.breed = breed;
    }
}
```

## 3.4 Разновидности видимости членов классов. 
```java

package ru.example.package1;

public class VisibilityDemo {
    public int publicVar = 1;          // Доступно везде
    protected int protectedVar = 2;    // Доступно в подклассах и в том же пакете
    int defaultVar = 3;                // package-private - только в этом пакете
    private int privateVar = 4;        // только в этом классе

    public void publicMethod() {}
    protected void protectedMethod() {}
    void defaultMethod() {}
    private void privateMethod() {}
}

```

```java

package ru.example.package2;

import ru.example.package1.VisibilityDemo;

// Класс в другом пакете, но подкласс
public class SubClass extends VisibilityDemo {
    publicVar = 10;          // Доступно
    protectedVar = 20;      // Доступно
    // defaultVar = 30;     // Ошибка: недоступно
    // privateVar = 40;     // Ошибка: недоступно

    publicMethod();         // Доступно
    protectedMethod();      // Доступно
    // defaultMethod();    // Ошибка: недоступно
    // privateMethod();    // Ошибка: недоступно

}

// Класс в другом пакете, не подкласс
public class OtherClassDiffPackage {
    public void test() {
        VisibilityDemo demo = new VisibilityDemo();
        demo.publicVar = 10;          // Доступно
        // demo.protectedVar = 20;    // Ошибка: недоступно
        // demo.defaultVar = 30;      // Ошибка: недоступно
        // demo.privateVar = 40;      // Ошибка: недоступно

        demo.publicMethod();         // Доступно
        // demo.protectedMethod();    // Ошибка: недоступно
        // demo.defaultMethod();      // Ошибка: недоступно
        // demo.privateMethod();      // Ошибка: недоступно
    }
}
```

Модификатор     | Класс | Пакет | Подкласс (другой пакет) | Все остальные
---------------|-------|-------|-------------------------|---------------
public         |  Да   |  Да   |           Да            |      Да
protected      |  Да   |  Да   |           Да            |      Нет
default        |  Да   |  Да   |           Нет           |      Нет
private        |  Да   |  Нет  |           Нет           |      Нет


## 3.5 Полиморфизм

```java
// 1. Перекрытие методов (Overriding)
class Animal {
    public void makeSound() {}
}
class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow");
    }
}

// 2. Перегрузка методов (Overloading)
class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
    public int add (int a, int b, int c) {
        return a + b + c;
    }
    public double add(double a, double b) {
        return a + b;
    }
}

// 3. Полиморфизм через интерфейсы
interface CanFly {
    void fly();
}
class Bird implements CanFly {
    @Override
    public void fly() {
        System.out.println("Bird is flying");
    }
}
class Airplane implements CanFly {
    @Override
    public void fly() {
        System.out.println("Airplane is flying");
    }
}
```

## 3.6 Абстрактные классы

```java
abstract class Animal {
    // Абстрактный метод (без реализации)
    public abstract void makeSound();

    // Обычный метод (с реализацией)
    public void sleep() {
        System.out.println("Animal is sleeping");
    }

    // Статический метод в абстрактном классе
    public static void staticMethod() {
        System.out.println("Static method in abstract class");
    }

    //конструктор абстрактного класса
    public Animal() {
        System.out.println("Constructor of Abstract Animal");
    }

    // Поля абстрактного класса
    protected String name;
}

class Dog extends Animal {
    // конкретная клфасс должна реализовать абстрактные методы
    @Override
    public void makeSound() {
        System.out.println("Dog Bark");
    }

    // можно иметь собственные поля и методы
    public void showName() {
        System.out.println("Dog's name is " + name);
    }
}
```

## 3.7 Конечные (final) классы

```java
// 1. final класс нельзя наследовать
final class Animal {
    public void makeSound() {...}
}

// Ошибка: нельзя наследовать final класс
// class Dog extends Animal {

// 2. final класс можно наследовать
final class Dog extends Mammal {
    // можно иметь обычные методы
    public void bark() {...}

    // можно иметь final методы - их нельзя переопределять в подклассах
    public final void finalMethod() {...}
}
```    

# 4. Вложенность классов. Статические вложенные и внутренние классы. Доступ к статическим вложенным классам. Внутренние классы. Доступ к внутренним классам. Внутренние локальные классы. Внутренние анонимные классы.

## 4.1 Статические вложенные классы

```java
class Animal {
    private String name = "Animal";
    static String dogType = "Bulldog";

    public Animal() {
        this.name = name;
    }

    // Статический вложенный класс
    static class DogToy {
        private String toyName;

        public DogToy(String toyName) {
            this.toyName = toyName;
        }

        public void play(){
            // Доступ к статическому полю внешнего класса
            System.out.println("Playing with " + toyName + " of type " + dogType);
            // Ошибка: нельзя обратиться к нестатическому полю внешнего класса
            // System.out.println("Animal name is " + name);
        }

        public static void showDogType() {
            System.out.println("Dog type is " + dogType);
        }
    }
}

```

## 4.2 Доступ к статическим вложенным классам.

```java
public class Main {
    public static void main(String[] args) {
        // Создание экземпляра статического вложенного класса
        Animal.DogToy toy = new Animal.DogToy("Bone");
        toy.play();

        // Вызов статического метода вложенного класса
        Animal.DogToy.showDogType();
    }
}
```

## 4.3 Внутренние классы

```java
class Dog {
    private String name;
    private String breed;

    public Dog(String name, String breed) {
        this.name = name;
        this.breed = breed;
    }

    // Внутренний класс
    class DogCollor{
        private String color;
        private String size;

        public DogCollor(String color, String size) {
            this.color = color;
            this.size = size;
        }

        public void showInfo() {
            // Доступ к полям внешнего класса
            System.out.println("Dog Name: " + name + ", Breed: " + breed + ", Color: " + color + ", Size: " + size);
        }
    }
}

```

## 4.4 Доступ к внутренним классам.

```java
public class Main {
    public static void main(String[] args) {
        // Сначала создаем экземпляр внешнего класса
        Dog dog = new Dog("Buddy", "Golden Retriever");
        // Затем создаем экземпляр внутреннего класса
        Dog.DogCollor collor = dog.new DogCollor("Golden", "Large");
        collor.showInfo();
    }
}
```

## 4.5 Внутренние локальные классы

```java
class Dog {
    private String name;

    public Dog(String name) {
        this.name = name;
    }

    // Метод с локальным внутренним классом
    public void getForWalk(String parkName) {
        final int walkDuration = 60; // Локальная переменная

        // Локальный внутренний класс
        class Walk {
            public void startWalk() {
                // Доступ к полям внешнего класса и локальным переменным
                System.out.println(name + " is walking in " + parkName);
                // Доступ к final локальной переменной
                System.out.println("Walk duration: " + walkDuration + " minutes");
            }
        }

        // Создание экземпляра локального класса и вызов метода
        Walk walk = new Walk();
        walk.startWalk();
    }
}

// Другой пример использования локального класса(метод с возвратом локального класса)
public Runnable getRunnable() {
    final String message = "Hello from Runnable";

    // Локальный класс, реализующий интерфейс Runnable
    class MyRunnable implements Runnable {
        @Override
        public void run() {
            System.out.println(message);
        }
    }

    return new MyRunnable();
}
```

## 4.6 Внутренние анонимные классы

```java
// 1. Анонимный класс от интерфейса / Anonymous class from interface / 基于接口的匿名类
interface Animal {
    void makeSound();
}

class Test1 {
    void test() {
        // Создание анонимного класса / Creating anonymous class / 创建匿名类
        Animal dog = new Animal() {
            @Override
            public void makeSound() {
                System.out.println("Woof!");
            }
        };
        dog.makeSound(); // Woof!
    }
}

// 2. Анонимный класс от абстрактного класса / Anonymous class from abstract class / 基于抽象类的匿名类
abstract class Vehicle {
    abstract void move();
}

class Test2 {
    void test() {
        Vehicle car = new Vehicle() {
            @Override
            void move() {
                System.out.println("Car is driving");
            }
        };
        car.move(); // Car is driving
    }
}

// 3. Анонимный класс с конструктором / Anonymous class with constructor-like / 类似构造函数的匿名类
class Dog {
    String name;
    Dog(String name) { this.name = name; }
    void bark() { System.out.println("Woof!"); }
}

class Test3 {
    void test() {
        // Передача параметров в "конструктор" / Passing parameters to "constructor" / 传递参数给"构造函数"
        Dog dog = new Dog("Rex") {
            @Override
            void bark() {
                System.out.println(name + " says: WOOF WOOF!");
            }
        };
        dog.bark(); // Rex says: WOOF WOOF!
    }
}

// 4. Анонимный класс в аргументе метода / Anonymous class in method argument / 方法参数中的匿名类
interface OnClickListener {
    void onClick();
}

class Button {
    void setOnClickListener(OnClickListener listener) {
        listener.onClick();
    }
}

class Test4 {
    void test() {
        Button button = new Button();
        // Анонимный класс как аргумент / Anonymous class as argument / 匿名类作为参数
        button.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick() {
                System.out.println("Button clicked!");
            }
        });
    }
}
```

# 5. Типы-перечисления. Поля и методы типов-перечислений.

```java
// 1. Простое перечисление
enum Day {
    SUNDAY, MONDAY,
    TUESDAY, WEDNESDAY,
    THURSDAY, FRIDAY, SATURDAY
}

// 2. Перечисление с полями и методами / Enum with fields and methods / 带字段和方法的枚举
enum Planet {
    // Константы с параметрами / Constants with parameters / 带参数的常量
    MERCURY("Меркурий", 3.303e+23, 2.4397e6),
    VENUS("Венера", 4.869e+24, 6.0518e6),
    EARTH("Земля", 5.976e+24, 6.37814e6);
    
    // Поля / Fields / 字段
    private final String russianName;
    private final double mass;   // кг / kg
    private final double radius; // м / m
    
    // Конструктор (private по умолчанию) / Constructor (private by default) / 构造函数（默认private）
    Planet(String russianName, double mass, double radius) {
        this.russianName = russianName;
        this.mass = mass;
        this.radius = radius;
    }
    
    // Методы / Methods / 方法
    public double surfaceGravity() {
        final double G = 6.67300E-11;
        return G * mass / (radius * radius);
    }
    
    public double surfaceWeight(double otherMass) {
        return otherMass * surfaceGravity();
    }
    
    // Getter-методы / Getter methods / Getter方法
    public String getRussianName() { return russianName; }
    public double getMass() { return mass; }
    public double getRadius() { return radius; }
}

// 3. Перечисление с разным поведением / Enum with different behaviors / 带不同行为的枚举
enum Operation {
    PLUS {
        public double apply(double x, double y) { return x + y; }
    },
    MINUS {
        public double apply(double x, double y) { return x - y; }
    },
    TIMES {
        public double apply(double x, double y) { return x * y; }
    },
    DIVIDE {
        public double apply(double x, double y) { return x / y; }
    };
    
    // Абстрактный метод / Abstract method / 抽象方法
    public abstract double apply(double x, double y);
}

// 4. Перечисление с имплементацией интерфейса / Enum implementing interface / 实现接口的枚举
interface Greeting {
    void sayHello();
}

enum GreetingType implements Greeting {
    FORMAL {
        public void sayHello() {
            System.out.println("Здравствуйте!");
        }
    },
    INFORMAL {
        public void sayHello() {
            System.out.println("Привет!");
        }
    },
    FRIENDLY {
        public void sayHello() {
            System.out.println("Приветик!");
        }
    };
}
```

# 6. Стандартная библиотека коллекций языка Java. Интерфейсы, реализации иалгоритмы коллекций. Структура библиотеки коллекций. Коллекции, множества исписки. Использование реализаций интерфейсов коллекций. Карты (maps) вбиблиотеке коллекций. Использование различных реализаций карт. Итераторыкарт и коллекций. Стандартные алгоритмы библиотеки для работы с коллекциями и массивами.

## 6.1 Стандартная библиотека коллекций языка Java
---

### **1. Основные интерфейсы / Core Interfaces / 核心接口**
- `Collection<E>` — базовый интерфейс всех коллекций  
- `List<E>` — упорядоченная коллекция с доступом по индексу  
- `Set<E>` — коллекция уникальных элементов  
- `Queue<E>` — коллекция для обработки в порядке FIFO/LIFO  
- `Deque<E>` — двусторонняя очередь  
- `Map<K,V>` — отображение ключ-значение (не наследует Collection)  
- `SortedSet<E>` — отсортированное множество  
- `SortedMap<K,V>` — отсортированное отображение  

---

### **2. Реализации List / List Implementations / List 实现**
- `ArrayList<E>` — динамический массив, быстрый доступ по индексу  
- `LinkedList<E>` — двусвязный список, быстрая вставка/удаление  
- `Vector<E>` — устаревшая синхронизированная версия ArrayList  
- `Stack<E>` — стек (наследует Vector, лучше использовать Deque)  
- `CopyOnWriteArrayList<E>` — потокобезопасный вариант для чтения

---

### **3. Реализации Set / Set Implementations / Set 实现**
- `HashSet<E>` — хэш-таблица, не гарантирует порядок  
- `LinkedHashSet<E>` — сохраняет порядок вставки  
- `TreeSet<E>` — отсортированное множество на основе красно-чёрного дерева  
- `EnumSet<E>` — высокопроизводительный набор для перечислений  
- `CopyOnWriteArraySet<E>` — потокобезопасный вариант  

---

### **4. Реализации Queue / Queue Implementations / Queue 实现**
- `PriorityQueue<E>` — очередь с приоритетом (куча)  
- `ArrayDeque<E>` — двусторонняя очередь на массиве  
- `LinkedList<E>` — также реализует Deque  
- `ConcurrentLinkedQueue<E>` — потокобезопасная неблокирующая очередь  
- `ArrayBlockingQueue<E>` — потокобезопасная блокирующая очередь с фиксированным размером  

---

### **5. Реализации Map / Map Implementations / Map 实现**
- `HashMap<K,V>` — хэш-таблица, не гарантирует порядок  
- `LinkedHashMap<K,V>` — сохраняет порядок вставки или доступа  
- `TreeMap<K,V>` — отсортированная карта по ключам  
- `Hashtable<K,V>` — устаревшая синхронизированная версия HashMap  
- `ConcurrentHashMap<K,V>` — потокобезопасная хэш-таблица  
- `WeakHashMap<K,V>` — с weak-ссылками на ключи  
- `EnumMap<K,V>` — для ключей-перечислений  

---

### **6. Утилитные классы / Utility Classes / 工具类**
- `Collections` — статические методы для работы с коллекциями  
- `Arrays` — методы для работы с массивами  
- `Objects` — вспомогательные методы для объектов  

---

### **7. Алгоритмы и операции / Algorithms and Operations / 算法和操作**
- **Сортировка** — `Collections.sort()`, `List.sort()`  
- **Поиск** — `Collections.binarySearch()`  
- **Перемешивание** — `Collections.shuffle()`  
- **Обратный порядок** — `Collections.reverse()`  
- **Заполнение** — `Collections.fill()`  
- **Копирование** — `Collections.copy()`  
- **Минимум/максимум** — `Collections.min()`, `Collections.max()`  
- **Частота** — `Collections.frequency()`  
- **Непересекающиеся** — `Collections.disjoint()`  

---

### **8. Итераторы / Iterators / 迭代器**
- `Iterator<E>` — базовый итератор  
- `ListIterator<E>` — итератор для List с двунаправленным доступом  
- `Spliterator<E>` — параллельный итератор (Java 8+)  

---

### **9. Особенности версий / Version Features / 版本特性**
- **Java 1.2** — появление Collections Framework  
- **Java 5** — дженерики, Iterable, for-each  
- **Java 6** — NavigableSet/NavigableMap  
- **Java 7** — Diamond operator, ForkJoinPool  
- **Java 8** — Stream API, лямбды, методы по умолчанию  
- **Java 9** — фабричные методы `List.of()`, `Set.of()`, `Map.of()`  
- **Java 10+** — улучшения производительности, новые методы  

---

### **10. Потокобезопасные коллекции / Thread-Safe Collections / 线程安全集合**
- `ConcurrentHashMap`  
- `CopyOnWriteArrayList`  
- `CopyOnWriteArraySet`  
- `ConcurrentLinkedQueue`  
- `ConcurrentSkipListSet`  
- `ConcurrentSkipListMap`  
- `BlockingQueue` и её реализации  

---

## 6.2 Использование реализаций интерфейсов коллекций

### **1. Базовые интерфейсы / Base Interfaces / 基础接口**
```
Iterable<E> (Java 5+)
    │
    └── Collection<E>
         ├── List<E>          (список)
         ├── Set<E>           (множество)
         │    └── SortedSet<E>
         │         └── NavigableSet<E> (Java 6+)
         └── Queue<E>         (очередь)
              └── Deque<E>    (двусторонняя очередь)

Map<K,V> (отдельная иерархия)
    ├── SortedMap<K,V>
    │    └── NavigableMap<K,V> (Java 6+)
    └── ConcurrentMap<K,V>
```

---

### **II. КЛЮЧЕВЫЕ ИНТЕРФЕЙСЫ И ИХ КОНТРАКТЫ / KEY INTERFACES AND THEIR CONTRACTS / 关键接口及其契约**

### **1. Collection<E>**
```java
// Основные операции / Basic operations / 基本操作
boolean add(E e)                    // Добавить элемент
boolean remove(Object o)            // Удалить элемент
boolean contains(Object o)          // Проверить наличие
int size()                          // Количество элементов
boolean isEmpty()                   // Пустая ли коллекция
void clear()                        // Очистить коллекцию
Iterator<E> iterator()              // Получить итератор
Object[] toArray()                  // Преобразовать в массив
<T> T[] toArray(T[] a)             // Типизированный массив

// Пакетные операции / Bulk operations / 批量操作
boolean addAll(Collection<? extends E> c)
boolean removeAll(Collection<?> c)
boolean retainAll(Collection<?> c)
boolean containsAll(Collection<?> c)
```

### **2. List<E>** (добавляет к Collection)
```java
// Доступ по индексу / Index access / 索引访问
E get(int index)
E set(int index, E element)
void add(int index, E element)
E remove(int index)
int indexOf(Object o)
int lastIndexOf(Object o)

// Итерация / Iteration / 迭代
ListIterator<E> listIterator()
ListIterator<E> listIterator(int index)

// Подсписки / Sublists / 子列表
List<E> subList(int fromIndex, int toIndex)

// Сортировка / Sorting / 排序
void sort(Comparator<? super E> c)  // Java 8+
```

### **3. Set<E>** (добавляет ограничение уникальности)
- Наследует все методы Collection
- **Гарантирует уникальность элементов** (по equals())
- Не добавляет новых методов к Collection

### **4. Queue<E>** (очередь)
```java
// Основные операции / Basic operations / 基本操作
boolean offer(E e)      // Добавить (возвращает false при переполнении)
E poll()                // Удалить и вернуть (null если пусто)
E peek()                // Посмотреть первый (null если пусто)

// Методы с исключениями / Exception-throwing methods / 抛异常的方法
boolean add(E e)        // Выбрасывает исключение при переполнении
E remove()              // Выбрасывает исключение если пусто
E element()             // Выбрасывает исключение если пусто
```

### **5. Deque<E>** (двусторонняя очередь)
```java
// Добавление / Addition / 添加
void addFirst(E e)      void addLast(E e)
boolean offerFirst(E e) boolean offerLast(E e)

// Удаление / Removal / 删除
E removeFirst()         E removeLast()
E pollFirst()           E pollLast()

// Просмотр / Peek / 查看
E getFirst()            E getLast()
E peekFirst()           E peekLast()
```

### **6. Map<K,V>**
```java
// Основные операции / Basic operations / 基本操作
V put(K key, V value)               // Добавить/заменить
V get(Object key)                   // Получить по ключу
V remove(Object key)                // Удалить по ключу
boolean containsKey(Object key)     // Проверить ключ
boolean containsValue(Object value) // Проверить значение
int size()                          // Количество пар
boolean isEmpty()                   // Пустая ли карта
void clear()                        // Очистить карту

// Просмотр / Views / 视图
Set<K> keySet()                     // Множество ключей
Collection<V> values()              // Коллекция значений
Set<Map.Entry<K,V>> entrySet()      // Множество пар

// Пакетные операции / Bulk operations / 批量操作
void putAll(Map<? extends K, ? extends V> m)
```

---

## **IV. АЛГОРИТМЫ КОЛЛЕКЦИЙ / COLLECTION ALGORITHMS / 集合算法**

### **1. Алгоритмы сортировки / Sorting Algorithms / 排序算法**
```java
// Сортировка списков / Sorting lists
Collections.sort(List<T> list)                     // Естественный порядок
Collections.sort(List<T> list, Comparator<T> c)    // С компаратором
List.sort(Comparator<T> c)                         // Java 8+

// Обратная сортировка / Reverse sorting
Collections.reverse(List<?> list)                  // Обратный порядок
Collections.reverseOrder()                         // Компаратор для обратной сортировки
Collections.reverseOrder(Comparator<T> cmp)        // Обратный компаратор
```

### **2. Алгоритмы поиска / Search Algorithms / 搜索算法**
```java
// Бинарный поиск / Binary search
Collections.binarySearch(List<? extends Comparable<? super T>> list, T key)
Collections.binarySearch(List<? extends T> list, T key, Comparator<? super T> c)

// Частота / Frequency
Collections.frequency(Collection<?> c, Object o)   // Количество вхождений
```

### **3. Алгоритмы перестановок / Permutation Algorithms / 排列算法**
```java
Collections.shuffle(List<?> list)                  // Случайное перемешивание
Collections.shuffle(List<?> list, Random rnd)      // С заданным Random
Collections.rotate(List<?> list, int distance)     // Циклический сдвиг
Collections.swap(List<?> list, int i, int j)       // Обмен элементов
```

### **4. Алгоритмы заполнения / Filling Algorithms / 填充算法**
```java
Collections.fill(List<? super T> list, T obj)      // Заполнить одним значением
Collections.nCopies(int n, T o)                    // Неизменяемый список копий
Collections.replaceAll(List<T> list, T oldVal, T newVal) // Заменить все вхождения
```

### **5. Алгоритмы экстремумов / Extremum Algorithms / 极值算法**
```java
Collections.min(Collection<? extends T> coll)      // Минимальный элемент
Collections.min(Collection<? extends T> coll, Comparator<? super T> comp)
Collections.max(Collection<? extends T> coll)      // Максимальный элемент
Collections.max(Collection<? extends T> coll, Comparator<? super T> comp)
```

### **6. Алгоритмы безопасности / Safety Algorithms / 安全算法**
```java
// Неизменяемые коллекции / Immutable collections (Java 9+)
List.of(e1, e2, e3)                                // Неизменяемый список
Set.of(e1, e2, e3)                                 // Неизменяемое множество
Map.of(k1, v1, k2, v2)                             // Неизменяемая карта

// Синхронизированные обёртки / Synchronized wrappers
Collections.synchronizedList(List<T> list)
Collections.synchronizedSet(Set<T> s)
Collections.synchronizedMap(Map<K,V> m)

// Неизменяемые обёртки / Unmodifiable wrappers
Collections.unmodifiableList(List<? extends T> list)
Collections.unmodifiableSet(Set<? extends T> s)
Collections.unmodifiableMap(Map<? extends K, ? extends V> m)
```

### **7. Алгоритмы проверок / Checking Algorithms / 检查算法**
```java
Collections.disjoint(Collection<?> c1, Collection<?> c2) // Не пересекаются ли
Collections.indexOfSubList(List<?> source, List<?> target) // Поиск подсписка
Collections.lastIndexOfSubList(List<?> source, List<?> target) // Поиск с конца
```

---

## 6.3 Структура библиотеки коллекций.