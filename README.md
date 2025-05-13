# Welcome to unit testing in flutter  

**`Lets first learn the about 2 core concepts of all testing`**

### 🧪 Test-Driven Development (TDD) Cycle

![red-green-refactor-cycle](assets\1_kdK8wQljp6MtEKAur6Wjrw.webp)

> A *red-green-refactor* workflow for writing reliable, maintainable, and test-first code.

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



**🧪 Arrange–Act–Assert (AAA) Pattern**

1. 📦 **Arrange** – Set up the test data and environment.
2. 🚀 **Act** – Execute the function or behavior under test.
3. ✅ **Assert** – Verify the outcome matches expectations.
