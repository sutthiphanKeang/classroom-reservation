<template>
  <v-container>
    <v-row>
      <v-col align-self="center">
        <v-text-field
          label="Name"
          outlined
          dense
          hide-details
          append-icon="mdi-account"
          v-model="searchReserve.name"
        ></v-text-field>
      </v-col>
      <v-col align-self="center">
        <v-text-field
          label="Room"
          outlined
          dense
          hide-details
          append-icon="mdi-google-classroom"
          v-model="searchReserve.number"
        ></v-text-field>
      </v-col>

      <v-col align-self="center"
        ><v-menu
          ref="menu"
          v-model="menu"
          :close-on-content-click="false"
          transition="scale-transition"
          offset-y
        >
          <template #activator="{ on, attrs }">
            <v-text-field
              label="Date"
              append-icon="mdi-calendar"
              outlined
              dense
              readonly
              v-bind="attrs"
              v-on="on"
              hide-details
              v-model="searchReserve.date"
            ></v-text-field>
          </template>
          <v-date-picker
            ref="picker"
            :max="new Date().toISOString().substr(0, 10)"
            min="1950-01-01"
          ></v-date-picker>
        </v-menu>
      </v-col>

      <v-col align-self="center">
        <v-select
          :items="time"
          append-icon="mdi-clock"
          menu-props="auto"
          hide-details
          label="Time"
          outlined
          dense
          v-model="searchReserve.time"
        ></v-select>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
        <v-btn
          color="primary"
          width="100%"
          text-align="center"
          @click="$emit('search', searchReserve)"
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
    searchReserve: {
      name: null,
      number: null,
      date: null,
      period: null,
    },
  }),

  methods: {
    clear() {
      this.searchReserve = {
        name: null,
        number: null,
        date: null,
        period: null,
      }
      this.$emit('clear')
    },
  },
}
</script>

<style></style>
