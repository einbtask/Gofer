<template>
   <main class='d-flex flex-column position-relative align-items-center'>
       <header class="d-flex justify-content-center">
           <component v-on:remove-toast="removeToast" :is="status" :action="action" class="position-absolute toast"/>
           <img class="img-fluid" src="../assets/gofer-logo.png" alt="gofer logo">
       </header>
       <div class="main-form">
           <section>
                <h2>User details</h2>
                <div class="d-flex justify-content-between mt-3">
                    <input v-model="first_name" placeholder="First Name" class="w-47" type="text">
                    <input v-model="last_name" placeholder="Last Name" class="w-47" type="text">
                </div>
                <div class="d-flex justify-content-between mt-3">
                    <Datepicker class="date w-47" v-model="selected_date" @selected="customDate" format="d.M.yyyy" placeholder="Birth Date"/>
                    <input  v-model="phone" placeholder="Phone Number" class="w-47" type="number">
                </div>
                <input v-model="email" placeholder="Email Address" class="w-100 mt-3" type="text">
           </section>
           <section class="mt-4">
               <h2>Account details</h2>
               <div class="d-flex justify-content-between">
                    <div class="w-70">
                        <input class="mt-3" v-model="username" placeholder="User Name" type="text">
                        <input class="mt-3" v-model="password" placeholder="Password" type="text">
                        <input class="mt-3" v-model="repeatedPassword" placeholder="Repeat Password" type="text">
                    </div>
                    <div class="file-container mt-3 w-25"> 
                    <input class="file-upload" type="file" @change="onFileSelected">
                    <label for="file"><span class="font-weight-bold">+ </span>Add Photo</label>
                    <img class="user-file" :src="img" alt="user image upload">
                    </div>
               </div>
           </section>
           <div class="buttons text-right mt-5">
               <button class="add" @click="createUser">Add</button>
               <button @click="clearForm">Clear</button>
           </div>
       </div>
      
    </main>
</template>

<script>
import Toast from './Toast'
import { EventBus } from '../event-bus.js';
import Datepicker from 'vuejs-datepicker';

export default {
      data(){
          return{
              first_name: "",
              last_name: "",
              bday: "",
              selected_date: null,
              phone: "",
              email:"",
              username:"",
              password:"",
              repeatedPassword:"",
              img: "../../static/file.png",
              selectedFile: null,
              status: "",
              action:""
          }
      },
      components:{Toast,
                  Datepicker
      },
      methods:{
        clearForm: function() {
            this.first_name = "",
            this.last_name = "",
            this.bday = "",
            this.phone = "",
            this.email = "",
            this.username = "",
            this.password = "",
            this.repeatedPassword = "",
            this.img =  "../../static/file.png",
            this.selectedFile = null,
            this.selected_date =  null
              
        },
        createUser: function() {
              let newUser = {first_name: this.first_name, last_name: this.last_name, bday: this.bday, phone: this.phone, email: this.email, username: this.username, password: this.password, img: this.img};
              EventBus.$emit('add-user', newUser);
              this.clearForm();
        },
        onFileSelected: function(event){
              let file = event.target.files[0]
              const reader  = new FileReader();
              reader.onload = e => this.img = e.target.result;
              reader.readAsDataURL(file);
        },
        showToast: function(action){
            this.status = Toast;
            this.action = action;
        },
        removeToast: function(){
            console.log("tremove");
            this.status = "";
            this.action = "";
        },
        customDate: function(date){
            let day = date.getDate();
            let monthIndex = date.getMonth();
            let year = date.getFullYear();
            monthIndex++
            this.bday = day + "." + monthIndex + "." + year;
        }
    },
    created: function () {
        EventBus.$on('show-toast', this.showToast);
    }
}


</script>

<style scoped>
main{
    width: 60%;
    background-color: #f5f7fa;
}
header{
    margin-top: 5rem;
}
.main-form{
    padding: 0 7rem;
    margin-top: 5rem;
    max-width: 900px;
}
button{
    width: 94px;
    height: 30px;
    border-radius: 4px;
    background-color: #ff5575;
    color: white;
}
.add{
    background-color: #5891e2;
}

.date {
    display: inline-block;
}

.toast{
    top:30px;
    right:30px;
}

.w-47{
    width:47%;
}
.w-70{
    width:70%;
}
.file-upload{
	opacity: 0;
	
}

label {
    color: #9ba0b2;
    display: inline-block;
    position: absolute;
    top:0;
    left:0;
    pointer-events: none;
    font-size: 12px;
    width: 100%;
    padding-top: 5px;
}
.file-container{
    background: white;
    height: auto;
    position: relative;
    box-shadow: 0 1px 6px 0 rgba(0, 0, 0, 0.1);
    border: solid 1px #e6e9f2;
    max-width: 130px;
}
.user-file{
    position: absolute;
    bottom:0;
    left:15%;
    width: 75%;
    max-height: 100px;
    max-width: 90px;
}
@media only screen and (max-width: 1023px) {
  main {
    width: 100%;
    height: auto;
  }
  
}
@media only screen and (max-width: 500px) {
  .main-form {
    padding: 0 1rem;
  }
  
}

</style>