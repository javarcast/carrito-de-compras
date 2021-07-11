<template>
  <div class="container">

    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div  class="col-md-6" :key="produc.id"  v-for="produc in products">
            <Product :isInCart="changeEnable(produc)"  @addProduct="addProductToList" :product="produc" />
          </div>
        </div>
      </div>
      <div class="col-md-5 my-5">
        <Cart @pay="payMount" @removeProduct="removeProd" :productLists="productLists" />
      </div>
    </div>

  </div>
</template>

<script>

import products from './productos.json'

import Product from './components/Product.vue'
import Cart from './components/Cart.vue'
export default {
  name: 'App',
  components: {
    Product,
    Cart
  },
  data(){
    return{
      products,
      productLists: []
    }
  },
  methods:{
    addProductToList(prod){
      this.productLists.push(prod);
      this.changeEnable(prod);
    },
    changeEnable(prod){
      const item = this.productLists.find( product => product.id === prod.id)
      if(item){
        return true
      }
      return false;
    },
    removeProd(prod){
      this.productLists = this.productLists.filter( item => {
        if(item.id == prod.id){
          this.total -= prod.price;
        }
         return item.id != prod.id
      })
    },
    payMount(){
      this.productLists = [];
      alert('Venta Completada !!!!');
    }
  
  }
}
</script>

<style>
</style>
