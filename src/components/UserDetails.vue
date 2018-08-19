<template>
   <div class="details d-flex">
       <div class="username flex-center flex-column p-3">
           <div class="arrow-up position-absolute"></div>
           <img :src="user.img" class='user-image rounded-circle mb-2' width='60px' height='60px'>
           <span>{{user.username}}</span>
       </div>
       <div class="p-3 text-left">
           <span>{{user.first_name}} {{user.last_name}}</span>
            <p>{{user.email}}</p>
            <p>{{user.bday}}</p>
            <p>{{user.phone}}</p>
       </div>
   </div>
                
                
</template>

<script>
	
export default {
      props: ['user']
}

</script>

<style scoped>
.details{
    position: absolute;
    width: 100%;
    min-width: 280px;
    top: 108%;
    z-index: 2;
    left:15%;
    box-shadow: 0 1px 6px 0 rgba(0, 0, 0, 0.1);
    background-color: #ffffff;
    border: solid 1px #e6e9f2;
}
.username{
    border-right: solid 1px #e6e9f2;
}
.arrow-up {
    top:-9px;
    width: 0; 
    height: 0; 
    border-left: 10px solid transparent;
    border-right: 10px solid transparent;
    border-bottom: 10px solid #ffffff;
}
p{
    color: #a5a8b5;
}



</style>