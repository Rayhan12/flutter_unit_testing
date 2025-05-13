# Welcome to unit testing in flutter  

**`Lets first learn the about 2 core concepts of all testing`**

> You dont need to focus on the code samples of this section.We will get into it later.

### Test-Driven Development (TDD) Cycle

![red-green-refactor-cycle](assets/1_kdK8wQljp6MtEKAur6Wjrw.webp)

> A *red-green-refactor* workflow for writing reliable, maintainable, and test-first code.

>For most developers, it’s not something that comes naturally and the hardest part is to get used to it. But the good news is that the process of TDD is rhythmic, and because of that, I will try to show you by example how easy it is when you feel the rhythm. Basically, through all your work you need to repeat 3 steps/colors:

---

#### 🔴 1. RED – Write a Failing Test

📌 **Goal:** Define what the code *should do* — **before** writing the implementation.

- ✍️ Write a unit test for a feature or behavior you want to implement.
- ❌ The test **must fail** initially (since the feature doesn't exist yet).
- 🧠 This step **clarifies the requirement** and gives a reason to write only what’s needed.
---
**Example:**

```dart
test('should return true when user is logged in', () {
  final auth = AuthService();
  expect(auth.isLoggedIn(), isTrue); // 🔴 Test fails — not yet implemented
});
```
---

#### 🟢 2. GREEN – Make the Test Pass

📌 **Goal:** Write *just enough code* to pass the failing test.

- ✅ Implement the **simplest logic** to satisfy the test.
- 🧩 No optimizations, no refactoring — just **make it work**.
- 🔐 Avoid overengineering; keep the solution **minimal and focused**.

---

**Example:**

```dart
class AuthService {
  bool isLoggedIn() => true; // 🟢 Hardcoded to pass the test
}
```

#### 🛠️ 3. REFACTOR – Clean the Code

📌 **Goal:** Improve the internal structure **without changing the behavior** or breaking any tests.

- 🔄 Refactor logic, variable names, structure, or remove duplication.
- 🧼 Focus on **readability**, **maintainability**, and **flexibility**.
- ✅ All tests **must remain green** — no functional changes.

---

**Example:**

```dart
class AuthService {
  bool _loggedIn = true;

  bool isLoggedIn() => _loggedIn; // 🛠️ Cleaner, flexible for future logic
}
```
---
> **Please keep this im mind**
> If you have opened your project and you began with anything else instead of creating a test file, stop there! 
Before implementing anything, we will write the test cases. Remember, Red-Green-Refactor.

---

### Design Structure of a Unit test

> Based on the implementation you can desing you test cases in folders as you need it.

```bash
test/
├── core/
│   ├── utils/
│   │   └── date_helper_test.dart
│   └── services/
│       └── logger_service_test.dart
│
├── shared/
│   └── models/
│       └── user_model_test.dart
│
├── modules/
│   ├── auth/
│       ├── application/
│       │   └── login_use_case_test.dart
│       ├── domain/
│       │   └── auth_validator_test.dart
│       └── presentation/
│           └── login_controller_test.dart
│
├── widgets/
│   └── custom_button_test.dart
│
└── main_test.dart

```

---

### Design pattern of a Unit test

> Always remember every `<test_file_name>.dart` test file follows the same structure

```dart
void main(){
    // Define your test cased....
}
```

Generally you can have **two types** of test cases in terms of **how you are writing them**.
1. Independed test case
2. A test case `GROUP` that contains multiple test cases

```dart
import 'package:flutter_test/flutter_test.dart';

void main() {

  // Independent case
  test(
    'description of the test case',
    () {
        // Code for your test
    },
  );

  // Group test cases
  group(
    'description of the test GROUP',
    () {
      test(
        'description of the test case 1 of this group',
        () {
            // Code for your test
        },
      );

      test(
        'description of the test case 2 of this group',
        () {
            // Code for your test
        },
      );

      test(
        'description of the test case 3 of this group',
        () {
            // Code for your test
        },
      );
    },
  );
}

```

**When to use which?**
> Generally for testing a **Class, Controller, Service** wright them in a group which gives you a compact segemnt to run only that part that you are currently working on at once and in sequence. 

> For stand alone functions you can go with Independent test case

---


### Arrange–Act–Assert (AAA) Pattern
> Now lets talk about how the arrangement works. We will focus on cases and use for flutter but its a standard structure. **Please focus on the implementation example from this point**



1. 📦 **Arrange** – Set up the test data and environment.
2. 🚀 **Act** – Execute the function or behavior under test.
3. ✅ **Assert** – Verify the outcome matches expectations.

---
#### 📦 1. Arrange

📌 **Goal:** Set up the test data and environment.

> Define the variables and class you need in the way you need it. Based on requirement you may need 2 types of setup.

1. **Data that maintain their state**
2. **Data that refresh just before every test function is called**
---


