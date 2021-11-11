<template>
  <div class="app">
    <cart-form
    @create="createCart"/>
  </div>
  <div class="cartForm">
    <cart-list 
    :carts="carts"
    @remove="removeCart"/>
  </div>
</template>

<script>
import CartForm from "@/components/CartForm";
import CartList from "@/components/CartList";
export default {
  components: {
    CartList,
    CartForm
  },
  data () {
    return {
      carts: [],
    }
  },
  methods: {
    createCart(cart) {
      this.carts.push(cart)
    },
    removeCart(cart) {
      this.carts = this.carts.filter(c => c.id !== cart.id)
    }
    
  }
}
</script>

<style>

.cartForm {
  display: flex;
  flex-wrap: wrap;
}

</style>
