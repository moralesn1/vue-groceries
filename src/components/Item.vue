<template>
  <div class="item-container">
    <!-- <div v-if="itemEdittingId === item.id"  class="item-description">
    <div>
      <textarea v-model="item.item"></textarea>
      <textarea v-model="item.amount"></textarea>
    </div>
    </div>
    <div v-else @click="setToEditing(item)" class="item-description">
      <h3>{{item.item}}</h3>
      <p>{{item.amount}}</p>    
    </div> -->
    <div class="item-description">
      <h3>{{item.item}}</h3>
      <p>{{item.amount}}</p>    
    </div>

    <div class="item-icons">
      <i @click="$emit('edit-item', item)" class="far fa-edit"></i>
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
  data() {
    return {
      flag: true,
      itemEdittingId: ''
    }
  },
  methods: {
    setToEditing(item) {
      this.itemEdittingId = item.id
    }
  }
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
  width: 100%;
}

textarea {
  margin-top: 10px;
  font-family: 'Poppins', sans-serif;
  width: 100%;
  font-size: 1.17em;
  font-weight: bolder;
  padding-left: 5px;
}

div {
  margin-right: 5px;
}
.item-description {
  width: 100%;
}

.item-icons {
  display: flex;
  flex-direction: column;
  margin-top: 5px;
  margin-bottom: 5px;
}

i.far.fa-edit {
  color: rgb(0, 0, 255);
}

i.fas.fa-trash-alt {
  margin-top: 10px;
  color: rgb(255, 0, 0);
}
</style>