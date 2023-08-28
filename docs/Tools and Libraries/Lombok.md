
#lombok #java
# What is Lombok

Java is a powerful programming language, but sometimes it requires a lot of words to do simple things. This can make your code long and repetitive, especially when you have to do things like creating `getters` and `setters`. This extra code doesn't really help your program do its main job. Writing this kind of code is not only boring but also takes up a lot of time. To fix this problem, we can use special tools and libraries that make it easier and faster to write code. And that's where Lombok comes in!

Lombok is a helpful tool for Java that solves the problem of writing the same code over and over. It does this by using special notes (called annotations) so you don't have to write common code that's usually repeated and takes a lot of time. Lombok works with your code and creates the necessary building blocks automatically based on these annotations. This means you can avoid making certain parts of your code, like constructors, equals, and hashCode functions, which saves you a lot of time. It lets you focus more on the important parts of your project. Plus, using Lombok keeps your code neat, tidy, and easier to read and work with.

# Install Lombok

We can install Lombok in different ways:
- manually  - add dependency int the project for Maven or Gradle
- via Lombok plugin - add Lombok plugin if you use IntelliJ IDEA
Lombok requires annotation processing to work properly. Make sure that annotation processing is enabled in your IDE or build tool settings.

# Lombok Annotations

Let's take a look at some of the most frequently used Lombok annotations. I'll provide an explanation for each annotation, along with a comparison to the equivalent Java code. 
If you want to explore more detailed examples and get additional support, you can click on each annotation to visit its page in the official Lombok documentation.

## @Getter and @Setter 
Let's dive into the `@Getter` and `@Setter` annotations. When you apply the `@Getter` annotation to a field, like "cardNumber," Lombok will automatically generate a method called `getCardNumber()`. This method simply retrieves the value stored in the "cardNumber" field.

On the other hand, when you use the `@Setter` annotation on the "cardNumber" field, Lombok will create a corresponding setter method called `setCardNumber()`. This setter method takes a parameter of the same type as the "cardNumber" field and assigns it to the field.

By default, these generated getter and setter methods are public, but you have the flexibility to adjust their access level. For instance, you can set them to be protected using AccessLevel, like:

1. `AccessLevel.PUBLIC`: The generated methods and fields will have public visibility, accessible from anywhere.
2. `AccessLevel.PRIVATE`: The generated methods and fields will have private visibility, accessible only within the same class.
3. `AccessLevel.PROTECTED`: The generated methods and fields will have protected visibility, accessible within the same package and subclasses.
4.  `AccessLevel.PACKAGE`: The generated methods and fields will have package-private visibility, accessible within the same package.
5.  `AccessLevel.MODULE`: The generated methods and fields will have module visibility, accessible within the same module.
6. `AccessLevel.NONE`: No method or field is generated.

Remember, these annotations aren't limited to individual fields. You can also apply them at the class level, which results in the automatic creation of getter and setter methods for all fields within the class. This streamlined approach not only reduces boilerplate code but also enhances the readability and maintainability of your Java code.

Example with Lombok:
```java
@Getter
@Setter
public class CreditCard {
    private int cardNumber;
    private String cardHolderName;
    @Setter(AccessLevel.PROTECTED)
    private String expirationDate;
}
```

Example without Lombok:
```java
public class CreditCard {
    private int cardNumber;
    private String cardHolderName;
    private String expirationDate;

    public int getCardNumber() {
        return cardNumber;
    }

    public void setCardNumber(int cardNumber) {
        this.cardNumber = cardNumber;
    }

    public String getCardHolderName() {
        return cardHolderName;
    }

    public void setCardHolderName(String cardHolderName) {
        this.cardHolderName = cardHolderName;
    }

    public String getExpirationDate() {
        return expirationDate;
    }

    protected void setExpirationDate(String expirationDate) {
        this.expirationDate = expirationDate;
    }
}
```


## @NoArgsConstructor, @AllArgsConstructor and  @RequiredArgsConstructor
When you use the `@NoArgsConstructor` annotation, it generates a constructor without any parameters. Conversely, by applying `@AllArgsConstructor`, a constructor is produced with parameters that match each field in the class. 
Meanwhile, `@RequiredArgsConstructor` creates a constructor customized for fields needing special handling – like non-initialized final fields or fields marked as `@NonNull` but not initialized in their declaration. Notably, these annotations don't affect static fields.

Example with Lombok:
```java
@NoArgsConstructor
@AllArgsConstructor
@RequiredArgsConstructor
public class CreditCard {
    private int cardNumber;
    private String cardHolderName;
    private String expirationDate;
    private final String bankName;
}
```

Example without Lombok:
```java
public class CreditCard {
    private int cardNumber;
    private String cardHolderName;
    private String expirationDate;
    private final String bankName;

    public CreditCard() {
    }

    public CreditCard(int cardNumber, String cardHolderName, String expirationDate, String bankName) {
        this.cardNumber = cardNumber;
        this.cardHolderName = cardHolderName;
        this.expirationDate = expirationDate;
        this.bankName = bankName;
    }

    public CreditCard(String bankName) {
        this.bankName = bankName;
    }
}
```

## @ToString
The `@ToString` annotation generates the `toString()` method, simplifying object printing. 

Example with Lombok: 
```java 
@ToString 
public class CreditCard { 
	private String cardNumber; 
	private String cardholderName; 
	private String expirationDate; 
	}
```

Example without Lombok:
```java
public class CreditCard { 
	private String cardNumber; 
	private String cardholderName; 
	private String expirationDate; 
	
	@Override public String toString() { 
	return "CreditCard(cardNumber=" + this.cardNumber + ", cardholderName=" 
	+ this.cardholderName + ", expirationDate=" + this.expirationDate + ")"; 
	} 
}
```


## @EqualsAndHashCode
The `@EqualsAndHashCode` annotation can be applied to any class definition, enabling Lombok to automatically generate implementations of the `equals(Object other)` and `hashCode()` methods. By default, these generated methods consider all non-static, non-transient fields. However, you have the flexibility to tailor this behavior using two primary options.
1. Using `@EqualsAndHashCode.Include` and `@EqualsAndHashCode.Exclude`: These annotations can be selectively applied to specific type members, allowing you to include or exclude fields or methods from the generated `equals` and `hashCode` calculations.
    
2. Using `@EqualsAndHashCode(onlyExplicitlyIncluded = true)` and `@EqualsAndHashCode.Include`: This combination allows you to precisely specify the fields or methods to be included in the generated methods.

Example with Lombok:
```java
@Getter
@Setter
@AllArgsConstructor
@NoArgsConstructor
@EqualsAndHashCode 
public class CreditCard { 
	private String cardNumber; 
	private String cardholderName; 
	private String expirationDate; }
```

Example without Lombok:
```java
public class CreditCard {
    private String cardNumber;
    private String cardholderName;
    private String expirationDate;

    public CreditCard(String cardNumber, String cardholderName, String expirationDate) {
        this.cardNumber = cardNumber;
        this.cardholderName = cardholderName;
        this.expirationDate = expirationDate;
    }

    public String getCardNumber() {
        return cardNumber;
    }

    public void setCardNumber(String cardNumber) {
        this.cardNumber = cardNumber;
    }

    public String getCardholderName() {
        return cardholderName;
    }

    public void setCardholderName(String cardholderName) {
        this.cardholderName = cardholderName;
    }

    public String getExpirationDate() {
        return expirationDate;
    }

    public void setExpirationDate(String expirationDate) {
        this.expirationDate = expirationDate;
    }

    @Override
    public int hashCode() {
        final int prime = 31;
        int result = 1;
        result = prime * result + ((cardNumber == null) ? 0 : cardNumber.hashCode());
        result = prime * result + ((cardholderName == null) ? 0 : cardholderName.hashCode());
        result = prime * result + ((expirationDate == null) ? 0 : expirationDate.hashCode());
        return result;
    }

    @Override
    public boolean equals(Object obj) {
        if (this == obj)
            return true;
        if (obj == null || getClass() != obj.getClass())
            return false;
        CreditCard other = (CreditCard) obj;
        return Objects.equals(cardNumber, other.cardNumber) &&
               Objects.equals(cardholderName, other.cardholderName) &&
               Objects.equals(expirationDate, other.expirationDate);
    }
}
```

If applying `@EqualsAndHashCode` to a class that extends another, this feature gets a bit trickier. Normally, auto-generating an `equals` and `hashCode` method for such classes is a bad idea, as the superclass also defines fields, which also need equals/hashCode code but this code will not be generated. For more details  check this [documentation](https://projectlombok.org/features/EqualsAndHashCode).

## @NonNull
The `@NonNull` annotation generates null-checks for constructor parameters.

Example with Lombok:
```java
public class CreditCard {     
	private String cardNumber;     
	private String cardholderName;     
	private String expirationDate;      
	
	public CreditCard(@NonNull String cardNumber, @NonNull String cardholderName, String expirationDate) {
	     this.cardNumber = cardNumber;         
	     this.cardholderName = cardholderName;         
	     this.expirationDate = expirationDate;     } }`
```

Example without Lombok:
```java
public class CreditCard {     
	private String cardNumber;     
	private String cardholderName;     
	private String expirationDate;
	
	public CreditCard(String cardNumber, String cardholderName, String expirationDate) {
		if (cardNumber == null || cardholderName == null) {
			throw new NullPointerException("cardNumber or cardholderName is marked @NonNull but is null");         
			}         
		this.cardNumber = cardNumber;         
		this.cardholderName = cardholderName;         
		this.expirationDate = expirationDate;     
		} 
}
```

## @Data
The `@Data` annotation combines `@ToString`, `@EqualsAndHashCode`, `@Getter`, `@Setter`, and `@RequiredArgsConstructor`.

With Lombok:
```java
@Data 
public class CreditCard {     
	private final String cardNumber;     
	private String cardholderName;     
	private String expirationDate; 
```

Example without Lombok:
```java
public class CreditCard {     
	private final String cardNumber;     
	private String cardholderName;     
	private String expirationDate;   
	   
	public CreditCard(String cardNumber) {         
		this.cardNumber = cardNumber;     
		}      
	// Getters and setters 
	     
	@Override     
	public int hashCode() {         
	// hashCode implementation     
	}     
	
	@Override     
	public boolean equals(Object o) {         
	// equals implementation     } }`

```

## @Value
The annotation `@Value` represents the immutable version of `@Data`. By default, Lombok designates all fields as private and final. It omits the generation of setters and declares the class as final, preventing inheritance. Much like `@Data`, it also generates implementations for `toString()`, `equals()`, and `hashCode()`.

Example with Lombok:
```java
@Data 
public class CreditCard { 
	private String cardNumber; 
	private String cardHolderName; 
	private String expirationDate; 
	}
```

Example without Lombok:
```java
public final class CreditCard {
    private final String cardNumber;
    private final String cardHolderName;
    private final String expirationDate;

    public CreditCard(String cardNumber, String cardHolderName, String expirationDate) {
        this.cardNumber = cardNumber;
        this.cardHolderName = cardHolderName;
        this.expirationDate = expirationDate;
    }

    public String getCardNumber() {
        return cardNumber;
    }

    public String getCardHolderName() {
        return cardHolderName;
    }

    public String getExpirationDate() {
        return expirationDate;
    }

    @Override 
    public int hashCode() {
        final int PRIME = 31;
        int result = 1;
        result = prime * result + ((getCardNumber() == null) ? 0 : getCardNumber().hashCode());
        result = prime * result + ((getCardHolderName() == null) ? 0 : getCardHolderName().hashCode());
        result = prime * result + ((getExpirationDate() == null) ? 0 : getExpirationDate().hashCode());
        return result;
    }

    @Override 
    public boolean equals(Object o) {
        if (o == this) return true;
        if (!(o instanceof CreditCard)) return false;
        CreditCard other = (CreditCard) o;
        if (!other.canEqual((Object)this)) return false;
        if (this.getCardNumber() == null ? other.getCardNumber() != null : !this.getCardNumber().equals(other.getCardNumber())) return false;
        if (this.getCardHolderName() == null ? other.getCardHolderName() != null : !this.getCardHolderName().equals(other.getCardHolderName())) return false;
        if (this.getExpirationDate() == null ? other.getExpirationDate() != null : !this.getExpirationDate().equals(other.getExpirationDate())) return false;
        return true;
    }
}
```


## @SneakyThrows
The `@SneakyThrows` annotation enables you to throw checked exceptions without explicitly declaring them in your method's `throws` clause, as you normally would. This annotation allows you to sidestep the need for mandatory `try-catch` blocks by handling checked exceptions silently. It's important to note that Lombok doesn't disregard, wrap, replace, or modify the thrown checked exception. Instead, it tricks the compiler. This works because, at the level of the JVM (Java Virtual Machine) class file, all exceptions can be thrown regardless of the `throws` clause in your methods. However, it's crucial to exercise caution when using this annotation, as it can be risky. 
For detailed guidance on when and how to use it, refer to [this](https://projectlombok.org/features/SneakyThrows) page in the official Lombok documentation.

Example with Lombok:
```java
import lombok.SneakyThrows;

public class SneakyThrowsDemo {
    public static void main(String[] args) {
        try {
            doSomething();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    @SneakyThrows
    public static void doSomething() {
        throw new Exception("An exception occurred");
    }
}

```

Example without Lombok:
```java
public class SneakyThrowsDemo {
    public static void main(String[] args) {
        try {
            doSomething();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    public static void doSomething() {
        try {
            throw new Exception("An exception occurred");
        } catch (Exception e) {
            // Handle or log the exception here
            e.printStackTrace();
        }
    }
}
```
In this version, without the `@SneakyThrows` annotation, we manually surround the exception-throwing code with a `try-catch` block within the `doSomething()` method. This is to handle the checked exception `Exception` that is thrown.

## [`@Builder`](https://projectlombok.org/features/Builder)
When you're faced with the task of creating objects following a step-by-step construction pattern, like `CreditCard.builder().cardNumber("1234567890123456").cardholderName("John Doe").expirationDate("12/24").build();`, the `@Builder` annotation can come in handy. This becomes especially beneficial when dealing with classes that have numerous fields. Rather than using a constructor with an abundance of parameters, this approach provides a more readable alternative. By incorporating the `@Builder` annotation, you delegate the task of generating builders to Lombok.

Applying the `@Builder` annotation to a class triggers Lombok to generate a class that adheres to the builder pattern mentioned earlier. For instance, if you annotate the `CreditCard` class, Lombok automatically produces a `CreditCardBuilder` class. Since your builder's behavior could be intricate or highly customized, Lombok provides several parameters to help you achieve your desired outcome. You can explore all these parameters [here](https://projectlombok.org/features/Builder).

Example with Lombok:
```java
@Builder
public class CreditCard {
    private String cardNumber;
    private String cardholderName;
    private String expirationDate;
}

public class Main {
    public static void main(String[] args) {
        CreditCard creditCard = CreditCard.builder()
            .cardNumber("1234567890123456")
            .cardholderName("John Doe")
            .expirationDate("12/24")
            .build();
    }
}
```

Example without Lombok:
```java
public class CreditCard {
    private String cardNumber;
    private String cardholderName;
    private String expirationDate;

    public CreditCard(String cardNumber, String cardholderName, String expirationDate) {
        this.cardNumber = cardNumber;
        this.cardholderName = cardholderName;
        this.expirationDate = expirationDate;
    }

    // Getters and setters...
}

public class CreditCardBuilder {
    private String cardNumber;
    private String cardholderName;
    private String expirationDate;

    public CreditCardBuilder cardNumber(String cardNumber) {
        this.cardNumber = cardNumber;
        return this;
    }

    public CreditCardBuilder cardholderName(String cardholderName) {
        this.cardholderName = cardholderName;
        return this;
    }

    public CreditCardBuilder expirationDate(String expirationDate) {
        this.expirationDate = expirationDate;
        return this;
    }

    public CreditCard build() {
        return new CreditCard(cardNumber, cardholderName, expirationDate);
    }
}

public class Main {
    public static void main(String[] args) {
        CreditCard creditCard = new CreditCardBuilder()
            .cardNumber("1234567890123456")
            .cardholderName("John Doe")
            .expirationDate("12/24")
            .build();
    }
}

```
As you can see, Lombok's `@Builder` simplifies the creation of builder classes, reducing the boilerplate code and enhancing readability.

## [`@Log`](https://projectlombok.org/features/log)
Setting up a logger instance in each class for logging purposes is a common practice, often involving repetitive code. However, Lombok's `@Log` annotation offers a solution. When you annotate a class with `@Log`, Lombok takes care of generating a static final `log` field within the class. 
This field is initialized according to your chosen logging library's requirements. Lombok provides a dedicated annotation for several popular logging frameworks, making it convenient for developers. 
Example:
- `@Log` - creates `private static final java.util.logging.Logger log = java.util.logging.Logger.getLogger(LogExample.class.getName());`
- `@Log4j2` - creates `private static final org.apache.logging.log4j.Logger log = org.apache.logging.log4j.LogManager.getLogger(LogExample.class);`
- `@Slf4j` - `creates private static final org.slf4j.Logger log = org.slf4j.LoggerFactory.getLogger(LogExample.class);`

The complete list of supported frameworks can be found [here](https://projectlombok.org/features/log).


# Lombok additional Info

Official site - https://projectlombok.org/

Lombok tutorials:
- [Java Lombok Tutorial by Amigoscode](https://www.youtube.com/watch?v=z7bsNF2Dtf0)

