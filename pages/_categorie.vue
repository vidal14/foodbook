<template>
  <main class="main-wrapper">
    <div class="container mx-auto">
      <headingFirst>
        <h1> {{ title }} </h1>
      </headingFirst>
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
  </main>
 
</template>

<script>

import Card from '~/components/Card'
import HeadingFirst from '~/components/HeadingFirst'

export default {
  components: {
    Card,
    HeadingFirst,
  },
  async asyncData({ $content, params }) {
    const docs = await $content('articles').without(['body', 'toc']).where({ 'categories' : { '$contains' : `${params.categorie}` }  }).fetch()
    let title = params.categorie.toUpperCase()
    console.log(params)
    //console.log(docs)
    return { docs, title }
  },

}

</script>

<style scoped>

</style>