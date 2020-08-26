<template>
  <div class="container mx-auto">
    <!-- <pre> {{ docs }}</pre> -->
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
import Logo from '~/components/Logo.vue'
import Card from '~/components/Card'

export default {
  components: {
    Logo,
    Card,
  },
  async asyncData({ $content }) {
    // const docs = await $content('/articles').without(['body', 'toc']).where({ 'categorie' : { '$in' : ['postres', 'vegan'] }  }).fetch()
    const docs = await $content('/articles').without(['body', 'toc']).fetch()
    return { docs }
  },
  methods: {
    goToDoc(slug) {
      this.$router.push({ path: `recipes/${slug}`})
    },
  }
}
</script>

<style scoped>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

.container {
  margin-top: 5rem;
  margin-bottom: 5rem;
}

.grid-full {
  display: grid;
  grid-template-columns: repeat(4, 25rem);
  row-gap: 10px;
  column-gap: 10px;
}
</style>
