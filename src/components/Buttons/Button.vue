<template>
  <button @click="onClick" :style="{background: color}" class="btn">{{ btnText }} </button>  
</template>

<script>
export default {
  name: 'Button',
  props: {
    btnText: {
      type: String,
      color: String
    },
    color: {
      type: String
    }
  },
  methods: {
    onClick(e) {
      e.preventDefault()
      console.log('clicked')
    }
  }
}
</script>

