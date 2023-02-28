# Vue.js

## Glossary

| Terms                 | Description                  |
| --------------------- | ---------------------------- |
| Vue.x                 | State management library     |
| SFC                   | Single File Component …      |
| String template       | Template provided to the component with option `template?:` as string |
| DOM template          | When the template is written in a `*.html file` |
| Directive             | Vue template attributs for magick template action and binding |
| Provide               | To pass a value in deeply descendency |
| Inject                | Catch the value passed by the ancestor with *Provide* |
| Composition API       |	Grâce au tag <script setup> on va pouvoir déclaré l’état, les methodes, le script d’initialisation et le template de manière plus classique au lieu d’exporter un objet. |
| Options API           |	C’est l’inverse de Composition API TODO à préciser |
| Custom element        | Custom template html element |
| Single-File Component |	SFC la logique, le template et le style ensemble, compilé |
| Directive             |	Attribut prefixé par v-qui est une expression javascript qui a accès à l’état du composant. Certains ? peuvent être écrit en raccourci ex : v-bind:id → :id, v-on:click → @click, : pour les propriétés, @ pour les méthodes v-model permet de raccourcir en une seule directive, la synchronisation de la propriété La propriété en directive peut être dynamique v-bind:[attr] ou :[attr] et attr vaut 'id' par exemple (une string ou null) |
| Dynamic argument      | Quand l’attribut est précisé dynamiquement ? Voir Directive. Préférable en basse casse, puisque le navigateur changera la casse au final. |
| Modifier              | On peut ajouter des modifier aux directives, sorte de raccourci de méthode appliquée à la directive, par ex @click.prevent pour lancer event.preventDefault() |
| Ref                   |	Attribut de référence à l’élément, accessible dans le script via this.$refs this.refs.p, accessible seulement après le montage du composant |
| Watcher               |	Des écouteurs de propriétés  |
| Emit                  | Permet à un composant enfant de communiquer avec le parent |
| Slot                  | Permet à composant parent de communiquer avec l’enfant, sorte de *children* |
| nextTick              | Fonction de callback pour s’assurer de faire quelque chose une fois que le DOM a été mis à jour |
| Computed properties   | "They’re similar to methods, except that they should not mutate data.” Ce sont des méthodes, contenu dans l’index computed qui sont dédiées à faire des calculs. On va s’en servir comme de simples propriétés. Donc pas de () on les consulte comme des propriétés. Elles ne doivent pas et ne devrait pas altérer les données. |
| Watcher               |	Méthode qui surveille une propriété (et porte le même nom) seul ou son utilisation. On pourra lancer une action lors de sa modification |

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
