<template>
  <header class="home">
    <div class="container">
      <nav class="navbar" :class="{ active: isActive }">
        <div class="container-fluid">
          <div class="navbar-logo">
            <a href="">
              <img src="https://i.postimg.cc/SKdrfZp5/estratweni-removebg-preview.png" alt="">
            </a>
          </div>
          <div class="brand-name">
            <h2 id="brand-title">e-Stratweni Mobile Foods</h2>
          </div>
          <div class="action-links">
            <a type="button" class="" data-bs-toggle="modal" data-bs-target="#SignUp">Register</a><span class="mx-1">/</span> 
            <a type="button" class="" data-bs-toggle="modal" data-bs-target="#LogIn"> Login</a>
          </div>
        </div>
      </nav>
      <button id="nav-btn" @click="toggleNav">
            <i className="fas fa-bars"></i>
        </button>
    </div>
    
      <!-- Log-In Modal -->
      

    <!-- Sign-up Modal -->
    
  </header>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      username:"",
      isActive: false,
    };
  },
  // methods: {
  //   toggleNav() {
  //     this.isActive = !this.isActive;
  //   },
  //   login() {
  //     fetch("https://capstone-estratweni.herokuapp.com/users/login", {
  //       method: "POST",
  //       body: JSON.stringify({
  //         email: this.email,
  //         password: this.password,
  //       }),
  //       headers: {
  //         "Content-type": "application/json; charset=UTF-8",
  //       },
  //     })
  //       .then((response) => response.json())
  //       .then(async (json) => {
  //         await localStorage.setItem("jwt", json.jwt);
  //         await localStorage.setItem("user", JSON.stringify(json.user));
  //         alert("User logged in");
  //         const user = await  JSON.parse(localStorage.getItem("user"))
  //         console.log(json.jwt)
          
  //         if(user.isAdmin) return await this.$router.push({ name: 'AdminDashboard' })
  //         else return await this.$router.push({ name: "Products" });
  //       })
  //       .catch((err) => {
  //         alert(err);
  //       });
  //   },
  //   register() {
  //     fetch("https://capstone-estratweni.herokuapp.com/users/", {
  //       method: "POST",
  //       body: JSON.stringify({
  //         username: this.username,
  //         email: this.email,
  //         password: this.password,
  //       }),
  //       headers: {
  //         "Content-type": "application/json; charset=UTF-8",
  //       },
  //     })
  //       .then((response) => response.json())
  //       .then(async (json) => {
  //         await localStorage.setItem("jwt", json.jwt);
  //         await localStorage.setItem("user", JSON.stringify(json.user));
  //         alert("User logged in");
  //         const user = await  JSON.parse(localStorage.getItem("user"))
  //         console.log(json.jwt)
          
  //         if(user.isAdmin) return await this.$router.push({ name: 'AdminDashboard' })
  //         else return await this.$router.push({ name: "Products" });
  //       })
  //       .catch((err) => {
  //         alert(err);
  //       });
  //   },
  // },
}
</script>

<style>
header.home {
  box-shadow: rgba(0, 0, 0, 0.15) 1.95px 1.95px 2.6px;
}
nav {
  height: 75px;
  margin: 5px;
}
 nav .container-fluid {
   display: flex;
   justify-content: space-around;
 }
 .navbar-logo img {
   height: 66px ;
   border-radius: 50%;
  
 }
 .navbar-logo {
  flex: 1;
  display: flex;
  justify-content: flex-start;
 }

  .brand-name {
    flex: 1;
  }
  .action-links {
    flex: 1;
    display: flex;
    justify-content: flex-end;
  }
#brand-title {
  width: 400px;
}
  button.login {
    background-color: rgb(247, 98, 14);
    color: #eee;
    font-weight: bold;
  }
  img.logo-img {
    width: 200px;
    height: 200px;
    object-fit: cover;
  }
  .modal-dialog.sign-up, .modal-content.sign-up {
    width: 60vw !important;
  }
  .modal-dialog.sign-up {
    max-width: 100% !important;
  }
  .form-image {
    background: linear-gradient(0deg, rgba(0, 0, 0, 0.55), rgba(0, 0, 0, 0.7)), url("https://i.postimg.cc/SKdrfZp5/estratweni-removebg-preview.png") no-repeat 50%;
    object-fit: cover; 
    background-position: center center;
    background-size: cover;
  }
  #SignUp, #SignUp .modal-content {
    /* margin: 0; */
    padding: 0 !important;
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
  nav {
    height: 100%;
    left: -100vw;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    transition: left 0.1s linear;
  }
  nav.active {
    left: 0;
  }
  #nav-btn {
    display: block;
  }
}
</style>