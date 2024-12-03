## SprintBoot_Greetings
It define a simple Spring Boot RESTful web service that returns a personalized greeting message when a user accesses the ```/greeting``` endpoint.

<br />

## Test your local host
| Link                                     | Description                       | Output Screenshot                |
|------------------------------------------|-----------------------------------|----------------------------------|
| [http://localhost:8080/greeting](http://localhost:8080/greeting)             | Default greeting                  | <img width="362" alt="Screenshot 2024-12-03 at 4 55 04 PM" src="https://github.com/user-attachments/assets/29f0e865-7ae3-471a-ad70-ca9551041458"> |
| [http://localhost:8080/greeting?name=Vivian](http://localhost:8080/greeting?name=Vivian) | Personalized greeting (`name=User`) | <img width="428" alt="Screenshot 2024-12-03 at 4 55 48 PM" src="https://github.com/user-attachments/assets/7e7eb5ef-1e75-48b7-9025-b3aff860509c"> |

<br />

## Key Terms -- `Greeting.java` ##

`com.example.restservice`:
| **Concept**         | **Description**                                                                 |
|---------------------|---------------------------------------------------------------------------------|
| Package Definition  | The line defines the package the class belongs to (`com.example.restservice`).   |
| Purpose of Packages | Packages are used to organize classes in Java.                                  |
| Directory Structure | The package name typically corresponds to the directory structure where the class file is stored. |

<br />

`public record Greeting(long id, String content) { }`:
| Component               | Description                                                                                                                                         |
|-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| **`public`**             | This is an access modifier, meaning the `Greeting` class can be accessed from any other class.                                                     |
| **`record`**             | A special type of class in Java (introduced in Java 14). A record automatically generates useful methods (like constructor, `equals()`, `hashCode()`, and `toString()`) based on the fields. |
| **`Greeting`**           | The name of the record, which functions as a class in Java.                                                                                        |
| **`(long id, String content)`** | The fields (or components) of the record: `id` (of type `long`) and `content` (of type `String`). These represent the data the record holds. |
| **`{ }`**                | The body of the record. In this case, it is empty, but the Java compiler automatically generates methods like constructor, `toString()`, `equals()`, and `hashCode()` based on the fields. |

<br />

```java
package com.example.restservice;

public record Greeting(long id, String content) { }
```
<br />

## Key Terms -- `GreetingController.java`

### Import Statements
| **Category**  | **Class/Annotation** | **Explanation**                                                                                                      |
|---------------|----------------------|----------------------------------------------------------------------------------------------------------------------|
| **Imports**   | `AtomicLong`          | Provides a thread-safe way to handle long values with atomic operations.                                            |
|               | `GetMapping`          | A Spring annotation used to map HTTP GET requests to a handler method.                                               |
|               | `RequestParam`        | A Spring annotation used to extract query parameters from HTTP requests.                                             |
|               | `RestController`      | A Spring annotation that marks a class as a controller where every method returns a domain object (usually JSON/XML). |

<br />

```java
import java.util.concurrent.atomic.AtomicLong;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;
```
<br />

### Class Declaration
| **Category**                          | **Explanation**                                                                                  |
|---------------------------------------|--------------------------------------------------------------------------------------------------|
| `@RestController`                     | Marks the class as a controller for a RESTful web service. Methods in this class handle HTTP requests and return response bodies directly (often as JSON). |
| `public class GreetingController`     | Declares the class `GreetingController`, which handles the greeting-related HTTP requests.       |

<br />

```java
@RestController
public class GreetingController {
  ...
}
```

<br />

### Static Constant Declaration
| Item              | Description                                                                                      |
|-------------------|--------------------------------------------------------------------------------------------------|
| **Category**      | Field Declaration                                                                                 |
| **Variable Name** | `template`                                                                                        |
| **Type**          | `String`                                                                                          |
| **Value**         | `"Hello, %s!"`                                                                                   |
| **Explanation**   | Declares a static constant string used for formatting greeting messages.                         |
| **Modifiers**     | `static` - Shared among all instances. <br> `final` - The value cannot be changed once initialized.|

<br />

```java
private static final String template = "Hello, %s!";
```

<br />

### Instance Variable Declaration
| Category             | Description                                                                                                                                     |
|----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| Field Declaration    | Declares an instance variable `counter` of type `AtomicLong`.                                                                                   |
| Initialization       | The `AtomicLong` is initialized using the default constructor, starting with a value of 0.                                                      |
| Purpose              | Used to generate a unique ID for each greeting, with values incrementing in a thread-safe manner.                                                 |

<br />

```java
private final AtomicLong counter = new AtomicLong();
```

<br />

### Method Declaration
| Category                        | Explanation                                                                                                                                              |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Method Definition and Annotation | @GetMapping("/greeting"): Maps HTTP GET requests to the /greeting URL path to the `greeting` method.                                                      |
| Method Return Type               | public Greeting greeting(...): The method returns a `Greeting` object.                                                                                  |
| Request Parameter Binding        | @RequestParam(value = "name", defaultValue = "World"): Binds the `name` parameter from the query string to the `name` method parameter. Default is "World".|

<br />

```java
@GetMapping("/greeting")
public Greeting greeting(@RequestParam(value = "name", defaultValue = "World") String name) { ... }
```

<br />

### Method Body
| **Method**                           | **Explanation**                                                                                                                                                                |
|--------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `counter.incrementAndGet()`          | Increments the counter by 1 and returns the updated value, providing a unique ID for each greeting.                                                                             |
| `String.format(template, name)`      | Formats the `template` string using the `name` parameter. For example, if `name` is "Alice", the result would be "Hello, Alice!".                                              |
| `new Greeting(...)`                  | Creates a new `Greeting` object using the incremented counter and the formatted greeting string. Assumes the `Greeting` class has a constructor that accepts an ID and message. |

<br />

```java
return new Greeting(counter.incrementAndGet(), String.format(template, name));
```

<br />

## Key Terms -- `RestServiceApplication.java` ##

### Imports 

| **Category**         | **Description**                                                                                                                                              |
|----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **SpringApplication** | A class that helps in launching a Spring Boot application.                                                                                                  |
| **SpringBootApplication** | A special annotation that marks the main class of a Spring Boot application and enables various features like component scanning, autoconfiguration, and property support. |

<br />

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
```

<br />

### Class Declaration

| Component                       | Description                                                                                       |
|----------------------------------|---------------------------------------------------------------------------------------------------|
| `@SpringBootApplication`         | Annotation used to indicate a Spring Boot application. It enables:                                 |
|                                  | - Component scanning (detecting beans and configurations).                                        |
|                                  | - Auto-configuration (configuring beans automatically based on classpath and properties).         |
|                                  | - Spring Boot's main configuration (e.g., running the application).                               |
| `public class RestServiceApplication` | Declaration of the class that marks `RestServiceApplication` as the main entry point for the application. |

<br />

```java
@SpringBootApplication
public class RestServiceApplication { ... }
```

<br />

### Running the Application

| **Category**                     | **Description**                                                                                                                                               |
|-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Spring Boot Application Runner** | This line starts the Spring Boot application by calling `SpringApplication.run()`.                                                                             |
| **RestServiceApplication.class**  | The main class that serves as the configuration for the Spring Boot application.                                                                               |
| **args**                          | Command-line arguments passed to the `main` method, which are forwarded to Spring Boot’s startup process.                                                      |

<br />

```java
SpringApplication.run(RestServiceApplication.class, args);
```

<br />

## Press the debug button to run

```
  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/

 :: Spring Boot ::                (v3.4.0)

2024-12-03T16:50:35.278-05:00  INFO 3508 --- [greeting] [           main] c.e.restservice.RestServiceApplication   : Starting RestServiceApplication using Java 17.0.13 with PID 3508 (/Users/vivianliu/Desktop/Terms/Autumn_2024/WSA_500/Week_9/greeting/target/classes started by vivianliu in /Users/vivianliu/Desktop/Terms/Autumn_2024/WSA_500/Week_9/greeting)
2024-12-03T16:50:35.280-05:00  INFO 3508 --- [greeting] [           main] c.e.restservice.RestServiceApplication   : No active profile set, falling back to 1 default profile: "default"
2024-12-03T16:50:35.676-05:00  INFO 3508 --- [greeting] [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port 8080 (http)
2024-12-03T16:50:35.685-05:00  INFO 3508 --- [greeting] [           main] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2024-12-03T16:50:35.685-05:00  INFO 3508 --- [greeting] [           main] o.apache.catalina.core.StandardEngine    : Starting Servlet engine: [Apache Tomcat/10.1.33]
2024-12-03T16:50:35.712-05:00  INFO 3508 --- [greeting] [           main] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2024-12-03T16:50:35.713-05:00  INFO 3508 --- [greeting] [           main] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 409 ms
2024-12-03T16:50:35.869-05:00  INFO 3508 --- [greeting] [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port 8080 (http) with context path '/'
2024-12-03T16:50:35.874-05:00  INFO 3508 --- [greeting] [           main] c.e.restservice.RestServiceApplication   : Started RestServiceApplication in 0.789 seconds (process running for 1.093)
2024-12-03T16:50:38.574-05:00  INFO 3508 --- [greeting] [nio-8080-exec-1] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring DispatcherServlet 'dispatcherServlet'
2024-12-03T16:50:38.574-05:00  INFO 3508 --- [greeting] [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : Initializing Servlet 'dispatcherServlet'
2024-12-03T16:50:38.575-05:00  INFO 3508 --- [greeting] [nio-8080-exec-1] o.s.web.servlet.DispatcherServlet        : Completed initialization in 1 ms
```
