<template>
  <v-card class="room-card">
    <v-card-title>ห้อง</v-card-title>
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
                <v-btn outlined large color="primary">
                  จองส์
                  <v-icon right> mdi-open-in-new </v-icon>
                </v-btn>
              </v-list-item-action>
            </div>
          </v-list-item>
        </template>
      </v-virtual-scroll>
    </div>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    benched: 0,
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
