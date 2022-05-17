<template>
    <div class="rating">
        <span v-for="(_, i) in stars" :key="i" >
            <VueFeather v-if="i < num" type="star" fill="#ff9f43" stroke="#ff9f43" width="16"></VueFeather>
            <VueFeather v-else type="star" stroke="#b9b9c3"></VueFeather>
        </span> 
    </div>
</template>

<script>
import { ref } from 'vue'
import VueFeather from 'vue-feather';


export default {
    name: "rating-c",
    props:['num'],
    components: {VueFeather},
    setup () {
        const stars = ref(Array(5).fill(""))
    
        return {
            stars
        }
    }
}
</script>

<style lang="scss" scoped>

</style>