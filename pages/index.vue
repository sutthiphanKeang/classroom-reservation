<template>
  <v-container class="idx">
    <v-row class="welcome">
      <v-col cols="3" align-self="center">
        <home-calendar />
      </v-col>
      <v-col align-self="center">
        <home-kinesis />
      </v-col>
    </v-row>
    <v-row class="contact">
      <v-col>
        <home-contact />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped>
.idx {
  height: 100%;
}
.contact {
  height: 30%;
}
.welcome {
  height: 70%;
}
</style>
