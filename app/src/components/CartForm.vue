<template>
    <form @submit.prevent class="form__box">
        <label class="label__name first">Наименование товара</label>
        <input 
            v-model="cart.title"
            class="input"
            type="text" 
            required="required"
            placeholder="Введите наименование товара">
        <label class="label__name">Описание товара</label>
        <textarea 
            v-model="cart.body"
            class="input area"
            required="required"
            placeholder="Введите описание товара"
            />
        <label class="label__name">Ссылка на изображение товара</label>
        <input 
            v-model="cart.image"
            type=""
            class="input"
            required="required"
            placeholder="Введите ссылку">
        <label class="label__name">Цена товара</label>
        <input 
            v-model="cart.price"
            type="number"
            class="input"
            required="required"
            placeholder="Введите цену">
        <button 
            @click="createCart"
            :disabled='!isComplete'
            class="btn">Добавить</button>
    </form>
</template>

<script>
export default {
    data () {
        
        return {
            cart: {
                title: '',
                body: '',
                image: '',
                price: ''
            },
        }
    },
    computed: {
        isComplete () {
            return this.cart.title && this.cart.body && this.cart.image && this.cart.price;
        },
    },
    methods: {
        createCart() {
            this.cart.id = Date.now();
            this.$emit('create', this.cart)
            this.cart = {
                title: '',
                body: '',
                image: '',
                price: '',
            }
        },
        
    }
    
}
</script>

<style scoped>
* {
    font-family: Source Sans Pro;
}
form {
  display: flex;
  flex-direction: column;
}
.form__box {
    background: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    margin-left: 32px;
}
.input {
  background: #FFFEFB;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    width: 284px;
    margin: 4px 24px 0 24px;
    padding: 10px 10px 11px 16px;
    border: none;
    
}
.area {
    height: 108px;
    text-align: left;
}
.label__name {
    font-size: 10px;
    line-height: 13px;
    letter-spacing: -0.02em;
    color: #49485E;
    margin: 16px 0 0 24px;
}
.first {
margin-top: 24px;
}
.btn {
    height: 36px;
    left: 56px;
    top: 463px;
    background: #7BAE73;
    color: #FFFFFF;
    border-radius: 10px;
    margin: 24px;
    border: none;
}

.success {
    background: #EEEEEE;
    color: #B4B4B4;
}
input:invalid ~ button {
    background: #EEEEEE;
    color: #B4B4B4;
}
</style>