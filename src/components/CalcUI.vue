<template>
  <div class="calc">
    <div class="calc__display">
      <div> 
        {{displayEvalArray}}
        <br>
        {{joinedCurrentNum}}
     </div>
    </div>
    <div class="calc__btn-container">
      <div class="calc__row">
        <div @click="clearAll()" class="calc__btn">C</div>
        <div @click="clearNum()" class="calc__btn">CE</div>
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
        <div id="btn-zero" @click="numHandler('0')" class="calc__btn calc__btn--num">0</div>
        <div @click="changeSign()" class="calc__btn calc__btn--num">+/-</div>
        <div @click="opHandler('.')" class="calc__btn calc__btn--num">.</div>
        <div @click="result()" id="btn-equal" class="calc__btn calc__btn--operator">=</div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'CalcUI',
  data: () => {
    return {
      evalArray: [],
      currentNum: ['0']
    }
  },
  methods: {
    opHandler: function(val) {
      let evalLastVal = this.evalArray[this.evalArray.length -1];
      let numLastVal = this.currentNum[this.currentNum.length -1];
      if (val === ".") {
        /* if(evalLastVal === ".") {
          return
        } else if (evalLastVal === '*' || evalLastVal === '/' || evalLastVal === '+' || evalLastVal === '-') {
          this.evalArray.push("0")
          this.evalArray.push(val)
        } else {
          this.evalArray.push(val)
        } */
        if(this.currentNum.includes(".")) {
          return
        }
        else (
          this.currentNum.push(val)
        )
      } else {
        if (this.currentNum.length === 0) {
          if(evalLastVal === '*' || evalLastVal === '/' || evalLastVal === '.' || evalLastVal === '+' || evalLastVal === '-') {
            this.evalArray.pop()
            this.evalArray.push(val)
          } else {
              return
          }
        } else {
            this.pushCurrentNum()
            this.evalArray.push(val)
        }
      }
    },
    pushCurrentNum: function() {
      this.evalArray.push(this.joinedCurrentNum)
      this.currentNum = []
    }, 
    numHandler: function(val) {
      let numLastVal = this.currentNum[this.currentNum.length -1];
      if(this.currentNum.length === 1 && numLastVal === '0'){
        this.currentNum.pop()
        this.currentNum.push(val)
      } else(
        this.currentNum.push(val)
      )
    },
    changeSign: function () {
      this.currentNum = [this.joinedCurrentNum * -1]
    },
    clearNum: function() {
      this.currentNum = ['0']
    },
    clearAll: function() {
      this.currentNum = ['0']
      this.evalArray = []
    },
    backspaceHandler: function() {
        this.currentNum.pop()
    },
    result: function() {
      let evalLastVal = this.evalArray[this.evalArray.length -1];
      if((this.currentNum.length === 0) && (evalLastVal === '*' || evalLastVal === '/' || evalLastVal === '.' || evalLastVal === '+' || evalLastVal === '-')) {
        return
      } else {
          this.pushCurrentNum()
          this.currentNum.push(eval(this.displayEvalArray))
          this.evalArray = []
      }
    }
  },
  computed: {
    displayEvalArray: function () {
      return this.evalArray.join('');
    },
    joinedCurrentNum: function () {
      return this.currentNum.join('')
    }
  }
}
</script>

<style lang="scss">
  @import '../styles/CalcUI.scss';
</style>

