<template>
  <div id="app">
     
    

    
      <h1 id="title"><strong></strong>{{ title }}</h1>
      
        <ul class="list-group">
          
          <h1 class="list-group-item" v-show="date"><strong></strong> {{ date }}</h1>
          
          
        </ul>

      <ul>
        <li class="list">
          <div id="text1">
            <!-- <h2>14:00</h2>
            <h3>Basisbeschätigung Besuch</h3>
            <p>Interessierte für den zweiten Kurs werden uns besuchen</p> -->
            <h2>{{ time1 }}</h2>
            <p>{{ title1 }}</p>
            <p>{{ descriprion1 }}</p>
          </div>
        

       
          <div id="text2">
            <h2>14:00</h2>
            <p>Basisbeschätigung Besuch</p>
            <p>Interessierte für den zweiten Kurs werden uns besuchen</p>
            <!-- <h2>{{ time2 }}/h2>
            <p>{{ title2 }}</p>
            <p>{{ descriprion2 }}</p> -->
          </div>
        

       
          <div id="text3">
            <h2>14:00</h2>
            <p>Basisbeschätigung Besuch</p>
            <p>Interessierte für den zweiten Kurs werden uns besuchen</p>
            <!-- <h2>{{ time3 }}</h2>
            <p>{{ title3}}</p>
            <p>{{ descriprion3 }}</p> -->
          </div>
        </li>
        
      </ul>
      <div id=footer>

        <img 
          :src="imgLink1" 
          :width="logoWidth1"
        >

        <img 
          v-bind:src="imgLink2" 
          :width="logoWidth2"
        >

         <img 
          :src="imgLink3" 
          :width="logoWidth3"
        >
      </div>
    </div>
</template>

<script>


export default {
  
  name: 'App',
  data() {
    return {
        title: "Welcome to Opportunity",
        time1: "14:00",
        title1: "Basisbeschätigung Besuch",
        descriprion1: "Interessierte für den zweiten Kurs werden uns besuchen",
        date: '',
        imgLink1: require("../src/assets/Stadt Zürich.png"),
        // logoWidth1: 100,
        imgLink2: require("../src/assets/Opportunity.png"),
        // logoWidth2: 100,
        imgLink3: require("../src/assets/SAG.png"),
        // logoWidth3: 100,
      };
    },
  
    
      
        methods: {
          
          printDate: function () {
            return new Date().toLocaleDateString();
          }
          
          
        },

        mounted: function () {
          this.date = this.printDate();
        }
  
}
</script>

<style>
#app {
  
}
body {
  background-color: rgb(223, 241, 247);
}
#title {
  font-family:Arial, Helvetica, sans-serif ;
  font-size: 50px;
  padding: 40px;
}
.list {
  list-style-type: none;
}
.list-group-item {
  color: crimson;
  text-align: left;

}

h1 {
  color: rgb(0, 0, 0);
  text-align: auto;
  margin: 50px;
  
}
h2    {
  color: darkred;
}

p { 
  text-align: left;
  font-family: verdana, medium, rgb(245, 3, 48);
  font-size: 20px;
  
}
#text1 {
  color: white;
  font: medium;
  background-color: rgb(109, 55, 196);
  width: auto;
  border: 0px;
  padding: 20px;
  margin-left: 50px;
  margin-right: 80px;
  margin-top: 30px;
 margin-bottom: 30px;
 
}

#text2 {
  color: white;
  font: medium;
  background-color: rgb(109, 55, 196);
  width: auto;
  border: 0px;
  padding: 20px;
  margin-left: 50px;
  margin-right: 80px;
  margin-top: 30px;
 margin-bottom: 30px;
 
}

#text3 {
  color: white;
  font: medium;
  background-color: rgb(109, 55, 196);
  width: auto;
  border: 0px;
  padding: 20px;
  margin-left: 50px;
  margin-right: 80px;
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
  padding: 15px;
  background-color: #ffffff;
  margin: 0px;
  width: 100%;
  
  
}

#footer img {
  height: 50px;
}
</style>
