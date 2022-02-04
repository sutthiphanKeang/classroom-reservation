<template>
  <kinesis-container class="parent d-flex justify-center">
    <kinesis-element
      class="classroom-reservation c mr-2"
      type="depth"
      :strength="15"
    />
    <kinesis-element
      class="classroom-reservation l mr-2"
      type="depth"
      :strength="20"
    />
    <kinesis-element
      class="classroom-reservation a1 mr-2"
      type="depth"
      :strength="30"
    />
    <kinesis-element
      class="classroom-reservation s1 mr-2"
      type="depth"
      :strength="15"
    />
    <kinesis-element
      class="classroom-reservation s2 mr-2"
      type="depth"
      :strength="30"
    />
    <kinesis-element
      class="classroom-reservation r1 mr-2"
      type="depth"
      :strength="20"
    />
    <kinesis-element
      class="classroom-reservation o1 mr-2"
      type="depth"
      :strength="15"
    />
    <kinesis-element
      class="classroom-reservation o2 mr-2"
      type="depth"
      :strength="30"
    />
    <kinesis-element
      class="classroom-reservation m mr-2"
      type="depth"
      :strength="20"
    />
    <kinesis-element
      class="classroom-reservation r2 mr-2"
      type="depth"
      :strength="30"
    />
    <kinesis-element
      class="classroom-reservation e1 mr-2"
      type="depth"
      :strength="15"
    />
    <kinesis-element
      class="classroom-reservation s3 mr-2"
      type="depth"
      :strength="30"
    />
    <kinesis-element
      class="classroom-reservation e2 mr-2"
      type="depth"
      :strength="20"
    />
    <kinesis-element
      class="classroom-reservation r3 mr-2"
      type="depth"
      :strength="15"
    />
    <kinesis-element
      class="classroom-reservation v mr-2"
      type="depth"
      :strength="30"
    />
    <kinesis-element
      class="classroom-reservation a2 mr-2"
      type="depth"
      :strength="20"
    />
    <kinesis-element
      class="classroom-reservation t mr-2"
      type="depth"
      :strength="15"
    />
    <kinesis-element
      class="classroom-reservation i mr-2"
      type="depth"
      :strength="30"
    />
    <kinesis-element
      class="classroom-reservation o3 mr-2"
      type="depth"
      :strength="20"
    />
    <kinesis-element
      class="classroom-reservation n mr-2"
      type="depth"
      :strength="30"
    />
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
  height: 60px;
}
.classroom-reservation {
  width: 700px;
  height: 100%;
  position: absolute;
  background-size: contain;
}
.c {
  background-image: url('../../assets/kinesis/classroom-reservation/1.PNG');
}
.l {
  background-image: url('../../assets/kinesis/classroom-reservation/2.PNG');
}
.a1 {
  background-image: url('../../assets/kinesis/classroom-reservation/3.PNG');
}
.s1 {
  background-image: url('../../assets/kinesis/classroom-reservation/4.PNG');
}
.s2 {
  background-image: url('../../assets/kinesis/classroom-reservation/5.PNG');
}
.r1 {
  background-image: url('../../assets/kinesis/classroom-reservation/6.PNG');
}
.o1 {
  background-image: url('../../assets/kinesis/classroom-reservation/7.PNG');
}
.o2 {
  background-image: url('../../assets/kinesis/classroom-reservation/8.PNG');
}
.m {
  background-image: url('../../assets/kinesis/classroom-reservation/9.PNG');
}
.r2 {
  background-image: url('../../assets/kinesis/classroom-reservation/10.PNG');
}
.e1 {
  background-image: url('../../assets/kinesis/classroom-reservation/11.PNG');
}
.s3 {
  background-image: url('../../assets/kinesis/classroom-reservation/12.PNG');
}
.e2 {
  background-image: url('../../assets/kinesis/classroom-reservation/13.PNG');
}
.r3 {
  background-image: url('../../assets/kinesis/classroom-reservation/14.PNG');
}
.v {
  background-image: url('../../assets/kinesis/classroom-reservation/15.PNG');
}
.a2 {
  background-image: url('../../assets/kinesis/classroom-reservation/16.PNG');
}
.t {
  background-image: url('../../assets/kinesis/classroom-reservation/17.PNG');
}
.i {
  background-image: url('../../assets/kinesis/classroom-reservation/18.PNG');
}
.o3 {
  background-image: url('../../assets/kinesis/classroom-reservation/19.PNG');
}
.n {
  background-image: url('../../assets/kinesis/classroom-reservation/20.PNG');
}
</style>
