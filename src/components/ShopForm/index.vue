<template>
    <div>
        <h4>Додати магазин</h4>
        <label>
            Назва:
            <input type="text" v-model="shop.title">
        </label>
        <label>
            Адреса:
            <input type="text" v-model="shop.address">
        </label>
        <label>
            Номер телефону:
            <input type="text" v-model="shop.phoneNumber">
        </label>
        <label>
            Спеціалізація:
            <input type="text" v-model="shop.specialization">
        </label>
        <button @click="createShop">Додати магазин</button>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                shop:{
                    title: '',
                    address: '',
                    phoneNumber: '',
                    specialization: ''
                }
            }
        },
        methods: {
            createShop() {
                this.shop.id = Date.now();
                this.$emit('create' , this.shop)
                this.shop = {
                    title: this.title,
                    address: this.address,
                    phoneNumber: this.phoneNumber,
                    specialization: this.specialization
                }
            }
        },
    }
</script>

<style lang="less" scoped>

</style>