<template>
  <NavHome />
  <section class="home-intro">
    <div class="container">
      <div class="intro">
        <div class="display-pic">
          <div class="image-intro">
          <img src="https://i.postimg.cc/Y002Rcrh/home-burger-removebg-preview.png" alt="">
          </div>
        </div>
        
        <div class="context-intro">
          <div class="welcome-note container">
            <h2 class="hero-title">Come e-Stratweni!</h2>
            <p class="hero-context text-secondary">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. A, quidem nostrum odit ut, voluptas dolorum assumenda vitae dignissimos in sequi beatae possimus. Quod, nihil? Tempora numquam, quisquam dignissimos recusandae magni impedit, officia voluptate nam magnam sed, facere repellendus. Vero, perferendis. Architecto deleniti tempore commodi pariatur, dicta consequatur culpa dolorum recusandae!
            </p>
            <button class="btn btn-secondary call-action" type="button" data-bs-toggle="modal" data-bs-target="#SignUp">
              Book Now
            </button>
          </div>
        </div>
      </div>

    </div>
  </section>
  <Login/>
  <Signup/>
  <Events/>
</template>

<script>
// @ is an alias to /src
import NavHome from '@/components/NavHome.vue'
import Events from '@/components/Events.vue'
import Login from '@/components/LoginModal.vue'
import Signup from '@/components/SignUpModal.vue'

export default {
  name: 'Home',
  components: {
    NavHome,
    Events,
    Login,
    Signup
  }
}
</script>

<style>
  section.home-intro {
    min-height: 90vh;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
  }
  .intro {
    display: flex;
    justify-content: space-around;
  }
  .display-pic {
    flex: 1;
    
  }
  .image-intro {
    box-shadow: rgba(149, 157, 165, 0.2) 0px 8px 24px;
    border-radius: 21% 79% 16% 84% / 83% 21% 79% 17%;
    height: 60vh;
    text-align: center;
  }
  .image-intro img {
    /* border-radius: 21% 79% 16% 84% / 83% 21% 79% 17%; */
    width: 100%;
    
    object-fit: cover;
  }
  .context-intro {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    
  }
  .welcome-note {
    text-align: left;
  }
  .hero-title {
    
  }
  .hero-context {
    font-size: 20px;
  }
  .call-action {
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  }

  
</style>