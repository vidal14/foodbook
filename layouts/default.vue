<template>
  <div>
    <nav class="flex items-center justify-between flex-wrap bg-gradient-to-r from-orange-400 to-orange-300 p-6">
      <div class="flex items-center flex-shrink-0 text-white mr-6">
        <span class="font-semibold text-xl tracking-tight">FoodBook</span>
      </div>
      <div class="block lg:hidden">
        <button
          class="flex items-center px-3 py-2 border rounded text-teal-200 border-teal-400 hover:text-white hover:border-white">
          <svg class="fill-current h-3 w-3" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
            <title>Menu</title>
            <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z" />
          </svg>
        </button>
      </div>
      <div class="w-full block flex-grow lg:flex lg:items-center lg:w-auto">
        <div class="text-sm lg:flex-grow">
          <nuxt-link to="/">Inicio</nuxt-link>
          <!-- <nuxt-link to="/">Informacion</nuxt-link> -->
        </div>
      </div>
    </nav>
    <div>
      <nuxt />
    </div>

    <footer class="bg-gradient-to-r from-orange-400 to-orange-300">


    </footer>

  </div>
</template>

<style>
  html {
    font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
      Roboto, 'Helvetica Neue', Arial, sans-serif;
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

  footer {
    width: 100%;
    min-height: 400px;
  }

</style>
