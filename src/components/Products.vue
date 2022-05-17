<template>
        <div :class="['product-page', `${showMode}`]">
        <!-- handle showing products with pagination  -->
            <template 
                v-for="(product, i) in filterdProducts" 
                :key="product.id" >
                <Product 
                    :product="product" 
                    :showMode="showMode" 
                    :theme="theme"
                    v-if="i >= (page-1) * itemsNumberInPage && i < page * itemsNumberInPage"    
                />
            </template>
            <!-- {{ filterdProducts.length }} -->
        </div>
        <Pagination :itemsList="filterdProducts" :itemsNumberInPage="itemsNumberInPage" :page="page" :handlePagination="handlePagination" :theme="theme" />

</template>

<script>
import {  onBeforeMount, ref, watch } from 'vue'
import Product from './Product.vue'
import Pagination from './Pagination.vue'

export default {
    name: "products-c",
    props: ['filterdProducts', 'showMode', 'theme'],
    components: {Product, Pagination},
    setup (props) {

        const page = ref(1)
        const itemsNumberInPage = ref(9)

        onBeforeMount(()=> {
            page.value = 1
        })
        
        watch(() => props.filterdProducts,() => {
                page.value = 1
                window.scrollTo({
                    top: 0,
                    behavior: "smooth",
                });

            });

        function handlePagination(e, i){
            if( e == 'before'){
                page.value > 1 ? page.value = page.value-1 :  ""
            }
            else if(e == 'after'){
                page.value < Math.ceil(props.filterdProducts.length / itemsNumberInPage.value) ? page.value = page.value+1 : ""
            }
            else{
                page.value = i+1
            }
            
            window.scrollTo({
                top: 0,
                behavior: "smooth",
            });

        }

        return {
            page,
            itemsNumberInPage,
            handlePagination
        }
    }
}
</script>

<style lang="scss" scoped>

</style>