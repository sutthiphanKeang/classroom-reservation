<template>
  <kinesis-container class="parent d-flex justify-center">
    <kinesis-element class="cmu c" type="depth" :strength="15" />
    <kinesis-element class="cmu h" type="depth" :strength="20" />
    <kinesis-element class="cmu i1" type="depth" :strength="5" />
    <kinesis-element class="cmu a1" type="depth" :strength="15" />
    <kinesis-element class="cmu n1" type="depth" :strength="20" />
    <kinesis-element class="cmu g" type="depth" :strength="10" />
    <kinesis-element class="cmu m" type="depth" :strength="15" />
    <kinesis-element class="cmu a2" type="depth" :strength="20" />
    <kinesis-element class="cmu i2" type="depth" :strength="10" />
    <kinesis-element class="cmu u" type="depth" :strength="20" />
    <kinesis-element class="cmu n2" type="depth" :strength="15" />
    <kinesis-element class="cmu i3" type="depth" :strength="10" />
    <kinesis-element class="cmu v" type="depth" :strength="20" />
    <kinesis-element class="cmu e" type="depth" :strength="15" />
    <kinesis-element class="cmu r" type="depth" :strength="20" />
    <kinesis-element class="cmu s" type="depth" :strength="20" />
    <kinesis-element class="cmu i4" type="depth" :strength="15" />
    <kinesis-element class="cmu t" type="depth" :strength="20" />
    <kinesis-element class="cmu y" type="depth" :strength="10" />
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
  height: 70px;
}
.cmu {
  width: 500px;
  height: 100%;
  position: absolute;
  background-size: contain;
}
.c {
  background-image: url('../../assets/kinesis/cmu/1.PNG');
}
.h {
  background-image: url('../../assets/kinesis/cmu/2.PNG');
}
.i1 {
  background-image: url('../../assets/kinesis/cmu/3.PNG');
}
.a1 {
  background-image: url('../../assets/kinesis/cmu/4.PNG');
}
.n1 {
  background-image: url('../../assets/kinesis/cmu/5.PNG');
}
.g {
  background-image: url('../../assets/kinesis/cmu/6.PNG');
}
.m {
  background-image: url('../../assets/kinesis/cmu/7.PNG');
}
.a2 {
  background-image: url('../../assets/kinesis/cmu/8.PNG');
}
.i2 {
  background-image: url('../../assets/kinesis/cmu/9.PNG');
}
.u {
  background-image: url('../../assets/kinesis/cmu/10.PNG');
}
.n2 {
  background-image: url('../../assets/kinesis/cmu/11.PNG');
}
.i3 {
  background-image: url('../../assets/kinesis/cmu/12.PNG');
}
.v {
  background-image: url('../../assets/kinesis/cmu/13.PNG');
}
.e {
  background-image: url('../../assets/kinesis/cmu/14.PNG');
}
.r {
  background-image: url('../../assets/kinesis/cmu/15.PNG');
}
.s {
  background-image: url('../../assets/kinesis/cmu/16.PNG');
}
.i4 {
  background-image: url('../../assets/kinesis/cmu/17.PNG');
}
.t {
  background-image: url('../../assets/kinesis/cmu/18.PNG');
}
.y {
  background-image: url('../../assets/kinesis/cmu/19.PNG');
}
</style>
