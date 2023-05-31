<template>
  <div class="fixedFooter">
    <div class="row justify-content-center align-items-center footer m-0 b-0"> 
      <div class="col mx-0 px-0">
        <a href="http://" target="_blank" rel="noopener noreferrer">Sobre</a> 
      </div> 
      <div class="col mx-0 px-0">
        <a href="http://" target="_blank" rel="noopener noreferrer">FAQ</a> 
      </div> 
      <div class="col mx-0 px-0">
        <a href="http://" target="_blank" rel="noopener noreferrer">Termos de uso</a> 
      </div> 
      <div class="col mx-0 px-0">
        <a href="http://" target="_blank" rel="noopener noreferrer">Politica de privacidade</a> 
      </div> 
    </div>

    <Transition> 
      <div v-if="!closeTitleMobile" class="titleMobile" >
        <p class="col">
          <b @click="closeTitleMobile = true">Fechar 
            <img class="mx-2" src="../assets/svg/logo-close.svg" /> 
          </b> 
        </p> 
        <p class="col">
          Não limite sua criatividade, junte-se a familia Blocks por apenas <b>BRL 19,99</b> 
        </p> 
        
        <b-button 
          class="mx-3 btn_blocks">Quero ser Premium
          <img class="mx-2" src="../assets/svg/ico-arow.svg" /> 
        </b-button> 
      </div>
    </Transition>
  </div>
</template>

<script>
export default {
  name: 'FooterDiv',
  props: {
    msg: String
  },
  data() {
    return {
      closeTitleMobile: false, 
    };
  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.fixedFooter{
  position: fixed;
  left: 0;
  bottom: 0;
  width: 100%;
}
.footer {
   background: rgba(233, 233, 233, 1);
   height: 65px;
   color: white;
   text-align: center; 
   .col {
    max-width: 168px !important;
   }
   a {
    text-decoration: none;
    color: #322E2E;
    font-size: 16px;
    line-height: 22px; 
     
  }
}
.titleMobile { 
  width: 100%;
  display: none; 
  flex-direction: column;
  justify-content: center;
  align-items: center; 
  width: 100%; 
  padding: 24px 14px; 
  background: #242424;
  backdrop-filter: blur(20px); 
  font-weight: 400;
  font-size: 15px;
  line-height: 20px;
  text-align: center; 
  color: #FFFFFF; 
   
}
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}
.v-enter-from,
.v-leave-to {
  opacity: 0;
}
@media only screen and (max-width: 600px) {
  .titleMobile {  
    display: flex; 
  }

  .footer{ 
    flex-direction: column;
    height: auto;
    padding-top: 18px;
    padding-bottom: 18px;
    align-items: start !important;
    padding-left: 14px;
    text-align: initial !important;
    .col {
      padding: 6px;
      max-width: 168px !important; 
      display: flex;
      line-height: 19px; 
    }
  }
}
</style>
