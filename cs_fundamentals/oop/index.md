# OOP

## What is OOP?
- OOP (Object Oriented Programming) is a programming style built around <strong> objects </strong>.
- <strong>Objects</strong> are things with data (properties) + behaviour (methods).
- Makes code more modular, reusable and easier to understand.
- Used in many languages like Java, Python, C# and JS/TS.

## The four pillars of OOP
| Concept       | Short Definition                                       | Quick Example                             |
|---------------|--------------------------------------------------------|-------------------------------------------|
| Encapsulation | Keep data and behavior together; hide internal details | Private variables in a class              |
| Abstraction   | Show what an object does, not how it works             | `StartEngine()` hides complex code        |
| Inheritance   | Let one class reusable another's features              | `Dog` extends `Animal`                    |
| Polymorphism  | Same action behaves differently for each object        | `speak()` → Dog barks, Cat meows          |

## Why does OOP matter?
Why use OOP?
- Encourages cleaner, structured code.
- makes programs easier to debug and scale.
- Improves code reuse and collaboration.
- Forms the base of many modern frameworks (React, Angular, Vue)

## Encapsulation (🔒)
Lock the data inside (literally like a lock). Only let people in through controlled doors (method).
- Bundles <strong>data</strong> (properties) and <strong>methods</strong> (behavior) inside a class.
- Hides internal details from outside access (data protection).
- Use <strong>getters</strong> / <strong>setters</strong> or <strong>private fields</strong> to control access.
- Promotes modularity and data integrity.

```
class BankAccount {
    #balance = 0;
    deposit(amount) { 
        if (amount > 0) this.#balance += amount; 
    }
    getBalance() {
        return this.#balance;
    }
}
```

## Abstraction (🎭)
Hodes the complexity, show only what's needed (like a mask)
- Focuses on <strong>what an object does</strong>, not <strong>how it does it</strong>.
- Simplifies complex systems using clean, simple interfaces.
- Hides implementation details through methods.
- Reduces clutter and improves readability.

```
class CoffeeMachine {
    start() {
        this.#boilWater();
        this.#brew();
    }
    #boilWater() {}
    #brew() {}
}
```

## Inheritance (🌳)
Child classes inherit traits from parent classes (like a family tree)
- Let's a child class reuse the properties and methods of a parent class.
- Promotes code reuse and avoids duplication.
- Child can override or add new features.
- Defined using the `extends` keyword in JavaScript / TypeScript.
```
class Animal {
    eat() {
        console.log("Eating...");
    }
}

class Dog extends Animal {
    bark() {
        console.log("Woof!");
    }
}
```

## Polymorphism (🔄)
One interface, many behaviors (multiple forms represented by the same method)
- Means "many forms"
- Same method name, <strong>different implementation</strong> depending on the object.
- Makes code more flexible and extensible.
- Commonly used with inheritance or interfaces.

```
class Animal {
    speak() {
        console.log("Some sound");
    }
}

class Dog extends Animal {
    speak() {
        console.log("Woof!");
    }
}

class Cat extends Animal {
    speak() {
        console.log("Meow!");
    }
}
```