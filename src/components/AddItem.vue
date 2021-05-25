<template>
  <form @submit="onSubmit" action="submit" class="add-form">
    <div class="form-control">
      <label for="grocery">Add Item</label>
      <input 
        v-model="item"
        name="item"
        type="text"
      />
    </div>
    <div class="form-control">
      <label for="amount">Amount</label>
      <input 
        v-model="amount"
        name="amount"
        type="text"
      />
    </div>
    <input type="submit" value="Add Item" class="btn btn-block">
  </form>

  
</template>

<script>
import Button from './Buttons/Button'

export default {
  name: 'AddItem',
  components: {
    Button
  },
  data() {
    return {
      item: this.item,
      amount: this.amount,
    }
  },
  props: {
    updatedItem: {
      type: Object
    }
  },
  emits: ['updatedItem'],
  mounted() {
    console.log('this got hit ')
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      if (!this.item) {
        alert('Please add an item')
        return
      }

      const newItem = {
        item: this.item,
        amount: this.amount
      }
      this.$emit('add-item', newItem)

      this.item = '',
      this.amount = ''
    }
  }
}
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>