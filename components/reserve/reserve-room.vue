<template>
  <v-card class="room-card">
    <v-card-title>
      <v-row>
        <v-col align-self="center">
          ห้อง
        </v-col>
        <v-col align-self="center">
          <v-text-field
            label="Search"
            outlined
            dense
            hide-details
            append-icon="mdi-magnify"
          ></v-text-field>
        </v-col>
      </v-row>
    </v-card-title>
    <div class="mt-2 p-flex align-center">
      <v-virtual-scroll height="720" item-height="100" :items="rooms">
        <template v-slot:default="{ item }">
          <v-list-item :key="item">
            <div class="room d-flex align-center">
              <img class="roompic" width="150" height="90" :src="item.pic" />
              <v-list-item-content>
                <v-list-item-title class="pl-4">
                  Room <strong>ID {{ item.id }}</strong>
                </v-list-item-title>
                <v-list-item-title class="pl-4">
                  ขนาด <strong>30</strong> คน
                </v-list-item-title>
              </v-list-item-content>

              <v-list-item-action>
                <v-btn 
                  @click="dialog = true"
                  outlined 
                  large 
                  color="primary"
                >
                  จองส์
                  <v-icon right> mdi-open-in-new </v-icon>
                </v-btn>
              </v-list-item-action>
            </div>
          </v-list-item>
        </template>
      </v-virtual-scroll>
      <v-dialog
        v-model="dialog"
        width="600px"
      >
        <v-card>
          <v-card-title>
            <span class="text-h5">Reserve Detail</span>
          </v-card-title>
          <v-container>
            <v-row dense>
              <v-col>
                <v-text-field
                  label="Firstname"
                  outlined
                  dense
                ></v-text-field>
              </v-col>
              <v-col>
                <v-text-field
                  label="Lastname"
                  outlined
                  dense
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col>
                <v-text-field
                  label="Email"
                  outlined
                  dense
                ></v-text-field>
              </v-col>
              <v-col>
                <v-text-field
                  label="Phone No."
                  outlined
                  dense
                ></v-text-field>
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
                  label="Time"
                  outlined
                  dense
                ></v-select>
              </v-col>
            </v-row>
            <v-row dense>
              <v-col>
                <v-textarea
                  auto-grow
                  outlined
                  label="Description"
                ></v-textarea>
              </v-col>
            </v-row>
          </v-container>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              color="blue darken-1"
              text
              @click="dialog = false"
            >
              Close
            </v-btn>
            <v-btn
              color="blue darken-1"
              text
              @click="confirm()"
            >
              Confirm
            </v-btn>
          </v-card-actions>
          
        </v-card>
      </v-dialog>
      
    </div>
    <v-snackbar
      v-model="snackbar"
    >
      Success!!!

      <template v-slot:action="{ attrs }">
        <v-btn
          color="pink"
          text
          v-bind="attrs"
          @click="snackbar = false"
        >
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
    time:["8.00-9.30","9.30-11.00","11.00-12.30","12.30-14.00"],
    rooms: [
      {
        id: 'CSB202',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB203',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB204',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB100',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB303',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB202',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB203',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB204',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB100',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB303',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB202',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB203',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB204',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB100',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB303',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB202',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB203',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB204',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB100',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB303',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB202',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB203',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB204',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB100',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
      {
        id: 'CSB303',
        pic: 'https://www.cs.science.cmu.ac.th/wp-content/uploads/2020/08/116837622_3250975954946134_5698865583461347309_o.jpg',
      },
    ],
  }),
  methods: {
    confirm(){
      this.snackbar = true;
      this.dialog = false;
  }} 
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
