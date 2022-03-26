<template>
  <Navbar/>
  <section class="profile">
    <div class="container">
      <div class="user-profile">
         <div class="card" style="">
          <img :src="user.cover" class="card-img-top" alt="...">
          <div class="card-body-main">
              
              <img :src="user.profile" class="card-img-top" alt="...">
              <div class="card-body">
                <h5 class="card-title">{{user.username}}</h5>
                <h5 class="card-title">{{user.email}}</h5>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                <a href="#" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#staticBackdrop">Edit Profile</a>
              </div>
          
          </div>
        </div>
      </div>
    </div>
    <EditProfile/>
  </section>
  
  
</template>

<script>
import Navbar from "@/components/Navbar"
import EditProfile from "@/components/EditUser"
export default {
    components: { Navbar, EditProfile},
    data(){
      return {
        user: JSON.parse(localStorage.getItem("user"))
      }
    },
    mounted(){
      console.log(this.user)
    }
}
</script>

<style scoped>
  .card-body-main {
    text-align: left;
  }
  .card-body-main img {
    width: 200px;
    height: 200px;
    object-fit: cover;
    border: 2px solid white;
    border-radius: 50%;
    position: relative;
    top: -120px;
    left: 2%;
  }
  .card-body-main .card-body {
    position: relative;
    top: -120px;
    left: 2%;
  }
  .card-body-main .card-body .card-title {
    font-weight: bold;
  }
</style>