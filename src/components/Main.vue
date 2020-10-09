<template>
  <div class="main-form">
    <div class="switcher"></div>
    <Switcher
      v-for="switcher in switchers" 
      v-bind:active="switcher.active"
      v-bind:id="switcher.id"
      v-bind:name="switcher.name"
      v-on:switch-action="onSwitchAction"
      v-bind:key="switcher.id"
    ></Switcher>
    <DecimalField
      v-bind:decimalValue="decimalValue"
      v-on:insert-decimal="onInsertDecimalValue"
    ></DecimalField>
    <NumberField
      v-for="roundNumber in roundNumbers" 
      v-bind:val="roundNumber.val"
      v-bind:id="roundNumber.id"
      v-bind:name="roundNumber.name"
      v-on:insert-number="onInsertNumberValue"
      v-bind:key="roundNumber.id"
    >
    </NumberField>
    <FinalResult
      v-bind:finalSolution="resultK"
    >
    </FinalResult>
    <div class="error-msg">{{errorMessage}}</div>
  </div>
</template>

<script>
import Switcher from './Switcher.vue'
import DecimalField from './DecimalField.vue'
import NumberField from './NumberField.vue'
import FinalResult from './FinalResult.vue'

export default {
  name: 'Main',
  components: {
    Switcher,
    DecimalField,
    NumberField,
    FinalResult
  },
  data () {
    return {
      switchers: [
        {id: 0, active: true, name: 'A'},
        {id: 1, active: true, name: 'B'},
        {id: 2, active: true, name: 'C'}
      ],
      decimalValue: 0.0,
      roundNumbers: [
        {id: 'n0', val: 0, name: 'E'}, 
        {id: 'n1', val: 0, name: 'F'}
      ],
      resultK: 0.0,
      errorMessage: ''
    }
  },
  methods: {
    onSwitchAction (event) {
      this.switchers[event].active = !this.switchers[event].active
    },
    onInsertDecimalValue (event) {
      let curVal = event ? parseFloat(event).toFixed(2) : this.decimalValue;
      this.decimalValue = parseFloat(curVal);
    },
    onInsertNumberValue (event) {
      this.roundNumbers.forEach(roundNum => 
        roundNum.id === event.id ? 
          roundNum.val = parseInt(event.number ? 
            event.number : roundNum.val) : false)
    },
    methodM ({D, E, F}) {
      let calc = D + (D * E / 10);

      calc % 1 === 0 ? F + D + (D * E / 100) : calc;
      return calc;
    },
    methodT ({D, F, tryArg}) {
      let calc = D - (D * F / 30);

      if (tryArg) {
        calc = calc % 1 === 0 ? this.methodM : this.methodT
      }
      return calc;
    },
    methodP ({D, E, F}) {
      let calc = D + (D * (E - F) / 25.5);
      calc % 1 === 0 ? 2 * D + (D * E / 100) : calc;
      return calc;
    },
    methodH: function ({A, B, C, M, P, T}) {
      
      let toBeCalled = (A && B && !C) ? () => T({tryArg: true}) : 
        (!A && B && C) ? T : 
        (A && !B && C) ? M : 
        (A && B && C) ? P : 
        () => this.errorHandling();

      return toBeCalled;
    },
    methodK: function () {
      let self = this,
          
          D = self.decimalValue,
          E = self.roundNumbers[0].val,
          F = self.roundNumbers[1].val,

          H = self.methodH({
            A: self.switchers[0].active,
            B: self.switchers[1].active,
            C: self.switchers[2].active,
            M: () => self.methodM({D, E, F}),
            P: () => self.methodP({D, E, F}),
            T: () => self.methodT({D, F})
          }),
          roundResult = parseFloat(H()).toFixed(2);
      self.resultK = parseFloat(roundResult);
      (self.resultK % 1 === 0) && self.errorHandling();
    },
    errorHandling: function () {
      clearTimeout(showError);
      this.errorMessage = 
      'Result must be decimal value. Please try another conditions.';
      let showError = setTimeout(() => {
        this.errorMessage = '';
      }, 2000);
      return 0.0;
    }
  },

  watch: {
    switchers: [
      {
        handler: 'methodH',
        deep: true
      },
      {
        handler: function () {
          (this.resultK || this.decimalValue) > 0 && this.methodK();
        },
        deep: true
      }
    ],
    decimalValue: 'methodK',
    roundNumbers: {
      handler: 'methodK',
      deep: true
    }
  }
}
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
