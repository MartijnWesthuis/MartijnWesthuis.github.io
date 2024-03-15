<template>
  <div class="introduction-container">
    <div class="introduction p-page d-flex">
      <div class="introduction__hello">
        <p>{{ introduction }}</p>
      </div>

      <div class="introduction__name-and-photo d-flex">
        <div class="introduction__name-and-photo__name">
          <h1>{{ name }}</h1>
        </div>
        <div class="introduction__name-and-photo__photo">
          <img src="../assets/Profiel-foto.png" />
        </div>
      </div>

      <div class="introduction__job-titles d-flex">
        <div
          class="introduction__job-titles__job-title introduction__job-titles__job-title--1 d-flex"
        >
          <h4>{{ jobTitle1 }}</h4>
        </div>
        <div
          class="introduction__job-titles__job-title introduction__job-titles__job-title--2 d-flex"
        >
          <h4>{{ jobTitle2 }}</h4>
        </div>
      </div>
    </div>

    <personal-profile
      title="Persoonlijk profiel"
      intro="Als optimistische, analytische developer combineer ik creativiteit met technische vaardigheden, wat resulteert in gave eindproducten. Ik werk goed in teamverband en zelfstandig, en sta open voor verandering en persoonlijke groei. In mijn vrije tijd geniet ik van natuurwandelingen, sporten, airsoft en gamen."
    />

    <call-to-action cta="Samenwerken?" />

  </div>
</template>

<script>
import PersonalProfile from './PersonalProfile.vue'
import CallToAction from './CallToAction.vue'

export default {
  components: {
    PersonalProfile,
    CallToAction,
  },
  props: {
    introduction: { type: String, required: true },
    name: { type: String, required: true },
    jobTitle1: { type: String, required: true },
    jobTitle2: { type: String, required: true }
  },
  data() {
    return {}
  },

}
</script>
