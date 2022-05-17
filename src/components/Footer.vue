<template>
    <div :class="['footer', `${theme}-theme`]">
        <p class='left'>
            COPYRIGHT © 2022 <span class='copyright'>Algoriza</span>, <span class='reserved'>All rights Reserved</span> 
        </p>
        <p class='right'>
            Hand-crafted & Made with <VueFeather type="heart" fill="red" stroke="red"></VueFeather>
        </p>
    </div>
</template>

<script>
import VueFeather from 'vue-feather';

export default {
    name: "footer-c",
    props:['theme'],
    components: {VueFeather},
}
</script>

<style lang="scss" scoped>

</style>