<template>
  <div>
      <h5 class="text-center">Productos en el Carrito</h5>
      <ul class="list-group">
          <li :key="product.id" v-for="product in productLists" class="list-group-item">
              {{product.title}}  -  ${{product.price}}
               <button @click="removeProduct(product)" class=" btn btn-danger">Eliminar</button>
          </li>
         
      </ul>
      <div class="card p-3 my-5">
        <h4 class="text-center">Total: ${{totalAmount}}</h4>
      </div>
      <button :disabled="productLists.length===0" @click="$emit('pay')" class="btn btn-info form-control">Pagar Ahora</button>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props:{
        productLists:{
            type: Array,
            required: true
        }
    },
    methods:{
        removeProduct(product){
            this.$emit('remove-product',product)
        }
    },
    computed:{
        totalAmount(){

            if(this.productLists.length>0){
               return this.productLists.reduce( (acum,p) => acum + Number(p.price),0);
            }
            return 0;
        }
    }
}
</script>

<style>

</style>