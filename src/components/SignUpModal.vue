<template>
  <div class="modal fade" id="SignUp" tabindex="-1" aria-labelledby="SignUpLabel" aria-hidden="true">
      <div class="modal-dialog sign-up">
        <div class="modal-content sign-up">
          <!-- <div class="modal-header">
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div> -->
          <div class="modal-body">
            <div class="row">
              <div class="col-sm-6 form-image text-center">
                <!-- <img src="https://i.postimg.cc/SKdrfZp5/estratweni-removebg-preview.png" width="400" alt=""> -->
              </div>
              <div class="col-sm-6">
                <form action="" @submit.prevent="register">
                  <h3 class="text-start my-5">Sign up</h3>

                  <div class="form-outline form-white mb-4">
                    <input required type="text" class="form-control form-control-lg" v-model="username" placeholder="username"/>
                  </div>

                  <div class="form-outline form-white mb-4">
                    <input required type="email"  class="form-control form-control-lg" v-model="email" placeholder="Email"/>
                  </div>

                  <div class="form-outline form-white mb-4">
                    <input required type="password"  class="form-control form-control-lg" v-model="password" placeholder="Password"/>
                  </div>

                  <button type="submit" class="btn btn-primary text-end" data-bs-dismiss="modal">Sign Up</button>
                </form>
                
              </div>
            </div>
          </div>
          
            <!-- <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary">Sign Up</button> -->
         
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
      username:"",
      isActive: false,
    };
  },
  methods: {
    toggleNav() {
      this.isActive = !this.isActive;
    },
      register() {
      fetch("https://capstone-estratweni.herokuapp.com/users", {
        method: "POST",
        body: JSON.stringify({
          username: this.username,
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
          await localStorage.setItem("user", JSON.stringify(json.newUser));
          alert("Welcome to eStratweni family");
          const user = await  JSON.parse(localStorage.getItem("user"))
          console.log(json.jwt)         
          return await this.$router.push({ name: "Products" });
        })
        .catch((err) => {
          alert(err);
        });
    },
  },
}
</script>

<style>

</style>