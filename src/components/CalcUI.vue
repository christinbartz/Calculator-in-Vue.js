<template>
  <div class="calc">
    <div class="calc__row calc__display">1235456</div>
    <div class="calc__row">
      <div class="calc__btn calc__btn--">C</div>
      <div class="calc__btn calc__btn--">+/-</div>
      <div class="calc__btn calc__btn--">%</div>
      <div class="calc__btn calc__btn--">/</div>
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
      <div @click="clickHandler('0')" class="calc__btn calc__btn--num">0</div>
      <div @click="clickHandler('.')" class="calc__btn calc__btn--num">.</div>
      <div id="" class="calc__btn calc__btn--operator">=</div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'CalcUI',
  data: () => {
    evalArray: []
  },
  methods: {
    clickHandler: (msg) => {
      console.log(msg)
    }
  }
}
</script>

<style lang="scss">
  @import '../styles/CalcUI.scss';
</style>

