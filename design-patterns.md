Here’s a list of common design patterns questions with answers and code examples in PHP. Each section highlights a particular design pattern, explains its purpose, and provides a relevant code snippet.

---

### **Design Patterns Questions and Answers with Code Examples**

#### **1. What is the Singleton Pattern?**

**Answer**: The Singleton Pattern ensures that a class has only one instance and provides a global point of access to it. This is useful for managing shared resources like configurations.

**Code Example**:
```php
class Singleton {
    private static $instance = null;

    private function __construct() {
        // Private constructor to prevent direct instantiation
    }

    public static function getInstance() {
        if (self::$instance === null) {
            self::$instance = new Singleton();
        }
        return self::$instance;
    }
}

// Usage
$instance1 = Singleton::getInstance();
$instance2 = Singleton::getInstance();

var_dump($instance1 === $instance2); // true
```

---

#### **2. What is the Factory Method Pattern?**

**Answer**: The Factory Method Pattern defines an interface for creating an object but allows subclasses to alter the type of objects that will be created. It promotes loose coupling.

**Code Example**:
```php
interface Product {
    public function getName();
}

class ConcreteProductA implements Product {
    public function getName() {
        return "Product A";
    }
}

class ConcreteProductB implements Product {
    public function getName() {
        return "Product B";
    }
}

abstract class Creator {
    abstract public function factoryMethod();

    public function someOperation() {
        $product = $this->factoryMethod();
        return $product->getName();
    }
}

class ConcreteCreatorA extends Creator {
    public function factoryMethod() {
        return new ConcreteProductA();
    }
}

class ConcreteCreatorB extends Creator {
    public function factoryMethod() {
        return new ConcreteProductB();
    }
}

// Usage
$creatorA = new ConcreteCreatorA();
echo $creatorA->someOperation(); // Product A

$creatorB = new ConcreteCreatorB();
echo $creatorB->someOperation(); // Product B
```

---

#### **3. What is the Observer Pattern?**

**Answer**: The Observer Pattern defines a one-to-many dependency between objects, so that when one object changes state, all its dependents are notified and updated automatically.

**Code Example**:
```php
class Subject {
    private $observers = [];

    public function attach($observer) {
        $this->observers[] = $observer;
    }

    public function notify() {
        foreach ($this->observers as $observer) {
            $observer->update();
        }
    }
}

class ConcreteObserver {
    public function update() {
        echo "Observer updated\n";
    }
}

// Usage
$subject = new Subject();
$observer = new ConcreteObserver();

$subject->attach($observer);
$subject->notify(); // Observer updated
```

---

#### **4. What is the Strategy Pattern?**

**Answer**: The Strategy Pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable. This allows the algorithm to vary independently from clients that use it.

**Code Example**:
```php
interface Strategy {
    public function doOperation($a, $b);
}

class Addition implements Strategy {
    public function doOperation($a, $b) {
        return $a + $b;
    }
}

class Subtraction implements Strategy {
    public function doOperation($a, $b) {
        return $a - $b;
    }
}

class Context {
    private $strategy;

    public function __construct(Strategy $strategy) {
        $this->strategy = $strategy;
    }

    public function executeStrategy($a, $b) {
        return $this->strategy->doOperation($a, $b);
    }
}

// Usage
$context = new Context(new Addition());
echo $context->executeStrategy(5, 3); // 8

$context = new Context(new Subtraction());
echo $context->executeStrategy(5, 3); // 2
```

---

#### **5. What is the Decorator Pattern?**

**Answer**: The Decorator Pattern allows behavior to be added to individual objects, either statically or dynamically, without affecting the behavior of other objects from the same class.

**Code Example**:
```php
interface Coffee {
    public function cost();
}

class BasicCoffee implements Coffee {
    public function cost() {
        return 5;
    }
}

class MilkDecorator implements Coffee {
    private $coffee;

    public function __construct(Coffee $coffee) {
        $this->coffee = $coffee;
    }

    public function cost() {
        return $this->coffee->cost() + 2; // Adding milk cost
    }
}

// Usage
$coffee = new BasicCoffee();
echo $coffee->cost(); // 5

$milkCoffee = new MilkDecorator($coffee);
echo $milkCoffee->cost(); // 7
```

---

#### **6. What is the Adapter Pattern?**

**Answer**: The Adapter Pattern allows the interface of an existing class to be used as another interface. It is useful when you want to work with incompatible interfaces.

**Code Example**:
```php
class OldSystem {
    public function oldRequest() {
        return "Old System Response";
    }
}

class NewSystem {
    public function newRequest() {
        return "New System Response";
    }
}

class Adapter {
    private $oldSystem;

    public function __construct(OldSystem $oldSystem) {
        $this->oldSystem = $oldSystem;
    }

    public function request() {
        return $this->oldSystem->oldRequest();
    }
}

// Usage
$oldSystem = new OldSystem();
$adapter = new Adapter($oldSystem);
echo $adapter->request(); // Old System Response
```

---

#### **7. What is the Command Pattern?**

**Answer**: The Command Pattern encapsulates a request as an object, thereby allowing for parameterization of clients with queues, requests, and operations.

**Code Example**:
```php
class Command {
    public function execute() {}
}

class LightOnCommand extends Command {
    private $light;

    public function __construct(Light $light) {
        $this->light = $light;
    }

    public function execute() {
        $this->light->turnOn();
    }
}

class Light {
    public function turnOn() {
        echo "Light is On\n";
    }
}

// Usage
$light = new Light();
$lightOn = new LightOnCommand($light);
$lightOn->execute(); // Light is On
```

---

These questions and answers with code examples provide a strong understanding of various design patterns relevant to a PHP developer, emphasizing best practices in software design and implementation.
