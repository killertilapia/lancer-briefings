<template>
  <header class="clipped-x-large-forward">
    <div class="title clipped-x-large-forward">
      <img class="logo" src="/icons/company-icon.svg" />
      <div class="title-container">
        <div class="title-row" id="title-first-line">
          <span id="title-header">{{ header.headerTitle }}</span>
          <span id="title-subheader">{{ header.headerSubtitle }}</span>
        </div>
        <div class="title-row">
          <span id="subtitle-header">{{ header.subheaderTitle }}</span>
          <span id="subtitle-subheader">// {{ header.subheaderSubtitle }}</span>
        </div>
      </div>
    </div>
    
    
    <div class="rhombus">&nbsp;</div>
    <video autoplay muted loop width="90px" height="90px">
      <source src="/ice_planet.webm" type="video/webm" />
    </video>
    
    <div class="location-info" @click="planetModal">
      <div class="location-row" id="planet-year">
        <div id="planet">
          <h4>Deployment Info</h4>
          <span class="subtitle">{{ header.planet }}</span>
        </div>
        <div id="year">
          <h4>Year</h4>
          <span class="subtitle">{{ header.year }}</span>
        </div>
      </div>
      <div class="location-row" id="system-gate-ring">
        <div id="system">
          <h4>System</h4>
          <span class="subtitle">{{ header.system }}</span>
        </div>
        <div id="gate">
          <h4>Gate</h4>
          <span class="subtitle">{{ header.gate }}</span>
        </div>
        <div id="ring">
          <h4>Ring</h4>
          <span class="subtitle">{{ header.ring }}</span>
        </div>
      </div>
      <div class="middle">
			  <div class="text">&nbsp;</div>
		  </div>
    </div>
  </header>
</template>

<script>

import PlanetModal from '../PlanetModal.vue';

export default {
  components: {
    PlanetModal
  },
  props: {
    header: {
      type: Object,
      required: true,
    }
  },
  methods: {
    planetModal(){      
      this.$oruga.modal.open({
        parent: this,
        component: PlanetModal,
        custom: true,
        trapFocus: true,     
        class: "planet-test" ,
        width: 1920,
      })
    }
  }
}
</script>

<style lang="scss" scoped>
  .location-info:hover{
    cursor: pointer;
    background-color: rgba(255, 255, 255, 0.3);
  }
</style>