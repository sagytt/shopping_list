<template>
    <div>
        <div v-if="product">
            <div>
                <input type="text" v-bind:value="product.name" id="name">
            </div>
            <div>
                <input type="text" v-bind:value="product.price" id="price">
            </div>
            <div>
                <textarea v-bind:value="product.description" id="description"></textarea>
            </div>
            <div>
                <button @click="updateProduct">Update</button>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "EditProduct",
        props: ['product'],
        methods: {
            updateProduct: function() {
                this.product.name= document.getElementById('name').value;
                this.product.price= document.getElementById('price').value;
                this.product.description= document.getElementById('description').value;
            }
        }
    }
</script>

<style scoped>

</style>