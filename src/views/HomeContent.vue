<template>
<div class="content">
 
     <ion-img class="logo" src="../../assets/veg.png"></ion-img>
           <i><h3>VegieTools</h3></i>
           <h4>Bitter Gourd and Paria</h4>   
   </div> 
    
</template>

<script>
 import {IonImg, } from '@ionic/vue';

export default {
     name: 'HomeContent',
   components: {
    IonImg,
  },
}
</script>

<style scoped>
.content{
  text-align: center;
  position: absolute;
  top: 27%;
  left: 50%;
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
  -ms-transform: translateX(-50%);
  transform: translateX(-50%);
}

.logo{
  width: 280px;
   display: block;
  margin-left: auto;
  margin-right: auto;
}
h3{
font-size: 78px;
font-family: 'Barlow Condensed', sans-serif;
font-weight: 1000;
color:#0c4b05;
}
h4{
    font-size: 38px;
    font-family: 'Barlow Condensed', sans-serif;
    color:#000000;
}

@media screen and (max-height: 1920px) {
 .logo{
  width: 500px;
 
}
}
</style>