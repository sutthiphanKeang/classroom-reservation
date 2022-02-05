<template>
  <v-dialog v-model="dialog" width="600px" persistent>
    <v-card>
      <v-form ref="form" v-model="valid" lazy-validation>
        <v-card-title>
          <span class="text-h5">Reserve Detail</span>
        </v-card-title>
        <v-container>
          <v-row dense>
            <v-col>
              <v-text-field
                label="First name"
                outlined
                dense
                v-model="firstName"
                required
                :rules="firstNameRules"
              ></v-text-field>
            </v-col>
            <v-col>
              <v-text-field
                label="Last name"
                outlined
                dense
                v-model="lastName"
                required
                :rules="lastNameRules"
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
                required
                :rules="emailRules"
              ></v-text-field>
            </v-col>
            <v-col>
              <v-text-field
                label="Phone No."
                outlined
                dense
                v-model="phone"
                required
                :counter="10"
                maxlength="10"
                :rules="phoneRules"
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
                    required
                    :rules="dateRules"
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
                multiple
                label="Time"
                outlined
                dense
                required
                :rules="timeRules"
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
                required
                :rules="passwordRules"
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
                required
                :rules="conRules"
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
          <v-btn color="error darken-1" text @click="reset"> Close </v-btn>
          <v-btn color="primary darken-1" text @click="confirm">
            Confirm
          </v-btn>
        </v-card-actions>
      </v-form>
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
  computed: {
    conRules() {
      return [
        (v) => !!v || 'Confirm password is required!',
        (v) => v === this.password || 'The passwords do not match. try again!',
      ]
    },
  },
  data: () => ({
    valid: true,
    show: false,
    showCon: false,
    firstName: '',
    lastName: '',
    email: '',
    phone: '',
    password: '',
    confirmPassword: '',
    description: '',
    same: false,
    selectedTime: [],
    freeTime: [],
    firstNameRules: [
      (v) => !!v || 'First name is required!',
      (v) =>
        (v && v.length >= 2) || 'First name must be more than 2 characters',
    ],
    lastNameRules: [
      (v) => !!v || 'Last name is required!',
      (v) => (v && v.length >= 2) || 'Last name must be more than 2 characters',
    ],
    emailRules: [
      (v) => !!v || 'Email is required!',
      (v) => /.+@.+\..+/.test(v) || 'E-mail must be valid',
    ],
    phoneRules: [
      (v) => !!v || 'Phone number is required!',
      (v) =>
        Number.isInteger(Number(v)) || 'Phone number must be an integer number',
    ],
    dateRules: [(v) => !!v || 'Date is required!'],
    timeRules: [(v) => (v && v.length >= 1) || 'Time is required!'],
    passwordRules: [
      (v) => !!v || 'Password is required!',
      (v) => (v && v.length >= 8) || 'Last name must be more than 8 characters',
      (v) =>
        (v && v.length <= 16) || 'Last name must be less than 16 characters',
    ],
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
      this.valid = this.$refs.form.validate()
      console.log(this.valid)
      if (this.valid) {
        this.$emit('confirm', {
          roomId: this.focusRoomId,
          by: `${this.firstName} ${this.lastName}`,
          date: this.date,
          periods: this.selectedTime,
          description: this.description,
          password: this.password,
          phone: this.phone,
          email: this.email,
        })
        this.firstName = ''
        this.lastName = ''
        this.email = ''
        this.phone = ''
        this.password = ''
        this.confirmPassword = ''
        this.description = ''
        this.selectedTime = []
        this.$refs.form.reset()
      }
    },
    reset() {
      this.$emit('close', false)
      this.$refs.form.reset()
    },
    async getFreeTime() {
      this.freeTime = await this.$axios.$get(
        `/reserve/freeTime/${this.focusRoomId}/${this.date}`
      )
    },
    dayjs,
  },
}
</script>

<style></style>
