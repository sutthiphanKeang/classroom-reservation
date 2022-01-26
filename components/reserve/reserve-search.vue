<template>
  <v-container>
    <v-row>
      <v-col align-self="center">
        <v-text-field
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
        ></v-select>
      </v-col>
      <v-col>
        <v-select
          :items="type"
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
        <v-btn color="primary" width="100%" text-align="center">
          Search
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
      </v-col>
    </v-row>

    <ReserveRoom class="mt-7" />
  </v-container>
</template>

<script>
import ReserveRoom from './reserve-room.vue'
export default {
  components: { ReserveRoom },
  data: () => ({
    time: [
      '08.00-9.30',
      '09.30-11.00',
      '11.00-12.30',
      '12.30-14.00',
      '14.00-15.30',
      '15.30-17.00',
    ],
    type: ['Lecture', 'Labatory'],
  }),
  computed: {
    items() {
      return Array.from({ length: this.length }, (k, v) => v + 1)
    },
    length() {
      return 20
    },
  },
}
</script>

<style></style>
