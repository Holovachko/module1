<template>
    <div>
            <div>
            <h1>Фільтр:</h1>
            <label > 
                Назва 
                <input type="text" v-model="searchTitle">
            </label>
        </div>
        <div>
            <h1>Сортування</h1>
            <label> Сортувати за :
                <select v-model="sortField">
                    <option value="title">Назва</option>
                    <option value="address">Адреса</option>
                    <option value="phoneNumber">Номер телефону</option>
                    <option value="specialization">Спеціалізація</option>
                </select>
            </label>
        </div>
        <shop-item
        v-for="shop in filteredShops"
        :shop = "shop"
        :key="shop.id"
        @remove ="$emit('remove', shop)"
        />

    </div>
</template>

<script>
import ShopItem from '@/components/ShopItem'
    export default {
        components: {
            ShopItem,
        },
         data() {
            return {
                searchTitle: null,
                sortField:null
            }
        },
        props: {
            shops: {
                type: Array,
                default: ()=> []
            },
        },
        computed: {
            filteredShops() {
                let list=this.shops
                if(this.searchTitle)
                    list= this.shops.filter(item=>item.title.startsWith(this.searchTitle)
                )
                if(this.sortField){
                    list.sort((item1, item2)=>{
                        let val1 = item1[this.sortField]
                        let val2 = item2[this.sortField]
                        if(typeof val1 ==='string'){
                            val1=val1.toUpperCase()
                            val2=val2.toUpperCase()
                        }
                        if(val1===val2 )
                            return 0
                        if(val1>val2)
                            return 1
                        return -1
                    })
                }

                return list
            }
        },
    }
</script>

<style scoped>

</style>