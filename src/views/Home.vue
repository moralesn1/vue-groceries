<template>
  <div class="container">
    <h3>Grocery List</h3>
    <AddItem @add-item="addItem" />
    <Groceries :items="items" />
  </div>
</template>

<script>
// @ is an alias to /src
import Groceries from '@/components/Groceries.vue'
import AddItem from '@/components/AddItem.vue'



export default {
  name: 'Home',
  components: {
    Groceries,
    AddItem
  },
  data() {
    return {
      items: []
    }
  },
  methods: {
  async addItem(item) {
    const response = await fetch('http://localhost:5000/items', {
      method: 'POST',
      headers: {
        'Content-type': 'application/json'
      },
      body: JSON.stringify(item)
    })

    const data = await response.json()

    this.items = [...this.items, data]

  },
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

<style>


.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

h3 {
  display: flex;
}
</style>
