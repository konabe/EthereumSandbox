<template>

  <div class="container py-6" v-if="isDrizzleInitialized">
    <h1 class="title">Show the Contract</h1>
    <div class="columns is-mobile">

      <div class="column">
        <div class="message">
          <div class="message-header">
            drizzle-contract(-form) component
          </div>
          <div class="message-body">

            <div class="container py-2">
              <drizzle-contract
                contractName="TutorialToken"
                method="totalSupply"
                label="Total"
              />
              <span class="is-size-7">
                contractName="TutorialToken" , method="totalSupply" , label="Total"
              </span>
            </div>

            <div class="container py-2">
              <drizzle-contract
                contractName="TutorialToken"
                method="symbol"
                label="Symbol"
              />
              <span class="is-size-7">
                contractName="TutorialToken" , method="symbol" , label="symbol"
              </span>
            </div>

            <div class="container py-2">
              <drizzle-contract
                contractName="TutorialToken"
                method="balanceOf"
                label="Your Balance"
                :methodArgs="accounts"
              />
              <span class="is-size-7">
                contractName="TutorialToken" , method="balanceOf" , label="Your Balance", :methodArgs="{{accounts}}"
              </span>
            </div>

            <div class="container py-2">
              <drizzle-contract-form
                contractName="TutorialToken"
                method="transfer"
                :placeholders="placeholders"
              />
              <span class="is-size-7">
                contractName="TutorialToken" , method="transfer" :placeholders="{{placeholders}}"
              </span>
            </div>

          </div>
        </div>
      </div>

      <div class="column">
        <div class="message">
          <div class="message-header">
            get from getContractData
          </div>
          <div class="message-body">

            <div>
              <strong>Total</strong> is {{getTotal}}
            </div>

            <div>
              <strong>Symbol</strong> is {{getSymbol}}
            </div>

            <div>
              <strong>Your Balance</strong> is {{getYourBalance}}
            </div>

            <div class="container py-4">
              <b-field label="To address">
                <b-input v-model="address"/>
              </b-field>

              <b-field label="Amount to Send">
                <b-input v-model="amount"/>
              </b-field>

              <b-button type="is-primary" @click="onSubmit()">
                Submit
              </b-button>

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
  name: 'TutorialToken',
  data: function() {
    return {
      address: "",
      amount: ""
    }
  },
  computed: {
    ...mapGetters('accounts', ['activeAccount', 'activeBalance']),
    ...mapGetters('drizzle', ['drizzleInstance', 'isDrizzleInitialized']),
    ...mapGetters('contracts', ['getContractData', 'contractInstances']),

    accounts() {
      return [this.activeAccount]
    },

    placeholders() {
      return ['To Address', 'Amount to Send']
    },

    getTotal() {
      return this.getContractData({
        contract: "TutorialToken",
        method: "totalSupply"
      })
    },

    getSymbol() {
      return this.getContractData({
        contract: "TutorialToken",
        method: "symbol"
      })
    },

    getYourBalance() {
      return this.getContractData({
        contract: "TutorialToken",
        method: "balanceOf"
      })
    }
  },
  methods: {
    onSubmit() {
      this.drizzleInstance
        .contracts["TutorialToken"]
        .methods["transfer"]
        .cacheSend(this.address, this.amount)
    }
  },
  created() {
  }
}
</script>

<style>
@import "../../node_modules/bulma/bulma.sass";
</style>
