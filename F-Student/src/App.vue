<template>
    <calculator
        @show-21="is21 = true"
    />

    <a 
        v-if="is21" 
        href="https://github.com/AngeloManlangit/21-Programming" 
        target="_blank" >
        <img style="padding: 5px; height:30vh; border-radius: 100%;" src="./assets/21Programming.png">
    </a>
    

    <speaker>
    </speaker>
</template>

<script>
import calculator from './components/calculator.vue'
import speaker from './components/speaker.vue'

export default {
    components: {
        calculator,
        speaker
    },
    data() {
        return {
            is21: false
        }
    }
}
</script>
