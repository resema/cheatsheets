# Flutter <!-- omit in toc -->
- [Book: Flutter-In-Action](#book-flutter-in-action)
  - [Concepts](#concepts)
    - [Widget, elements, state and rendering](#widget-elements-state-and-rendering)
      - [Update or not - this is the question](#update-or-not---this-is-the-question)
    - [Widget keys](#widget-keys)
  - [Side Notes](#side-notes)
  - [Flutter UI](#flutter-ui)
    - [Structural widgets](#structural-widgets)
    - [Themes and styling](#themes-and-styling)
    - [Layout](#layout)

---
---
# Book: Flutter-In-Action
## Concepts
### Widget, elements, state and rendering
- the flutter framework manages **three trees**:
  - widget tree: ephemeral and light-weight,
  - element tree: uses widget and connect them the the render tree,
  - render tree.
- **state object** are managed by element tree,
  - long-lived,
  - can be reused,
  - elements have references to widgets.
- elements are the **brains** of the operations,
  - contain **only meta information** and a **reference to a widget**,
  - **know** how to update their **own reference to a different widget**.
  - are therefore considered to be simple

> anytime Flutter is rebuilding, the element's reference points to the *new widget in the exact location in the widget tree of the element's old reference*.

#### Update or not - this is the question
- elements **look at what** to deciper **if** an **update of the widget** is **needed**?
  - **exact type** at runtime
  - widget's key (if there is one)

---
### Widget keys
- **helps** Flutter to know **when two widgets** of the same type are **actually different**
  - `GlobalKey`: subclass of `Key` (*do not use, is mostly a global state*)
  - `LocalKey`: subclass of `Key`
    - `ValueKey`: subclass of `LocalKey`
      - `PageStorageKey`: subclass of `ValueKey<T>`
    - `ObjectKey`: implement `LocalKey`
    - `UniqueKey`: implement `LocalKey`

---
## Side Notes
> stateful widgets have always a state object

---
---
## Flutter UI
### Structural widgets

---
### Themes and styling

---
### Layout

---
