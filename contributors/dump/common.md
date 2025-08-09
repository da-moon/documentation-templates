## OO Principels

- Encapsulation: Ensure that each class encapsulates its own data and behavior.
  For example, the `VirtualDOM` class should encapsulate the logic for building
  and manipulating the Virtual DOM, while the `LXMLParser` class should
  encapsulate the parsing logic.
- Single Responsibility Principle (SRP): Each class should have a single
  responsibility. For example, the `VirtualDOMBuilder` class should only be
  responsible for building the Virtual DOM, not for parsing XML.
- Dependency Inversion Principle (DIP): High-level modules should not depend on
  low-level modules. Instead, both should depend on abstractions.



--------

@@@@@@@@@@@@@@@@@@@

# Software Development Guidelines

## 1. Write Short Units of Code

### Guideline Explanation

- Small units are easier to understand, reuse, and test.
- When writing new units, don't let them grow above 15 lines of code.
- When a unit grows beyond 15 lines of code, you need to shorten it by
  splitting it into smaller units of no longer than 15 lines of code.
- **Further reading:** Chapter 2 of _Building Maintainable Software_

---

## 2. Write Simple Units of Code

### Guideline Explanation

- Keeping the number of branch points (if, for, while, etc.) low makes units
  easier to modify and test.
- Try to limit the McCabe complexity, that is, the number of branch points plus
  1, in a unit to at most 5.
- You can reduce complexity by extracting sub-branches to separate units of no
  more than 4 branch points.
- **Further reading:** Chapter 3 of _Building Maintainable Software_

---

## 3. Write Code Once

### Guideline Explanation

- When code is copied, bugs need to be fixed in multiple places. This is both
  inefficient and error-prone.
- Avoid duplication by never copy/pasting blocks of code.
- Reduce duplication by extracting shared code, either to a new unit or to a
  superclass.
- **Further reading:** Chapter 4 of _Building Maintainable Software_

---

## 4. Keep Unit Interfaces Small

### Guideline Explanation

- Keeping the number of parameters low makes units easier to understand and
  reuse.
- Limit the number of parameters per unit to at most 2.
- The number of parameters can be reduced by grouping related parameters into
  objects.
- Alternatively, try extracting parts of units that require fewer parameters.
- **Further reading:** Chapter 5 of _Building Maintainable Software_

---

## 5. Separate Concerns in Modules

### Guideline Explanation

- Keep the codebase loosely coupled, as it makes it easier to minimize the
  consequences of changes.
- Identify and extract responsibilities of large modules to separate modules
  and hide implementation details behind interfaces.
- Strive to get modules to have no more than 10 incoming calls.
- **Further reading:** Chapter 6 of _Building Maintainable Software_

---

## 6. Couple Architecture Components Loosely

### Guideline Explanation

- Having loose coupling between top-level components makes it easier to
  maintain components in isolation.
- Do this by minimizing the amount of interface code; that is, code in modules
  that are both called from and call modules of other components (throughput),
  and code in modules that are called from modules of other components
  (incoming).
- You can hide a component's implementation details through various means,
  e.g., using the "abstract factory" design pattern.
- **Further reading:** Chapter 7 of _Building Maintainable Software_

---

## 7. Keep Architecture Components Balanced

### Guideline Explanation

- Balancing the number and relative size of components makes it easier to
  locate code.
- Organize source code in a way that the number of components is between 2 and
  12, and ensure the components are of approximately equal size (keep component
  size uniformity less than 0.71).
- For actionable results, you need to define architecture components, for
  example by configuring a zoom level in the tab on the right of the guideline
  view. A zoom level recognizes as architecture components the folders at a
  particular nesting depth.
- **Further reading:** Chapter 8 of _Building Maintainable Software_

---

## 8. Keep Your Codebase Small

### Guideline Explanation

- Keeping your codebase small improves maintainability, as it's less work to
  make structural changes in a smaller codebase.
- Avoid codebase growth by actively reducing system size.
- Refactor existing code to achieve the same functionality using less volume,
  and prefer libraries and frameworks over "homegrown" implementations of
  standard functionality.
- Strive to keep volume below 20 Person-years.
- **Further reading:** Chapter 9 of _Building Maintainable Software_

---

## 9. Automate Tests

### Guideline Explanation

- Automating tests for your codebase makes development more predictable and
  less risky.
- Add tests for existing code every time you change it.
- For small systems (less than 1,000 lines of code), you should have at least
  some test code and one assertion (currently only checked for Java and C#
  systems).
- For medium systems (less than 10,000 lines of code), the total lines of test
  code should be at least 50% of the total lines of production code, and the
  assert density (percentage of lines of test code containing assertions)
  should be at least 1% (currently only checked for Java and C# systems).
- For large systems (more than 10,000 lines of code), the total lines of test
  code should be at least 50% of the total lines of production code, and the
  assert density should be at least 5% (currently only checked for Java and C#
  systems).
- **Further reading:** Chapter 10 of _Building Maintainable Software_

---

## 10. Write Clean Code

### Guideline Explanation

- Clean code is more maintainable.
- Proactively search and remove code smells.
- Remove useless comments, commented code blocks, and dead code. Refactor
  poorly handled exceptions, magic constants, and poorly named units or
  variables.
- **Further reading:** Chapter 11 of _Building Maintainable Software_



-------
@@@@@@@@@@@@@@@@


1. **Single Responsibility Principle (SRP):** Ensure each class, module, or
   file has only one reason to change by assigning it a single responsibility.
2. **Modularization:** Divide the codebase into distinct modules where each
   module encapsulates related functionality, allowing for independent
   development, testing, and maintenance.
3. **Separation of Concerns:** Structure the code so that different concerns or
   aspects of the system are handled by distinct sections, preventing overlap
   and increasing clarity.
4. **Layered Architecture:** Organize the system into layers, where each layer
   has a distinct responsibility, and higher layers depend on the services
   provided by lower layers.
5. **Encapsulation:** Bundle data and the methods that operate on that data
   within single units (e.g., classes) and restrict access to the internal
   components to maintain integrity.
6. **Package-by-Feature:** Organize the codebase by features rather than by
   technical layers, ensuring that all related code (e.g., models, services,
   controllers) for a feature is grouped together.
7. **Component-Based Architecture:** Divide the system into reusable
   components, each encapsulating a specific piece of functionality, allowing
   them to be combined to form the full system.

**Task:** When refactoring or generating new code, follow the above principles
meticulously. Below are examples that demonstrate how to apply these principles
effectively.

---

**Few-Shot Examples:**

---

**Example 1: Single Responsibility Principle (SRP)**

**Original Code:**

```python
class UserManager:
    def create_user(self, user_data):
        # logic to create a user
    def delete_user(self, user_id):
        # logic to delete a user
    def update_user(self, user_id, new_data):
        # logic to update a user
    def log_user_activity(self, user_id, activity):
        # logic to log user activity
```

**Refactored Code Applying SRP:**

```python
class UserService:
    def create_user(self, user_data):
        # logic to create a user

    def delete_user(self, user_id):
        # logic to delete a user

    def update_user(self, user_id, new_data):
        # logic to update a user

class UserActivityLogger:
    def log_user_activity(self, user_id, activity):
        # logic to log user activity
```

_Explanation:_ The `UserManager` class has been refactored into two classes,
each with a single responsibility. The `UserService` handles user management,
while the `UserActivityLogger` handles activity logging. This refactor adheres
to the SRP and improves modularization and encapsulation.

---

**Example 2: Modularization**

**Original Codebase:**

```plaintext
project-root/
├── user_manager.py    # Contains all logic related to users, from creation to logging activities
```

**Refactored Codebase Applying Modularization:**

```plaintext
project-root/
├── user/
│   ├── __init__.py    # Initializes the user module
│   ├── service.py     # Contains user management logic (create, update, delete)
│   ├── logger.py      # Contains user activity logging logic
```

_Explanation:_ The codebase has been modularized by separating the user-related
logic into distinct modules (e.g., `service.py` for user management and
`logger.py` for activity logging). This allows each module to be developed,
tested, and maintained independently.

---

**Example 3: Separation of Concerns**

**Original Code:**

```python
def handle_user_request(request):
    # directly interacts with the database
    # performs business logic
    # returns a response
```

**Refactored Code Applying Separation of Concerns:**

```python
class UserController:
    def __init__(self, user_service):
        self.user_service = user_service

    def handle_request(self, request):
        user_data = self.user_service.process_request(request)
        return user_data
```

_Explanation:_ The logic has been separated into distinct concerns: the
controller (`UserController`) handles the request and coordinates with the
service (`UserService`) to process it. This prevents overlap between database
interactions, business logic, and request handling, improving clarity and
maintainability.

---

**Example 4: Layered Architecture**

**Original Code:**

```python
def handle_request(request):
    # directly interacts with the database
    # performs business logic
    # returns a response
```

**Refactored Code with Layered Architecture:**

```python
class RequestHandler:
    def __init__(self, business_logic, database):
        self.business_logic = business_logic
        self.database = database

    def handle_request(self, request):
        data = self.database.get_data(request)
        result = self.business_logic.process(data)
        return result
```

_Explanation:_ The logic has been separated into distinct layers: a database
layer and a business logic layer. The `RequestHandler` class coordinates
between these layers, making the code more maintainable and easier to extend.

---

**Example 5: Encapsulation**

**Original Code:**

```python
user_data = {'name': 'John Doe', 'email': 'john@example.com'}
```

**Refactored Code Applying Encapsulation:**

```python
class User:
    def __init__(self, name, email):
        self._name = name
        self._email = email

    def get_name(self):
        return self._name

    def get_email(self):
        return self._email
```

_Explanation:_ The user data is now encapsulated within the `User` class. This
class provides methods to access the data, ensuring that the internal state is
protected and can only be accessed through defined interfaces.

---

**Example 6: Package-by-Feature**

**Original Project Structure:**

```plaintext
project-root/
├── models/
│   ├── user.py
│   ├── order.py
├── services/
│   ├── user_service.py
│   ├── order_service.py
├── controllers/
│   ├── user_controller.py
│   ├── order_controller.py
```

**Refactored Project Structure Applying Package-by-Feature:**

```plaintext
project-root/
├── user/
│   ├── __init__.py
│   ├── models.py       # User model definition
│   ├── service.py      # User management logic
│   ├── controller.py   # User-related request handling
├── order/
│   ├── __init__.py
│   ├── models.py       # Order model definition
│   ├── service.py      # Order management logic
│   ├── controller.py   # Order-related request handling
```

_Explanation:_ The project has been reorganized to follow the
Package-by-Feature pattern. Each feature (e.g., `user`, `order`) has its own
directory, containing the relevant models, services, and controllers. This
improves modularity and makes the codebase easier to navigate.

---

**Example 7: Component-Based Architecture**

**Original Codebase:**

```plaintext
project-root/
├── core/
│   ├── user_manager.py
│   ├── order_manager.py
```

**Refactored Codebase Applying Component-Based Architecture:**

```plaintext
project-root/
├── components/
│   ├── user/
│   │   ├── __init__.py
│   │   ├── service.py    # User management logic
│   │   ├── controller.py # User-related request handling
│   │   ├── models.py     # User model definition
│   │
│   ├── order/
│       ├── __init__.py
│       ├── service.py    # Order management logic
│       ├── controller.py # Order-related request handling
│       ├── models.py     # Order model definition
```

_Explanation:_ The codebase is organized into reusable components (e.g.,
`user`, `order`). Each component encapsulates a specific piece of
functionality, making the system modular, maintainable, and scalable.
Components can be developed, tested, and deployed independently.

---

