<template>
  <div class="orderAmount">
      <span v-on:click="quantity -= 1" class="orderAmount__button orderAmount__button--minus"><i class="fa fa-minus"></i></span>
      <input v-model="quantity" class="orderAmount__amount" type="text" name="orderAmount">
      <span v-on:click="quantity += 1" class="orderAmount__button orderAmount__button--plus"><i class="fa fa-plus"></i></span>
    <div class="orderAmount__addToCartButton" v-on:click="nextView">バスケットに追加</div>
  </div>
</template>

<style lang="scss" scoped>
$blue: #4a5774;

.orderAmount {
  // display: inline-flex;
  display: flex;
  flex-wrap: wrap;
  filter: drop-shadow(2px 2px 2px #aaa);
  &__button {
    display: inline-flex;
    width: 56px;
    height: 40px;
    background-color: $blue;
    color: #eee;
    align-items: center;
    justify-content: center;
    font-size: 16px;
    margin-bottom: 16px;
    &--minus {
      border-radius: 3px 0 0 3px;
    }
    &--plus {
      border-radius: 0 3px 3px 0;
    }
  }
  &__amount {
    max-width: 142px;
    display: inline-block;
    box-sizing: border-box;
    height: 40px;
    padding: 0;
    margin: 0;
    text-align: center;
    font-size: 24px;
  }
  &__addToCartButton {
    display: inline-flex;
    margin-bottom: 8px;
    align-items: center;
    justify-content: center;
    background-color: red;
    height: 48px;
    width: 100%;
    color: #eee;
    font-weight: bold;
    border-radius: 3px;
    filter: drop-shadow(2px 2px 2px #aaa);
  }
}
</style>

<script>
export default {
  data: function() {
    return {
      quantity: 1 
    }
  },
  methods: {
    nextView: function () {
      this.$emit('nextview');
    }
  }
}
</script>

