<template>
  <v-app v-bind:style="{ backgroundColor: color}">
    <v-toolbar app class="flex-grow-0 pr-0" dark>
      <v-toolbar-title>
        <router-link to="/" tag="span" style="cursor: pointer">
          Classroom Reservation
        </router-link>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items class="hidden-xs-only">
        <v-btn v-for="item in menuItems" :key="item.title" :to="item.path" flat>
          <v-icon left dark>{{ item.icon }}</v-icon>
          {{ item.title }}
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>
    <v-main> <nuxt /> </v-main>
  </v-app>
</template>

<script>
export default {
  data: () => ({
    menuItems: [
      {
        title: 'Home',
        path: '/',
        icon: 'mdi-home',
      },
      {
        title: 'Classroom',
        path: '/reserve',
        icon: 'mdi-google-classroom',
      },
      {
        title: 'Reservation List',
        path: '/reserved-list',
        icon: 'mdi-format-list-bulleted',
      },
    ],
    color: '#F5F5F5'
  }),
}
</script>

<style lang="scss" scoped>
 
</style>
