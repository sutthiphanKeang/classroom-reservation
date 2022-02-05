<template>
  <div>
    <ListReserve @search="search" @clear="clear" />
    <v-card class="mt-2" min-height="120" max-height="720">
      <v-card-title>Reservation List</v-card-title>
      <div v-if="loading == true" class="d-flex justify-center">
        <v-progress-circular
          :size="70"
          :width="7"
          color="primary"
          indeterminate
        ></v-progress-circular>
      </div>
      <v-list
        v-else
        class="vscroll pt-0"
        max-height="650"
        max-width="100%"
        ripple
        flat
        ><v-list-item-group>
          <v-list-item
            v-for="(r, index) in reserved"
            :key="index"
            class="list-item"
          >
            <v-list-item-content>
              <v-list-item-title
                ><ReserveScroll :item="r" @cancel="getCancel"></ReserveScroll
              ></v-list-item-title>
            </v-list-item-content>
          </v-list-item> </v-list-item-group
      ></v-list>
    </v-card>
    <CancelReserveDialog :dialog="dialog" @close="close" @confirm="confirm" :error="error" :errorMessage="errorMessage" />
    <v-snackbar v-model="snackbar">
      {{ snackbarMessege }}
      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
import ListReserve from './list-reserve.vue'
import ReserveScroll from './reserve-scroll.vue'
import CancelReserveDialog from './cancel-reserve-dialog.vue'
export default {
  components: { ReserveScroll, CancelReserveDialog, ListReserve },
  data: () => ({
    error: false,
    errorMessage: '',
    loading: false,
    snackbar: false,
    snackbarMessege: '',
    dialog: false,
    time: [
      '08.00-9.30',
      '09.30-11.00',
      '11.00-12.30',
      '12.30-14.00',
      '14.00-15.30',
      '15.30-17.00',
    ],
    reserved: [],
    _id: '',
  }),

  mounted() {
    this.getAllReserved()
  },

  methods: {
    getCancel(value) {
      this._id = value
      this.dialog = true
    },

    close(value) {
      this.error = false
      this.errorMessage = ''
      this.dialog = value
    },

    search(value) {
      const data = {
        name: value.name == '' || value.name == null ? null : value.name,
        number:
          value.number == '' || value.number == null ? null : value.number,
        date:
          value.date == '' || value.date == null
            ? null
            : new Date(value.date).toISOString(),
        start:
          value.time == '' || value.time == null ? null : value.time?.start,
        end: value.time == '' || value.time == null ? null : value.time?.end,
      }
      this.searchRoom(data)
    },
    clear() {
      this.getAllReserved()
    },
    
    async confirm(value) {
      this.snackbar = false
      const data = { password: value, _id: this._id }
      await this.cancelReserves(data)

    },

    async getAllReserved() {
      this.loading = true
      this.reserved = await this.$axios.$get('/reserve/all')
      this.loading = false
    },

    async searchRoom(data) {
      this.loading = true
      this.reserved = await this.$axios.$get(
        `/reserve/search/${data.name}/${data.number}/${data.date}/${data.start}/${data.end}`
      )
      this.loading = false
    },

    async cancelReserves(data) {
      const cancelResult = await this.$axios.$put('/reserve/cancel', data)
      if(cancelResult.includes("Fail")){
        this.errorMessage = cancelResult
        this.error = true
        return

      }
      this.snackbarMessege = cancelResult
      this.dialog = false
      this.snackbar = true
      await this.getAllReserved()
      
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
