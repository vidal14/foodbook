<template>
  <div class="mobile-menu">
      <nav class="flex justify-center items-center">
          <ul>
              <li class="mb-1">
                  <nuxt-link to="/">Recetas</nuxt-link>
              </li>
               <li class="mb-6">
                  <nuxt-link to="informacion">Información</nuxt-link>
              </li>
              <li class="mb-1">
                  <button>Search</button>
              </li>
              <pre> {{ isActive }} </pre>
          </ul>
      </nav>
      <button 
        @click.prevent="closeMenu"
        class="button-close">
          Cerrar
      </button>
      <pre> {{ isActive }} </pre>
  </div>
</template>

<script>
export default {
  props: {
    isActive: {
      type: Boolean
    },
  },
  methods: {
    closeMenu() {
      let stateMenu = this.isActive;
      stateMenu = false
      this.$emit("update-menu", stateMenu);
    }
  }
}
</script>

<style scoped>

 .mobile-menu {
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1000;
    background-color: var(--color-dark-gray);
    padding: var(--padding-container);
 }

 .mobile-menu nav {
    width: 100%;
    height: 100%;
 }

 .mobile-menu a,
 .mobile-menu li button {
    font-family: var(--font-family-headings);
    color: var(--color-white);
 }

 .mobile-menu a {
    font-size: 50px;
 }

 .mobile-menu li button {
  font-size: 38px;
 }

 .button-close {
   position: absolute;
   top: var(--padding-container);
   right: var(--padding-container);
   font-size: var(--font-size-lg);
   color: var(--color-white);
 }

</style>
