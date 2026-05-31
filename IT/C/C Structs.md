```c
struct City {
  char *name;
  int lat;
  int lon;
};
```

```c
typedef struct Pastry {
    char *name;
    float weight;
} pastry_t;
```
- Now, you can use `pastry_t` wherever before you would have used `struct Pastry`.
- The `_t` at the end is a common convention to indicate a type.
- In fact, you can optionally skip giving the struct a name, and only refer to the type as `pastry_t`.
## Forward Declaration
```c
typedef struct Node node_t;

typedef struct Node {
  int value;
  node_t *next;
} node_t;
```
### Zero Initializer
```c
int main() {
  struct City c = {0};
}
```
This sets all the fields to `0` values.
### Positional Initializer
```c
int main() {
  struct City c = {"San Francisco", 37, -122};
}
```
### Designated Initializer
- It's easier to read (has the field names)
- If the fields change, you don't have to worry about breaking the ordering
```c
int main() {
  struct City c = {
    .name = "San Francisco",
    .lat = 37,
    .lon = -122
  };
}
```
Remember, it's `.name` not `name`. If this trips you up, just remember it's `.name` and not `name` because that's how you access the field, e.g. `c.name`.
### Accessing Fields
Accessing a field in a struct is done using the `.` operator. For example:
```c
struct City c;
c.lat = 41; // Set the latitude
printf("Latitude: %d", c.lat); // Print the latitude
```
### Struct Padding
Oversimplified:
1. The fields of a struct are laid out in memory contiguously (next to each other).
2. Structs can vary in size depending on how they are laid out.
3. As a _rule of thumb_, ordering your fields from largest to smallest will help the compiler minimize padding:

```c
typedef struct {
  char* a;
  double b;
  char c;
  char d;
  long e;
  char f;
} poorly_aligned_t;

typedef struct {
  double b;
  long e;
  char* a;
  char c;
  char d;
  char f;
} better_t;
```