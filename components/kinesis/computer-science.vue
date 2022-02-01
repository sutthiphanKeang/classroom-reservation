<template>
  <kinesis-container class="parent d-flex justify-center">
      <kinesis-element class="computer-science c1" type="depth" :strength="15" />
      <kinesis-element class="computer-science o" type="depth" :strength="20" />
      <kinesis-element class="computer-science m" type="depth" :strength="30" />
      <kinesis-element class="computer-science p" type="depth" :strength="15" />
      <kinesis-element class="computer-science u" type="depth" :strength="30" />
      <kinesis-element class="computer-science t" type="depth" :strength="20" />
      <kinesis-element class="computer-science e1" type="depth" :strength="15" />
      <kinesis-element class="computer-science r mr-8" type="depth" :strength="30" />
      <kinesis-element class="computer-science s" type="depth" :strength="20" />
      <kinesis-element class="computer-science c2" type="depth" :strength="30" />
      <kinesis-element class="computer-science i" type="depth" :strength="15" />
      <kinesis-element class="computer-science e2" type="depth" :strength="30" />
      <kinesis-element class="computer-science n" type="depth" :strength="20" />
      <kinesis-element class="computer-science c3" type="depth" :strength="15" />
      <kinesis-element class="computer-science e3" type="depth" :strength="30" />
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
.computer-science {
  height: 20px;
  background-size: contain;
  background-repeat: no-repeat;
}
.c1 {
  background-image: url('../../assets/kinesis/computer-science/IMG_3305.PNG');
  width: 50%;
}
.o {
  background-image: url('../../assets/kinesis/computer-science/IMG_3306.PNG');
  width: 50%;
}
.m {
  background-image: url('../../assets/kinesis/computer-science/IMG_3307.PNG');
  width: 50%;
}
.p {
  background-image: url('../../assets/kinesis/computer-science/IMG_3308.PNG');
  width: 50%;
}
.u {
  background-image: url('../../assets/kinesis/computer-science/IMG_3309.PNG');
  width: 50%;
}
.t {
  background-image: url('../../assets/kinesis/computer-science/IMG_3310.PNG');
  width: 50%;
}
.e1 {
  background-image: url('../../assets/kinesis/computer-science/IMG_3311.PNG');
  width: 50%;
}
.r {
  background-image: url('../../assets/kinesis/computer-science/IMG_3312.PNG');
  width: 50%;
}
.s {
  background-image: url('../../assets/kinesis/computer-science/IMG_3313.PNG');
  width: 50%;
}
.c2 {
  background-image: url('../../assets/kinesis/computer-science/IMG_3314.PNG');
  width: 50%;
}
.i {
  background-image: url('../../assets/kinesis/computer-science/IMG_3315.PNG');
  width: 50%;
}
.e2 {
  background-image: url('../../assets/kinesis/computer-science/IMG_3316.PNG');
  width: 50%;
}
.n {
  background-image: url('../../assets/kinesis/computer-science/IMG_3317.PNG');
  width: 50%;
}
.c3 {
  background-image: url('../../assets/kinesis/computer-science/IMG_3318.PNG');
  width: 50%;
}
.e3 {
  background-image: url('../../assets/kinesis/computer-science/IMG_3319.PNG');
  width: 50%;
}
</style>