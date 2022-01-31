<template>
  <v-dialog v-model="dialog" width="600px" persistent>
    <v-card>
      <v-card-title> Confirm Cancelation </v-card-title>
      <v-text-field
        v-model="password"
        label="Password"
        outlined
        dense
        class="pa-4"
        :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
        :type="show ? 'text' : 'password'"
        @click:append="show = !show"
      >
      </v-text-field>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn color="error darken-1" text @click="$emit('close', false)">
          Close
        </v-btn>
        <v-btn
          color="primary darken-1"
          text
          @click="$emit('confirm', password)"
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

  data: () => ({
    password: '',
    show: false,
  }),
}
</script>

<style></style>
