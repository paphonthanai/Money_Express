<script setup>

import iconCoin from '@/components/icons/iconCoin.vue'
import iconGamepad from '@/components/icons/iconGamepad.vue'
import iconGive from '@/components/icons/iconGive.vue'
import iconTalk from '@/components/icons/iconTalk.vue'
import iconSell from '@/components/icons/IconSell.vue'
</script>


<template>

    <div class="w-full mx-auto text-[#fff]">
        <ul class="hidden md:flex flex-cols gap-4 justify-center">
            <li class="btn glass py-8 px-6 text-lg font-thin rounded-lg
            bg-white/10 border-white/30 shadow-lg backdrop-blur-md hover:bg-white/20">
                <iconGamepad />
                เติมเกมส์
            </li>
            <li class="btn glass py-8 px-6 text-lg font-thin rounded-lg
            bg-white/10 border-white/30 shadow-lg backdrop-blur-md hover:bg-white/20">
                <iconCoin />
                เติมเงิน
            </li>
            <li class="btn glass py-8 px-6 text-lg font-thin rounded-lg
            bg-white/10 border-white/30 shadow-lg backdrop-blur-md hover:bg-white/20">
                <iconGive />
                โปรโมชั่น
            </li>
            <li class="btn glass py-8 px-6 text-lg font-thin rounded-lg
            bg-white/10 border-white/30 shadow-lg backdrop-blur-md hover:bg-white/20">
                <iconSell />
                ซื้อขาย ไอดีเกมส์
            </li>
            <li class="btn glass py-8 px-6 text-lg font-thin rounded-lg
            bg-white/10 border-white/30 shadow-lg backdrop-blur-md hover:bg-white/20">
                <iconTalk />
                บริการอื่นๆ
            </li>
        </ul>
    </div>

</template>