<template>
  <div class="container">
    <h1 class="title">Show the Accounts</h1>
    <div class="columns is-mobile">

      <div class="column">
        <div class="message">
          <div class="message-header">
            drizzle-account component
          </div>
          <div class="message-body">
            <drizzle-account units="Ether" :precision="2" />
          </div>
        </div>
      </div>

      <div class="column">
        <div class="message">
          <div class="message-header">
            get from accounts store
          </div>
          <div class="message-body">
            <div>
              <strong>activeAcount</strong> is {{activeAccount}}
            </div>
            <div>
              <strong>activeBalance</strong> is {{activeBalance}}
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>
</template>


<script>
import { mapGetters } from 'vuex'

export default {
  name: 'AccountInfo',
 
  computed: {
    ...mapGetters('drizzle', ['drizzleInstance']),
    ...mapGetters('accounts', ['activeAccount', 'activeBalance'])
  }
}
</script>

<style>
@import "../../node_modules/bulma/bulma.sass";
</style>
