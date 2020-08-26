<template>
  <div class="card-article rounded overflow-hidden shadow-lg" @click="goToDoc(link)">
    <img class="w-full" src="https://images.unsplash.com/photo-1490645935967-10de6ba17061?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1335&q=80" :alt="title" />
    <div class="px-6 py-4">
      <div class="font-bold text-xl mb-2">{{ title }}</div>
      <p class="text-gray-700 text-base">
        {{ description }}
      </p>
    </div>
    <div class="px-6 pt-4 pb-2">
      <span
        class="inline-block bg-gray-200 rounded-full px-3 py-1 text-sm font-semibold text-gray-700 mr-2 mb-2"
        v-for="(categorie, index) in categories"
        :key="index"
      >
        {{ categorie }}
      </span>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    description: {
      type: String,
      required: true
    },
    link: {
      type: String,
      required: true
    },
    categories: {
      type: Array,
      required: true
    },
  },
  methods: {
    goToDoc(slug) {
      this.$router.push({ path: `recipes/${slug}`})
    },
  } 
}
</script>

<style scoped>
  .card-article {
    cursor: pointer;
  }

</style>
