# 05_app/ - Application Layer

For overall architecture, see [../ARCHITECTURE.md](../ARCHITECTURE.md)

## Purpose

The composition root that wires everything together and launches the application.

## Contents

| File/Directory |                                     |
|----------------|-------------------------------------|
| `app.dart`     | Main app widget                     |
| `routes.dart`  | Navigation configuration            |
| `di/`          | Dependency injection setup          |
| `config/`      | App configuration, environments     |

## Dependencies

- ✅ 01_common/
- ✅ 02_domain/
- ✅ 03_data/
- ✅ 04_presentation/

## Example Files

```dart
// app/app.dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MultiProvider(
      providers: [
        ChangeNotifierProvider(create: (_) => UserController(getIt<GetUserUseCase>())),
      ],
      child: MaterialApp(
        title: AppConstants.appName,
        theme: AppTheme.light,
        routes: AppRoutes.routes,
      ),
    );
  }
}

// app/di/locator.dart
final getIt = GetIt.instance;

void setupDependencies() {
  getIt.registerLazySingleton<UserRepository>(() => UserRepositoryImpl(getIt()));
  getIt.registerLazySingleton<GetUserUseCase>(() => GetUserUseCase(getIt()));
}
```

---

<sub>This document was AI-generated but refined by a human.</sub>
