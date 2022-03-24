<template>
  <!-- <div class="hearder-wrap">
    <div class="row">
      <div class="col-sm-12 col-md-12">
        <a href="/">
          <img src="https://i.postimg.cc/ht7Vhpn1/logo-removebg-preview.png" width="250" height="250" alt="" srcset="">
        </a>
      </div>
    </div>
  </div>   -->
  <!-- <div id="nav" class="bg-black text-center">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div> -->
  <router-view/>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /* color: #2c3e50; */
  color: black;
  
}

#nav {
  /* padding: 30px; */
  height: 60px;
  display: flex;
  justify-content: center;
  align-items: center;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
  /* color: antiquewhite; */
}
#nav .dropdown-menu a {
  color: #2c3e50; 
}
#nav a.router-link-exact-active {
  /* color: #42b983; */
  color: blue;
}
#nav .dropdown-menu a.router-link-exact-active {
  /* color: #42b983; */
  color: black;
}
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

</style>
