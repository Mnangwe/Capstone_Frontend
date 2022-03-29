<template>
  <section>
    <h2>Editing Product</h2>
  </section>

  
</template>

<script>
export default {
  props: ['id'],
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
            console.log("We are here")
            fetch(`https://capstone-estratweni.herokuapp.com/products/${this.id}`, {
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
  },
  unpdated(){
    console.log(this.id)
  }
}
</script>

<style>

</style>