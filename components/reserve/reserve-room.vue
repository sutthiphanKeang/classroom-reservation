<template>
  <div>
    <ReserveSearch @search="search" @clear="clear" />
    <v-card class="mt-2" min-height="120" max-height="720">
      <v-card-title>Classroom List</v-card-title>
      <div v-if="loading == true" class="d-flex justify-center">
        <v-progress-circular
          :size="70"
          :width="7"
          color="primary"
          indeterminate
        ></v-progress-circular>
      </div>
      <v-list v-else class="vscroll pt-0" max-height="650" max-width="100%" ripple flat
        ><v-list-item-group>
          <v-list-item
            v-for="(r, index) in rooms"
            :key="index"
            class="list-item"
          >
            <v-list-item-content>
              <v-list-item-title
                ><RoomDetails
                  :item="r"
                  @reserving="setFocusData"
                  class="room-details"
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
import ReserveSearch from './reserve-search.vue'
import RoomDetails from './room-details.vue'
import RoomDialog from './room-dialog.vue'
export default {
  components: { RoomDetails, RoomDialog, ReserveSearch },
  data: () => ({
    loading: false,
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
    async clear() {
      await this.getAllRooms()
    },
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
      this.loading = true
      this.rooms = await this.$axios.$get('/rooms/all')
      this.loading = false
    },

    async search(value) {
      const data = {
        number:
          value.number == '' || value.number == null ? null : value.number,
        date:
          value.date == '' || value.date == null
            ? null
            : new Date(value.date).toISOString(),
        start:
          value.time == '' || value.time == null ? null : value.time?.start,
        end: value.time == '' || value.time == null ? null : value.time?.end,
        type: value.type == '' || value.type == null ? null : value.type,
      }

      this.rooms = await this.$axios.$get(
        `/rooms/search/${data.number}/${data.date}/${data.start}/${data.end}/${data.type}`
      )
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
.room-details {
  width: 98%;
}
</style>
