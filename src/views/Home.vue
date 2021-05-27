<template>
  <div class="container">
    <h3>Grocery List</h3>
    <AddItem 
      @add-item="addItem"
      @update-item="updateItem"
      @onSuccess="showEditForm = false"
      :currentItem="currentItem"
    />
    <Items 
      :items="items" 
      @delete-item="deleteItem"
      @edit-item="editItem"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import Items from '@/components/Items.vue'
import AddItem from '@/components/AddItem.vue'

export default {
  name: 'Home',
  components: {
    Items,
    AddItem,
  },
  data() {
    return {
      items: [],
      showEditForm: false,
      currentItem: {}
    }
  },
  props: {
    item: {
      type: Object
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
  editItem(item) {

    const singleItem = item;
    this.currentItem = singleItem;
    this.showEditForm = !this.showEditForm

  },
  async updateItem(item) {
    try {
      const response = await fetch(`http://localhost:5000/items/${item.id}`, {
      method: 'PUT',
      headers: {
        'Content-type': 'application/json'
      },
      body: JSON.stringify(item)
      })
      const data = await response.json();
      return data
    } catch(e) {
      console.log(e)
    }
  },
  async deleteItem(id) {
    if(confirm('Are you sure?')) {
      const response = await fetch(`http://localhost:5000/items/${id}`, {
        method: 'DELETE'
      })
      
      response.status === 200 ? 
        (this.items = this.items.filter((item) => item.id !== id))
        :
        alert('Error deleting item')

    }
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
