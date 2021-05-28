<template>
  <form 
    v-if="toggleEditForm" 
    :currentItem="currentItem" 
    @submit="onEdit" 
    action="submit" class="add-form"
    >
    <div class="form-control">
      <label for="grocery">Edit Item</label>
      <input 
        v-model="currentItem.item"
        name="item"
        type="text"
      />
    </div>
    <div class="form-control">
      <label for="amount">Edit Amount</label>
      <input 
        v-model="currentItem.amount"
        name="amount"
        type="text"
      />
    </div>
    <input type="submit" 
      value="Save Changes" 
      class="btn btn-block edit"
    >
  </form>
  <form 
    v-else 
    @submit="onSubmit" 
    action="submit" 
    class="add-form"
  >
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
    <input 
      type="submit" 
      value="Add Item" 
      class="btn btn-block submit"
    >
  </form>
</template>

<script>

export default {
  name: 'AddItem',
  data() {
    return {
      item: this.item,
      amount: this.amount,
      editItem: this.currentItem.item,
      editAmount: this.currentItem.amount,
      toggleForm: this.toggleEditForm
    }
  },
  props: {
    currentItem: {
      type: Object
    },
    toggleEditForm: {
      type: Boolean
    },
  },
  emits: ['currentItem', 'add-item', 'update-item', 'onSuccess'],
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
    },
    onEdit(e) {
      e.preventDefault();

      if (!this.currentItem.item) {
        alert('Please add an item')
        return
      }

      const updatedItem = {
        id: this.currentItem.id,
        item: this.currentItem.item,
        amount: this.currentItem.amount
      }

      this.$emit('update-item', updatedItem)
      e.target.reset()

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

input {
  font-family: 'Roboto', sans-serif;
}

input.btn.btn-block.edit {
  background-color: rgb(0, 168, 0);
}

input.btn.btn-block.submit {
  background-color: #0000ff;
}


</style>