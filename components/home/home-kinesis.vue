<template>
  <div>
    <Welcome />
    <ClassroomReservation />
    <ComputerScience />
    <Cmu />
    <PicCom />
  </div>
</template>

<script>
import ClassroomReservation from '../kinesis/classroom-reservation.vue'
import Cmu from '../kinesis/cmu.vue'
import ComputerScience from '../kinesis/computer-science.vue'
import PicCom from '../kinesis/pic-com.vue'
import Welcome from '../kinesis/welcome.vue'
export default {
  components: { Welcome, ComputerScience, ClassroomReservation, Cmu, PicCom },
}
</script>

<style lang="scss" scoped></style>
