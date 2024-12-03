## SprintBoot_Greetings

<br />

## Test your local host
| Link                                     | Description                       | Output Screenshot                |
|------------------------------------------|-----------------------------------|----------------------------------|
| [http://localhost:8080/greeting](http://localhost:8080/greeting)             | Default greeting                  | <img width="362" alt="Screenshot 2024-12-03 at 4 55 04 PM" src="https://github.com/user-attachments/assets/29f0e865-7ae3-471a-ad70-ca9551041458"> |
| [http://localhost:8080/greeting?name=Vivian](http://localhost:8080/greeting?name=Vivian) | Personalized greeting (`name=User`) | <img width="428" alt="Screenshot 2024-12-03 at 4 55 48 PM" src="https://github.com/user-attachments/assets/7e7eb5ef-1e75-48b7-9025-b3aff860509c"> |


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
