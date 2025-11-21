# 03_data/ - Data Layer

For overall architecture, see [../ARCHITECTURE.md](../ARCHITECTURE.md)

## Purpose

Implements the domain interfaces and handles data operations. This layer knows HOW to get data from various sources.

## Contents

| **Folder**           |                                           |
|----------------------|-------------------------------------------|
| `models/`            | Data transfer objects (DTOs)              |
| `repositories_impl/` | Concrete repository implementations       |
| `data_sources/`      | API clients, local storage                |
| `mappers/`           | Convert between entities and DTOs         |

## Dependencies

- ✅ 01_common/
- ✅ 02_domain/
- ❌ No 04_presentation/

Example Files

```dart
// data/models/user_dto.dart
class UserDto {
  final String id;
  final String fullName;
  final String emailAddress;
  
  UserDto({required this.id, required this.fullName, required this.emailAddress});
  
  factory UserDto.fromJson(Map<String, dynamic> json) {
    return UserDto(
      id: json['id'],
      fullName: json['full_name'],
      emailAddress: json['email'],
    );
  }
}

// data/repositories_impl/user_repository_impl.dart
class UserRepositoryImpl implements UserRepository {
  final UserDataSource dataSource;
  
  UserRepositoryImpl(this.dataSource);
  
  @override
  Future<User> getUserById(String id) async {
    final userDto = await dataSource.getUserById(id);
    return UserMapper.toEntity(userDto);
  }
}
```

---

<sub>This document was AI-generated but refined by a human.</sub>
