<template>
   <div class='user d-flex align-items-center pl-3' @click="activeUser" :class="{ active: isActive }">
      <img :src="user.img" class='user-image rounded-circle mr-3' width='30px' height='30px'/>
      <span>{{user.first_name}} {{user.last_name}}</span>
      <div class="details" :class="{ show: showDetails }">
        <img class="remove position-absolute" src="static/remove.png" alt="remove user X" @click="$emit('remove-user', user)">
        <UserDetails :user="user"/>
      </div>
    </div>
</template>

<script>
import UserDetails from './UserDetails'

export default {
    data(){
        return{
            isActive: false,
            showDetails: false
        }
    },
    props: ['user'],
    components:{ UserDetails },
    methods:{
        activeUser: function(){
            this.isActive = !this.isActive;
            this.showDetails = !this.showDetails;
    //   },
    //   removeUser: function(){
    //       this.$parent.users.$remove(this.user);
        }
    }
}

</script>

<style scoped>
.user{
    height: 66px;
    border-bottom: solid 1px #e6e9f2;
    position:relative;
}
.active{
    background-color:#f5f7fa;
}
.remove{
    top: 40%;
    right: 15px;
}
.show{
    display: block !important;
    
}
.details{
    display: none;
}
</style>