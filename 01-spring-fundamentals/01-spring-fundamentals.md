# Chapter 1: Spring Fundamentals

_Status: In progress — topics being taught one at a time in chat; full notes filled in as each topic is covered._

## 1. What is Spring Framework? Why Spring?

Plain Java forces you to manually `new` up every object and wire dependencies by hand.

**Spring's core idea**: you write plain Java classes, and Spring's container creates them, wires them together, and manages their lifecycle.

```java
// Plain Java — OrderService creates its own dependency
public class OrderService {
    private PaymentGateway gateway = new RazorpayGateway();
}

// Spring way — OrderService just declares what it needs
@Service // <-- the one Spring-specific line: "Spring, please manage and construct this"
public class OrderService {
    private final PaymentGateway gateway;

    public OrderService(PaymentGateway gateway) { // Spring calls this for you
        this.gateway = gateway;
    }
}
```
Business classes stay plain Java. Spring's role = the `@Service` annotation that opts the class in, plus the container running behind the scenes that does the `new` and wiring you'd otherwise write by hand.

**Interview line**: *"Spring is built around Inversion of Control — it manages object creation and wiring so business classes stay decoupled."*

> 🔴 **Doubt (asked during this chapter): "This constructor code is plain Java too — how does Spring relate to it?"**
>
> Answer: The constructor itself is plain Java — Spring's involvement is (1) the `@Service` annotation marking the class as Spring-managed, and (2) the container calling `new OrderService(...)` for you at startup instead of you writing that line yourself.

> 🔴 **Doubt (asked during this chapter): "How does Spring know which constructor to call — parameterless or parameterized?"**
>
> Answer: Spring inspects the class via reflection at startup.
> - **Only one constructor exists** → Spring uses it automatically, no annotation needed.
> - **Multiple constructors exist** → Spring can't guess which to use, so mark the intended one with `@Autowired`. Without it, Spring falls back to the no-arg constructor and any dependency fields stay `null`.
>
> ```java
> @Service
> public class OrderService {
>     private PaymentGateway gateway;
>
>     public OrderService() { } // constructor A
>
>     @Autowired
>     public OrderService(PaymentGateway gateway) { // constructor B — Spring uses this one
>         this.gateway = gateway;
>     }
> }
> ```
>
> `@Autowired` placement rule: it goes directly above whichever thing you're marking — constructor, field, or setter:
> ```java
> @Autowired
> private PaymentGateway gateway;                          // field injection
>
> @Autowired
> public void setGateway(PaymentGateway gateway) { ... }    // setter injection
> ```
> (Injection types covered properly in Topic 8.)

> 🔴 **Doubt (asked during this chapter): "What is 'decoupled'?"**
>
> Answer: Decoupled = a class doesn't depend on another class's concrete details, only on what it needs (usually an interface). Change one, the other doesn't break.
>
> - **Coupled (bad)**: `OrderService` hardcodes `new RazorpayGateway()` — tightly tied to that one class; switching gateways means editing `OrderService`.
> - **Decoupled (good)**: `OrderService` only takes a `PaymentGateway` via its constructor — it doesn't care which implementation it gets, so `StripeGateway` can be swapped in with zero changes to `OrderService`.

---

## 2. IoC (Inversion of Control)

**Normal control flow**: your code decides when to create objects and calls the shots.
```java
PaymentGateway gateway = new RazorpayGateway(); // you're in control
OrderService service = new OrderService(gateway);
```

**Inverted control**: you hand that responsibility to a framework. You just declare "I need a `PaymentGateway`" and the **Spring IoC Container** decides what to create and when, then hands it to you.

Sometimes called the **"Hollywood Principle": "Don't call us, we'll call you."** You don't call `new` to get your dependencies — the container calls your constructor and gives them to you.

**Key terms:**
- **IoC** = the *principle* — control is inverted, framework manages object creation/wiring instead of your code.
- **IoC Container** = the actual engine in Spring that does this (named properly — `ApplicationContext` — in Topic 4).
- **Dependency Injection (DI)** = the *mechanism* the container uses to implement IoC (handing dependencies to your objects, mainly via constructors).

So: **IoC is the "what/why," DI is the "how."**

**Interview line**: *"IoC means the framework controls object creation and wiring instead of your code doing it manually. DI is the specific technique Spring uses to achieve that — injecting dependencies into your objects rather than having them create their own."*