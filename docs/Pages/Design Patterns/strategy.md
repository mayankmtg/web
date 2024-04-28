
---

## Strategy design pattern

There's a need to control class behaviour based on strategy.

Strategy typically has an interface with some set methods.
All strategy subclasses (typically all different strategies), implement the said interface.

The main class whose behaviour needs to be controlled typically takes this strategy in the constructor/class-definition.

### Example

```java
interface Strategy {
    method()
}

class Strategy1 implements Strategy {
    method() {
        print ("This is strategy 1")
    }
}

class Strategy2 implements Strategy {
    method() {
        print ("This is strategy 1")
    }
}

class Main {
    strategy Strategy
}


m1 = Main(Strategy1())
m2 = Main(Strategy2())

m1.method()
m2.method()
```

---
