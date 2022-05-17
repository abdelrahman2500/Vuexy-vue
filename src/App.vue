<template>
    <div :class="['App', `${theme}-theme`]">
        <Sidebar :activeSideBar="activeSideBar" :theme="theme" />
        <div :class="['overlay-for-sidebar', activeSideBar]" @click="showSidebar"></div>
            <div class='content'>
                <Header :showSidebar="showSidebar" :theme="theme" :setTheme="setTheme" />
                <div class='page-content'>
                    <PageTitle :theme="theme" />
                    <div class='products-and-filters'>
                        <div :class="['overlay-filter', activeProductFilter]" @click="showProductFilter"></div>
                        <ProductsFilter 
                            :products="products" 
                            :filterdProducts="filterdProducts" 
                            @handleBrand="handleBrand"
                            @handleCategory="handleCategory"
                            @handleRangePrice="handleRangePrice" 
                            @handleRating="handleRating"
                            :handleSlider="handleSlider"
                            :activeProductFilter="activeProductFilter" 
                            :showProductFilter="showProductFilter" 
                            :theme="theme" />
                        <div class='products-and-search'>
                            <SearchFilter 
                                :products="products" 
                                :filterdProducts="filterdProducts" 
                                :setShowMode="setShowMode" 
                                @handleSearchByName="handleSearchByName" 
                                :feature="feature" 
                                @handleByPrice="handleByPrice" 
                                :showProductFilter="showProductFilter" 
                                :showMode="showMode"  
                                :theme="theme" />
                            <Products :filterdProducts="filterdProducts" :showMode="showMode" :theme="theme" />
                        </div>
                    </div>
                </div>
                <!-- Footer -->
                <Footer :theme="theme" />
                <div :class="['go-to-up', showTopBtn ? 'show' : '']">
                    <button @click="goToTop"><VueFeather type="arrow-up" ></VueFeather></button>
                </div>
            </div>
    </div>
</template>

<script>
import {ref} from 'vue'
import data from './assets/data.json'
import Sidebar from './components/Sidebar.vue'
import { onBeforeMount } from '@vue/runtime-core'
import Header from './components/Header.vue'
import PageTitle from './components/PageTitle.vue'
import ProductsFilter from './components/ProductsFilter.vue'
import SearchFilter from './components/SearchFilter.vue'
import Products from './components/Products.vue'
import Footer from './components/Footer.vue'
import VueFeather from 'vue-feather';
export default {
    components: { Sidebar, Header, PageTitle, ProductsFilter, SearchFilter, Products, Footer, VueFeather },
    setup () {

        const filterdProducts = ref(data.products);
        const products = ref(data.products);
        const theme = ref('dark');
        const activeSideBar = ref('');
        const activeProductFilter = ref('');
        const feature = ref('Featured');
        const showMode = ref('menu-mode');
        const showTopBtn = ref(false);

        onBeforeMount(() => {
            products.value = data.products 
            window.addEventListener("scroll", () => {
                if (window.scrollY > 200) {
                    showTopBtn.value = true;
                } else {
                    showTopBtn.value = false;
                }
            });
        })

        function setTheme(){
            theme.value == "dark" ? theme.value ="light" : theme.value ="dark"
        }

        function showSidebar(){
            activeSideBar.value == "active" ? activeSideBar.value ="": activeSideBar.value ="active"
        }

        function showProductFilter(){
            activeProductFilter.value == "active" ? activeProductFilter.value = "" : activeProductFilter.value = "active"
        }

        function handleByPrice(e){
            let sort = e.target.innerText ;
            feature.value = sort
            filterdProducts.value = filterdProducts.value.sort((a,b) => (
                sort === 'Lowest' ? ((a.price > b.price) ? 1 : -1) 
                : sort === 'Highest' ?  ((a.price < b.price) ? 1 : -1) 
                : ( a.id < b.id ? 1 : -1 )
            ))
        }

        // handle filter by price range
        function handleRangePrice(e){
            switch (e.target.value) {
                case "all":
                    filterdProducts.value = products.value
                    break;
                case "<=$10":
                    filterdProducts.value = products.value.filter(product => product.price <= 10)
                    break;
                case "$10-$100":
                    filterdProducts.value = products.value.filter(product => product.price > 10 && product.price <= 100)
                    break;
                case "$100-$500":
                    filterdProducts.value = products.value.filter(product => product.price > 100 && product.price <= 500)
                    break;
                case ">=500$":
                    filterdProducts.value = products.value.filter(product => product.price > 500)
                    break;
                default:
                    break;
            }
        }

        // handle filter by brand
        function handleBrand(e){
            if(e.target.value == "all"){
                filterdProducts.value = products.value
            } else {
            filterdProducts.value = products.value.filter(product => product.brand == e.target.value)
            }
        }

        // handle filter by category
        function handleCategory(e){
            if(e.target.value == "all"){
                filterdProducts.value = products.value
            } else {
                filterdProducts.value = products.value.filter(product => product.category == e.target.value)
            }
        }

        // handle filter by rating
        function handleRating(rate){
            filterdProducts.value = products.value.filter(product => product.rating >= rate)
        }

        function handleSlider(range1, range2){
            filterdProducts.value = products.value.filter(pro => (
                range1 <= range2 ? pro.price >= range1 && pro.price <= range2 :  pro.price <= range1 && pro.price >= range2 
            ))
        }

        function setShowMode(mode){
            showMode.value = mode
        }

        // handle filter by searching
        function handleSearchByName(value){
            if(value.trim()){
                filterdProducts.value = products.value.filter((product) => product.name.toLowerCase().includes(value.trim().toLowerCase()))
            } else {
                filterdProducts.value = products.value
            }
        }

        function goToTop() {
            window.scrollTo({
                top: 0,
                behavior: "smooth",
            });
        }
        

        return {
            filterdProducts,
            products,
            theme,
            activeSideBar,
            activeProductFilter,
            feature,
            showMode,
            showTopBtn,


            setTheme,
            showSidebar,
            showProductFilter,
            handleByPrice,
            handleRangePrice,
            handleBrand,
            handleCategory,
            handleRating,
            handleSlider,
            setShowMode,
            handleSearchByName,
            goToTop,
        }
    }
}
</script>

<style lang="scss">
    @import './styles/main.scss';
    @import './styles/_App.scss';
</style>
