
<template>
  <v-container>
    <v-form :disabled="isDisabled">
      <v-container>
        <v-row>
          <v-col cols="4" md="4" sm="12" >
            <v-text-field v-model="form.startPoint" label="Start Point" ></v-text-field>
          </v-col>

          <v-col cols="4" md="4" sm="12"  >
              <v-text-field v-model="form.endPoint" label="End Point"></v-text-field>
          </v-col>

          <v-col cols="4" md="4" sm="12" >
            <v-btn
              depressed
              color="primary"
              @click="submit"
              :disabled="isDisabled"
            >
              Get Distance
            </v-btn>
          </v-col>
        </v-row>
      </v-container>
    </v-form>
  </v-container>
</template>

<script>
  const axios = require('axios');

  export default {
    name: 'GetRoadDistance',

    data: () => ({
      form: {
        startPoint: "",
        endPoint: "",
      },
      isDisabled: false
    }),

    methods: {
      async submit() {
        // axios.defaults.headers.get['Content-Type'] ='application/x-www-form-urlencoded';
        // axios.defaults.withCredentials = true
        console.log('axios.defaults.withCredentials: ', axios.defaults.withCredentials);
        const res =  await axios.get('https://maps.googleapis.com/maps/api/distancematrix/json?origins=Washington%2C%20DC&destinations=New%20York%20City%2C%20NY&units=METRIC&key=AIzaSyCs8LFR1x5yfg9nEaB46JA7ifu77y2RdlY/')
        console.log('res: ', res);
      }
    }
  }
</script>
