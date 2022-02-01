<template>
  <div>
    <Welcome />
    <ComputerScience />
  </div>
</template>

<script>
import ComputerScience from '../kinesis/computer-science.vue'
import Welcome from '../kinesis/welcome.vue'
export default {
  components: {Welcome, ComputerScience},
}
</script>

<style lang="scss" scoped>

</style>
