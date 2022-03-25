<template>
     <div class="nav-home ">
       <div class="marketing">
         <div class="container">
           <div class="advert">
             <marquee behavior="" width="100%" direction="">Our Kasi Favourit Spot Don't Miss Out. Zwakala Estratweni</marquee>
           </div>
         </div>
       </div>
       <header class="">
          <h3>
          Welcome to e-Stratweni Mobile Foods
          </h3>
          <nav class="navbar navbar-expand-lg" id="nav"  :class="{ active: isActive }">
            <div class="container-fluid">
              <a class="navbar-brand" href="#"><img src="https://i.postimg.cc/VkJLXBdR/logo-2-removebg-preview.png" width="60" height="60" alt=""></a>
              <button class="navbar-toggler  text-dark" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavDropdown" aria-controls="navbarNavDropdown" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
              </button>
              <div class="collapse navbar-collapse" id="navbarNavDropdown">
                <ul class="navbar-nav">
                  <li class="nav-item">          
                    <router-link class="nav-link active" aria-current="page" @click="toggleNav" :to="{ name: 'Products' }">Products</router-link>
                  </li>
                  <li class="nav-item">          
                    <router-link class="nav-link" @click="toggleNav" :to="{ name: 'Cart' }">Cart</router-link>
                  </li>
                  <li class="nav-item">        
                    <router-link class="nav-link" @click="toggleNav" v-if="user.isAdmin" :to="{ name: 'AdminDashboard' }">Admin</router-link>
                  </li>
                  <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle" href="#" id="navbarDropdownMenuLink" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                      Me 
                    </a>
                    <ul class="dropdown-menu" aria-labelledby="navbarDropdownMenuLink">
                      <li>
                        <router-link class="dropdown-item" :to="{ name: 'Profile' }">Profile</router-link>
                      </li>
                      <li>
                        <router-link class="dropdown-item" @click="logout" :to="{ name: 'Home' }">Log out</router-link>
                      </li>
                    </ul>
                  </li>
                </ul>
              </div>
            </div>
          </nav>
       </header> 
    </div>
</template>

<script>
export default {
    data() {
    return {
      isActive: false,
      user: JSON.parse(localStorage.getItem("user"))
    };
  },
  methods: {
    toggleNav() {
      this.isActive = !this.isActive;
    },
    logout() {
      localStorage.clear();
      alert("Goodbye! See you soon")
      this.toggleNav;
    },
  },
}
</script>

<style>
.nav-home {
  background: whitesmoke;
  padding-top: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
  margin-bottom: 5px;
  color: white;
  background: linear-gradient(95deg,#F39848 15%, #EF8256 45%, #CBA17D 75%, #fb5343 100% ) 95%/200% 100%;
}
header h3 {
  color: #2c3e50; 
}
header {
  width: 100%;
  background: #fff;
}
.nav h2, .nav nav {
  text-align: left;
}
.marketing {
  font-weight: bolder;
}
.collapse {
justify-content: center;
}
.navbar-brand {
  position: relative;
  left: 20%;
}
#nav-btn {
  position: fixed;
  top: 20px;
  right: 20px;
  background: #f5f5f5;
  box-shadow: 8px 8px 15px #e4e4e4, -8px -8px 15px #ffffff;
  padding: 20px;
  border-radius: 50%;
  border: none;
  outline: none;
  display: none;
}
@media screen and (max-width:992px) {
  .navbar-brand {
    display: none;
  }
}
@media screen and (max-width: 500px) {
  #nav {
    height: 100%;
    left: -100vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: left 0.1s linear;
  }
  #nav.active {
    left: 0;
  }
  #nav-btn {
    display: block;
  }
}
</style>