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
# **Структура библиотеки коллекций Java / Java Collections Framework Structure / Java集合库结构**

## **1. ОСНОВНЫЕ ИНТЕРФЕЙСЫ / CORE INTERFACES / 核心接口**
```
Iterable<E>
    └── Collection<E>
         ├── List<E>        // Список (порядок + дубликаты)
         ├── Set<E>         // Множество (уникальные элементы)
         │    └── SortedSet<E>
         └── Queue<E>       // Очередь
              └── Deque<E>  // Двусторонняя очередь

Map<K,V> (отдельная иерархия)
    └── SortedMap<K,V>
```

## **2. ОСНОВНЫЕ РЕАЛИЗАЦИИ / MAIN IMPLEMENTATIONS / 主要实现**

### **List:**
- `ArrayList` - динамический массив (быстрый доступ по индексу)
- `LinkedList` - двусвязный список (быстрая вставка/удаление)
- `Vector` - устаревший синхронизированный ArrayList

### **Set:**
- `HashSet` - хэш-таблица (без порядка)
- `LinkedHashSet` - сохраняет порядок вставки
- `TreeSet` - отсортированное множество

### **Map:**
- `HashMap` - хэш-таблица ключ-значение
- `LinkedHashMap` - сохраняет порядок вставки
- `TreeMap` - отсортированная карта

## **3. УТИЛИТНЫЕ КЛАССЫ / UTILITY CLASSES / 工具类**
- `Collections` - статические методы для работы с коллекциями
- `Arrays` - методы для работы с массивами

## **4. ПОТОКОБЕЗОПАСНЫЕ ВЕРСИИ / THREAD-SAFE VERSIONS / 线程安全版本**
- `ConcurrentHashMap`, `CopyOnWriteArrayList`
- `Collections.synchronizedXXX()` - синхронизированные обёртки

## **5. КЛЮЧЕВЫЕ ХАРАКТЕРИСТИКИ / KEY CHARACTERISTICS / 关键特性**

| Тип / Type | Дубликаты / Duplicates | Порядок / Order | Доступ по индексу / Index Access |
|-----------|----------------------|----------------|---------------------------------|
| **List** | Да / Yes | Сохраняется / Preserved | Да / Yes |
| **Set** | Нет / No | Не гарантирован / Not guaranteed | Нет / No |
| **Queue** | Да / Yes | FIFO/LIFO | Нет / No |

## **6. ВЫБОР КОЛЛЕКЦИИ / COLLECTION SELECTION / 集合选择**
- **ArrayList** - по умолчанию для списков
- **HashSet** - по умолчанию для множеств
- **HashMap** - по умолчанию для карт
- **LinkedList** - если нужен Deque или частые вставки в середину
- **TreeSet/TreeMap** - если нужна сортировка

## 6.4 Коллекции, множества и списки.
# **Коллекции, множества и списки / Collections, Sets and Lists / 集合、集和列表**

## **1. КОЛЛЕКЦИИ (COLLECTIONS) - общая категория / General Category / 通用类别**
- **Базовый интерфейс**: `Collection<E>`
- **Назначение**: Группировка объектов
- **Основные операции**: add(), remove(), contains(), size()
- **Все коллекции**: Iterable (можно использовать for-each)

## **2. СПИСКИ (LISTS) - упорядоченные коллекции / Ordered Collections / 有序集合**
- **Интерфейс**: `List<E>` extends `Collection<E>`
- **Характеристики**:
  - Сохраняют порядок вставки / Preserve insertion order / 保持插入顺序
  - Разрешают дубликаты / Allow duplicates / 允许重复
  - Доступ по индексу / Index access / 支持索引访问
- **Основные методы**: get(index), set(index, element), indexOf()
- **Реализации**:
  - `ArrayList` - динамический массив, быстрый доступ
  - `LinkedList` - двусвязный список, быстрая вставка
- **Использование**: когда важен порядок или нужен доступ по индексу

## **3. МНОЖЕСТВА (SETS) - уникальные элементы / Unique Elements / 唯一元素**
- **Интерфейс**: `Set<E>` extends `Collection<E>`
- **Характеристики**:
  - Гарантируют уникальность элементов / Guarantee element uniqueness / 保证元素唯一性
  - Не гарантируют порядок (кроме специальных) / No order guarantee (except special) / 不保证顺序（特殊除外）
  - Нет доступа по индексу / No index access / 不支持索引访问
- **Основной контракт**: два объекта equals() = true → не могут быть в Set одновременно
- **Реализации**:
  - `HashSet` - хэш-таблица, быстрый доступ
  - `LinkedHashSet` - сохраняет порядок вставки
  - `TreeSet` - отсортированное множество
- **Использование**: когда нужны уникальные значения без дубликатов

## 6.5 использование различных реализаций карт.
# **Использование реализаций интерфейсов коллекций / Using Collection Interface Implementations / 使用集合接口的实现**

## **1. ОСНОВНОЙ ПРИНЦИП / BASIC PRINCIPLE / 基本原则**
```java
// Программируйте на уровне интерфейсов, а не реализаций
// Program to interfaces, not implementations
// 面向接口编程，而不是实现

// ХОРОШО / GOOD / 好的:
List<String> list = new ArrayList<>();
Set<Integer> set = new HashSet<>();
Map<String, Integer> map = new HashMap<>();

// ПЛОХО / BAD / 不好的:
ArrayList<String> list = new ArrayList<>(); // Привязка к реализации
```

## **2. ВЫБОР РЕАЛИЗАЦИИ ПО ТРЕБОВАНИЯМ / CHOOSING IMPLEMENTATION BY REQUIREMENTS / 根据需求选择实现**

### **Для List:**
```java
// 1. ArrayList - по умолчанию
List<String> defaultList = new ArrayList<>();

// 2. LinkedList - частые вставки/удаления в середине
List<String> linkedList = new LinkedList<>();

// 3. CopyOnWriteArrayList - многопоточное чтение
List<String> threadSafeList = new CopyOnWriteArrayList<>();

// 4. Vector - устаревший (лучше использовать синхронизированные обёртки)
List<String> synchronizedList = Collections.synchronizedList(new ArrayList<>());
```

### **Для Set:**
```java
// 1. HashSet - по умолчанию (быстрый доступ, нет порядка)
Set<String> defaultSet = new HashSet<>();

// 2. LinkedHashSet - нужен порядок вставки
Set<String> orderedSet = new LinkedHashSet<>();

// 3. TreeSet - нужна сортировка
Set<String> sortedSet = new TreeSet<>();

// 4. EnumSet - для enum, максимальная производительность
enum Day { MONDAY, TUESDAY }
Set<Day> enumSet = EnumSet.of(Day.MONDAY, Day.TUESDAY);
```

### **Для Map:**
```java
// 1. HashMap - по умолчанию
Map<String, Integer> defaultMap = new HashMap<>();

// 2. LinkedHashMap - порядок вставки или доступа
Map<String, Integer> orderedMap = new LinkedHashMap<>();

// 3. TreeMap - сортировка по ключам
Map<String, Integer> sortedMap = new TreeMap<>();

// 4. ConcurrentHashMap - потокобезопасность
Map<String, Integer> concurrentMap = new ConcurrentHashMap<>();
```

## **3. НАСТРОЙКА РЕАЛИЗАЦИЙ / CONFIGURING IMPLEMENTATIONS / 配置实现**

### **Начальная ёмкость / Initial Capacity / 初始容量:**
```java
// ArrayList с начальной ёмкостью 100
List<String> list = new ArrayList<>(100);

// HashMap с начальной ёмкостью 50 и фактором загрузки 0.75
Map<String, Integer> map = new HashMap<>(50, 0.75f);
```

## 6.6 Карты (maps) в библиотеке коллекций.
# **Карты (maps) в библиотеке коллекций / Maps in Collections Library / 集合库中的Map**

## **1. ОСНОВНЫЕ ОПЕРАЦИИ / BASIC OPERATIONS / 基本操作**

```java
// Создание карты / Creating a map / 创建Map
Map<String, Integer> map = new HashMap<>();

// 1. Добавление элементов / Adding elements / 添加元素
map.put("apple", 10);     // Добавить ключ-значение / Add key-value / 添加键值对
map.put("banana", 5);
map.put("orange", 8);

// 2. Получение значения / Getting value / 获取值
Integer apples = map.get("apple");     // 10
Integer grapes = map.get("grapes");    // null (ключа нет / key doesn't exist / 键不存在)

// 3. Проверка наличия ключа/значения / Check if key/value exists / 检查键/值是否存在
boolean hasApple = map.containsKey("apple");   // true
boolean hasValue5 = map.containsValue(5);      // true

// 4. Удаление элемента / Remove element / 删除元素
map.remove("banana");      // Удалить по ключу / Remove by key / 根据键删除

// 5. Размер карты / Map size / Map大小
int size = map.size();     // 2 (после удаления banana / after removing banana / 删除banana后)

// 6. Проверка на пустоту / Check if empty / 检查是否为空
boolean isEmpty = map.isEmpty();  // false
```

## **2. ПЕРЕБОР ЭЛЕМЕНТОВ / ITERATING OVER MAP / 遍历Map**

```java
Map<String, Integer> fruits = new HashMap<>();
fruits.put("apple", 10);
fruits.put("banana", 5);
fruits.put("orange", 8);

// 1. Перебор ключей / Iterate over keys / 遍历键
for (String key : fruits.keySet()) {
    System.out.println("Key: " + key + ", Value: " + fruits.get(key));
}

// 2. Перебор значений / Iterate over values / 遍历值
for (Integer value : fruits.values()) {
    System.out.println("Value: " + value);
}

// 3. Перебор пар ключ-значение / Iterate over key-value pairs / 遍历键值对
for (Map.Entry<String, Integer> entry : fruits.entrySet()) {
    String key = entry.getKey();
    Integer value = entry.getValue();
    System.out.println(key + " = " + value);
}

// 4. Java 8: forEach с лямбдой / Java 8: forEach with lambda
fruits.forEach((key, value) -> 
    System.out.println(key + " -> " + value)
);
```



## 6.7 Использование различных реализаций карт.
# **Использование различных реализаций карт / Using Different Map Implementations / 使用不同的Map实现**

## **1. HASHMAP - СТАНДАРТНАЯ ХЭШ-ТАБЛИЦА / STANDARD HASH TABLE / 标准哈希表**

```java
// Самый распространённый выбор, нет гарантии порядка
// Most common choice, no order guarantee
// 最常用选择，不保证顺序

Map<String, Integer> hashMap = new HashMap<>();

// Настройка начальной ёмкости и фактора загрузки
// Configure initial capacity and load factor
// 配置初始容量和负载因子
Map<String, Integer> tunedHashMap = new HashMap<>(16, 0.75f);
// 16 - начальная ёмкость, 0.75 - когда увеличивать размер
// 16 - initial capacity, 0.75 - when to resize
// 16 - 初始容量，0.75 - 何时扩容

// Особенности / Features / 特点:
// - Лучшая производительность в большинстве случаев
// - Best performance for most cases
// - 大多数情况下性能最好
// - Разрешает null ключи и значения
// - Allows null keys and values
// - 允许null键和值
// - Не гарантирует порядок итерации
// - No iteration order guarantee
// - 不保证迭代顺序
```

## **2. LINKEDHASHMAP - СОХРАНЕНИЕ ПОРЯДКА / PRESERVES ORDER / 保持顺序**

```java
// Сохраняет порядок вставки или порядок доступа
// Preserves insertion order or access order
// 保持插入顺序或访问顺序

// 1. Порядок вставки (по умолчанию) / Insertion order (default) / 插入顺序（默认）
Map<String, Integer> insertionOrderMap = new LinkedHashMap<>();
insertionOrderMap.put("zebra", 1);
insertionOrderMap.put("apple", 2);
insertionOrderMap.put("banana", 3);
// Порядок итерации: zebra → apple → banana
// Iteration order: zebra → apple → banana
// 迭代顺序：zebra → apple → banana

// 2. Порядок доступа (LRU кэш) / Access order (LRU cache) / 访问顺序（LRU缓存）
Map<String, Integer> accessOrderMap = new LinkedHashMap<>(
    16,      // начальная ёмкость / initial capacity
    0.75f,   // фактор загрузки / load factor
    true     // true = порядок доступа, false = порядок вставки
);
accessOrderMap.put("A", 1);
accessOrderMap.put("B", 2);
accessOrderMap.put("C", 3);
accessOrderMap.get("A"); // Теперь A становится последним при итерации
// Порядок итерации: B → C → A (последние использованные в конце)
```

## **3. TREEMAP - СОРТИРОВАННАЯ КАРТА / SORTED MAP / 排序的Map**

```java
// Автоматическая сортировка по ключам (натуральный порядок или Comparator)
// Automatic sorting by keys (natural order or Comparator)
// 按键自动排序（自然顺序或Comparator）

// 1. Натуральный порядок (ключи должны реализовать Comparable)
Map<String, Integer> treeMap = new TreeMap<>();
treeMap.put("zebra", 1);
treeMap.put("apple", 2);
treeMap.put("banana", 3);
// Автоматическая сортировка: apple → banana → zebra
// Automatic sorting: apple → banana → zebra
// 自动排序：apple → banana → zebra

// 2. С кастомным Comparator / With custom Comparator
Map<String, Integer> reverseTreeMap = new TreeMap<>(Comparator.reverseOrder());
reverseTreeMap.put("apple", 1);
reverseTreeMap.put("banana", 2);
// Сортировка в обратном порядке: banana → apple

// 3. По длине строки / By string length
Map<String, Integer> lengthSortedMap = new TreeMap<>(
    Comparator.comparingInt(String::length)
        .thenComparing(Comparator.naturalOrder())
);
lengthSortedMap.put("aaa", 1);
lengthSortedMap.put("bb", 2);
lengthSortedMap.put("c", 3);
// Сортировка: c → bb → aaa (по длине, затем по алфавиту)
```

## **4. CONCURRENTHASHMAP - ПОТОКОБЕЗОПАСНАЯ / THREAD-SAFE / 线程安全**

```java
// Для многопоточных приложений без блокировок
// For multithreaded applications without locks
// 用于无锁的多线程应用程序

ConcurrentMap<String, Integer> concurrentMap = new ConcurrentHashMap<>();

// Атомарные операции / Atomic operations / 原子操作
concurrentMap.putIfAbsent("key", 100);  // Добавить если нет
concurrentMap.replace("key", 100, 200); // Заменить если старое значение 100

// Потокобезопасный перебор / Thread-safe iteration
for (Map.Entry<String, Integer> entry : concurrentMap.entrySet()) {
    // Не требует синхронизации / Doesn't require synchronization
    System.out.println(entry.getKey() + ": " + entry.getValue());
}

// Особенности / Features / 特点:
// - Сегментированная блокировка (лучше чем synchronized)
// - Segmented locking (better than synchronized)
// - 分段锁（比synchronized好）
// - Не блокирует всю карту при операциях
// - Doesn't lock entire map during operations
// - 操作期间不锁定整个Map
```

## **5. WEAKHASHMAP - С WEAK-ССЫЛКАМИ НА КЛЮЧИ / WITH WEAK REFERENCES TO KEYS / 对键使用弱引用**

```java
// Ключи могут быть удалены сборщиком мусора если нет других ссылок
// Keys can be garbage collected if no other references
// 如果没有其他引用，键可以被垃圾回收

Map<Object, String> weakMap = new WeakHashMap<>();
Object key = new Object();
weakMap.put(key, "value");

key = null; // Теперь ключ может быть удален сборщиком мусора
System.gc(); // Сборка мусора / Garbage collection / 垃圾回收

// После GC запись может исчезнуть из карты
// After GC the entry may disappear from map
// GC后条目可能会从Map中消失

// Использование: кэши, где ключи могут быть удалены
// Use case: caches where keys can be removed
// 用例：键可以被删除的缓存
```

## **6. ENUMMAP - ДЛЯ ПЕРЕЧИСЛЕНИЙ / FOR ENUMS / 用于枚举**

```java
enum Day { MONDAY, TUESDAY, WEDNESDAY }

// Высокопроизводительная карта для enum ключей
// High-performance map for enum keys
// 用于枚举键的高性能Map

EnumMap<Day, String> schedule = new EnumMap<>(Day.class);
schedule.put(Day.MONDAY, "Work");
schedule.put(Day.TUESDAY, "Meeting");

// Особенности / Features / 特点:
// - Массив внутри (очень быстрая)
// - Array internally (very fast)
// - 内部使用数组（非常快）
// - Гарантированный порядок объявления enum
// - Guaranteed enum declaration order
// - 保证枚举声明的顺序
// - Не разрешает null ключи
// - Doesn't allow null keys
// - 不允许null键
```

## **7. ИДЕНТИФИЦИРУЮЩАЯ ХЭШ-ТАБЛИЦА / IDENTITY HASH MAP / 标识哈希表**

```java
// Сравнение ключей по == (ссылочное равенство), а не equals()
// Key comparison by == (reference equality), not equals()
// 按键的==（引用相等）比较，而不是equals()

Map<String, Integer> identityMap = new IdentityHashMap<>();
String key1 = new String("key");
String key2 = new String("key"); // Другой объект / Different object / 不同的对象

identityMap.put(key1, 1);
identityMap.put(key2, 2); // Добавит, т.к. key1 != key2 (по ссылке)

System.out.println(identityMap.size()); // 2 (два разных ключа)
System.out.println(key1.equals(key2));  // true (по значению)
```

## 6.8 Итераторы карт и коллекций.
# **Итераторы карт и коллекций / Iterators for Maps and Collections / Map和集合的迭代器**

## **1. БАЗОВЫЙ ИТЕРАТОР ДЛЯ КОЛЛЕКЦИЙ / BASIC ITERATOR FOR COLLECTIONS / 集合的基本迭代器**

```java
List<String> fruits = new ArrayList<>();
fruits.add("apple");
fruits.add("banana");
fruits.add("orange");

// Получение итератора / Get iterator / 获取迭代器
Iterator<String> iterator = fruits.iterator();

// Проверка наличия следующего элемента / Check if has next element / 检查是否有下一个元素
while (iterator.hasNext()) {
    // Получение следующего элемента / Get next element / 获取下一个元素
    String fruit = iterator.next();
    System.out.println(fruit);
    
    // Удаление текущего элемента во время итерации
    // Remove current element during iteration
    // 在迭代期间删除当前元素
    if (fruit.equals("banana")) {
        iterator.remove(); // Безопасное удаление / Safe removal / 安全删除
    }
}
// Результат: ["apple", "orange"] (banana удалён)
```

## **2. LISTITERATOR - ДВУНАПРАВЛЕННЫЙ ИТЕРАТОР / BIDIRECTIONAL ITERATOR / 双向迭代器**

```java
List<String> list = new ArrayList<>(Arrays.asList("A", "B", "C", "D"));

// Получение ListIterator / Get ListIterator / 获取ListIterator
ListIterator<String> listIterator = list.listIterator();

// Движение вперёд / Forward movement / 向前移动
while (listIterator.hasNext()) {
    String element = listIterator.next();
    System.out.println("Next: " + element);
    
    // Проверка предыдущего элемента / Check previous element / 检查前一个元素
    if (listIterator.hasPrevious()) {
        System.out.println("  Previous index: " + listIterator.previousIndex());
    }
    
    // Модификация элемента / Modify element / 修改元素
    if (element.equals("B")) {
        listIterator.set("B-modified"); // Заменить текущий элемент
    }
    
    // Добавление элемента / Add element / 添加元素
    if (element.equals("C")) {
        listIterator.add("C-added"); // Добавить перед следующим
    }
}

// Движение назад / Backward movement / 向后移动
while (listIterator.hasPrevious()) {
    String element = listIterator.previous();
    System.out.println("Previous: " + element);
}
```

## **3. ИТЕРАТОРЫ ДЛЯ MAP / ITERATORS FOR MAP / Map的迭代器**

```java
Map<String, Integer> map = new HashMap<>();
map.put("apple", 10);
map.put("banana", 5);
map.put("orange", 8);

// 1. Итерация по ключам / Iterate over keys / 遍历键
Iterator<String> keyIterator = map.keySet().iterator();
while (keyIterator.hasNext()) {
    String key = keyIterator.next();
    if (key.equals("banana")) {
        keyIterator.remove(); // Удаляет и ключ, и значение
    }
}

// 2. Итерация по значениям / Iterate over values / 遍历值
Iterator<Integer> valueIterator = map.values().iterator();
while (valueIterator.hasNext()) {
    Integer value = valueIterator.next();
    if (value < 6) {
        valueIterator.remove(); // Удаляет запись с этим значением
    }
}

// 3. Итерация по entrySet (самый эффективный способ)
Iterator<Map.Entry<String, Integer>> entryIterator = map.entrySet().iterator();
while (entryIterator.hasNext()) {
    Map.Entry<String, Integer> entry = entryIterator.next();
    String key = entry.getKey();
    Integer value = entry.getValue();
    
    if (key.equals("orange")) {
        entry.setValue(15); // Изменить значение
    }
    
    System.out.println(key + " = " + value);
}
```

## 6.9 Стандартные алгоритмы библиотеки для работы с коллекциямии массивами.
# **Стандартные алгоритмы библиотеки для работы с коллекциями и массивами / Standard Algorithms for Collections and Arrays / 集合和数组的标准算法**

## **1. КЛАСС COLLECTIONS / CLASS COLLECTIONS / Collections类**

### **Сортировка / Sorting / 排序**
```java
List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5, 9);

// Сортировка в естественном порядке / Natural order sorting / 自然顺序排序
Collections.sort(numbers); // [1, 1, 3, 4, 5, 9]

// Сортировка в обратном порядке / Reverse order sorting / 反向排序
Collections.sort(numbers, Collections.reverseOrder()); // [9, 5, 4, 3, 1, 1]

// Сортировка с кастомным Comparator / Custom Comparator sorting / 自定义Comparator排序
Collections.sort(numbers, (a, b) -> b - a); // [9, 5, 4, 3, 1, 1]

// Java 8+ метод списка / Java 8+ list method
numbers.sort(Comparator.naturalOrder()); // [1, 1, 3, 4, 5, 9]
```

### **Бинарный поиск / Binary Search / 二分查找**
```java
List<Integer> sortedList = Arrays.asList(1, 3, 5, 7, 9);

// Бинарный поиск в отсортированном списке
// Binary search in sorted list
// 在已排序列表中二分查找
int index = Collections.binarySearch(sortedList, 5); // 2 (индекс / index)

// Если элемент не найден / If element not found / 如果元素未找到
int notFound = Collections.binarySearch(sortedList, 6); // -4
// Отрицательное значение = -(точка вставки) - 1
// Negative value = -(insertion point) - 1
// 负值 = -(插入点) - 1
// Для 6 точка вставки = 3 → результат = -4
```

### **Перемешивание / Shuffling / 洗牌**
```java
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5);

// Случайное перемешивание / Random shuffle / 随机打乱
Collections.shuffle(list); // Например: [3, 1, 5, 2, 4]

// С конкретным Random / With specific Random / 使用特定的Random
Collections.shuffle(list, new Random(42)); // Детерминированное перемешивание
```

### **Обратный порядок / Reverse Order / 反转顺序**
```java
List<String> words = Arrays.asList("A", "B", "C", "D");

// Обратить порядок элементов / Reverse element order / 反转元素顺序
Collections.reverse(words); // ["D", "C", "B", "A"]

// Получить Comparator для обратного порядка / Get Comparator for reverse order
Comparator<String> reverseComparator = Collections.reverseOrder();
words.sort(reverseComparator); // Сортировка в обратном порядке
```

## **2. КЛАСС ARRAYS / CLASS ARRAYS / Arrays类**

### **Сортировка массивов / Array Sorting / 数组排序**
```java
int[] numbers = {5, 2, 8, 1, 9};

// Сортировка всего массива / Sort entire array / 排序整个数组
Arrays.sort(numbers); // [1, 2, 5, 8, 9]

// Сортировка части массива / Sort part of array / 排序部分数组
int[] partial = {5, 2, 8, 1, 9};
Arrays.sort(partial, 1, 4); // Сортировать с индекса 1 до 3
// Результат: [5, 1, 2, 8, 9]

// Параллельная сортировка (Java 8+) / Parallel sort
int[] bigArray = new int[100000];
Arrays.parallelSort(bigArray); // Использует ForkJoinPool
```

### **Бинарный поиск в массивах / Binary Search in Arrays / 数组中二分查找**
```java
int[] sortedArray = {1, 3, 5, 7, 9};

// Поиск в отсортированном массиве / Search in sorted array / 在已排序数组中查找
int index = Arrays.binarySearch(sortedArray, 5); // 2

// Поиск в диапазоне / Search in range / 在范围内查找
int rangeIndex = Arrays.binarySearch(sortedArray, 1, 4, 7); // 3
// Ищет между индексами 1 и 3 (включительно) / Searches between indices 1 and 3
```

### **Сравнение и заполнение / Comparison and Filling / 比较和填充**
```java
int[] arr1 = {1, 2, 3};
int[] arr2 = {1, 2, 3};
int[] arr3 = {1, 2, 4};

// Сравнение массивов / Compare arrays / 比较数组
boolean equal1 = Arrays.equals(arr1, arr2); // true
boolean equal2 = Arrays.equals(arr1, arr3); // false

// Глубокое сравнение для многомерных массивов / Deep comparison for multi-dimensional
int[][] deep1 = {{1, 2}, {3, 4}};
int[][] deep2 = {{1, 2}, {3, 4}};
boolean deepEqual = Arrays.deepEquals(deep1, deep2); // true

// Заполнение массива / Fill array / 填充数组
int[] array = new int[5];
Arrays.fill(array, 7); // [7, 7, 7, 7, 7]
Arrays.fill(array, 1, 4, 9); // Заполнить индексы 1-3: [7, 9, 9, 9, 7]
```

## **3. ПОЛЕЗНЫЕ АЛГОРИТМЫ COLLECTIONS / USEFUL COLLECTIONS ALGORITHMS / 有用的集合算法**

### **Минимум и максимум / Min and Max / 最小值和最大值**
```java
List<Integer> numbers = Arrays.asList(3, 1, 4, 1, 5);

// Найти минимальный элемент / Find minimum element / 找到最小元素
Integer min = Collections.min(numbers); // 1

// Найти максимальный элемент / Find maximum element / 找到最大元素
Integer max = Collections.max(numbers); // 5

// С кастомным Comparator / With custom Comparator
String minLength = Collections.min(
    Arrays.asList("apple", "kiwi", "banana"),
    Comparator.comparingInt(String::length) // Сравнить по длине
); // "kiwi"
```

### **Частота и непересекающиеся / Frequency and Disjoint / 频率和不相交**
```java
List<String> words = Arrays.asList("apple", "banana", "apple", "orange");

// Подсчитать частоту элемента / Count element frequency / 计算元素频率
int appleCount = Collections.frequency(words, "apple"); // 2

// Проверить непересекающиеся коллекции / Check disjoint collections
List<Integer> list1 = Arrays.asList(1, 2, 3);
List<Integer> list2 = Arrays.asList(4, 5, 6);
List<Integer> list3 = Arrays.asList(3, 4, 5);

boolean noCommon1 = Collections.disjoint(list1, list2); // true
boolean noCommon2 = Collections.disjoint(list1, list3); // false
```

### **Вращение и замена / Rotation and Replacement / 旋转和替换**
```java
List<Integer> list = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5));

// Циклическое вращение / Circular rotation / 循环旋转
Collections.rotate(list, 2);  // [4, 5, 1, 2, 3] - сдвиг вправо
Collections.rotate(list, -1); // [5, 1, 2, 3, 4] - сдвиг влево

// Заменить все вхождения / Replace all occurrences / 替换所有出现
List<String> words = new ArrayList<>(Arrays.asList("a", "b", "a", "c"));
Collections.replaceAll(words, "a", "X"); // ["X", "b", "X", "c"]
```

## **4. КОПИРОВАНИЕ И ОБМЕН / COPYING AND SWAPPING / 复制和交换**

```java
// Копирование списка / Copy list / 复制列表
List<String> source = Arrays.asList("A", "B", "C");
List<String> dest = new ArrayList<>(Arrays.asList("X", "Y", "Z", "W"));

Collections.copy(dest, source); // dest теперь: ["A", "B", "C", "W"]
// dest должен быть не меньше source

// Обмен элементов / Swap elements / 交换元素
List<Integer> numbers = new ArrayList<>(Arrays.asList(1, 2, 3, 4));
Collections.swap(numbers, 0, 3); // [4, 2, 3, 1]
```

## **5. АЛГОРИТМЫ ПРЕОБРАЗОВАНИЯ / TRANSFORMATION ALGORITHMS / 转换算法**

### **Преобразование в массивы / Convert to Arrays / 转换为数组**
```java
List<String> list = Arrays.asList("A", "B", "C");

// Коллекция → массив / Collection → array / 集合 → 数组
String[] array1 = list.toArray(new String[0]); // Массив правильного размера

// Создание неизменяемого списка из массива / Create immutable list from array
List<String> unmodifiable = Arrays.asList("A", "B", "C");
// unmodifiable.add("D"); // UnsupportedOperationException

// Java 9+ фабричные методы / Java 9+ factory methods
List<String> fixedList = List.of("A", "B", "C");
Set<Integer> fixedSet = Set.of(1, 2, 3);
Map<String, Integer> fixedMap = Map.of("A", 1, "B", 2);
```

### **Многократное копирование / nCopies / 多次复制**
```java
// Создать неизменяемый список из n копий / Create immutable list of n copies
List<String> repeated = Collections.nCopies(3, "Hello");
// ["Hello", "Hello", "Hello"] - immutable list
```

# 7.Методы рефакторинга для преобразования структуры программы на языке Java. Рефакторинг типов. Рефакторинг иерархии наследования. Перемещение методов по иерархии наследования и между классами. Использование среды Eclipse для рефакторинга программы на языке Java.

## 7.1 Методы рефакторинга для преобразования структуры программы на языке Java.
这是 **第 7 题 (Question 7)** 的核心内容。
考题原文提到：**“Методы рефакторинга... Рефакторинг иерархии наследования. Перемещение методов”**（重构方法...继承层次重构。移动方法）。

这里为你挑选了 **3 个最经典、最适合初学者** 的重构例子。

---

### 1. Extract Method (Выделение метода / 提取方法)

**场景：** 一个方法太长了，或者某段代码逻辑是独立的。我们把它“挖”出来变成一个新方法。
**Сценарий:** Метод слишком длинный, или часть кода логически независима. Мы "выделяем" её в новый метод.
**Scenario:** A method is too long, or a piece of code is logically independent. We "extract" it into a new method.

#### 🔴 Before (До / 重构前)

```java
void printOwing() {
    printBanner();

    // RU: Печать деталей (дублирование или сложная логика)
    // EN: Print details (duplication or complex logic)
    // CN: 打印细节（重复代码或复杂逻辑）
    System.out.println("name: " + name);
    System.out.println("amount: " + amount);
}

```

#### 🟢 After (После / 重构后)

```java
void printOwing() {
    printBanner();
    printDetails(amount); // RU: Вызов нового метода
                          // EN: Call the new method
                          // CN: 调用新方法
}

// RU: Выделенный метод. Код стал чище.
// EN: Extracted method. Code became cleaner.
// CN: 被提取的方法。代码变得更整洁。
void printDetails(double amount) {
    System.out.println("name: " + name);
    System.out.println("amount: " + amount);
}

```

---

### 2. Rename Method (Переименование метода / 重命名方法)

**场景：** 方法名不能清楚地说明它在做什么。
**Сценарий:** Имя метода не объясняет ясно, что он делает.
**Scenario:** The method name does not clearly explain what it does.

#### 🔴 Before (До / 重构前)

```java
// RU: Имя "doIt" ничего не значит
// EN: Name "doIt" means nothing
// CN: 名字 "doIt" 没有任何意义
public int doIt() {
    return days * 24;
}

```

#### 🟢 After (После / 重构后)

```java
// RU: Имя объясняет суть (часы в днях)
// EN: Name explains the essence (hours in days)
// CN: 名字解释了本质（天数转小时）
public int convertDaysToHours() {
    return days * 24;
}

```

---

### 3. Pull Up Method (Подъем метода / 上移方法)

**场景：** 两个子类有完全相同的代码。为了消除重复，我们把它移到父类里。**(这是考题中“继承层次重构”的重点)**
**Сценарий:** Два подкласса имеют абсолютно одинаковый код. Чтобы убрать дублирование, мы переносим его в родительский класс.
**Scenario:** Two subclasses have exactly the same code. To remove duplication, we move it to the parent class.

#### 🔴 Before (До / 重构前)

```java
class Dog extends Animal {
    // RU: Дублирующийся код
    // EN: Duplicated code
    // CN: 重复代码
    void sleep() { System.out.println("Zzz..."); }
}

class Cat extends Animal {
    // RU: Дублирующийся код
    // EN: Duplicated code
    // CN: 重复代码
    void sleep() { System.out.println("Zzz..."); }
}

```

#### 🟢 After (После / 重构后)

```java
class Animal {
    // RU: Метод перемещен в родителя (Рефакторинг иерархии)
    // EN: Method moved to parent (Hierarchy refactoring)
    // CN: 方法被移到父类（继承层次重构）
    void sleep() { 
        System.out.println("Zzz..."); 
    }
}

class Dog extends Animal { 
    // RU: Теперь пусто, наследует sleep()
    // EN: Now empty, inherits sleep()
    // CN: 现在是空的，继承了 sleep()
}

class Cat extends Animal { 
    // ... 
}

```

---

## 7.2 Рефакторинг типов. 
这是 **第 7 题 (Question 7)** 中的 **“Рефакторинг типов” (类型重构)** 。

最经典、最常考的例子是 **“Generalize Type” (泛化类型)**，即用更通用的接口替换具体的实现类。

---

### 1. Generalize Type (Обобщение типа / 泛化类型)

**场景：** 我们把变量声明为具体类（如 `ArrayList`），这限制了灵活性。应该改为接口（如 `List`）。
**Сценарий:** Мы объявляем переменную как конкретный класс (`ArrayList`), что ограничивает гибкость. Лучше использовать интерфейс (`List`).
**Scenario:** We declare a variable as a concrete class (`ArrayList`), limiting flexibility. It's better to use an interface (`List`).

#### 🔴 Before (До / 重构前)

```java
// RU: Жесткая привязка к ArrayList. Мы не можем легко заменить его на LinkedList.
// EN: Hard dependency on ArrayList. We cannot easily switch to LinkedList.
// CN: 硬编码依赖 ArrayList。我们无法轻松切换到 LinkedList。
public void processData() {
    ArrayList<String> names = new ArrayList<>();
    names.add("Alice");
    // ...
}

```

#### 🟢 After (После / 重构后)

```java
// RU: Использование интерфейса List. Теперь можно подставить любую реализацию списка.
// EN: Using List interface. Now we can swap in any list implementation.
// CN: 使用 List 接口。现在可以替换为任何列表实现。
public void processData() {
    List<String> names = new ArrayList<>(); 
    // List<String> names = new LinkedList<>(); // RU: Легко изменить! (CN: 容易更改！)
    names.add("Alice");
    // ...
}

```

---

### 2. Replace Primitive with Object (Замена примитива объектом / 以对象取代基本类型)

**场景：** 代码里用简单的 `String` 或 `int` 表示复杂概念（如电话号码、邮政编码）。应该创建一个专门的类。
**Сценарий:** Код использует простые `String` или `int` для сложных понятий (телефон, индекс). Стоит создать специальный класс.
**Scenario:** The code uses simple `String` or `int` for complex concepts (phone, zip code). A special class should be created.

#### 🔴 Before (До / 重构前)

```java
class User {
    String name;
    
    // RU: Просто строка. Нет проверки формата, нет логики.
    // EN: Just a string. No format validation, no logic.
    // CN: 只是个字符串。没有格式验证，没有逻辑。
    String phoneNumber; 
}

```

#### 🟢 After (После / 重构后)

```java
class User {
    String name;
    
    // RU: Теперь это тип! Внутри класса PhoneNumber может быть валидация.
    // EN: Now it's a type! Inside PhoneNumber class, there can be validation.
    // CN: 现在它是一个类型！PhoneNumber 类内部可以包含验证逻辑。
    PhoneNumber phoneNumber; 
}

class PhoneNumber {
    private String number;
    // Constructor, format logic...
}

```

---

### 7.3 Рефакторинг иерархии наследования.
这是 **第 7 题 (Question 7)** 中的 **“Рефакторинг иерархии наследования” (继承层次重构)**。

这一部分的重点在于**改变类之间的父子关系**，而不仅仅是移动方法。最经典的两个例子是 **“提炼超类” (Extract Superclass)** 和 **“折叠继承体系” (Collapse Hierarchy)**。

---

### 1. Extract Superclass (Выделение суперкласса / 提炼超类)

**场景：** 两个类有相似的字段和方法，但它们没有共同的父类（或者父类太通用了）。我们需要创建一个新的父类来存放共性。
**Сценарий:** Два класса имеют похожие поля и методы, но у них нет общего родителя. Мы создаем новый родительский класс для общего кода.
**Scenario:** Two classes have similar fields and methods, but they lack a common parent. We create a new parent class for the common code.

#### 🔴 Before (До / 重构前)

```java
// RU: Два независимых класса с дублированием (name, email)
// EN: Two independent classes with duplication (name, email)
// CN: 两个独立的类，存在重复代码 (name, email)

class Student {
    String name;
    String email;
    void study() { ... }
}

class Teacher {
    String name;
    String email;
    void teach() { ... }
}

```

#### 🟢 After (После / 重构后)

```java
// RU: Создаем общего родителя Person
// EN: Create a common parent Person
// CN: 创建一个共同的父类 Person
class Person {
    String name;
    String email;
}

// RU: Теперь классы наследуются от Person. Дублирование исчезло.
// EN: Now classes inherit from Person. Duplication is gone.
// CN: 现在这些类继承自 Person。重复代码消失了。
class Student extends Person {
    void study() { ... }
}

class Teacher extends Person {
    void teach() { ... }
}

```

---

### 2. Collapse Hierarchy (Свертывание иерархии / 折叠继承体系)

**场景：** 子类和父类太像了，子类几乎没有添加任何新功能（由于重构或其他原因）。这时应该把它们合并。
**Сценарий:** Подкласс и суперкласс слишком похожи, подкласс почти ничего не добавляет. Их следует объединить.
**Scenario:** The subclass and superclass are too similar; the subclass adds almost nothing. They should be merged.

#### 🔴 Before (До / 重构前)

```java
class Employee {
    int salary;
}

// RU: Этот класс почти пустой. Он не нужен.
// EN: This class is almost empty. It is not needed.
// CN: 这个类几乎是空的。它是不必要的。
class Salesman extends Employee {
    // RU: Нет уникального поведения
    // EN: No unique behavior
    // CN: 没有独特的行为
}

```

#### 🟢 After (После / 重构后)

```java
// RU: Мы удалили класс Salesman и перенесли всё использование в Employee
// EN: We removed Salesman class and moved all usage to Employee
// CN: 我们删除了 Salesman 类，并将所有引用都移到了 Employee
class Employee {
    int salary;
    // ...
}

```

---

## 7.4 Перемещение методов по иерархии наследования и между классами.
这是 **第 7 题 (Question 7)** 的最后一部分：**“Перемещение методов по иерархии наследования и между классами”**（在继承层次结构中移动方法以及在类之间移动方法）。

这部分主要考察两个核心操作：

1. **Push Down Method (Спуск метода / 方法下移):** 针对继承关系。
2. **Move Method (Перемещение метода / 移动方法):** 针对类与类之间的协作。

---

### 1. Push Down Method (Спуск метода / 方法下移)

**场景：** 父类中有一个方法，但只有**部分**子类需要它。对于其他子类来说，这个方法是多余甚至错误的。
**Сценарий:** В родительском классе есть метод, который нужен только **некоторым** подклассам.
**Scenario:** The parent class has a method that is used by only **some** subclasses.

#### 🔴 Before (До / 重构前)

```java
class Animal {
    // RU: Ошибка: не все животные лают. Кошкам этот метод не нужен.
    // EN: Error: not all animals bark. Cats don't need this method.
    // CN: 错误：不是所有动物都会叫。猫不需要这个方法。
    void bark() {
        System.out.println("Woof!");
    }
}

class Dog extends Animal { }

class Cat extends Animal {
    // RU: Наследует bark(), что странно.
    // EN: Inherits bark(), which is weird.
    // CN: 继承了 bark()，这很奇怪。
}

```

#### 🟢 After (После / 重构后)

```java
class Animal {
    // RU: Метод убран из родителя.
    // EN: Method removed from parent.
    // CN: 方法从父类中移除。
}

class Dog extends Animal {
    // RU: Метод перемещен ("спущен") сюда, где он действительно нужен.
    // EN: Method moved ("pushed down") here, where it is actually needed.
    // CN: 方法被移动（“下移”）到这里，这里才是真正需要它的地方。
    void bark() {
        System.out.println("Woof!");
    }
}

class Cat extends Animal {
    // RU: Чисто. Нет лишних методов.
    // EN: Clean. No extra methods.
    // CN: 干净。没有多余的方法。
}

```

---

### 2. Move Method (Перемещение метода / 移动方法)

**场景：** 一个类（Class A）中的方法，使用**另一个类**（Class B）的数据比用自己类的数据还多。这种现象叫“特性依恋” (Feature Envy)。应该把这个方法移到 Class B 去。
**Сценарий:** Метод в классе A использует данные класса B больше, чем свои собственные. Это называется "Зависть к функциям". Метод нужно перенести в класс B.
**Scenario:** A method in Class A uses more data from Class B than from its own class. This is called "Feature Envy". The method should be moved to Class B.

#### 🔴 Before (До / 重构前)

**目标：** `Student` 类里有个打印 `Course` 详情的方法。

```java
class Student {
    // ...
    
    // RU: Этот метод живет в Student, но использует только данные Course.
    // EN: This method lives in Student, but uses only Course data.
    // CN: 这个方法在 Student 里，但只使用了 Course 的数据。
    void printCourseInfo(Course c) {
        System.out.println("Course: " + c.getTitle() + ", Price: " + c.getPrice());
    }
}

class Course {
    private String title;
    private double price;
    // getters...
}

```

#### 🟢 After (После / 重构后)

**操作：** 把方法剪切到 `Course` 类里。

```java
class Student {
    // RU: Теперь Student просто вызывает метод у Course.
    // EN: Now Student just calls the method on Course.
    // CN: 现在 Student 只是调用 Course 的方法。
    void displayInfo(Course c) {
        c.printInfo();
    }
}

class Course {
    private String title;
    private double price;

    // RU: Метод перемещен сюда. Ему здесь самое место.
    // EN: Method moved here. It belongs here.
    // CN: 方法移到了这里。这才是它的归宿。
    void printInfo() {
        System.out.println("Course: " + this.title + ", Price: " + this.price);
    }
}

```

---

### 7.5 Использование среды Eclipse для рефакторинга программы на языке Java.
这是 **第 7 题 (Question 7)** 的最后一个考点：**“Использование среды Eclipse для рефакторинга программы на языке Java”** (使用 Eclipse 环境重构 Java 程序) 。

在考试中，回答这道题的关键不仅是写代码，还要描述 **“操作步骤” (Action/Steps)**。Eclipse 的强大之处在于它是自动化的。

这里有两个最常用的 Eclipse 重构功能演示。

---

### 1. Rename (Переименование / 重命名)

**场景：** 你想改一个变量名。如果你手动改，你需要查找整个项目里所有用到它的地方。用 Eclipse，一键搞定。
**Сценарий:** Вы хотите изменить имя переменной. Вручную это долго. Eclipse делает это автоматически во всем проекте.
**Scenario:** You want to rename a variable. Doing it manually is slow. Eclipse does it automatically across the whole project.

**操作步骤 (Steps):**

1. **RU:** Выделите переменную `n` -> Нажмите **Alt + Shift + R** -> Введите `name` -> Enter.
2. **EN:** Select variable `n` -> Press **Alt + Shift + R** -> Type `name` -> Enter.
3. **CN:** 选中变量 `n` -> 按 **Alt + Shift + R** -> 输入 `name` -> 回车。

#### 🔴 Before (До / 操作前)

```java
public class Student {
    // RU: Плохое имя, непонятно что это
    // EN: Bad name, unclear meaning
    // CN: 名字不好，不清楚是什么
    private String n; 

    public String getN() {
        return n;
    }
}

```

#### 🟢 After (После / Eclipse 自动修改后)

```java
public class Student {
    // RU: Eclipse переименовал поле И метод (getN -> getName)
    // EN: Eclipse renamed the field AND the method (getN -> getName)
    // CN: Eclipse 重命名了字段和方法 (getN -> getName)
    private String name; 

    public String getName() {
        return name;
    }
}

```

---

### 2. Encapsulate Field (Инкапсуляция поля / 封装字段)

**场景：** 你有一些 `public` 字段，想改成标准的 `private` 字段加 Getters/Setters。
**Сценарий:** У вас есть `public` поля, нужно превратить их в `private` с геттерами и сеттерами.
**Scenario:** You have `public` fields, need to convert them to `private` with getters and setters.

**操作步骤 (Steps):**

1. **RU:** Правый клик по полю -> **Refactor** -> **Encapsulate Field...**
2. **EN:** Right-click on field -> **Refactor** -> **Encapsulate Field...**
3. **CN:** 右键点击字段 -> **Refactor** -> **Encapsulate Field...**

#### 🔴 Before (До / 操作前)

```java
public class User {
    // RU: Публичный доступ (небезопасно)
    // EN: Public access (unsafe)
    // CN: 公有访问（不安全）
    public int age;
}

```

#### 🟢 After (После / Eclipse 自动修改后)

```java
public class User {
    // RU: Eclipse сделал поле приватным
    // EN: Eclipse made the field private
    // CN: Eclipse 把字段变成了私有
    private int age;

    // RU: И автоматически сгенерировал методы
    // EN: And automatically generated methods
    // CN: 并且自动生成了方法
    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

```

---

### 3. 常用快捷键 (Полезные горячие клавиши / Useful Shortcuts)

考试时如果能写出这几个快捷键，会非常加分：

| 功能 (Function) | 快捷键 (Windows) | 俄语说明 (RU) |
| --- | --- | --- |
| **Rename** | `Alt + Shift + R` | Переименование (самый важный!) |
| **Extract Method** | `Alt + Shift + M` | Выделение метода (код в новый метод) |
| **Extract Local Variable** | `Alt + Shift + L` | Выделение локальной переменной |
| **Organize Imports** | `Ctrl + Shift + O` | Организация импорта (удаление лишнего) |

---
