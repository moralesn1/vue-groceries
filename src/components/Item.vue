<template>
  <div class="item-container">
    <div>
      <h3>{{item.item}}</h3>
      <p>{{item.amount}}</p>
    </div>
    <div class="item-icons">
      <i @click="$emit('delete-item', item.id)" class="fas fa-trash-alt"></i>
    </div>

  </div>
</template>

<script>
export default {
  name: 'Item',
  props: {
    item: {
      type: Object
    }
  },
}
</script>

<style scoped>
.item-container {
  margin: 10px 0px 10px 0px;
  padding-left: 5px;
  padding-right: 5px;
  border: 1px solid black;
  border-radius: 5px;
  display: flex;
  justify-content: space-between;
}
</style>