<template>
  <Navbar />
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
            <button class="btn btn-secondary call-action" type="button">
              Book Now
            </button>
          </div>
        </div>
      </div>

    </div>
  </section>

  <section class="display-events">
    <div class="container">
      <div class="timeline-events">
        <!-- First Event -->
        <div class="event-1">
          <div class="container">
            <div class="card-wrapper">
                <div class="card card-1">
                  <div class="card-image">
                     <img src="https://i.postimg.cc/G2Lb345W/delivery-removebg-preview.png" class="card-img-top" alt="...">
                  </div>
                  <div class="circular-shape"></div>
                 <div class="card-body-1">
                    <h3 class="card-title text-center">The Fast Dilivery <span class="card-1">Foods</span></h3>
                    <p class="card-text">Our number one Job is to make sure we fill your tummy with our delicious food. Catch it while it still hot</p>
                    <a href="#" class="btn delivery rounded-pill px-5 my-2">Get Started</a>
                  </div>
                </div>
            </div>
          </div>
        </div>
        <!-- Secont Event -->
        <div class="event-2">
          <div class="container">
            <div class="card-wrapper">
              <div class="card">
                  <img src="" class="card-img-top" alt="...">
                  <div class="card-body">
                    <h5 class="card-title">Card title</h5>
                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                    <a href="#" class="btn btn-primary">Go somewhere</a>
                  </div>
                </div>
            </div>
          </div>
        </div>
        <!-- Third Event -->
        <div class="event-3"> 
          <div class="container">
            <div class="card-wrapper">
              <div class="card">
                  <img src="" class="card-img-top" alt="...">
                  <div class="card-body">
                    <h5 class="card-title">Card title</h5>
                    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
                    <a href="#" class="btn btn-primary">Go somewhere</a>
                  </div>
                </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
// @ is an alias to /src
import Navbar from '@/components/Navbar.vue'

export default {
  name: 'Home',
  components: {
    Navbar
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

   /* The Second Section */

  section.display-events {
    height: 100vh;
    background: #eee;
  }

  .event-1, .event-3 {
    padding-top: 5%;
    flex: 1;
    display: flex;
    justify-content: center;
  }

  .event-2 {
    padding-top: 12%;
    flex: 1;
  }
  .timeline-events {
    display: flex;
    text-align: center;
    justify-content: space-around;
  }
  .display-events .card {
    border-radius: 20px;
    height: 80vh;
  }
  .card-image {
    background-color:rgb(247, 224, 194);
    height: 60%;
    border-radius: 20px 20px 0 0;
  }
  .card-image img{
    height: 100%;
    object-fit: cover;
    transform: scale(0.95);
  }
  .circular-shape {
    height: 10%;
    width: 100%;
    border-radius: 50%;
    top: -5%;
    background: #fff;
    position: relative;
    margin: 0;
    padding: 0;
  }
  .card-body-1 .card-title{
    font-weight: bold;
    /* position: relative;
    top: -20%;
    border: 1px solid black; 
    border-radius: 50% 50% 20px 20px;
    height: 40%;
    background: #fff; */
  }
  .card-body-1 {
    padding: 0 10% 10% 10%;
    text-align: center;
  }
  span.card-1 {
    font-weight: bold;
    color: rgb(247, 98, 14);
  }
  .delivery {
    background-color: rgb(247, 98, 14);
    color: #eee;
    font-weight: bold;
    
  }
</style>