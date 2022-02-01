<template>
  <kinesis-container class="parent d-flex justify-center">
      <kinesis-element class="welcome w" type="depth" :strength="15" />
      <kinesis-element class="welcome e" type="depth" :strength="20" />
      <kinesis-element class="welcome l" type="depth" :strength="30" />
      <kinesis-element class="welcome c" type="depth" :strength="15" />
      <kinesis-element class="welcome o" type="depth" :strength="30" />
      <kinesis-element class="welcome m" type="depth" :strength="20" />
      <kinesis-element class="welcome e" type="depth" :strength="15" />
      <kinesis-element class="welcome wf" type="depth" :strength="30" />
    </kinesis-container>
</template>

<script>
import { KinesisContainer, KinesisElement } from 'vue-kinesis'
export default {
    components: { KinesisContainer, KinesisElement },
}
</script>

<style lang="scss" scoped>
.parent{
  height: 80px;
}
.welcome {
  
  height: 62px;
  background-size: contain;
  background-repeat: no-repeat;
}
.w {
  background-image: url('../../assets/kinesis/welcome/IMG_3262.PNG');
  width: 50%;
  
}
.e {
  background-image: url('../../assets/kinesis/welcome/IMG_3263.PNG');
  width: 50%;
}
.l {
  background-image: url('../../assets/kinesis/welcome/IMG_3264.PNG');
  width: 50%;
}
.c {
  background-image: url('../../assets/kinesis/welcome/IMG_3265.PNG');
  width: 50%;
}
.o {
  background-image: url('../../assets/kinesis/welcome/IMG_3266.PNG');
  width: 50%;
}
.m {
  background-image: url('../../assets/kinesis/welcome/IMG_3267.PNG');
  width: 50%;
}
.e {
  background-image: url('../../assets/kinesis/welcome/IMG_3268.PNG');
  width: 50%;
}
.wf {
  background-image: url('../../assets/kinesis/welcome/IMG_3269.PNG');
  width: 50%;
}
</style>