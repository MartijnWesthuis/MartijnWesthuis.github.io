<template>
    <div class="personal-profile d-flex p-page gap-1">
      <div>
        <h3>{{ title }}</h3>
      </div>
      <div class="personal-profile__intro">
        {{ intro }}
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: { type: String, required: true },
      intro: { type: String, required: true }
    },
    data() {
      return {}
    }
  }
  </script>
  