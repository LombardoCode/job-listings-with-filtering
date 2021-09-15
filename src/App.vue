<template>
  <div id="app">
		<vue-header></vue-header>
		<div class="container">
			<oferta-laboral
				v-for="(oferta, index) in datosOfertasLaborales" :key="index"
				:id="oferta.id"
				:company="oferta.company"
				:logo="oferta.logo"
				:new_offer="oferta.new"
				:featured="oferta.featured"
				:position="oferta.position"
				:role="oferta.role"
				:level="oferta.level"
				:postedAt="oferta.postedAt"
				:contract="oferta.contract"
				:location="oferta.location"
				:languages="oferta.languages"
				:tools="oferta.tools"
			></oferta-laboral>
		</div>
    <!-- Item Start -->
    Photosnap
    New!
    Featured
    Senior Frontend Developer
    1d ago
    Full Time
    USA only
    <!-- Role -->
    Frontend
    <!-- Level -->
    Senior
    <!-- Languages -->
    HTML
    CSS
    JavaScript
    <!-- Item End -->

    <!-- Item Start -->
    Manage
    New!
    Featured
    Fullstack Developer
    1d ago
    Part Time
    Remote
    <!-- Role -->
    Fullstack
    <!-- Level -->
    Midweight
    <!-- Languages -->
    Python
    <!-- Tools -->
    React
    <!-- Item End -->

    <!-- Item Start -->
    Account
    New!
    Junior Frontend Developer
    2d ago
    Part Time
    USA only
    <!-- Role -->
    Frontend
    <!-- Level -->
    Junior
    <!-- Languages -->
    JavaScript
    <!-- Tools -->
    React
    Sass
    <!-- Item End -->

    <!-- Item Start -->
    MyHome
    Junior Frontend Developer
    5d ago
    Contract
    USA only
    <!-- Role -->
    Frontend
    <!-- Level -->
    Junior
    <!-- Languages -->
    CSS
    JavaScript
    <!-- Item End -->

    <!-- Item Start -->
    Loop Studios
    Software Engineer
    1w ago
    Full Time
    Worldwide
    <!-- Role -->
    Fullstack
    <!-- Level -->
    Midweight
    <!-- Languages -->
    JavaScript
    Ruby
    <!-- Tools -->
    Sass
    <!-- Item End -->

    <!-- Item Start -->
    FaceIt
    Junior Backend Developer
    2w ago
    Full Time
    UK only
    <!-- Role -->
    Backend
    <!-- Level -->
    Junior
    <!-- Languages -->
    Ruby
    <!-- Tools -->
    RoR
    <!-- Item End -->

    <!-- Item Start -->
    Shortly
    Junior Developer
    2w ago
    Full Time
    Worldwide
    <!-- Role -->
    Frontend
    <!-- Level -->
    Junior
    <!-- Languages -->
    HTML
    JavaScript
    <!-- Tools -->
    Sass
    <!-- Item End -->

    <!-- Item Start -->
    Insure
    Junior Frontend Developer
    2w ago
    Full Time
    USA only
    <!-- Role -->
    Frontend
    <!-- Level -->
    Junior
    <!-- Languages -->
    JavaScript
    <!-- Tools -->
    Vue
    Sass
    <!-- Item End -->

    <!-- Item Start -->
    Eyecam Co.
    Full Stack Engineer
    3w ago
    Full Time
    Worldwide
    <!-- Role -->
    Fullstack
    <!-- Level -->
    Midweight
    <!-- Languages -->
    JavaScript
    Python
    <!-- Tools -->
    Django
    <!-- Item End -->

    <!-- Item Start -->
    The Air Filter Company
    Front-end Dev
    1mo ago
    Part Time
    Worldwide
    <!-- Role -->
    Frontend
    <!-- Level -->
    Junior
    <!-- Languages -->
    JavaScript
    <!-- Tools -->
    React
    Sass
    <!-- Item End -->

    <div class="attribution">
      Challenge by <a href="https://www.frontendmentor.io?ref=challenge" target="_blank">Frontend Mentor</a>.
      Coded by <a href="#">Your Name Here</a>.
    </div>
  </div>
</template>

<script>
import datosOfertasLaborales from './assets/data.json'
import OfertaLaboral from './components/OfertaLaboral'
import VueHeader from './components/VueHeader.vue'
export default {
  name: 'App',
  components: {
    OfertaLaboral,
		VueHeader
  },
  data() {
    return {
      datosOfertasLaborales
    }
  }
}
</script>

<style lang="sass">
	html
		box-sizing: border-box
		margin: 0
		padding: 0

	*, *:before, *:after
		box-sizing: inherit
		margin: 0
		padding: 0

	.container
		padding: 22px 20px
</style>
