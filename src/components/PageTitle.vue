<template>
    <div :class="['page-title', `${theme}-theme`]">
        <div class='left'>
            <h2 class='title'>Shop</h2>
            <ul class='path'>
                <li><VueFeather type="home" ></VueFeather></li>
                <li><VueFeather type="chevron-right" class='arrow' ></VueFeather><span>ECommerce</span> </li>
                <li><VueFeather type="chevron-right" class='arrow' ></VueFeather><span class='active'>Shop</span></li>
            </ul>
        </div>
        <div class='right'>
            <button><VueFeather type="settings" ></VueFeather></button>
        </div>
    </div>
</template>

<script>
import VueFeather from 'vue-feather';

export default {
    name: "pageTitle-c",
    props:["theme"],
    components: {VueFeather},
}
</script>

<style lang="scss" scoped>

</style>