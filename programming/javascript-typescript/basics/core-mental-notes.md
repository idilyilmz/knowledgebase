# Mental Notes

## **Core**

### 🧩 1. Revisit the Core Concept (Quick Mental Reset)

A **getter** in JavaScript looks like this:

```js
class Example {
  constructor(value) {
    this._value = value;
  }

  get value() {
    return this._value;  // ✅ must explicitly return something
  }
}

const ex = new Example(42);
console.log(ex.value); // 42
```

👉 Without the `return`, the getter automatically returns `undefined`.

So just remember:

> “A getter *returns* a value — it’s meant to *get*, not *do*.”

That’s your mini mental cue:
**get → return something**

### 🧠 2. Build “Syntax Reflexes” With Micro-Practice

Try **micro-reps** — short, repetitive coding bursts (2–3 mins) that focus on just one concept.
Example:

```js
// practice: write 3 getter methods that return different values
class Dog {
  constructor(name, age) {
    this._name = name;
    this._age = age;
  }
  get name() { return this._name; }
  get age() { return this._age; }
  get info() { return `${this._name} is ${this._age} years old.`; }
}
```

Then, type a few wrong versions intentionally (without `return`) and observe what happens in the console — it builds awareness through contrast.

### 🧭 3. Use Tools That Reinforce Syntax Awareness

* **ESLint** or **Prettier**: can highlight or auto-fix common syntax slips.
* **VS Code IntelliSense**: shows expected return types and warns about missing returns in getters.
* **TypeScript (optional)**: catches missing `return` statements automatically in some cases.

### 🧱 4. Write Mini Mental Notes

Sometimes a quick “cheat tag” helps anchor habits:

```js
// 🧠 getters RETURN values
get myValue() { return this._val; }
```

Add that as a comment once or twice in your practice code — repetition helps encode it into long-term recall.

### 🧩 5. Relearn by Teaching

Explain the concept *out loud* (or to a rubber duck 🦆).
For example:

> “A getter is like a property access — when it’s called, it *returns* the value instead of doing something else.”

Teaching strengthens the connection between logic and syntax memory.

### 🚀 6. Keep It Light and Repetitive

You don’t need to drill it endlessly. Just spend **5 minutes daily** reviewing small snippets like:

```js
get something() { return this._something; }
```

After a week or two, it becomes automatic again.

## 🧩 **OOP Core Mental Notes**

### 🧱 1. **Object**

> “An object is a box of data *and* behavior.”
> Properties = nouns 🧺, Methods = verbs ⚙️

```js
const dog = {
  name: "Buddy",
  bark() { console.log("Woof!"); }
};
```

➡️ Think: “Objects describe *what something is* and *what it can do*.”

### 🧬 2. **Class**

> “A class is a blueprint — not the building.”
> You can’t live in the blueprint, but you can make houses from it. 🏠

```js
class Dog {
  constructor(name) {
    this.name = name;
  }
  bark() { console.log(`${this.name} barks!`); }
}
```

➡️ Mnemonic: *Class creates, object exists.*

### 🚀 3. **Instance**

> “An instance is a real thing made from the class.”

```js
const rex = new Dog("Rex");
rex.bark(); // Rex barks!
```

➡️ “`new` = make it real.”

### 🪞 4. **`this` keyword**

> “`this` refers to the *current object in context*.”
> It’s the self-awareness of your instance. 🧘

```js
class Cat {
  constructor(name) { this.name = name; }
  meow() { console.log(`${this.name} says meow`); }
}
```

➡️ “`this` = me, right now.”

### 🧩 5. **Encapsulation**

> “Keep data safe and clean — hide the mess, expose the use.” 🧹
> Only reveal what others *need* to interact with.

```js
class BankAccount {
  #balance = 0; // private field
  deposit(amount) { this.#balance += amount; }
  get balance() { return this.#balance; }
}
```

➡️ “Encapsulation = control the door, not the room.”

### 🧬 6. **Abstraction**

> “Show the *what*, hide the *how*.” 🎭
> Users don’t care *how* it works — only *that* it works.

```js
car.start(); // abstraction hides the engine details
```

➡️ “Abstraction = simplicity by hiding complexity.”

### 👨‍👩‍👧 7. **Inheritance**

> “A subclass inherits from a parent — like a child learning family traits.” 👪
> DRY principle in action (Don’t Repeat Yourself).

```js
class Animal {
  eat() { console.log("Eating..."); }
}
class Dog extends Animal {
  bark() { console.log("Woof!"); }
}
```

➡️ “Extend, don’t redo.”

### 🌀 8. **Polymorphism**

> “Many forms, one interface.” 🦋
> Same method name → different behaviors depending on the object.

```js
class Animal { speak() { console.log("Some sound"); } }
class Dog extends Animal { speak() { console.log("Bark!"); } }
class Cat extends Animal { speak() { console.log("Meow!"); } }

const pets = [new Dog(), new Cat()];
pets.forEach(pet => pet.speak()); // Bark! Meow!
```

➡️ “One call, many voices.”

### 🔒 9. **Private vs Public**

> “Public shares; Private protects.”
> Prefix with `#` in JS to make a property private.

```js
class User {
  #password;
  constructor(password) { this.#password = password; }
}
```

➡️ “If you lock it (`#`), you control it.”

### 🧠 10. **Composition**

> “Prefer *has-a* over *is-a* when possible.” 🧩
> Don’t always subclass — combine behaviors.

```js
class Engine {
  start() { console.log("Engine on"); }
}
class Car {
  constructor() { this.engine = new Engine(); }
  start() { this.engine.start(); }
}
```

➡️ “Composition builds; inheritance borrows.”

## 🧰 **TypeScript-Specific OOP Notes**

* **Access Modifiers**

  > `public` = anyone can use
  > `protected` = subclass only
  > `private` = class only

  ```ts
  class Person {
    public name: string;
    private age: number;
    protected id: number;
  }
  ```

* **Interfaces**

  > “Interfaces define *shape*, not *substance*.”

  ```ts
  interface Flyable { fly(): void; }
  class Bird implements Flyable {
    fly() { console.log("Flying high!"); }
  }
  ```

* **Abstract Classes**

  > “Abstract = can’t be built, but can be extended.”

  ```ts
  abstract class Shape {
    abstract area(): number;
  }
  class Circle extends Shape {
    area() { return Math.PI * 5 ** 2; }
  }
  ```

## 🪜 **Quick OOP Mantras**

* 💭 “Classes describe, objects exist.”
* 🔁 “Reuse via inheritance, adapt via composition.”
* 🔒 “Encapsulate what varies.”
* 🧱 “Start simple, abstract later.”
* 🪄 “If it has state and behavior, it’s an object.”
* 🚫 “Avoid God classes — no one object should do everything.”
