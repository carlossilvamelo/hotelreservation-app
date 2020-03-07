<template>
  <div class="text-center">
    <v-dialog v-model="dialog" width="500">
      <v-card>
        <v-card-title class="headline grey lighten-2" primary-title>Hotels informations</v-card-title>
        <v-data-table
          :headers="headers"
          :items="hotels"
          :items-per-page="5"
          item-key="name"
        ></v-data-table>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" text @click="close()">Ok</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  name: "ModalResult",
  props: {
    dialog: {
      type: Boolean,
      required: true,
      default: false
    },
    hotels: {
      type: [],
      required: true
    }
  },
  data () {
      return {
        headers: [
          {
            text: 'Name',
            align: 'start',
            value: 'name',
          },
          { text: 'Classification', value: 'classification' },
          { text: 'Price', value: 'calculatedPrice' },
        ],
        desserts: [
        ],
      }
    },
    methods:{
      close(){
         this.$emit("confirmationEvent", {});
      }
    }

};
</script>