<template>
  <v-card class="room-card">
    <v-card-title> Classroom </v-card-title>
    <div class="mt-2 p-flex align-center">
      <v-virtual-scroll height="408" item-height="100" :items="rooms">
        <template v-slot:default="{ item }">
          <v-list-item :key="item">
            <div class="room d-flex align-center">
              <img
                class="roompic"
                width="150"
                height="90"
                :src="roomImage(item.image)"
              />
              <v-list-item-content>
                <v-list-item-title class="pl-4">
                  Room <strong> {{ item.number }}</strong>
                </v-list-item-title>
                <v-list-item-title class="pl-4">
                  Type <strong> {{ item.type }}</strong>
                </v-list-item-title>
                <v-list-item-title class="pl-4">
                  Capacity <strong> {{ item.quantity }}</strong> seats
                </v-list-item-title>
              </v-list-item-content>

              <v-list-item-action>
                <v-btn
                  @click="setFocusData(item._id)"
                  outlined
                  large
                  color="primary"
                >
                  Reserve
                  <v-icon right> mdi-open-in-new </v-icon>
                </v-btn>
              </v-list-item-action>
            </div>
          </v-list-item>
        </template>
      </v-virtual-scroll>

      <v-dialog v-model="dialog" width="600px">
        <v-card>
          <v-card-title>
            <span class="text-h5">Reserve Detail</span>
          </v-card-title>
          <v-container>
            <v-row dense>
              <v-col>
                <v-text-field
                  label="Firstname"
                  outlined
                  dense
                  v-model="firstName"
                ></v-text-field>
              </v-col>
              <v-col>
                <v-text-field
                  label="Lastname"
                  outlined
                  dense
                  v-model="lastName"
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col>
                <v-text-field
                  label="Email"
                  outlined
                  dense
                  v-model="email"
                ></v-text-field>
              </v-col>
              <v-col>
                <v-text-field
                  label="Phone No."
                  outlined
                  dense
                  v-model="phone"
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col
                ><v-menu
                  ref="menu"
                  v-model="menu"
                  :close-on-content-click="false"
                  transition="scale-transition"
                  offset-y
                  min-width="auto"
                >
                  <template #activator="{ on, attrs }">
                    <v-text-field
                      v-model="date"
                      label="Date"
                      append-icon="mdi-calendar"
                      outlined
                      dense
                      readonly
                      v-bind="attrs"
                      v-on="on"
                    ></v-text-field>
                  </template>
                  <v-date-picker
                    v-model="date"
                    ref="picker"
                    :min="dayjs().add(1, 'day').toISOString().substr(0, 10)"
                  ></v-date-picker>
                </v-menu>
              </v-col>
              <v-col>
                <v-select
                  v-model="selectedTime"
                  :items="freeTime"
                  append-icon="mdi-clock"
                  menu-props="auto"
                  hide-details
                  multiple
                  label="Time"
                  outlined
                  dense
                ></v-select>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col>
                <v-text-field
                  v-model="password"
                  label="Password"
                  outlined
                  dense
                ></v-text-field>
              </v-col>
              <v-col>
                <v-text-field
                  v-model="confirmPassword"
                  label="Confirm Password"
                  outlined
                  dense
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col>
                <v-textarea
                  v-model="description"
                  auto-grow
                  outlined
                  label="Description"
                ></v-textarea>
              </v-col>
            </v-row>
          </v-container>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="error darken-1" text @click="dialog = false">
              Close
            </v-btn>
            <v-btn color="primary darken-1" text @click="confirm()">
              Confirm
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
    <v-snackbar v-model="snackbar">
      {{ snackbarMessage }}
      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </v-card>
</template>

<script>
import dayjs from 'dayjs'
export default {
  data: () => ({
    benched: 0,
    dialog: false,
    menu: false,
    snackbar: false,
    snackbarMessage: '',
    date: null,
    focusRoomId: '',
    firstName: '',
    lastName: '',
    email: '',
    phone: '',
    password: '',
    confirmPassword: '',
    description: '',
    freeTime: [],
    rooms: [],
    selectedTime: [],
  }),

  mounted() {
    this.getAllRooms()
  },

  watch: {
    date(next) {
      if (next && this.focusRoomId != '') {
        this.getFreeTime()
      }
    },
    focusRoomId(next) {
      if (next && this.date != null) {
        this.getFreeTime()
      }
    },
  },

  methods: {
    async confirm() {
      const data = {
        roomId: this.focusRoomId,
        by: `${this.firstName} ${this.lastName}`,
        date: this.date,
        time: this.selectedTime,
        description: this.description,
        password: this.password,
        phone: this.phone,
        email: this.email,
      }
      await this.createReserve(data)
      this.dialog = false
      this.snackbar = true
      this.focusRoomId = ''
      this.date = null
    },

    async createReserve(reaserveData) {
      const reserveResult = await this.$axios.$post('/reserve', reaserveData)
      this.snackbarMessage = reserveResult
    },

    async getAllRooms() {
      this.rooms = await this.$axios.$get('/rooms/all')
    },

    roomImage(name) {
      return `${process.env.endpoint}rooms/room-image/${name}`
    },

    setFocusData(id) {
      this.dialog = true
      this.focusRoomId = id
    },

    async getFreeTime() {
      this.freeTime = await this.$axios.$get('/reserve/freeTime', {
        id: this.focusRoomId,
        date: this.date,
      })
    },
    dayjs,
  },
}
</script>

<style lang="scss" scoped>
.roompic {
  border-radius: 4px;
}
.room {
  height: 100px;
  width: 100%;
  border-top: 1px solid rgba(22, 22, 22, 0.1);
}
</style>
