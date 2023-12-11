<script setup>
    import data from './data.json'
</script>
<template>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3  gap-12 pt-6">
        <div  v-for="items in data ">
            <div class="flex flex-col gap-2 relative">
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
</template>