<template>
   <div>
       <router-link to="/">Головна</router-link>
       <router-link to="/second">Друга сторінка</router-link>
       <router-link to="third">Третя сторінка </router-link>


   <shop-form
   @create = 'createShop'
   />
   <shop-list 
   :shops = 'shops'
   @remove ="removeShop"
   />
  </div>
</template>

<script>
import ShopForm from "@/components/ShopForm"
import ShopList from "@/components/ShopList"
    export default {
    name: 'HomePage',
    components: {
    ShopForm,
    ShopList
 },
  data() {
    return {
      shops: [
        {
          id: 1,
          title: 'a;lkfdsjas;dlfjasd;fs',
          address: 'werqwrwqer',
          phoneNumber: '31241254302',
          specialization: 'xcvznczxcv'
        }
      ]
    }
  },
  methods: {
    createShop(shop) {
      this.shops.push(shop);
    },
    removeShop(shop){
        this.shops = this.shops.filter(s => s.id !== shop.id)
    }
  },
    }
</script>

<style scoped>

</style>