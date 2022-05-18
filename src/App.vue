<template>
  <div id="app">
     
    <h1 id="title">{{ title }}</h1>
    <h1 class="currentDate">{{ printcurrentDate() }}</h1>
      
    <ul v-if="entries">


      
      <li class="entry-list"
          v-for="entry in entries"
          :key="entry.id"
      >
        <span class="entry-time">{{ entry[0]}} {{ entry[1].replaceAll("/",".")}}</span>
        <h2 class="entry-title">{{ entry[2]}}</h2>
        <h3 class="entry-description">{{ entry[3]}}</h3>
      </li>       
    </ul>       
    <h1 v-else class="no-entries" >No entries!</h1> 
        
            
    <div id=footer>

        <img 
          :src="imgLink1" 
        
        >

        <img 
          v-bind:src="imgLink2" 
          
        >

         <img 
          :src="imgLink3" 
          
        >
    </div>

  </div>
</template>      
      

        
<script>
import axios from "axios"; // axios is a library for making HTTP requests to the backend


export default {
  
  name: 'App',
  data() {
    return {
        title: "Welcome to Opportunity",
        sheet_id:"1a81aI0Y8ViZO0tI92h2YSMqVQJ8hmNNMyMylXgvwiU4",
        api_token:"AIzaSyA-qeDXOhEeQDA0vQf7LgkF7DQtGnAtmAU",
        entries:[],
        imgLink1: require("../src/assets/Stadt Zürich.png"),
        // logoWidth1: 100,
        imgLink2: require("../src/assets/Opportunity.png"),
        // logoWidth2: 100,
        imgLink3: require("../src/assets/SAG.png"),
        // logoWidth3: 100,
      };
    },
  
        computed: {
            // computed properties are like data properties, but with a method combined and it gets executed automaticly
            gsheet_url() {
            
              return `https://sheets.googleapis.com/v4/spreadsheets/${this.sheet_id}/values:batchGet?ranges=A2%3AE100&valueRenderOption=FORMATTED_VALUE&key=${this.api_token}`;

            },
        },
        methods: {
          getData() {
            axios.get(this.gsheet_url).then((response) => {
              this.entries = response.data.valueRanges[0].values;
            });
          },

          refreshData() {
            
              this.getData();
              this.printcurrentDate()
           
          },
          
          printcurrentDate: function () {

           return new Date().toLocaleDateString();
          }
          
          
        },

        mounted () {
          this.refreshData();// get first initial data and then wait for the next
          setInterval(this.refreshData, 1000*60*30);// wait 30mins for next update
        }
        
          // oder andere Weise das gleiche zu schreiben:

          // this.refreshData(); 
          // setInterval(
          // this.refreshData,
          // 18000000); 
         
          //  oder so:

          //   this.refreshData();
          //   setInterval( function(){
          //   this.refreshData(); 
          //   }, 1000*60*30); 
          
          // oder so:
  
}
</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Inter:wght@500;900&display=swap');

#app {
  font-family:'Inter', Arial, Helvetica, sans-serif; 
}

.no-entries {
  background-color: blue;
  padding: 40px;
  margin-left: 80px;
  text-align: center;
  font-size: 50px;
  color: rgb(255, 234, 0);
}

.entry-time{
  color: #ffffff;
}

h2 {
  color: rgb(219, 85, 94);
}

body {
  background-color: rgb(223, 241, 247);
}

#title {
  font-family: 'Inter', Arial, Helvetica, sans-serif;
  font-size: 60px;
  padding: 40px;
  font-weight: 900;
}

.currentDate {
  color: rgb(104, 106, 119);
  text-align: left;
  font-size: 50px;
  padding: 40px;
}

h1 {
  color: rgb(0, 0, 0);
  text-align: auto;
  margin: 50px;
}

.entry-list{
  list-style-type: none;
  font-family: 'Inter', Arial, Helvetica, sans-serif;
  color: #e1a6c0;
  font: medium;
  background-color: rgb(109, 55, 196);
  border: 0px;
  padding: 20px;
  margin-left: 50px;
  margin-right: 50px;
  margin-top: 30px;
  margin-bottom: 30px;
}

#footer {
  display: flex;
  justify-content: space-between;
  box-sizing: border-box;
  position: fixed;
  bottom: 0;
  left: 0px;
  padding: 40px;
  background-color: #ffffff;
  margin: 0px;
  width: 100%;
}

#footer img {
  height: 50px;
}

</style>
