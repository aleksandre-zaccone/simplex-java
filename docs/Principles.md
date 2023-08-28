# **Principles** 
# **Software Development Principles and Best Practice**
## <u>DRY  - Don’t Repeat Yourself</u>
Reduce redundancy by ensuring that each piece of knowledge or logic has a single, authoritative representation within a codebase. 
In other words, every piece of information or functionality should exist in only one place in your software.

The DRY principle aims to eliminate duplicated code, data, or design in a project. By adhering to this principle, you can achieve several benefits:

1. **Code Re-usability:** When logic is centralized and not duplicated, it becomes easier to reuse that code in multiple parts of your application, reducing the need to rewrite the same code.
2. **Consistency:** Changes or updates need to be made in only one place, ensuring that the behavior remains consistent across the application.
3. **Maintenance:** Having a single source of truth reduces the chances of introducing bugs due to inconsistencies between duplicated code sections.
4. **Readability and Understandability:** Developers can more easily understand and navigate the codebase when there's no redundancy, leading to improved collaboration and faster on-boarding for new team members.
5. **Efficiency:** DRY code tends to be more efficient to manage and maintain over time, as you don't have to remember or update multiple occurrences of the same logic.

## <u>KISS - Keep It Simple Stupid</u>

The basic idea is to favor straightforward solutions that are easy to understand, maintain, and troubleshoot, rather than overly complex ones.

1. **Simplicity:** Aim for the simplest solution that effectively solves the problem. Avoid unnecessary complexity and convoluted designs.
2. **Clarity:** Make your code, architecture, and user interfaces clear and easy to understand. Avoid obscure or confusing structures that might hinder comprehension.
3. **Maintenance:** Simple solutions are often easier to maintain and debug. Complex solutions can become difficult to modify or fix, leading to increased development time and potential errors.
4. **Efficiency:** Complexity can introduce performance bottlenecks and increase resource usage. A simpler solution can often be more efficient and have better performance.
5. **Accessibility:** A simple design is more accessible to other developers, allowing for easier collaboration and knowledge sharing.
6. **User Experience:** In user interfaces, prioritize simplicity and ease of use. Overly complex interfaces can confuse users and lead to frustration.


## <u>SOLID</u>
 - **S - Single Responsibility Principle** - Every class or module should come with its own responsibility for a single part of the feature offered in the software. 
- **O - Open/Closed Principle** - Software entities like functions, modules, or classes must be closed for modification but open for extension.
- **L - Liskov Substitution Principle** - It means that objects of a derived (child) class should be able to replace objects of the parent class without affecting the correctness of the program.
- **I - Interface Segregation Principle** - Clients (classes that use interfaces) should not be forced to implement interfaces they do not use. In other words, it's better to have multiple small, specific interfaces rather than a single large, general-purpose interface.
- **D - Dependency Inversion Principle**- High-level modules (classes or components that manage the overall flow of your program) should not depend on low-level modules (classes that perform specific tasks). Both high-level and low-level modules should depend on abstractions (interfaces or abstract classes) rather than concrete implementations. Abstractions should not depend on details; details should depend on abstractions.

## <u>YAGNI - You Aren’t Gonna Need It</u>
Do not add functionality to your codebase until you actually need it to solve a specific problem or fulfill a requirement. In other words, don't implement features or capabilities based on speculation or assumptions about future needs.

## <u>BDUF - Big Design Up Front</u>
Figure out general design first and than implement it. 