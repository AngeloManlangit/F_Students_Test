<template>
  <calculator
        @set-easter-egg="addEasterEgg($event)"
    />

  <prog21EE v-if="showProg21" />

  <Jon v-if="showJon" />
    
  <speaker 
    :file_index="fIndex">
  </speaker>
</template>

<script>
import calculator from '../components/calculator.vue'
import speaker from '../components/speaker.vue'
import prog21EE from '../components/21Programming.vue'
import Jon from '../components/Jon.vue'

export default {
    components: {
        calculator,
        speaker,
        prog21EE,
        Jon
    },
    data() {
        return {
            showProg21: false,
            showJon: false,
            fIndex: 0
        }
    },
    methods: {
        addEasterEgg(eggNum) {
            if (eggNum == 21) {
                this.showProg21 = true;
            }
            else if (eggNum == 69) {
                this.showJon = true;
                this.fIndex = 1;
            }
        }
    }
}
</script>