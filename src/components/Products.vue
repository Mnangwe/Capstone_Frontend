<template>
  <section class="awesome-table">
        <table>
            <thead>
                <tr>
                    <th v-for="(obj, index) in configProduct" :key="index">
                        {{ obj.title }}
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(row, index) in theData" :key="index">
                    <td v-for="(obj, ind) in configProduct" :key="ind">
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
    props: ['theData', 'configProduct'],
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
                })
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
                    price: parseInt(product.price)
                }),
                headers: {
                    "Content-type": "application/json; charset=UTF-8",
                    Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                }
                }).then(res => res.json())
                .then(data => {
                    console.log(data)
                    alert("Your successfully edited")
                })
            }
          }
        }
    },
    
}
</script>

<style scoped>
    figure img {
        height: 60px;
        width: 60px;
        border: 1px solid #bbb;
        border-radius: 50%;
        overflow: hidden;
    }
    .awesome-table {
    border: 1px solid #999;
    border-radius: 4px;
    color: #333;
    overflow: auto;
    margin-top: 30px;
    }
    figure {
        margin-block-start: 0;
        margin-block-end: 0;
        margin-inline-start: 0;
        margin-inline-end: 0;
    }
    table {
        border-collapse: collapse;
        width: 100%;
    }
    table th {
        position: sticky;
        top: 0;
        background: #aaa;
        padding: 10px 5px;
        text-align: left;
        border-bottom: 1px solid #999;
    }
    table td {
        padding: 5px 5px;
        text-align: left;
    }
    table td:nth-child(3){
        width: 45%;
        margin-right: 5px;
    }
    table td:nth-child(4){
        font-weight: bold;
    }
    table td:nth-child(2){
        font-weight: bold;
    }
</style>