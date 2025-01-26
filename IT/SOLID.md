## Single Responsibility
- Break down code into modules with single responsibilities each.
## Open/Closed
- Design modules to be able to add function without changing it, by extending it.
- Once a module is in use it shouldn't be modified.
## Liskov Substitution
- Only extend modules when they are the same in essence.
- If it doesn't fit it's design it should be it's own type, and not extend a previous type.
## Interface Segregation
- Modules shouldn't need to know about functionality they don't use.
- Splitting modules into smaller abstractions like interfaces will help in creating the exact functionality required.
## Dependency Inversion 
-  Modules shouldn't communicate with each other directly, they should communicate abstractly, typically via interfaces.
- Isolated modules can be changed or replaced as necessary, without affecting other modules, they just need to correctly interact with their interfaces.