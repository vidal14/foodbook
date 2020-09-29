<template>
  <main class="main-wrapper">
     <headingFirst>
        <h1>Search</h1>
      </headingFirst>

      <div class="container mx-auto">
          <p>Resultados para la búsqueda: {{searchQuery}}</p>
          <pre> {{searchQuery}} </pre>
          <pre> {{prueba}} </pre>

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

      

       <pre> {{docs}}</pre>
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
  data() {
      return {
        articles: [],
        searchQuery: '',
        prueba: 'cremas'
      }
  },
  async asyncData({ $content, params }) {
    //const docs = await $content('/articles').without(['body', 'toc']).where({ 'categories' : { '$contains' : 'vegan' }  }).fetch()
   console.log('recetas')
   
    console.log($content)
    // const docs = await $content('articles').without(['body', 'toc']).limit(6).search(this.searchQuery).fetch()
    const docs = await $content('articles').without(['body', 'toc']).where({ 'categories' : { '$contains' : 'cremas' }  }).fetch()
    // console.log(docs.categories)
    return { docs }
  },
 created() {
    this.searchQuery = this.$route.query.recipes;
    console.log(this.searchQuery)
    console.log(this.prueba)
  },
    
//   methods: {
//     submitResults() {
//       console.log(this.$route.query.recipes)
//       console.log(this.articles)
//       this.$router.push({ path: '/search', query:{recipes: this.articles} });
//     }
//   },
}
</script>

<style>

</style>
