<template>
  <div>
    <header>
        <nav class="main-header container mx-auto flex items-center justify-between flex-wrap p-6">
          <div class="brand">
            <nuxt-link to="/">JUSTCOOK</nuxt-link>
          </div>
          <div class="main-nav flex-grow">
            <div class="flex items-center">
              <nuxt-link to="/">Recetas</nuxt-link>
              <nuxt-link to="/informacion">Informacion</nuxt-link>
            </div>
          </div>
          <div class="search-button">
            <SearchBar />
          </div>
       </nav>
    </header>
  
    <div>
      <nuxt />
    </div>

    <footer class="main-footer">


    </footer>

  </div>
</template>

<script>
import SearchBar from '~/components/SearchBar'

export default {
  components: {
    SearchBar,
  },
}
</script>  

<style>
  @import url('https://fonts.googleapis.com/css2?family=Anton&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Source+Serif+Pro:wght@400;600&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;600;700&display=swap');

  :root {
    --font-family-body: 'Open Sans', sans-serif;
    --font-family-headings: 'Anton', sans-serif;
    --font-family-headings-two: 'Source Serif Pro', serif;

    --font-size-h1: 60px;

    --color-white: #fff;
    --color-dark-gray: #4d4d4d;
    --color-light-beige: #f5f4f3;
    --color-beige: #f3efe3;
    --color-red: #ff6e6e;

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
}

h2 {
  font-family: var(--font-family-headings);
}

.container {
  padding: 0 15px;
}

.main-header {
  height: var(--main-header-height);
}

.main-header .main-nav a {
  font-size: 1.25em;
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
