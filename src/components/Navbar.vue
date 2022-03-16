<template>
  <header class="home">
    <div class="container">
      <nav class="navbar">
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
    </div>
    
      <!-- Log-In Modal -->
      <div class="modal fade" id="LogIn" tabindex="-1" aria-labelledby="LogInLabel" aria-hidden="true">
        <div class="modal-dialog" style="border-radius: 2rem; width: 42% !important;">
          <div class="modal-content card">
            <div class="modal-header">
              <button type="button" class="btn-close text-white" data-bs-dismiss="modal" aria-label="Close"></button>
            </div>
            <!-- CONTENT -->
            <div class="modal-body">

              
              <h2 class="fw-bold mb-2 text-uppercase">Login</h2>
              <img src="https://i.postimg.cc/VkJLXBdR/logo-2-removebg-preview.png" class="logo-img" alt="">
              <p class="text-secondary mb-5">Please enter your login and password!</p>
              
              <div class="form-outline form-white mb-4">
                <input type="email" id="typeEmailX" class="form-control form-control-lg" placeholder="Email"/>
              </div>

              <div class="form-outline form-white mb-4">
                <input type="password" id="typePasswordX" class="form-control form-control-lg" placeholder="Password"/>
              </div>

              <p class="small mb-5 pb-lg-2"><a class="text-white-50" href="#!">Forgot password?</a></p>

              <button class="btn login btn-lg rounded-pill px-5" data-bs-dismiss="modal" type="submit">Login</button>

              <div class="d-flex justify-content-center text-center mt-4 pt-1">
                <a href="#!" class="text-white"><i class="fab fa-facebook-f fa-lg"></i></a>
                <a href="#!" class="text-white"><i class="fab fa-twitter fa-lg mx-4 px-2"></i></a>
                <a href="#!" class="text-white"><i class="fab fa-google fa-lg"></i></a>
              </div>

            </div>

            <div>
              <p class="mb-5">Don't have an account? <a href="#!" class="text-secondary fw-bold" type="button" data-bs-toggle="modal" data-bs-target="#SignUp" data-bs-dismiss="modal" aria-label="Close">Sign Up</a></p>
            </div>
          </div>
        </div>
      </div>

    <!-- Sign-up Modal -->
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
                <form action="">
                  <h3 class="text-start my-5">Sign up</h3>

                  <div class="form-outline form-white mb-4">
                    <input type="text" class="form-control form-control-lg" placeholder="username"/>
                  </div>

                  <div class="form-outline form-white mb-4">
                    <input type="email"  class="form-control form-control-lg" placeholder="Email"/>
                  </div>

                  <div class="form-outline form-white mb-4">
                    <input type="password"  class="form-control form-control-lg" placeholder="Password"/>
                  </div>

                  <button type="button" class="btn btn-primary text-end" data-bs-dismiss="modal">Sign Up</button>
                </form>
                
              </div>
            </div>
          </div>
          
            <!-- <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
            <button type="button" class="btn btn-primary">Sign Up</button> -->
         
        </div>
      </div>
    </div>
  </header>
</template>

<script>
export default {

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
</style>