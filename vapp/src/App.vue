<template>
  <section class="section">
    <div class="container">

      <div class="container">
        <img src="./assets/drizzle-logo.png" />
        <img src="./assets/logo.png" />
      </div>

      <div class="container" v-if="isDrizzleInitialized" id="app">
        <AccountInfo />
        <TutorialToken />
        <SimpleStorage />
        <ComplexStorage />
      </div>

    </div>
  </section>
</template>

<script>
import TutorialToken from './components/TutorialToken'
import SimpleStorage from './components/SimpleStorage'
import ComplexStorage from './components/ComplexStorage'

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
