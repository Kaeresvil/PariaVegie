<template >

      <div v-if="hideNav" class="navigation">
            <ion-content
                :scroll-events="true"
                >  
           <ul  v-for='(plants, index) in content' :key='index'>
              <li @click="viewDetails(plants.content ,plants.title)">{{plants.title}}</li>
            </ul>
            </ion-content>

              <div class="backMore"><ion-icon @click="backMore" src="../../assets/svg/cross.svg"></ion-icon></div>

      </div>
    
</template>
<script>
import { defineComponent } from 'vue';

export default defineComponent({
     name: 'moreContent',
     props:{
       id:String
     },
  components: { 
       
},
mounted(){
  this.content=this[this.id];
},
data(){
      return{ 
        content:null,
        1:[
          {
            title: 'Description, Nutritive and Variety',
            content:'../workplace/Bitter Gourd/BitterGourd'
            },
          {
            title:'Land Preparation and Crop Establishment ',
            content:'../workplace/Bitter Gourd/LandPreparationandCropEstablishment'
            },
          {
            title:'Integrated Nutrient and Water Management',
            content:'../workplace/Bitter Gourd/IntegratedandWaterManagement'
            },
          {
           title:'Integrated Pest Management',
            content:'../workplace/Bitter Gourd/IntegratedPestManagement'
            },
          {
             title:'Disease Management',
              content:'../workplace/Bitter Gourd/DiseaseManagement'
            },
          {
             title:'Harvesting and Post-harvest Handling',
            content:'../workplace/Bitter Gourd/HarvestingandPostHarvestHandling'
            },
          {
             title:'Self-Test',
             content:'../workplace/Bitter Gourd/Bittergourdpretest'
            },
            ],

            2:[
              {
            title: 'Saguday ti Paria',
            content:'../workplace/Paria/Paria'
              },
              {
            title:'Panaggisagana iti Pagmulaan ken Wagas ti Panagmula',
            content:'../workplace/Paria/PanangisaganaitiPagmulaankenWagastiPanagmula'
            },
              {
            title:'Panagganagan ken Panagpadanum',
            content:'../workplace/Paria/PanagganagankenPanagpadanum'
            },
              {
            title:'Panangmanehar kadagiti Peste',
            content:'../workplace/Paria/PanangmaneharkadagitiPeste'
            },
              {
            title:'Panagmanehar iti Sakit',
            content:'../workplace/Paria/PanagmaneharitiSakit'
            },
             {
            title:'Panangtariwidwid Kadagti Ruot',
            content:'../workplace/Paria/PanangtarawidwidKadagitiRuot'
            },
              {
            title:'Panagapit ken Panangtaming iti Apit',
            content:'../workplace/Paria/PanagapitkenPanangtamingitiApit'
            },
        
            ],
          
  
          hideNav: true,
          moreContent: null,
          
        
      }
  }, methods:{
  
   
      //for Showmore navigation
      backMore(){
      this.$emit('backtoShow');
      },
      viewDetails(content, title){
        this.$emit('existContent', content, title);
      }
     
    }
});
</script>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
ion-icon{ 
    width: 25px;
    height: 25px;
}
ion-content{ 
   --background: transparent;
 }
.navigation{
   border: 1px solid black;
  position: absolute;
  width: 80%;
  height: 50%;
  top: 53%;  
  left: 50%; 
  transform: translate(-50%, -50%);                                 
  background-color: #161616;
  z-index: 1;
  border-radius: 20px 20px;
}

li{
  font-family:  sans-serif;
  font-size: 20px;
  color:#e9e9e9;
  font-weight:600;
  padding: 18px;
  border-bottom: 2px solid rgb(77, 77, 77);
}

.backMore{
    position: absolute;
    border-radius: 50px 50px;
    width: 48px;
    height: 48px;
    right: -15px;
    top: -17px;
     z-index: 1;
     background-color: #0c4b05;
     text-align: center;
     padding-top: 12px;

   
}

@media only screen and (max-device-height : 480px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio : 2) {


li{
  font-size: 16px;
}

.backMore{
    width: 43px;
    height: 43px;
     padding-top: 11px;

   
}
ion-icon{ 
    width: 22px;
    height: 22px;
}

}

@media only screen and (max-device-height : 450px) and (orientation : landscape) and (-webkit-min-device-pixel-ratio : 2) {

li{
  font-size: 16px;
}

.backMore{
    width: 43px;
    height: 43px;
     padding-top: 11px;

   
}
ion-icon{ 
    width: 22px;
    height: 22px;
}
}


</style>