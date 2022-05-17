<template>
    <div :class="['dropdown', `${theme}-theme`]">
            <div :class="['dropdown-head',  `${active == 'active' ? 'active' : ''}`]">
                
            <!-- if dropdwon have icon or not  -->
                <template v-if="icon">
                    <VueFeather :type="icon" ></VueFeather>
                </template>
                <h3 :class="[!icon ? 'heading' : '']" @click="handleToggleList">
                    {{head}}
                    <template v-if="list && active == 'active'">
                        <VueFeather type="chevron-down" ></VueFeather>
                    </template>
                    <template v-if="list && active == 'dis-active'">
                        <VueFeather type="chevron-right" ></VueFeather>
                    </template>
                </h3>
            </div>
            <!-- if dropdwon have list or not  -->
            <template v-if="list">
                <ul :class="active">
                    <li v-for="item, i in list" :key="i" :class="i == 0 ? 'active' : ''">
                        <svg  width="14px" height="14px"
                            viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" 
                            strokeLinecap="round" strokeLinejoin="round" 
                            >
                                <circle cx="12" cy="12" r="10"></circle>
                        </svg>
                        {{item}}
                    </li>
                </ul>
            </template>
        </div>
</template>

<script>
import { ref } from 'vue'
import VueFeather from 'vue-feather';

export default {
    name: "drop-down",
    props: ["icon", "head" , "list", "theme"],
    components: {VueFeather},
    setup () {

        const active = ref('dis-active')

        function handleToggleList(){
            active.value == "active" ? active.value = "dis-active" : active.value = "active"
        }

        
    
        return {
            active,
            handleToggleList
        }
    }
}
</script>

<style lang="scss">
    // @import '../styles/_dropdown.scss';
</style>