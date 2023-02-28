# Vue.js

## My vue.js style guide notes

[Source](https://vuejs.org/style-guide/)

### Rules categories

| Priorities   | Description                                 |
| ------------ | ------------------------------------------- |
| A            | Preventing errors                           |
| B            | Strongly recommended                        |
| C            | Recommended                                 |
| D            | Use with caution, recommended in some cases |

### Priority: A

- Use multi-word component names
- Use detailed prop definitions
- Add `:key` with `v-for`
- Avoid `v-if` with `v-for` (put it upper or use a computed function already filtering)
- Use component scoped styling

### Priority: B

- Component should be in its own file
- SFC (Single File Component) filename : should always be **PascalCase** | **kebab-case**
- Base components (generics) should begin with a specific prefix like : `Base`, `App`, `V`
- Component appear once in application should have `The` prefix in their filename
- Child component filename should include the parent component name as prefix
- Component names should have the most high context on the left, and the more precise and action on the right
- Self-closing components
  - In DOM templates : **never**
  - Other : Without child always
- Component name casing in templates : should be in **PascalCase** in SFC & *String template*,
  but **kebab-case** in DOM templates
- Component name casing in js/jsx should alway be **PascalCase**
- Component names should prefer full words over abbreviations
- **Prop name** :
  - should always use camelCase in declaration
  - **kebab-case** in *DOM template*
- Element with **multiple attributes** should span multilpe lines
- Avoid complex expressions in templates
- Keep computed properties simple, split it if necessary
- Always use quotes for attributes
- Directive shorthands should be used always or never

### Priority: C

#### Component/instance options order

> This is the default order we recommend for component options.
> They're split into categories, so you'll know where to add new properties from plugins.

1. `name`
2. `compilerOptions`
3. `components` & `directives`
4. `extends`, `mixins` & `provide`/`inject`
5. `inheritAttrs`, `props`, `emits`
6. `setup`
7. `data`, `computed`
8. `watch`, `beforeCreate`, `created`, `beforeMount`, `mounted`, `beforeUpdate`, `updated`, `actived`, `deactivated`, `beforeUnmount`, `unmounted`, `errorCaptured`, `renderTracked`, `renderTriggered`
9. methods
10. `template`/`render`

#### Element attribute order

1. `is`
2. `v-for`
3. `v-if`, `v-else-if`, `v-else`, `v-show`, `v-cloak`
4. `v-pre`, `v-once`
5. `id`
6. `ref`, `key`
7. `v-model`
8. Other attributes (all unspecified bound & unbound attributes)
9. `v-on`
10. `v-html`, `v-text`

#### Add space between each properties, taking care of vim users 💚

#### SFC top level order -> `<script>`, `<template>` & `<style>`

### Priority: D

- Element selectors should be avoided with `scoped`
- *Props* & *events* should be preferred for parent & child communication
