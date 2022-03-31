<template>
  <section>


<!-- Modal -->
<div class="modal fade" id="editProduct" tabindex="-1" aria-labelledby="editProductLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="editProductLabel">Modal title</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
          <form action="" @submit.prevent="editProduct">
            <input type="text" v-model="name" placeholder="name of a product">
            <input type="text" v-model="price" placeholder="price">
            <input type="text" v-model="image" placeholder="image of a product">
            <input type="text" v-model="desc" placeholder="description">
            <div class="modal-footer">
              <!-- <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button> -->
              <button type="submit" class="btn btn-primary" data-bs-dismiss="modal">Save changes</button>
            </div>
          </form>
      </div>
      
    </div>
  </div>
</div>

    
  </section>

  
</template>

<script>
export default {
  props: ['product'],
  data(){
    return{
      name:this.product.name,
      tempCategories: '',
      categories:this.product.categories,
      desc: this.product.desc,
      price: this.product.price,
      image: this.product.image
    }
  },
  methods: {
    editCategories(e){
      if(e.key === "," && this.tempCategories){
        this.categories.push(this.tempCategories)
        console.log(this.categories)
        this.tempCategories = ''
        
      }
    },
    editProduct(){
      if(localStorage.getItem("jwt")){
            console.log("We are here")
            if(this.name || this.categories || this.desc || this.price || this.image){
                fetch(`https://capstone-estratweni.herokuapp.com/products/${this.product._id}`, {
                  method: "PUT",
                  body: JSON.stringify({
                    name: this.name,
                    categories: this.categories,
                    desc: this.desc,
                    price: parseInt(this.price),
                    image: this.image
                  }),
                  headers: {
                    "Content-type": "application/json; charset=UTF-8",
                    Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                  }
                }).then(res => res.json())
                  .then(data => {
                    console.log(data)
                    alert(data.msg)
                    location.reload()
                })


            }    
      }
    }
  },
  mounted(){
    console.log(this.product)
  }
}
</script>

<style>

</style>