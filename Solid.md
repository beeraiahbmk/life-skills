# SOLID Introduction:

## SOLID Principles are design principles that enables us manage most of the software design problems.
## The term SOLID is acronym for five design principles intended to make software designs more understandable, flexible, maintanable.

# SOLID Acronym:

1. S : Single Responsibility Principle (SRP)
2. O : Open Closed Principle (OCP)
3. L : Liskov Substitution Principle (LSP)
4. I : Interface Segregation Principle (ISP)
5. D : Dependency Inversion Principle (DIP)


# Sngle Responsibility Principle (srp)

## Definition : 
1. A class Should have only one reason to change.
## Explanation : 
1. Every module or class should have an responsibility over a single part of the functionality provided by the software, And that responsibility should be entirely encapsulated by class.
2. Each class and module should focus on single task at a time.
3. Everything in that class should be related to that single purpose.


```java 
//Before applying SRP
interface User{
    boolean login();
    boolean register();
    void logError();
    boolean sendEmail();
}
//After applying SRP
interface User{
    boolean login(stirng userName, stirng password);
    boolean register(string userName, stirng password, string email);
}
interface userRegister{
    void logError(string error);
}
interface userEmail{
    boolean sendEmail(string emailContent);

}
```
# Open Closed Principle (OCP)

## Definition : 
1. Software entities such as classes, modules, functions, etc. should be open for extension, but closed for modification.
## Explantion :
1. Any new functionality should be implemented by adding new classes, attributes and methods, instead of changing current ones or existing ones.

```java
// without OCP
class Discount {
    double calculate(double amount, String type) {
        if (type.equals("Seasonal")) {
            return amount * 0.9;
        } else if (type.equals("Clearance")) {
            return amount * 0.7;
        }
        return amount;
    }
}

// With OCP
interface Discount {
    double calculate(double amount);
}

class SeasonalDiscount implements Discount {
    public double calculate(double amount) {
        return amount * 0.9;
    }
}

class ClearanceDiscount implements Discount {
    public double calculate(double amount) {
        return amount * 0.7;
    }
}
```
# Liskov Substitution principle (LSP)

## Definition : 
1. S is a type of T, then objects of type T may be replaced with objects of type S.
## Explanation : 
1. Derived types must be completely substitutable for their base types.
2. Liskov substitution is a particular definition of a subtyping relation, called behavioral subtyping.


```java
class Bird {
    void fly() { System.out.println("Flying"); }
}

class Ostrich extends Bird {
    @Override
    void fly() { throw new UnsupportedOperationException("Ostriches can't fly"); }
}

```

# Interface Segregation Principle (ISP)

## Definition : 
1. No client should be forced to depends on methods it does not use.

## Explanation : 
1. One fat interface need to be split to many smaller and relevant interfaces so that client can know about the interfaces that are relevant to them.

```java
// Without ISP
interface Worker {
    void work();
    void eat();
}

class Robot implements Worker {
    public void work() 
    public void eat() { throw new UnsupportedOperationException(); }
}

// With ISP
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

class Robot implements Workable {
    public void work() 
} 

```
# Dependency Inversion Principle (DIP)

1. High level modules should not depend on low level modules. Both should depend on abstraction.
2. Abstraction should not depend on details. Details should depend on abstractions.
3. The interaction between high level and low level modules should be tought of as an abstract interaction bettween them.

```java

// Without DIP
class Light {
    void turnOn() { /* logic */ }
}

class Switch {
    private Light light;

    public Switch() {
        this.light = new Light();
    }

    void toggle() { light.turnOn(); }
}

// With DIP
interface Switchable {
    void turnOn();
}

class Light implements Switchable {
    public void turnOn() { /* logic */ }
}

class Switch {
    private Switchable device;

    public Switch(Switchable device) {
        this.device = device;
    }

    void toggle() { device.turnOn(); }
}

```

# Benefinits of an SOLID principles :

1. SOLID Principles help create code that can be easily modified and extended.
2. SOLID Principles make it easier to identify and modify specific functionalities without impacting the rest of the system.
3. SOLID Principles promote the creation of modular components that can be reused across different parts of the system.


# References :

1. " SOLID principles explained "- https://www.geeksforgeeks.org/solid-principles/
2. SOLID design principles - https://www.youtube.com/watch?v=HLFbeC78YlU&list=PL6n9fhu94yhXjG1w2blMXUzyDrZ_eyOme&index=1
3. A solid guide to SOLID principles - https://www.baeldung.com/solid-principles