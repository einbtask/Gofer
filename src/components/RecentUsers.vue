<template>
   <div class="h-50 pl-3 pt-4">
       <h2>Recent users</h2>
       <div class="recent-users d-flex mt-3">
        <div v-for="(img_src,index) in usersToShow" class="w-30 mb-3" :key="index">
           <img  :src="'../../static/user_' + img_src + '.png'" class='user-img rounded-circle' width='50px' height='50px'>
        </div>
        <div class="w-30 d-flex justify-content-center">
            <div class="flex-center more">+{{usersCounter-usersToShow}}</div>
        </div>
       </div>

   </div>
                
                
</template>

<script>
import { EventBus } from '../event-bus.js';
	
export default {
      data(){
          return{
              usersCounter: 24,
              usersToShow: 11
          }
      }
      
}

</script>

<style scoped>
.w-30{
    width: 30%;
}
.user.img{
    object-fit: contain;
}
.recent-users{
    flex-wrap: wrap;
}
.more{
    width: 50px;
  height: 50px;
  border-radius: 40px;
  background-color: #8b8b8b;
  color: white;
  font-weight: bold;

}

</style>