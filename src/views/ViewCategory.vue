<template >

  <div class="Catheader2">
      <div class="head-grid">
        <h6>{{vegetableName}}</h6>
      </div>
      <div class="head-grid">
          <p class="breadcrumbs"><i>{{breadcrumbs}}</i></p>
      </div>   
        </div>
 <Vegetable v-if="contentShow" :content="content"  :num="count" class="content"/>

<div v-if="showMore" class="showMore"><ion-icon class="iconplus" @click="showMoreBtn" src="../../assets/svg/plus.svg"></ion-icon>
 </div>

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
          content: '../workplace/Bitter Gourd/Bitter Gourd Desc',
          vegetableName: 'Bitter Gourd',
          breadcrumbs: 'Bitter Gourd',
          showMore: true,
          keys: '1',
           clickShowMore: false,
           contentShow: true,
           count: 0,

       }
    }else  if(!this.language){
    return{
          content: '../workplace/Paria/Paria-Desc',
          vegetableName: 'Paria',
          breadcrumbs: 'Paria',
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
     height: calc(96vh - 151px);
}
.Catheader2{
  border-radius: 10px 10px;
  background-color: #f7f7f7e3;
  color: rgb(3, 3, 3);
  width: 95%;
  height: 1.75rem;
  transform: translate(+2.5%, +5px);
  margin-bottom: 10px;   
  display: grid;
  grid-template-columns: auto auto;
  
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
  font-weight:500;
  font-size: 13px;
   width: 100%;
   padding: 7px 0 0 0;
}

#h5p-container{
max-width: 100%;
}  
ion-content{ 
   --background: transparent;
 }
.showMore{
    position: absolute;
    border-radius: 50px 50px;
    width: 53px;
    height: 53px;
    right: 15px;
    bottom: 93px;
    z-index: 1;
    background-color: #0c4b05;
    padding-top: 10px; 
}
ion-icon{ 
    width: 33px;
    height: 33px;
}
</style>