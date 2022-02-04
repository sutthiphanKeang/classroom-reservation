<template>
  <kinesis-container class="parent d-flex justify-center">
    <kinesis-element class="welcome w mr-10" type="depth" :strength="15" />
    <kinesis-element class="welcome e1 mr-10" type="depth" :strength="20" />
    <kinesis-element class="welcome l mr-10" type="depth" :strength="10" />
    <kinesis-element class="welcome c mr-10" type="depth" :strength="16" />
    <kinesis-element class="welcome o mr-10" type="depth" :strength="11" />
    <kinesis-element class="welcome m mr-10" type="depth" :strength="20" />
    <kinesis-element class="welcome e2 mr-10" type="depth" :strength="15" />
    <kinesis-element class="welcome wf" type="depth" :strength="18" />
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
  width: 100%;
  height: 170px;
}
.welcome {
  width: 750px;
  height: 100%;
  position: absolute;
  background-size: contain;
}
.w {
  background-image: url('../../assets/kinesis/welcome/1.PNG'); 
}
.e1 {
  background-image: url('../../assets/kinesis/welcome/2.PNG');
}
.l {
  background-image: url('../../assets/kinesis/welcome/3.PNG');
}
.c {
  background-image: url('../../assets/kinesis/welcome/4.PNG');
}
.o {
  background-image: url('../../assets/kinesis/welcome/5.PNG');
}
.m {
  background-image: url('../../assets/kinesis/welcome/6.PNG');
}
.e2 {
  background-image: url('../../assets/kinesis/welcome/7.PNG');
}
.wf {
  background-image: url('../../assets/kinesis/welcome/8.PNG');
}
</style>
