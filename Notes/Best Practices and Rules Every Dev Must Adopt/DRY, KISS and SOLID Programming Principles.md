From my experience as a first year undergraduate student, and listening to seniors’ experiences, Schools and Colleges teach you how to program and also the required Math such as Discrete Mathematics and Calculus. But when you leave university and enter the industry, there are concepts and principles you must know to have an easy transition. We will discussing about **KISS, DRY** and **SOLID** principles.

# KISS Principle

> Keep It Simple, Stupid!

Oftentimes, you will find yourself working together in a team. A group of developers working on different aspects of the project. If you were to switch over and work on someone else’s code, would you like to see a messy code without any comments, or variables? Or would like to see a nicely documented code that explains that part of the project well? Obviously the latter.

If you are writing a very complex program, and say you fall sick. You revisit your project after a week when you recovered. Of course you would lose the flow of programming, but would you like to come and see a code which you don’t understand anymore? Or see something that you can understand slightly to begin with? Again, the latter.

Now imagine you are working on a project alone and you are working on it everyday. You will encounter bugs and you need to debug them. How easy would it to debug the code if your code is more complicated than it has to be?

All the above scenarios point to one thing — Keep It Simple, Stupid!

> "==Any fool can write code that a computer can understand. Good programmers write code that humans can understand.” — Martin Fowler=="

At the end of the day, the machine will not care whether you wrote a simple code or a complicated code to do a certain task. In contrast, it definitely matters to humans (including you) who would read and try to understand the code.

## But how do I KISS? (sounds weird, I am aware)

Consider a model class, Student. This will store 2 items and a map whose key and value are both pairs. The first pair is of 2 strings: the module’s name and id. The second pair is of 2 doubles, marks achieved and the maximum mark of that module.

```java
data class Student(  
  val name: String,  
  val age: Int,  
  val moduleMarks: Map<Pair<String, String>, Pair<Int, Int>>  
)
```

After making such a design choice, you are now required to record the names of students and the modules in which they scored over 80%.

```java
fun scholars(students: List<Student>): Map<String, List<String>> { 
  val scholars = mutableMapOf<String, List<String>>()  
  students.forEach { student ->  
    scholars[student.name] = student.moduleMarks  
      .filter { (_, (a, m)) -> a / m > 0.8}  
      .map { ((n, _), _) -> n }  
  }  
  return scholars  
}
```

Coming back even after a few days to a code like this would be disastrous. Although you can argue this was a fairly easy example, there are ways to make this simpler. Introduce more abstractions and variables as possible.

```java
data class Student(  
  val name: String,  
  val age: Int,  
  val moduleMarks: Map<Module, Mark>  
)  
  
data class Module(  
  val name: String,  
  val id: String  
)  
  
data class Mark(  
  val achieved: Double,  
  val maximum: Double  
) {  
  fun isAbove(percentage: Double): Boolean {  
    return achieved / maximum * 100 > percentage  
}  
  
fun scholars(students: List<Student>): Map<String, List<String>> {  
  val scholars = mutableMapOf<String, List<String>>()  
  students.forEach { student ->  
    val modulesAbove80 = student.moduleMarks  
      .filter { (_, mark) -> mark.isAbove(80.0)}  
      .map { (module, _) -> module.name }  
  
    scholars[student.name] = modulesAbove80  
  }  
  return scholars  
}
```

This adds in a lot of code. But more importantly, the code looks cleaner and reads like English.

# DRY Principle

> Don’t Repeat Yourself

If you find that you are performing the same code over and over again, create a function and re-use it. In my university assignment, I was working on a set of objects (cells) and most (if not all) functions defined required me to search and fetch a particular object from the set and operate on it.
```java
public class Spreadsheet implements Basic Spreadsheet {  
  private final Set<Cell> cells;  
  
  @Override  
  public double getCellValue(CellLocation location) {  
    Cell cell = cells.stream()  
        .filter(cell -> cell.location.equals(location))  
        .findFirst()  
        .orElse(null);  
      
    return cell == null ? 0d : cell.getValue();  
  }  
  
  @Override  
  public String getCellExpression(CellLocation location) {  
    Cell cell = cells.stream()  
        .filter(cell -> cell.location.equals(location))  
        .findFirst()  
        .orElse(null);  
      
    return cell == null ? "" : cell.getExpression();  
  }  
  
  @Override  
  public void setCellExpression(CellLocation location, String input) throws InvalidSyntaxException {  
    Cell cell = cells.stream()  
        .filter(cell -> cell.location.equals(location))  
        .findFirst()  
        .orElse(null);  
  
    // ...  
  }  
  
  // ...  
}
```

That is a big code above. But while I was typing this code, I found myself copy pasting the same block of code multiple times in different parts. Hence, I abstracted them out into functions that I re-use everywhere.
```java
public class Spreadsheet implements BasicSpreadsheet {  
  private final Set<Cell> cells;  
  
  @Override  
  public double getCellValue(CellLocation location) {  
    return getFromCell(location, Cell::getValue, 0d);  
  }  
  
  @Override  
  public String getCellExpression(CellLocation location) {  
    return getFromCell(location, Cell::getExpression, "");  
  }  
  
  @Override  
  public void setCellExpression(CellLocation location, String input) throws InvalidSyntaxException {  
    Cell cell = findCell(location);  
  
    // ...  
  }  
  
  // ...  
  
  private Cell findCell(CellLocation location) {  
    return cells.stream()  
        .filter(cell -> cell.location.equals(location))  
        .findFirst()  
        .orElse(null);  
  }  
  
  private <T> T getFromCell(CellLocation location,  
                            Function<Cell, T> function,  
                            T defaultValue) {  
    Cell cell = findCell(location);  
    return cell == null ? defaultValue : function.apply(cell);  
  }  
}
```

This way, if I realize there is a bug in my code, I do not have change the code at _n_ different places. Changing it once, inside the function, is enough fix the bug everywhere.

# SOLID **Principles**

This is not one single principle, but 5 principles that are crucial to know for software development.

## S — Single Responsibility

> A class should have one, and only one, reason to change.

Possibly the easiest principle to understand. Every class/function that you define must perform one task only. Consider that you are building a networking application.
```java
class Repository(  
  private val api: MyRemoteDatabase,  
  private val local: MyLocalDatabase  
) {  
  fun fetchRemoteData() = flow {  
    // Fetching API data  
    val response = api.getData()  
  
    // Saving data in the cache  
    var model = Model.parse(response.payload)  
    val success = local.addModel(model)  
    if (!success) {  
      emit(Error("Error caching the remote data"))  
      return@flow  
    }  
  
    // Returning data from a single source of truth  
    model = local.find(model.key)  
    emit(Success(model))  
  }  
}
```
The above code is in violation of the Single Responsibility Principle. The function does not only fetch remote data, but it is also responsible for storing the data locally. This should be extracted out to a different class.
```java
class Repository(  
  private val api: MyRemoteDatabase,  
  private val cache: MyCachingService /* Notice I changed the dependency */  
) {  
  fun fetchRemoteData() = flow {  
    // Fetching API data  
    val response = api.getData()  
  
    val model = cache.save(response.payload)  
  
    // Sending back the data  
    model?.let {  
      emit(Success(it))  
    } ?: emit(Error("Error caching the remote data"))  
  }  
}  
  
// Shifted all caching logic to another class  
class MyCachingService(  
  private val local: MyLocalDatabase  
) {  
  suspend fun save(payload: Payload): Model? {  
    var model = Model.parse(payload)  
    val success = local.addModel(model)  
    return if (success)  
      local.find(model.key)  
    else  
      null  
  }  
}
```
Notice how `MyCachingService` is responsible only to save the incoming payload into the local database while the repository is responsible only for fetching the data the sending the model above. It is a good practice to do this because of something called **_separation of concerns_** which improves debugging and testability.

## O — Open/Closed

> Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification.

This principle basically means that **do not write software code that, in future changes, breaks the client-side code**. Consider that you are building a web development API in Kotlin. You have designed the ParagraphTag, the AnchorTag and the ImageTag. In your code, you are asked to compare the heights of two elements.

```java
class ParagraphTag(  
  val width: Int,  
  val height: Int  
)  
  
class AnchorTag(  
  val width: Int,  
  val height: Int  
)  
  
class ImageTag(  
  val width: Int,  
  val height: Int  
)  
  
// Client-code  
infix fun ParagraphTag.tallerThan(anchor: AnchorTag): Boolean {  
  return this.height > anchor.height  
}  
  
infix fun AnchorTag.tallerThan(anchor: ParagraphTag): Boolean {  
  return this.height > anchor.height  
}  
  
infix fun ParagraphTag.tallerThan(anchor: ImageTag): Boolean {  
  return this.height > anchor.height  
}  
  
// ... more functions
```

Sigh! That was a lot of work. Now you have new requirements asking you to include a Heading tag as well. You would have to add _six more functions_ in the client-side. Not only is this tedious, you are also **modifying** the client-side code to fit your program’s needs.

Instead, declare an interface — `PageTag`
```java
interface PageTag {  
  val width: Int  
  val height: Int  
}  
  
class ParagraphTag(  
  override val width: Int,  
  override val height: Int  
) : PageTag  
  
class AnchorTag(  
  override val width: Int,  
  override val height: Int  
) : PageTag  
  
class ImageTag(  
  override val width: Int,  
  override val height: Int  
) : PageTag  
  
  
// Client Code  
infix fun PageTag.tallerThan(other: PageTag): Boolean {  
  return this.height > other.height  
}
```

Now you have **closed** the client code for further modifying it. In order to **extend** your functionality, it is **open** to create a new class and implement `PageTag`, and everything will work perfectly.

## L — Liskov Substitution

> If S is a subtype of T, then any properties provable by T must also be provable by S.

Oh. Maths? Well, this isn’t good. In contrast, this is an easy principle to understand. Let us consider a new example.
```java
open class Bird {  
  open fun fly() {  
    // ... performs code to fly  
  }  
  
  open fun eat() {  
    // ...  
  }  
}  
  
class Penguin : Bird() {  
  override fun fly() {  
    throw UnsupportedOperationException("Penguins cannot fly")  
  }  
}
```

Notice how the `Bird` class above does not throw any exception while `Penguin` class does. _You cannot replace Penguin with Bird in your client code without breaking it or modifying it_. This violates Liskov Substitution principle. `Penguin` extending the `Bird` breaks the client-side code, thereby also violating the open/closed principle.

A way to fix this is to change your design implementation.
```java
open class FlightlessBird {  
  open fun eat() {  
    // ...  
  }  
}  
  
open class Bird : FlightlessBird() {  
  open fun fly() {  
    // ...  
  }  
}  
  
class Penguin : FlightlessBird() {  
   // ...  
}  
  
class Eagle : Bird() {  
  // ...  
}
```

This code above explains if a `FlightlessBird` can eat, then all sub classes of `FlightlessBird` can also eat. Similarly, if `Bird` can fly, then all sub classes of `Bird` must also fly.

## I — Interface Segregation

> Interfaces should not force their clients to depend on methods it does not use.

This definition does not look scary. In reality, it isn’t scary. Consider that you are building a car, an aeroplane and a bicycle. Since they are all vehicles, you are implementing the Vehicle interface.
```java
interface Vehicle {  
  fun turnOn()  
  fun turnOff()  
  fun drive()  
  fun fly()  
  fun pedal()  
}  
  
class Car : Vehicle {  
  override fun turnOn() { /* Implementation */ }  
  override fun turnOff() { /* Implementation */ }  
  override fun drive() { /* Implementation */ }  
  override fun fly() = Unit  
  override fun pedal() = Unit  
}  
  
class Aeroplane : Vehicle {  
  override fun turnOn() { /* Implementation */ }  
  override fun turnOff() { /* Implementation */ }  
  override fun drive() = Unit  
  override fun fly() { /* Implementation */ }  
  override fun pedal() = Unit  
}  
  
class Bicycle : Vehicle {  
  override fun turnOn() = Unit  
  override fun turnOff() = Unit  
  override fun drive() = Unit  
  override fun fly() = Unit  
  override fun pedal() { /* Implementation */ }  
}
```

Yuck! See how the classes are forced to implement the methods it doesn’t need to? I also cannot declare the classes as abstract. By Interface Segregation Principle, we should instead have this design.

```java
interface SystemRunnable {  
  fun turnOn()  
  fun turnOff()  
}  
  
interface Drivable() {  
  fun drive()  
}  
  
interface Flyable() {  
  fun fly()  
}  
  
interface Pedalable() {  
  fun pedal()  
}  
  
class Car : SystemRunnable, Drivable {  
  override fun turnOn() { /* Implementation */ }  
  override fun turnOff() { /* Implementation */ }  
  override fun drive() { /* Implementation */ }  
}  
  
class Aeroplane : SystemRunnable, Flyable {  
  override fun turnOn() { /* Implementation */ }  
  override fun turnOff() { /* Implementation */ }  
  override fun fly() { /* Implementation */ }  
}  
  
class Bicycle : Pedalable {  
  override fun pedal() { /* Implementation */ }  
}
```

Now this looks a lot cleaner and it is also easier to reference different capabilities by their interfaces.

## D — Dependency Inversion

> 1. High-level modules should not depend on low-level modules; both should depend on abstractions.
> 
> 2. Abstractions should not depend on details. Details should depend upon abstractions.

What does that even mean? High-level modules are those module that the business or the UI sees. Low-level modules are those which handle the intricacies of the application. Recall my example from Solid Responsibility Principle:

```java
class Repository(  
  private val api: MyRemoteDatabase,  
  private val cache: MyCachingService  
) {  
  fun fetchRemoteData() = flow {  
    // Fetching API data  
    val response = api.getData()  
  
    val model = cache.save(response.payload)  
  
    // Sending back the data  
    model?.let {  
      emit(Success(it))  
    } ?: emit(Error("Error caching the remote data"))  
  }  
}  
  
class MyRemoteDatabase {  
  suspend fun getData(): Response { /* ... */ }  
}  
  
class MyCachingService(  
  private val local: MyLocalDatabase  
) {  
  suspend fun save(): Model? { /* ... */ }  
}  
  
class MyLocalDatabase {  
  suspend fun add(model: Model): Boolean { /* ... */ }  
  suspend fun find(key: Model.Key): Model { /* ... */ }  
}
```

It looks alright and it will work perfectly. However, in the future, if I decide to change my Local database, from PostgreSQL to MongoDB; or if I decide to alter my caching mechanism completely, I would have to change entire implementation details, and client-side code as well. High-level modules depend on low-level concrete modules.

This is not right. Instead, you must abstract the functionality into an interface and have concrete implementations extend it.

```java
interface CachingService {  
  suspend fun save(): Model?  
}  
  
interface SomeLocalDb() {  
  suspend fun add(model: Model): Boolean  
  suspend fun find(key: Model.Key): Model  
}  
  
class Repository(  
  private val api: SomeRemoteDb,  
  private val cache: CachingService  
) { /* Implementation */ }  
  
class MyCachingService(  
  private val local: SomeLocalDb  
) : CachingService { /* Implement methods */ }  
  
class MyAltCachingService(  
  private val local: SomeLocalDb  
) : CachingService { /* Implement methods */ }  
  
class PostgreSQLLocalDb : SomeLocalDb { /* Implement methods */ }  
class MongoLocalDb : SomeLocalDb { /* Implement methods */ }
```
