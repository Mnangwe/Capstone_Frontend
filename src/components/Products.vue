<template>
    
    <AddProduct/>
    <EditProduct v-for="(row, index) in theData" :key="index" :product="row"/>
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
                            <button v-if="obj.type === 'image'" type="submit" class="btn btn-primary btn-product" data-bs-toggle="modal" data-bs-target="#editProduct">Edit Product</button>
                            <button v-if="obj.type === 'image'" type="button" class="btn btn-danger" @click="deleteProduct(row._id)">Delete</button>
                        </div>
                        
                        
                    </td>
                </tr>
            </tbody>
        </table> 
    </section>
    
</template>

<script>
import AddProduct from "./AddProduct.vue"
import EditProduct from "./EditProduct.vue"
export default {
    
    components: { AddProduct, EditProduct },
    props: ['theData', 'configProduct'],
    data(){
        return{
            editing: false
        }
    },
    methods: {
        deleteProduct(id){
          if(localStorage.getItem("jwt")){
            let confirmation = confirm(
            `Are you sure you want to remove this product from the list?`
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
                    await alert(data.msg)
                    location.reload()
                })
                }
            
            }
        },
        editProduct(id){
            if(localStorage.getItem("jwt")){
                fetch(`https://capstone-estratweni.herokuapp.com/products/${id}`, {
                    method: 'PUT',
                    body: JSON.stringify({
                        id: 1,
                        title: 'foo',
                        body: 'bar',
                        userId: 1,
                    }),
                    headers: {
                        'Content-type': 'application/json; charset=UTF-8',
                        Authorization: `Bearer ${localStorage.getItem("jwt")}`,
                    },
                    })
                .then((response) => response.json())
                .then((json) => console.log(json));
            }
        }
       
    },
    
    
}
</script>

<style scoped>
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

figure img {
  height: 60px;
  width: 60px;
  border: 1px solid #bbb;
  border-radius: 50%;
  overflow: hidden;
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
  max-height: 110px !;
}   
table {
  border-collapse: collapse;
  width: 100%;
}
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
    .card-buttons {
        display: flex;
    }
    .card-buttons .btn {
        margin: 4px;
    }
</style>