<template>
    <div class="box flex-center">
        <h1 
            style="text-align: center; margin: 10% auto 10px">
            🔥Calculator🔥</h1>
        <form class="flex-center forms">
            <input type="number" class="inputs" v-model="input_1">

            <select class="inputs" v-model="operator">
                <option value="+">+</option>
                <option value="-">-</option>
                <option value="*">×</option>
                <option value="/">÷</option>
            </select>

            <input type="number" class="inputs" v-model="input_2">
            
            <button  
                class="inputs cool-button"
                @click.prevent="displayResult()"
                >
                Calculate!
            </button>
        </form>
        
        <p
            v-show="showResult"
        ><b>{{ resultText }}</b></p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            input_1: null,
            input_2: null,
            operator: '',
            resultText: '',
            showResult: false,
        }
    },
    methods: {
        displayResult() {
            if (this.input_1 && this.operator && this.input_2) {
                this.showResult = true;
            }
            
            if (!this.input_1) {
                alert("Wadahelly? Put an input in the first input first my guy");
            }
            else if (!this.operator) {
                alert("Give an operator before you proceed... NOW!");
            }
            else if (!this.input_2) {
                alert("Oh my goodness complete the thing before you click calculate PLEASE");
            }

            if (this.input_1 == 9 && this.operator == "+" && this.input_2 == 10) {
                this.resultText = 'Result: 21'

                // to say 21 is true in App.vue
                this.$emit('show-21');
            }
            else {
                this.resultText = 'Result: Hello World!'
            }
        }
    }
}
</script>

<style scoped>
.flex-center {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-content: center;
}

.box {
    background: white;
    border: 1px solid rgb(225, 225, 225);
    border-radius: 20px;
    box-shadow: 6px 6px;

    width: 16%;
    max-width: 20%;

    padding: 0px 10px 3px;
    
    position: fixed;
    left: 42%;
    top: 2%;
}

.forms {
    font-size: xx-large;
    width: 90%;
    max-width: 90%;
}

.inputs {
    font-size: 20px;
    height: 30px;
    width: 100%;
    max-width: 100%;
    margin: 10px;
}

p {
    font-size: 18px;
    margin: 10px auto;
    text-align: center;
}

/* Button from CSS Scan */

.cool-button {
  background-color: #e8f9ee;
  border-radius: 100px;
  box-shadow: rgba(44, 187, 99, .2) 0 -25px 18px -14px inset,rgba(44, 187, 99, .15) 0 1px 2px,rgba(44, 187, 99, .15) 0 2px 4px,rgba(44, 187, 99, .15) 0 4px 8px,rgba(44, 187, 99, .15) 0 8px 16px,rgba(44, 187, 99, .15) 0 16px 32px;
  color: rgb(20, 117, 20);
  text-shadow: 0px 0px 0px rgb(23, 89, 23);
  cursor: pointer;
  display: inline-block;
  padding: 0px;
  text-align: center;
  height: auto;
  text-decoration: none;
  transition: all 250ms;
  border: 0px;
  font-size: 25px;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  margin-bottom: 15px;
}

.cool-button:hover {
  box-shadow: rgba(44,187,99,.35) 0 -25px 18px -14px inset,rgba(44,187,99,.25) 0 1px 2px,rgba(44,187,99,.25) 0 2px 4px,rgba(44,187,99,.25) 0 4px 8px,rgba(44,187,99,.25) 0 8px 16px,rgba(44,187,99,.25) 0 16px 32px;
  text-shadow: 3px 3px 5px rgb(84, 233, 84);
  transform: scale(1.05) rotate(-1deg);
}
</style>