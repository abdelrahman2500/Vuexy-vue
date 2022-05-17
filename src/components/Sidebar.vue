<template>
    <div :class="['sidebar', activeSideBar, `${theme}-theme`]">
        <div class='sidebar-header'>
                <div class='logo'>
                    <div class='logo-img'>
                        <img src='https://pixinvent.com/demo/vuexy-vuejs-admin-dashboard-template/demo-1/img/logo.36f34a9f.svg' />
                    </div>
                    <div class='logo-name'>
                        <h2>Vuexy</h2>
                        <VueFeather type="circle" ></VueFeather>
                    </div>
                </div>
            </div>
            <div class='dashboards'>
            <!-- dropdown accept icon ,head and list to show  -->
                <Dropdown :theme="theme" icon="home" head="Dashboards" :list="['eCommerce', 'Analystics']" />
                <Dropdown :theme="theme" head="APPS & PAGES"  />
                <Dropdown :theme="theme" head="Email" icon="mail" />
                <Dropdown :theme="theme" head="Chat" icon="message-square" />
                <Dropdown :theme="theme" head="Todo" icon="check-square" />
                <Dropdown :theme="theme" head="Calender" icon="calendar" />
                <Dropdown :theme="theme" head="USER INTERFACE"  />
                <Dropdown :theme="theme" icon="user" head="Dashboards" :list="['List', 'View', 'Edit']" />
                <Dropdown :theme="theme" icon="file-text" head="Invoice" :list="['List', 'Preview', 'Edit', 'Add']" />
                <Dropdown :theme="theme" icon="shopping-cart" head="eCommerce" :list="['Shop', 'Details', 'Checkout']" />
                <Dropdown :theme="theme" icon="user" head="Dashboards" :list="['List', 'View', 'Edit']" />
                <Dropdown :theme="theme" icon="home" head="Dashboards" />
                <Dropdown :theme="theme" icon="file-text" head="Invoice" :list="['List', 'Preview', 'Edit', 'Add']" />
                <Dropdown :theme="theme" icon="home" head="Dashboards" />
                <Dropdown :theme="theme" head="FORMS & TABLES"  />
                <Dropdown :theme="theme" icon="home" head="Dashboards" />
                <Dropdown :theme="theme" icon="user" head="Dashboards" :list="['List', 'View', 'Edit']" />
                <Dropdown :theme="theme" icon="home" head="Dashboards" />
                <Dropdown :theme="theme" icon="home" head="Dashboards" />
                <Dropdown :theme="theme" icon="file-text" head="Invoice" :list="['List', 'Preview', 'Edit', 'Add']" />
                
            </div>
    </div>
</template>

<script>
import VueFeather from 'vue-feather';
import Dropdown from './Dropdown.vue';

export default {
    components: { Dropdown ,VueFeather },
    name: "side-bar",
    props: ['activeSideBar', 'theme'],
}
</script>

<style lang="scss" >

</style>