<template>
<div class="home">
    <Items :items="items"/>
</div>
</template>

<script>
import AddItem from '@/components/AddItem.vue'
import Items from "@/components/Items.vue"

export default {
  name: 'Groceries',
  components: {
    AddItem,
    Items
  },
  props: {
    items: {
      type: Array
    }
  },
  method: {
  },
  // emits: ['add-item']
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
