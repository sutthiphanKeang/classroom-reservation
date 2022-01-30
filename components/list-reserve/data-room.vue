<template>
  <div>
    <v-card>
      <v-card-title> Reservation List </v-card-title>
      <div class="mt-2 p-flex align-center">
        <v-virtual-scroll height="408" item-height="100" :items="reserved">
          <template v-slot:default="{ item }">
            <v-list-item :key="item">
              <v-list-item-content class="item pl-4"
                ><v-row>
                  <v-col
                    ><v-row
                      ><v-col
                        >Name: <strong>{{ item.name }}</strong></v-col
                      ><v-col
                        >Room: <strong>{{ item.roomNumber }}</strong></v-col
                      ><v-col
                        >Date:
                        <strong>{{
                          dayjs(item.date).format('DD/MM/YYYY')
                        }}</strong></v-col
                      >
                      <v-col
                        >Description:
                        <strong>{{ item.description }}</strong></v-col
                      ></v-row
                    ><v-row
                      ><v-col
                        >Time:
                        <v-chip
                          v-for="t in item.times"
                          :key="t"
                          label
                          outlined
                          class="ma-1"
                          color="primary"
                          >{{ t }}</v-chip
                        >
                      </v-col></v-row
                    ></v-col
                  ><v-col cols="1" class="text-end"
                    ><v-btn
                      text
                      @click="dialog = true"
                      outlined
                      large
                      color="error"
                    >
                      Cancel
                    </v-btn></v-col
                  ></v-row
                >
              </v-list-item-content>
            </v-list-item>
          </template>
        </v-virtual-scroll>
      </div>
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
import dayjs from 'dayjs'
export default {
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
      console.log(this.reserved)
    },
    dayjs,
  },
}
</script>

<style lang="scss" scoped>
.item {
  border-top: 1px solid rgba(22, 22, 22, 0.1);
}
</style>
