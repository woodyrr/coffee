<script setup>
    import { ref} from 'vue';
    import All from './full.vue'
    import availlable from './available.vue'
    const currentTab = ref('Watching')

    const tabs = {
        All,
        availlable
    }

    
</script>

<template>
    <div>
        <img src="../assets/bg-cafe.jpg" alt="" srcset="">
    </div>
    <div class="absolute top-[26%] px-[10%] w-full pb-[10%]">
    
        <div class=" bg-[#1B1D1F] w-full text-[#FEF7EE] flex justify-center items-center text-center flex-col gap-6 rounded-2xl pb-24">
            <div class="flex flex-col gap-5 items-center text-center w-full pt-20 main">
                <h1 class="text-5xl text-[#FEF7EE] font-bold">
                Our Collection
                </h1>
                <p class="text-[#6F757C] px-[25%] text-base">Introducing our Coffee Collection, a selection of unique coffees from different roast types and origins, expertly roasted in small batches and shipped fresh weekly.</p>
            </div>
            <div class="flex gap-3 pt-10">
                <div class="flex gap-3">
                    <div class="text-center ">
                        <button
                        v-for="(_, tab) in tabs"
                        :key="tab"
                        :class="['tab-button', { active: currentTab === tab }]"
                        @click="currentTab = tab"
                        class="p-2 rounded-lg "
                        
                        >
                        {{ tab }}
                        </button>
                        <component :is="tabs[currentTab]"></component>
                    </div>
                </div>
                
            </div>

        </div>
        
    </div>
  
</template>

<style scoped>
    .main{
        background-image: url('../assets/vector.svg');
        background-repeat: no-repeat;
        background-position:center  ;
        
    }
    .btncolor{
        background-color: #6F757C;
    }
    .tab-button.active {
    background-color:#6F757C;
    font-weight: bold;
    }

</style>
