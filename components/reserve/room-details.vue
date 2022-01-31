<template>
  <v-row>
    <v-col class="d-flex justify-center" cols="2"
      ><img
        class="roompic"
        width="150"
        height="90"
        :src="roomImage(item.image)"
    /></v-col>

    <v-col align-self="center">
      Room: <strong> {{ item.number }}</strong></v-col
    >
    <v-col align-self="center"
      >Type: <strong> {{ item.type }}</strong></v-col
    >
    <v-col align-self="center"
      >Capacity: <strong> {{ item.quantity }}</strong> seats</v-col
    >

    <v-col cols="1" align-self="center">
      <v-btn
        @click="$emit('reserving', item._id)"
        outlined
        large
        color="primary"
      >
        Reserve
        <v-icon right> mdi-open-in-new </v-icon>
      </v-btn>
    </v-col>
  </v-row>
</template>

<script>
export default {
  props: {
    item: Object,
  },
  methods: {
    roomImage(name) {
      return `${process.env.endpoint}rooms/room-image/${name}`
    },
  },
}
</script>

<style lang="scss" scoped>
.roompic {
  border-radius: 4px;
}
</style>
