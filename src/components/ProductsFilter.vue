<template>
    <div :class="['products-filter', `${theme}-theme`, `${activeProductFilter}`]">
            <h6 class='filter-title'>Filters</h6>
            <!-- {{ filterdProducts }} -->
            <div class='filter-options'>
                <form @change="changeMultiRange">
                    <label for="multi-range">
                        <h6>Multi Range</h6>
                    </label>
                    <label class="form-control">
                        <input type="radio" id="multi-range" name="range" value="all" />
                        All
                    </label> 
                    <label class="form-control">
                        <input type="radio" id="multi-range" name="range" value="<=$10" />
                        &lt;=$10
                    </label> 
                    <label class="form-control">
                        <input type="radio" id="multi-range" name="range" value="$10-$100" />
                        $10-$100
                    </label> 
                    <label class="form-control">
                        <input type="radio" id="multi-range" name="range" value="$100-$500" />
                        $100-$500
                    </label> 
                    <label class="form-control">
                        <input type="radio" id="multi-range" name="range" value=">=500$" />
                        &gt;=500$
                    </label> 
                </form>
                <form >
                    <RangeSlider :products="products" :theme="theme" :filterdProducts="filterdProducts" :handleSlider="handleSlider" />
                </form>
                <form @change="changeCategory">
                    <label>
                        <h6>categories</h6>
                    </label>
                    <label class="form-control">
                        <input type="radio" id="category" name="range" value="all" />
                        all
                    </label>
                    <label v-for="category in categories" class="form-control" :key="category">
                        <input type="radio" id="category" name="range" :value="category" />
                        {{category}}
                    </label>
                </form>
                <form @change="changeBrand">
                    <label for="brand">
                        <h6>Brands</h6>
                    </label>
                    <label class="form-control">
                        <input type="radio" id="brand" name="range" value="all" />
                        all
                    </label>
                    <label v-for="brand in brands" class="form-control" :key="brand">
                        <input type="radio" id="brand" name="range" :value="brand" />
                        {{brand}}
                    </label>
                </form>
                <form>
                    <label>
                        <h6>Rating</h6>
                    </label>
                        <div v-for="(_,i) in Array(5).fill('')" class='row' :key="i">
                            <div class='products-rating'  @click="changeRate(i)">
                                <Rating :num="Array(5).fill('').length - i" />
                                <span>
                                    &amp;up
                                </span>
                            </div>
                            <span class='products-amount'>{{products.filter(product => product.rating >= Array(5).fill("").length - i).length}}</span>
                        </div>
                </form>
            </div>
        </div>
</template>

<script>
import { onBeforeMount,  ref } from 'vue'
import RangeSlider from './RangeSlider.vue'
import Rating from './Rating.vue'

export default {
    components: { RangeSlider, Rating },
    name: "proFilter-c",
    props: ['products', 'filterdProducts', 'handleRangePrice', 'handleBrand', 'handleCategory', 'handleRating', 'handleSlider', 'activeProductFilter', 'theme'],
    setup (props, context) {


        const brands = ref(new Set())
        const brandsArr = ref([])
        const categories = ref(new Set())
        const categoriesArr = ref([])

        onBeforeMount(() => {
            props.products.map((pro) => brands.value = brands.value.add(pro.brand));
            brandsArr.value = [...brands.value];

            props.products.map((pro) => categories.value = categories.value.add(pro.category));
            categoriesArr.value = [...categories.value];
        })

        function changeMultiRange(e){
            context.emit('handleRangePrice', e)
        }

        function changeBrand(e){
            context.emit('handleBrand', e)
        }

        function changeCategory(e){
            context.emit('handleCategory', e)
        }

        function changeRate(i){
            context.emit('handleRating', Array(5).fill('').length - i)
        }

        return {
            brands,
            brandsArr,
            categories,
            categoriesArr,
            changeMultiRange,
            changeBrand,
            changeCategory,
            changeRate,
        }
    }
}
</script>

<style lang="scss" scoped>

</style>