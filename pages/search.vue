<template>
  <main class="main-wrapper">
     <headingFirst>
        <h1>Search</h1>
      </headingFirst>

      <div class="container mx-auto">
          <p>Resultados para la búsqueda: {{textSearch}}</p>

          <div class="grid-full">
          <card
            v-for="(doc, index) in docs"
            :key="index"
            :title="doc.title"
            :description="doc.description"
            :link="doc.slug"
            :image="doc.picture"
            :categories="doc.categories"
          >
          </card>
      </div>
      </div>

      

       <!-- <pre> {{docs}}</pre> -->
  </main>
</template>

<script>
import Card from '~/components/Card'
import HeadingFirst from '~/components/HeadingFirst'

export default {
  components: {
    HeadingFirst,
     Card,
  },
  
  async asyncData({ $content, query }) {
   
    let textSearch = query.recipes
    //const docs = await $content('articles').without(['body', 'toc']).where({ 'categories' : { '$contains' : `${query.recipes}` }  }).fetch()
    const docs = await $content('articles').without(['body', 'toc']).search(`${query.recipes}`).limit(10).fetch()
    return { docs, textSearch }
  },
    
}
</script>

<style>

</style>
