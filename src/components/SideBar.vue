<template>
    <div class="bar d-flex align-items-center pt-3 flex-column">
        <div v-for="(img_src,index) in 8" :class="'bar-icon d-flex justify-content-center align-items-center mb-3 icon' + img_src" :key="index">
           <img :src="'./static/icon_' + img_src + '.svg'" class="pl-1 pt-1">
        </div>

    </div>
</template> 


<script>
export default {
  data () {
    return {
        img_url: "../assets/icon_1.svg",
        img_type: ".svg",
        images:["icon_1.svg", "icon_2.svg"]
    }
  }
}
</script>

<style scoped> 
.bar{
    width: 70px;
    background-color: #454c68;
    height: 100%;

}
.bar-icon{
  width: 40px;
  height: 40px;
  background-color: #696E85;
  border-radius: 50%;
}
.icon6{
      background-color: #47a0f9;

}

.active{
    background-color: #51A3F2;
}

@media only screen and (max-width: 1023px) {
  .bar {
    width: 100%;
    flex-direction: row !important;
    justify-content: space-around;
    height: auto;
    flex-wrap: wrap;
  }
  
}
@media only screen and (max-width: 1023px) {
    .bar-icon{
        width: 30px;
        height: 30px;
    }   
}
</style>

