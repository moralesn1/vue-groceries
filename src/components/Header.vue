<template>
  <div class="header">
    <h3>Grocery List</h3>
      <Button 
        @btn-click="$emit('toggle-show-item-form')"
        :btnText="showAddForm ? 'Close' : 'Add an Item'"
        :color="showAddForm ? '#ff0000' : '#249900' "
      />
  </div>
  
</template>



<script>
import Button from './Buttons/Button'
  export default {
    name: 'Header',
    components: {
      Button
    },
    props: {
      showAddForm: {
        type: Boolean
      }
    }
  }
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
}
</style>