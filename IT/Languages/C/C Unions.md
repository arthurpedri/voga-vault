Unions in C can hold one of several types. They're like a less-strict [sum type](https://en.wikipedia.org/wiki/Algebraic_data_type) from the world of functional programming. Here's an example union:
```c
typedef union AgeOrName {
  int age;
  char *name;
} age_or_name_t;
```

The `age_or_name_t` type can hold _either_ an `int` or a `char *`, but not both at the same time (that would be a struct). We provide the list of possible types so that the C compiler knows the _maximum_ potential memory requirement, and can account for that.
- A `union` only reserves enough space to hold the largest type in the union and then _all_ of the fields **use the same memory**.
- If we try to access the other field, we will get get garbage (Bytes interpreted using the incorrect type)
- Unions store their value in the same memory location, no matter which field or type is actively being used. That means that accessing any field apart from the one you set is generally a **bad idea**.
## Helper Fields
One interesting (albeit not commonly used) trick is to use unions to create "helpers" for accessing different parts of a piece of memory. Consider the following:

```c
typedef union Color {
  struct {
    uint8_t r;
    uint8_t g;
    uint8_t b;
    uint8_t a;
  } components;
  uint32_t rgba;
} color_t;
```
Only 4 bytes are used. And, unlike in 99% of scenarios, it makes sense to both set _and_ get values from this union through both the `components` and `rgba` fields! Both fields in the union are exactly 32 bits in size, which means that we can "safely" (?) access the entire set of colors through the `.rgba` field, or get a single color component through the `.components` field.

The convenience of additional fields, with the efficiency of a single memory location!