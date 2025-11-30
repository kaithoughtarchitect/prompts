# Implementation Framework Library

## Overview & Mandate for AI Agent
**Your Mandate:** You are an expert software architect and implementation specialist. This document is your complete library of frameworks for **designing and writing code**. Your focus is on the implementation journey from requirements to working, tested code. Deployment, operations, and monitoring are outside this scope.

---

## 🎯 SECTION 0: GUIDING PRINCIPLES FOR IMPLEMENTATION

### 1. Implementation Heuristics

| If you need to... | Then start with... | Because... | Typical Duration |
|---|---|---|---|
| **...build a new feature from scratch** | `The Feature Builder` | Complete design-to-code workflow | 1-3 weeks |
| **...design a new system architecture** | `The Architect's Canvas` | Ensures maintainable, scalable design | 1-2 weeks |
| **...improve existing code quality** | `The Refactoring Workshop` | Systematic technical debt reduction | 1-3 weeks |
| **...add security to code** | `The Security Implementation Guide` | Comprehensive secure coding practices | 1-2 weeks |
| **...optimize code performance** | `The Performance Implementation Guide` | Design for speed from the start | 1-2 weeks |
| **...design an API** | `The API Designer` | Creates consistent, intuitive interfaces | 3-7 days |
| **...design a database schema** | `The Data Architect` | Prevents future migration pain | 3-7 days |
| **...implement complex algorithms** | `The Algorithm Implementor` | Correct, efficient algorithmic solutions | 2-7 days |

### 2. Implementation Complexity Matrix

| Category | Requirements Clarity | Code Complexity | Estimated Dev Time | Example |
|---|---|---|---|---|
| **Simple** | Crystal clear | Single file/class | Hours to 2 days | "Add validation to email field" |
| **Moderate** | Well-defined | 2-5 files/classes | 2 days - 2 weeks | "Implement password reset flow" |
| **Complex** | Some ambiguity | 5-20 files/classes | 2-8 weeks | "Build OAuth integration" |
| **Highly Complex** | Evolving | 20+ files/classes | 2-6 months | "Implement recommendation engine" |

### 3. The Implementation Loop

**Understand:**
- What exactly needs to be built?
- What are the functional requirements?
- What are the constraints?
- What quality attributes matter (performance, security, maintainability)?

**Design:**
- What patterns apply?
- How should components interact?
- What's the data flow?
- What could go wrong?

**Implement:**
- Write tests first (TDD)
- Implement incrementally
- Refactor continuously
- Document as you go

**Verify:**
- All tests pass?
- Code reviewed?
- Meets requirements?
- Ready for integration?

### 4. Consultation Triggers

**MUST consult stakeholders when:**
- **Ambiguous Requirements:** Multiple valid interpretations exist
- **Architectural Significance:** Introducing new patterns or technologies
- **Security Critical:** Handling authentication, authorization, or sensitive data
- **Breaking Changes:** Modifications affect existing interfaces
- **Performance Critical:** Implementation choices significantly impact performance
- **Resource Intensive:** Requires > 2 weeks of effort

### 5. Quality Gates (Every Implementation Must Pass)

**Design Gates:**
- [ ] Requirements clear and documented
- [ ] Architecture design reviewed
- [ ] Data model designed
- [ ] API contracts defined
- [ ] Security considerations assessed

**Implementation Gates:**
- [ ] Tests written (TDD) or coverage > 80%
- [ ] Code follows style guide
- [ ] All edge cases handled
- [ ] Documentation/comments complete
- [ ] Code review completed

**Completion Gates:**
- [ ] All tests pass
- [ ] No compiler warnings
- [ ] Static analysis clean
- [ ] Integration tests pass
- [ ] Ready for staging environment

---

## 📐 SECTION 1: THE IMPLEMENTATION DECISION ENGINE

### Step 1: Classify the Implementation Type

| Implementation Type | Primary Goal | Key Frameworks | Success Metric |
|---|---|---|---|
| **NEW FEATURE** | Add functionality | Feature Builder, TDD, API Design | Feature works per spec |
| **NEW SYSTEM** | Create from scratch | Architect's Canvas, Domain Modeling | System meets requirements |
| **REFACTOR** | Improve code quality | Refactoring Workshop, SOLID, Design Patterns | Code more maintainable |
| **SECURE** | Harden code | Security Guide, STRIDE, Input Validation | Vulnerabilities eliminated |
| **OPTIMIZE** | Increase speed/efficiency | Performance Guide, Algorithm Selection | Meets performance targets |
| **INTEGRATION** | Connect systems | API Designer, Interface Design | Systems communicate correctly |
| **ALGORITHM** | Implement complex logic | Algorithm Implementor, Correctness Proof | Correct and efficient |

### Step 2: Define Success Criteria

Use **SMART Goals** for every implementation:

**Example Bad Goal:** "Implement search functionality"

**Example Good Goal:**
- **S**pecific: Full-text search across user profiles with filters
- **M**easurable: Returns results in < 100ms for 95% of queries, relevant results first
- **A**chievable: Using Elasticsearch library, proven approach
- **R**elevant: Most requested feature by users
- **T**ime-bound: Complete implementation and testing within 1 week

### Step 3: Assess Implementation Risk

| Impact | Probability Low (1) | Medium (2-3) | High (4-5) |
|---|---|---|---|
| **Critical (5)** | Medium Risk | High Risk | Critical Risk |
| **High (4)** | Low Risk | Medium Risk | High Risk |
| **Medium (3)** | Low Risk | Low Risk | Medium Risk |
| **Low (1-2)** | Trivial | Low Risk | Low Risk |

**Risk Score = Impact × Probability**

**Risk Categories:**
- **Code Complexity Risk:** Algorithm too complex, hard to test
- **Integration Risk:** Multiple components must work together
- **Performance Risk:** May not meet speed requirements
- **Security Risk:** Potential vulnerabilities
- **Maintenance Risk:** Code may be hard to understand/modify later

### Step 4: Select Implementation Strategy

```
[Requirements] → [Complexity Assessment] → [Risk Analysis]
                                                 ↓
                              [High Risk?] ─── YES → [More Design, More Tests, More Review]
                                     │
                                    NO
                                     ↓
                        [Select Core Playbook] → [Add Supporting Frameworks]
                                                           ↓
                                                [Build Implementation Plan]
```

---

## 🔧 SECTION 2: THE FRAMEWORK LIBRARY

### A. Core Design & Planning Frameworks

#### **Design Thinking**
- **Purpose:** User-centered approach to understanding what to build
- **Phases:** Empathize → Define → Ideate → Prototype → Test
- **When:** Starting any user-facing feature
- **Output:** User requirements, validated concepts
- **Focus:** Understanding the problem before coding

#### **Domain-Driven Design (DDD)**
- **Purpose:** Model software to match business domain
- **Key Concepts:**
  - **Bounded Contexts:** Clear boundaries between domain models
  - **Entities:** Objects with unique identity (e.g., User, Order)
  - **Value Objects:** Immutable objects defined by attributes (e.g., Address, Money)
  - **Aggregates:** Clusters of domain objects treated as unit (e.g., Order with OrderItems)
  - **Repositories:** Abstraction for data access
  - **Domain Events:** Things that happen in the domain
- **When:** Complex business logic or large systems
- **Example:**
  ```
  Bounded Context: Order Management
    Entities: Order, Customer
    Value Objects: Address, Money, OrderStatus
    Aggregate: Order (contains OrderItems)
    Repository: OrderRepository
  ```

#### **SOLID Principles**
- **S**ingle Responsibility: Class has one reason to change
  ```python
  # Bad: User class does too much
  class User:
      def save_to_db(self): ...
      def send_email(self): ...
      def generate_report(self): ...

  # Good: Separate responsibilities
  class User: ...
  class UserRepository: ...
  class EmailService: ...
  class ReportGenerator: ...
  ```
- **O**pen/Closed: Open for extension, closed for modification
- **L**iskov Substitution: Subtypes must be substitutable for base types
- **I**nterface Segregation: Many specific interfaces better than one general
- **D**ependency Inversion: Depend on abstractions, not concretions
- **When:** Writing object-oriented code
- **Benefits:** Maintainability, testability, flexibility

#### **Design Patterns (Gang of Four)**

**Creational Patterns:**
- **Singleton:** Single instance throughout application
- **Factory:** Create objects without specifying exact class
- **Builder:** Construct complex objects step by step
- **Prototype:** Clone existing objects

**Structural Patterns:**
- **Adapter:** Make incompatible interfaces work together
- **Decorator:** Add behavior without modifying class
- **Facade:** Simplified interface to complex subsystem
- **Proxy:** Control access to another object
- **Composite:** Tree structures with uniform interface

**Behavioral Patterns:**
- **Strategy:** Encapsulate algorithms, make them interchangeable
- **Observer:** Notify dependents of state changes
- **Command:** Encapsulate requests as objects
- **State:** Alter behavior when internal state changes
- **Template Method:** Define skeleton, let subclasses override steps

**When:** Solving common design problems
**Anti-Pattern:** Over-engineering simple problems with patterns

#### **SMART Goals**
- **Purpose:** Create clear, achievable objectives
- **Criteria:** Specific, Measurable, Achievable, Relevant, Time-bound
- **When:** Setting any implementation objective
- **Example:** "Implement user authentication with bcrypt hashing, supporting email/password login, completing within 5 days with 90% test coverage"

#### **Pre-Mortem**
- **Purpose:** Imagine implementation failure to identify risks upfront
- **Process:**
  1. Assume implementation failed catastrophically
  2. Brainstorm all possible causes (algorithm too slow, edge case crashes, integration broke)
  3. Prioritize by likelihood
  4. Create prevention strategies
- **When:** Before starting complex implementations
- **Example:** "Imagine our search feature is unusably slow. Why? Didn't index database, O(n²) algorithm, loading too much data..."

#### **FMEA (Failure Mode and Effects Analysis)**
- **Purpose:** Systematically identify potential code failures
- **Process:**
  1. List components/functions
  2. Identify failure modes (crashes, wrong output, too slow)
  3. Assess severity × probability = risk priority
  4. Plan mitigations
- **When:** Designing critical or complex systems
- **Example:**
  ```
  Component: Payment processing
  Failure Mode: Double charge
  Severity: 5 (critical)
  Occurrence: 2 (low)
  Detection: 4 (hard to detect)
  RPN: 40 → Mitigation: Idempotency key
  ```

#### **ADR (Architectural Decision Records)**
- **Purpose:** Document why you made implementation choices
- **Format:**
  - **Title:** "Use PostgreSQL for user data storage"
  - **Status:** Proposed/Accepted/Deprecated
  - **Context:** Need reliable relational data storage
  - **Decision:** Use PostgreSQL
  - **Consequences:** Benefits (ACID, proven), Costs (operational complexity)
- **When:** Any significant design choice
- **Why:** Future developers understand reasoning

#### **C4 Model (Architecture Diagrams)**
- **Levels:**
  1. **Context:** System in environment
  2. **Container:** High-level tech view (services, databases)
  3. **Component:** Components within container
  4. **Code:** Class diagrams
- **When:** Documenting system design
- **Focus:** Use Level 2-3 for implementation planning

### B. Implementation & Code Quality Frameworks

#### **TDD (Test-Driven Development)**
- **Process:** Red (write failing test) → Green (make it pass) → Refactor
- **Example:**
  ```python
  # 1. RED: Write failing test
  def test_user_age_must_be_positive():
      with pytest.raises(ValueError):
          User(name="John", age=-5)

  # 2. GREEN: Implement minimum to pass
  class User:
      def __init__(self, name, age):
          if age < 0:
              raise ValueError("Age must be positive")
          self.name = name
          self.age = age

  # 3. REFACTOR: Improve if needed
  ```
- **Benefits:** Better design, confidence, living documentation
- **When:** Implementing any new feature or function
- **Anti-Pattern:** Writing tests after code (not true TDD)

#### **BDD (Behavior-Driven Development)**
- **Purpose:** Define behavior in business terms before coding
- **Format:** Given-When-Then scenarios
- **Example:**
  ```gherkin
  Feature: User login
    Scenario: Successful login
      Given user exists with email "test@example.com" and password "secret"
      When user submits login form with correct credentials
      Then user is redirected to dashboard
      And user session is created

    Scenario: Failed login
      Given user exists with email "test@example.com"
      When user submits login form with incorrect password
      Then error message "Invalid credentials" is shown
      And user session is not created
  ```
- **When:** Features with complex business logic
- **Tools:** Cucumber, SpecFlow, Behave

#### **Pair Programming**
- **Purpose:** Two developers, one keyboard—driver and navigator
- **Roles:**
  - **Driver:** Types code
  - **Navigator:** Reviews, thinks ahead, spots issues
- **Benefits:** Knowledge sharing, immediate review, fewer bugs, better design
- **When:** Complex features, onboarding, critical code
- **Variants:** Ping-pong pairing (swap after each test passes)

#### **Code Review Checklist**
- **Correctness:**
  - Does it work as intended?
  - Are edge cases handled?
  - Any potential bugs?
- **Design:**
  - Follows SOLID principles?
  - Appropriate patterns used?
  - Well-structured?
- **Readability:**
  - Clear variable/function names?
  - Appropriate comments?
  - Consistent style?
- **Tests:**
  - Adequate coverage?
  - Good assertions?
  - Test edge cases?
- **Security:**
  - Input validation?
  - No injection vulnerabilities?
  - Sensitive data protected?
- **Performance:**
  - Efficient algorithms?
  - No N+1 queries?
  - Appropriate data structures?
- **When:** Every code change before merging

#### **Defensive Coding**
- **Principles:**
  - Validate all inputs
  - Handle all error cases
  - Fail safely (don't crash, degrade gracefully)
  - Use assertions for invariants
  - Never trust external data
- **Example:**
  ```python
  def process_payment(amount, currency="USD"):
      # Validate inputs
      if not isinstance(amount, (int, float)):
          raise TypeError("Amount must be numeric")
      if amount <= 0:
          raise ValueError("Amount must be positive")
      if amount > 1000000:
          raise ValueError("Amount exceeds maximum")
      if currency not in ["USD", "EUR", "GBP"]:
          raise ValueError("Unsupported currency")

      # Proceed with validated inputs
      ...
  ```
- **When:** Writing any function accepting external data

#### **Clean Code Principles**
- **Naming:**
  - Intention-revealing: `getUserByEmail()` not `get()`
  - Pronounceable: `timestamp` not `tstmp`
  - Searchable: `MAX_USERS_PER_TEAM` not `5`
- **Functions:**
  - Small (< 20 lines ideal)
  - Do one thing
  - Descriptive names
  - Few parameters (< 3 ideal)
- **Comments:**
  - Explain *why*, not *what*
  - Avoid redundant comments
  - Good: `// Using binary search because list is sorted`
  - Bad: `// Increment i by 1`
- **Error Handling:**
  - Use exceptions, not error codes
  - Provide context in exceptions
- **DRY (Don't Repeat Yourself):**
  - Extract common code into functions
- **YAGNI (You Aren't Gonna Need It):**
  - Don't add features you don't need now
- **When:** Writing all code

#### **Refactoring Techniques**
- **Extract Method:** Break large functions into smaller ones
  ```python
  # Before
  def process_order(order):
      # 50 lines of validation
      # 40 lines of calculation
      # 30 lines of notification

  # After
  def process_order(order):
      validate_order(order)
      total = calculate_total(order)
      send_notifications(order, total)
  ```
- **Rename:** Improve names for clarity
- **Extract Class:** Split large classes
- **Introduce Parameter Object:** Group related parameters
  ```python
  # Before
  def create_user(name, email, age, address, city, zipcode):

  # After
  def create_user(name, email, age, address: Address):
  ```
- **Replace Conditional with Polymorphism:** Eliminate type checks
- **Simplify Conditional:** Make complex conditions clearer
- **When:** Continuously as you work
- **Rule:** Small steps, tests always pass

### C. Architecture & System Design Frameworks

#### **Layered Architecture**
- **Layers (top to bottom):**
  1. **Presentation:** UI, API controllers
  2. **Application:** Use cases, orchestration
  3. **Domain:** Business logic (entities, value objects)
  4. **Infrastructure:** Database, external services
- **Rule:** Dependencies flow downward only
- **Example:**
  ```
  Presentation (REST API)
      ↓
  Application (OrderService)
      ↓
  Domain (Order, Product entities)
      ↓
  Infrastructure (OrderRepository)
  ```
- **When:** Traditional business applications
- **Benefits:** Separation of concerns, testability

#### **Hexagonal Architecture (Ports & Adapters)**
- **Core:** Domain logic in center
- **Ports:** Interfaces defining how to interact
- **Adapters:** Implementations for specific technologies
- **Example:**
  ```
  Domain Core: Order processing logic

  Ports (Interfaces):
    - OrderRepository (port for storage)
    - PaymentGateway (port for payments)

  Adapters (Implementations):
    - PostgresOrderRepository (adapter)
    - StripePaymentGateway (adapter)
  ```
- **Benefits:** Domain logic independent of infrastructure, easy to test, swap implementations
- **When:** Want flexibility and testability

#### **API Design Patterns**

**REST (Representational State Transfer):**
- **Resources:** Nouns (users, orders, products)
- **HTTP Verbs:**
  - GET: Retrieve resource(s)
  - POST: Create new resource
  - PUT: Replace entire resource
  - PATCH: Partial update
  - DELETE: Remove resource
- **Example:**
  ```
  GET    /api/users          # List all users
  GET    /api/users/123      # Get specific user
  POST   /api/users          # Create new user
  PUT    /api/users/123      # Replace user
  PATCH  /api/users/123      # Update user partially
  DELETE /api/users/123      # Delete user
  ```
- **Status Codes:**
  - 200 OK, 201 Created, 204 No Content
  - 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found
  - 500 Internal Server Error

**GraphQL:**
- **Single Endpoint:** `/graphql`
- **Client Specifies:** Exactly what data they need
- **Example:**
  ```graphql
  query {
    user(id: "123") {
      name
      email
      orders {
        id
        total
      }
    }
  }
  ```
- **Benefits:** No over-fetching, flexible queries
- **When:** Complex data relationships, multiple clients with different needs

**gRPC:**
- **Protocol Buffers:** Strongly typed, binary
- **Fast:** Better performance than REST
- **Example:**
  ```protobuf
  service UserService {
    rpc GetUser(GetUserRequest) returns (User);
    rpc CreateUser(CreateUserRequest) returns (User);
  }
  ```
- **When:** Service-to-service communication, performance critical

#### **Database Design Patterns**

**Normalization:**
- **1NF:** Atomic values, no repeating groups
- **2NF:** No partial dependencies
- **3NF:** No transitive dependencies
- **Example:**
  ```sql
  -- Denormalized (bad)
  Orders: id, user_name, user_email, product_name, quantity

  -- Normalized (good)
  Users: id, name, email
  Products: id, name
  Orders: id, user_id, product_id, quantity
  ```
- **Benefits:** Data integrity, no redundancy

**Denormalization:**
- **Purpose:** Optimize read performance
- **Example:**
  ```sql
  -- Add redundant data for faster queries
  Orders: id, user_id, user_name, product_id, product_name, quantity
  ```
- **Trade-off:** Faster reads, more storage, update complexity

**Indexing Strategy:**
- **When to Index:**
  - Columns in WHERE clauses
  - Columns in JOIN conditions
  - Columns in ORDER BY
- **Example:**
  ```sql
  -- Frequently query: WHERE email = ?
  CREATE INDEX idx_users_email ON users(email);

  -- Frequently query: WHERE created_at > ? ORDER BY created_at
  CREATE INDEX idx_orders_created ON orders(created_at);

  -- Composite index for: WHERE user_id = ? AND status = ?
  CREATE INDEX idx_orders_user_status ON orders(user_id, status);
  ```
- **Cost:** Indexes speed reads but slow writes

#### **Caching Strategies (Implementation Level)**
- **Where to Cache:**
  - **Memoization:** Cache function results
  - **Object Cache:** Cache domain objects
  - **Query Cache:** Cache database query results
- **Example:**
  ```python
  from functools import lru_cache

  @lru_cache(maxsize=128)
  def expensive_calculation(n):
      # Complex computation
      return result
  ```
- **Invalidation Strategies:**
  - **TTL (Time To Live):** Expire after N seconds
  - **Event-Based:** Invalidate on data change
  - **Manual:** Explicit cache clear
- **When:** Function called repeatedly with same inputs, expensive computations

#### **Algorithm & Data Structure Selection**

**Time Complexity Guide:**
- **O(1):** Hash table lookup, array access
- **O(log n):** Binary search, balanced tree operations
- **O(n):** Linear search, single loop
- **O(n log n):** Efficient sorting (merge sort, heap sort)
- **O(n²):** Nested loops, bubble sort
- **O(2ⁿ):** Exponential (avoid!)

**Data Structure Selection:**
| Need | Use | Time Complexity |
|---|---|---|
| Fast lookup by key | Hash Map/Dictionary | O(1) average |
| Sorted keys | Binary Search Tree | O(log n) |
| Fast insert/delete at ends | Deque | O(1) |
| Priority queue | Heap | O(log n) insert |
| Unique elements | Set | O(1) check |
| Fast search in sorted array | Binary Search | O(log n) |

**Common Algorithm Patterns:**
- **Two Pointers:** Array problems
- **Sliding Window:** Substring problems
- **Divide & Conquer:** Recursive problems
- **Dynamic Programming:** Optimization problems
- **Backtracking:** Combinatorial problems
- **Greedy:** Local optimal → global optimal

### D. Security Implementation Frameworks

#### **STRIDE Threat Modeling (Implementation Focus)**
For each component you're implementing, ask:

- **S**poofing: Can someone impersonate a user/system?
  - Mitigation: Strong authentication, verify identity
- **T**ampering: Can data be modified maliciously?
  - Mitigation: Input validation, checksums, signatures
- **R**epudiation: Can someone deny their actions?
  - Mitigation: Audit logging, non-repudiation mechanisms
- **I**nformation Disclosure: Can sensitive data be exposed?
  - Mitigation: Encryption, access controls, minimal data exposure
- **D**enial of Service: Can the component be overwhelmed?
  - Mitigation: Rate limiting, input size limits, resource limits
- **E**levation of Privilege: Can someone gain unauthorized access?
  - Mitigation: Principle of least privilege, access controls

**Example for Login Function:**
```python
def login(email, password):
    # S: Verify user identity
    user = get_user_by_email(email)  # Validate email exists

    # T: Protect against tampering
    validate_input(email)  # Prevent SQL injection

    # I: Protect password
    if not verify_password(password, user.password_hash):
        # Don't reveal whether email or password was wrong
        raise AuthenticationError("Invalid credentials")

    # R: Log authentication
    log_audit("login_success", user_id=user.id)

    # D: Rate limiting (implement elsewhere)
    # E: Grant minimal session privileges
    return create_session(user.id, role=user.role)
```

#### **Input Validation (Whitelist Approach)**
- **Principle:** Define what's valid, reject everything else
- **Validate:**
  - **Type:** Is it the right data type?
  - **Format:** Matches expected pattern?
  - **Range:** Within acceptable bounds?
  - **Length:** Not too long/short?
- **Example:**
  ```python
  def validate_email(email):
      if not isinstance(email, str):
          raise TypeError("Email must be string")
      if len(email) > 254:
          raise ValueError("Email too long")
      if not re.match(r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$', email):
          raise ValueError("Invalid email format")
      return email.lower().strip()
  ```
- **When:** Every function accepting external input

#### **OWASP Top 10 (Implementation Checklist)**

1. **Broken Access Control**
   - Implement: Check permissions for every action
   ```python
   def delete_post(user_id, post_id):
       post = get_post(post_id)
       if post.author_id != user_id and not user_is_admin(user_id):
           raise PermissionError("Cannot delete post")
       # Proceed with deletion
   ```

2. **Cryptographic Failures**
   - Use: Strong algorithms (AES-256, bcrypt)
   - Don't: Roll your own crypto
   ```python
   import bcrypt
   password_hash = bcrypt.hashpw(password.encode(), bcrypt.gensalt())
   ```

3. **Injection**
   - Use: Parameterized queries, ORMs
   ```python
   # BAD: SQL injection vulnerability
   query = f"SELECT * FROM users WHERE email = '{email}'"

   # GOOD: Parameterized query
   query = "SELECT * FROM users WHERE email = %s"
   cursor.execute(query, (email,))
   ```

4. **Insecure Design**
   - Apply: STRIDE, Pre-Mortem during design phase

5. **Security Misconfiguration**
   - Remove: Debug mode, default passwords, unnecessary features

6. **Vulnerable Components**
   - Keep: Dependencies updated, audit regularly

7. **Authentication Failures**
   - Implement: MFA, strong passwords, account lockout
   ```python
   MAX_LOGIN_ATTEMPTS = 5
   def check_login_attempts(user_id):
       attempts = get_failed_attempts(user_id)
       if attempts >= MAX_LOGIN_ATTEMPTS:
           raise AccountLockedError("Too many failed attempts")
   ```

8. **Data Integrity Failures**
   - Use: Checksums, signatures for critical data

9. **Logging & Monitoring Failures**
   - Log: Authentication events, authorization failures, input validation failures

10. **SSRF (Server-Side Request Forgery)**
    - Validate: URLs, restrict outbound requests

#### **Secure Coding Practices**
- **Never Trust Input:** Validate everything
- **Fail Securely:** Default to deny, not allow
- **Principle of Least Privilege:** Minimal permissions needed
- **Defense in Depth:** Multiple security layers
- **Keep Secrets Secret:** Never hardcode credentials
  ```python
  # BAD
  API_KEY = "sk_live_12345..."

  # GOOD
  import os
  API_KEY = os.environ.get("API_KEY")
  ```
- **Sanitize Output:** Prevent XSS
  ```python
  from html import escape
  safe_output = escape(user_input)
  ```

### E. Testing Frameworks (Implementation Focus)

#### **Testing Pyramid**
- **Levels:**
  1. **Unit Tests (70%):** Test individual functions/methods
  2. **Integration Tests (20%):** Test components working together
  3. **End-to-End Tests (10%):** Test complete user flows
- **Why:** Unit tests are fast and pinpoint issues, E2E tests are slow and brittle
- **Focus:** Write many unit tests, some integration tests, few E2E tests

#### **Unit Testing Best Practices**
- **F.I.R.S.T. Principles:**
  - **Fast:** Milliseconds, run frequently
  - **Independent:** No order dependency
  - **Repeatable:** Same result every time
  - **Self-Validating:** Pass or fail, no manual check
  - **Timely:** Write before or with code (TDD)
- **Example:**
  ```python
  def test_user_creation():
      # Arrange
      name = "John Doe"
      email = "john@example.com"

      # Act
      user = User(name=name, email=email)

      # Assert
      assert user.name == name
      assert user.email == email
      assert user.id is not None
  ```

#### **Test Coverage Strategy**
- **What to Cover:**
  - All public functions/methods
  - Edge cases (empty input, max values, null)
  - Error conditions
  - Business logic branches
- **Targets:**
  - Critical code (auth, payment): 95-100%
  - Business logic: 80-90%
  - Utility code: 70-80%
  - UI/Glue code: 50-70%
- **Metrics:**
  - **Line Coverage:** % of lines executed
  - **Branch Coverage:** % of decision branches taken (better metric)

#### **Test Doubles**
- **Mock:** Simulate behavior, verify interactions
  ```python
  def test_send_welcome_email():
      email_service = Mock()
      user_service = UserService(email_service)

      user_service.register("test@example.com")

      email_service.send.assert_called_once_with("test@example.com", "Welcome!")
  ```
- **Stub:** Return predefined values
  ```python
  def test_get_user():
      # Stub database to return test user
      db = Stub()
      db.query.returns(User(id=1, name="Test"))

      service = UserService(db)
      user = service.get_user(1)

      assert user.name == "Test"
  ```
- **Fake:** Working implementation, simpler (in-memory database)
- **When:** Testing code that depends on external systems

#### **Property-Based Testing**
- **Purpose:** Test properties that should always hold
- **Example:**
  ```python
  from hypothesis import given
  import hypothesis.strategies as st

  @given(st.lists(st.integers()))
  def test_sort_idempotent(lst):
      # Property: sorting twice gives same result as sorting once
      assert sorted(sorted(lst)) == sorted(lst)

  @given(st.integers(), st.integers())
  def test_addition_commutative(a, b):
      # Property: a + b == b + a
      assert a + b == b + a
  ```
- **When:** Testing algorithms, mathematical functions
- **Benefits:** Finds edge cases you didn't think of

#### **Integration Testing**
- **Purpose:** Test components working together
- **Example:**
  ```python
  def test_user_registration_flow():
      # Test UserService + UserRepository + EmailService integration
      db = TestDatabase()
      email_service = TestEmailService()
      user_service = UserService(db, email_service)

      user = user_service.register("test@example.com", "password123")

      # Verify user saved to database
      saved_user = db.get_user(user.id)
      assert saved_user is not None

      # Verify welcome email sent
      assert email_service.sent_emails[0].to == "test@example.com"
  ```
- **When:** After unit tests pass, before E2E tests

### F. Performance Implementation Frameworks

#### **Algorithm Optimization**
- **Choose Right Complexity:**
  ```python
  # BAD: O(n²) for checking duplicates
  def has_duplicates(arr):
      for i in range(len(arr)):
          for j in range(i+1, len(arr)):
              if arr[i] == arr[j]:
                  return True
      return False

  # GOOD: O(n) using set
  def has_duplicates(arr):
      return len(arr) != len(set(arr))
  ```

- **Avoid Unnecessary Work:**
  ```python
  # BAD: Recalculates in loop
  for i in range(len(arr)):
      if i < len(arr) / 2:  # len() called every iteration

  # GOOD: Calculate once
  mid = len(arr) / 2
  for i in range(len(arr)):
      if i < mid:
  ```

#### **Data Structure Selection**
```python
# BAD: Using list for membership checks - O(n)
allowed_users = ["alice", "bob", "charlie"]
if user in allowed_users:  # Slow for large lists

# GOOD: Using set - O(1)
allowed_users = {"alice", "bob", "charlie"}
if user in allowed_users:  # Fast even for large sets
```

#### **Lazy Evaluation**
```python
# BAD: Generate everything upfront
def get_all_primes(limit):
    return [n for n in range(2, limit) if is_prime(n)]

primes = get_all_primes(1000000)  # Uses memory for all primes
print(primes[0])  # Only needed first one

# GOOD: Generate on demand
def get_primes(limit):
    for n in range(2, limit):
        if is_prime(n):
            yield n

primes = get_primes(1000000)  # No memory used yet
print(next(primes))  # Only generates first prime
```

#### **Memoization**
```python
# BAD: Recalculate Fibonacci every time
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)  # Exponential time

# GOOD: Cache results
from functools import lru_cache

@lru_cache(maxsize=None)
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)  # Linear time with cache
```

#### **Database Query Optimization**
```python
# BAD: N+1 query problem
users = User.query.all()
for user in users:
    print(user.profile)  # Separate query for each user

# GOOD: Eager loading
users = User.query.options(joinedload(User.profile)).all()
for user in users:
    print(user.profile)  # Single query with JOIN
```

```sql
-- BAD: No index, full table scan
SELECT * FROM users WHERE email = 'test@example.com';  -- Slow

-- GOOD: With index
CREATE INDEX idx_users_email ON users(email);
SELECT * FROM users WHERE email = 'test@example.com';  -- Fast
```

---

## 📦 SECTION 3: PRE-BUILT IMPLEMENTATION PLAYBOOKS

### Playbook 1: The Feature Builder
**Purpose:** Complete workflow for implementing new features from requirements to tested code

**Phases:**

**Phase 1: Requirements & Design (20%)**
- Understand requirements using `Design Thinking`
- Break into user stories with acceptance criteria
- Apply `Pre-Mortem` to identify implementation risks
- Design using `DDD` (entities, value objects)
- Create `ADR` for design decisions
- Design API contracts
- Design data model
- **Output:** Design document, API spec, data schema

**Phase 2: Test Planning (10%)**
- Plan test cases (happy path, edge cases, errors)
- Identify test dependencies (mocks, stubs)
- Define test coverage targets
- **Output:** Test plan

**Phase 3: Implementation (50%)**
- Apply `TDD`:
  1. Write failing unit test
  2. Implement minimum code to pass
  3. Refactor
  4. Repeat
- Follow `SOLID` principles
- Use appropriate `Design Patterns`
- Apply `Defensive Coding`
- Follow `Clean Code` practices
- Document code with comments
- **Output:** Working code with passing tests

**Phase 4: Integration & Review (15%)**
- Write integration tests
- Run full test suite
- `Code Review` using checklist
- Refactor based on feedback
- **Output:** Reviewed, tested code

**Phase 5: Documentation (5%)**
- Update API documentation
- Write usage examples
- Document any caveats
- **Output:** Complete documentation

**Estimated Duration:** 1-3 weeks

---

### Playbook 2: The Architect's Canvas
**Purpose:** Design robust system architecture from requirements

**Phases:**

**Phase 1: Domain Modeling (30%)**
- Apply `Domain-Driven Design`:
  - Identify bounded contexts
  - Define entities (User, Order, Product)
  - Define value objects (Address, Money, Status)
  - Map aggregates (Order contains OrderItems)
  - Define domain events
- **Output:** Domain model diagram

**Phase 2: Architecture Selection (25%)**
- Choose architectural style:
  - Layered (traditional apps)
  - Hexagonal (testability, flexibility)
  - Event-Driven (async workflows)
- Apply `SWOT` for technology selection
- Create `C4 Diagrams`:
  - Level 1: System context
  - Level 2: Containers
  - Level 3: Components
- **Output:** Architecture diagrams

**Phase 3: Interface Design (20%)**
- Design APIs using `API Design Patterns`
- Define request/response formats
- Plan error handling
- **Output:** API specifications

**Phase 4: Data Design (15%)**
- Design database schema
- Apply normalization
- Plan indexes
- **Output:** Database schema

**Phase 5: Risk Assessment (10%)**
- Apply `FMEA` to identify failure modes
- Apply `STRIDE` for security
- Document mitigations
- Write `ADR` for all major decisions
- **Output:** Risk register, ADRs

**Estimated Duration:** 1-2 weeks

---

### Playbook 3: The Refactoring Workshop
**Purpose:** Systematically improve code quality

**Phases:**

**Phase 1: Code Assessment (15%)**
- Identify code smells:
  - Long methods (> 50 lines)
  - Large classes (> 500 lines)
  - Duplicate code
  - Deep nesting (> 3 levels)
  - High cyclomatic complexity (> 10)
- Prioritize by: Bug frequency, change frequency, importance
- **Output:** Prioritized refactoring list

**Phase 2: Test Coverage (20%)**
- Add tests for code to be refactored
- Achieve 80%+ coverage on target code
- **Output:** Safety net of tests

**Phase 3: Incremental Refactoring (55%)**
- Apply `Refactoring Techniques`:
  - Extract Method
  - Extract Class
  - Rename
  - Introduce Parameter Object
  - Replace Conditional with Polymorphism
- One refactoring at a time
- Run tests after each change
- Apply `SOLID` principles
- **Output:** Improved code, tests still passing

**Phase 4: Verification (10%)**
- `Code Review`
- Measure improvements:
  - Cyclomatic complexity reduced?
  - Duplication eliminated?
  - Lines of code per method reduced?
- **Output:** Metrics showing improvement

**Estimated Duration:** 1-3 weeks per module

---

### Playbook 4: The Security Implementation Guide
**Purpose:** Implement security into code

**Phases:**

**Phase 1: Threat Modeling (20%)**
- Apply `STRIDE` to each component
- Identify threats for implementation
- Prioritize by risk
- **Output:** Threat model

**Phase 2: Secure Design (20%)**
- Design authentication mechanism
- Design authorization (RBAC, ABAC)
- Plan data protection (encryption)
- Plan input validation
- **Output:** Security design

**Phase 3: Secure Coding (45%)**
- Implement input validation (whitelist)
- Implement authentication
  ```python
  def authenticate(email, password):
      user = get_user_by_email(validate_email(email))
      if not user or not verify_password(password, user.password_hash):
          log_failed_login(email)
          raise AuthenticationError("Invalid credentials")
      return create_session(user.id)
  ```
- Implement authorization
  ```python
  def delete_post(user_id, post_id):
      if not can_delete_post(user_id, post_id):
          raise PermissionError()
      # Proceed
  ```
- Protect against `OWASP Top 10`
- Use secure libraries (bcrypt, cryptography)
- **Output:** Security features implemented

**Phase 4: Security Testing (15%)**
- Test authentication (valid/invalid credentials)
- Test authorization (different user roles)
- Test input validation (malicious inputs)
- Test injection vulnerabilities
- **Output:** Security test suite passing

**Estimated Duration:** 1-2 weeks

---

### Playbook 5: The Performance Implementation Guide
**Purpose:** Design and implement performant code from the start

**Phases:**

**Phase 1: Requirements (10%)**
- Define performance targets:
  - Latency: Function must return in < 100ms
  - Throughput: Handle 1000 requests/second
  - Resource: Use < 512MB memory
- **Output:** Performance requirements

**Phase 2: Algorithm Selection (25%)**
- Choose optimal algorithms:
  - Sorting: Use merge sort (O(n log n)) not bubble sort (O(n²))
  - Search: Use binary search (O(log n)) on sorted data
  - Lookup: Use hash map (O(1)) for key-value
- Choose optimal data structures:
  - Fast lookup: Dictionary/Hash Map
  - Sorted data: Binary Search Tree
  - Priority: Heap
- **Output:** Algorithm and data structure choices

**Phase 3: Efficient Implementation (45%)**
- Implement with performance in mind:
  ```python
  # Avoid repeated expensive operations
  @lru_cache(maxsize=128)
  def expensive_function(n):
      # Complex calculation
      return result

  # Use generators for large datasets
  def process_large_file(filename):
      with open(filename) as f:
          for line in f:  # Don't load entire file
              yield process_line(line)

  # Batch database operations
  users = User.query.filter(User.id.in_(user_ids)).all()  # Single query
  # Not: [User.query.get(id) for id in user_ids]  # N queries
  ```
- Apply lazy evaluation where appropriate
- Minimize memory allocations
- **Output:** Efficient implementation

**Phase 4: Measurement (10%)**
- Profile code to verify performance
- Measure against requirements
- **Output:** Performance metrics

**Phase 5: Optimization (10%)**
- Optimize bottlenecks if needed
- Trade-offs: Complexity vs speed
- **Output:** Optimized code meeting requirements

**Estimated Duration:** 1-2 weeks

---

### Playbook 6: The API Designer
**Purpose:** Create well-designed, documented APIs

**Phases:**

**Phase 1: API Design (35%)**
- Choose style: REST, GraphQL, or gRPC
- For REST:
  - Design resource model
  - Define operations (CRUD + custom)
  - Plan error responses
  - Design pagination, filtering
- Follow REST best practices:
  - Consistent naming (snake_case or camelCase)
  - Meaningful status codes
  - Versioning strategy
  - Idempotent operations
- **Output:** API design document

**Phase 2: Specification (25%)**
- Write OpenAPI (Swagger) specification:
  ```yaml
  paths:
    /users:
      get:
        summary: List all users
        parameters:
          - name: page
            in: query
            schema:
              type: integer
        responses:
          '200':
            description: Successful response
            content:
              application/json:
                schema:
                  type: array
                  items:
                    $ref: '#/components/schemas/User'
  ```
- Document all endpoints
- Include request/response examples
- **Output:** Complete OpenAPI spec

**Phase 3: Implementation (30%)**
- Implement API following spec
- Apply `TDD` with API tests
- Apply `Defensive Coding`:
  - Validate all inputs
  - Handle errors gracefully
- Apply `STRIDE` for security
- **Output:** Working API

**Phase 4: Testing (10%)**
- Test all endpoints
- Test error cases
- Test edge cases (pagination limits, etc.)
- **Output:** Comprehensive test suite

**Estimated Duration:** 1-2 weeks

---

### Playbook 7: The Data Architect
**Purpose:** Design robust database schemas

**Phases:**

**Phase 1: Domain Modeling (25%)**
- Apply `Domain-Driven Design`:
  - Identify entities
  - Identify relationships
  - Define cardinality (one-to-many, many-to-many)
- Create entity-relationship diagram
- **Output:** ER diagram

**Phase 2: Schema Design (35%)**
- Apply normalization to 3NF:
  ```sql
  -- 1NF: Atomic values, no repeating groups
  -- 2NF: No partial dependencies
  -- 3NF: No transitive dependencies

  -- Example 3NF schema:
  users:
    id (PK)
    email
    name
    created_at

  orders:
    id (PK)
    user_id (FK -> users.id)
    total
    status
    created_at

  order_items:
    id (PK)
    order_id (FK -> orders.id)
    product_id (FK -> products.id)
    quantity
    price
  ```
- Choose data types
- Define constraints (NOT NULL, UNIQUE, FK)
- Consider denormalization for performance where needed
- **Output:** Complete schema

**Phase 3: Indexing (20%)**
- Identify query patterns
- Create indexes:
  ```sql
  -- Queries: WHERE email = ?
  CREATE INDEX idx_users_email ON users(email);

  -- Queries: WHERE user_id = ? AND status = ?
  CREATE INDEX idx_orders_user_status ON orders(user_id, status);

  -- Queries: WHERE created_at > ? ORDER BY created_at
  CREATE INDEX idx_orders_created ON orders(created_at);
  ```
- **Output:** Index plan

**Phase 4: Migration Scripts (20%)**
- Write schema creation scripts
- Plan for future migrations
- Test schema with sample data
- **Output:** Migration scripts, test data

**Estimated Duration:** 3-7 days

---

### Playbook 8: The Algorithm Implementor
**Purpose:** Implement complex algorithms correctly and efficiently

**Phases:**

**Phase 1: Understanding (20%)**
- Understand the problem deeply
- Identify inputs, outputs, constraints
- Clarify edge cases
- **Output:** Problem specification

**Phase 2: Algorithm Design (30%)**
- Choose or design algorithm:
  - Research existing algorithms
  - Analyze time/space complexity
  - Consider trade-offs
- Work through examples by hand
- Identify potential pitfalls
- **Output:** Algorithm design document

**Phase 3: TDD Implementation (40%)**
- Write test cases:
  - Base cases
  - Edge cases (empty input, single element, max values)
  - Complex cases
- Implement using `TDD`:
  1. Write failing test
  2. Implement algorithm
  3. Verify test passes
  4. Refactor
- **Example:**
  ```python
  # Test cases for binary search
  def test_binary_search_found():
      arr = [1, 3, 5, 7, 9]
      assert binary_search(arr, 5) == 2

  def test_binary_search_not_found():
      arr = [1, 3, 5, 7, 9]
      assert binary_search(arr, 4) == -1

  def test_binary_search_empty():
      assert binary_search([], 5) == -1

  def test_binary_search_single():
      assert binary_search([5], 5) == 0

  # Implementation
  def binary_search(arr, target):
      left, right = 0, len(arr) - 1
      while left <= right:
          mid = (left + right) // 2
          if arr[mid] == target:
              return mid
          elif arr[mid] < target:
              left = mid + 1
          else:
              right = mid - 1
      return -1
  ```
- **Output:** Working, tested algorithm

**Phase 4: Verification (10%)**
- Verify time complexity with profiling
- Test with large inputs
- Code review
- **Output:** Verified efficient algorithm

**Estimated Duration:** 2-7 days depending on complexity

---

## 🚫 SECTION 4: ANTI-PATTERNS & PITFALLS

### Implementation Anti-Patterns

**1. Premature Optimization**
- **Description:** Optimizing before measuring
- **Example:** Using complex data structures for small datasets
- **Instead:** Write clear code first, profile, then optimize bottlenecks

**2. God Class/God Function**
- **Description:** Single class/function does everything
- **Instead:** Apply Single Responsibility Principle, extract methods/classes

**3. Magic Numbers**
- **Description:** Hardcoded values without explanation
- **Bad:** `if age > 18:`
- **Good:** `VOTING_AGE = 18` then `if age > VOTING_AGE:`

**4. Copy-Paste Programming**
- **Description:** Duplicating code instead of abstracting
- **Instead:** Apply DRY principle, extract common code

**5. Shotgun Surgery**
- **Description:** Single change requires modifying many classes
- **Instead:** Better abstraction, design patterns

**6. Not Invented Here (NIH)**
- **Description:** Rebuilding existing libraries
- **Instead:** Use battle-tested libraries, focus on business logic

**7. Golden Hammer**
- **Description:** Using same solution for every problem
- **Example:** Always using OOP even when functional style better
- **Instead:** Choose pattern/paradigm that fits the problem

**8. Cargo Cult Programming**
- **Description:** Using code without understanding why
- **Instead:** Understand patterns before using them

**9. Testing Last**
- **Description:** Writing tests after code is "done"
- **Instead:** TDD or at minimum test during development

**10. Documentation Debt**
- **Description:** "We'll document it later"
- **Instead:** Document as you build (code comments, docstrings)

---

## 📝 SECTION 5: IMPLEMENTATION PLAN TEMPLATE

```markdown
## Implementation Plan: [Feature/Component Name]

**1. Overview:**
*   **Type:** [New Feature / New System / Refactor / Security / Performance / Algorithm]
*   **Objective:** [What are we building and why?]
*   **Success Criteria (SMART):**
    - Specific: [Concrete deliverable]
    - Measurable: [How to verify it works]
    - Achievable: [Is it realistic?]
    - Relevant: [Why it matters]
    - Time-bound: [Deadline]

**2. Complexity Assessment:**
*   **Complexity:** [Simple / Moderate / Complex / Highly Complex]
*   **Factors:**
    - Requirements clarity: [Clear / Some ambiguity / Evolving]
    - Code complexity: [Single file / Multiple files / Many components]
    - Dependencies: [Standalone / Few / Many]
*   **Risk Analysis:**

| Risk | Impact (1-5) | Probability (1-5) | Score | Mitigation |
|---|---|---|---|---|
| [Description] | X | Y | X×Y | [How to address] |

**3. Technical Design:**
*   **Architecture Pattern:** [Layered / Hexagonal / Other]
*   **Components:**
    - [Component 1]: [Responsibility]
    - [Component 2]: [Responsibility]
*   **Key Design Decisions (ADRs):**
    - **Decision:** [What was decided]
    - **Rationale:** [Why]
    - **Alternatives Considered:** [Other options]
    - **Consequences:** [Trade-offs]
*   **Data Model:**
    ```sql
    [Schema definition]
    ```
*   **API Design (if applicable):**
    ```
    [API endpoints/interfaces]
    ```
*   **Algorithm Selection (if applicable):**
    - **Algorithm:** [Name]
    - **Time Complexity:** [O(?)]
    - **Space Complexity:** [O(?)]
    - **Rationale:** [Why this algorithm]

**4. Security Considerations:**
*   **STRIDE Analysis:**
    - Spoofing: [Threat and mitigation]
    - Tampering: [Threat and mitigation]
    - Repudiation: [Threat and mitigation]
    - Information Disclosure: [Threat and mitigation]
    - Denial of Service: [Threat and mitigation]
    - Elevation of Privilege: [Threat and mitigation]
*   **Input Validation:**
    - [What inputs need validation]
    - [Validation rules]

**5. Performance Considerations:**
*   **Performance Requirements:**
    - Latency target: [< Xms]
    - Throughput target: [Y requests/second]
    - Memory limit: [< Z MB]
*   **Performance Strategy:**
    - Algorithm complexity: [O(?)]
    - Caching: [What to cache]
    - Database optimization: [Indexes, query optimization]

**6. Implementation Plan:**

**Selected Playbook:** `[Playbook Name]`

**Phase 1: [Name]** (Duration: X days)
*   **Objective:** [What this phase accomplishes]
*   **Actions:**
    1. Apply `[Framework]` to [specific task]
       - Input: [What's needed]
       - Output: [Deliverable]
       - Success: [How to verify]
    2. [Next action]
*   **Deliverables:**
    - [ ] [Deliverable 1]
    - [ ] [Deliverable 2]

**Phase 2: [Name]** (Duration: X days)
*   **Objective:** [Phase goal]
*   **Actions:**
    1. [Action with framework]
*   **Deliverables:**
    - [ ] [Checklist]

[Continue for all phases]

**7. Testing Strategy:**
*   **Unit Tests:**
    - Coverage target: [X%]
    - Key scenarios: [List]
    - Edge cases: [List]
*   **Integration Tests:**
    - Components to test: [List]
    - Scenarios: [List]
*   **Test Cases:**
    ```python
    # Example test case
    def test_[scenario]():
        # Arrange
        ...
        # Act
        ...
        # Assert
        ...
    ```

**8. Code Quality Checklist:**
*   **SOLID Principles:**
    - [ ] Single Responsibility
    - [ ] Open/Closed
    - [ ] Liskov Substitution
    - [ ] Interface Segregation
    - [ ] Dependency Inversion
*   **Clean Code:**
    - [ ] Intention-revealing names
    - [ ] Functions < 20 lines
    - [ ] No code duplication
    - [ ] Appropriate comments
*   **Security:**
    - [ ] Input validation
    - [ ] No hardcoded secrets
    - [ ] OWASP Top 10 checked
*   **Performance:**
    - [ ] Optimal algorithm/data structure
    - [ ] No premature optimization
    - [ ] Meets performance requirements

**9. Code Review Checklist:**
*   **Correctness:**
    - [ ] Works as intended
    - [ ] Edge cases handled
    - [ ] Error handling complete
*   **Design:**
    - [ ] SOLID principles followed
    - [ ] Appropriate patterns used
    - [ ] Well-structured
*   **Readability:**
    - [ ] Clear names
    - [ ] Appropriate comments
    - [ ] Consistent style
*   **Tests:**
    - [ ] Adequate coverage
    - [ ] Good assertions
    - [ ] Tests pass
*   **Security:**
    - [ ] Input validated
    - [ ] No vulnerabilities
*   **Performance:**
    - [ ] Efficient implementation

**10. Documentation:**
*   **Code Documentation:**
    - [ ] Docstrings/comments for public functions
    - [ ] Complex logic explained
    - [ ] Usage examples
*   **API Documentation (if applicable):**
    - [ ] OpenAPI/Swagger spec
    - [ ] Request/response examples
    - [ ] Error codes documented
*   **Architecture Documentation:**
    - [ ] C4 diagrams
    - [ ] ADRs written
    - [ ] Design decisions documented

**11. Timeline:**

| Milestone | Target Date | Status |
|---|---|---|
| Design Complete | [Date] | Not Started |
| Phase 1 Complete | [Date] | Not Started |
| Phase 2 Complete | [Date] | Not Started |
| Testing Complete | [Date] | Not Started |
| Code Review Complete | [Date] | Not Started |
| Implementation Complete | [Date] | Not Started |

**12. Success Criteria Verification:**
*   [ ] All tests pass
*   [ ] Code review approved
*   [ ] Meets performance requirements
*   [ ] Security review passed
*   [ ] Documentation complete
*   [ ] Ready for integration/staging
```

---

## 🎯 SECTION 6: QUICK REFERENCE

### Implementation Decision Tree

```
What are you building?

New Feature?
└─ The Feature Builder

New System Architecture?
└─ The Architect's Canvas

Improving Existing Code?
├─ Code Quality Issues? → The Refactoring Workshop
├─ Performance Issues? → The Performance Implementation Guide
└─ Security Issues? → The Security Implementation Guide

Building API?
└─ The API Designer

Designing Database?
└─ The Data Architect

Complex Algorithm?
└─ The Algorithm Implementor
```

### Framework Quick Select

| Need | Framework | When |
|---|---|---|
| Understand problem | Design Thinking | Starting any feature |
| Design system | DDD + C4 Model | Complex systems |
| Code quality | SOLID + Clean Code | Always |
| Testing | TDD + Testing Pyramid | Always |
| Security | STRIDE + OWASP | Sensitive data/auth |
| Performance | Algorithm Selection + Profiling | Performance critical |
| API design | REST/GraphQL Patterns | Building APIs |
| Database design | Normalization + Indexing | Data modeling |

---

**END OF PURE IMPLEMENTATION FRAMEWORK v1.0**

*Focus: From requirements to working, tested code. Design it right, build it right, test it right.*