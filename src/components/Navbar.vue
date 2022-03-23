<template>
     <div class="nav-home ">
       <div class="marketing">
         <div class="container">
           <div class="advert">
             <p>Our Kasi Favourit Spot Don't Miss Out</p>
           </div>
         </div>
       </div>
       <header class="bg-dark">
         <h3>
         Welcome to e-Stratweni Mobile Foods
       </h3>
        <nav id="nav"  :class="{ active: isActive }">
        <!-- <router-link @click="toggleNav" to="/">Home</router-link> -->
        <!-- <router-link @click="toggleNav" to="/about">About</router-link> -->

        <router-link @click="toggleNav" :to="{ name: 'Products' }">Products</router-link>
        
        <router-link @click="toggleNav" :to="{ name: 'Cart' }">Cart</router-link>
        <router-link @click="toggleNav" :to="{ name: 'AdminDashboard' }"
        >Admin</router-link
        >
        <router-link @click="logout" class="logout" :to="{ name: 'Home' }"
        >Log out</router-link
        >
        </nav>
        <button id="nav-btn" @click="toggleNav">
            <i className="fas fa-bars"></i>
        </button>
       </header>
       
    </div>
</template>

<script>
export default {
    data() {
    return {
      isActive: false,
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
  color: black;
}
header {
  width: 100%;
}
.nav h2, .nav nav {
  text-align: left;
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