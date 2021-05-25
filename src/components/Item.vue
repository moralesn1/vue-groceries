<template>
  <div class="item-container">
    <div class="item-description">
      <h3>{{item.item}}</h3>
      <p>{{item.amount}}</p>
    </div>
    <div class="item-icons">
      <!-- <i @click="emitEvent(item)" class="far fa-edit"></i> -->
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
      flag: true
    }
  },
  methods: {
    // emitEvent() {
    //   this.eventBus.emit('emit-event', item)
    // }
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

.item-description {
  width: 100%;
}

.item-icons {
  display: flex;
  flex-direction: column;
  padding-top: 5px;
  margin-bottom: 5px;
}

i.far.fa-edit {
  color: rgb(0, 0, 255);
}

i.fas.fa-trash-alt {
  padding-top: 10px;
  color: rgb(255, 0, 0);
}
</style>