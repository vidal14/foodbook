<template>
  <div class="container">
    <!-- <pre> {{ docs }}</pre> -->
    <div class="grid-full">
      <card
        v-for="(doc, index) in docs"
        :key="index"
        :title="doc.title"
        :description="doc.description"
        :link="doc.slug"
        :image="doc.picture"
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

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}

.grid-full {
  display: grid;
  grid-template-columns: repeat(4, 25rem);
  row-gap: 10px;
  column-gap: 10px;
}
</style>
