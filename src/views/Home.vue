<template>
  <div class="home">
    <Groceries :items="items"/>

  </div>
</template>

<script>
// @ is an alias to /src
import Groceries from '@/components/Groceries.vue'


export default {
  name: 'Home',
  components: {
    Groceries,
  },
  data() {
    return {
      items: []
    }
  },
  methods: {
    async fetchItems() {
      const response = await fetch('http://localhost:5000/items')
      const data = await response.json()
      return data
    }
  },
  async created() {
    this.items = await this.fetchItems()
  }
}
</script>
