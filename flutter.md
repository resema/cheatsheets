# Flutter <!-- omit in toc -->
- [Book: Flutter-In-Action](#book-flutter-in-action)
  - [Concepts](#concepts)
    - [Widget, elements, state and rendering](#widget-elements-state-and-rendering)
      - [Update or not - this is the question](#update-or-not---this-is-the-question)
    - [Widget keys](#widget-keys)
  - [Side Notes](#side-notes)
  - [Flutter UI](#flutter-ui)
    - [Structural widgets](#structural-widgets)
    - [Styling and Themes](#styling-and-themes)
  - [Side Notes](#side-notes-1)
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
> - stateful widgets have always a state object
> - **stateless widgets** have a **build** method in the **widget body**
> - **statefull widgets** have the **build** method in the **state's body**

---
---
## Flutter UI
### Structural widgets
- `MaterialApp` widget:
  - adds material design-specific functionality and syling options to app
  - sets up the **navigator**
  - [link](https://material.io/design) to the concepts/specs of the material concept

- `Scaffold` is a convenience widget
  - gives the app **structure**, aka the foundation and walls

- `AppBar` 
  - provides navigation features
  - uses in `Scaffold.appBar`

### Styling and Themes
- `Theme` widget
  - is accessible anywhere in your widget tree
  - sets defaults for fonts, page animation, icon styles, and more

- `MediaQuery`
  - is a widget similar to `Theme`
  - `BuildContext` can access it anywhere through **`of`**-method
    - looks up the tree
    - finds nearest `MediaQuery`
    - gives a reference to it back
  - f.ex. `MediaQuery.of(context).size`
    - static method

- `Stack` is the go-to widget to
  - place widgets aon top each other
  - in explicit way in relation to each other

- `Table`

---
## Side Notes
> - constraints passed to widget by parents, tell the widget how big it can be, but parents are **not** concerned with its final size --> **flexibility**
> - only one unit of measurement: **logical pixel**
>   - results in some math -> MediaQuery


---
### Themes and styling

---
### Layout

---
