
# VueTheme - Vue.js Boilerplate Theme for Wordpress
WordPress boilerplate theme using [WP REST API](https://developer.wordpress.org/rest-api/), [VueJs 2](http://vuejs.org), [Vue Ruter](https://router.vuejs.org/), [Vuex](https://vuex.vuejs.org/), and [Axios](https://github.com/axios/axios). Inspired on [rtCamp](https://github.com/rtCamp/VueTheme)'s solution.

## Installation
1. This is a regular WP theme. Install it from the admin.
2. Add `define( 'VUE_DEV', true );` in `wp-config.php` to get asset files from webpack dev server.
3. To start dev server with hot reload `npm run dev`. You will need also a PHP server. See webpack.config.js
5. To create build for production with minification `npm run build` and set `define( 'VUE_DEV', false );`

## Theme Directory basic structure
```
/admin
/php
  /lib
/src
  /assets 
  /components
  /sass
      /resources
axios.js
filters.js 
main.js
router.js
store.js 
config.ini
```

## Router
The following elements are automated and exposed to Vue Router:
* Posts singles -> PostSingle.vue 
* CPT Singles -> CptnameSingle.vue
* Pages -> Page.vue
* Pages with template -> PageTemplateName.vue. Since we are not using php templates, page templates are set in `config.ini`.

Other components must be set in router.php

## WordPress
Go to `/php` to set the WordPress functionality like any other theme. All files in the root of `/php` directory are included automatically. Use  `/php/lib` for classes and libraries.

## Custom cache
There's a custom cache class for heavy queries, like the router or the menus. It works with other caching tools, such as WP Rocket. You can customize when to flush the cache when you save it (for example when save pages, or a certain post type).

## Webpack
Edit your build and dev public path in `webpack.config.js`. 
````
if (process.env.NODE_ENV == 'development') {
  var buildPublicPath = '/dist/';
} else {
  var buildPublicPath = '/wp-content/themes/VueTheme/dist/';
}
````

## SASS & Mixins in Vue components
If you ever used Vue.js, you know it can be tricky to use scss mixins in Vue components. For that reason, we use `sass-resources-loader` to preload scss resources.

Any sass file included in `/src/assets/sass/resources` will be preloaded and available everywhere, vue components included.


## Next
* Expose Achives, Categories, tags to Vue Router.
* Automatic edit of SCRIPTS_VERSION in config.init each time we `npm run build`
* Nuxt.js ?
