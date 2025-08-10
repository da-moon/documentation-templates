# Common Software Development Principles

## Rules Table

| Rule ID | Rule Summary                                                              |
| ------- | ------------------------------------------------------------------------- |
| R1      | Write short units of code (max 15 lines)                                 |
| R2      | Write simple units (max 5 branch points/McCabe complexity)               |
| R3      | Write code once - avoid duplication                                      |
| R4      | Keep unit interfaces small (max 2 parameters)                            |
| R5      | Separate concerns in modules (max 10 incoming calls)                     |
| R6      | Couple architecture components loosely                                   |
| R7      | Keep architecture components balanced (2-12 components)                  |
| R8      | Keep codebase small (prefer libraries over homegrown)                    |
| R9      | Automate tests (50%+ test coverage for medium+ systems)                  |
| R10     | Write clean code (remove dead code, magic constants, poor names)         |
| R11     | Apply Single Responsibility Principle                                    |
| R12     | Use modularization for independent development                           |
| R13     | Implement separation of concerns                                         |
| R14     | Use layered architecture with clear dependencies                         |
| R15     | Encapsulate data and behavior together                                   |
| R16     | Organize by features, not technical layers                               |
| R17     | Build component-based architecture                                       |
| R18     | Apply Dependency Inversion Principle                                     |
| R19     | Use abstractions over concrete implementations                           |
| R20     | Maintain high cohesion within modules                                    |

---

## R1: Write short units of code (max 15 lines)

```python
# ❌ BAD - 25+ line function
def process_order(order_data):
    # Validation
    if not order_data:
        raise ValueError("No order data")
    if 'items' not in order_data:
        raise ValueError("No items")
    
    # Calculate totals
    subtotal = 0
    for item in order_data['items']:
        price = item['price']
        quantity = item['quantity']
        subtotal += price * quantity
    
    # Apply discounts
    discount = 0
    if subtotal > 100:
        discount = subtotal * 0.1
    elif subtotal > 50:
        discount = subtotal * 0.05
    
    # Calculate tax
    tax_rate = 0.08
    tax = (subtotal - discount) * tax_rate
    
    # Final total
    total = subtotal - discount + tax
    
    return {
        'subtotal': subtotal,
        'discount': discount,
        'tax': tax,
        'total': total
    }

# ✅ GOOD - Functions under 15 lines
def process_order(order_data):
    validate_order_data(order_data)
    subtotal = calculate_subtotal(order_data['items'])
    discount = calculate_discount(subtotal)
    tax = calculate_tax(subtotal, discount)
    return create_order_summary(subtotal, discount, tax)

def calculate_subtotal(items):
    return sum(item['price'] * item['quantity'] for item in items)

def calculate_discount(subtotal):
    if subtotal > 100:
        return subtotal * 0.1
    elif subtotal > 50:
        return subtotal * 0.05
    return 0
```

## R2: Write simple units (max 5 branch points/McCabe complexity)

```python
# ❌ BAD - Complexity of 8
def get_user_status(user):
    if user is None:
        return "invalid"
    if user.is_deleted:
        return "deleted"
    if user.is_suspended:
        return "suspended"
    if user.email_verified:
        if user.phone_verified:
            if user.has_2fa:
                return "fully_verified"
            else:
                return "partially_verified"
        else:
            return "email_only"
    else:
        return "unverified"

# ✅ GOOD - Complexity of 4 or less per function
def get_user_status(user):
    if user is None:
        return "invalid"
    if user.is_deleted:
        return "deleted"
    if user.is_suspended:
        return "suspended"
    return get_verification_status(user)

def get_verification_status(user):
    if not user.email_verified:
        return "unverified"
    if not user.phone_verified:
        return "email_only"
    return "fully_verified" if user.has_2fa else "partially_verified"
```

## R3: Write code once - avoid duplication

```python
# ❌ BAD - Duplicated validation logic
class UserController:
    def create_user(self, data):
        if not data.get('email'):
            raise ValueError("Email required")
        if '@' not in data['email']:
            raise ValueError("Invalid email")
        # create user...
    
    def update_user(self, data):
        if not data.get('email'):
            raise ValueError("Email required")
        if '@' not in data['email']:
            raise ValueError("Invalid email")
        # update user...

# ✅ GOOD - Extracted common validation
class UserController:
    def create_user(self, data):
        self._validate_email(data)
        # create user...
    
    def update_user(self, data):
        self._validate_email(data)
        # update user...
    
    def _validate_email(self, data):
        if not data.get('email'):
            raise ValueError("Email required")
        if '@' not in data['email']:
            raise ValueError("Invalid email")
```

## R4: Keep unit interfaces small (max 2 parameters)

```python
# ❌ BAD - Too many parameters
def send_notification(user_id, message, title, priority, retry_count, timeout):
    # implementation
    pass

# ✅ GOOD - Grouped into object
from dataclasses import dataclass

@dataclass
class NotificationRequest:
    user_id: str
    message: str
    title: str = ""
    priority: int = 1
    retry_count: int = 3
    timeout: int = 30

def send_notification(request: NotificationRequest):
    # implementation using request.user_id, request.message, etc.
    pass
```

## R5: Separate concerns in modules (max 10 incoming calls)

```python
# ❌ BAD - Module with too many responsibilities
# user_manager.py - Called by 15+ different modules
class UserManager:
    def authenticate_user(self): ...
    def create_user(self): ...
    def update_profile(self): ...
    def send_email(self): ...
    def log_activity(self): ...
    def generate_report(self): ...

# ✅ GOOD - Separated concerns
# auth/service.py - Called by 3 modules
class AuthService:
    def authenticate_user(self): ...

# user/service.py - Called by 5 modules  
class UserService:
    def create_user(self): ...
    def update_profile(self): ...

# notification/service.py - Called by 4 modules
class NotificationService:
    def send_email(self): ...
```

## R6: Couple architecture components loosely

```python
# ❌ BAD - Tight coupling
class OrderService:
    def __init__(self):
        self.db = PostgreSQLDatabase()  # Direct dependency
        self.email = SMTPEmailer()      # Direct dependency
    
    def process_order(self, order):
        self.db.save(order)
        self.email.send(order.user_email, "Order confirmed")

# ✅ GOOD - Loose coupling with interfaces
from abc import ABC, abstractmethod

class Database(ABC):
    @abstractmethod
    def save(self, data): pass

class Emailer(ABC):
    @abstractmethod
    def send(self, to, message): pass

class OrderService:
    def __init__(self, db: Database, emailer: Emailer):
        self.db = db          # Dependency injection
        self.emailer = emailer # Dependency injection
    
    def process_order(self, order):
        self.db.save(order)
        self.emailer.send(order.user_email, "Order confirmed")
```

## R7: Keep architecture components balanced (2-12 components)

```plaintext
# ❌ BAD - Unbalanced architecture
project/
├── user/ (5000 lines)
├── order/ (4500 lines)
├── payment/ (4000 lines)
├── util/ (50 lines)        # Too small
├── helper/ (30 lines)      # Too small
├── misc/ (20 lines)        # Too small

# ✅ GOOD - Balanced components
project/
├── user/ (1500 lines)
├── order/ (1400 lines)
├── payment/ (1300 lines)
├── notification/ (1200 lines)
├── reporting/ (1100 lines)
├── common/ (800 lines)      # Utilities consolidated
```

## R8: Keep codebase small (prefer libraries over homegrown)

```python
# ❌ BAD - Reinventing the wheel
class CustomJSONParser:
    def parse(self, json_string):
        # 200 lines of custom JSON parsing logic
        ...

class CustomHTTPClient:
    def get(self, url):
        # 300 lines of custom HTTP implementation
        ...

# ✅ GOOD - Using established libraries
import json
import requests

def parse_json(json_string):
    return json.loads(json_string)

def fetch_data(url):
    return requests.get(url).json()
```

## R9: Automate tests (50%+ test coverage for medium+ systems)

```python
# ❌ BAD - No tests
def calculate_discount(price, customer_type):
    if customer_type == 'premium':
        return price * 0.2
    elif customer_type == 'regular':
        return price * 0.1
    return 0

# ✅ GOOD - Comprehensive test coverage
def calculate_discount(price, customer_type):
    """Calculate discount based on customer type."""
    discounts = {
        'premium': 0.2,
        'regular': 0.1
    }
    return price * discounts.get(customer_type, 0)

# test_discount.py
import pytest

def test_premium_discount():
    assert calculate_discount(100, 'premium') == 20

def test_regular_discount():
    assert calculate_discount(100, 'regular') == 10

def test_no_discount():
    assert calculate_discount(100, 'guest') == 0

def test_zero_price():
    assert calculate_discount(0, 'premium') == 0
```

## R10: Write clean code (remove dead code, magic constants, poor names)

```python
# ❌ BAD - Unclean code
def proc(d):
    # Old implementation
    # result = d * 1.08
    # return result
    
    x = d * 1.08  # What is 1.08?
    y = 100       # Magic number
    
    if x > y:
        return x * 0.9  # Another magic number
    return x

# ✅ GOOD - Clean code
# Constants with clear names
TAX_RATE = 0.08
DISCOUNT_THRESHOLD = 100
DISCOUNT_RATE = 0.1

def calculate_price_with_tax(base_price):
    """Calculate final price including tax and discounts."""
    price_with_tax = base_price * (1 + TAX_RATE)
    
    if price_with_tax > DISCOUNT_THRESHOLD:
        return price_with_tax * (1 - DISCOUNT_RATE)
    return price_with_tax
```

## R11: Apply Single Responsibility Principle

```python
# ❌ BAD - Multiple responsibilities
class Employee:
    def calculate_pay(self): ...
    def save_to_database(self): ...
    def send_email(self): ...
    def generate_report(self): ...

# ✅ GOOD - Single responsibility per class
class Employee:
    """Represents employee data and business logic."""
    def calculate_pay(self): ...

class EmployeeRepository:
    """Handles employee persistence."""
    def save(self, employee): ...

class EmployeeNotifier:
    """Handles employee communications."""
    def send_email(self, employee): ...

class EmployeeReporter:
    """Generates employee reports."""
    def generate_report(self, employee): ...
```

## R12: Use modularization for independent development

```python
# ❌ BAD - Monolithic structure
# app.py (5000 lines)
class Application:
    def handle_users(self): ...
    def handle_orders(self): ...
    def handle_payments(self): ...
    def handle_shipping(self): ...

# ✅ GOOD - Modular structure
# user/__init__.py
from .service import UserService
from .repository import UserRepository

# order/__init__.py
from .service import OrderService
from .repository import OrderRepository

# Each module can be developed, tested, and deployed independently
```

## R13: Implement separation of concerns

```python
# ❌ BAD - Mixed concerns
def handle_request(request):
    # Validation logic
    if not request.get('user_id'):
        return {'error': 'Missing user_id'}
    
    # Database access
    conn = db.connect()
    user = conn.query(f"SELECT * FROM users WHERE id = {request['user_id']}")
    
    # Business logic
    if user.age < 18:
        discount = 0.2
    else:
        discount = 0.1
    
    # Response formatting
    return json.dumps({'user': user, 'discount': discount})

# ✅ GOOD - Separated concerns
class RequestValidator:
    def validate(self, request):
        if not request.get('user_id'):
            raise ValidationError('Missing user_id')

class UserRepository:
    def get_user(self, user_id):
        return self.db.query("SELECT * FROM users WHERE id = ?", user_id)

class DiscountService:
    def calculate_discount(self, user):
        return 0.2 if user.age < 18 else 0.1

class RequestHandler:
    def handle(self, request):
        self.validator.validate(request)
        user = self.repository.get_user(request['user_id'])
        discount = self.service.calculate_discount(user)
        return {'user': user, 'discount': discount}
```

## R14: Use layered architecture with clear dependencies

```python
# ✅ GOOD - Clear layered architecture

# Presentation Layer (depends on Application Layer)
class UserController:
    def __init__(self, user_service: UserService):
        self.service = user_service
    
    def get_user(self, request):
        user_id = request.params['id']
        user = self.service.get_user_by_id(user_id)
        return JsonResponse(user)

# Application Layer (depends on Domain Layer)
class UserService:
    def __init__(self, user_repository: UserRepository):
        self.repository = user_repository
    
    def get_user_by_id(self, user_id):
        user = self.repository.find_by_id(user_id)
        if not user:
            raise UserNotFoundError(user_id)
        return user

# Domain Layer (no dependencies on other layers)
@dataclass
class User:
    id: str
    name: str
    email: str
    
    def is_active(self):
        return self.status == 'active'

# Infrastructure Layer (implements Domain interfaces)
class UserRepository:
    def find_by_id(self, user_id):
        # Database access logic
        pass
```

## R15: Encapsulate data and behavior together

```python
# ❌ BAD - Data without behavior
user_data = {
    'balance': 100,
    'status': 'active'
}

def withdraw_money(data, amount):
    if data['status'] != 'active':
        raise Exception("Account not active")
    if data['balance'] < amount:
        raise Exception("Insufficient funds")
    data['balance'] -= amount

# ✅ GOOD - Encapsulated data and behavior
class Account:
    def __init__(self, balance, status):
        self._balance = balance
        self._status = status
    
    def withdraw(self, amount):
        if self._status != 'active':
            raise Exception("Account not active")
        if self._balance < amount:
            raise Exception("Insufficient funds")
        self._balance -= amount
    
    @property
    def balance(self):
        return self._balance
```

## R16: Organize by features, not technical layers

```plaintext
# ❌ BAD - Organization by technical layers
project/
├── controllers/
│   ├── user_controller.py
│   ├── product_controller.py
│   └── order_controller.py
├── services/
│   ├── user_service.py
│   ├── product_service.py
│   └── order_service.py
├── models/
│   ├── user.py
│   ├── product.py
│   └── order.py

# ✅ GOOD - Organization by features
project/
├── user/
│   ├── __init__.py
│   ├── controller.py
│   ├── service.py
│   ├── model.py
│   └── repository.py
├── product/
│   ├── __init__.py
│   ├── controller.py
│   ├── service.py
│   ├── model.py
│   └── repository.py
├── order/
│   ├── __init__.py
│   ├── controller.py
│   ├── service.py
│   ├── model.py
│   └── repository.py
```

## R17: Build component-based architecture

```python
# ✅ GOOD - Component-based design
class AuthenticationComponent:
    """Self-contained authentication component."""
    
    def __init__(self, token_service, user_repository):
        self.token_service = token_service
        self.user_repository = user_repository
    
    def login(self, credentials):
        user = self.user_repository.find_by_email(credentials.email)
        if self._verify_password(credentials.password, user.password_hash):
            return self.token_service.generate_token(user)
        raise AuthenticationError()
    
    def logout(self, token):
        self.token_service.revoke_token(token)
    
    def verify_token(self, token):
        return self.token_service.verify_token(token)

# Components can be composed together
class Application:
    def __init__(self):
        self.auth = AuthenticationComponent(token_service, user_repo)
        self.user = UserComponent(user_repo, validator)
        self.notification = NotificationComponent(email_service)
```

## R18: Apply Dependency Inversion Principle

```python
# ❌ BAD - High-level depends on low-level
class EmailService:
    def __init__(self):
        self.smtp_client = SMTPClient()  # Concrete dependency
    
    def send(self, message):
        self.smtp_client.send_mail(message)

# ✅ GOOD - Both depend on abstractions
from abc import ABC, abstractmethod

# Abstraction
class EmailSender(ABC):
    @abstractmethod
    def send(self, message): pass

# High-level module
class EmailService:
    def __init__(self, sender: EmailSender):
        self.sender = sender  # Depends on abstraction
    
    def send_notification(self, user, message):
        self.sender.send(message)

# Low-level module
class SMTPEmailSender(EmailSender):
    def send(self, message):
        # SMTP implementation
        pass

class SendGridEmailSender(EmailSender):
    def send(self, message):
        # SendGrid implementation
        pass
```

## R19: Use abstractions over concrete implementations

```python
# ❌ BAD - Tied to concrete implementation
class OrderProcessor:
    def __init__(self):
        self.db = MySQLDatabase()
    
    def process(self, order):
        self.db.save_to_mysql(order)

# ✅ GOOD - Using abstractions
from abc import ABC, abstractmethod

class Database(ABC):
    @abstractmethod
    def save(self, data): pass
    
    @abstractmethod
    def find(self, id): pass

class OrderProcessor:
    def __init__(self, database: Database):
        self.db = database
    
    def process(self, order):
        self.db.save(order)

# Can swap implementations
mysql_processor = OrderProcessor(MySQLDatabase())
postgres_processor = OrderProcessor(PostgresDatabase())
mongo_processor = OrderProcessor(MongoDatabase())
```

## R20: Maintain high cohesion within modules

```python
# ❌ BAD - Low cohesion (unrelated functions)
class Utilities:
    def calculate_tax(self, amount): ...
    def send_email(self, recipient): ...
    def parse_xml(self, data): ...
    def encrypt_password(self, password): ...

# ✅ GOOD - High cohesion (related functions)
class TaxCalculator:
    def calculate_sales_tax(self, amount): ...
    def calculate_income_tax(self, income): ...
    def calculate_property_tax(self, value): ...
    def get_tax_rate(self, location): ...

class EmailService:
    def send_email(self, recipient, subject, body): ...
    def send_bulk_email(self, recipients, template): ...
    def validate_email_address(self, email): ...
    def format_email_template(self, template, data): ...
```