# Vue.js Complete Course (2026 Ready)

A comprehensive Vue.js learning path covering Vue 3 fundamentals, advanced concepts, and hands-on projects.  
This curriculum is suitable for junior to mid-level Vue developers and serves as a strong foundation for modern Vue development in 2026.

---

## 📚 Course Content

## Milestones
- Intro
- What is Vue.js?
- Side Talk
- Installations
- Folder Structure
- Component In Depth
- Text Interpolation
- Attribute Bindings
- Dynamic Bindings
- Styling In Depth
- Event Handlers In Vue
- Reactivity & Reactive
- ref()
- Computed Properties
- Conditional Rendering
- v-for
- v-model
- Props
- Component Event
- Slots
- Provide & Inject
- Lifecycle Hooks
- Watchers
- Template Ref
- Async Components
- Composables
- Custom Directives
- Dynamic Components
- Data Fetching In Vue
- Project 1
- Project 2
- Project 3
- Project 4
- Project 5
- Project 6
- Project 7
- Project 8
- Project 9
- Project 10
- Outro


### Fundamentals
- Intro  
- What is Vue.js?  
- Installations  
- Folder Structure  
- Component In Depth  
- Text Interpolation  
- Attribute Bindings  
- Dynamic Bindings  
- Styling In Depth  
- Event Handlers In Vue  

### Reactivity & Core Concepts
- Reactivity & Reactive  
- ref()  
- Computed Properties  
- Conditional Rendering  
- v-for  
- v-model  

### Component Communication
- Props  
- Component Event  
- Slots  
- Provide & Inject  

### Advanced Vue Concepts
- Lifecycle Hooks  
- Watchers  
- Template Ref  
- Async Components  
- Composables  
- Custom Directives  
- Dynamic Components  
- Data Fetching In Vue  

### Projects
- Project 1  
- Project 2  
- Project 3  
- Project 4  
- Project 5  
- Project 6  
- Project 7  
- Project 8  
- Project 9  
- Project 10  

---

## 🚀 Skills Covered

- Vue 3 & Composition API
- Component-driven architecture
- Reactive state management
- Dynamic UI rendering
- Reusable composables
- Async & performance-aware components
- Real-world project development

---

## ⚠️ Recommended Additions for 2026

To be fully industry-ready, consider adding the following:

- TypeScript with Vue (`<script setup lang="ts">`)
- Pinia (State Management)
- Vue Router (Advanced Routing)
- Testing (Unit & E2E)
- Performance Optimization Techniques
- Vite & Build Tooling
- Deployment & Environment Configuration

---

## ✅ Who This Is For

- Beginners learning Vue.js from scratch
- Developers transitioning from React or Angular
- Junior to mid-level frontend developers
- Anyone aiming to build production-ready Vue applications

---

## 🧠 Final Notes

This course covers approximately **85–90% of real-world Vue usage**.  
Completing the projects and extending them with TypeScript, Pinia, and Vue Router will make you **job-ready in 2026**.

---

Happy coding! 💚

### Components 
- reusable and self contained unit
- encapsulates a specific functionality or user interface
- fundamental building block of Vue apps for modular code structuring

### Text Interpolation
- process of dynamically binding the data to content of HTML element in your template
- allows you to display value of JS expression or a variable within markup
- Syntax ```{{data}}```

### Attribute Binding
- Binds HTML elements to data in Vue instances
- Old way : ```v-bind:attr```
- New way : ```:attr```

# Vue.js Core Concepts Cheat Sheet

---

## Directives & Data Binding

### `v-for`
Iterates over an array or object and renders a template for each item in the collection.

#### Why use `:key`?
* **Efficient DOM updates:** When Vue renders a list of elements, it uses a **Virtual DOM** to determine the most efficient way to update the actual DOM.
* **Identification:** The key helps Vue identify which elements have changed, been added, or been removed.
* **Performance:** Without a key, Vue may need to recreate the entire DOM structure for each update, which is inefficient.
* **Avoiding Pitfalls:** * Prevents duplicate key warnings in the console.
    * Prevents incorrect rendering when items are rearranged in a list.

### `v-model`
Provides **two-way data binding** between form inputs and component state.

---

## Component Communication

### Props
* Short for **properties**.
* Used to pass data from a **parent component to a child component**.
* Useful for creating reusable or modular components.
* **Note:** Props are **immutable** (read-only for the child).

### Component Events
Used to send data from a **child component to a parent component**.
* **Child:** Uses `$emit` to trigger a custom event carrying the data.
* **Parent:** Uses the `v-on` directive (`@`) to listen for the custom event emitted by the child.

### Provide & Inject
A way to share data from a parent component to **deeply nested** child components without passing props at every level ("Prop Drilling").
* **Provide:** The parent shares the data.
* **Inject:** The child receives the data, even if many levels apart.
* **Use Case:** Mainly for theme settings, global values, or plugins; not for regular parent-child communication.

---

## Slots
A placeholder inside a component that lets you pass content in from the outside.
* **The Concept:** The component is a box 📦; the slot is a hole where you put custom content.
* **Fallback Content:** Default content displayed when no content is provided to the slot.
* **Named Slots:** Labeled spaces (e.g., Header, Body, Footer) so you can decide exactly where specific content goes.

---

## Lifecycle Hooks

| Hook | Description |
| :--- | :--- |
| **onBeforeMount()** | Called right before the component is mounted. State is reactive, but no DOM nodes exist yet. |
| **onMounted()** | Executed after the component is inserted into the DOM. Used for fetching data or setting up event listeners. |
| **onBeforeUpdate()** | Called right before the DOM is updated due to a reactive change. Safe to modify state here. |
| **onUnmounted()** | Called when the component is being removed from the DOM. |

---

## Reactivity & Logic

### Watchers
Watch for changes reactively in a specific property or expression.
* **Syntax:** `watch(source, callback, options)`
* **Source:** Can be a `ref()`, reactive object, array, or getter function.
* **Callback:** Receives `(newVal, oldVal)`.
* **Options:** Includes `immediate`, `deep`, `flush`, and `onTrack/onTrigger`.

### Template Refs
A way to create a reference to a child component or DOM element within a template, allowing direct manipulation in the component logic.

### Composables
A reusable function that packages related state and logic to "plug and play" features across different parts of an app (e.g., `useComposable()`).

---

## Advanced Components & Directives

### Async Components
Components loaded and rendered only when needed.
* **Function:** `defineAsyncComponent()`
* **Benefit:** Optimizes initial load time by splitting large components from the initial bundle.

### Custom Directives
Reusable "low-level" modifiers used to directly manipulate DOM elements (e.g., auto-focusing) via the `v-` attribute prefix.

### Dynamic Components
Allows switching between different components on the fly using a single placeholder.
* **Syntax:** Uses the `<component :is="...">` syntax to render a component based on a variable.
