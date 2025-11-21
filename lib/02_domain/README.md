# 02_domain/ - Business Logic Layer

For overall architecture, see [../ARCHITECTURE.md](../ARCHITECTURE.md)

## Purpose

Contains the core business logic, entities, and use cases. This layer defines **WHAT** the app does without knowing **HOW** it's implemented.

## Contents

| **Folder**        |                                    |
|-------------------|------------------------------------|
| `entities/`       | Business objects/models            |
| `repositories/`   | Abstract repository interfaces     |
| `use_cases/`      | Business logic operations          |
| `value_objects/`  | Domain-specific value types        |

Dependencies

- ✅ 01_common/
- ❌ No 03_data/ or 04_presentation/

Example Files

```dart
// domain/entities/user.dart
class User {
  final String id;
  final String name;
  final String email;
  
  User({required this.id, required this.name, required this.email});
}

// domain/repositories/user_repository.dart
abstract class UserRepository {
  Future<User> getUserById(String id);
  Future<List<User>> getUsers();
}

// domain/use_cases/get_user_use_case.dart
class GetUserUseCase {
  final UserRepository repository;
  
  GetUserUseCase(this.repository);
  
  Future<User> execute(String userId) {
    return repository.getUserById(userId);
  }
}
```

---

<sub>This document was AI-generated but refined by a human.</sub>
