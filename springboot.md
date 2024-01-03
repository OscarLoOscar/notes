step 1.operation 2.controller 3.model 4 service

# Spring Boot Summary
### Application in Spring Boot
- JAVA : STACK / HEAP
- Spring Boot : 
    - 1. Spring Context -> DI / IoC 
    - 2. Request -> Process -> Thread (@Async)

### All technique knowledge in Spring Boot ,  Annotation (MVC)
- @RestController /@Service / @Repository / @Configuration(管理Bean) -> @Component ( Inject a Bean into context )
- @RestController ： RESTful Api ,
    - @pathVariable , @RequestParm , @RequestBody
    - ResponseEntity\<T>
    -  Define API URI path
    -  Call service layer
- @Service  // Bean -> new ProductServiceHolder() -> Spring Context
  - Business logic (Serve Business , Not Consumer)
- @Repository (after 3.0 , no longer need)
  - Jpa / Hibernate -> H2/MySQL/PostgreSQL
  - Work woth Entity or Database (save & saveAndFlush)
  
- @Configuration -> @Bean
  - Self construct Beans to context before application startup
- @Autowird
  - Decoupling controller / service / repository
  - inject Bean from context to object reference
- Jpa @Entity -> @OneToMany , @ManyToOne ,@ManyToMany
  - Jpa is to help manage SQLs to be fired in DB,considering the table relationship(i.e. primary/foriegn key)
  - @Query(native = true , Native Query = Normal SQL)
  - @Query(native = false, JPQL)
- Mybatis (vs Jpa / Hiberate)
  - Non-Hiberate framwork , which just fire the hard-coded SQL one by one 
- AOP (Aspect-oriented programming)(@RestControllerAdvice)
  - Global Exception Handler(to grab exception thrown by methods)
- Libray (ApiResponse/ BusinessException , enum ,etc)
  - Reusable
- ResTtemplate
  - REST API call(get/post),return  T object
- RedisTtemplate
  - Work with Cache memory product (redis)
  - put(),get()
- Test (Junit5 -> Unit Test)
  - Why test case?
    - Regression in day 2 project(main reason)
    - 1 developer work on the same project to avoid careless/bugs
    - TDD(Test Driven Design),Test Case First,before main code
  - @SpringBootTest 
    - full load all bean like main code for the test cases in class level
  - @WebMvcTest(@MockMvc)
    - Load web related , controller , etc.To test api , like postman 
  - @DataJpaTest
    - Load DataSource related beans, to test Jpa methods .
  - @Mock
    - when method A call ClassB.Method B , we freeze the result of Method B , to focus on Method A Unit test
  - @MockBean
    -   @To test "@Autowird" process in main code (Controller autowired Service)
  - @InjectMock ,   @InjectMocks  automatically able to refer objected being @Mock , automatically able to refer objected being @Mock

    - When Class A  to call a Mocked Class B , we will use @InjectMock for class A
    - 
 - static import 
  - Assertions(assertEquals)
    - to check expectedValue (left) vs actualValue (right)
  - hamcrest(assertThat)
    - Matchers
- Maven
  -  \<parent>,\<dependencies>,\<plugins>
  - spring boot starter
  - mvn clean,comiple/test/install
  - manage jar version
  - concept of extends , child override parent
- API documentation
  - swagger2 (springfox framwork,@EnableSeagger2)
    - an interface to present the APIs inside the App
  - OpenAPI3 (@Operations , @APIResponses , @Parameters , etc)
      - an interface to present the APIs inside the 
      - /apidocs -> JSON -> Convery to YAML -> CodeGen (Design First)
- Validation (@Valid -> @RequestBody)
  - @Size,@Max,@Min
  - Custom annotation -> Validator -> build custom logic for valid object 
- ScheduledTask
  - self create process /thread to do something (API / calculation ,etc)
    - @ScheduledTask(cron),setup SSMM24HH DDMONYY
- Dto(ModelMapper)
  - Deal with requirement from consumer
- Lombok
- ObjectMapper (Deserialization / serialization) 
  - readValue (Method to deserialize JSON content from given JSON content String.)
  - writeValueAsString(Method that can be used to serialize any Java value as a String. Functionally equivalent to calling writeValue(Writer, Object) with java.io.StringWriter and constructing String, but more efficient.)



