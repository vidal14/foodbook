<template>
    <div class="container mx-auto">
      <h1> {{ title }} </h1>
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
 
</template>

<script>

import Card from '~/components/Card'

export default {
  components: {
    Card,
  },
  async asyncData({ $content, params }) {
    const docs = await $content('/articles').without(['body', 'toc']).where({ 'categories' : { '$contains' : `${params.categorie}` }  }).fetch()
    let title = params.categorie.toUpperCase()
    console.log(title)
    console.log(docs)
    return { docs, title }
  },

}

</script>

<style scoped>
  h1 {
    font-size: 80px;
  }
</style>