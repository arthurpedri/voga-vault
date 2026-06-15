- Interfaces are a set of properties, methods and other members.
- They are declared with a [[Function signatures|signature]] but their behaviors are not defined.
 - A class implements an interface if it defines those things.
## Clean Interface Rules of Thumb
### Keep Interfaces small
Interfaces are meant to define the minimal behavior necessary to accurately represent an idea or concept.
### Interfaces Should Have No Knowledge of Satisfying Types
An interface should define what is necessary for other types to classify as a member of that interface. They shouldn't be aware of any types that happen to satisfy the interface at design time.
### Interfaces Are Not Classes
- Interfaces are not classes, they are slimmer.
- Interfaces don't have constructors or deconstructors that require that data is created or destroyed.
- Interfaces aren't hierarchical by nature, though there is syntactic sugar to create interfaces that happen to be supersets of other interfaces.
- Interfaces define function signatures, but not underlying behavior.