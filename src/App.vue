<template>
  <div id="app">
    <SideBar/>
    <UsersList/>
    <UserForm/>
    <div class="recent">
      <RecentUsers/>
      <RecentPhotos/>
    </div>
  </div>
</template>

<script>
import SideBar from './components/SideBar'
import UsersList from './components/UsersList'
import UserForm from './components/UserForm'
import RecentUsers from './components/RecentUsers'
import RecentPhotos from './components/RecentPhotos'
export default {
  name: 'App',
  components: {
    UsersList,
    SideBar,
    UserForm,
    RecentUsers,
    RecentPhotos
  }
}
</script>

<style>
body{
  margin: 0;
  font-family: 'Open Sans', sans-serif;
}
#app {
  display: flex;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
}

.flex-center{
  display: flex;
  justify-content: center;
  align-items: center;
}
h2{
  font-size: 1rem;
  font-weight: bold;
  text-align: left;
  color: #131b3c;
  margin-bottom: 0;

}
.recent{
  width: 20%;
  background-color: #f5f7fa;
  border-left: 1px solid #e6e9f2;
}
p{
  margin-bottom:0;
}
input{
    max-height: 34px;
    border-radius: 5px !important;
    box-shadow: 0 1px 6px 0 rgba(0, 0, 0, 0.1);
    border: solid 1px #e6e9f2;
    padding: 12px;
    font-size:12px;
    width: 100%;
}

@media only screen and (max-width: 1023px) {
  #app {
    flex-direction: column;
    height: auto;
  }
  .recent{
    width:100%;
  }
  
}
</style>
