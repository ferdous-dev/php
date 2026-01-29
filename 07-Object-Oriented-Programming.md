Object-Oriented Programming (OOP) in PHP provides several features to support the principles of OOP: encapsulation, inheritance, and polymorphism. Here’s an overview of the key OOP features in PHP:

#### 1. Classes and Objects
- **Class**: A class is a blueprint or template that defines what an object will be like.
- **Object**: An object is an instance of a class. When an object is created, it inherits all the properties and methods defined in the class.
```php
<?php
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
?>
```
**`Note`**
- **Properties**: Data inside class.
- **Methods**: Function inside class.
#### 2. Keywords
In PHP, the `$this`, `self`, `parent`, and `static` keywords are used to refer to different contexts within object-oriented programming. Here’s an explanation of each:
##### $this
`$this` keyword refers to the **current object instance**. It is used **inside a class method** to access **properties or methods of that specific object**.
```php
class Animal {
    public $name;

    public function __construct($name) {
        $this->name = $name; // Using $this to refer to the current instance's                                     property
    }

    public function describe() {
        return "This is a " . $this->name; // Using $this to access a method
    }
}

$animal = new Animal("Cat");
echo $animal->describe(); // Output: This is a Cat
```
`Note:` `$this` **cannot be used in static methods**..
##### ::self 
`::self` refers to the **current class** (not the object). It is used to access **static properties, constants, and methods** within the same class. It cannot be used to access **object** properties or methods.
```php
class Animal {
    public static $type = "Animal";

    public static function getType() {
        return self::$type; // Using self to refer to the static property
    }
}

echo Animal::getType(); // Output: Animal
```
**Note:** `self` **does NOT work with inheritance** (it always points to the class where it is written).
##### ::parent
`parent` keyword is used to access members of the parent class within a child class. It is primarily used to invoke overridden methods or access overridden properties from the parent class.
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
`Note:` We can not access non-static properties/variables using the parent keywords, but we can only access static properties of the parent class.

| `$this`              | `::self`                   | `::parent`                 |
| -------------------- | -------------------------- | -------------------------- |
| refers to the object | refers to the class itself | refers to the parent class |
##### static
The `static` keyword is used to declare properties and methods of a class as static. Static properties and methods can be used without creating an instance of the class.
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
**Note:** The `static` keyword is also used to declare variables in a function which keep their value after the function has ended.

| Keyword    | Refers To              | Usage Example          |
| ---------- | ---------------------- | ---------------------- |
| `$this`    | Current object         | `$this->property`      |
| `self::`   | Current class (static) | `self::STATIC_VAR`     |
| `parent::` | Parent class (static)  | `parent::methodName()` |
#### 3. Visibility (Access Modifiers)
- **public**: Accessible from anywhere.
- **protected**: Accessible within the class and by inheriting classes.
- **private**: Accessible only within the class itself.
```php
class Car {
    private $color;
    protected $model;
    public $make;

    public function setColor($color) {
        $this->color = $color;
    }

    public function getColor() {
        return $this->color;
    }
}
```
- **final:** The `final` keyword is used to prevent a class from being inherited and to prevent inherited method from being overridden.
#### 4. Inheritance
- Allows a class to inherit properties and methods from another class using the `extends` keyword.
```php
// Parent class
class Animal {
    public $name;
    public $type;

    public function __construct($name, $type) {
        $this->name = $name;
        $this->type = $type;
    }

    public function describe() {
        return "This is a $this->type named $this->name.";
    }
}

// Child class
class Cat extends Animal {
    public function __construct($name) {
        parent::__construct($name, "Cat");
    }

    public function makeSound() {
        return "Mew! Mew!";
    }
}

// Creating an instance of the Cat class
$myCat = new Cat("Anarcoli");

echo $myCat->describe(); // Output: This is a Cat named Anarcoli.
echo "<br>";
echo $myCat->makeSound(); // Output: Mew! Mew!
```
##### Overriding Methods
Overriding methods in PHP refers to the ability of a child class to provide a specific implementation of a method that is already defined in its parent class. This allows the child class to tailor or extend the behavior of the method to meet its specific needs.
```php
// Parent class
class Animal {
    public $name;
    public $type;

    public function __construct($name, $type) {
        $this->name = $name;
        $this->type = $type;
    }

    public function describe() {
        return "This is a $this->type named $this->name.";
    }

    public function makeSound() {
        return "Some generic animal sound.";
    }
}

// Child class
class Cat extends Animal {
    public function __construct($name) {
        parent::__construct($name, "Cat");
    }

    // Overriding the makeSound method
    public function makeSound() {
        return "Mew! Mew!";
    }
}

// Creating an instance of the Cat class
$myCat = new Cat("Anarcoli");

echo $myCat->describe(); // Output: This is a Cat named Anarcoli.
echo "<br>";
echo $myCat->makeSound(); // Output: Mew! Mew!
```
#### 5. Polymorphism
- Method Overriding: A child class can provide a specific implementation of a method that is already defined in its parent class.
```php
class Car {
    public function display() {
        return "Car";
    }
}

class ElectricCar extends Car {
    public function display() {
        return "Electric Car";
    }
}

$car = new ElectricCar();
echo $car->display();  // Outputs: Electric Car
```
#### 6. Encapsulation
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
#### 7. Abstract Classes
Abstract classes are classes that cannot be instantiated directly and may contain both abstract and concrete methods. They serve as blueprints for other classes.
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
`Use:` Abstract classes are useful when you want to define a common set of methods and properties that multiple classes will share. By using an abstract class, you can ensure that these methods and properties are implemented consistently across all the subclasses.
#### 8. Interfaces
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
#### 9. Traits
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
#### 10. Constructor and Destructor
- **Constructor**: A special method called when an object is instantiated.
  1. Constructor can take arguments
  2. Constructor doesn't return value
- **Destructor**: A special method called when an object is destroyed.
  1. Destructor can't take parameters
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
        public function __destruct(){
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