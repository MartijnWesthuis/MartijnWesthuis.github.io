<template>
  <div class="call-to-action">
    <h3>{{ cta }}</h3>

    <big-button label="Neem contact op" onclick="location.href='mailto:mpwesthuis@gmail.com'"/>
  </div>
</template>

<script>
import BigButton from './BigButton.vue'

export default {
  components: {
    BigButton
  },
  props: {
    cta: { type: String, required: true }
  },
  data() {
    return {}
  }
}
</script>
