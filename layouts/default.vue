<template>
  <v-app>
    <v-toolbar app class="flex-grow-0 pr-0" dark>
      <v-toolbar-title>
        <router-link to="/" tag="span" style="cursor: pointer">
          ระบบจองห้องเรียน
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
        title: 'หน้าหลัก',
        path: '/',
        icon: 'mdi-home',
      },
      {
        title: 'จองห้องเรียน',
        path: '/reserve',
        icon: 'mdi-google-classroom',
      },
      {
        title: 'รายการ',
        path: '/reserved-list',
        icon: 'mdi-format-list-bulleted',
      },
    ],
  }),
}
</script>

<style lang="scss" scoped></style>
