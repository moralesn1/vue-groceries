<template>
<div class="container">
  <h3>Grocery List</h3>
  <AddItem />
</div>
</template>

<script>
import AddItem from '@/components/AddItem.vue'

export default {
  name: 'HelloWorld',
  components: {
    AddItem
  },
  props: {
  },
  data() {
    return {
      counter: 0
    }
  },
  methods: {
  }
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
  justify-content: center;
}


</style>
