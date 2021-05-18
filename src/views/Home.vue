<template>
  <div class="home">
    <Groceries />
  </div>
</template>

<script>
// @ is an alias to /src
import Groceries from '@/components/Groceries.vue'


export default {
  name: 'Home',
  components: {
    Groceries,
  }
}
</script>
