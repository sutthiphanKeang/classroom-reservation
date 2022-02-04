<template>
  <kinesis-container class="parent d-flex justify-center">
      <kinesis-element class="computer-science c1" type="depth" :strength="15" />
      <kinesis-element class="computer-science o" type="depth" :strength="20" />
      <kinesis-element class="computer-science m" type="depth" :strength="30" />
      <kinesis-element class="computer-science p" type="depth" :strength="15" />
      <kinesis-element class="computer-science u" type="depth" :strength="30" />
      <kinesis-element class="computer-science t" type="depth" :strength="20" />
      <kinesis-element class="computer-science e1" type="depth" :strength="15" />
      <kinesis-element class="computer-science r" type="depth" :strength="30" />
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
  width: 100%;
  height: 80px;
}
.computer-science {
  width: 650px;
  height: 100%;
  position: absolute;
  background-size: contain;
}
.c1 {
  background-image: url('../../assets/kinesis/computer-science/1.PNG');
}
.o {
  background-image: url('../../assets/kinesis/computer-science/2.PNG');
}
.m {
  background-image: url('../../assets/kinesis/computer-science/3.PNG');
}
.p {
  background-image: url('../../assets/kinesis/computer-science/4.PNG');
}
.u {
  background-image: url('../../assets/kinesis/computer-science/5.PNG');
}
.t {
  background-image: url('../../assets/kinesis/computer-science/6.PNG');
}
.e1 {
  background-image: url('../../assets/kinesis/computer-science/7.PNG');
}
.r {
  background-image: url('../../assets/kinesis/computer-science/8.PNG');
}
.s {
  background-image: url('../../assets/kinesis/computer-science/9.PNG');
}
.c2 {
  background-image: url('../../assets/kinesis/computer-science/10.PNG');
}
.i {
  background-image: url('../../assets/kinesis/computer-science/11.PNG');
}
.e2 {
  background-image: url('../../assets/kinesis/computer-science/12.PNG');
}
.n {
  background-image: url('../../assets/kinesis/computer-science/13.PNG');
}
.c3 {
  background-image: url('../../assets/kinesis/computer-science/14.PNG');
}
.e3 {
  background-image: url('../../assets/kinesis/computer-science/15.PNG');
}
</style>