<template>
  <div class="box">
    <!-- Lander Event -->
    <div class="mt-5">
      <input v-model="placementLandr" type="checkbox" @change="$emit('update:placementLandr', $event.target.checked)">
      <label class="is-inline ml-3 label">Lander</label>
      <div class="column">
        <div v-if="traffic == 'Facebook' || traffic == 'Tiktok'">
          <div class="control">
            <div class="select">
              <select v-model="landrEvent" @change="$emit('update:landrEvent', $event.target.value)">
                <option v-if="traffic == 'Facebook'" value="'AddPaymentInfo'">Add Payment Info</option>
                <option v-if="traffic == 'Facebook'" value="AddToCart">Add To Cart</option>
                <option v-if="traffic == 'Facebook'" value="CompleteRegistration">Complete Registration</option>
                <option v-if="traffic == 'Facebook'" value="InitiateCheckout">Initiate Checkout</option>
                <option v-if="traffic == 'Facebook'" value="Lead">Lead</option>
                <option v-if="traffic == 'Facebook'" value="PageView">Page View</option>
                <option v-if="traffic == 'Facebook'" value="Purchase">Purchase</option>
                <option v-if="traffic == 'Facebook'" value="Search">Search</option>
                <option v-if="traffic == 'Facebook'" value="ViewContent">View Content</option>
                <option v-if="traffic == 'Tiktok'" value="AddToCart">Add To Cart</option>
                <option v-if="traffic == 'Tiktok'" value="AddPaymentInfo">Add Payment Info</option>
                <option v-if="traffic == 'Tiktok'" value="AddToWishlist">Add To Wishlist</option>
                <option v-if="traffic == 'Tiktok'" value="ClickButton">Click Button</option>
                <option v-if="traffic == 'Tiktok'" value="CompletePayment">Complete Payment</option>
                <option v-if="traffic == 'Tiktok'" value="CompleteRegistration">Complete Registration</option> 
                <option v-if="traffic == 'Tiktok'" value="InitiateCheckout">Initiate Checkout</option>
                <option v-if="traffic == 'Tiktok'" value="ViewContent">View Content</option>
                <option v-if="traffic == 'Tiktok'" value="Search">Search</option>
              </select>
            </div>
          </div>
        </div>
        <div v-if="traffic == 'Taboola'">
          <input class="input" type="text" placeholder="input Taboola event..." v-model="taboolaLandrEvent" @input="$emit('update:taboolaLandrEvent', $event.target.value)">
        </div>
        <div v-if="traffic == 'Outbrain'">
          <input class="input" type="text" placeholder="input Outbrain event..." v-model="outbrainLandrEvent" @input="$emit('update:outbrainLandrEvent', $event.target.value)">
        </div>
      </div>
    </div>

    <hr>

    <!-- Serp Event -->
    <div class="mt-5">
      <input v-model="placementSerp" type="checkbox" @change="$emit('update:placementSerp', $event.target.checked)">
      <label class="is-inline ml-3 label">Serp</label>
      <div class="column">
        <div v-if="traffic == 'Facebook' || traffic == 'Tiktok'">
          <div class="control">
            <div class="select">
              <select v-model="serpEvent" @change="$emit('update:serpEvent', $event.target.value)">
                <option v-if="traffic == 'Facebook'" value="'AddPaymentInfo'">Add Payment Info</option>
                <option v-if="traffic == 'Facebook'" value="AddToCart">Add To Cart</option>
                <option v-if="traffic == 'Facebook'" value="CompleteRegistration">Complete Registration</option>
                <option v-if="traffic == 'Facebook'" value="InitiateCheckout">Initiate Checkout</option>
                <option v-if="traffic == 'Facebook'" value="Lead">Lead</option>
                <option v-if="traffic == 'Facebook'" value="PageView">Page View</option>
                <option v-if="traffic == 'Facebook'" value="Purchase">Purchase</option>
                <option v-if="traffic == 'Facebook'" value="Search">Search</option>
                <option v-if="traffic == 'Facebook'" value="ViewContent">View Content</option>
                <option v-if="traffic == 'Tiktok'" value="AddToCart">Add To Cart</option>
                <option v-if="traffic == 'Tiktok'" value="AddPaymentInfo">Add Payment Info</option>
                <option v-if="traffic == 'Tiktok'" value="AddToWishlist">Add To Wishlist</option>
                <option v-if="traffic == 'Tiktok'" value="ClickButton">Click Button</option>
                <option v-if="traffic == 'Tiktok'" value="CompletePayment">Complete Payment</option>
                <option v-if="traffic == 'Tiktok'" value="CompleteRegistration">Complete Registration</option> 
                <option v-if="traffic == 'Tiktok'" value="InitiateCheckout">Initiate Checkout</option>
                <option v-if="traffic == 'Tiktok'" value="ViewContent">View Content</option>
                <option v-if="traffic == 'Tiktok'" value="Search">Search</option>
              </select>
            </div>
          </div>
        </div>
        <div v-if="traffic == 'Taboola'">
          <input class="input" type="text" placeholder="input Taboola event..." v-model="taboolaSerpEvent" @input="$emit('update:taboolaSerpEvent', $event.target.value)">
        </div>
        <div v-if="traffic == 'Outbrain'">
          <input class="input" type="text" placeholder="input Outbrain event..." v-model="outbrainSerpEvent" @input="$emit('update:outbrainSerpEvent', $event.target.value)">
        </div>
      </div>
    </div>

    <hr>

    <!-- Ad Click Event -->
    <div class="mt-5">
      <input v-model="placementAdclick" type="checkbox" @change="$emit('update:placementAdclick', $event.target.checked)">
      <label class="is-inline ml-3 label">Ad Click</label>
      <div class="column">
        <div v-if="traffic == 'Facebook' || traffic == 'Tiktok'">
          <div class="control">
            <div class="select">
              <select v-model="adclickEvent" @change="$emit('update:adclickEvent', $event.target.value)">
                <option v-if="traffic == 'Facebook'" value="'AddPaymentInfo'">Add Payment Info</option>
                <option v-if="traffic == 'Facebook'" value="AddToCart">Add To Cart</option>
                <option v-if="traffic == 'Facebook'" value="CompleteRegistration">Complete Registration</option>
                <option v-if="traffic == 'Facebook'" value="InitiateCheckout">Initiate Checkout</option>
                <option v-if="traffic == 'Facebook'" value="Lead">Lead</option>
                <option v-if="traffic == 'Facebook'" value="PageView">Page View</option>
                <option v-if="traffic == 'Facebook'" value="Purchase">Purchase</option>
                <option v-if="traffic == 'Facebook'" value="Search">Search</option>
                <option v-if="traffic == 'Facebook'" value="ViewContent">View Content</option>
                <option v-if="traffic == 'Tiktok'" value="AddToCart">Add To Cart</option>
                <option v-if="traffic == 'Tiktok'" value="AddPaymentInfo">Add Payment Info</option>
                <option v-if="traffic == 'Tiktok'" value="AddToWishlist">Add To Wishlist</option>
                <option v-if="traffic == 'Tiktok'" value="ClickButton">Click Button</option>
                <option v-if="traffic == 'Tiktok'" value="CompletePayment">Complete Payment</option>
                <option v-if="traffic == 'Tiktok'" value="CompleteRegistration">Complete Registration</option> 
                <option v-if="traffic == 'Tiktok'" value="InitiateCheckout">Initiate Checkout</option>
                <option v-if="traffic == 'Tiktok'" value="ViewContent">View Content</option>
                <option v-if="traffic == 'Tiktok'" value="Search">Search</option>
              </select>
            </div>
          </div>
        </div>
        <div v-if="traffic == 'Taboola'">
          <input class="input" type="text" placeholder="input Taboola event..." v-model="taboolaAdclickEvent" @input="$emit('update:taboolaAdclickEvent', $event.target.value)">
        </div>
        <div v-if="traffic == 'Outbrain'">
          <input class="input" type="text" placeholder="input Outbrain event..." v-model="outbrainAdClickEvent" @input="$emit('update:outbrainAdClickEvent', $event.target.value)">
        </div>
      </div>
    </div>

    <!-- Estimated CPC Section -->
    <div v-if="traffic == 'Facebook'" class="is-flex is-justify-content-space-between">
      <div>
        <label class="is-inline ml-3 label">Add Estimated CPC?</label>
        <input type="checkbox" class="ml-3" v-model="enableEstimatedCPC" @change="$emit('update:enableEstimatedCPC', $event.target.checked)">
      </div>
    </div>

    <div v-if="enableEstimatedCPC" class="is-flex is-align-items-center" style="gap: 1rem;">
      <input type="number" 
             class="input" 
             v-model="cpcNumber" 
             @input="$emit('update:cpcNumber', $event.target.value)"
             placeholder="Enter CPC number" 
             style="width: 150px; min-width: 120px; max-width: 200px;">
      
      <div class="select" style="min-width: 300px; max-width: 500px;">
        <select v-model="estimatedCPCValue" @change="$emit('update:estimatedCPCValue', $event.target.value)">
          <option value="">Select CPC</option>
          <option :value="`{$estimatedGoogleCPC_${cpcNumber}}`">estimatedGoogleCPC -- Last 3 Days Rolling Average</option>
          <option :value="`{$estimatedGoogleCPCToday_${cpcNumber}}`">estimatedGoogleCPCToday -- Today's Average</option>
          <option :value="`{$estimatedGoogleCPCYesterday_${cpcNumber}}`">estimatedGoogleCPCYesterday -- Yesterday's Average</option>
          <option :value="`{$estimatedGoogleCPCNow_${cpcNumber}}`">estimatedGoogleCPCNow - Last Hour Average</option>
        </select>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PixelEvents',
  props: {
    traffic: {
      type: String,
      required: true
    },
    placementLandr: {
      type: Boolean,
      default: false
    },
    placementSerp: {
      type: Boolean,
      default: false
    },
    placementAdclick: {
      type: Boolean,
      default: false
    },
    landrEvent: {
      type: String,
      default: ''
    },
    serpEvent: {
      type: String,
      default: ''
    },
    adclickEvent: {
      type: String,
      default: ''
    },
    taboolaLandrEvent: {
      type: String,
      default: ''
    },
    taboolaSerpEvent: {
      type: String,
      default: ''
    },
    taboolaAdclickEvent: {
      type: String,
      default: ''
    },
    outbrainLandrEvent: {
      type: String,
      default: ''
    },
    outbrainSerpEvent: {
      type: String,
      default: ''
    },
    outbrainAdClickEvent: {
      type: String,
      default: ''
    },
    enableEstimatedCPC: {
      type: Boolean,
      default: false
    },
    cpcNumber: {
      type: [Number, String],
      default: 0
    },
    estimatedCPCValue: {
      type: String,
      default: ''
    }
  },
  emits: [
    'update:placementLandr',
    'update:placementSerp',
    'update:placementAdclick',
    'update:landrEvent',
    'update:serpEvent',
    'update:adclickEvent',
    'update:taboolaLandrEvent',
    'update:taboolaSerpEvent',
    'update:taboolaAdclickEvent',
    'update:outbrainLandrEvent',
    'update:outbrainSerpEvent',
    'update:outbrainAdClickEvent',
    'update:enableEstimatedCPC',
    'update:cpcNumber',
    'update:estimatedCPCValue'
  ]
}
</script> 