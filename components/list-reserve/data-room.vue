<template>
  <div>
    <v-card>
      <v-card-title> รายการจอง </v-card-title>
      <div class="mt-2 p-flex align-center">
        <v-virtual-scroll height="408" item-height="100" :items="rooms">
          <template v-slot:default="{ item }">
            <v-list-item :key="item">
              <div class="menu d-flex align-center">
                <v-list-item-content>
                  <v-row>
                    <v-col>
                      <v-list-item-title class="pl-4">
                        Room <strong>ID {{ item.id }}</strong>
                      </v-list-item-title>
                      <v-list-item-title class="pl-4">
                        Name <strong> {{ item.name }}</strong>
                      </v-list-item-title>
                    </v-col>
                    <v-col>
                      <v-list-item-title class="pl-4">
                        Date <strong>{{ item.date }}</strong>
                      </v-list-item-title>
                      <v-list-item-title class="pl-4">
                        Time <strong> {{ item.time }}</strong>
                      </v-list-item-title>
                    </v-col>
                    <v-col class="d-flex justify-end">
                      <v-btn
                        @click="dialog = true"
                        outlined
                        large
                        color="error"
                      >
                        ยกเลิก
                        <v-icon right> mdi-open-in-new </v-icon>
                      </v-btn>
                    </v-col>
                  </v-row>
                </v-list-item-content>
              </div>
            </v-list-item>
          </template>
        </v-virtual-scroll>
      </div>
    </v-card>
    <v-dialog v-model="dialog" width="600px">
      <v-card>
        <v-card-title> ยืนยันการยกเลิก </v-card-title>
        <v-text-field label="Password" outlined dense class="pa-4">
        </v-text-field>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="blue darken-1" text @click="dialog = false">
            Close
          </v-btn>
          <v-btn color="blue darken-1" text @click="confirm()"> Confirm </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
    <v-snackbar v-model="snackbar">
      Success!!!

      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
export default {
  data: () => ({
    dialog: false,
    snackbar: false,
    time: [
      '08.00-9.30',
      '09.30-11.00',
      '11.00-12.30',
      '12.30-14.00',
      '14.00-15.30',
      '15.30-17.00',
    ],
    rooms: [
      {
        id: 'CSB202',
        name: 'Sutthiphan P.',
        date: '25/01/22',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB203',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB204',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB100',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB303',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB202',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB203',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB204',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB100',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB303',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB202',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB203',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB204',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB100',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB303',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB202',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB203',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB204',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB100',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB303',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB202',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB203',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB204',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB100',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
      {
        id: 'CSB303',
        name: 'Sutthiphan P.',
        date: 'ใส่วันน่ะจ้ะ',
        time: 'ใส่เวลาเด้อพี่',
      },
    ],
  }),
  methods: {
    confirm() {
      this.snackbar = true
      this.dialog = false
    },
  },
}
</script>

<style>
.menu {
  height: 100px;
  width: 100%;
  border-top: 1px solid rgba(22, 22, 22, 0.1);
}
</style>
