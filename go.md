# GoLang <!-- omit in toc -->
- [Book: Go-In-Action](#book-go-in-action)
  - [Concepts](#concepts)
    - [Public & Private](#public--private)
    - [Variable declaration](#variable-declaration)
    - [Asynchronous](#asynchronous)
    - [Implement an interface](#implement-an-interface)
  - [Side Notes](#side-notes)

---
---
# Book: Go-In-Action
## Concepts
### Public & Private
- identifiers are eitehr **exported** or **unexported** from a package
  - lower case -> unexported
  - upper case -> experted

### Variable declaration
- short declaration operator `:=` declares and initialize at same time

### Asynchronous
- channels implement a **queue** of **typed values** that are used to **communicate data between goroutines**
-  `WaitGroup` tracks when a goroutine is finished
   -  is a **counting semaphore**

### Implement an interface
- use the declaration of an empty struct
  - **allocates zero bytes**
  - implement **all methods of an interface**
  - methods declared with **empty struct name** as **value receiver**

---
## Side Notes
> - all variables are **zero-initialized**
> - functions can have **multiple return values**
> - Go supports `Closures`
>   - func can access variables directly
>   - vars have a single state
> - `any` aka `interface{}` is a generic type 
>   - takes every type
>   - uses reflection
> - it's best practice to **decalre methods** using **pointer receiver**
> - in case of the **derived type**
>   - **value receiver** can be called by interface type values that contain **both values and pointers**
> - when methods directly called via **interface type**,
>   - the rules are different:
>      - pointer receiver can only be called by interface type values that contain pointer
>       - value receiver can be called by interface type values that contain both values and pointers

---
---