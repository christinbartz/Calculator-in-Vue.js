<template>
  <div class="calc">
    <div class="calc__display">
      <div> 
        {{displayEvalArray}}
     </div>
    </div>
    <div class="calc__btn-container">
      <div class="calc__row">
        <div @click="clearDisplay()" class="calc__btn calc__btn--double">C</div>
        <div @click="backspaceHandler()" class="calc__btn"><--</div>
        <div @click="opHandler('/')" class="calc__btn calc__btn--operator">/</div>
      </div>
      <div class="calc__row">
        <div @click="numHandler('7')" class="calc__btn calc__btn--num">7</div>
        <div @click="numHandler('8')" class="calc__btn calc__btn--num">8</div>
        <div @click="numHandler('9')" class="calc__btn calc__btn--num">9</div>
        <div @click="opHandler('*')" class="calc__btn calc__btn--operator">x</div>
      </div>
      <div class="calc__row">
        <div @click="numHandler('4')" class="calc__btn calc__btn--num">4</div>
        <div @click="numHandler('5')" class="calc__btn calc__btn--num">5</div>
        <div @click="numHandler('6')" class="calc__btn calc__btn--num">6</div>
        <div @click="opHandler('-')" class="calc__btn calc__btn--operator">-</div>
      </div>
      <div class="calc__row">
        <div @click="numHandler('1')" class="calc__btn calc__btn--num">1</div>
        <div @click="numHandler('2')" class="calc__btn calc__btn--num">2</div>
        <div @click="numHandler('3')" class="calc__btn calc__btn--num">3</div>
        <div @click="opHandler('+')" class="calc__btn calc__btn--operator">+</div>
      </div>
      <div class="calc__row">
        <div id="btn-zero" @click="numHandler('0')" class="calc__btn calc__btn--num calc__btn--double">0</div>
        <div @click="opHandler('.')" class="calc__btn calc__btn--num">.</div>
        <div @click="currentResult()" id="btn-equal" class="calc__btn calc__btn--operator">=</div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'CalcUI',
  data: () => {
    return {
      evalArray: ['0']
    }
  },
  methods: {
    opHandler: function(val) {
      let evalLastVal = this.evalArray[this.evalArray.length -1];
      if(val === '-') {
        if(evalLastVal === '-') {
          return
        } if(evalLastVal === '0'){
          this.evalArray.pop()
          this.evalArray.push(val)
        } else {
          this.evalArray.push(val)
        }
      } else {
        if(evalLastVal === '*' || evalLastVal === '/' || evalLastVal === '.' || evalLastVal === '+') {
          this.evalArray.pop()
          this.evalArray.push(val)
        } else {
          this.evalArray.push(val)
        }
      }
    },
    numHandler: function(val) {
      let evalLastVal = this.evalArray[this.evalArray.length -1];
      if(this.evalArray.length < 2 && evalLastVal === '0'){
        this.evalArray.pop()
        this.evalArray.push(val)
      } else(
        this.evalArray.push(val)
      )
    },
    clearDisplay: function() {
      this.evalArray = ['0']
    },
    backspaceHandler: function() {
      this.evalArray.pop()
    },
    currentResult: function() {
      this.evalArray = [eval(this.displayEvalArray)]
    }
  },
  computed: {
    displayEvalArray: function () {
      return this.evalArray.join('');
    }
  }
}
</script>

<style lang="scss">
  @import '../styles/CalcUI.scss';
</style>

