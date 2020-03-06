<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center" justify="center">
        <v-icon dark right large style="padding: 50px">mdi-hospital-building</v-icon>
        Hotel Reservation
      </div>
    </v-app-bar>
    <v-content>
      <HotelReservation/>
    </v-content>
  </v-app>
</template>

<script>
import HotelReservation from './components/HotelReservation';

export default {
  name: 'App',

  components: {
    HotelReservation,
  },

  data: () => ({
    //
  }),
};
</script>
