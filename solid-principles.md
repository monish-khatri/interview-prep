### **SOLID Principles Questions and Answers**

#### **1. What does the SOLID acronym stand for?**
- **Answer**: SOLID stands for five design principles aimed at making software designs more understandable, flexible, and maintainable:
  - **S**: Single Responsibility Principle (SRP)
  - **O**: Open/Closed Principle (OCP)
  - **L**: Liskov Substitution Principle (LSP)
  - **I**: Interface Segregation Principle (ISP)
  - **D**: Dependency Inversion Principle (DIP)

---

#### **2. What is the Single Responsibility Principle (SRP)?**
- **Answer**: SRP states that a class should have only one reason to change, meaning it should have only one job or responsibility. This principle helps to reduce the complexity of classes and promotes easier testing and maintenance.
```php
class User {
    private $name;
    
    public function __construct($name) {
        $this->name = $name;
    }

    public function getName() {
        return $this->name;
    }
}

class UserRepository {
    public function save(User $user) {
        // Code to save user to the database
    }
}

class EmailService {
    public function sendEmail(User $user) {
        // Code to send email to user
    }
}

// Usage
$user = new User("John Doe");
$userRepo = new UserRepository();
$userRepo->save($user);
$emailService = new EmailService();
$emailService->sendEmail($user);

```
---

#### **3. How do you implement the Open/Closed Principle (OCP)?**
- **Answer**: The OCP states that software entities (classes, modules, functions) should be open for extension but closed for modification. This can be achieved by using interfaces or abstract classes, allowing new functionality to be added through new implementations rather than altering existing code.
```php
interface Shape {
    public function area();
}

class Rectangle implements Shape {
    private $width;
    private $height;

    public function __construct($width, $height) {
        $this->width = $width;
        $this->height = $height;
    }

    public function area() {
        return $this->width * $this->height;
    }
}

class Circle implements Shape {
    private $radius;

    public function __construct($radius) {
        $this->radius = $radius;
    }

    public function area() {
        return pi() * ($this->radius ** 2);
    }
}

// Usage
function calculateArea(Shape $shape) {
    return $shape->area();
}

$rectangle = new Rectangle(10, 5);
$circle = new Circle(7);
echo calculateArea($rectangle); // 50
echo calculateArea($circle); // 153.94

```
---

#### **4. Explain the Liskov Substitution Principle (LSP).**
- **Answer**: The LSP dictates that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program. This means that subclasses should extend the behavior of the parent class without changing its intended functionality.
```php
class Bird {
    public function fly() {
        return "Flying";
    }
}

class Sparrow extends Bird {
    public function fly() {
        return "Sparrow flying";
    }
}

class Ostrich extends Bird {
    public function fly() {
        throw new Exception("Ostrich cannot fly");
    }
}

// Usage
function makeBirdFly(Bird $bird) {
    return $bird->fly();
}

$sparrow = new Sparrow();
echo makeBirdFly($sparrow); // Sparrow flying
$ostrich = new Ostrich();
// echo makeBirdFly($ostrich); // Exception: Ostrich cannot fly

```
---

#### **5. What is the Interface Segregation Principle (ISP)?**
- **Answer**: ISP states that no client should be forced to depend on methods it does not use. Instead of having a large, general-purpose interface, it is better to have smaller, more specific ones. This leads to a more modular design and prevents bloated interfaces that require clients to implement unnecessary methods.
```php
interface Printer {
    public function printDocument($document);
}

interface Scanner {
    public function scanDocument($document);
}

class MultiFunctionPrinter implements Printer, Scanner {
    public function printDocument($document) {
        // Print logic
    }
    
    public function scanDocument($document) {
        // Scan logic
    }
}

// Usage
$printer = new MultiFunctionPrinter();
$printer->printDocument("document.pdf");
$printer->scanDocument("document.pdf");

```
---

#### **6. Describe the Dependency Inversion Principle (DIP).**
- **Answer**: The DIP asserts that high-level modules should not depend on low-level modules; both should depend on abstractions. Additionally, abstractions should not depend on details; details should depend on abstractions. This principle promotes loose coupling by inverting the traditional dependency structure through the use of interfaces or abstract classes.
```php
interface PaymentGateway {
    public function pay($amount);
}

class PayPalPayment implements PaymentGateway {
    public function pay($amount) {
        // PayPal payment logic
        return "Paid $amount using PayPal";
    }
}

class StripePayment implements PaymentGateway {
    public function pay($amount) {
        // Stripe payment logic
        return "Paid $amount using Stripe";
    }
}

class ShoppingCart {
    private $paymentGateway;

    public function __construct(PaymentGateway $paymentGateway) {
        $this->paymentGateway = $paymentGateway;
    }

    public function checkout($amount) {
        return $this->paymentGateway->pay($amount);
    }
}

// Usage
$paypal = new PayPalPayment();
$cart = new ShoppingCart($paypal);
echo $cart->checkout(100); // Paid 100 using PayPal

```
---

#### **7. How do the SOLID principles benefit your PHP applications?**
- **Answer**: The SOLID principles improve PHP applications by:
  - Enhancing code readability and maintainability.
  - Making it easier to test and debug individual components.
  - Promoting reuse of code and reducing redundancy.
  - Facilitating changes and new feature additions without breaking existing functionality.

---

#### **8. Can you give an example of a violation of the Single Responsibility Principle?**
- **Answer**: A class that handles both user authentication and sending email notifications violates SRP. If there is a change in email service, both functionalities need to be modified, which increases the risk of introducing bugs and makes the class more complex.

---

#### **9. What is a common violation of the Open/Closed Principle?**
- **Answer**: Modifying an existing class to add new features instead of extending it is a violation of OCP. For instance, adding a new method to an existing payment class to support a new payment method means modifying the existing code rather than creating a new class that implements a common interface.

---

#### **10. How can you ensure adherence to the Interface Segregation Principle?**
- **Answer**: To adhere to ISP, create multiple, specific interfaces rather than one general-purpose interface. For example, instead of having a single interface for all functionalities of a printer (printing, scanning, faxing), create separate interfaces for each function, allowing clients to implement only the ones they need.

---

These questions and answers provide a solid understanding of the SOLID principles, focusing on their importance and implementation in PHP development, especially for someone with 5 years of experience.
