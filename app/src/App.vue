<template>
<div>
<div class="main">
  <p class="label">Добавление товара</p>
  <my-select
      v-model="selectedSort"
      :options="sortOptions"
      class="select"
    />
</div>
<div class="app__main">
  <div class="app">
    <cart-form
    @create="createCart"/>
  </div>
  <div class="cartForm">
    <cart-list 
    :carts="sortedCarts"
    @remove="removeCart"/>
  </div>
</div>
</div>
</template>

<script>
import CartForm from "@/components/CartForm";
import CartList from "@/components/CartList";
import MySelect from "@/components/MySelect";
export default {
  components: {
    CartList,
    CartForm,
    MySelect
  },
  data () {
    return {
      carts: [],
      selectedSort: '',
      sortOptions: [
        {value: 'title', name: 'По наименованию'},
        {value: 'price', name: 'По цене'}
      ]
    }
  },
  methods: {
    createCart(cart) {
      this.carts.push(cart)
    },
    removeCart(cart) {
      this.carts = this.carts.filter(c => c.id !== cart.id)
    }
  },
  computed: {
    sortedCarts() {
      return [...this.carts].sort((cart1, cart2) =>
      cart1[this.selectedSort]?.localCompare(cart2[this.selectedSort])
    )
    }
  },
  watch: {
  }
}
</script>

<style>
* {
    font-family: Source Sans Pro;
}
.cartForm {
  display: flex;
  flex-wrap: wrap;
}
.main {
  display: flex;
  justify-content: space-between;
}
.app__main {
  display: flex;
}
.label {
  font-family: Source Sans Pro;
  font-style: normal;
  font-weight: 600;
  font-size: 28px;
  line-height: 35px;
  color: #3F3F3F;
  margin: 32px 0 16px 32px;
}
.select {
  background: #FFFEFB;
  box-shadow: 0px 2px 5px rgb(0 0 0 / 10%);
  border-radius: 4px;
  border: navajowhite;
  margin: 22px;
  padding: 10px 27px 11px 16px;
  font-family: Source Sans Pro;
  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 15px;
  color: #B4B4B4;
}

</style>
