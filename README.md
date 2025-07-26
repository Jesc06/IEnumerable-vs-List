
# IEnumerable vs List in C#

> **Always program to interfaces, not implementations.**

When working in C# (especially in Clean Architecture), it's best to return `IEnumerable<T>` from your methods if you're just reading data. Use `List<T>` only if you need to change the data (add/remove/sort).

---

### ✅ TL;DR — Quick Guide

| If you need to...          | Use...           |
| -------------------------- | ---------------- |
| Just read the data         | `IEnumerable<T>` |
| Add or remove items        | `List<T>`        |
| Keep your API flexible     | `IEnumerable<T>` |
| Use List-specific features | `List<T>`        |

---

### 💡 Why use `IEnumerable<T>`?

- It's more **abstract** — it hides the exact data type (e.g., `List`, `Array`, etc.)
- It helps you **write flexible and testable code**
- It works well with **LINQ** (e.g., `.Where()`, `.Select()`, etc.)

---

### 🚨 When to use `List<T>`

Use `List<T>` if:

- You need to **add or remove** items
- You need to **sort** or use **indexes** (e.g., `list[0]`)
- You want **performance** with frequent item access

---

### 📌 Rule of Thumb

Start with `IEnumerable<T>` if you just need to **return or loop through data**. Switch to `List<T>` only if you **really need its features**.

---

### Example:

```csharp
// ✅ Good: Returning read-only data
public IEnumerable<User> GetAllUsers()
{
    return _context.Users.ToList();
}

// ❗ Use List only if you need to modify it
public List<User> GetEditableUsers()
{
    var users = _context.Users.ToList();
    users.Add(new User());
    return users;
}
```

---

This helps keep your code **clean, flexible, and maintainable**.


