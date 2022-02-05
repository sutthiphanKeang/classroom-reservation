<template>
  <v-dialog v-model="dialog" width="600px" persistent>
    <v-card>
      <v-card-title> Confirm Cancelation </v-card-title>
      <v-text-field
        :error = "error"
        :error-messages = "errorMessage"
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
        <v-btn color="error darken-1" text @click="close">
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
    errorMessage: String,
    number: String,
    dialog: false,
    error: false,
  },

  data: () => ({
    password: '',
    show: false,
  }),
  methods: {
    close(){
      this.password = ''
      this.$emit('close', false)
    }
  }
}
</script>

<style></style>
