<template>
<div>
<hr>
   <div class="box map-box">
        <div class="columns">
            <div class="column">
                <label class="label is-inline ml-3">Make a Postback</label>
                 <button @click="this.copyPostback" class="is-inline button is-small is-warning is-rounded ml-3">copy</button>
                 <p v-if="this.copiedPostback" class="is-inline has-text-danger is-size-7 ml-3">Text Copied to Clipboard</p>
            </div>
            <div class="is-flex">
                <button @click="this.firePostback" class="button is-success mr-4 mt-2">Make Postback</button>
                <button class="button is-danger mt-2" @click="this.reset">Reset</button>
            </div>
        </div>
        <input class="input mt-3" type="text" placeholder="insert url" v-model="this.postbackURL">
        <div class="textarea is-medium mt-2">
            <div ref="postbackref" class="pixel-text">
                {{ this.postbackResult }}
            </div>
        </div>
    </div>
</div>
</template>

<style>

</style>

<script>
export default {
    data() {
        return {
             postbackURL: "",
            postbackResult: "",
             copiedPostback: false
        }
    },
    methods: {
         firePostback() {
            this.postbackResult = `var img = document.createElement("img"); 
                img.src = "${this.postbackURL}";
                img.style.display = 'none';
                document.body.appendChild(img);`;
        },
         copyPostback() {
            const text = this.$refs.postbackref.innerText;
            navigator.clipboard.writeText(text)
                .then(() => {
                    this.copiedPostback = true;
                })
                .catch((error) => {
                    alert("Failed to copy text " + error);
                });
        },
         reset() {
            location.reload();
        }
    }
}
</script>