<template>
  <v-card class="room-card">
    <v-card-title> Classroom </v-card-title>
    <div class="mt-2 p-flex align-center">
      <v-virtual-scroll height="408" item-height="100" :items="rooms">
        <template v-slot:default="{ item }">
          <v-list-item :key="item">
            <div class="room d-flex align-center">
              <img class="roompic" width="150" height="90" :src="item.pic" />
              <v-list-item-content>
                <v-list-item-title class="pl-4">
                  Room <strong>ID {{ item.id }}</strong>
                </v-list-item-title>
                <v-list-item-title class="pl-4">
                  Type <strong> {{ item.type }}</strong>
                </v-list-item-title>
                <v-list-item-title class="pl-4">
                  Capacity <strong> {{ item.capacity }}</strong> seats
                </v-list-item-title>
              </v-list-item-content>

              <v-list-item-action>
                <v-btn @click="dialog = true" outlined large color="primary">
                  Reserve
                  <v-icon right> mdi-open-in-new </v-icon>
                </v-btn>
              </v-list-item-action>
            </div>
          </v-list-item>
        </template>
      </v-virtual-scroll>
      <v-dialog v-model="dialog" width="600px">
        <v-card>
          <v-card-title>
            <span class="text-h5">Reserve Detail</span>
          </v-card-title>
          <v-container>
            <v-row dense>
              <v-col>
                <v-text-field label="Firstname" outlined dense></v-text-field>
              </v-col>
              <v-col>
                <v-text-field label="Lastname" outlined dense></v-text-field>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col>
                <v-text-field label="Email" outlined dense></v-text-field>
              </v-col>
              <v-col>
                <v-text-field label="Phone No." outlined dense></v-text-field>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col
                ><v-menu
                  ref="menu"
                  v-model="menu"
                  :close-on-content-click="false"
                  transition="scale-transition"
                  offset-y
                  min-width="auto"
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
                    ></v-text-field>
                  </template>
                  <v-date-picker
                    ref="picker"
                    :max="new Date().toISOString().substr(0, 10)"
                    min="1950-01-01"
                  ></v-date-picker>
                </v-menu>
              </v-col>
              <v-col>
                <v-select
                  :items="time"
                  append-icon="mdi-clock"
                  menu-props="auto"
                  hide-details
                  multiple
                  label="Time"
                  outlined
                  dense
                ></v-select>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col>
                <v-text-field label="Password" outlined dense></v-text-field>
              </v-col>
              <v-col>
                <v-text-field
                  label="Confirm Password"
                  outlined
                  dense
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col>
                <v-textarea auto-grow outlined label="Description"></v-textarea>
              </v-col>
            </v-row>
          </v-container>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="blue darken-1" text @click="dialog = false">
              Close
            </v-btn>
            <v-btn color="blue darken-1" text @click="confirm()">
              Confirm
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
    <v-snackbar v-model="snackbar">
      Success!!!

      <template v-slot:action="{ attrs }">
        <v-btn color="pink" text v-bind="attrs" @click="snackbar = false">
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    benched: 0,
    dialog: false,
    menu: false,
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
        id: 'CSB100',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Lecture',
        capacity: '104',
      },
      {
        id: 'CSB201',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Lecture',
        capacity: '25',
      },
      {
        id: 'CSB202',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Lecture',
        capacity: '25',
      },
      {
        id: 'CSB203',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Lecture',
        capacity: '20',
      },
      {
        id: 'CSB207',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Lecture',
        capacity: '30',
      },
      {
        id: 'CSB209',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Lecture',
        capacity: '35',
      },
      {
        id: 'CSB210',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Lecture',
        capacity: '38',
      },
      {
        id: 'CSB301',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Labatory',
        capacity: '40',
      },
      {
        id: 'CSB303',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Labatory',
        capacity: '22',
      },
      {
        id: 'CSB307',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Labatory',
        capacity: '70',
      },
      {
        id: 'CSB308',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Labatory',
        capacity: '30',
      },
      {
        id: 'CSB309',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
        type: 'Labatory',
        capacity: '10',
      },
      ,
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

<style lang="scss" scoped>
.roompic {
  border-radius: 4px;
}
.room {
  height: 100px;
  width: 100%;
  border-top: 1px solid rgba(22, 22, 22, 0.1);
}
</style>
