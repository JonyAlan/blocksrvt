<template>
  <div id="app">
    <Header />
    <div class="row justify-content-center menu">
      <div class="col-11 col-md-8">
        <h2>Catálogo</h2> 
        <hr class="hrh2">
      </div> 
    </div>
    <div class="row justify-content-center"> 
      <div class="col-11 col-md-8">
        <h2 class="descResult">Resultados</h2>  
      </div> 
    </div>

  
    <div class="row justify-content-center"> 
      <div class="row col-11 col-md-8" > 
        <div class="col itensRow" v-for="(item, index) in ListFiles" :key="index"> 
          
            <div class="img">
              <b-img :src="'https://plugin-storage.nyc3.digitaloceanspaces.com/families/images/'+item.id+'.jpg'"  fluid-grow :alt="item.details.name"></b-img>
            </div>   

            <div class="card-footer">
              {{ item.details.name }}
            </div> 
        </div> 
      </div>
    
    
    </div>
    <Footer msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue';
 import axios from "axios";

export default {
  name: 'App',
  components: {
    Header,
    Footer
  },
  data() {
    return {
      ListFiles: [], 
      ListNewFiles: [], 
      init: 0, 
    };
  },
  beforeMount() {
    this.getInitialUsers();
  },
  mounted() {
 
    window.onscroll = () => {
      let bottomOfWindow = document.documentElement.scrollTop + window.innerHeight + 2 > document.documentElement.offsetHeight;
      if (bottomOfWindow) {
        this.getMoreDados()
      }
    }
  
    
  },
  methods: {
    
    getInitialUsers() {
      axios.get(`https://test-candidaturas-front-end.onrender.com/families?skip=0&take=32`)
        .then(async (response) => {
          this.ListFiles = response.data 
      });
    },
  
    getMoreDados() {

      var self = this; 

      this.init += 32
      console.log("🚀 ~ file: App.vue:84 ~ getMoreDados ~ this.init:", this.init)

      axios.get(`https://test-candidaturas-front-end.onrender.com/families?skip=${this.init}&take=${this.init + 32}`)
        .then(async (response) => {
          self.ListFiles.push(...response.data)  
          console.log("🚀 ~ file: App.vue:86 ~ .then ~ self.ListFiles:", self.ListFiles)
        });
    },

     
  },
}
</script>

<style lang="scss">
.row {
  --bs-gutter-x: 0 !important;
}
body { 
  margin: 0;
  padding: 0;
  font-family: 'Open Sans';
  font-style: normal;
  font-weight: 400; 
  line-height: 25px;
}
#app {  
  flex-direction: column;
  font-family: 'Open Sans';
  font-style: normal; 
  .menu {
    background: #FBFBFB;
    width: 100%;
    box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.15);  
    border-top: 1px solid; 
    border-image: linear-gradient(90deg, #A11CF3 0%, #D835C5 100%) 94;
    position: relative;
    h2 {
      font-weight: 700;
      font-size: 28px;
      color: #202020; 
      margin: 29px 0 37px 0;
      line-height: 100%;  
      
    } 
    .hrh2 { 
      width: 33px; 
      margin-top: -35px;  
      left: 150px;
      background: linear-gradient(90deg, #A11CF3 0%, #D835C5 100%); 
      opacity: 1 !important;
      height: 4px; 
      border: 0; 
      border-radius: 50px;
    }
  }
  .descResult { 
    font-weight: 600;
    font-size: 24px;
    line-height: 100%;  
    color: #202020;
    margin-top: 34px;
  }
  .itensRow {
    margin-bottom: 16px;
    margin-right: 16px;
    .img{
      width: 176px;
      height: 198px; 
      border: 1px solid rgba(204, 204, 204, 1);
      box-sizing: border-box; 
      background: #FFFFFF;
      border: 1px solid #CCCCCC;
      border-radius: 8px 8px 0px 0px;  

      display: flex; 
      align-items: center;
      justify-content: center;
      img {
        width: 92px !important;
      }

    }
    .card-footer{
      display: flex;
      width: 176px;
      height: 36px; 
      flex-direction: row;
      align-items: center;
      font-weight: 600;
      font-size: 10px;
      line-height: 100%;
      padding: 8px;
      background: linear-gradient(180deg, #FEFEFE 0%, #F8F8F8 100%);
      border-width: 0px 1px 1px 1px;
      border-style: solid;
      border-color: #CCCCCC;
      backdrop-filter: blur(20px); 
      border-radius: 0px 0px 8px 8px; 
    }
  }
}
@media only screen and (max-width: 600px) {
  .headerApp{
    display: none;
  }
  #app {  
  .itensRow {
    margin-bottom: 16px;
    margin-right: 16px;
    .img{
      width: 138px;
      height: 137px;  
      img {
        width: 70px !important;
      }

    }
    .card-footer{
      display: flex;
      width: 138px; 
      height: 46px;
   
    }
  }
}
}
 
</style>
