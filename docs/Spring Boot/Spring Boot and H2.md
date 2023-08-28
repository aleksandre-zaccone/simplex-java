# **Spring Boot and H2**

# **Project Details**

Project Name: Product Management System

Project Description: A simple system with a REST API to add, update, and remove products from an H2 database.

Tools Used:

* Java 17
    
* Spring Boot 3.1.2
    
* Spring Web
    
* Spring Data JPA
    
* Lombok
    
* H2
    
<br>
# **What is H2 Database**

H2 is a lightweight, open-source, Java-based relational database engine. It is designed to be fast and embeddable, making it an excellent choice for testing and development purposes. One of its notable features is its ability to run in-memory, meaning that data is stored in memory rather than persisted to disk. This makes it extremely fast for temporary data storage and manipulation.

Official Site - [https://www.h2database.com/html/main.html](https://www.h2database.com/html/main.html)

<br>
# **How to set-up and use H2 with Spring boot**

Here's a step-by-step tutorial on how to set up and use the H2 in-memory database with Spring Boot and Java.

You can download the project from Git - [https://github.com/aleksandre-zaccone/SpringBoot-H2-Tutorial](https://github.com/aleksandre-zaccone/SpringBoot-H2-Tutorial)

<br>
## Step 1: Create a Spring Boot Project:

If you don't have a Spring Boot project already, you can create one using Spring Initializr (https://start.spring.io/). Include the necessary dependencies: Spring Web and H2 Database.

## Step 2: Configure H2 Database:

In your application.yml file, add the following H2 database configuration:

```plaintext
Spring:
// This property enables the H2 Database Console. The H2 console is a web-based interface that allows you to interact with the H2 in-memory database.
  h2:
    console:
      enabled: true

/* 
spring.datasource.url: jdbc:h2:mem:ProductManagement - This is the JDBC URL of the H2 database. Here, we are specifying that we want to connect to an H2 in-memory database named "ProductManagement".

spring.datasource.driverClassName: org.h2.Driver - This property specifies the fully qualified class name of the JDBC driver to use. In this case, it's the driver for the H2 database.

spring.datasource.username: sa - This is the username to be used when connecting to the database. In H2, "sa" is the default username for the built-in user.

spring.datasource.password: - This is the password to be used when connecting to the database. For H2 in-memory databases, the password is typically left empty.
*/

  datasource:
    url: jdbc:h2:mem:ProductManagement
    driverClassName: org.h2.Driver
    username: sa
    Password:

/* 
spring.jpa.database-platform: org.hibernate.dialect.H2Dialect - This property sets the Hibernate database dialect for H2. Hibernate is an Object-Relational Mapping (ORM) framework used to interact with databases. The dialect defines how Hibernate generates SQL queries specific to the chosen database.
*/
  jpa:
    database-platform: org.hibernate.dialect.H2Dialect
```

Do not forget to remove all text from the comment section. YAML files do not understand Java comments, and you may encounter errors if you do not remove them.

Upon the application's completion, the H2 database can be explored via the UI at the following console URL: http://localhost:8080/h2-console.

To log in to the H2 database, use the properties from the yaml.file.

![H2 Login UI](https://drive.google.com/uc?id=1HaMxFuGuo3iyZh-oMDtwLUrT6aEMiPor)

![H2 Main UI](https://drive.google.com/uc?id=1fVYEb_b5Vne7koqrA0zSfGUl_A9dEyju)

## Step 3: Create an Entity:

Create a Java class representing an entity that you want to store in the database. For our Application we use Product.class

```java
@AllArgsConstructor
@NoArgsConstructor
@Data
@Builder
@Entity
public class Product {
   @Id
   @GeneratedValue(strategy = GenerationType.IDENTITY)
   private Long id;
   private String name;
   private double price;
}
```

# Step 4: Create a Repository

Create a repository for Create, Read, Update, and Delete operations:

```java
@Repository
public interface ProductRepository extends JpaRepository<Product, Long> {

   Optional<Product> findById(Long id);

   List<Product> findByName(String name);

}
```

## Step 5: Create the Service

Create a service class to implement ProductRepository:

```java
@Service
public class ProductService {

   @Autowired
   private ProductRepository productRepository;

   public List<Product> getAllProducts() {
       return productRepository.findAll();
   }

   public Optional<Product> getProductById(Long id) {
       return productRepository.findById(id);
   }

   public List<Product> getProductsByName(String name) {
       return productRepository.findByName(name);
   }

   public Product saveProduct(Product product) {
       return productRepository.save(product);
   }

   public void deleteProductById(Long id) {
       productRepository.deleteById(id);
   }

}
```

## Step 6: Create the RestController

### Create a RestController with endpoints:

```java
@RestController
@RequestMapping("/api/products")
public class ProductController {

   @Autowired
   private ProductService productService;

   @GetMapping
   public List<Product> getAllProducts() {
       return productService.getAllProducts();
   }

   @GetMapping("/{id}")
   public ResponseEntity<Product> getProductById(@PathVariable Long id) {
       Optional<Product> product = productService.getProductById(id);
       return product.map(ResponseEntity::ok).orElse(ResponseEntity.notFound().build());
   }

   @GetMapping("/search")
   public List<Product> getProductsByName(@RequestParam(name = "name", required = true) String name) {
       return productService.getProductsByName(name);
   }

   @PostMapping
   public Product addProduct(@RequestBody Product product) {
       return productService.saveProduct(product);
   }

   @PutMapping("/{id}")
   public ResponseEntity<Product> updateProduct(@PathVariable Long id, @RequestBody Product product) {
       Optional<Product> existingProduct = productService.getProductById(id);

       if (existingProduct.isPresent()) {
           product.setId(id);
           productService.saveProduct(product);
           return ResponseEntity.ok(product);
       } else {
           return ResponseEntity.notFound().build();
       }
   }

   @DeleteMapping("/{id}")
   public ResponseEntity<Void> deleteProductById(@PathVariable Long id) {
       productService.deleteProductById(id);
       return ResponseEntity.noContent().build();
   }

}
```

This controller provides a simple Create, Read, Update, and Delete (CRUD) API for managing products using Spring Boot and H2.

It includes methods for retrieving all products, retrieving a product by ID, searching for products by name, adding a new product, updating an existing product, and deleting a product by ID.

The @PathVariable annotation is used to retrieve a product by ID, and the @RequestParam annotation is used to search for products by name.

## Step 7: Test API from Postman

### Endpoints:

* GET All Products:
    
    * Method: GET
        
    * URL: http://localhost:8080/api/products
        
* GET Product by ID:
    
    * Method: GET
        
    * URL: http://localhost:8080/api/products/{id}
        
    * Example: http://localhost:8080/api/products/1
        
* GET Products by Name (Search):
    
    * Method: GET
        
    * URL: http://localhost:8080/api/products/search?name={name}
        
    * Example: http://localhost:8080/api/products/search?name=Google%20Fold%20Phone
        
* POST Add Product:
    
    * Method: POST
        
    * URL: http://localhost:8080/api/products
        
    * Headers: Content-Type: application/json
        
    * Body (raw JSON):
```json
{ "name": "Google Fold Phone", "price": 1499.99 }
```

* PUT Update Product by ID:
    * Method: PUT
    * URL: http://localhost:8080/api/products/{id}
    * Example: http://localhost:8080/api/products/1
    * Headers: Content-Type: application/json
    * Body (raw JSON):
```json
{ "name": "Updated Google Fold Phone", "price": 1599.99 }
```


* DELETE Product by ID:
    
    * Method: DELETE
        
    * URL: http://localhost:8080/api/products/{id}
        
    * Example: http://localhost:8080/api/products/1
        

### To use Postman

1. Open Postman.
    
2. Select the appropriate HTTP method (GET, POST, PUT, DELETE).
    
3. Enter the endpoint URL.
    
4. If required, add headers (such as Content-Type: application/json) based on the request.
    
5. Add the request body (for POST and PUT requests) in JSON format.
    
6. Click the "Send" button to make the request.
    

You can customize the examples above based on your specific use case and the actual data you want to send or receive.


