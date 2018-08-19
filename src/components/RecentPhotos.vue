<template>
   <div class="h-50 pl-3 pt-4">
       <h2>Recent photos</h2>
       <div class="grid-container mt-3 position-relative">
           <img :src="'./static/photo_' + img_src + '.png'" :class="'img ' + 'img' + img_src" v-for="(img_src,index) in photosToShow" class="w-30 mb-3" :key="index"/>
           <div class="count">+{{photosCounter - photosToShow}}</div>
       </div>
   </div>
                
                
</template>

<script>
	
export default {
      data(){
          return{
              photosCounter: 47,
              photosToShow: 5
          }
      }
}

</script>

<style scoped>
.img{
    box-shadow: 0 1px 6px 0 rgba(0, 0, 0, 0.1);
    border: 2px solid white;

}
.grid-container{
    display: grid;
    grid-template-columns: 66.66% 33.34%;
    grid-template-rows:repeat(3, 33.33%);
    grid-template-areas: "img1 img2""img1 img3""img4 img5";
    max-width: 210px;
}
.img1{
    grid-area: img1;
}
.img2{
    grid-area: img2;
}
.img3{
    grid-area: img3;
}
.img4{
    grid-area: img4;
}
.img5{
    grid-area: img5;
    position: relative;
}
.count{
    color: white;
    position: absolute;
    bottom: 15%;
    right: 15%; 
    z-index: 2;   
}
@media only screen and (max-width: 1200px) {
    .img {
        width: 90%;
    }
    .count{
        right: 13%;
    } 
}
</style>