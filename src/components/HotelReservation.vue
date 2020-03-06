<template>
 <v-container>
    <v-layout row wrap>
    <v-row class="col-12" justify="center">
      <h1>Find the bast hotel price</h1>
     
    </v-row>
    <v-row class="col-12" justify="center">
        <v-btn large color="primary" style="float: right" @click="calculateBestHotel">Calculate</v-btn>
    </v-row>
    <v-row class="col-12" justify="center">
      <v-col class="col-2" justify="center">
        <v-icon large right style="padding: 50px ">mdi-face</v-icon>
        <v-combobox 
        v-model="selectedClientType"
        :items="clientTypes"
        label="Client Type"></v-combobox>
      </v-col>
      <v-col class="col-10" justify="center">
        <v-date-picker v-model="dates" multiple full-width landscape></v-date-picker>
      </v-col>
    </v-row>

    <v-row class="col-12 p10" justify="center">
      <v-menu
        ref="menu"
        v-model="menu"
        :close-on-content-click="false"
        :nudge-right="40"
        :return-value.sync="dates"
        lazy
        transition="scale-transition"
        offset-y
        full-width
        min-width="290px"
      >
        <template v-slot:activator="{ on }">
          <v-combobox v-model="dates" multiple chips large-chips label="Selected dates" v-on="on"></v-combobox>
        </template>
        <v-date-picker v-model="dates" multiple no-title scrollable>
          <v-spacer></v-spacer>
          <v-btn flat color="primary" @click="menu = false">Cancel</v-btn>
          <v-btn flat color="primary" @click="$refs.menu.save(dates)">OK</v-btn>
        </v-date-picker>
      </v-menu>
    </v-row>
  </v-layout>
 </v-container>
</template>

<script>
import axios from "axios";
axios.defaults.withCredentials = true;
const baseUrl = "";
export default {
  name: "HotelReservation",
  mounted(){
this.selectedClientType = this.clientTypes[0];
  },
  data: () => ({
    dates: [],
    selectedClientType: "",
    clientTypes:[
      "REGULAR",
      "REWARDS"
    ],
    menu: false
  }),
  methods:{
    async calculateBestHotel(){

      const dateList = this.dates.map((date)=>{
       return  new Date(date);
      })
      const payload = {
        clientType: this.selectedClientType ,
        dates:dateList
      }
      console.log(payload);
     await  axios
      .post(
        `${baseUrl}hotels/best-price`,
        payload
      )
      .then(response => {

      })
      .catch(error => {
      });
     
    }
  }
};
</script>

