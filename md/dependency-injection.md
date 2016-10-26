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
### Injection

- Use the `@Inject` annotation to inject dependencies in classes, fields, constructors
- Many frameworks have their own injection eg: `Spring::@Autowired` `Mockito::@InjectMocks`

-
### Injection rules

- Only beans can be injected
- Differentiate between beans using qualifiers, `@named`, or `@alternative` with XML configuration
- Injection occurs within the specified scope & context (If unspecified, it is `@Dependent`)

-
### Container Managed Beans:

- Must have no-arg constructor or `@Inject` annotation
- Must be top-level concrete class or have `@Decorate` annotation
- Cannot be nonstatic inner classes
- Cannot be defined as EJB
- Are not annotated as `@Vetoed`

-
### JSF & JSP

- They exist
- They are old, mostly deprecated, but not entirely dead
- Some of this is relevant to them
- Look it up when you need it

-
### Related concepts

- Inversion of Control (IoC)
- Frameworks
- Java EE Containers


-
### Resources

- [Martin Fowler on DI](http://martinfowler.com/articles/injection.html)
- [Spring IoC Container](http://docs.spring.io/spring/docs/current/spring-framework-reference/htmlsingle/#beans)
- [Spring Boot Dependency Injection](http://docs.spring.io/spring-boot/docs/1.4.1.RELEASE/reference/htmlsingle/#using-boot-spring-beans-and-dependency-injection)
- [Oracle Java EE 7 CDI Tutorial](https://docs.oracle.com/javaee/7/tutorial/partcdi.htm#GJBNR)