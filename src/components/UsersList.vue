<template>
    <div class="users-list pt-3">
        <h2 class="pl-3">Gofer Users</h2>
        <User v-on:remove-user="removeUser" v-for="(user,index) in users" :user="user" :key="index"/>
    </div>
</template> 


<script>
    import { EventBus } from '../event-bus.js';
    import User from './user.vue';
    export default {
        
        data(){
            return{
            users: [{first_name:"David", last_name:"Cohen", bday:"2.4.2000", phone:"058-5458888", email:"davidc@gmail.com", username:"davidC", password:"*****", img:"../../static/man1.png"},
                    {first_name:"Dana", last_name:"Shalom", bday:"1.5.1886", phone:"052-4554488", email:"dana@gmail.com", username:"dandan", password:"*****", img:"../../static/woman2.png"}],
            } 
        },
        components: {
            User     
        },
        methods:{
            toast: function(arg){
                let action = arg
                EventBus.$emit('show-toast', action);
            },
            removeUser: function(clickedUser){
                this.users = this.users.filter(user => user !== clickedUser);
                this.toast("deleted");
            },
            addUser: function(user){
                this.users.push(user);
                this.toast("added");
            }
        },
        created: function () {
            EventBus.$on('add-user', this.addUser);
        }
            
    }

</script>

<style scoped> 
.users-list{
    width: 20%;
    height: 100%;
    box-shadow: 0 0 8px 0 rgba(0, 0, 0, 0.09);
    border-right: solid 1px #e6e9f2;


}
h2{
    height: 50px;
    border-bottom: solid 1px #e6e9f2;
}
@media only screen and (max-width: 1023px) {
  .users-list {
    width: 100%;
    height: auto;
  }
  
}
</style>