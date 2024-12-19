### **Core Java**

1. **What are the features of Java?**
   - Object-oriented, platform-independent, robust, secure, high-performance, multithreaded, distributed, etc.

2. **What is the difference between `==` and `equals()`?**
   - `==` compares object references, while `equals()` compares object content.

3. **Explain the concept of a Class and an Object.**
   - A class is a blueprint, and an object is an instance of a class.

4. **What is the difference between `abstract` class and `interface`?**
   - Abstract class can have method implementations, while interface methods are abstract by default (pre-Java 8).

5. **What is the purpose of the `super` keyword?**
   - Used to access the parent class’s members and constructors.

6. **What is the difference between `String`, `StringBuilder`, and `StringBuffer`?**
   - `String` is immutable, `StringBuilder` is mutable and non-synchronized, `StringBuffer` is mutable and synchronized.

7. **What is the difference between `HashSet` and `TreeSet`?**
   - `HashSet` is faster and unordered, while `TreeSet` is sorted and slower.

8. **What is a static method?**
   - A method that belongs to the class rather than an instance and can be called without creating an object.

9. **What is the purpose of `final`, `finally`, and `finalize`?**
   - `final`: Prevents modification.
   - `finally`: Ensures code execution in a try-catch block.
   - `finalize`: Called by garbage collector before object destruction.

10. **What are Java annotations?**
    - Metadata for code, e.g., `@Override`, `@Deprecated`, `@FunctionalInterface`.

---

### **Object-Oriented Programming (OOP)**

11. **What are the principles of OOP?**
    - Encapsulation, Abstraction, Inheritance, Polymorphism.

12. **What is the difference between `method overloading` and `method overriding`?**
    - Overloading occurs within the same class; overriding occurs between parent and child classes.

13. **Explain the `this` keyword.**
    - Refers to the current instance of a class.

14. **What is a constructor?**
    - A method used to initialize objects, invoked automatically upon object creation.

15. **What is an inner class?**
    - A class defined inside another class.

---

### **Multithreading and Concurrency**

16. **What is multithreading?**
    - Concurrent execution of two or more threads.

17. **What is the difference between `synchronized` and `volatile`?**
    - `synchronized` ensures atomicity; `volatile` ensures visibility of changes.

18. **What is a deadlock?**
    - A situation where two threads wait indefinitely for each other’s resources.

19. **What are thread states in Java?**
    - New, Runnable, Blocked, Waiting, Timed Waiting, Terminated.

20. **What is the difference between `wait()` and `sleep()`?**
    - `wait()` releases the lock; `sleep()` doesn’t.

---

### **Collections Framework**

21. **What are the differences between List, Set, and Map?**
    - List: Ordered and allows duplicates.
    - Set: Unordered and unique elements.
    - Map: Key-value pairs.

22. **What is the difference between `ArrayList` and `LinkedList`?**
    - `ArrayList` is faster for random access; `LinkedList` is better for insertions and deletions.

23. **Explain the difference between `HashMap` and `Hashtable`.**
    - `HashMap` is non-synchronized; `Hashtable` is synchronized.

24. **What is the difference between `fail-fast` and `fail-safe` iterators?**
    - Fail-fast: Throws `ConcurrentModificationException`.
    - Fail-safe: Doesn’t throw an exception.

25. **What is the purpose of `Comparable` and `Comparator`?**
    - `Comparable`: Defines natural ordering.
    - `Comparator`: Defines custom ordering.

---

### **Design Patterns**

26. **Explain the Singleton design pattern.**
    - Ensures only one instance of a class is created.

27. **What is the Factory Method pattern?**
    - Defines a method for creating objects, but lets subclasses decide the implementation.

28. **What is the Observer pattern?**
    - Defines a one-to-many dependency between objects.

29. **Explain Dependency Injection.**
    - A design pattern to implement IoC, where dependencies are injected into objects.

30. **What is the Builder pattern?**
    - Separates the construction of a complex object from its representation.

---

### **Spring Framework**

31. **What is Spring?**
    - A framework that simplifies Java application development.

32. **What is Spring Boot?**
    - A Spring module that simplifies microservice development.

33. **What is Spring MVC?**
    - A framework for building web applications.

34. **What is the difference between `@Component`, `@Service`, `@Repository`, and `@Controller`?**
    - They are Spring stereotypes used for specific roles.

35. **What is AOP in Spring?**
    - Aspect-Oriented Programming, e.g., logging, security.

36. **What are the advantages of Spring Boot?**
    - Simplifies configuration, embedded servers, auto-configuration, production-ready features.

37. **What is the purpose of `@SpringBootApplication`?**
    - Combines `@Configuration`, `@EnableAutoConfiguration`, and `@ComponentScan`.

38. **What is the difference between `@RestController` and `@Controller`?**
    - `@RestController` returns JSON/XML directly; `@Controller` returns a view.

39. **How does Spring Boot handle dependency management?**
    - Uses the Spring Boot Starter dependencies.

40. **What is Spring Data JPA?**
    - Simplifies JPA implementation with repository interfaces.

---

### **JPA and Hibernate**

41. **What is Hibernate?**
    - An ORM tool for database interactions.

42. **What is the difference between `save()` and `persist()` in Hibernate?**
    - `save()`: Returns the generated identifier.
    - `persist()`: Does not return anything.

43. **What are Hibernate Annotations?**
    - Used to define mappings, e.g., `@Entity`, `@Table`, `@Id`.

44. **What is Lazy and Eager Fetching?**
    - Lazy: Fetches data when accessed.
    - Eager: Fetches data immediately.

45. **What is the second-level cache in Hibernate?**
    - A session-independent cache.

46. **What is the difference between `get()` and `load()`?**
    - `get()`: Fetches data immediately.
    - `load()`: Returns a proxy and fetches data lazily.

47. **What are common Hibernate exceptions?**
    - `LazyInitializationException`, `ConstraintViolationException`, `OptimisticLockException`.

---

### **Microservices**

48. **What are microservices?**
    - Architectural style that structures applications as small, independent services.

49. **What is service discovery?**
    - A mechanism to locate services dynamically (e.g., Eureka).

50. **What are the key features of REST?**
    - Stateless, client-server, cacheable, layered system.

51. **What is the difference between Monolithic and Microservices architectures?**
    - Monolithic: Single application. Microservices: Independent, loosely coupled services.

52. **What is the role of API Gateway?**
    - Manages requests, routing, and security in microservices.

53. **What is Circuit Breaker in microservices?**
    - A design pattern to handle service failures gracefully.

54. **What are some tools for microservices orchestration?**
    - Kubernetes, Docker Swarm.

55. **What is distributed tracing?**
    - Tracks requests across microservices (e.g., using Zipkin, Jaeger).

---

### **Advanced Java**

56. **What is the difference between `Servlet` and `RESTful Web Services`?**
    - Servlets handle HTTP requests; RESTful services follow REST principles.

57. **What is Java Stream API?**
    - Provides functional-style operations on collections and streams.

58. **What is a Lambda Expression?**
    - A concise way to represent anonymous functions.

59. **What is the purpose of `Optional` in Java?**
    - Handles null values more gracefully.

60. **What are functional interfaces in Java?**
    - Interfaces with a single abstract method, e.g., `Runnable`, `Callable`, `Function`.

61. **What is the Executor framework in Java?**
    - A framework for managing and controlling thread execution.

62. **What is the difference between `Callable` and `Runnable`?**
    - `Callable` can return a value and throw exceptions; `Runnable` cannot.

63. **What are CompletableFutures in Java?**
    - Asynchronous programming constructs that handle non-blocking operations.

64. **What is the use of `java.util.concurrent` package?**
    - Provides utilities for concurrent programming, e.g., `ExecutorService`, `Locks`.

65. **What is the purpose of `Reflection` in Java?**
    - Allows runtime inspection and modification of classes, methods, and fields.

