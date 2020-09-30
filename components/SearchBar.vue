<template>
    <div class="search-container relative">
        <input
        v-model="searchQuery"
        v-on:keyup.enter="submitResults"
        type="search"
        autocomplete="off"
        placeholder="Buscar Recetas"
        class="search-input"
        />
        <ul class="search-results-dropdown" v-if="articles.length">
            <li v-for="article of articles" :key="article.slug">
                <NuxtLink :to="{ path: `recipes/${article.slug}`}">
                {{ article.title }}
                </NuxtLink>
            </li>
        </ul>
        <!-- <pre> {{ articles }}</pre> -->
    </div>

</template>

<script>
  export default {
    data() {
      return {
        searchQuery: '',
        articles: []
      }
    },
    methods: {
      submitResults() {
        console.log('busqueda resultados')
        console.log($nuxt.$route.name)
        console.log(this.searchQuery)
        //this.$router.go({ path: '/search', query:{recipes: this.searchQuery}, force: true})
        // if ($nuxt.$route.name != 'search') {
          this.$router.push({ path: '/search', query:{recipes: this.searchQuery} })
        // } else {
        //   this.$router.go({ path: '/search', query:{recipes: this.searchQuery}, force: true })
        // }
      }
    },
    watch: {
      async searchQuery(searchQuery) {
        if (!searchQuery) {
          this.articles = []
          return
        }
        this.articles = await this.$content('articles')
          .without('body')
          .limit(6)
          .search(searchQuery)
          .fetch()
      }
    }
  }
</script>

<style scoped>
    .search-input {
      border-bottom: 2px solid var(--color-dark-gray);
      padding: 0.3rem 0;
      background-color: transparent;
      color: var(--color-dark-gray);
      font-size: 18px;
      font-weight: 600;
      outline: 0;
      min-width: 300px;
    }

    .search-input:focus {
      border-color: var(--color-red);
    }

    input[type=search]::placeholder {
      color: var(--color-dark-gray) !important;
    }

    .search-results-dropdown {
      position: absolute;
      top: calc(100% + 15px);
    }

</style>
