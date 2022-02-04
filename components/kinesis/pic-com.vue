<template>
  <kinesis-container class="parent d-flex justify-center">
    <kinesis-element class="pic com" type="depth" :strength="15" />
  </kinesis-container>
</template>

<script>
import { KinesisContainer, KinesisElement } from 'vue-kinesis'
export default {
  components: { KinesisContainer, KinesisElement },
}
</script>

<style lang="scss" scoped>
.parent {
  height: 80px;
}
.pic {
  height: 80px;
  position: absolute;
  background-size: contain;
}
.com {
  background-image: url('../../assets/kinesis/pic-com/1.PNG');
  width: 80px;
}
</style>
