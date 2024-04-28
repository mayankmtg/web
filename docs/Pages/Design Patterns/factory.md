
---

## Factory design pattern

This is the classic case of polymorphism implementation

A Factory generates objects of different types (but same parent interface) based on some constant identifier passed.

That generated object can be used directly.

## Example

```java
class Parent {
    method()
}

class Child1 implements Parent {}
class Child2 implements Parent {}

class Factory (s String) Parent {
    if s == "1" {
        return Child1()
    }
    if s == "2" {
        return Child2()
    }
}

f = Factory()
f.method()
```

This is a very commonly used design pattern

---
