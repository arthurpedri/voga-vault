```c
typedef enum DaysOfWeek {
  MONDAY, // 0
  TACO_TUESDAY, // 1
  WEDNESDAY, // 2
  THURSDAY, // ...
  FRIDAY,
  SATURDAY,
  FUNDAY,
} days_of_week_t;
```
An `enum` is _not_ a collection type like a struct or an array. It's just a list of integers constrained to a new type, where each is given an explicit name.
### Non-Default Values
```c
typedef enum {
  EXIT_SUCCESS = 0,
  EXIT_FAILURE = 1,
  EXIT_COMMAND_NOT_FOUND = 127,
} ExitStatus;
```