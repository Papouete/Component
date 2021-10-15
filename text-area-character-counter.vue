<template>
<div>
    <v-textarea 
        v-model="text"
        :maxLength="maxLength"
        outlined 
        placeholder="Mon message..."
        no-resize
        hide-details="">
    </v-textarea>
    <div class="counter pt-2" v-show="hasCharactersRemaining">{{totalCharacters}}/{{maxLength}} caractères.</div>
    <div :class="{'max-counter': !hasCharactersRemaining}" v-show="!hasCharactersRemaining">Limite de caractères atteinte.</div>
</div>
</template>

<script>

export default {

    data() {
        return {
            text: "",
            maxLength: 150,
        };   
    },

    computed: {
        totalCharacters() {
            return this.text.length;
        },
    
        hasCharactersRemaining() {
            return this.totalCharacters < this.maxLength
        },

    },

    watch: {
        text() {
            this.text = this.text.substring(0,this.maxLength)
        }
    }
}
</script>

<style lang="scss">

.max-counter {
    color: red;
}

.counter {
    color:#6b5cd7;
    font-weight: bold;
}

</style>