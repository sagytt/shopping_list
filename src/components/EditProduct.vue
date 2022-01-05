<template>
    <div>
        <form v-if="product">
            <label for="name">First Name</label>
            <input type="text" id="name" name="name" v-bind:value="product.name">

            <label for="description">Description</label>
            <textarea id="description" v-bind:value="product.description"></textarea>

            <label for="price">Price</label>
            <input type="number" id="price" name="price" v-bind:value="product.price">

            <input type="submit" @click="updateProduct" value="Save">
        </form>
    </div>
</template>

<script>
    export default {
        name: "EditProduct",
        props: ['product'],
        methods: {
            updateProduct: function() {
                this.product.name = document.getElementById('name').value;
                this.product.price= document.getElementById('price').value;
                this.product.description= document.getElementById('description').value;
            }
        }
    }
</script>

<style scoped>
    #formdata{
        top: 120px;
        float: right;
        position: fixed;
    }
    input[type=text], select {
        width: 100%;
        padding: 12px 20px;
        margin: 8px 0;
        display: inline-block;
        border: 1px solid #ccc;
        border-radius: 4px;
        box-sizing: border-box;
    }

    input[type=submit] {
        width: 100%;
        background-color: #4CAF50;
        color: white;
        padding: 14px 20px;
        margin: 8px 0;
        border: none;
        border-radius: 4px;
        cursor: pointer;
    }

    input[type=submit]:hover {
        background-color: #45a049;
    }

    div {
        border-radius: 5px;
        background-color: #f2f2f2;
        padding: 20px;
    }
</style>