<template >
<div v-if="showMore" class="showMore"><ion-icon class="iconmenu" @click="showMoreBtn(vegetableName, vegetableid)" src="../../assets/svg/menu-burger.svg"></ion-icon>
 </div>
  <div class="Catheader2">
      <div class="head-grid">
          <p class="breadcrumbs"><i>{{breadcrumbs}}</i></p>
      </div>   
        </div>
 <Vegetable v-if="contentShow" :content="content"  :num="count" class="content"/>



 <MoreView v-if="clickShowMore" :id="vegie" v-on:backtoShow="moreContentBack" v-on:existContent="hideExistContent"/>

</template>
<script>
import { defineComponent } from 'vue';
import Vegetable from './H5Pstandalone.vue'
import MoreView from './moreContent.vue'
export default defineComponent({
     name: 'ViewCategory',
     props:{
    language: {
      type: Boolean,
      required: true
    }

  },
  data(){
     if(this.language){
    return{
          content: '../workplace/Bitter Gourd/BitterGourd',
          vegetableName: 'Bitter Gourd',
          breadcrumbs: 'Description, Nutritive and Variety',
          showMore: true,
          keys: '1',
           clickShowMore: false,
           contentShow: true,
           count: 0,

       }
    }else  if(!this.language){
    return{
          content: '../workplace/Paria/Paria',
          vegetableName: 'Paria',
          breadcrumbs: 'Saguday ti Paria',
          showMore: true,
          keys: '2',
          clickShowMore: false,
          contentShow: true,
          count: 0,
       }
    }
  },
  components: {
      Vegetable,
      MoreView,   
},
methods: {
  showMoreBtn(){
    this.clickShowMore = true;
    this.vegie = this.keys;
    this.showMore = false;
  },
  moreContentBack(){
     this.clickShowMore = false;
    this.vegie = this.keys;
    this.showMore = true;
  },
  hideExistContent(content, title){
     this.clickShowMore = false;
     this.showMore = true;
    this.contentShow = false;
    this.content = content;
    this.breadcrumbs = title;
     this.$nextTick(() => {
        this.contentShow = true;
      });
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
.content{
     height: calc(96vh - 155px);
}
.Catheader2{
  border-radius: 10px 10px;
  background-color: #f7f7f7e3;
  color: rgb(3, 3, 3);
  width: 95%;
  height: auto;
  transform: translate(+2.5%, +5px);
  margin-bottom: 10px;   
  
}
h6{
  font-family: 'Barlow Condensed', sans-serif;
  font-size: 16px;
  color:rgb(36, 36, 36);
  font-weight:1000;
   float: left;
   width: auto;
   padding: 3px 0 0 10px;
}
.breadcrumbs{
  color: black;
  font-weight:700;
  font-size: 14px;
   width: 100%;
   padding: 6px 0 6px 0;
}

#h5p-container{
max-width: 100%;
}  
ion-content{ 
   --background: transparent;
 }
.showMore{
  position: absolute;
  right: 18px;
  top: 20px;
}
.iconmenu{
    width: 37px;
    height: 37px;

}

/* 
Responsive CSS */


@media only screen and (max-device-height : 480px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio : 2) {
 .content{
    height: calc(96vh - 131px);
}

.showMore{
  right: 18px;
  top: 13px;
}
.iconmenu{
    width: 27px;
    height: 27px;

}

}



@media only screen and (min-device-height : 741px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio : 2) {
 .content{
    height: calc(96vh - 151px);
}

}

@media only screen and (min-device-height : 952px) and (orientation : portrait) and (-webkit-min-device-pixel-ratio : 2) {
 .content{
    height: calc(96vh - 138px);
}

}

@media only screen and (max-device-height : 450px) and (orientation : landscape) and (-webkit-min-device-pixel-ratio : 2) {

 .content{
    height: calc(96vh - 131px);
}

.showMore{
  right: 18px;
  top: 13px;
}
.iconmenu{
    width: 27px;
    height: 27px;

}
}
</style>