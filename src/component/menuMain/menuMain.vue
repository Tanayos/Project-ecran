<template>
  <div  class="menu" :class="{'is-active2': isActive}">



    <section>
      <div @click="isActives()" id="croix-contenair">
        <img class="croix" src="../../assets/crossTop.svg" alt="">
      </div>
      <img class="img-id" src="../../assets/id-img.png" alt="">
      <p>Bienvenue, <span>{{name}}</span></p>
    </section>

    <ul>
      <router-link class="ul-li" v-for="(p, n) in pages" :to="{name:p}" :key="n" tag="li" active-class="is-active" exact>
        <img class="icone-menu" :src="'../../assets/menu'+n+'.svg'" />
        <span>
          {{p}}
        </span>

      </router-link>

    </ul>

  </div>
</template>




<script>
import{EventBus} from "../../event-bus.js"
export default{
 data (){
   return{
     pages:["Accueil", "Liste de Slides", "Calendrier", "Archives", "Profil", "Aide","Deconnection"],
     name: this.$store.state.name,
     isActive: false,
   }
 },
 mounted(){
   EventBus.$on("toggle-burger", status =>{
    //  console.log(status)
     this.isActive = !status;

   })
 },
 methods : {
   isActives(){
            this.isActive = !this.isActive;
        }
 },
}
</script>




<style lang="scss">

.menu{
    transition: left 0.5s ease;
    background: #1799a6;
    color: white;
    font-size: 1rem;
    height: 100vh;
    left: -25rem;
    // padding: 6rem 2rem 2rem 2rem;
    top: 0;
    width: 15rem;
    z-index: 6;
    position: fixed;



  section{
  text-align: center;
  border-left: 1px solid #1799a6;
  border-right: 1px solid #1799a6;


  #croix-contenair{
    display: flex;
    justify-content: flex-end;

  .croix{
    cursor: pointer;
    width:30px;
    height: 30px;
    margin:10px 10px 0 0;
    }
  }

  .img-id{
    margin-top: 20px;
    width:100px;
    height:100px;
  }

  p{
    margin:0 ;
    padding-bottom: 40px;
    span{
      font-weight: bold;
    }
  }

}
.text-danger{
 left: 10px;
 transition: opacity 0.4s, transform 0s 0.4s;
}
ul{
  display: flex;
  flex-direction:column;
  margin-top: 0;

  .ul-li{
    cursor: pointer;
    display: flex;
    align-items: center;
    margin: 0;

    border:1px solid #1799a6;
    .icone-menu{
      width: 25px;
      padding:10px;
    }

    &.is-active, &:hover{
      background-color: #52858a;
      color:#fff;

    }

  }

}





}// fin menu

.is-active2{
    left: 0%;
  }



</style>
