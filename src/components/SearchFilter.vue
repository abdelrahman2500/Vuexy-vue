<template>
    <div :class="['search-filter', `${theme}-theme`]">
        <div class='search-row'>
            <h4>{{filterdProducts.length}} results found</h4>
            <div class='toggle-menu' @click="showProductFilter"><VueFeather type="menu" ></VueFeather></div>
            <div class='btns'>
                <div class='features'>
                    <button class='features-btn' @click="handleSortBtn">{{feature}} <VueFeather type="chevron-down" ></VueFeather></button>
                    <ul :class="active ? active = 'active' : active = ''">
                        <li @click="changeFeature($event)">Featured</li>
                        <li @click="changeFeature($event)">Lowest</li>
                        <li @click="changeFeature($event)">Highest</li>
                    </ul>
                </div>
                <div class='group-btns'>
                    <button :class="`${showMode == 'menu-mode' ? 'active': ''}`" @click="setShowMode('menu-mode')"> <VueFeather type="grid" ></VueFeather></button>
                    <button :class="`${showMode == 'list-mode' ? 'active': ''}`" @click="setShowMode('list-mode')"> <VueFeather type="list" ></VueFeather></button>
                </div>
            </div>
        </div>
        <form >
            <input type="text" placeholder='Search Product' v-model="searchValue" @change="filterBySearch" />
            <span><VueFeather type='search'></VueFeather></span>
        </form>
    </div>
</template>

<script>
import { ref, watch } from 'vue'
import VueFeather from 'vue-feather';

export default {
    name: "search-c",
    components: {VueFeather},
    props: ['products', 'filterdProducts', 'feature', 'handleByPrice', 'showProductFilter', 'handleSearchByName', 'showMode', 'setShowMode', 'theme'],
    setup (props, context) {

        const searchValue = ref('')
        const active = ref(false)

        function handleSortBtn(){
            active.value ? active.value = false : active.value = true 
        }

        function filterBySearch(){
            context.emit('handleSearchByName', searchValue.value)
        }

        function changeFeature(e){
            context.emit('handleByPrice', e)
            handleSortBtn()
        }

        watch(searchValue, filterBySearch)
    
        return {
            searchValue,
            active,
            filterBySearch,
            changeFeature,
            handleSortBtn
        }
    }
}
</script>

<style lang="scss" scoped>

</style>