<template>
   <div class="toast position-relative d-flex align-items-center justify-content-center">
        <img class="icon" :src="'./static/' + action + '.png'" alt="user added" >
        <p>User {{action}}</p> 
        <img class="remove" @click="$emit('remove-toast')" src="static/remove.png" alt="remove user X" >
   </div>
</template>

<script>
export default {
      props: ['action'],
     
}
</script>

<style scoped>
.toast{
    width: 163px;
    height: 36px;
    border-radius: 4px;
    background-color: #ffffff;
    box-shadow: 0 2px 10px 0 rgba(0, 0, 0, 0.08);
}
.remove{
    position: absolute;
    top:33%;
    right: 10px;
}
.icon{
    position: absolute;
    left: 10px;
    top: 33%;
}
</style>