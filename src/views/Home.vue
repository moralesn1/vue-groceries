<template>
  <div class="container">
    <Header 
      @toggle-show-item-form="toggleShowItemForm"
      :showAddForm="showAddForm"
    />
    <AddItem v-show="showAddForm"
      @add-item="addItem"
      @update-item="updateItem"
      :toggleEditForm="toggleEditForm"
      :currentItem="currentItem"
    />
    <Items 
      :items="items" 
      @delete-item="deleteItem"
      @id-for-updating="itemIdforUpdating"
    />
  </div>
</template>

<script>
// @ is an alias to /src
import Header from '@/components/Header.vue'
import Items from '@/components/Items.vue'
import AddItem from '@/components/AddItem.vue'

export default {
  name: 'Home',
  components: {
    Items,
    AddItem,
    Header
  },
  data() {
    return {
      items: [],
      toggleEditForm: false,
      toggleAddItem: true,
      currentItem: {},
      showAddForm: true,
    }
  },
  props: {
    item: {
      type: Object
    }
  },                           
  methods: {
    toggleShowItemForm() {
      this.showAddForm = !this.showAddForm;
      console.log('hit')
    },
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
    itemIdforUpdating(item) {
      this.currentItem = item;
      this.toggleEditForm = !this.toggleEditForm
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

        this.toggleEditForm = !this.toggleEditForm

        return data
    
      } catch(e) {
        alert('Error updating item')
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
  min-width: 300px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

h3 {
  display: flex;
  margin-top: 5px;
}

@media only screen and (max-width: 500px) {
  .container {
    margin: 10px;
  }
}


</style>
