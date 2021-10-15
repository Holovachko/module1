<template>
    <div>
    <div class="item">
        <div><strong>Назва магазина</strong> : {{shop.title}}</div>
        <div><strong>Адреса магазина</strong> : {{shop.address}}</div>
        <div><strong>Номер телефону магазина</strong> : {{shop.phoneNumber}}</div>
        <div><strong>Спеціалізація магазина</strong> : {{shop.specialization}}</div>
    </div>
    <button @click="$emit('remove' , shop)">удалити</button>
    </div>
</template>

<script>
    export default {
        props: {
            shop: {
                type: Object,
                default: null
            },
        },
    }
</script>

<style scoped>
.item{
    margin: 10px;
}
</style>