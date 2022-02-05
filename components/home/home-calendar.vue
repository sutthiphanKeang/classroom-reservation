<template>
  <v-row>
    <v-col cols="12">
      <div class="box">
        <div class="LCD d-flex justify-center">
          <div class="hours">{{ hours }}</div>
          <div class="divider">:</div>
          <div class="minutes">{{ minutes }}</div>
          <div class="divider">:</div>
          <div class="seconds">{{ seconds }}</div>
        </div>
      </div>
    </v-col>
    <v-col class="mt-16" cols="12" align-self= "end">
      <v-date-picker
        v-model="picker"
        dark
        full-width
      ></v-date-picker>
    </v-col>
  </v-row>
</template>

<script>
export default {
  data: () => ({
    picker: new Date(Date.now() - new Date().getTimezoneOffset() * 60000)
      .toISOString()
      .substr(0, 10),
    hours: 0,
    minutes: 0,
    seconds: 0,
  }),
  mounted() {
    setInterval(() => this.setTime(), 1000)
  },
  methods: {
    setTime() {
      const date = new Date()
      let hours = date.getHours()
      let minutes = date.getMinutes()
      let seconds = date.getSeconds()
      hours = hours <= 9 ? `${hours}`.padStart(2, 0) : hours
      minutes = minutes <= 9 ? `${minutes}`.padStart(2, 0) : minutes
      seconds = seconds <= 9 ? `${seconds}`.padStart(2, 0) : seconds
      this.hours = hours
      this.minutes = minutes
      this.seconds = seconds
    },
  },
}
</script>

<style lang="scss" scoped>
.LCD > div {
  font-family: 'alarm clock';
  font-size: 50px;
  color: aliceblue;
  text-shadow: 0 0 0.2em rgb(88, 88, 88), 0 0 0.2em rgb(88, 88, 88),
    0 0 0.2em rgb(88, 88, 88);
}
.box {
  background-color: rgba(0, 0, 0, 0.75);
  border: 1px solid darkgrey;
  border-radius: 7px;
}

</style>
