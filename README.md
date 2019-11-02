# NUXTJS with Laravel api

**Laravel API Development** with **Nuxt JS** as a **frontend framework** that helps you build powerful **Server Side Rendered Vue js applications with Vuex** in a best possbile way.

## Why Nuxt?
- NuxtJS is a framework  for VueJs
- SSR Built-in
- Page based routing
- Pre-rendered before serving to client
- SEO support
- Benefits of **SPA** and **SSR** together.

## Types of Applications can be built

- Universal App
- Single Page App (SPA)
- Static Websites

## Basic Routing

- Creating page with .vue extension will be routed automatically

```
|-- pages
    |-- index.vue
    |-- about.vue
```

## Nested Routing

```
|-- pages
    |-- index.vue
    |-- about.vue
|-- | -- users
		 | -- index.vue
		 | -- _id.vue
```
- Pages can be grouped inside the folder for usability. Inside the folder should create **`index.vue`**
- (_)underscore followed by page id should be used for dynamic or nested routing. **`_id.vue`**
- And nesting can be go deeper as well. The structure rule is same.

```
|-- pages
    |-- index.vue
    |-- about.vue
    | -- users
		 | -- _id
			  | -- index.vue
```

### Route Parameters

	$route.params.id
we can get route parameter using this variable.

## Nuxt-child component

- Nuxt child component used to repeat the component to its all related pages. For example if we want to show some component only for user group of pages.
	 1. File name should match with the folder name we want to use
	 2. Should use tag `<nuxt-child />`
