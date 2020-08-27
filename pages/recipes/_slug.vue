<template>
  <main class="main-wrapper">
     <div class="container mx-auto">
      <div class="recipe-header">
        <div class="categorie-list text-center">
          <nuxt-link
            class="custom-tag inline-block rounded-full px-3 py-1 text-sm mr-2 mb-2"
            v-for="(categorie, index) in doc.categories"
            :key="index"
            :to="{ path: `/${categorie}`, params: `${categorie}`}">
            {{ categorie }}
          </nuxt-link>
        </div>
        <h1 class="text-center"> {{ doc.title | uppercase }}</h1>
        <div class="recipe-image">
          <img :src="`../images/recipes/${doc.picture}.jpg`" :alt="doc.title">
        </div>
        
      </div>

      <div class="recipe-content">
        <div class="recipe-ingredients">
          <h2>Ingredientes</h2>
          <ul class="ingredients-list">
            <li
            v-for="(ingredient, index) in doc.ingredients"
            :key="index"
            >
            {{ ingredient }}
            </li>
          </ul>
        </div>
        <div class="recipe-steps">
          <nuxt-content :document="doc" />
        </div>
      </div>
    </div>
  </main>
   
 
</template>

<script>

export default {
  async asyncData({ $content, params }) {
    const doc = await $content(`/articles/${params.slug}`).fetch()
    return { doc }
  },

  filters: {
    uppercase: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.toUpperCase()
    }
  }
}
</script>

<style scoped>

  .main-wrapper {
    padding-bottom: 0;
  }

  h1 {
    margin-bottom: 40px;
  }

  h2,
  .nuxt-content h2 {
    font-size: 28px;
    margin-bottom: 20px;
  }

  .recipe-image {
    width: 100%;
    height: 550px;
  }

  .recipe-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .recipe-content {
    display: grid;
    grid-template-columns: 400px auto;
  }

  .recipe-ingredients,
  .recipe-steps {
    padding: 50px 40px;
  }

  .recipe-ingredients {
    background-color: #f1e7c9;
  }

  @media (max-width: 1024px) {
    .recipe-content {
      grid-template-columns: 1fr;
    }
  }
</style>