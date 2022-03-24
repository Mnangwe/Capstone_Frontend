<template>
  <section class="details">
      <div class="container" v-if="product">
          <div class="details">
            <div class="row">
                <h2>{{product.name}}</h2>
            </div>
            <div class="row">
                <div class="card-wrapper">
                    <div class="card" style="width: 18rem;">
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
  </section>
</template>

<script>
export default {
    props: ["id"],
    data() {
        return {
        product: null,
        };
    },
    mounted() {
        if(this.id){
        fetch("https://capstone-estratweni.herokuapp.com/products/" + this.id, {
        method: "GET",
        headers: {
            "Content-type": "application/json; charset=UTF-8",
            Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
        })
        .then((response) => response.json())
        .then(async (json) => {
            this.product = json;
        })

        }
    }
}
</script>

<style>

</style>