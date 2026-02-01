Object-Oriented Programming (OOP) in PHP helps organize code using **classes and objects**, making it reusable, scalable, and easier to maintain.

PHP supports the core OOP principles:
- **Encapsulation**
- **Inheritance**
- **Polymorphism**
- **Abstraction**
### 1. Classes and Objects
- **Class**: A class is a blueprint or template that defines what an object will be like.
- **Object**: An object is an instance of a class. When an object is created, it has access to all the properties and methods defined in the class.
```php
class Car {
    // Properties
    public $brand;
    public $color;

    // Constructor (runs automatically when object is created)
    public function __construct($brand, $color) {
        $this->brand = $brand;
        $this->color = $color;
    }

    // Method
    public function getInfo() {
        return "This car is a {$this->color} {$this->brand}.";
    }
}

// Create an object (instance of Car)
$myCar = new Car("Toyota", "Red");

// Use a method
echo $myCar->getInfo();
```
**`Note`**
- **Properties**: Data inside class.
- **Methods**: Function inside class.

---
### 2. Important Keywords
##### `$this`
`$this` keyword refers to the **current object instance**. It is used **inside a class method** to access **non-static properties or methods of that specific object**.
```php
class Animal {
    public $name;

    public function __construct($name) {
        $this->name = $name; // Using $this to refer to the current instance's                                     property
    }

    public function describe() {           // Using $this to access a method
        return "This is a " . $this->name; 
    }
}

$animal = new Animal("Cat");
echo $animal->describe(); // Output: This is a Cat
```
`Note:` `$this` **cannot be used in static methods**.
##### self:: 
`self::` refers to the **current class** (not the object). It is used to access **static properties, constants, and methods** within the same class. `self::` does **not support inheritance (late static binding)**
```php
class Animal {
    public static $type = "Cat";

    public static function getType() {
        return self::$type; // Using self to refer to the static property
    }
}

echo Animal::getType(); // Output: Cat
```
##### parent::
`parent::` keyword is used to access members of the parent class within a child class. It is primarily used to invoke overridden methods or access overridden properties from the parent class.
```php
class Animal {
    public function makeSound() {
        return "Some generic animal sound";
    }
}

class Cat extends Animal {
    public function makeSound() {
        return parent::makeSound() . ". But specifically, Mew! Mew!"; // Using                                               parent to call the overridden method
    }
}

$cat = new Cat();
echo $cat->makeSound(); // Output: Some generic animal sound. But specifically, Mew! Mew!
```
`Note:` `parent::` can only be used to call **methods** or **static properties/methods** of the parent class.  Non-static properties are accessed via `$this`, not `parent::`.

| `$this`                    | `self::`                            | `parent::`                  |
| -------------------------- | ----------------------------------- | --------------------------- |
| Access current object data | Access static members of same class | Access parent class members |

##### static
`static` is used to declare **class properties and methods** that belong to the class itself, not to any specific object. Static properties and methods can be accessed **without creating an instance** of the class.
```php
class Math {
    public static $pi = 3.14;

    public static function add($a, $b) {
        return $a + $b;
    }
}

echo Math::$pi;
echo Math::add(2, 3);
```
**Important points:**
- Static members are accessed using the scope resolution operator `::`, not `->`.
- Inside a static method, we **cannot use `$this`**, because there is no object instance.
- Static properties are shared across all uses of the class.

**Note:**  
The `static` keyword is also used inside functions to declare variables that **retain their value between function calls**.

✅ **Rule of thumb:** Use static for **constants, shared utilities, or counters**, but not for core business data.

---
### 3. Visibility (Access Modifiers)
- **public**: Accessible from anywhere.
- **protected**: Accessible within the class and by inheriting classes.
- **private**: Accessible only within the class itself.
  
- **final:** Prevents inheritance or overriding, but does not control visibility.

---
### `4. Inheritance`
Inheritance allows a child class to reuse parent class functionality.
```php
class ParentClass {
    public $property = "I am a property";

    public function greet() {
        echo "Hello from ParentClass";
    }
}

class ChildClass extends ParentClass {
    // Child class inherits everything from ParentClass
}


// Creating an instance of the ChildClass
$child = new ChildClass();
echo $child->property;  // Output: I am a property
$child->greet();        // Output: Hello from ParentClass
```
**Key Points**
- Use `extends` keyword to inherit.
- Child class **inherits all public and protected members (except private)** of the parent.
- Child can add its own methods and properties.
### `5. Method Overriding`
Method overriding allows a **child class to provide its own implementation** for a method already defined in the parent class. This allows the child class to tailor or extend the behavior of the method to meet its specific needs. When overriding, the method signature (name + parameters) should match the parent method.
```php
// Parent class
class Car {
    public function display() {
        return "Car";
    }
}
	
// Child class
class ElectricCar extends Car {
    public function display() {
        return "Electric Car"; // Overrides parent method
    }
}

// Creating an instance of the ChildClass class
$car = new ElectricCar();
echo $car->display();  // Outputs: Electric Car
```

| Inheritance                               | Method Overriding               |
| ----------------------------------------- | ------------------------------- |
| Child uses parent’s features as they are. | Child redefines parent’s method |

### `6. Polymorphism`
Same method name → different behavior
```php
class Animal {
    public function sound() {
        return "Some sound";
    }
}

class Dog extends Animal {
    public function sound() {
        return "Bark";
    }
}

class Cat extends Animal {
    public function sound() {
        return "Meow";
    }
}

//
$animals = [new Dog(), new Cat()];

foreach ($animals as $animal) {
    echo $animal->sound() . "<br>";
}
```
**Key Rule:**
- Parent reference, child behavior
- Polymorphism works through method overriding and inheritance.
### 7. Encapsulation
Encapsulation is the concept of **restricting direct access** to an object’s internal data and requiring all interaction to happen through methods.

This is achieved using **access modifiers**:
- `public`: Accessible from anywhere.
- `private`: Accessible only within the class.
- `protected`: Accessible within the class and its subclasses.

### 🔒 Example:
```php
class BankAccount {
    private $balance = 0;

    public function deposit($amount) {
        if ($amount > 0) {
            $this->balance += $amount;
        }
    }

    public function getBalance() {
        return $this->balance;
    }
}

$account = new BankAccount();
$account->deposit(1000);
echo $account->getBalance(); // Output: 1000
```
### 8. Abstract Classes
Abstract classes are classes that cannot be instantiated directly and may contain both abstract and normal methods. They serve as blueprints for other classes.
```php
abstract class Animal {  
    protected $name;  
    abstract public function makeSound();  
}  

class Cat extends Animal {  
    public function makeSound() {  
        return "Meow!";  
    }  
}

class Dog extends Animal {  
    public function makeSound() {  
        return "Woof!";  
    }  
}
```
`Use:` Abstract classes are useful when we want to define a common set of methods and properties that multiple classes will share. By using an abstract class, we can ensure that these methods and properties are implemented consistently across all the subclasses.
### 9. Interfaces
Define the methods that a class must implement without providing the implementation.
```php
interface Drivable {
    public function startEngine();
    public function stopEngine();
}

class Car implements Drivable {
    public function startEngine() {
        // implementation
    }

    public function stopEngine() {
        // implementation
    }
}
```
**Note:** A class can implement **multiple interfaces**, unlike inheritance.

| Abstract Classes | Interfaces |
|-----------------|------------|
| Can have properties | Cannot have properties |
| Can have implemented methods | Only method signatures (before PHP 8) |
| Single inheritance (extends) | Multiple implementation (implements) |
| Use `abstract` keyword | Use `interface` keyword |
### 10. Traits
Reusable methods within classes to avoid the limitations of single inheritance.
```php
trait Gps {
    public function getCoordinates() {
        return "Coordinates";
    }
}

class Car {
    use Gps;
}

$car = new Car();
echo $car->getCoordinates();
```
### 11. Constructor and Destructor
- **Constructor**: A special method called when an object is instantiated.
  1. Constructor can accept parameters
  2. Constructor doesn't return value
- **Destructor**: A special method called when an object is destroyed.
  1. Destructor can't accept parameters
  2. Destructor is **not guaranteed to run immediately** — it runs when the object is destroyed or script ends.
```php
class Person {

    // first name of person
    private $fname;
    // last name of person
    private $lname;

    // Constructor
    public function __construct($fname, $lname) {
        echo "Initialising the object...<br/>";
        $this->fname = $fname;
        $this->lname = $lname;
    }

    // Destructor
    public function __destruct() {
        // clean up resources or do something else
        echo "Destroying Object...";
    }

    // public method to show name
    public function showName() {
        echo "My name is: " . $this->fname . " " . $this->lname . "<br/>";
    }
}

// creating class object
$john = new Person("John", "Wick");
$john->showName();
```