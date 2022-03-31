<template>
  <div class="modal fade" id="LogIn" tabindex="-1" aria-labelledby="LogInLabel" aria-hidden="true">
        <div class="modal-dialog" style="border-radius: 2rem; width: 42% !important;">
          <div class="modal-content card">
            <div class="modal-header">
              <button type="button" class="btn-close text-white" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <!-- CONTENT -->
            <form @submit.prevent="login" class="modal-body">
              <h2 class="fw-bold mb-2 text-uppercase">Login</h2>
              <img src="https://i.postimg.cc/VkJLXBdR/logo-2-removebg-preview.png" class="logo-img" alt="">
              <p class="text-secondary mb-5">Please enter your login and password!</p>
              
              <div class="form-outline form-white mb-4">
                <input required type="email" v-model="email" id="typeEmailX" class="form-control form-control-lg" placeholder="Email"/>
              </div>

              <div class="form-outline form-white mb-4">
                <input required type="password" v-model="password" id="typePasswordX" class="form-control form-control-lg" placeholder="Password"/>
              </div>

              <p class="small mb-5 pb-lg-2"><a class="text-white-50" href="#!">Forgot password?</a></p>

              <button class="btn login btn-lg rounded-pill px-5" data-bs-dismiss="modal" type="submit">Login</button>

              <div class="d-flex justify-content-center text-center mt-4 pt-1">
                <a href="#!" class="text-white"><i class="fab fa-facebook-f fa-lg"></i></a>
                <a href="#!" class="text-white"><i class="fab fa-twitter fa-lg mx-4 px-2"></i></a>
                <a href="#!" class="text-white"><i class="fab fa-google fa-lg"></i></a>
              </div>

            </form>

            <div>
              <p class="mb-5">Don't have an account? <a href="#!" class="text-secondary fw-bold" type="button" data-bs-toggle="modal" data-bs-target="#SignUp" data-bs-dismiss="modal" aria-label="Close">Sign Up</a></p>
            </div>
          </div>
        </div>
      </div>
</template>

<script>
export default {
     data() {
    return {
      email: "",
      password: "",
    //   username:"",
      isActive: false,
    };
  },
  methods: {
    toggleNav() {
      this.isActive = !this.isActive;
    },
    login() {
      fetch("https://capstone-estratweni.herokuapp.com/users/login", {
        method: "POST",
        body: JSON.stringify({
          email: this.email,
          password: this.password,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then(async (json) => {
          await localStorage.setItem("jwt", json.jwt);
          await localStorage.setItem("user", JSON.stringify(json.user));
          await localStorage.setItem("password", JSON.stringify(this.password));
          alert("User logged in");
          const user = await  JSON.parse(localStorage.getItem("user"))
          console.log(json.jwt)
          
          if(user.isAdmin) return await this.$router.push({ name: 'AdminDashboard' })
          else return await this.$router.push({ name: "Products" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  }
}
</script>

<style>

</style>