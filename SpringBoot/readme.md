## 🚀 **Spring Boot Interview Preparation (Beginner to Intermediate)**  

Agar aap **Spring Boot ka job interview** dene wale hain, to ye **detailed guide** aapko **best preparation** karne me madad karegi.  

---

# **📌 What is Spring Boot?**
### **1️⃣ Spring Boot kya hai?**
✅ **Spring Boot ek Java-based framework hai** jo **Spring Framework** ka part hai.  
✅ Ye **microservices development** aur **standalone applications** banane ke liye use hota hai.  
✅ **Main features:**  
   - **Auto Configuration** → Manual configuration ki zaroorat nahi.  
   - **Embedded Servers** → Tomcat, Jetty, Undertow pre-configured hote hain.  
   - **Production-Ready Features** → Metrics, health checks, logging, monitoring, etc.  

---

# **📌 Key Features of Spring Boot**
### **2️⃣ Spring Boot ke Benefits kya hain?**
✅ **1. Easy Configuration** → XML-based configuration ki zaroorat nahi.  
✅ **2. Standalone Applications** → `main()` method ke through application run hoti hai.  
✅ **3. Embedded Servers** → Inbuilt Tomcat, Jetty, Undertow.  
✅ **4. Microservices Development** → Cloud-based applications ke liye best hai.  
✅ **5. Spring Boot Starter Dependencies** → `spring-boot-starter-web`, `spring-boot-starter-data-jpa`, etc.  
✅ **6. Spring Boot Actuator** → Health check, monitoring, logging.  

---

# **📌 Spring Boot Architecture**
### **3️⃣ Spring Boot Architecture kya hai?**
✅ **Layers in Spring Boot Application:**  
- **Presentation Layer** → Controllers handle requests.  
- **Service Layer** → Business logic.  
- **Repository Layer (DAO Layer)** → Database interaction.  
- **Database Layer** → H2, MySQL, PostgreSQL, etc.  

📌 **Spring Boot MVC Example:**  
```java
@RestController
@RequestMapping("/users")
public class UserController {
    
    @GetMapping("/{id}")
    public String getUser(@PathVariable int id) {
        return "User ID: " + id;
    }
}
```
👉 **Yahaan `/users/{id}` API ek User ka data return karegi.**  

---

# **📌 Spring Boot Key Annotations**
### **4️⃣ Important Annotations in Spring Boot**
| Annotation | Description |
|------------|------------|
| `@SpringBootApplication` | Spring Boot application start karne ke liye. |
| `@RestController` | REST API create karne ke liye. |
| `@RequestMapping` | Request URL mapping ke liye. |
| `@GetMapping`, `@PostMapping` | HTTP GET aur POST requests ke liye. |
| `@Autowired` | Dependency Injection ke liye. |
| `@Service` | Service layer define karne ke liye. |
| `@Repository` | Database interaction ke liye. |
| `@Entity` | JPA Entity define karne ke liye. |
| `@Table(name="users")` | Database table name specify karne ke liye. |

📌 **Example:**  
```java
@Service
public class UserService {
    public String getUserName() {
        return "John Doe";
    }
}
```
```java
@RestController
public class UserController {
    @Autowired
    private UserService userService;

    @GetMapping("/username")
    public String getUsername() {
        return userService.getUserName();
    }
}
```
👉 **Is API se `/username` call karne pe `John Doe` return hoga.**  

---

# **📌 Spring Boot Configuration**
### **5️⃣ Spring Boot `application.properties` Configuration**
✅ **Spring Boot me `application.properties` ya `application.yml` ka use hota hai.**  
✅ **Database Configuration Example:**
```properties
server.port=8081
spring.datasource.url=jdbc:mysql://localhost:3306/mydb
spring.datasource.username=root
spring.datasource.password=root
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```
👉 **Yahaan humne database ka URL, username, password aur Hibernate properties define ki hain.**  

---

# **📌 Spring Boot with Database**
### **6️⃣ Spring Boot + JPA + MySQL**
📌 **Entity Example:**  
```java
@Entity
@Table(name="users")
public class User {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
    private String name;
    private String email;
}
```
📌 **Repository Example:**  
```java
@Repository
public interface UserRepository extends JpaRepository<User, Long> {
}
```
📌 **Service Example:**  
```java
@Service
public class UserService {
    @Autowired
    private UserRepository userRepository;

    public List<User> getAllUsers() {
        return userRepository.findAll();
    }
}
```
📌 **Controller Example:**  
```java
@RestController
@RequestMapping("/users")
public class UserController {
    @Autowired
    private UserService userService;

    @GetMapping
    public List<User> getUsers() {
        return userService.getAllUsers();
    }
}
```
👉 **Ye API `/users` call karne pe database se users ka data fetch karegi.**  

---

# **📌 Spring Boot Security**
### **7️⃣ Spring Boot Security + JWT Authentication**
✅ **Spring Security use karne ke liye `spring-boot-starter-security` dependency use hoti hai.**  
✅ **JWT (JSON Web Token) ka use authentication ke liye hota hai.**  

📌 **Basic Security Example:**  
```java
@Configuration
@EnableWebSecurity
public class SecurityConfig {
    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http.authorizeHttpRequests(auth -> auth
                .requestMatchers("/public/**").permitAll()
                .anyRequest().authenticated()
        )
        .formLogin(Customizer.withDefaults());
        return http.build();
    }
}
```
👉 **Isme `/public/**` sabko accessible hai, lekin baaki sab authorized users ke liye hai.**  

---

# **🔥 Spring Boot Interview Questions (Beginner to Intermediate)**
| # | Question | Answer |
|---|---------|---------|
| 1 | Spring Boot kya hai? | Ye Spring Framework ka ek extension hai jo Java applications ko build aur deploy karna easy banata hai. |
| 2 | Spring Boot vs Spring Framework me kya difference hai? | Spring Boot me auto-configuration, embedded server, aur opinionated defaults hote hain, jabki Spring me manual configuration karni padti hai. |
| 3 | `@SpringBootApplication` annotation ka kya kaam hai? | Ye `@Configuration`, `@EnableAutoConfiguration`, aur `@ComponentScan` ka combination hai. |
| 4 | Spring Boot me Embedded Server kya hota hai? | Spring Boot Tomcat, Jetty, Undertow jaise embedded servers ke saath aata hai, jisse external server configure karne ki zaroorat nahi hoti. |
| 5 | Spring Boot me `application.properties` ka kya role hai? | Ye application configuration settings store karne ke liye use hota hai, jaise database connection, logging, etc. |
| 6 | JPA aur Hibernate me kya difference hai? | JPA ek specification hai, jabki Hibernate JPA ka ek implementation hai. |
| 7 | Spring Boot me Dependency Injection ka kya use hai? | Dependency Injection Spring container ko objects manage karne ki suvidha deta hai. |
| 8 | `@RestController` aur `@Controller` me kya difference hai? | `@RestController` sirf REST API return karta hai, jabki `@Controller` HTML pages bhi return kar sakta hai. |
| 9 | Spring Boot Security ka use kya hai? | Ye authentication aur authorization provide karta hai, jisme JWT, OAuth, aur Basic Auth included hote hain. |

---

## **🔥 Final Preparation Tips**
✅ **Spring Boot projects practice karein**  
✅ **Annotations aur concepts ko achhe se samjhein**  
✅ **REST API, Security, JPA aur Actuator explore karein**  
✅ **Interview ke liye mock tests aur coding exercises karein**  

Agar aapko kisi **specific topic par aur detail chahiye** to bata sakte hain! 🚀🔥
