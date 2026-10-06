## How the System Works

The application follows a **3-tier architecture**:

- **Presentation:** `Main.java` provides a CLI for authentication and banking operations, while `DemoJdbcAndJoins.java` demonstrates JDBC operations and complex queries.
- **Service Layer:** Handles business logic, validation, banking rules, and audit logging.
- **Repository Layer:** Encapsulates SQL operations using JDBC and manages database persistence.

## Object-Oriented Programming

The project demonstrates core Java OOP concepts:

- **Encapsulation:** Private/protected fields with controlled access and input validation.
- **Inheritance:** Hierarchies for `Client`, `Account`, and `Loan` with specialized subclasses.
- **Polymorphism:** Method overriding for operations such as `withdraw()`, `isEligible()`, and `getDisplayName()`.
- **Abstraction:** Abstract domain classes and a generic `Repository<T, ID>` interface.
- **Design Patterns:** Singleton, Repository/DAO, and immutable account snapshots for multi-step operations.
- **Comparable:** Accounts implement `Comparable<Account>` for natural balance-based sorting.

### Java Features

- `List`, `Set`, and `Map` collections
- Custom domain-specific exceptions
- `java.time` (`LocalDate`, `LocalDateTime`)
- Strongly typed enums
- Thread-safe audit logging using Java NIO.2
- Overridden `equals()`, `hashCode()`, and `toString()`

## Database & JDBC

The persistence layer uses **raw JDBC** without an ORM framework.

- **Singleton connection manager** using `DriverManager` and configurable database properties.
- **PreparedStatement** for parameterized SQL queries and SQL injection protection.
- **Try-with-resources** for automatic database resource management.
- **Generated keys** retrieved using `RETURN_GENERATED_KEYS`.
- **Explicit ACID transactions** with `commit()` and `rollback()` for critical operations such as account transfers.
- **Multi-table JOIN queries** for client portfolios, active loans, and transaction audit reports.
- Repository classes separate SQL persistence logic from business logic.
