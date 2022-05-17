<template>
        <div :class="['pagination', `${theme}-theme`]">
            <div class='pagination-list' v-if="itemsList.length && typeof itemsNumberInPage == 'number' && itemsList.length > itemsNumberInPage">
                <span :class="['pagination-item', 'before', `${page == 1 ? 'disable' : ''}`]" @click="handlePagination('before')">
                    <VueFeather type="chevron-left"></VueFeather>
                </span>
                <div class='numbers'>
                    <template v-for="(_,i) in itemsList" :key="i">
                        <button v-if="i < Math.ceil(itemsList.length / itemsNumberInPage)" :class="['pagination-item', `${i+1 == page ? 'active' : ''}`]" 
                            @click="handlePagination(_, i)">
                            <span>{{i+1}}</span>    
                        </button>
                    </template>
                </div>
                <span :class="['pagination-item', 'after', `${page == Math.ceil(itemsList.length / itemsNumberInPage) ? 'disable' : ''}`]" 
                    @click="handlePagination('after')">
                    <VueFeather type="chevron-right"></VueFeather>    
                </span>
            </div>

        </div>
</template>

<script>
import VueFeather from 'vue-feather';


export default {
    name: "pagination-c",
    components: {VueFeather},
    props: ['itemsList', 'itemsNumberInPage', 'page', 'handlePagination', 'theme'],

}
</script>

<style lang="scss" scoped>

</style>