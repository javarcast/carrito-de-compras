<template>
  <div class="card my-5">
      <div class="card-body">
          <h5 class="text-center card-title">{{product.title}}</h5>
          <img :src="product.image" width="275" height="150" :alt="product.title">
          <p class="text-center text-muted card-text display-4">$ {{Number(product.price).toFixed()}}</p>
          <button :disabled="isInCart" @click="addToCard" class="btn btn-success form-control">{{isInCart?'Agregado':'Agregar al carrito'}}</button>
      </div>
  </div>
</template>

<script>
export default {
    name: 'Product',
    props:{
        product:{
            type: Object,
            requred: true
        },
        isInCart:{
            type: Boolean,
            default: false
        }
    },
    methods:{
        addToCard(){
            this.$emit('addProduct',this.product)
        }
    }
}
</script>

<style>

</style>