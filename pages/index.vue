<template>
  <main class="main-wrapper">
    <div class="container mx-auto">
      <headingFirst>
        <h1>DON'T THINK JUST COOK </h1>
      </headingFirst>
      <categorieList :recipes="docs"></categorieList>

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
import CategorieList from '~/components/CategorieList'

export default {
  components: {
    Card,
    HeadingFirst,
    CategorieList,
  },
  async asyncData({ $content }) {
    //const docs = await $content('/articles').without(['body', 'toc']).where({ 'categories' : { '$contains' : 'vegan' }  }).fetch()
    const docs = await $content('/articles').without(['body', 'toc']).fetch()
    console.log(docs.categories)
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

.main-wrapper {
  padding: 6rem 0;
}

.grid-full {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  row-gap: 30px;
  column-gap: 15px;
}

.custom-tag {
  background-color: var(--color-red);
  color: var(--color-dark-gray);
  font-weight: 600;
  color: var(--color-white);
  transition-property: background-color, color, border-color;
  transition-duration: 0.125s;
  transition-timing-function: linear;
}

@media (max-width: 1024px) {
  .grid-full {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 698px) {
  .grid-full {
    grid-template-columns: 1fr;
  }
}


.custom-tag:hover {
  background-color: var(--color-dark-gray);
}

/* NUXT CONTENT */

.nuxt-content h2 {
  font-size: 28px;
  margin-bottom: 20px;
}

.nuxt-content > p,
.nuxt-content > ul {
  margin-bottom: 40px;
}

.nuxt-content ul,
.ingredients-list {
  padding-left: 20px;
}

.nuxt-content ul li,
.ingredients-list li {
  list-style: disc;
  margin-bottom: 0.5rem;
}

</style>
