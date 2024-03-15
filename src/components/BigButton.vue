<template>
<button class="big-button">
    {{ label }}
</button>
  </template>
  
  <script>
  export default {
    props: {
      label: { type: String, required: true, default: 'label' },
      //url: { type: String, required: true }
    },
    data() {
      return {}
    }
  }
  </script>
  