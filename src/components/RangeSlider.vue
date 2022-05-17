<template>
    <label for="price-range">
        <h6>Price Range</h6>
        <span v-if="range1 <= range2">{{range1}} : {{range2}}$</span>
        <span v-else>{{range2}} : {{range1}}$</span>
    </label>

    <div :class="['range-slider', `${theme}-theme`]" @change="handleSlider(range1, range2)">
        <input type="range" step="1" :min="Math.min(...minmax)" :max="Math.max(...minmax)" :value="range1" @change="range1 = Number($event.target.value)" id="slider1" />
        <input type="range" step="1" :min="Math.min(...minmax)" :max="Math.max(...minmax)" :value="range2" @change="range2 = Number($event.target.value)" id="slider2" />
    </div>
</template>

<script>
import { onBeforeMount, ref } from 'vue'

export default {
    name: "r-slider-c",
    props: ['products', 'handleSlider', 'theme'],
    setup (props) {

        const minmax = ref([])
        const range1 = ref(0)
        const range2 = ref(100)

    onBeforeMount(() => {
        props.products.forEach(p => minmax.value.push(p.price))
        range1.value = Math.min(...minmax.value)
        range2.value = Math.max(...minmax.value)
    })
    
    
        return {
            minmax,
            range1,
            range2,
        }
    }
}
</script>

<style lang="scss" scoped>
    label{
        display: flex;
        justify-content: space-between;
        span{
            color: #7367f0;
        }
    }
</style>