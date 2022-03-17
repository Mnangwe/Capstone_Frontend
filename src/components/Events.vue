<template>
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
               <div class="card card-2 p-3">
                   <div class="food-head row py-3 px-4">
                       <div class="col-12"></div>
                       <div class="intro col-12">
                           <p class="text-start py-2"><span class="iconify mx-2" data-icon="eva:search-fill"></span>search your food...</p>
                       </div>
                   </div>
                  
                   <div class="card-body">
                       
                     <div class="delivery-scooter">
                         <img src="https://i.postimg.cc/yNFsmf1c/delivery-2-removebg-preview.png" width="120" height="120" alt="">
                     </div>
                    <div class="row my-4">
                        <div class="display-category">
                            <h4 class="intro-text text-start my-2">Categories</h4>
                        </div>
                        <div class="category-display row">
                            <div class="catergory-1 category bg-dark mx-3">
                                <p class="icon"><span class="iconify" data-icon="emojione:french-fries"></span></p><p class="text-white"> Fries</p>
                            </div>
                            <div class="catergory-1 category">
                                <p class="icon"><span class="iconify" data-icon="emojione:french-fries"></span></p><p class="text-white"> Fries</p>
                            </div>
                            
                        </div>
                    </div>
                     <div class="row">
                         <div class="display-products">
                            <h4 class="intro-text text-start">Popular Now</h4>
                            <p class="all">View All <span class="iconify mx-2" data-icon="bi:arrow-up-right-circle-fill"></span></p>
                         </div>
                         <div class="burger-display">
                           <img src="https://i.postimg.cc/Jn8pmgmT/burger-1-removebg-preview.png" width="100" height="70" alt="">
                           <div class="burger-body">
                               <h5 class="title">Beef Burger</h5>
                               <p class="desc text-secondary">Cheese Mozarella</p>
                               <p class="price"><span class="rand">R</span><span class="money">40.00</span></p>
                           </div>
                         </div>
                         <div class="burger-display">
                           <img src="https://i.postimg.cc/Jn8pmgmT/burger-1-removebg-preview.png" width="100" height="70" alt="">
                           <div class="burger-body">
                               <h5 class="title">Beef Burger</h5>
                               <p class="desc text-secondary">Cheese Mozarella</p>
                               <p class="price"><span class="rand">R</span><span class="money">40.00</span></p>
                           </div>
                         </div>
                     </div>

                     <!-- <div class="row landing-food">

                     </div> -->
                     <div class="row my-5">
                         <div class="icons-events">
                             <div class="mobile">
                                 <span class="iconify" data-icon="clarity:bell-outline-badged"></span>
                             </div>
                             <div class="mobile">
                                 <span class="iconify" data-icon="emojione:red-heart"></span>
                             </div>
                             <div class="search">
                                 <span class="iconify text-white" data-icon="bytesize:search"></span>
                             </div>
                             <div class="mobile">
                                 <span class="iconify" data-icon="bi:cart4"></span>
                             </div>
                             <div class="mobile cart">
                                 <span class="iconify" data-icon="simple-icons:carto"></span>
                             </div>
                         </div>
                     </div>
                     
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
export default {

}
</script>

<style scoped>

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
   .card-wrapper > .card {
     border-radius: 30px;
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
   .location .intro {
       display: flex;
       justify-content: space-around;
       height: 4vmin;
       padding: 2px;
   }
   .display-products {
       display: flex;
       justify-content: space-between;
   }
 
   .burger-display {
       box-shadow: rgba(0, 0, 0, 0.05) 0px 2px 7px 0px;
       width: 50%;
   }
   .burger-display .price .rand{
       font-weight: bold;
       color: rgb(255, 123, 0);
       padding: 5px;
   }
   .burger-display .price .money {
       font-size: 20px;
       font-weight: bold;
       color: #222;
   }
   .burger-body .desc {
       font-size: 14px;
   }
   .burger-body .title {
       color: #222;
   }
   .burger-body p, .burger-body h5 {
       margin: 0;
   }
   .heading-display {
       display: flex;
       justify-content: space-around;
   }
   .all {
       text-decoration: none;
       color: rgb(255, 123, 0);
       padding-top: 4px;
   }
   .category-display .category {
       width: 50%;
       display: flex;
       justify-content: space-around;
       padding-top: 10px;
   }

   .category-display .category  {
       font-size: 20px;
       background: red;
       width: 40%;
   }
   .category-display .category  {
       border-radius: 25px;

       background: white;
   }
   .category-display .category p.icon {
       background: white;
       border-radius: 50%;
       width: 35%;
       height: 75%;
   }
   p.icon span {
       transform: scale(1.5);
   }
   .icons-events {
       display: flex;
       justify-content: space-around;
       align-items: flex-end;
   }
   .icons-events .iconify {
       transform: scale(1.7);
   }
   .icons-events .search {
       transform: scale(1.5);
       background: red;
       border-radius: 50%;
       width: 4vmin;
       height: 4vmin;
       padding-top: 2.7%;
       padding-left: 1.25%;
   }
   .icons-events .cart {
       transform: scale(2);
   }
   .landing-food {
       margin-bottom: 40%;
   }
   .food-head {
       display: flex;
       justify-content: flex-start;
       align-items: flex-end;
   }
   .intro p {
    background: #eee;
    border-radius: 10px;
    color: #888;
    width: 100%;
   }
   .intro p .iconify {
       transform: scale(1.8);
   }
</style>