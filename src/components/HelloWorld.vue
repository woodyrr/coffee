<script setup>
    import { ref} from 'vue';
    import all_products from './full.vue'
    import availlable_now from './available.vue'
    const currentTab = ref('Watching')
    import data from './data.json'
    const tabs = {
        all_products,
        availlable_now
    }
    let bro = true

    
</script>

<template>
    <div>
        <img src="../assets/bg-cafe.jpg" alt="" srcset="" class="h-[250px] sm:h-[280px] md:h-[450px] lg:h-[520px] w-full">
    </div>
    <div class="absolute top-[13%] sm:top-[18%] md:top-[26%] px-[10%] w-full pb-[10%]">
    
        <div class=" bg-[#1B1D1F] w-full text-[#FEF7EE] flex justify-center items-center text-center flex-col gap-6 rounded-2xl pb-24">
            <div class="flex flex-col gap-5 items-center text-center w-full pt-20 main">
                <h1 class="text-2xl sm:text-3xl md:text-4xl lg:text-5xl text-[#FEF7EE] font-bold">
                Our Collection
                </h1>
                <p class="text-[#6F757C] px-[13%] md:px-[25%] text-sm md:text-base">Introducing our Coffee Collection, a selection of unique coffees from different roast types and origins, expertly roasted in small batches and shipped fresh weekly.</p>
            </div>
            <div class="flex gap-3 pt-10">
                <div class="flex gap-3">
                    <div class="text-center ">
                        <button
                        v-for="(_, tab) in tabs"
                        :key="tab"
                        :class="['tab-button', { active: currentTab === tab }]"
                        @click="currentTab = tab, bro = false"
                        class="p-2 rounded-lg "
                        
                        >
                        {{ tab }}
                        </button>
                        <component :is="tabs[currentTab]"></component>
                    </div>
                </div>
                
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3  gap-12 pt-6" v-if="bro == true">
                <div  v-for="items in data ">
                    <!-- <div v-if="items."></div> -->
                    <div  class="flex flex-col gap-2 relative">
                        <img :src="items.image" alt="" srcset="" class="h-full md:h-[150px] 2xl:h-[200px] rounded-2xl ">
                        <div v-if="items.popular == true" class="absolute bg-[#F6C768] px-2 py-1 text-[#111315] font-semibold rounded-full top-2 left-2">popular</div>
                        
                        
                        <div class="flex justify-between">
                            <div class="name text-xl">{{items.name}}</div>
                            <div class="pricing bg-[#BEE3CC] p-2 rounded-md text-[#111315] font-semibold">{{items.price}}</div>
                        </div>
                        <div class="flex justify-between">
                            <div class="flex gap-2 font-semibold">
                                <div v-if="items.rating" class="flex">
                                    <div>
                                        <img src="../assets/Star_fill.svg" alt="" srcset="">
                                    </div>
                                    <div class="rating">{{items.rating}}</div>
                                </div>
                                <div v-else class="flex gap-2">
                                    <div>
                                        <img src="../assets/Star.svg" alt="" srcset="">
                                    </div>
                                    <div class="text-[#6F757C] text-sm md:text-base">No ratings</div>
                                </div>
                                
                                <div class="votes text-[#6F757C]" v-if="items.votes > 0">({{items.votes}} votes)</div>
                            </div>
                            <div>
                                <div v-if="items.available == false" class="text-[#ED735D]">
                                    Sold out
                                </div>
                            </div>
                            
                        </div>
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
