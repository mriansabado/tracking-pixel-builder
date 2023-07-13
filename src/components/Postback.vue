<template>
<div>
<hr>
   <div class="box map-box">
        <div class="columns">
            <div class="column">
                <label class="label is-inline ml-3">Make a Postback</label>
            </div>
            <div class="is-flex">
                <button @click="this.firePostback" class="button is-success mr-4 mt-2">Make Postback</button>
                <button class="button is-danger mt-2" @click="this.reset">Reset</button>
            </div>
        </div>
        <input class="input mt-3" type="text" placeholder="insert url" v-model="this.postbackURL">
        <div class="textarea is-medium mt-2">
            <div class="pixel-text">
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
        }
    },
    methods: {
         firePostback() {
            this.postbackResult = `var img = document.createElement("img"); 
                img.src = "${this.postbackURL}";
                img.style.display = 'none';
                document.body.appendChild(img);`;
        }
    }
}
</script>