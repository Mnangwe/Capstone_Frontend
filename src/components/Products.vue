<template>
  <section class="awesome-table">
        <table>
            <thead>
                <tr>
                    <th v-for="(obj, index) in config" :key="index">
                        {{ obj.title }}
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(row, index) in theData" :key="index">
                    <td v-for="(obj, ind) in config" :key="ind">
                        <span v-if="obj.type === 'text'">{{row[obj.key]}}</span>
                        <span v-if="obj.type === 'date'">{{new Date(row[obj.key]).toLocaleDateString()}} </span>
                        <figure v-if="obj.type === 'image'">
                            <img :src="row[obj.key]" height="60px">
                        </figure>
                        <div class="card-buttons">
                            <button v-if="obj.type === 'image'" type="submit" class="btn btn-primary">Edit Roles</button>
                            <button v-if="obj.type === 'image'" type="button" class="btn btn-primary" @click="deleteProduct(row._id)">Delete</button>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
    </section>
</template>

<script>
export default {
    props: ['theData', 'config'],
    methods: {
        deleteProduct(id){
          if(localStorage.getItem("jwt")){
            let confirmation = confirm(
            `Are you sure you want to remove this user from the list?`
            );

            if (confirmation) {
              fetch(`https://capstone-estratweni.herokuapp.com/products/${id}`, {
                method: "DELETE",
                headers: {
                  "Content-type": "application/json; charset=UTF-8",
                  Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                }
            }).then(res => res.json())
              .then(async data => {
                await console.log(data)
                await console.log(data.msg)
                location.reload()
              }).catch((err) => {
                alert(err);
            }
              
          }
        },
        editProduct(id){
          if(localStorage.getItem("jwt")){
            const product = this.products.find(product => product._id === id)
            console.log(product)
            if(product.name || product.categories || product.desc || product.price){
                fetch(`https://capstone-estratweni.herokuapp.com/products/${id}/role`, {
                method: "PUT",
                body: JSON.stringify({
                    name: product.name,
                    categories: product.categories,
                    desc: product.desc,
                    price: product.price
                }),
                headers: {
                    "Content-type": "application/json; charset=UTF-8",
                    Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                }
                }).then(res => res.json())
                .then(data => {
                    console.log(data)
                    alert("Your successfully edited")
                }).catch((err) => {
                alert(err);
            }
          }
        }
    },
    
}
</script>

<style scoped>

</style>