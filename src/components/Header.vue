<template>
<div :class="['header', `${theme}-theme`]">
            <nav class='header-nav'>
                <div class='left'>
                    <ul>
                        <li class='toggle-menu' @click="showSidebar" ><VueFeather type="menu" ></VueFeather></li>
                    </ul>
                    <ul class='icons'>
                        <li><VueFeather type="calendar" ></VueFeather></li>
                        <li><VueFeather type="message-square" ></VueFeather></li>
                        <li><VueFeather type="mail" ></VueFeather></li>
                        <li><VueFeather type="check-square" ></VueFeather></li>
                        <li><VueFeather type="star" color="red"></VueFeather></li>
                    </ul>
                </div>
                <div class='right'>
                    <ul class='icons'>
                        <li class='lang'>
                            <img src='data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGQAAAA1CAMAAACA7r40AAAA/FBMVEWyIjNPN2Y8O27///8/PnBOTXxycpY9PG9RUX5HR3dIR3dLSnlPTny4uMpWVYFFRHVwb5VlZIx7e52DgqOIh6aIiKc+PXBJSHhTUn9hYYqyIjReXohgX4lYV4Lr6/C2tcjPdYB0c5haWYRYV4Nra5GJiac+PW/FxdTHYG1RUH3eoajltbtOTXvty89BQHHg3+hSUX6GYoC6usyVlbFycZa7u8yUk6+sq8FCQXO0tMe1tMhiYYpMS3pDQnNvbpTExNN8fJ7GxdTGxtWCgqLHx9WXlrLXi5SYl7Kiobrg4Oiiorrn5u3n5+2jo7ukpLvw8PTx8fX09Pf19firqsC5sMNxAAAAAnRSTlPQ9qN1Xw4AAAGlSURBVHhe7ZXFiiRBFEVjznvp5W7t7j3u7m7//y8D1dAMGbnI4jW5KOpsgjibCxFcrrtVEmcBGAGQJHB98d3EgEM/ygsg/nwRAy15rxQ4Ywh3JQX49hVgKA/Ad1hDkkGTMSQJjGkOEmo133FmwAEQyl8FfSj3gFgkzjsQAw6AZ796AP2fGcDBS8/ZQ7ZQlJ2d+bEFqp6zhuh9Cf9/pDtKkTs04KBTD4jgx3eICOodoshz1p7M6UUAUQ+Ap2Pf2UMI5UBBX18/Ut7ZQ84Jui10QKsbcA7dt77jxIBDt+sxMNzrD4HL+rZS4Iw9iTZkCjRFmsBUHkcUOGMI7dkpKezuQsrprM3zR76zN572ekdBX623gaONJ0d5B5sGHAA1+QTwRQJgX2Q/7+w9GZGlDZKERpoxgkbDc8s0WscGSo+WGMiNVlgwWuFNjdafPsDe7wzg3RvP2UNCFGVtbX6EoOo7PhgoO1rGnswHiquB4mqgfIcxpBTGkNslMf2JVMAShRxXgJtUwBKFbFbAqicL4U4qYNWThXCHFbDqyUK4swpY9WQhXBX8A2rVjaQ6HWXmAAAAAElFTkSuQmCC' />
                            <span class='lang-span'>English</span>
                        </li>
                        <li class='toggle-theme' @click="setTheme">
                            <template v-if="theme == 'dark'">
                                <VueFeather type="sun" ></VueFeather>
                            </template>
                            <template v-else>
                                <VueFeather type="moon" ></VueFeather>
                            </template>
                        </li>
                        <li><VueFeather type="search" ></VueFeather></li>
                        <li><VueFeather type="shopping-cart" ></VueFeather></li>
                        <li class='notification'>
                            <span class='notification-sapn'>6</span>
                            <VueFeather type="bell" ></VueFeather>
                        </li>
                        <li class='user'>
                            <div class='user-info'>
                                <p class='user-name'>Abdelrahman</p>
                                <span class='user-role'>admin</span>
                            </div>
                            <span class='user-icon'>
                                <VueFeather type="user" ></VueFeather>
                                <span class='status'></span>
                            </span>
                        </li>
                    </ul>
                </div>
            </nav>
        </div>
</template>

<script>
import VueFeather from 'vue-feather';

export default {
    name: "header-c",
    components: {VueFeather},
    props: ["showSidebar", "theme", "setTheme"],
}
</script>

<style lang="scss" >

</style>