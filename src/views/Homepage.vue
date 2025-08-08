<template>
  <calculator
        @set-easter-egg="addEasterEgg($event)"
    />

  <prog21EE v-if="showProg21" />
    
  <speaker>
  </speaker>
</template>

<script>
import calculator from '../components/calculator.vue'
import speaker from '../components/speaker.vue'
import prog21EE from '../components/21Programming.vue'

export default {
    components: {
        calculator,
        speaker,
        prog21EE
    },
    data() {
        return {
            showProg21: false
        }
    },
    methods: {
        addEasterEgg(eggNum) {
            if (eggNum == 21) {
                this.showProg21 = true;
            }
        }
    }
}
</script>