<template>
  <div class="box map-box">
    <div class="columns">
      <div class="column">
        <label class="label is-inline ml-3">Modify a URL</label>
        <button @click="copyPostback" class="is-inline button is-small is-warning is-rounded ml-3">copy</button>
        <p v-if="copiedPostback" class="is-inline has-text-danger is-size-7 ml-3">Text Copied to Clipboard</p>
        <div>
          <input type="checkbox" class="ml-3" :checked="localAdClickText" @change="updateAdClickText">
          <label class="is-inline ml-1">On AdClick</label>
        </div>
      </div>
      <div>
      </div>
      <div class="is-flex">
        <button @click="firePostback" class="button is-success mr-4 mt-2">Make Postback</button>
        <button class="button is-danger mt-2" @click="$emit('reset')">Reset</button>
      </div>
    </div>
    <input class="input" type="text" placeholder="insert url" :value="postbackURL" @input="$emit('update:postbackURL', $event.target.value)">
    <div class="textarea is-medium mt-2">
      <div v-if="localAdClickText" ref="postbackref" class="pixel-text">
        {{ adClickPostbackResult }}
      </div>
      <div v-else ref="postbackref" class="pixel-text">
        {{ postbackResult }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PostbackSection',
  props: {
    postbackURL: {
      type: String,
      required: true
    },
    adClickText: {
      type: Boolean,
      default: false
    },
    postbackResult: {
      type: String,
      default: ''
    },
    adClickPostbackResult: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      copiedPostback: false,
      localAdClickText: this.adClickText
    }
  },
  watch: {
    adClickText(newValue) {
      this.localAdClickText = newValue;
    }
  },
  methods: {
    updateAdClickText(event) {
      this.localAdClickText = event.target.checked;
      this.$emit('update:adClickText', event.target.checked);
    },
    copyPostback() {
      const text = this.$refs.postbackref.innerText;
      navigator.clipboard.writeText(text)
        .then(() => {
          this.copiedPostback = true;
          setTimeout(() => {
            this.copiedPostback = false;
          }, 2000);
        })
        .catch((error) => {
          alert("Failed to copy text " + error);
        });
    },
    firePostback() {
      this.$emit('fire-postback');
    }
  },
  emits: ['update:postbackURL', 'update:adClickText', 'reset', 'fire-postback']
}
</script>

<style scoped>
.pixel-text {
  font-size: small;
  white-space: pre;
  font-family: monospace;
}
</style> 