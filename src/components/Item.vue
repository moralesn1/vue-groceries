<template>
  <div>
    <h3>{{item.item}}</h3>
    <p>{{item.amount}}</p>
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