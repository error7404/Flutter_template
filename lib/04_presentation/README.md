# 04_presentation/ - UI Layer

For overall architecture, see [../ARCHITECTURE.md](../ARCHITECTURE.md)

## Purpose

Contains all UI components, state management, and presentation logic. This layer focuses on **HOW** data is displayed to users.

## Contents

| **Folder**     |                                           |
|----------------|-------------------------------------------|
| `pages/`       | Full screens/routes                       |
| `widgets/`     | Reusable UI components                    |
| `controllers/` | State management (Providers, BLoCs, etc.) |
| `views/`       | Stateless widget compositions             |
| `states/`      | State classes, view models                |

## Dependencies

- ✅ 01_common/
- ✅ 02_domain/
- ✅ 03_data/ (via dependency injection)

Example Files

```dart
// presentation/controllers/user_controller.dart
class UserController extends ChangeNotifier {
  final GetUserUseCase getUserUseCase;
  User? _user;
  bool _loading = false;
  
  User? get user => _user;
  bool get loading => _loading;
  
  UserController(this.getUserUseCase);
  
  Future<void> loadUser(String userId) async {
    _loading = true;
    notifyListeners();
    
    try {
      _user = await getUserUseCase.execute(userId);
    } catch (e) {
      // Handle error
    } finally {
      _loading = false;
      notifyListeners();
    }
  }
}

// presentation/pages/user_profile_page.dart
class UserProfilePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Consumer<UserController>(
        builder: (context, controller, child) {
          if (controller.loading) return CircularProgressIndicator();
          if (controller.user == null) return Text('No user data');
          
          return UserProfileView(user: controller.user!);
        },
      ),
    );
  }
}
```

---

<sub>This document was AI-generated but refined by a human.</sub>
