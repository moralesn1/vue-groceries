<template>
  <div class="item-container">
    <div class="item-description">
      <h3>{{item.item}}</h3>
      <p>{{item.amount}}</p>    
    </div>

    <div class="item-icons">
      <i @click="$emit('id-for-updating', item)" class="far fa-edit"></i>
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
  color: #0000ff;
}

i.fas.fa-trash-alt {
  margin-top: 10px;
  color: #ff0000
}

i.fas.fa-trash-alt, i.far.fa-edit:hover {
  cursor: pointer;
}
i.fas.fa-trash-alt, i.far.fa-edit:active {
  transform: scale(0.88);
}
</style>