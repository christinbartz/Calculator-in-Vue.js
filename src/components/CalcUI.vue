<template>
  <div class="calc">
    <div class="calc__row calc__display">1235456</div>
    <div class="calc__row">
      <div id="" class="calc__btn calc__btn--">C</div>
      <div id="" class="calc__btn calc__btn--">+/-</div>
      <div id="" class="calc__btn calc__btn--">%</div>
      <div id="" class="calc__btn calc__btn--">/</div>
    </div>
    <div class="calc__row">
      <div id="" class="calc__btn calc__btn--num">7</div>
      <div id="" class="calc__btn calc__btn--num">8</div>
      <div id="" class="calc__btn calc__btn--num">9</div>
      <div id="" class="calc__btn calc__btn--operator">x</div>
    </div>
    <div class="calc__row">
      <div id="" class="calc__btn calc__btn--num">4</div>
      <div id="" class="calc__btn calc__btn--num">5</div>
      <div id="" class="calc__btn calc__btn--num">6</div>
      <div id="" class="calc__btn calc__btn--operator">-</div>
    </div>
    <div class="calc__row">
      <div id="" class="calc__btn calc__btn--num">1</div>
      <div id="" class="calc__btn calc__btn--num">2</div>
      <div id="" class="calc__btn calc__btn--num">3</div>
      <div id="" class="calc__btn calc__btn--operator">+</div>
    </div>
    <div class="calc__row">
      <div id="" class="calc__btn calc__btn--num">0</div>
      <div id="" class="calc__btn calc__btn--num">.</div>
      <div id="" class="calc__btn calc__btn--operator">=</div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'CalcUI'
}
</script>

<style lang="scss">
.calc {
  display: flex;
  width: 464px;
  height: 640px;
  &__row {
    flex-direction: row;
  }
}
</style>

