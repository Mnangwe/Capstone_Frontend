<template>
  <Navbar/>

  <section class="profile">
    <div class="container">
      <div class="user-profile" v-if="user">
         <div class="card" style="">
           <EditProfile :user="user"/>
          <img :src="user.cover" class="card-img-top" alt="...">
          <div class="card-body-main">
              <img :src="user.profile" class="card-img-top" alt="...">
              <div class="card-body">
                <a class="remove-user" @click="deleteProfile(user._id)"><span class="iconify" data-icon="bi:trash"></span></a>
                <h5 class="card-title">{{user.username}}</h5>
                <h5 class="card-title">{{user.email}}</h5>
                <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                <a href="#" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#editProfile">Edit Profile</a>
              </div>
          
          </div>
        </div>
      </div>
      <div class="profile" v-else>
          <Loader />
      </div>
    </div>
    
  </section>
  
  
</template>

<script>
import Navbar from "@/components/Navbar"
import EditProfile from "@/components/EditUser"
import Loader from "@/components/Loader"
export default {
    components: { Navbar, EditProfile, Loader, },
    data(){
      return {
        user:JSON.parse(localStorage.getItem("user"))
      }
    },
    methods: {
      deleteProfile(id){
        if(localStorage.getItem("jwt")){
            let confirmation = confirm(
            `Are you sure you want to remove your account`
            );

            if (confirmation) {
              fetch(`https://capstone-estratweni.herokuapp.com/users/${id}`, {
                method: "DELETE",
                headers: {
                  "Content-type": "application/json; charset=UTF-8",
                  Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                }
            }).then(res => res.json())
              .then(async data => {
                await console.log(data)
                await alert(data.msg)
                await localStorage.clear();
                    alert("Goodbye! See you soon")
                    this.$router.push({ name: "Home" });
              })
            }
        
      
    
              
          }
      }
    },
    mounted(){
      if (localStorage.getItem("jwt")) {
        if(localStorage.getItem("user")){
          this.user = JSON.parse(localStorage.getItem("user"))
          console.log(this.user)
        }else if(localStorage.getItem("newUser")){
          this.user = JSON.parse(localStorage.getItem("newUser"))
          console.log(this.user)
        }
      }
    
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
  a.remove-user {
    font-size: 30px;
    cursor: pointer;
    position: relative;
    right: 0;
  }
</style>