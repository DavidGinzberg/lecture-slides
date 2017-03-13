# Dependency Injection

-
### What does DI do?

- Decouple component creation and use
- Allow runtime selection of resources/services
- Leaves component selection up to the container

-
### Inversion of Control

Container/framework handles generic tasks (windows, http requests & responses) and calls custom code in response to events.

Inverted from the traditional model: bespoke code for every menu, handled request, choreographed run-through etc.

-
### Injection in Spring

- Use the `@Autowired` annotation to inject dependencies (beans) in classes, fields, constructors
- Similar to `@Inject` in Java EE [JSR-330](https://jcp.org/en/jsr/detail?id=330)
- Many frameworks have their own injection eg: `Mockito::@InjectMocks`

-
### Bean Injection

- Beans are used to satisfy dependencies
- `@Bean` creates a bean from methods in a `@configuration` class

-
### Components

- Class marked by `@Component` or one of its stereotypes
- Automatically maps to a bean when `@ComponentScan` is present
- Stereotypes: `@Repository`, `@Service`, `@Controller`
- `@Configuration` is also a type of Component


-
### Injection rules

- Only beans can be injected automatically
- Values can be injected but [must be specified](http://stackoverflow.com/questions/317687/how-can-i-inject-a-property-value-into-a-spring-bean-which-was-configured-using#339811)
- Decide between multiple compatible beans with `@Primary` or `@Qualifier`
- Injected beans are singletons by default; other scopes are available



-
### Related concepts

- Inversion of Control (IoC)
- Java EE Containers


-
### Resources

- [Martin Fowler on DI](http://martinfowler.com/articles/injection.html)
- [Spring IoC Container](http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#beans)
- [Spring Boot Dependency Injection](http://docs.spring.io/spring-boot/docs/1.4.1.RELEASE/reference/htmlsingle/#using-boot-spring-beans-and-dependency-injection)
- [Oracle Java EE 7 CDI Tutorial](https://docs.oracle.com/javaee/7/tutorial/partcdi.htm#GJBNR)