# Flutter <!-- omit in toc -->
- [1. Book: Flutter-In-Action](#1-book-flutter-in-action)
  - [Concepts](#concepts)
    - [Widget, elements, state and rendering](#widget-elements-state-and-rendering)
  - [- know how to update their own reference to a different widget.](#--know-how-to-update-their-own-reference-to-a-different-widget)

---
---
# 1. Book: Flutter-In-Action
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
  - know how to update their own reference to a different widget.
---