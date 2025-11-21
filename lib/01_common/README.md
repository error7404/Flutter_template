# 01_common/ - Foundation Layer

For overall architecture, see [../ARCHITECTURE.md](../ARCHITECTURE.md)

## Purpose

Contains universal utilities, constants, and base classes that have zero dependencies on other project layers. This is the foundation everything else builds upon.

## Contents

| **Directory**    |                                          |
|------------------|------------------------------------------|
| `constants/`     | App-wide constants, strings, enums       |
| `utils/`         | Helper functions, validators, formatters |
| `themes/`        | Colors, typography, styling constants    |
| `exceptions/`    | Custom exception classes                 |
| `extensions/`    | Dart extension methods                   |

## Dependencies

- ❌ No internal project dependencies
- ✅ Only external packages (if absolutely necessary)

## Example Files

```dart
// common/constants/app_constants.dart
class AppConstants {
  static const String appName = 'My App';
  static const double defaultPadding = 16.0;
}

// common/utils/date_utils.dart
class DateUtils {
  static String formatDate(DateTime date) {
    return '${date.day}/${date.month}/${date.year}';
  }
}
```

---

<sub>This document was AI-generated but refined by a human.</sub>
