<template>
    <div class="cart" v-for="cart in carts" :key="cart.id" @remove="$emit('remove', cart)">
        <div class="image"><img src="../assets/log1.png"></div>
        <div class="name"><strong>{{cart.title}}</strong></div>
        <div class="about">{{cart.body}}</div>
        <div class="price"><strong>{{cart.price}} руб.</strong></div>
        <button @click="$emit('remove', cart)" class="del"><img src="../assets/del.svg"></button>
    </div>
    
</template>

<script>
export default {
    props: {
        carts: {
            type: Array,
            required: true
        }
    },
}
</script>

<style scoped>
* {
    font-family: Source Sans Pro;
}
.cart {
    display: flex;
    flex-direction: column;
    text-align: left;
    width: 332px;
    background: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    margin-left: 16px;
    margin-bottom: 16px;
}
.name {
    padding: 16px 16px 16px 16px;
    word-break: break-all;
}
.about {
    padding: 16px 16px 32px 16px;
    word-break: break-all;
}
.price {
    padding: 0 16px 24px 16px;
}
.del {
    background: #FF8484;
    box-shadow: 0px 2px 4px rgb(0 0 0 / 10%);
    border-radius: 10px;
    padding: 8px;
    position: absolute;
    margin: -16px 0px 0px 311px;
    opacity: 0;
    border: none;
}
.del:hover {
    display: inline-block;
    opacity: 1;
}
.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active,
.list-leave-active {
  transition: all 5s ease;
}
.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(80px);
}
</style>