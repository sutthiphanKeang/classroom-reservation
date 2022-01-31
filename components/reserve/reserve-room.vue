<template>
  <div>
    <v-card class="mt-2" min-height="120" max-height="900">
      <v-card-title>Classroom List</v-card-title>
      <v-list class="vscroll pt-0" max-height="820" ripple flat
        ><v-list-item-group>
          <v-list-item
            v-for="(r, index) in rooms"
            :key="index"
            class="list-item"
          >
            <v-list-item-content>
              <v-list-item-title
                ><RoomDetails :item="r" @reserving="setFocusData"
              /></v-list-item-title>
            </v-list-item-content>
          </v-list-item> </v-list-item-group
      ></v-list>
      <RoomDialog
        :dialog="dialog"
        :date="date"
        :focusRoomId="focusRoomId"
        @confirm="sendReserve"
        @close="close"
      />
      <v-snackbar v-model="snackbar">
        {{ snackbarMessege }}
        <template v-slot:action="{ attrs }">
          <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
            Close
          </v-btn>
        </template>
      </v-snackbar>
    </v-card>
  </div>
</template>

<script>
import RoomDetails from './room-details.vue'
import RoomDialog from './room-dialog.vue'
export default {
  components: { RoomDetails, RoomDialog },
  data: () => ({
    dialog: false,
    menu: false,
    snackbar: false,
    snackbarMessege: '',
    date: null,
    focusRoomId: '',
    rooms: [],
  }),

  mounted() {
    this.getAllRooms()
  },

  methods: {
    async sendReserve(data) {
      await this.createReserve(data)
      this.dialog = false
      this.snackbar = true
      this.focusRoomId = ''
      this.date = null
    },

    async createReserve(reaserveData) {
      const reserveResult = await this.$axios.$post('/reserve', reaserveData)
      this.snackbarMessege = reserveResult
    },

    async getAllRooms() {
      this.rooms = await this.$axios.$get('/rooms/all')
    },

    close(value) {
      this.dialog = value
    },
    setFocusData(id) {
      this.dialog = true
      this.focusRoomId = id
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
