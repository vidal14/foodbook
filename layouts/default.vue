<template>
  <div>
    <header>
        <nav class="main-header container mx-auto flex items-center justify-between flex-wrap p-6">
          <div class="brand">
            <nuxt-link to="/">JUSTCOOK</nuxt-link>
          </div>
          <div class="main-nav flex-grow hidden md:block">
            <div class="flex items-center">
              <nuxt-link to="/">Recetas</nuxt-link>
              <nuxt-link to="informacion">Informacion</nuxt-link>
            </div>
          </div>
          <div class="search-button hidden md:block">
            <SearchBar />
          </div>
          <div class="menu-button md:hidden">
            <button @click='menuMobile = true'>Menu</button>
          </div>
       </nav>
    </header>
  
    <div>
      <nuxt />
    </div>

    <footer class="main-footer">


    </footer>
  
    <MobileMenu v-if="menuMobile" :is-active="menuMobile" @update-menu="updateMenu"/>

  </div>
</template>

<script>
import SearchBar from '~/components/SearchBar'
import MobileMenu from '~/components/MobileMenu'

export default {
  data() {
    return {
      menuMobile: false,
    }
  },
  components: {
    MobileMenu,
    SearchBar
  },
  methods: {
    updateMenu(state) {
      this.menuMobile = state;
    }
  },
  watch: {
    '$route' () {
      this.menuMobile = false
    }
  },
}
</script>  

<style>

  :root {
    --font-family-body: 'Open Sans', sans-serif;
    --font-family-headings: 'Anton', sans-serif;
    --font-family-headings-two: 'Source Serif Pro', serif;

    --font-size-h1: 60px;
    --font-size-xl: 1.25rem;
    --font-size-lg: 1.125rem;
    --font-size-base: 1rem;

    --color-white: #fff;
    --color-dark-gray: #4d4d4d;
    --color-light-beige: #f5f4f3;
    --color-beige: #f3efe3;
    --color-red: #ff6e6e;

    --padding-container: 15px;

    --main-header-height: 100px;
  }

  html {
    font-size: 16px;
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
  }

  *,
  *:before,
  *:after {
    box-sizing: border-box;
    margin: 0;
  }

body {
  font-family: var(--font-family-body);
  background-color: var(--color-beige);
  color: var(--color-dark-gray);
}

h1 {
  font-family: var(--font-family-headings);
  font-size: var(--font-size-h1);
  line-height: 1.2;
}

h2 {
  font-family: var(--font-family-headings);
}

.container {
  padding: 0 var(--padding-container);
}

.main-header {
  height: var(--main-header-height);
}

.main-header .main-nav a {
  font-size: var(--font-size-lg);
  font-weight: 600;
}

.main-header a {
  transition: color 0.15s linear;
}

.main-header a:hover {
  color: var(--color-red);
}

.main-header .brand {
  font-family: var(--font-family-headings);
  font-size: 34px;
  margin-right: 40px;
}

.main-nav a:not(:last-of-type) {
  margin-right: 1rem;
}

footer {
  width: 100%;
  min-height: 200px;
  background-color: var(--color-dark-gray);
  display: none;
}

</style>
