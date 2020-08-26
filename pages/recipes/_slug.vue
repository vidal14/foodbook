<template>
    <div class="container mx-auto">
      <div class="header-recipe">
        <h1> {{ doc.title }}</h1>
        <img class="w-full" src="https://images.unsplash.com/photo-1490645935967-10de6ba17061?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1335&q=80" :alt="doc.title">
      </div>
        <nuxt-content :document="doc" />
    </div>
 
</template>

<script>

export default {
  async asyncData({ $content, params }) {
    const doc = await $content(`/articles/${params.slug}`).fetch()
    return { doc }
  },
}
</script>

<style scoped>
  h1 {
    font-size: 80px;
  }
</style>