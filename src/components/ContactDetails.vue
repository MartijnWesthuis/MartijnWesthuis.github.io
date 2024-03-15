<template>
  <div class="contact-details">
    <div class="contact-details__detail">
      <icon name="mail"  />
      {{ email }}
    </div>
    <div class="contact-details__detail">
      <icon name="phone-call"  />
      {{ phone }}
    </div>
  </div>
</template>

<script>
 import Icon from "./IcomoonVue.vue";
export default {
 
  components: { Icon },
  props: {
    email: { type: String, required: true },
    phone: { type: String, required: true }
  },
  data() {
    return {}
  }
}
</script>
