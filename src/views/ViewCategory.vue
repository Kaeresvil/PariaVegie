<template >
<div>
  <div class="Catheader2">
      <div class="head-grid">
        <h6>{{vegetableName}}</h6>
      </div>
      <div class="head-grid">
          <p class="breadcrumbs"><i>{{breadcrumbs}}</i></p>
      </div>   
        </div>
 <Vegetable class="content"/>

    </div> 
</template>
<script>
import { defineComponent } from 'vue';
import Vegetable from './H5Pstandalone.vue'
export default defineComponent({
     name: 'ViewCategory',
  components: {
      Vegetable      
},
  
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
     position: relative;
}
.Catheader2{
  border-radius: 10px 10px;
  background-color: #f7f7f7e3;
  color: rgb(3, 3, 3);
  width: 95%;
  height: 30px;
  transform: translate(+2.5%, +5px);
  margin-bottom: 10px;   
  display: grid;
  grid-template-columns: auto auto;
  
}
</style>