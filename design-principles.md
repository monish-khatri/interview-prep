Here’s a comprehensive list of design principles questions with answers and code examples in PHP, tailored for a developer with 5 years of experience. These principles cover various aspects of software design and best practices.

---

### **Design Principles Questions and Answers with Code Examples**

#### **1. What is the DRY principle?**

**Answer**: The DRY (Don't Repeat Yourself) principle states that duplication of code should be eliminated. Every piece of knowledge must have a single, unambiguous representation in the system.

**Code Example**:
```php
// Violating DRY
class User {
    public function getUserInfo($userId) {
        // Fetch user info from the database
        return "User Info for $userId";
    }
}

class Admin {
    public function getAdminInfo($adminId) {
        // Fetch admin info from the database
        return "Admin Info for $adminId";
    }
}

// Following DRY
class UserRepository {
    public function getUserInfo($id) {
        // Fetch user info from the database
        return "User Info for $id";
    }
}

class User {
    private $userRepository;

    public function __construct(UserRepository $userRepository) {
        $this->userRepository = $userRepository;
    }

    public function getUserInfo($userId) {
        return $this->userRepository->getUserInfo($userId);
    }
}

class Admin {
    private $userRepository;

    public function __construct(UserRepository $userRepository) {
        $this->userRepository = $userRepository;
    }

    public function getAdminInfo($adminId) {
        return $this->userRepository->getUserInfo($adminId);
    }
}
```

---

#### **2. What is the KISS principle?**

**Answer**: The KISS (Keep It Simple, Stupid) principle advocates for simplicity in design. Systems should be as simple as possible, avoiding unnecessary complexity.

**Code Example**:
```php
// Violating KISS
class ComplexCalculator {
    public function calculate($operation, $a, $b) {
        switch ($operation) {
            case 'add':
                return $a + $b;
            case 'subtract':
                return $a - $b;
            // Complex operations can be added
        }
    }
}

// Following KISS
class SimpleCalculator {
    public function add($a, $b) {
        return $a + $b;
    }

    public function subtract($a, $b) {
        return $a - $b;
    }
}

// Usage
$calculator = new SimpleCalculator();
echo $calculator->add(5, 3); // 8
```

---

#### **3. What is the YAGNI principle?**

**Answer**: YAGNI (You Aren't Gonna Need It) is a principle that states that a programmer should not add functionality until it is necessary. This helps in avoiding unnecessary complexity and over-engineering.

**Code Example**:
```php
class User {
    private $name;
    private $email;

    public function __construct($name, $email) {
        $this->name = $name;
        $this->email = $email;
    }

    // Unnecessary methods added preemptively
    public function getUserData() {
        return ['name' => $this->name, 'email' => $this->email];
    }

    // Following YAGNI: Only necessary methods
    public function getName() {
        return $this->name;
    }

    public function getEmail() {
        return $this->email;
    }
}

// Usage
$user = new User("John Doe", "john@example.com");
echo $user->getName(); // John Doe
```

---

#### **4. Explain the Composition Over Inheritance principle.**

**Answer**: Composition over inheritance suggests that classes should achieve polymorphic behavior and code reuse by composing objects with behaviors rather than inheriting from a base class.

**Code Example**:
```php
interface QuackBehavior {
    public function quack();
}

class LoudQuack implements QuackBehavior {
    public function quack() {
        return "Quacking loudly!";
    }
}

class MuteQuack implements QuackBehavior {
    public function quack() {
        return "Silence";
    }
}

class Duck {
    protected $quackBehavior;

    public function setQuackBehavior(QuackBehavior $qb) {
        $this->quackBehavior = $qb;
    }

    public function performQuack() {
        return $this->quackBehavior->quack();
    }
}

// Usage
$duck = new Duck();
$duck->setQuackBehavior(new LoudQuack());
echo $duck->performQuack(); // Quacking loudly!
$duck->setQuackBehavior(new MuteQuack());
echo $duck->performQuack(); // Silence
```

---

#### **5. What is the Separation of Concerns principle?**

**Answer**: The Separation of Concerns principle states that different concerns or functionalities of a program should be separated into distinct sections, making the system easier to manage and modify.

**Code Example**:
```php
// Violating Separation of Concerns
class UserManager {
    public function createUser($userData) {
        // Logic to create a user
        // Logic to send an email
    }
}

// Following Separation of Concerns
class UserManager {
    private $emailService;

    public function __construct(EmailService $emailService) {
        $this->emailService = $emailService;
    }

    public function createUser($userData) {
        // Logic to create a user
        $this->emailService->sendEmail($userData['email'], "Welcome!");
    }
}

class EmailService {
    public function sendEmail($to, $message) {
        // Logic to send an email
    }
}

// Usage
$emailService = new EmailService();
$userManager = new UserManager($emailService);
$userManager->createUser(['email' => 'john@example.com']);
```

---

#### **6. Explain the Law of Demeter.**

**Answer**: The Law of Demeter (or Principle of Least Knowledge) suggests that an object should only talk to its immediate friends and not to strangers. This helps reduce dependencies between components.

**Code Example**:
```php
class Engine {
    public function start() {
        return "Engine starting";
    }
}

class Car {
    private $engine;

    public function __construct(Engine $engine) {
        $this->engine = $engine;
    }

    public function startCar() {
        return $this->engine->start();
    }
}

// Usage
$engine = new Engine();
$car = new Car($engine);
echo $car->startCar(); // Engine starting
```

---

These questions and answers, along with the code examples, cover various design principles relevant to a PHP developer with 5 years of experience, emphasizing best practices and effective software design.
