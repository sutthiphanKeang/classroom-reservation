<template>
  <div>
    <v-card class="mt-2" min-height="120" max-height="900">
      <v-card-title>Reservation List</v-card-title>
      <v-list class="vscroll pt-0" max-height="820" ripple flat
        ><v-list-item-group>
          <v-list-item v-for="r in reserved" :key="r" class="list-item">
            <v-list-item-content>
              <v-list-item-title
                ><ReserveScroll :item="r"></ReserveScroll
              ></v-list-item-title>
            </v-list-item-content>
          </v-list-item> </v-list-item-group
      ></v-list>
    </v-card>

    <v-dialog v-model="dialog" width="600px">
      <v-card>
        <v-card-title> Confirm Cancelation </v-card-title>
        <v-text-field label="Password" outlined dense class="pa-4">
        </v-text-field>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1 " text @click="dialog = false">
            Close
          </v-btn>
          <v-btn color="blue darken-1" text @click="confirm()"> Confirm </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-snackbar v-model="snackbar">
      Success!!!
      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
import ReserveScroll from './reserve-scroll.vue'
export default {
  components: { ReserveScroll },
  data: () => ({
    dialog: false,
    snackbar: false,
    time: [
      '08.00-9.30',
      '09.30-11.00',
      '11.00-12.30',
      '12.30-14.00',
      '14.00-15.30',
      '15.30-17.00',
    ],
    reserved: [],
  }),

  mounted() {
    this.getAllReserved()
  },

  methods: {
    confirm() {
      this.snackbar = true
      this.dialog = false
    },

    async getAllReserved() {
      this.reserved = await this.$axios.$get('/reserve/all')
    },
  },
}
</script>

<style lang="scss" scoped>
.vscroll {
  overflow-y: scroll;
}
.list-item {
  border-bottom: solid 1px rgba(22, 22, 22, 0.1);
}
</style>
