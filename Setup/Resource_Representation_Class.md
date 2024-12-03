## Create a Resource Representation Class

Link: https://spring.io/guides/gs/rest-service

<br />

Path of ```Greeting.java``` file: ```src/main/java/com/example/restservice/Greeting.java```
* Create a new folder named ```restservice``` under ```example``` directory
* Then paste the code to the ```Greeting.java```:

```java
package com.example.greeting;

public record Greeting(long id, String content) { }
```

<br />

## Create a Resource Controller
In Spring’s approach to building RESTful web services, HTTP requests are handled by a controller. 

<br />

Path of ```GreetingController.java``` file: ```src/main/java/com/example/restservice/GreetingController.java```

```java
package com.example.restservice;

import java.util.concurrent.atomic.AtomicLong;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GreetingController {

	private static final String template = "Hello, %s!";
	private final AtomicLong counter = new AtomicLong();

	@GetMapping("/greeting")
	public Greeting greeting(@RequestParam(value = "name", defaultValue = "World") String name) {
		return new Greeting(counter.incrementAndGet(), String.format(template, name));
	}
}
```

<br />

## Run the Service

Path of ```RestServiceApplication.java``` file: ```src/main/java/com/example/restservice/RestServiceApplication.java```

```java
package com.example.restservice;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class RestServiceApplication {

	public static void main(String[] args) {
		SpringApplication.run(RestServiceApplication.class, args);
	}
}
```

<br />

## Click "Run and Debug" to run

Link: http://localhost:8080/greeting

<br />

Return output:
```json
{"id":1,"content":"Hello, World!"}
```








