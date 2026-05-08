# Naming classes and functions

Naming is one of the most important parts of software design. Good names reduce cognitive load, improve navigation, and help teams understand intent without needing to read implementation details.

Two common approaches appear frequently in backend systems: organizing classes by domain or by responsibility.

## Package by domain

Example:

```text
user/
  UserService.kt
  UserRepository.kt
  UserController.kt

payment/
  PaymentService.kt
  PaymentRepository.kt
  PaymentGateway.kt
```

Positive points:

- Keeps everything related to a business capability close together.
- Easier for teams to navigate large systems through business concepts.
- Improves ownership and modularity around domains.
- Works very well in microservices and domain-driven design.

Negative points:

- Shared technical concerns may become duplicated across domains.
- Some abstractions become harder to standardize globally.
- Cross-domain refactors may require touching many packages.

This style usually scales better for products where business complexity grows faster than technical complexity.

## Package by responsibility

Example:

```text
controllers/
  UserController.kt
  PaymentController.kt

services/
  UserService.kt
  PaymentService.kt

repositories/
  UserRepository.kt
  PaymentRepository.kt
```

Positive points:

- Simple and familiar structure for smaller applications.
- Easy to understand for new developers.
- Centralizes technical patterns and responsibilities.
- Works well for CRUD-oriented systems.

Negative points:

- Business context becomes fragmented across folders.
- Navigation gets harder as the system grows.
- Related features are physically separated in the codebase.
- Encourages “god layers” with oversized service packages.

This style is often effective early in a project, but can become harder to maintain as domains evolve.

## Naming classes

A class name should communicate responsibility, not implementation detail.

Good examples:

```kotlin
PaymentProcessor
InvoiceGenerator
UserAuthenticator
```

Less clear examples:

```kotlin
Manager
Helper
Utils
ProcessorImpl
```

Positive points of explicit naming:

- Makes intent immediately understandable.
- Reduces the need for comments.
- Improves discoverability in IDE search.

Negative points of overly generic naming:

- Hides responsibility.
- Encourages classes to grow without boundaries.
- Makes onboarding harder for new developers.

Names like `Helper` or `Util` often indicate unclear ownership or mixed responsibilities.

## Naming functions

Function names should describe behavior clearly and predictably.

Good examples:

```kotlin
calculateTotal()
sendWelcomeEmail()
findActiveUsers()
```

Less clear examples:

```kotlin
handle()
process()
execute()
doStuff()
```

Positive points of descriptive function names:

- Makes code readable almost like documentation.
- Clarifies side effects and intent.
- Reduces ambiguity during maintenance.

Negative points of vague function names:

- Forces developers to inspect implementation details.
- Makes debugging and refactoring harder.
- Increases cognitive overhead during reviews.

A good function name usually answers at least one of these questions:

- What does it do?
- What does it return?
- Does it mutate state?
- Does it trigger side effects?

## Verb vs noun naming

Functions usually benefit from verbs:

```kotlin
createInvoice()
validateToken()
publishEvent()
```

Classes usually benefit from nouns:

```kotlin
InvoiceRepository
TokenValidator
EventPublisher
```

Positive points:

- Creates consistency across the codebase.
- Helps distinguish behavior from structure.
- Improves readability during navigation.

## Consistency over cleverness

A naming convention only works when it is consistently applied.

Positive points:

- Teams move faster when patterns are predictable.
- Reduces unnecessary discussions during reviews.
- Improves maintainability long term.

Negative points of inconsistent naming:

- Similar concepts receive different names.
- Developers lose confidence in conventions.
- Searchability and discoverability suffer.

Clear and boring names are usually better than creative names. In most systems, predictability is more valuable than originality.
