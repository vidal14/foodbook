<template>
  <div class="container mx-auto">
    <h1>DON'T THINK ONLY COOK</h1>
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
    //const docs = await $content('/articles').without(['body', 'toc']).where({ 'categories' : { '$contains' : 'vegan' }  }).fetch()
    const docs = await $content('/articles').without(['body', 'toc']).fetch()
    return { docs }
  },
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/

@import url('https://fonts.googleapis.com/css2?family=Anton&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Source+Serif+Pro:wght@400;600&display=swap');

:root {
  --font-family-headings: 'Anton', sans-serif;
  --font-family-headings-two: 'Source Serif Pro', serif;

  --font-size-h1: 60px;
}

h1 {
  font-family: var(--font-family-headings);
  /* font-weight: 600; */
  font-size: var(--font-size-h1);
}

h2 {
  font-family: var(--font-family-headings);
}

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

.nuxt-content h2 {
  font-size: 28px;
  margin-bottom: 20px;
}

.nuxt-content > p {
  margin-bottom: 40px;
}

</style>
