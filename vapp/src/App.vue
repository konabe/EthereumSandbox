<template>
  <section class="section">
    <div class="container">

      <div class="container">
        <img src="./assets/drizzle-logo.png" />
        <img src="./assets/logo.png" />
      </div>

      <div class="container" v-if="isDrizzleInitialized" id="app">
        
        <AccountInfo />

        <div class="container">
          <h2>Tutorial Token</h2>
          <TutorialToken />
        </div>

        <div class="container">
          <h2>Simple Storage</h2>
          <SimpleStorage />
        </div>

        <div class="container">
          <h2>Complex Storage</h2>
          <ComplexStorage />
        </div>

      </div>
      
    </div>
  </section>
</template>

<script>
import TutorialToken from './TutorialToken'
import SimpleStorage from './SimpleStorage'
import ComplexStorage from './ComplexStorage'

import AccountInfo from './components/AccountInfo';

import { mapGetters } from 'vuex'

export default {
  name: 'app',
  components: {
    ComplexStorage,
    TutorialToken,
    SimpleStorage,
    AccountInfo
  },

  computed: mapGetters('drizzle', ['isDrizzleInitialized'])
}
</script>

<style>
@import "../node_modules/bulma/bulma.sass";
</style>
