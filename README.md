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
