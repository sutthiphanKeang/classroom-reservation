<template>
  <v-container>
    <v-row>
      <v-col align-self="center">
        <v-text-field
          v-model="searchData.number"
          label="Room"
          outlined
          dense
          hide-details
          append-icon="mdi-google-classroom"
        ></v-text-field>
      </v-col>

      <v-col align-self="center"
        ><v-menu
          ref="menu"
          :close-on-content-click="false"
          transition="scale-transition"
          offset-y
        >
          <template #activator="{ on, attrs }">
            <v-text-field
              label="Date"
              v-model="searchData.date"
              append-icon="mdi-calendar"
              outlined
              dense
              readonly
              v-bind="attrs"
              v-on="on"
              hide-details
            ></v-text-field>
          </template>
          <v-date-picker
            ref="picker"
            v-model="searchData.date"
            :min="dayjs().add(1, 'day').toISOString().substr(0, 10)"
          ></v-date-picker>
        </v-menu>
      </v-col>

      <v-col align-self="center">
        <v-select
          :items="time"
          v-model="searchData.time"
          append-icon="mdi-clock"
          menu-props="auto"
          hide-details
          label="Time"
          outlined
          dense
        ></v-select>
      </v-col>
      <v-col>
        <v-select
          :items="type"
          v-model="searchData.type"
          menu-props="auto"
          hide-details
          label="Type"
          outlined
          dense
        ></v-select>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-btn
          color="primary"
          width="100%"
          text-align="center"
          @click="$emit('search', searchData)"
        >
          Search
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
      </v-col>
      <v-col>
        <v-btn
          color="secondary"
          width="100%"
          text-align="center"
          outlined
          @click="clear"
        >
          Clear
          <v-icon>mdi-trash-can-outline </v-icon>
        </v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import dayjs from 'dayjs'
export default {
  data: () => ({
    time: [
      { text: '08.00 - 09.30', value: { start: '8.00', end: '9.30' } },
      { text: '09.30 - 11.00', value: { start: '9.30', end: '11.00' } },
      { text: '11.00 - 12.30', value: { start: '11.00', end: '12.30' } },
      { text: '12.30 - 14.00', value: { start: '12.30', end: '14.00' } },
      { text: '14.00 - 15.30', value: { start: '14.00', end: '15.30' } },
      { text: '15.30 - 17.00', value: { start: '15.30', end: '17.00' } },
    ],
    searchData: {
      date: null,
      number: null,
      time: null,
      type: null,
    },
    type: [
      { text: 'Lecture', value: 0 },
      { text: 'Laboratory', value: 1 },
    ],
  }),
  computed: {
    items() {
      return Array.from({ length: this.length }, (k, v) => v + 1)
    },
    length() {
      return 20
    },
  },
  methods: {
    clear() {
      this.searchData = {
        date: null,
        number: null,
        time: null,
        type: null,
      }
      this.$emit('clear')
    },
    dayjs,
  },
}
</script>

<style></style>
