<template>
  <v-container>
    <v-card>
      <v-card-title>
        <h3>Please tell us more about yourself.</h3>
        <v-spacer></v-spacer>
        <p>Call: 914-485-4463</p>
      </v-card-title>

        <v-layer 
          justify-center 
          text-center 
          wrap
          >
          <v-flex xs12>
            <center><p class='text-center'>At Multi-line Insurance Agency we are continuously working to provide the individual coverage you require. When it comes to protecting your auto, home, business and family, don't leave it up to chance, or fly-by-night brokers. At Multi-line Insurance Agency we take pride in our business and strive to be relationship specialists providing you with the total insurance solution for all your needs. Being insured with the best has its advantages.</p></center>
          </v-flex>
        </v-layer>

      <v-form class="px3 myform">
        <v-text-field label="First Name" v-model="first"></v-text-field>
        <v-text-field label="Last Name" v-model="last"></v-text-field>
        <v-text-field label="Phone"  v-model="phone" ></v-text-field>
        <v-text-field label="Email"  v-model="email" ></v-text-field>
        <v-textarea label="Additional Comments"  v-model="info" ></v-textarea>
        <v-btn text class="success btn" @click="submit()">Submit</v-btn>
      </v-form>
    </v-card>
  </v-container>
</template>

<script>
import axios from 'axios';
export default {
  data() {
    return {
      first: "",
      last: "",
      phone: "",
      email: "",
      info: ""
    }
  },//end data
  methods: {

    submit() {
      console.log ("Submitting: ", this.first, this.last );

      //cooper s - get campaign identifier from URL

    var varArr = [];
    var vars = {};
    var varKey;
    var varValue;
    var varObj = {}

    var parts = window.location.href.replace(/[?&]+([^=&]+)=([^&]*)/gi, function(m,key,value) {
        vars[key] = value;
    });

    console.log("Our campaign: ", vars.utm_campaign );

      var timestamp = new Date();

      var infoObj = {
        firstname: this.first,
        lastname: this.last,
        phone: this.phone,
        email: this.email,
        info: this.info,
        campaign: vars.utm_campaign,
        timestamp: timestamp
      }

      const url = `https://sleepy-everglades-99189.herokuapp.com/multiline`;

      axios.post(url,infoObj)
        .then(function (response) {
          console.log("POST: ", response.data);

        })
        .catch(function (error) {
          console.log("POST Error: ",  error);
        });
      
          this.first = "";
          this.last="";
          this.phone="";
          this.email="";
          this.info="";
          
    }//end submit
  },//end methods
};//end export
</script>
<style scoped>

.myform {
  padding: 1em;
  background: #eee;
}
.btn {
  padding: 1em;
  float: right;
  color: #fff;
  width: 25%;
  cursor: pointer;
}

.text-center {
  margin: 1em;
  padding: 1em;
  background: #eee;
}
</style>
