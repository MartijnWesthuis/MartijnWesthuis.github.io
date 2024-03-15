<template>
  <div class="container">
  <header>
    <contact-details email="mpwesthuis@gmail.com" phone="+316 36 11 24 06" />
  </header>
  <main>
    <introduction-header
      introduction="Hallo! Mijn naam is"
      name="Martijn Westhuis"
      jobTitle1="UX Designer"
      jobTitle2="Front-end Developer"

    />
  
    <work-experience  title="Werkervaring"/>

    <education-overview  title="Opleidingen"/>

  </main>
</div>
</template>

<script>
import ContactDetails from './components/ContactDetails.vue'
import IntroductionHeader from './components/IntroductionHeader.vue'
import WorkExperience from './components/WorkExperience.vue'
import EducationOverview from './components/EducationOverview.vue'

export default {
  components: {
    ContactDetails,
    IntroductionHeader,
    WorkExperience,
    EducationOverview

  },
  data() {
    return {}
  },
  methods: {

   }
}
</script>

<style lang="scss">
@import 'styles/main.scss';
</style>
