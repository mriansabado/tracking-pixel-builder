<template>
  <div class="box">
    <div>
      <label class="label">Traffic</label>
      <div class="control">
        <div class="select">
          <select :value="localTraffic" @change="updateTraffic">
            <option value="Facebook">Facebook</option>
            <option value="Tiktok">Tiktok</option>
            <option value="Taboola">Taboola</option>
            <option value="Outbrain">Outbrain</option>
          </select>
        </div>
      </div>
      <span class="ml-2 has-text-danger" v-if="warningTraffic">! Select a Traffic Source</span>
    </div>
    <div class="column mt-5">
      <label class="pt-4 has-text-weight-bold">Pixel ID</label>
      <input class="input" :value="localPixelID" @input="updatePixelID" type="text">
      <span class="ml-2 has-text-danger" v-if="warningPixelID">! Enter a Pixel ID</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TrafficAndPixelID',
  props: {
    traffic: {
      type: String,
      required: true
    },
    pixelID: {
      type: String,
      required: true
    },
    warningTraffic: {
      type: Boolean,
      default: false
    },
    warningPixelID: {
      type: Boolean,
      default: false
    }
  },
  data() {
    return {
      localTraffic: this.traffic,
      localPixelID: this.pixelID
    }
  },
  watch: {
    traffic(newValue) {
      this.localTraffic = newValue;
    },
    pixelID(newValue) {
      this.localPixelID = newValue;
    }
  },
  methods: {
    updateTraffic(event) {
      this.localTraffic = event.target.value;
      this.$emit('update:traffic', event.target.value);
    },
    updatePixelID(event) {
      this.localPixelID = event.target.value;
      this.$emit('update:pixelID', event.target.value);
    }
  },
  emits: ['update:traffic', 'update:pixelID']
}
</script> 