<template>
  <div :key="item.id" v-for="item in items">
    <Item :item="item" />
    
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
  }
}
</script>