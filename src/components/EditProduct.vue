<template>


<!-- Modal -->
<div class="modal fade" id="editProduct" tabindex="-1" aria-labelledby="editProductLabel" aria-hidden="true">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="editProductLabel">Edit Product</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <form @submit.prevent="editProduct" class="modal-body">
        <input v-model="name" type="text" placeholder="product name">
        <input v-model="tempCategories" type="text" placeholder="chicken, burger">
        <input v-model="desc" type="text" placeholder="description">
        <input v-model="price" type="text" placeholder="price">
        <input v-model="image" type="text" placeholder="https://www.image.jpeg.com">
        <button type="submit" class="btn btn-primary">Save changes</button>
      </form>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
        <button type="button" class="btn btn-primary">Save changes</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  props: ['theData'],
  data(){
    return{
      name:null,
      tempCategories: '',
      categories:[],
      desc: null,
      price: null,
      image: null
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
        if(this.name || this.categories || this.desc || this.price || this.image){
            const product = this.theData.find(product => product._id === id)
            console.log(product)
            fetch(`https://capstone-estratweni.herokuapp.com/products/${product._id}`, {
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
                })
          }
      }
    }
  }
}
</script>

<style>

</style>