<template>
   <div class="main-container">
       <div class="header">
           <div>
             <ion-img class="logo1" src="../../assets/logoW.png"></ion-img>
            </div>  <!--end of logohead -->

             <div>
             <h6>VegieTools</h6>
             </div>
       </div><!-- end of header div -->
       <div class="liner">
       </div><!-- end of liner div -->
       
       <div class="content">
           <Transition name="fade">
           <div v-if="hideCon">
           <HomeContent/>
           </div>
            </Transition>
           
             <Transition name="fade"> 
             <div v-if="hideCat" class="viewCategory">
              
                <ViewCategory :language="isEnglish"/>
               
            </div>
             </Transition>

             <Transition name="fade"> 
             <div v-if="hideAboutUs" class="about">
                <About/>
            </div>
              </Transition>
       </div><!-- end of content div -->
        <Transition name="fade">
         <div v-if="lang" class="navigation">
             <h5>Select Language</h5>
           <ul>
              <li @click="eng">English</li>
              <li @click="iloco">Iloco</li>
            </ul>

              <div class="backMore"><ion-icon @click="backMore" src="../../assets/svg/cross.svg" class="ex"></ion-icon></div>

             </div> 
        </Transition>
       <div class="footer">
           <div class="grid-item">
                <ion-icon  @click="aboutClick" class="footerbtn" src="../../assets/svg/info.svg"></ion-icon>
                 <p  @click="aboutClick" >About</p>
            </div>
            <div class="grid-item">
                <ion-icon @click="homeClick"  class="footerbtn" src="../../assets/svg/home.svg"></ion-icon>
                 <p  @click="homeClick" >Home</p>
            </div>
            <div  class="grid-item">
                <ion-icon  @click="categoryClick" class="footerbtn" src="../../assets/svg/apps.svg"></ion-icon>
                <p  @click="categoryClick" >Learn Now</p>
                
            </div>
      </div> <!-- end of footer div -->

  

   </div><!-- end of container div -->
</template>

<script>
import {IonImg, IonIcon, } from '@ionic/vue';
import ViewCategory from './ViewCategory.vue'
import HomeContent from './HomeContent.vue'
import About from './About.vue'


export default {
     name: 'HomePage',
   components: {
    IonIcon,
    IonImg,
    ViewCategory,
    HomeContent,
    About,

  },
  data(){
      return{
          hideCat: false,
          hideAboutUs: false,
          hideCon: true,
          hideClick: false,
          lang: false,
          isEnglish: false,
      }
  }, methods:{
   
    
      categoryClick(){
        this.lang = true;
        
      },
      homeClick(){
          this.hideCat = false;
        this.hideCon = true;
         this.hideAboutUs = false;
        this.lang = false;
      },
      aboutClick(){
          this.hideAboutUs = true;
        this.hideCon = false;
        this.hideCat = false;
        this.lang = false;
      },
      backMore(){
        this.lang = false;
      },
      eng(){
        this.hideCat = false;
        this.hideCon = false;
        this.hideAboutUs = false;
        this.lang = false;
        this.isEnglish = true;
        this.$nextTick(() => {
        this.hideCat = true;
        });
      },
      iloco(){
      this.hideCat = false;
      this.hideCon = false;
      this.hideAboutUs = false;
      this.lang = false;
      this.isEnglish = false;
      this.$nextTick(() => {
      this.hideCat = true;
        });
      }
  }
  
}
</script>

<style scoped>
*{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
}
.main-container{
  position: fixed;
  width: 100%;
  height: 100%;
  background: url("/public/assets/VegieTools.png"); 
  background-size:100% 100%;
}
.header{
    display:flex;
    width: 100%;
    height: 80px;
    background-color:#0c4b05;
}
.liner{
    width: 100%;
    height: 8px;
    background-color: gold;
}
.header > div{
    height: 68px;
  padding: 5px ;
}
.logo1{
    width: 60px;
    margin-top: 2px;
}

.grid-list{
 border-bottom:1px solid rgb(82, 82, 82);
 padding-top:28px;
}
.footer{
   display: grid;
   grid-template-columns: 33% 33% 33%;
    position: absolute;
    bottom: 0;
    width: 100%;
    height: 60px;
    background-color:#0c4b05;
    justify-items: center;
}
.grid-item{
  padding-top: 7px;
}
h1{
    position: absolute;
     padding: 0 0 0 47px;
   font-size: 34px;
   font-family: 'Bebas Neue', sans-serif;
    font-weight:600;
    color:#ffffff; 
}
h6{
    font-family: 'Bebas Neue', sans-serif;
   font-size: 18px;
   color:rgb(255, 255, 255);
   text-align: center;
   font-weight:800;
   padding-top: 25px;

}
ion-icon{ 
    width: 35px;
    height: 35px;
}
.footerbtn{ 
    width: 27px;
    height: 27px;
}
p{
    color:#ffffff;
    font-size: 14px;
    width: 70px;
}
.menubtn{
    position: absolute;
    right: 0;
    margin-right: 10px;
    margin-top: 22px;
}
.self{
    position: absolute;
    left:0;
     padding: 3px 0 0 10px;
}
.power{
    position: absolute;
    left:0;
    padding: 3px 0 0 10px;
}
ion-button{
    background: none;
}

/* CSS for the Menu Container Transition */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.2s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
/* 
End of transition */


.ex{
  width: 22px;
  height: 22px;
}
ion-content{ 
   --background: transparent;
 }
.navigation{
   border: 1px solid black;
  position: absolute;
  width: 75%;
  height: auto;
  top: 53%;  
  left: 50%; 
  transform: translate(-50%, -50%);                                 
  background-color: #161616;
  border-radius: 20px 20px;
}

li{
  font-family:  sans-serif;
  font-size: 20px;
  color:#e9e9e9;
  font-weight:600;
  padding: 18px;
  border-top: 2px solid rgb(54, 54, 54);
}

.backMore{
    position: absolute;
    border-radius: 50px 50px;
    width: 42px;
    height: 42px;
    right: -17px;
    top: -15px;
     z-index: 1;
     background-color: #0c4b05;
     text-align: center;
     padding-top: 11px;

   
}
h5{
  color: white;
  font-size: 22px;
  font-weight: 900;
  font-family: 'Bebas Neue', sans-serif;
  padding-top: 2px;
}


/* 
Responsive CSS */


@media only screen and (max-device-height : 480px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio : 2) {
.header{
    height: 55px;
}
.liner{
    height: 6px;
}
.logo1{
    width: 43px;
}
h6{
   font-size: 16px;
  padding-top: 14px;
}
.footer{
    height: 53px;
}
.footerbtn{ 
    width: 25x;
    height: 25px;
}

p{
    font-size: 11px;
}
h5{
  font-size: 20px;
}


li{
  font-size: 17px;

}

}

@media only screen and (min-device-height : 481px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio : 2) {
.logo{
  width: 200px;

}

.content{
  top: 25%;

}
h3{
font-size: 63px;
}
h4{
    font-size: 28px;

}

}
@media only screen and (min-device-height : 850px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio : 2) {
.logo{
  width: 250px;

}

.content{
  top: 29%;

}
h3{
font-size: 72px;
}
h4{
    font-size: 35px;

}

}
@media screen 
  and (min-height: 1024px){
.logo{
  width: 300px;

}

.content{
  top: 27%;

}
h3{
font-size: 85px;
}
h4{
    font-size: 45px;

}

}
@media screen 
  and (min-height: 1180px){
.logo{
  width: 420px;

}

.content{
  top: 25%;

}
h3{
font-size: 125px;
}
h4{
    font-size: 55px;

}

}
@media screen 
  and (min-height: 1368px){
.logo{
  width: 450px;

}

.content{
  top: 25%;

}
h3{
font-size: 125px;
}
h4{
    font-size: 55px;

}
}

/* landscpae responsive */

@media only screen and (max-device-height : 450px) and (orientation : landscape) and (-webkit-min-device-pixel-ratio : 2) {
.header{
    height: 50px;
}
.liner{
    height: 6px;
}
.logo1{
    width: 38px;
}
h6{
   font-size: 17px;
  padding-top: 8px;
}
.footer{
    height: 50px;
}
.footerbtn{ 
    width: 22x;
    height: 22px;
}

p{
    font-size: 11px;
}
}
</style>