<template>
  <div class="field">
    <div class="control">
      <div class="textarea is-large landrTextArea">
        <div>
          <label class="label is-inline">Lander</label>
          <button @click="copyTextLandr" class="is-inline button is-small is-warning is-rounded ml-3 mt-1">copy</button>
          <p v-if="copiedLandr" class="is-inline has-text-danger is-size-7 ml-3 copied-text">Text Copied to Clipboard</p>
        </div>
        <hr>
        <div ref="landrRef" v-if="traffic == 'Facebook' && placementLandr" class="pixel-text"> 
          {{ fbLandrResult }}
        </div>
        <div ref="landrRef" v-if="traffic == 'Tiktok' && placementLandr" class="pixel-text">
          {{ ttLandrResult }}
        </div>
        <div ref="landrRef" v-if="traffic == 'Taboola' && placementLandr" class="pixel-text">
          {{ taboolaLandrResult }}
        </div>
        <div ref="landrRef" v-if="traffic == 'Outbrain' && placementLandr" class="pixel-text">
          {{ outbrainLandrResult }}
        </div>
        <span v-else></span>
      </div>
    </div>
    <div class="control mt-4">
      <div class="textarea is-large serpTextArea">
        <div>
          <label class="label is-inline">Serp</label>
          <button @click="copyTextSerp" class="is-inline button is-small is-warning is-rounded ml-3 mt-1">copy</button>
          <p v-if="copiedSerp" class="is-inline has-text-danger is-size-7 ml-3 copied-text">Text Copied to Clipboard</p>
        </div>
        <hr>
        <div ref="serpRef">
          <div v-if="traffic == 'Facebook' && placementSerp" class="pixel-text">
            {{ fbSerpResult }}
          </div>
          <div v-if="traffic == 'Tiktok' && placementSerp" class="pixel-text">
            {{ ttSerpResult }}
          </div>
          <div v-if="traffic == 'Taboola' && placementSerp" class="pixel-text">
            {{ taboolaSerpResult }}
          </div>
          <div v-if="traffic == 'Outbrain' && placementSerp" class="pixel-text">
            {{ outbrainSerpResult }}
          </div>
          
          <div v-if="traffic == 'Facebook' && placementAdclick && placementSerp" class="pixel-text">
            {{ fbAdclickResult }}
          </div>
          <div v-if="traffic == 'Facebook' && placementAdclick && !placementSerp" class="pixel-text">
            {{ fbAdclickOnlyResult }}
          </div>
          <div v-if="traffic == 'Tiktok' && placementAdclick && placementSerp" class="pixel-text">
            {{ ttAdclickResult }}
          </div>
          <div v-if="traffic == 'Tiktok' && placementAdclick && !placementSerp" class="pixel-text">
            {{ ttAdclickOnlyResult }}
          </div>
          <div v-if="traffic == 'Taboola' && placementAdclick && placementSerp" class="pixel-text">
            {{ taboolaAdclickResult }}
          </div>
          <div v-if="traffic == 'Taboola' && placementAdclick && !placementSerp" class="pixel-text">
            {{ taboolaAdclickOnlyResult }}
          </div>
          <div v-if="traffic == 'Outbrain' && placementAdclick && placementSerp" class="pixel-text">
            {{ outbrainAdclickResult }}
          </div>
          <div v-if="traffic == 'Outbrain' && placementAdclick && !placementSerp" class="pixel-text">
            {{ outbrainAdclickOnlyResult }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ResultsArea',
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
    fbLandrResult: {
      type: String,
      default: ''
    },
    fbSerpResult: {
      type: String,
      default: ''
    },
    fbAdclickResult: {
      type: String,
      default: ''
    },
    fbAdclickOnlyResult: {
      type: String,
      default: ''
    },
    ttLandrResult: {
      type: String,
      default: ''
    },
    ttSerpResult: {
      type: String,
      default: ''
    },
    ttAdclickResult: {
      type: String,
      default: ''
    },
    ttAdclickOnlyResult: {
      type: String,
      default: ''
    },
    taboolaLandrResult: {
      type: String,
      default: ''
    },
    taboolaSerpResult: {
      type: String,
      default: ''
    },
    taboolaAdclickResult: {
      type: String,
      default: ''
    },
    taboolaAdclickOnlyResult: {
      type: String,
      default: ''
    },
    outbrainLandrResult: {
      type: String,
      default: ''
    },
    outbrainSerpResult: {
      type: String,
      default: ''
    },
    outbrainAdclickResult: {
      type: String,
      default: ''
    },
    outbrainAdclickOnlyResult: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      copiedLandr: false,
      copiedSerp: false
    }
  },
  methods: {
    copyTextLandr() {
      const text = this.$refs.landrRef.innerText;
      navigator.clipboard.writeText(text)
        .then(() => {
          this.copiedLandr = true;
          setTimeout(() => {
            this.copiedLandr = false;
          }, 2000);
        })
        .catch((error) => {
          alert("Failed to copy text " + error);
        });
    },
    copyTextSerp() {
      const text = this.$refs.serpRef.innerText;
      navigator.clipboard.writeText(text)
        .then(() => {
          this.copiedSerp = true;
          setTimeout(() => {
            this.copiedSerp = false;
          }, 2000);
        })
        .catch((error) => {
          alert("Failed to copy text " + error);
        });
    }
  }
}
</script>

<style scoped>
.landrTextArea {
  height: 330px;
  width: 300px;
  overflow: auto;
}

.serpTextArea {
  height: 380px;
  width: 300px;
  overflow: auto;
}

.pixel-text {
  font-size: small;
  white-space: pre;
  font-family: monospace;
}

.copied-text {
  opacity: 1;
  transition: opacity 0.5s ease-out;
}
</style> 