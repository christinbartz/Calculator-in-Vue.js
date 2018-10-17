<template>
  <div class="calc">
    <div class="calc__display">
     <div> {{displayEvalArray}} </div>
    </div>
    <div class="calc__btn-container">
      <div class="calc__row">
        <div @click="clearDisplay()" class="calc__btn calc__btn--double">C</div>
        <div class="calc__btn calc__btn--">+/-</div>
        <div @click="clickHandler('/')" class="calc__btn calc__btn--operator">/</div>
      </div>
      <div class="calc__row">
        <div @click="clickHandler('7')" class="calc__btn calc__btn--num">7</div>
        <div @click="clickHandler('8')" class="calc__btn calc__btn--num">8</div>
        <div @click="clickHandler('9')" class="calc__btn calc__btn--num">9</div>
        <div @click="clickHandler('*')" class="calc__btn calc__btn--operator">x</div>
      </div>
      <div class="calc__row">
        <div @click="clickHandler('4')" class="calc__btn calc__btn--num">4</div>
        <div @click="clickHandler('5')" class="calc__btn calc__btn--num">5</div>
        <div @click="clickHandler('6')" class="calc__btn calc__btn--num">6</div>
        <div @click="clickHandler('-')" class="calc__btn calc__btn--operator">-</div>
      </div>
      <div class="calc__row">
        <div @click="clickHandler('1')" class="calc__btn calc__btn--num">1</div>
        <div @click="clickHandler('2')" class="calc__btn calc__btn--num">2</div>
        <div @click="clickHandler('3')" class="calc__btn calc__btn--num">3</div>
        <div @click="clickHandler('+')" class="calc__btn calc__btn--operator">+</div>
      </div>
      <div class="calc__row">
        <div id="btn-zero" @click="clickHandler('0')" class="calc__btn calc__btn--num calc__btn--double">0</div>
        <div @click="clickHandler('.')" class="calc__btn calc__btn--num">.</div>
        <div id="btn-equal" class="calc__btn calc__btn--operator">=</div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'CalcUI',
  data: () => {
    return {
      evalArray: []
    }
  },
  methods: {
    clickHandler: function(num) {
      this.evalArray.push(num)
    },
    clearDisplay: function() {
      this.evalArray = []
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

