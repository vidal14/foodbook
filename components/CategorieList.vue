<template>
  <div class="container mx-auto">
    <ul class="categorie-list">
      <li
        v-for="(categorie, index) in categories"
        :key="index"
        >
          <nuxt-link
          class="custom-tag inline-block px-3 py-1 mr-2 mb-2"
          :to="{ path: `/${categorie}`}"
          >
          {{ categorie | capitalize }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>
<script>
  export default {
    data: function () {
        return {
            categories: [
            'vegetariana',
            'postres',
            'cremas',
            'entrantes',
          ],
        }
    },
    props: {
      recipes: {
        type: Array,
        required: true
      },
    },
    filters: {
    capitalize: function (value) {
      if (!value) return ''
      value = value.toString()
      return value.charAt(0).toUpperCase() + value.slice(1)
    }
   },
  }
</script>

<style scoped>

 .categorie-list {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 50px;
    padding-bottom: 0.6rem;
    flex-wrap: wrap;
 }

 .custom-tag {
    padding: 17px 30px;
    border-radius: 6px;
    font-size: 18px;
    background: transparent;
    border: 2px solid var(--color-dark-gray);
    color: var(--color-dark-gray);
    box-shadow: 2px 6px 13px -6px rgba(0,0,0,0.52);
 }

  .custom-tag:hover {
    background: var(--color-red);
    border-color: var(--color-red);
    color: var(--color-white);
 }

 @media (max-width: 798px) {
    .container {
      padding: 0;
    }

    .categorie-list {
      justify-content: flex-start;
      padding-left: 15px;
      flex-wrap: nowrap;
      overflow-x: auto;
    }
 }

</style>
