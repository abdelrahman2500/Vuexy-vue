<template>
<div :class="['product', `${theme}-theme`]">

            <div class='menu-mode' v-if="showMode == 'menu-mode'">
                <div class='product-img'>
                    <img :src="product.img" />
                </div>
                <div class='product-details'>
                    <div class='rating-and-price'>
                        <div class='product-rating'>
                            <Rating :num="product.rating" />
                        </div>
                        <div class='product-price'>
                            <h6>${{product.price}}</h6> 
                        </div>
                    </div>
                    <div class='name-and-description'>
                        <h6 class='name'>
                            {{product.name}}
                        </h6>
                        <p class='desc'>
                            {{product.discription}}
                        </p>
                    </div>
                </div>
                <div class='product-actions'>
                    <button class='wish' @click="() => color =='transparent' ? color ='red' : color ='transparent'">
                        <VueFeather type="heart" :fill="color"></VueFeather>Wishlist
                    </button>
                    <button class='add'><VueFeather type="shopping-cart"></VueFeather> View In Cart</button>
                </div>
            </div>

            <div class='list-mode' v-else>
                <div class='product-img'>
                    <img :src="product.img" />
                </div>
                <div class='product-details'>
                    <h6 class='name'>
                        {{product.name}}
                    </h6>
                    <p class='product-brand'>
                        by <span>{{product.brand}}</span>
                    </p>
                    <div class='product-rating'>
                            <Rating :num="product.rating" />
                    </div>
                    <p class='desc'>
                        {{product.discription}}
                    </p>
                </div>
                <div class='product-actions'>
                    <div class='product-price'>
                        <h4>${{product.price}}</h4> 
                    </div>
                    <button class='wish' @click="() => color =='transparent' ? color ='red' : color ='transparent'">
                        <VueFeather type="heart" :fill="color" ></VueFeather>Wishlist
                    </button>
                    <button class='add'><VueFeather type="shopping-cart"></VueFeather> View In Cart</button>
                </div>
            </div>
        </div>
</template>

<script>
import { ref } from 'vue'
import VueFeather from 'vue-feather';
import Rating from './Rating.vue'

export default {
    name: "product-c",
    props: ['product', 'showMode', 'theme'],
    components: {VueFeather, Rating},
    setup () {

        const color = ref('transparent')
    
        return {
            color
        }
    }
}
</script>

<style lang="scss" scoped>

</style>