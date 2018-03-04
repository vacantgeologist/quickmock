<template>
  <div class="productArea">
    <img class="productArea__image" src="//jp.images-monotaro.com/Monotaro3/pi/thum/mono08239813-061102-02.jpg">
    <div class="productArea__info">
      <div class="infoArea">
        <span class="infoArea__shippingDays">当日</span>
        <span class="infoArea__price">￥292</span>
        <span class="productDescription">
          <div class="productDescription__text">
            <p class="infoLine">
              <span class="infoLine__tag">注文コード</span>
              <span class="infoLine__text">20394857</span>
            </p>
            <p class="infoLine">
              <span class="infoLine__tag">品番</span>
              <span class="infoLine__text">EX-2039482-34</span>
              <span class="infoLine__tag">容量</span>
              <span class="infoLine__text">1双</span>
              <span class="infoLine__tag">サイズ</span>
              <span class="infoLine__text">L</span>
            </p>
          </div>
        </span>
      </div>
    </div>
    <no-ssr>
      <transition name="component-fade" mode="out-in" leave-active-class="grow">
        <component v-bind:is="view" v-on:nextview="changeView"></component>
      </transition>
    </no-ssr>
  </div>
</template>

<script>
import OrderAmount from './OrderAmount.vue';

export default {
  data: () => {
    return {
      displayState: {
        init: true,
        setAmount: false,
        addedToCard: false
      },
      view: 'v-a'
    }
  },
  components: {
    'v-a': {
        data: function() {
          return {
            lac: 'grow'
          }
        },
        template: '<div class="productArea__addToCartButton" v-on:click="$emit(\'nextview\')">購入する</div>',
    },
    'v-b': OrderAmount,
    'v-c': {
      template: '<div class="productArea__addToCartSuccessPanel"><span class="productArea__addToCartSuccessIcon"><i class="fa fa-check-circle"></i></span>バスケットに追加しました</div>',
    },
  },
  methods: {
    changeView: function () {
        console.log('Hey nah', this.view);
      switch (this.view) {
        case 'v-a':
        this.view = 'v-b';
        break;
        case 'v-b':
        this.view = 'v-c';
        break;
        case 'v-c':
        this.view = 'v-a';
        break;
      }

    }
  }
}
</script>

<style lang="scss">
$grey: #aaa;
$light_grey: #dfdfdf;

@keyframes grow {
  50% { height: 104px; margin-top: 0; }
  100% { height: 48px; margin-top: 56px; }
}

.grow {
  animation: grow .2s ease;
}
.shrink {
  background-color: green;
}

.component-fade-enter-active, .component-fade-leave-active {
  // transition: opacity .3s ease .3s;
}
.component-fade-enter, .component-fade-leave-to {
  // opacity: 0;
}

.productArea {
  background-color: white;
  width: 100%;
  padding: 16px;
  border-radius: 4px;
  display: flex;
  flex-wrap: wrap;
  &__image {
    width: 100px;
    height: 100px;
    margin-bottom: 16px;
    margin-right: 8px;
  }
  &__info {
    font-size: 12px;
    width: 50%;
    flex-grow: 2;
    margin-bottom: 16px;
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
  &__addToCartSuccessPanel {
    display: inline-flex;
    margin-bottom: 8px;
    align-items: center;
    justify-content: center;
    background-color: #6cdd92;
    height: 104px;
    width: 100%;
    color: white;
    font-size: 16px;
    font-weight: bold;
    border-radius: 3px;
  }
  &__addToCartSuccessIcon {
    color: white;
    font-size: 32px;
    margin-right: 16px;
  }
}

.infoArea {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  &__price {
    display: inline-flex;
    align-items: center; 
    justify-content: flex-end;
    background-color: #fff2dd;
    color: red;
    font-weight: bold;
    font-size: 24px;
    height: 24px;
    padding: 0 8px;
    margin-bottom: 8px;
  }
  &__shippingDays {
    flex-grow: 2;
    margin-right: 8px;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    background-color: red;
    color: #eee;
    height: 24px;
    font-size: 16px;
    letter-spacing: 4px;
    border-radius: 3px;
    margin-bottom: 8px;
  }
}

.infoLine {
  text-align: left;
  line-height: 16px;
  &__tag {
    flex-grow: 0;
    display: inline-block;
    height: 16px;
    background-color: #ccc;
    border: 1px solid #555;
    border-radius: 2px;
    color: #333;
    font-weight: bold;
    margin-right: 8px;
    margin-bottom: 8px;
    padding: 0 4px;
  }
  &__text {
    flex-grow: 2;
    margin-right: 8px;
  }
}


</style>



