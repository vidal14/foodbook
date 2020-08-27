<template>
  <ul class="categorie-list">
     <li
      v-for="(recipe, index) in recipes"
      :key="index"
      >
        <nuxt-link
        class="custom-tag inline-block px-3 py-1 mr-2 mb-2"
        to="/"
        >
        {{ recipe.categories }}
      </nuxt-link>
     </li>
     <!-- <pre>{{ categories }}</pre> -->
  </ul>
</template>
<script>
  export default {
    props: {
      recipes: {
        type: Array,
        required: true
      },
      categories: '',
    },
    // methods: {
    //     filterCategories() {
    //         this.recipes.filter(recipe => {
    //             this.categories = 'hola'
    //             console.log(categories)
    //             return this.categories
    //         })
    //     }
    // }
  }
</script>

<style scoped>

 .categorie-list {
    display: flex;
    align-items: center;
    margin-bottom: 50px;
 }

 .custom-tag {
    padding: 20px 30px;
    border-radius: 6px;
    font-size: 18px;
    background: var(--color-dark-gray);
 }

  .custom-tag:hover {
    background: var(--color-red);
 }

</style>
