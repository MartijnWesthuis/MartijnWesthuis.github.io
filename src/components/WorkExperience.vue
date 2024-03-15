<template>
  <div class="work-experience" ref="workExperience">
    <h2>{{ title }}</h2>

    <div class="work-experience__peroid-container">
      <div
        class="work-experience__peroid-container__active"
        :style="'transform: translateX(' + translationX + 'rem)'"
      ></div>
      <div
        :class="[
          { 'work-experience__peroid-container__year--active': currentIndex === index },
          'work-experience__peroid-container__year'
        ]"
        v-for="(item, index) in descriptions"
        :key="index"
        @click="goToPeriod(index)"
      >
        {{ item.year }}
      </div>
    </div>

    <experience-description
      v-for="(item, index) in filteredDescriptions"
      :key="index"
      :jobTitle="item.jobTitle"
      :location="item.location"
      :tools="item.tools"
      :descriptions="item.descriptions"
      :selectedPeriod="currentIndex"
    />
  </div>
</template>

<script>
import ExperienceDescription from './ExperienceDescription.vue'

export default {
  components: {
    ExperienceDescription
  },
  props: {
    title: { type: String, required: true }
  },
  data() {
    return {
      breakpointSM: 0,
      breakpointSMValue: 0,
      windowWidth: 0,
      currentIndex: 0,
      translationX: 0.1,
      translationValue: 9,
      translationValueMD: 13,
      descriptions: [
        {
          year: '2017-heden',
          jobTitle: 'Front-end Developer',
          location: 'Cablon Medical B.V.',
          tools: [
            'html',
            'CSS',
            'JS',
            'VueJS',
            'SPA',
            'VS Professional',
            'GitHub',
            'jira',
            'Adobe Xd',
            'illustrator',
            'Premiere pro',
            'Photoshop',
            'inDesign'
          ],
          descriptions: [
            'Bouwen van een patiëntoproepsysteem voor in de wachtkamer van ziekenhuizen. Ik ben hierbij verantwoordelijk voor UI Design en de gehele voorkant van deze app.',
            ' Bouwen van een offerte wizard met veel business logic zoals de offerte automatisch aanvullen met bijbehorende contracten en filteren van producten aan de hand van keuzes die gebruikers maken. Bij deze web app ben ik volledig verantwoordelijk voor UI Design, HTML/CSS en groot deel van de logica in VueJS. ',
            'Ik heb meegebouwd aan een inventarisprogramma voor stralingsbeschermde kleding voor in ziekenhuizen. Naast het uitvoeren van onderhoud, bouw ik mooie nieuwe features voor deze web app, zoals de voorkant van een Excel importtool, een product configurator en keuringsysteem. Ik ben volledig verantwoordelijk voor UI Design, HTML/CSS en een deel van de logica in VueJS.',
            'Daarnaast heb ik voor verschillende desktop apps UI Designs gemaakt en een UI-Kit gerealiseerd waar Developers zelfstandig mee aan de slag kunnen. En ondersteun ik Marketing met grafisch ontwerp en 2D animaties'
          ]
        },
        {
          year: '2013 - 2017',
          jobTitle: 'Allround Vormgever',
          location: 'Wegwijs B.V.',
          tools: ['illustrator', 'Premiere pro', 'Photoshop', 'inDesign'],
          descriptions: [
            'Grafisch vormgeven van (interactieve) magazines. Websites ontwerpen. Ontwerpen presenteren aan management en/of klanten'
          ]
        },
        {
          year: '2012-2018',
          jobTitle: 'Freelance Fotograaf',
          location: 'Nederland',
          tools: ['Lightroom', 'Photoshop', 'inDesign'],
          descriptions: ['Allround fotografie zoals: productfotografie, architectuur en bruiloften']
        }
      ]
    }
  },
  mounted() {
    this.breakpointSM = getComputedStyle(document.documentElement)
      .getPropertyValue('--breakpoint-sm')
      .trim()

    this.breakpointSMValue = parseInt(this.breakpointSM, 10)
    console.log(this.breakpointSM)

    this.windowWidth = window.innerWidth // Set initial value
    this.debouncedHandleResize = this.debounce(this.handleResize, 100)
    window.addEventListener('resize', this.debouncedHandleResize)
  },
  beforeUnmount() {
    window.removeEventListener('resize', this.debouncedHandleResize)
  },
  methods: {
    handleResize() {
      this.windowWidth = window.innerWidth
    },
    goToPeriod: function (index) {
      this.currentIndex = index

      if (index === 0) {
        this.translationX = 0.1
      }

      if (index !== 0 && this.windowWidth >= this.breakpointSMValue) {
        this.translationX = this.currentIndex * this.translationValueMD
      }
      if (index !== 0 && this.windowWidth <= this.breakpointSMValue) {
        this.translationX = this.currentIndex * this.translationValue
      }

      if (index === this.descriptions.length - 1 && this.windowWidth >= this.breakpointSMValue) {
        this.translationX = this.currentIndex * this.translationValueMD - 0.1
      }

      if (index === this.descriptions.length - 1 && this.windowWidth <= this.breakpointSMValue) {
        this.translationX = this.currentIndex * this.translationValue - 0.1
      }
    },
    debounce(func, wait) {
      let timeout

      return function executedFunction(...args) {
        const later = () => {
          clearTimeout(timeout)
          func(...args)
        }

        clearTimeout(timeout)
        timeout = setTimeout(later, wait)
      }
    }
  },
  computed: {
    filteredDescriptions() {
      return [this.descriptions[this.currentIndex]]
    }
  },
  watch: {
    windowWidth(){
        this.currentIndex = 0;
        this.translationX = 0.1;
    }
  }
}
</script>
