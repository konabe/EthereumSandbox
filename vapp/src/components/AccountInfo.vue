<template>
  <div class="container py-6" v-if="isDrizzleInitialized">
    <h1 class="title">Show the Accounts</h1>
    <div class="columns is-mobile">

      <div class="column">
        <div class="message">
          <div class="message-header">
            drizzle-account component
          </div>
          
          <div class="message-body">
            <div class="container py-2">
              <drizzle-account units="Ether" :precision="2" />
              <span class="is-size-7">
                units="TutorialToken" , method="balanceOf" , label="Your Balance", :methodArgs="{{accounts}}"
              </span>
            </div>
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
              <strong>activeBalance</strong> is {{drizzleInstance.web3.utils.fromWei(activeBalance)}}
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
    ...mapGetters('drizzle', ['drizzleInstance', 'isDrizzleInitialized']),
    ...mapGetters('accounts', ['activeAccount', 'activeBalance']),
  }
}
</script>

<style>
@import "../../node_modules/bulma/bulma.sass";
</style>
