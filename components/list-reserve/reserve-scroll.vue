<template>
  <v-row>
    <v-col>
      <v-row>
        <v-col align-self="center">
          Name: <strong>{{ item.name }}</strong>
        </v-col>
        <v-col align-self="center">
          Room: <strong>{{ item.roomNumber }}</strong>
        </v-col>
        <v-col align-self="center">
          Date:
          <strong>{{ dayjs(item.date).format('DD/MM/YYYY') }}</strong>
        </v-col>
        <v-col align-self="center">
          Description:<strong>{{ item.description }}</strong>
        </v-col>
      </v-row>
      <v-row>
        <v-col align-self="center">
          Time:
          <v-chip
            v-for="(i, index) in item.periods"
            :key="index"
            label
            outlined
            class="ml-1"
            color="primary"
            >{{ i.start }} - {{ i.end }}
          </v-chip>
        </v-col>
        <v-col cols="3" align-self="center">
          <ReserveStatus :date="item.date" :status="item.cancelled" />
        </v-col>
      </v-row>
    </v-col>
    <v-col cols="1" class="text-end" align-self="center">
      <v-btn
        text
        @click="$emit('cancel', item._id)"
        outlined
        large
        color="error"
        :disabled="item.cancelled"
      >
        Cancel
      </v-btn>
    </v-col>
  </v-row>
</template>

<script>
import dayjs from 'dayjs'
import ReserveStatus from './reserve-status.vue'
export default {
  components: { ReserveStatus },
  props: {
    item: Object,
  },

  methods: {
    dayjs,
  },
}
</script>

<style></style>
