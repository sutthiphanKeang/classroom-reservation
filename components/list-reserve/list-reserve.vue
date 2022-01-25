<template>
  <v-container>
    <v-row>
      <v-col align-self="center">
        <v-text-field
          label="Name"
          outlined
          dense
          hide-details
          append-icon="mdi-magnify"
        ></v-text-field>
      </v-col>
      <v-col align-self="center">
        <v-text-field
          label="Room"
          outlined
          dense
          hide-details
          append-icon="mdi-magnify"
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
    </v-row>
    <v-row>
      <v-col>
        <v-btn color="primary" width="100%" text-align="center">
          กดสิจ้ะ
          <v-spacer></v-spacer>
          <v-icon> mdi-magnify </v-icon>
        </v-btn>
      </v-col>
    </v-row>
    
    <DataRoom class = 'mt-7' />
    
  </v-container>
</template>

<script>
import DataRoom from './data-room.vue'
export default {
  components: { DataRoom },
  data: () => ({
    time: [
      '08.00-9.30',
      '09.30-11.00',
      '11.00-12.30',
      '12.30-14.00',
      '14.00-15.30',
      '15.30-17.00',
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
}
</script>

<style></style>
