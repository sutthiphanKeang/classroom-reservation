<template>
  <div>
   
    <v-card
      elevation="16"
      width="80%"
      class="mx-auto"
    >
      <v-virtual-scroll
        :bench="benched"
        :items="items"
        height="700"
        item-height="124"
        class="text-align-center"
      >
        <template v-slot:default="{ item }">
          <v-list-item :key="item">
            <v-list-item-action>
              <v-btn
                fab
                small
                depressed
                color="primary"
              >
                {{ item }}
              </v-btn>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title>
               CSB202 <strong>ID {{ item }}</strong>
              </v-list-item-title>
            </v-list-item-content>

            <v-list-item-action>
              <v-icon small>
                mdi-open-in-new
              </v-icon>
            </v-list-item-action>
          </v-list-item>

          <v-divider></v-divider>
        </template>
      </v-virtual-scroll>
    </v-card>
  </div>
</template>
<script>
  export default {
    data: () => ({
      benched: 0,
    }),
    computed: {
      items () {
        return Array.from({ length: this.length }, (k, v) => v + 1)
      },
      length () {
        return 20
      },
    },
  }
</script>

<style></style>
