<template>
  <v-dialog v-model="dialog" width="600px" persistent>
    <v-card>
      <v-card-title> Confirm Cancelation </v-card-title>
      <v-text-field label="Password" outlined dense class="pa-4">
      </v-text-field>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="blue darken-1 " text @click="$emit('closeDialog', false)">
          Close
        </v-btn>
        <v-btn
          color="blue darken-1"
          text
          @click="$emit('confirmDialog', false)"
        >
          Confirm
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  props: {
    number: String,
    dialog: false,
  },

  methods: {},
}
</script>

<style></style>
