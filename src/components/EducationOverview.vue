<template>
  <div class="education p-page">
    <div class="education__title">
      <h2>{{ title }}</h2>
    </div>

    <div class="education__list">
      <div v-for="item in education" :key="item" class="education__list__item">
        <h3>{{ item }}</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: { type: String, required: true }
  },
  data() {
    return {
      education: ['Havo', 'MBO 4 Fotografie', 'MBO 4 (Addendum jaar) Mediavormgeven interactief']
    }
  }
}
</script>
