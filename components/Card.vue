<template>
  <div class="card-article rounded overflow-hidden">
    <nuxt-link :to="{ path: `recipes/${link}`}">
        <div class="card-image">
        <img :src="`../images/recipes/${image}.jpg`" :alt="title" />
      </div>

       <div class="px-6 py-4">
        <div class="font-bold text-xl mb-2">{{ title }}</div>
        <p class="text-gray-700 text-base">
          {{ description }}
        </p>
      </div>
    </nuxt-link>
  
   
    <div class="card-tags px-6 pt-4 pb-2">
      <nuxt-link
        class="custom-tag inline-block rounded-full px-3 py-1 text-sm mr-2 mb-2"
        v-for="(categorie, index) in categories"
        :key="index"
        :to="{ path: `/${categorie}`, params: `${categorie}`}"
      >
        {{ categorie }}
      </nuxt-link>
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
    image: {
      type: String,
      required: true
    },
  },
  // methods: {
  //   goToDoc(slug) {
  //     this.$router.push({ path: `recipes/${slug}`})
  //   },

  //   goToCategorie(slug) {
  //     this.$router.push({ path: `/${slug}`})
  //   },
  // } 
}
</script>

<style scoped>

  :root {
    --card-image-height: 300px;
  }

  .card-article {
    cursor: pointer;
    background-color: var(--color-light-beige);
    box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
    transition-property: transform, box-shadow;
    transition-timing-function: ease;
    transition-duration: 0.10s;
    position: relative;
  }

  .card-article:hover {
    transform: translateY(-10px);
    box-shadow: 4px 10px 15px -3px rgba(0, 0, 0, 0.2), 0 4px 6px -2px rgba(0, 0, 0, 0.15);
  }

  .card-image {
    width: 100%;
    height: 250px;
    position: relative;
  }

  .card-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

   .card-image::before {
     content: '';
     position: absolute;
     top: 0;
     left: 0;
     width: 100%;
     height: 100%;
     background: rgb(0,0,0);
      background: linear-gradient(180deg, rgba(0,0,0,0.8) 0%, rgba(0,0,0,0.5334908963585435) 15%, rgba(0,0,0,0.12172619047619047) 28%, rgba(255,255,255,0) 39%);
   }

  .card-tags {
    position: absolute;
    top: 0;
    right: 0;
  }

</style>
