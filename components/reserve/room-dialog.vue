<template>
  <v-dialog v-model="dialog" width="600px" persistent>
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
              :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
              :type="show ? 'text' : 'password'"
              label="Password"
              outlined
              dense
              @click:append="show = !show"
            ></v-text-field>
          </v-col>
          <v-col>
            <v-text-field
              v-model="confirmPassword"
              :append-icon="showCon ? 'mdi-eye' : 'mdi-eye-off'"
              :type="showCon ? 'text' : 'password'"
              label="Confirm Password"
              outlined
              dense
              @click:append="showCon = !showCon"
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
        <v-btn color="error darken-1" text @click="$emit('close', false)">
          Close
        </v-btn>
        <v-btn
          color="primary darken-1"
          text
          @click="$emit('confirm', confirm())"
        >
          Confirm
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
import dayjs from 'dayjs'
export default {
  props: {
    date: Date,
    dialog: Boolean,
    focusRoomId: String,
  },
  data: () => ({
    show: false,
    showCon: false,
    firstName: '',
    lastName: '',
    email: '',
    phone: '',
    password: '',
    confirmPassword: '',
    description: '',
    selectedTime: [],
    freeTime: [],
  }),
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
    confirm() {
      return {
        roomId: this.focusRoomId,
        by: `${this.firstName} ${this.lastName}`,
        date: this.date,
        time: this.selectedTime,
        description: this.description,
        password: this.password,
        phone: this.phone,
        email: this.email,
      }
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

<style></style>
