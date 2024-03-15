<template>
  <div class="experience-description">
    <div class="experience-description__details">
      <div class="experience-description__details__title p-page">
        <h3>{{ jobTitle }}</h3>
        <p>{{ location }}</p>
      </div>

      <div class="experience-description__details__tools p-page">
        <div
          v-for="(tool, index) in tools"
          :key="index"
          class="experience-description__details__tools__tool"
        >
          {{ tool }}
        </div>
      </div>
    </div>

    <!-- mobile description-->
    <div class="experience-description__description experience-description__description--mobile p-page">
      <transition :name="transitionName" mode="out-in">
        <div
          :key="currentIndex"
          :class="['experience-description__description__inner', {'experience-description__description__inner--active': true}]"
        >
          <p>{{ descriptions[currentIndex] }}</p>
        </div>
      </transition>

      <div class="experience-description__controls">
      <div  :class="[{'hide-prev ': currentIndex === 0},'experience-description__controls__prev']">
        <icon name="chevron-left" @click="prevCard" />
      </div>
      <div :class="[{'hide-next': currentIndex === descriptions.length - 1},'experience-description__controls__next']">
        <icon name="chevron-right" @click="nextCard" />
      </div>
    </div>

    </div>

    <!-- desktop description-->
    <!-- <div class="experience-description__description p-page">
        <div class="experience-description__description__inner">
          <p v-for="item in descriptions" :key="item">{{ item}}</p>
        </div>
    </div> -->
    


  </div>
</template>

<script>
import Icon from './IcomoonVue.vue'
export default {
  components: { Icon },
  props: {
    jobTitle: { type: String, required: true },
    location: { type: String, required: true },
    tools: { type: Array, required: true },
    descriptions: { type: Array, required: true },
    selectedPeriod: {type: Number,required: true}
  },
  data() {
    return {
      slideDirection: 'next',
      currentIndex: 0
    }
  },

  methods: {
    nextCard() {
    if (this.currentIndex < this.descriptions.length - 1) {
      this.slideDirection = 'next';
      this.currentIndex++;
    }
  },
  prevCard() {
    if (this.currentIndex > 0) {
      this.slideDirection = 'prev';
      this.currentIndex--;
    }
  }
  },
  computed: {
    transitionName() {
      return this.slideDirection === 'next' ? 'slide-next' : 'slide-prev';
    }
  },
  watch: {
    selectedPeriod(){
      this.currentIndex = 0;
    }
  }
}
</script>
