<template>
  <button @click="onClick" class="btn">{{ btnText }} </button>  
</template>

<script>
export default {
  name: 'Button',
  props: {
    btnText: {
      type: String,
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

