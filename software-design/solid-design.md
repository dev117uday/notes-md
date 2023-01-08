---
description: not liquid
---

# Solid Design

* `s`: Single Responsibility Principle
  * Each class should have only one sole purpose, and not be filled with excessive functionality
  * ex : loan class, there can be multiple loans, car, personal, home.
  * ex : send otp class, there can be multiple ways to send otp, email, sms, whatsapp.
* `o`: Open & Close Principle
  * Classes should be open for extension, closed for modification.
  * In other words, you should not have to rewrite an existing class for implementing new features.
  * ex: using interfaces, can can implement create new class to implement new features.
* `l`: Leskov's Subsititution Principle
  * This means that every subclass or derived class should be substitutable for their base or parent class.
  * ex: we have 3 social media: facebook, instagram & whatsapp
    * whatsapp doesnt support features like publish posts
    * there is no calling on instagram
  * we create interface that contain common functionality, have our classes extend from them
  * for specific features, we create new interfaces for them
* `i`: Interfae Segragation Principle
  * Interfaces should not force classes to implement what they can’t do.
  * Large interfaces should be divided into small ones.
* `d`: Dependency Inversion Principle
  * The principle states that we must use abstraction (abstract classes and interfaces) instead of concrete implementation.
  * High level modules should not depend on the low level module but both should depend on the abstraction.
  * ex: when perform payment, it doesnt matter whether you visa or mastercard, debit or credit card, payment provider will take it.
  * instead of taking input a specific class, take a interface which can be implemented by classes

For examples with code : [https://medium.com/@javatechie/solid-design-principle-java-ae96a48db97](https://medium.com/@javatechie/solid-design-principle-java-ae96a48db97)
