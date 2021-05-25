<template>
  <div class="items-container" :key="item.id" v-for="item in items">
    <Item 
      :item="item" 
      @delete-item="$emit('delete-item', item.id)"
      @edit-item="$emit('edit-item', item)"
    />
    
  </div>
</template>

<script>
import Item from './Item'

export default {
  name: 'Items',
  components: {
    Item
  },
  props: {
    items: {
      type: Array
    }
  },
  emits: ['delete-item', 'edit-item']
}
</script>

<style scoped>
</style>