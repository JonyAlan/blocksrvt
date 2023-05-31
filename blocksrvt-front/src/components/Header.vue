<template>
  <div class="header m-0 p-0  "> 
    <div class="title" >
      <h1 class="col">
        Não limite sua criatividade, junte-se a familia Blocks por apenas <b>BRL 19,99</b> 
        <span v-on:mouseenter="button = true" v-on:mouseout="button = false"> 
          <b-button v-if="!button"
            class=" btn_blocks">Quero ser Premium
            <img class="mx-2" src="../assets/svg/ico-arow.svg" /> 
          </b-button>  
          <b-button v-else
            class=" btn_blocks_focus">Quero ser Premium
            <img class="mx-2" src="../assets/svg/ico-arow.svg" /> 
          </b-button>   
        </span>
      </h1> 
    </div>
    <div class="logo">
      <img src="../assets/svg/logo.svg" /> 
    </div>  
  </div>
</template>

<script>
export default {
  name: 'HeaderDiv',
  props: {
    msg: String
  },
  data() {
    return {
      button: false, 
    };
  },
  
}
</script>
 
<style  lang="scss">
 
.btn_blocks {
  width: 222px;
  align-items: center;
  padding: 6px 17px; 
  height: 48px; 
  background: linear-gradient(90deg, #A11CF3 0%, #D835C5 100%);
  backdrop-filter: blur(3.5px); 
  border-radius: 8px;
  border: none !important; 
  font-size: 16px;
  font-weight: 600;
  line-height: 22px;
  letter-spacing: 0em;
  text-align: left;
  color: rgba(255, 255, 255, 1);
  margin-left: 18px !important;
}
 
.btn_blocks_focus {
  position: relative;
  width: 220px ;
  margin-left: 19px !important;
  height: 48px;
}
.btn_blocks_focus::before {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 8px; 
  padding: 1px;  
  background: linear-gradient(90deg, #A11CF3 0%, #D835C5 100%) ;
  -webkit-mask: 
     linear-gradient(#090909 0 0) content-box, 
     linear-gradient(#0b0b0b 0 0);
  -webkit-mask-composite: xor; 
          
}

.btn_blocks_focus  { animation: fadeIn .5s; }

@keyframes fadeIn {
  0% { opacity: .2; }
  100% { opacity: 1; }
}
 
 
.header { 
  width: 100%;
  display: flex; 
  flex-direction: column;
  justify-content: center;
  align-items: center;
  .title { 
    width: 100%; 
    padding: 24px 0; 
    background: rgba(36, 36, 36, 0.75);
    backdrop-filter: blur(20px);
  }
  .logo {
    img {
      width: 146px !important;
      height: 54px;
      margin: 13px 0px; 
    }
  }
  h1 {
    font-family: 'Open Sans';
    font-style: normal;
    font-weight: 400;
    font-size: 18px;
    line-height: 25px;
    /* identical to box height */ 
    text-align: center; 
    color: #FFFFFF; 
  }
}
@media only screen and (max-width: 600px) {
  .title{
    display: none;
  }
}

 
</style>
