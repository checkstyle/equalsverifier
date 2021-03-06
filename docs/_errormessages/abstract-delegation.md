---
title: Abstract delegation
---
    Abstract delegation: Foo's equals method delegates to an abstract method
    Abstract delegation: Foo's hashCode method delegates to an abstract method

This error can occur when the class under test, one of its fields, or its superclass, is abstract, and their `equals` or `hashCode` method calls an abstract method.

EqualsVerifier creates instances of the class under test and its superclass and repeatedly calls their `equals` and `hashCode` methods. However, it can't create implementations of abstract methods. The "Abstract delegation" error therefore occurs when calling `equals` or `hashCode` would throw an `AbstractMethodError`.

If one of the fields has an abstract type, the error can be avoided by calling `withPrefabValues` for that type. For other cases, there is currently no solution. Try rewriting the class so that `equals` and `hashCode` can use fields, instead of the abstract method.

Note that, from version 1.1.4, EqualsVerifier includes the name of the abstract method that caused the error in its error message.

