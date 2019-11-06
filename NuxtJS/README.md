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
 ---
## Custom Error Pages

- jsut create `error.vue` in the **layout** folder

## Difference between VUE and NUXT in getting API
- Using **axios** in vue, we use `mounted()` function to get APIs
- in Nuxt we use **asyncdata()** to get API and that  will be SSR
- we can't use `this.something` in asyncdata instead we use `context.something`
-   For Ex: `this.posts =` instead we use `context.posts`
- **asyncdata** runs in both server and client side


> Need to make defaut data() method. This will be merged/synced with data returning from asynData() method.

## Async Await
- use async keyword before asyncData() method to denote this is an async task 
- and `await` keyword before API request to wait for the data retrival.


```
async aysncData() {
    let res = await axios.get('API URL GOES HERE')
    return {posts: res.data}
} 
```
> Note: Don't forgot import axios if axios used to call API

## Page Head Section

- Can take control over each page <head> section using `head: { ... }` in the script area.
- Ex: 
```
<script>
export default {
    head: {
        title: 'My Custom Title'
    }
}
```

## Fetch method

- **Fetch()** works pretty much similar to asyncData(). The only difference is instead of rendering data to the page, we populate the data store using this method.
- Ex: 
```
<script>
export default {
  async fetch ({ store, params }) {
    let { data } = await axios.get('http://my-api/stars')
    store.commit('setStars', data)
  }
}
</script>
```

> Tip: Use **`** backtick to easy usage with variables and text together.

## Veux Store

```
async aysncData({store}) {
    let res = await axios.get('API URL GOES HERE')
    store.dispatch('setPosts', posts);
} 
```
- instead of rendering to the page. We populated vuex store using the above example. 
- we called `setPosts` function using `store.dispatch()` method. 
- to get the data from vuex store we call getter function from store in `computed: {}`

```
computed: {
    allPosts() {
        return this.$store.getters.posts
    }
}
```
- the above example will call getters function from vuex store. 
- we can also use `mapGetters` from vuex to make the code leaner.
    > import {mapGetters} from 'vuex'

then same above code can be simplified as
```
computed: {
    ...mapGetters(['posts'])
}
```






