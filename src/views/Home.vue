<template>
    <div class="home">
        <div class="row">
            <div class="column">
                <ul>
                    <li  class="list img-list"
                         v-for="(product, i) in this.products"
                         :key="i"
                         @click="selectProduct(i)">
                        <div class="inner">
                            <div class="li-img">
                                <img :src="product.thumbnailImage"
                                     alt="Hot air balloons"/>
                            </div>
                            <div class="li-text">
                                <h3 class="li-head">{{product.name}}</h3>
                                <div class="li-sub">
                                    <p>{{product.description}}</p>
                                </div>
                            </div>
                            <button class="button" style="vertical-align:middle"><span>Delete </span></button>
                        </div>
                    </li>
                </ul>
            </div>
            <div class="column">
                <EditProduct :product="this.selectedProduct"/>
            </div>
        </div>
    </div>
</template>

<script>
    // @ is an alias to /src
    import EditProduct from '@/components/EditProduct.vue'
    import json from '@/data/items.json'

    export default {
        name: 'Home',
        data() {
            return {
                products: json,
                selectedProduct: null
            }
        },
        methods: {
            selectProduct: function (i) {
                this.selectedProduct = this.products[i];
            }
        },
        components: {

            EditProduct
        }
    }
</script>

<style>
    * {
        box-sizing: border-box;
    }
    .column {
        float: left;
        width: 50%;
        padding: 5px;
    }
    .row {
        margin-left:-5px;
        margin-right:-5px;
    }
    .row::after {
        content: "";
        clear: both;
        display: table;
    }
    .button {
        display: inline-block;
        border-radius: 4px;
        background-color: #f4511e;
        border: none;
        color: #FFFFFF;
        text-align: center;
        /* font-size: 0px; */
        /* padding: 20px; */
        height: 29px;
        /* padding-bottom: 24px; */
        width: 90px;
        transition: all 0.5s;
        cursor: pointer;
        margin-top: 22px;
        margin-left: 41px;
    }
    .button span:after {
        content: '\00bb';
        position: absolute;
        opacity: 0;
        top: 0;
        right: -20px;
        transition: 0.5s;
    }

    .button:hover span {
        padding-right: 25px;
    }

    .button:hover span:after {
        opacity: 1;
        right: 0;
    }
    .list {
        max-width: 1400px;
        margin: 20px auto;
    }

    .img-list {
        text-decoration: none;
        border: 3px solid #2c3e50;
        border-radius: 5px;
    }

    .li-sub p {
        margin: 0;
    }

    .list li {
        display: table;
        border-collapse: collapse;
        width: 100%;
    }

    .inner {
        display: table-row;
        overflow: hidden;
        cursor: pointer;
    }

    .li-img {
        display: table-cell;
        vertical-align: middle;
        width: 30%;
        padding-right: 1em;
    }

    .li-img img {
        display: block;
        width: 50px;
        height: 50px;
    }

    .li-text {
        display: table-cell;
        vertical-align: middle;
        width: 70%;
    }

    .li-head {
        margin: 10px 0 10px 0;
    }

    .li-sub {
        margin: 0;
    }

    @media all and (min-width: 45em) {
        .list li {
            float: left;
            width: 50%;
        }
    }

    @media all and (min-width: 75em) {
        .list li {
            width: 33.33333%;
        }
    }

    /* for flexbox */
    @supports (display: flex) {
        .list {
            display: flex;
            flex-direction: row;
            justify-content: center;
        }

        .li-img,
        .li-text,
        .list li {
            display: block;
            float: none;
        }

        .li-img {
            align-self: center; /* to match the middle alignment of the original */
        }

        .inner {
            display: flex;
        }
    }

    /* for grid */
    @supports (display: grid) {
        .list {
            /*display: flex;*/
            /*display: grid;*/
            /*grid-template-columns: repeat(auto-fill, minmax(400px, 1fr));*/
            width: 45%;
        }

        .list li {
            width: auto; /* this overrides the media queries */
        }
    }

    .flex-container {
        display: flex;
        flex-direction: row;
    }
    .flex-item-left {
        flex: 100%;
    }
    .flex-item-right {

        flex: 100%;
    }
    @media (max-width: 800px) {
        .flex-container {
            flex-direction: column;
        }
    }

</style>
