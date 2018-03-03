<template>
  <section class="container">
    <div class="phone">
      <img class="phone__image" src="/iphone_mock.png">
      <div class="phone__mockArea">
        <mock></mock>
      </div>
    </div>
  </section>
</template>

<script>
import Mock from '~/components/Mock.vue'

export default {
  components: {
    Mock 
  }
}
</script>

<style lang="scss">
$color__bg1: rgba(26, 97, 138, 0.5);
$color__bg2: rgba(94, 197, 175, 0.5);
$dropshadow: #333;

$phone_width: 320px;
$phone_height: 640px;
$screen_width: 304px;
$screen_height: 506px;

.container {
  background-image: linear-gradient(-0.05turn, $color__bg1 0%, $color__bg2 100%);
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.phone {
  &__image {
    position: fixed;
    top: 50%;
    left: 50%;
    margin-left: $phone_width / 2 * -1;
    margin-top: $phone_height / 2 * -1 + 6;
    width: $phone_width;
    height: $phone_height;
    filter: drop-shadow(20px 20px 30px $dropshadow);

  }
  &__mockArea {
    position: fixed;
    top: 50%;
    left: 50%;
    margin-left: $screen_width / 2 * -1;
    margin-top: $screen_height / 2 * -1;
    width: $screen_width;
    height: $screen_height;
    background-color: #eee;
  }
}
</style>
